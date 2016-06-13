# scrape_instagram_ruby
Let's scrape instagram with Ruby! This is a short sample code to scrape instagram website with instagram user_id. You can get user profile and latest 12 images.

##Code

```
require 'open-uri'
require 'JSON'

def scrape_instagram(user_id)
  begin
    instagram_source = open("https://www.instagram.com/#{user_id}").read
    content = JSON.parse(instagram_source.split("window._sharedData = ")[1].split(";</script>")[0])
    return content['entry_data']['ProfilePage'][0]['user']
  rescue Exception => e
    return nil
  end
end
```

##Usage
```
scrape_instagram("nyanchan22")
```