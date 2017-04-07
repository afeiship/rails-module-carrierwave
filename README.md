# rails-module-carrierwave
> Rails module for carrierwave.

## step by step:
+ install gem:
```ruby
gem 'carrierwave', '~> 0.10.0'
gem 'mini_magick', '~> 4.3'
```
+ generate basic code:
```bash
rails g scaffold Pet name:string description:text image:string
rake db:migrate
```

+ create carrievave config file:
```ruby
# *config/initializers/carrier_wave.rb*
require 'carrierwave/orm/activerecord'
```
```bash
rails generate uploader Image
# you can modify the config
```

+ modify html.erb part:
    + show part:
    ```ruby
    ## old:
    <%= @pet.image %>
    ## new:
    <%= image_tag @pet.image.thumb.url %>
    ```
    + upload part:
    ```html
    <!--Old-->
    <div class="field">
        <%= f.label :image %>
        <%= f.file_text :image %>
    </div>

    <!--New-->
    <div class="field">
        <%= f.label :image %>
        <%= f.file_field :image %>


        <% if f.object.image? %>
            <%= image_tag f.object.image.thumb.url %>
            <%= f.label :remove_image %>
            <%= f.check_box :remove_image %> 
        <% end %>
    </div>
    ```

## resources:
+ https://code.tutsplus.com/tutorials/rails-image-upload-using-carrierwave-in-a-rails-app--cms-25183
+ https://github.com/carrierwaveuploader/carrierwave
+ http://railscasts.com/episodes/253-carrierwave-file-uploads
+ http://www.jianshu.com/p/3105b3a3b7c6