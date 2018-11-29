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

# modèles (et relations + leur migrations)
## bases

Les modèles sont la partie "M" du MVC. Ils donnent accès à la base de données via un ORM (Object Relational Mapping), sont utilisés pour la validation côté serveur, et facilitent la création d'association entre différentes tables. La commande : 

```bash
rails g model posts
```

## validation

## callbacks

## associations

# controlleurs

# vues

# helpers

# migrations classiques
