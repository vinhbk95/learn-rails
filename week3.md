# Week 3

### Tạo mới project
- `$ rails new sample_app`

### Tạo controller đi kèm với 2 action là help và home
- `$ rails generate controller StaticPages home help`

### Hoàn thành yêu cầu của thầy:
- Tạo thành phần *navbar* và *footer*
  - Tạo mới file `_navbar.html.erb` trong thư mục `/app/views/layouts/`
  ``` html
  <nav class="navbar navbar-default" role="navigation">
	<div class="container">
		<!-- Brand and toggle get grouped for better mobile display -->
		<div class="navbar-header">
			<button type="button" class="navbar-toggle" data-toggle="collapse" data-target=".navbar-ex1-collapse">
				<span class="sr-only">Toggle navigation</span>
				<span class="icon-bar"></span>
				<span class="icon-bar"></span>
				<span class="icon-bar"></span>
			</button>
			<a class="navbar-brand" href="#">IS Team</a>
		</div>

		<!-- Collect the nav links, forms, and other content for toggling -->
		<div class="collapse navbar-collapse navbar-ex1-collapse">

			<ul class="nav navbar-nav navbar-right">
				<li><a href="/">Home</a></li>
				<li><a href="/static_pages/help">Help</a></li>
				<li class="dropdown">
					<a href="#" class="dropdown-toggle" data-toggle="dropdown">Login <b class="caret"></b></a>
					<ul class="dropdown-menu">
						<li><a href="#">Action</a></li>
						<li><a href="#">Another action</a></li>
						<li><a href="#">Something else here</a></li>
						<li><a href="#">Separated link</a></li>
					</ul>
				</li>
			</ul>
		</div><!-- /.navbar-collapse -->
	</div>
</nav>
  ```
  - Tạo mới thành phần `_footer.html.erb` trong thư mục `/app/views/layouts/` 
  ``` html
  <footer>
	<span class="pull-left"><%= link_to 'Rails Tutorials', 'http://google.com' %></span>
	<span class="pull-right">About</span>
	<span class="pull-right">Contact</span>
	<span class="pull-right">News</span>
</footer>
  ```
- Add 2 thành phần *navbar* và *footer* vào master layout
  - Sửa phần *body* của file `/app/views/layout/application.html.erb`
  ``` html
  <body>
	<%= render 'layouts/navbar' %>
	<%= yield %>
	<%= render 'layouts/footer' %>
  </body>
  ```
- Thêm một link vào web:
  - Sử dụng `<%= link_to 'tiêu đề', 'http://linkxxx.com' %>` để thêm vào một link bất kỳ
- Hoàn thiện:
  - Add bootstrap để làm đẹp giao diện với css, thêm link vào phần *head* của `application.html.erb`, nhớ cho lên trên cùng:
  ``` html
  <!-- Latest compiled and minified CSS -->
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
  ```
  - Customize css: thêm css bên dưới vào file `app/assets/stylesheets/static_pages.scss`
  ``` css
  h1{
	color: red;
	font-size: 80px;
	margin-top: 150px;
	margin-bottom: 20px;
	font-weight: 700;
}

p{
	padding: 30px;
	font-size: 30px;
}

footer{
	width: 100%;
	position: absolute;
	bottom: 0px;
}

footer, footer>span{
	height: 60px;
	background-color: #F2F2F2;
	padding: 0px 50px 0px 50px;
	line-height: 60px;
}
  ```
  - Thêm vào file `config/routes.rb` để vào ngay home khi gõ http://domain.com:3000/:  
  ``` ruby
  root 'static_pages#home'
  ```
  
### Demo
- http://ruby-hust.herokuapp.com/

