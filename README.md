# rails-cheat-sheet

## routes

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

## generateurs (et migrations?)

## modèles

## controlleurs

## vues

## helpers

## migrations classiques
