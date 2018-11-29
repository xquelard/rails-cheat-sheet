# routes

```ruby
# (get/post/update/delete) url to: 'controller#action', as: helper_name

# same
get 'photos/show'
get 'photos/show', :to 'photos#show'
get 'photos/show' => 'photos#show'

#same
resources :photos
get    'photos',          to: 'photos#index'
get    'photos/new',      to: 'photos#new'
post   'photos',          to: 'photos#create'
get    'photos/:id',      to: 'photos#show' # params[:id]
get    'photos/:id/edit', to: 'photos#edit'
patch  'photos/:id',      to: 'photos#update' #works with put as well
delete 'photos/:id'       to: 'photos#destroy'

# corresponding helpers :
#   photos_path
#   photo_path(:id)
#   new_photo_path
#   edit_photo_path(:id)
```

# generateurs (et migrations?) (plutot les mettre dans chaque sous partie?)

# conventions de nommage

|   | Model name | Controller name     | Table | Files (views directory + controller file) name |
|---|------------|---------------------|-----------------------------------------------------------|---|
|   | Post       | PostsController     | posts | posts/ and posts_controller.rb  |
|   | LineItem   | LineItemsController | line_items | line_items/ and line_items_controller.rb  |
|   | Mouse      | MiceController      | mice | mice/ and mice_controller.rb  |

# modèles
## bases

Les modèles sont la partie "M" du MVC. Ils donnent accès à la base de données via un ORM (Object Relational Mapping), sont utilisés pour la validation côté serveur, et facilitent la création d'association entre différentes tables. La commande : 

```bash
# can use --force-plural if the default plural value is not fitting
rails g model posts
```

créé le modèle et la migration suivantes : 

```ruby
#app/models/post.rb
class Post < ApplicationRecord
end

#db/migrate/timestamp_create_posts.rb
class CreatePosts < ActiveRecord::Migration[5.2]
  def change
    create_table :posts do |t|

      t.timestamps
    end
  end
end
```

## ORM

```ruby
# CREATING

user = User.new
user.name = "David"
user.occupation = "Code Artist"
user.save

# same as above as
user = User.create(name: "David", occupation: "Code Artist")


# SEARCHNG

User.all.where(name: "David", occupation: "Code Artist").order(created_at: :desc)
user = User.first
david = User.find_by(name: 'David')


# UPDATING

user = User.find_by(name: 'David')
user.name = 'Dave'
user.save

# same as above
User.find_by(name: 'David').update(name: 'Dave') # update_all exists too


# DELETING

user = User.find_by(name: 'David')
user.destroy # destroy_all exists too
```

## validation

Les validations s'écrivent directement dans les modèles. Les méthodes suivantes provoquent toutes une vérification des règles de validation (les versions bang des méthodes lèvent une exception, `save` et `update` renvoient `false` en case d'erreur, et `create` renvoi simplement l'objet) : 

- create
- create!
- save ( en ajoutant l'attribut `validate: false` , on peut passer la validation)
- save!
- update
- update!

Il est également possible de checker manuellement si les règles de validations fonctionnent avec les méthodes `valid?` ou `invalid?` (appeller ces méthodes trigger les validations, et remplissent donc le `object.errors.messages` , tout comme un appel à `save()` le ferait) : 

```ruby
class Person < ApplicationRecord
  validates :name, presence: true
end

Person.create(name: "John Doe").valid? # => true
Person.create(name: nil).invalid? # => true
```
 
## callbacks

## associations

# controlleurs

# vues

# helpers

# migrations classiques
