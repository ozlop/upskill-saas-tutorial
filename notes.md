## saasapp

### Exercise #17 - Adding pages
To create a new web page for the rails app:

 1. Add a controller file.
  - The controller file contains a new class for the new controller that inherits ApplicationController properties
  - app/controllers/concerns/$controller_file.rb

      ```ruby
        class PagesController < ApplicationController
          def home
          end
        end
      ```

 2. Add a views file.
  - The views file is the actual HTML.
  - app/views/layouts/pages/$views_file.erb
  **This file name must match the method in the controllers file**


 3. Modify routes file.
  - The routes file allows you to point to the new views file.
    ```ruby
    Rails.application.routes.draw do
       root to: 'pages#home'
    end
    ```

Page rendering process:
Home page hit > routes.rb activated > root (home) points to PagesController with home method > controller file activates and uses the home method > home.html.erb is pulled from the views folder.


### Exercise #18 - Google Fonts

*The application layout file shows up on every page of the site.*


*The <%= yield %> dictates where rails pulls in information to from the other views files.*

To add custom fonts to the new homepage:


1. Add google fonts href to app/views/layouts/application.html.erb file.
```html
<!DOCTYPE html>
<html>
  <head>
    <title>Saasapp</title>
    <%= csrf_meta_tags %>
  </head>

  <body>
    <%= yield %>
  </body>
</html>
```
```html
<!DOCTYPE html>
<html>
  <head>
    <title>Saasapp</title>
    <%= csrf_meta_tags %>
    <link href="https://fonts.googleapis.com/css?family=Source+Sans+Pro:400,700,900" rel="stylesheet">
    <%= stylesheet_link_tag    'application', media: 'all', 'data-turbolinks-track': 'reload' %>
    <%= javascript_include_tag 'application', 'data-turbolinks-track': 'reload' %>
  </head>

  <body>
    <%= yield %>
  </body>
</html>
```

2. Add CSS style to app/assets/stylesheets/application.css
```CSS
h1, h2, h3 {
  font-family: 'Source Sans Pro', sans-serif;
}
```


### Exercise #20 - Additional Pages

1. Define a function for the page in the controller file.
2. Create a views file.
3. Modify the routes.rb file in config directory.
```ruby
Rails.application.routes.draw do
    root to: 'pages#home'
    get 'about', to: 'pages#about'
end
```
**Notice the difference between the home page route and the additional page (about) route.**
