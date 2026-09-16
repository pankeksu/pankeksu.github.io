def rewrite_url(page_url)
    return_url = page_url.dup
    if ENV['JEKYLL_ENV'] == 'production'
        site = @context.registers[:site]
        site_url = site.config['url']
        if page_url.start_with?('https://')
            for subdomain in site.config['subdomain_folders']
                if page_url.start_with?(site_url + '/' + subdomain + '/')
                    return_url['www.volgar.name/' + subdomain + '/'] = subdomain + '.volgar.name/'
                    break
                end
            end
        elsif page_url.start_with?('/')
            from_page = @context['page']
            for subdomain in site.config['subdomain_folders']
                if from_page['path'].start_with?(subdomain + '/')
                    from_subdomain = subdomain
                end
                if page_url.start_with?('/' + subdomain + '/')
                    to_subdomain = subdomain
                end
            end
            if !to_subdomain.nil?
                return_url.slice!(0, to_subdomain.length + 1)
            end
            if from_subdomain != to_subdomain
                return_url = site_url.gsub('www', to_subdomain || 'www') + return_url
            end
        end
    end
    return_url
end