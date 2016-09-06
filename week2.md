# week2
### Cài đặt ruby on rails
- Cài đặt ruby: `tự cài`
- Cài đặt Ruby on Rails 4.2.6 (giống thầy): `$gem install rails -v 4.2.6`
- Kiểm ta version Rails: `$rails -v` kết qủa `Rails 4.2.6` 

### Tạo mới một project :
- Lấy tên là `blog` và cd vào tư mục đó luôn `$rails new blog | cd blog`
- Cho ruby tải các gói cần tiết về `$bundle install`
- Chạy web: `$rails s` mở web ở địa chỉ http://localhost:3000

### Hoàn thành yêu cầu của thầy:
- Tạo các file và cấu trúc data:
  - `$rails generate scaffold user email:string`
  - `$rails generate scaffold micropost user_id:integer content:string`
  - `$rake db:migrate RAILS_ENV=development`
  - Test thử ở link http://localhost:3000/users và http://localhost:3000/mircoposts
- Hiển thị microposts của mội user:
  - sửa file `blog/app/views/users/show.html.erb`
  ``` html
  <p id="notice"><%= notice %></p>
<p>
  <strong>Email:</strong>
  <%= @user.email %>
</p>
<p>
	<strong>Microposts</strong>
	<ul>
		<% Micropost::where(user_id: @user.id).each do |p| %>
	    <li><%= p.content %></li>
	    <% end %>
	</ul>
</p>
<%= link_to 'Edit', edit_user_path(@user) %> |
<%= link_to 'Back', users_path %>
  ```
- Hiển thị combobox cọn user lúc têm micropost
  - Sửa file: `blog/app/views/micropost/_form.html.erb`
  ``` html
  <%= form_for(@micropost) do |f| %>
  <% if @micropost.errors.any? %>
    <div id="error_explanation">
      <h2><%= pluralize(@micropost.errors.count, "error") %> prohibited this micropost from being saved:</h2>

      <ul>
      <% @micropost.errors.full_messages.each do |message| %>
        <li><%= message %></li>
      <% end %>
      </ul>
    </div>
  <% end %>

  <div class="field">
    <%= f.label :user_id %><br>
    <%= f.collection_select :user_id, User::all, :id, :email %>
  </div>
  <div class="field">
    <%= f.label :content %><br>
    <%= f.text_field :content %>
  </div>
  <div class="actions">
    <%= f.submit %>
  </div>
<% end %>

  ```
