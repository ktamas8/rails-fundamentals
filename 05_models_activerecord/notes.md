## ActiveRecord and ActiveRelation

- active record: design pattern for relational databases
- ActiveRecord: Rails implementation of active record design pattern
- retrieve and maipulate data as objects, not as static rows

ActiveRecord object are 'intelligent'

- understand the structure of the table
- contain data from data rows
- know how to create, read, update, and delete rows
- can be manipulated as objects, then saved easily

ActiveRecord example

```
user = User.new
user.first_name = 'John'
user.save # SQL INSERT

user.last_name = 'Doe'
user.save # SQL UPDATE

user.destroy # SQL DELETE
```

What is ActiveRelation?

- also known as 'Arel'
- object-oriented interpretaion of relational algebra
- simplifies the generation of complex queries
- small queries are chainable
- complex joins and aggregations use efficient SQL
- queries do not execute until needed

ActiveRelation example

```
users = User.where(first_name: 'John') # no query executed yet
users = users.order('last_name ASC').limit(5) # no query executed
user.each { |user| ... } # query executed
```

## Rails console

`bundle exec rails console`
or
`bundle exec rails c`

irb preloaded with our Rails project

Let's experiment:

`subject = Subject.new`

`subject.name = 'Test'`

`subject.save`

# Create records

Method 1

```
subject = Subject.new(name: 'First Subject', visible: true)
subject.position = 1
subject.save
```

Method 2

```
subject2 = Subject.create(name: 'Second Subject', visible: false)
```

## Update records

Method 1

```
subject = Subject.find(1)
subject.name = 'Initial Subject'
subject.save
```

Method 2

```
subject2 = Subject.find(2)
subject2.update(name: 'Next Subject', position: 2)
```

# Delete records

```
bad = Subject.create(name: 'Bad Subject')
subject = Subject.find(3)
subject.destroy
```

# Find records

Find by id

Subject.find(1)

Find by conditions

`Subject.where(visible: true)`

`Subject.where(visible: true).first`

`Subject.where(visible: true, position: 1..3).order(:name).limit(5)`

# One-to-many associations

There are three types of associations:
- one-to-one
- one-to-many
- many-to-many

```
class Subject
  has_many :pages
end
```

```
class Page
  belongs_to :subject
end
```

Association methods for has_many

- subject.pages
- subject.pages << page
- subject.pages.delete(page)
- subject.pages.empty?
- subject.pages.size
- etc...
