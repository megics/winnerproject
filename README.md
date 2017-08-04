# ÜÇÜNCÜ TAKIM
- Kaan K. Kölköy
- Ayşegül Koca
- Yankı Ekin Yüksel
- Meliha Gizem Çelik
---
---
---

# GEMS
## [Devise](https://github.com/plataformatec/devise)
- ```gem 'devise'```
- ```bundle install```
- ```rails generate devise User```
- ```rails db:migrate```
    - bu noktadan sonra eğer bir sayfaya erişim için üyelik gerekiyorsa:
    - ilgili controller'ın başına ```before_action :authenticate_user!```
    - kontrol etmek için ```user_signed_in?```
    - aktif kullanıcıya erişmek için ```current_user```
    - aktif session'a erişmek için ```user_session```
- root oluşturmak için ```routes.rb``` dosyasına ```root "home#index"```
- ```rails generate devise:views users```
- Custom controller oluşturmak için
    - ```rails generate devise:controllers users```
    - ```routes.rb``` dosyasında değişiklik yap:
    - ```devise_for :users, controllers: { sessions: 'users/sessions' }```
    - ```views/devise/sessions```'ı ```views/users/sessions``` yap

---
## [Annotate](https://github.com/ctran/annotate_models)
#### [Her migrationdan sonra model ile ilgili kısa özet geçmesi için]
- ```gem 'annotate', require: false```

Bu kadar

---
## [Faker](https://github.com/stympy/faker)
#### Eğlenceli veritabanı testi için
- ```gem 'faker'```
---
## [Bootstrap](https://github.com/twbs/bootstrap-sass)

- ```gem 'bootstrap-sass', '~> 3.3.6'```
- ```app/assets/stylesheets/application.css```'i ```application.scss```'e çevirip içine ```@import 'bootstrap``` ve ```@import "bootstrap-sprockets"``` ekleyin 
- Sunucuyu kapatıp açın
---
## [Simple Form](https://github.com/plataformatec/simple_form)
#### [Formlar kolaylaşsın diye]
- ```gem 'simple_form'```
- ```bundle install```
- ```rails generate simple_form:install --bootstrap```
---
## [Will_paginate](https://github.com/mislav/will_paginate) ve [will_paginate_bootstrap](https://github.com/bootstrap-ruby/will_paginate-bootstrap)
#### Öğreleri sayfalandırmak için, bootstrap'in kendi stilleriyle
- ```gem 'will_paginate', '~> 3.1.0'```
- ```gem 'will_paginate-bootstrap'```
- Kullanımı:
    ```ruby
    ## perform a paginated query:
    @posts = Post.paginate(:page => params[:page])

    # or, use an explicit "per page" limit:
    Post.paginate(:page => params[:page], :per_page => 30)

    ## render page links in the view:
    <%= will_paginate @posts, renderer: BootstrapPagination::Rails %>
    ```
---
## [Whenever](https://github.com/javan/whenever)
#### CronJob oluşturmak için
- ```gem 'whenever', :require => false```
- ```wheneverize .``` 
---
## [Ransack](https://github.com/activerecord-hackery/ransack)
#### Arama formu oluşturmak için
- ```gem 'ransack', github: 'activerecord-hackery/ransack'```

### Kullanımı:

Controller:
```ruby
def index
@q = Person.ransack(params[:q])
@people = @q.result(distinct: true)
end
```
View:
```erb
<%= search_form_for @q do |f| %>

  # Search if the name field contains...
  <%= f.label :name_cont %>
  <%= f.search_field :name_cont %>

  # Search if an associated articles.title starts with...
  <%= f.label :articles_title_start %>
  <%= f.search_field :articles_title_start %>

  # Attributes may be chained. Search multiple attributes for one value...
  <%= f.label :name_or_description_or_email_or_articles_title_cont %>
  <%= f.search_field :name_or_description_or_email_or_articles_title_cont %>

  <%= f.submit %>
<% end %>
```
---
## [Paranoia](https://github.com/rubysherpas/paranoia)
#### Yumuşşak silmek
- ```gem "paranoia", github: "rubysherpas/paranoia", branch: "rails5"```
- bundle install
- ```bin/rails generate migration AddDeletedAtToModelIsmi deleted_at:datetime:index```
- Kullanımı (model içerisinde)
```ruby
class Client < ActiveRecord::Base
  acts_as_paranoid

  # ...
end
```
---
---
---
# GitHub kulanımı
- ```git pull origin development``` yaptıktan sonra ilk iş branch oluşturmak => ```git checkout -b 'branch ismi'```
- Üzerinde çalıştığınız özellik tamamlandıktan sonra ```git push origin 'branch ismi'``` yapıp GihGub'a yollayın. 
- Conflict varsa çözülmesi için oradan ele alınacaktır.
---
- Pull yapmak için ```git checkout development``` yapıp master branch'inden ```git pull origin development``` yapıp ilk aşamaya geri dönün.