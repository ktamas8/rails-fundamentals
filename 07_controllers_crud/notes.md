## Read index

## Read show

## Create - new

## Create - create

## Strong parameters

Solves a security issue when mass assigning (assigning multiple) parameters. A maliciuos user could alter our post request and try to update for example the password of a user.

Strong parameters will make it possible white listing parameters that we can accept as part of mass assignment.

`params.require(:subject).permit(:name, :position, :visible)`

## Update - edit and update

## Partials and helpers

- better code organization
- DRY
- partials are partial templates
- helpers are methods that can be called in the view templates

Let's move the create/update form to a partial!

## Challenge

Implement CRUD for pages:
- resourceful routes
- controller associations
- index, show, new, create, edit, update, delete, destroy
- views
