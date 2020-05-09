## Render a template

Request-Response Loop
- route
- controller
- view template

- add `get 'demo/hello'` to routes
- add hello action to controller
- add hello.html.erb file to views
- demonstrate in browser that the route is accessible
- default behaviour - convention over configuration in action
- add `render 'hello'` to index and vice versa to demonstrate that the defaults can be overwritten

## Redirect actions

Controllers can redirect - not only render a view. Example scenario:

Not logged in user requests an action only available to logged in users. Controller redirects to login page.
We don't want just to render login view. We want to redirect so that the url also changes.

How it works in action?
It is a HTTP Redirect - 302 response
Brand new web request takes place

`redirect_to(controller: 'demo', action: 'index')`
controller can be omitted if stays within same controller
`redirect_to(action: 'index')`
`redirect_to('https://www.anydomain.com/any-path')`

Demonstrate this in practice
Also show server console - two requests!

## View templates

We can embed Ruby code in our template. The default way is ERB.

What is ERB?
- short for embedded Ruby
- templating system to embed Ruby code

Template file naming
- e.g.: hello.html.erb
- template name: hello
- processed with: ERB
- output format: HTML

Embedding Ruby in an ERB template
- <% Ruby code %> - executes Ruby code
- <%= Ruby code %> - executes Ruby code and outputs the result into the template

Demonstration

Use hello.html.erb
`<% 1 + 1 %>` - nothing happens as no output
`<%= 1 + 1 %>` - displays 2
`<% target = 'world' %>`
`<%= "Hello #{target}!" %>`

We can also use it for control flow
`<% 3.times do |n| %>`
`<p><%= n %></p>`
`<% end %>`

Let's check the HTML source in the browser to show how it was injected there.

## Instance variables

Variables: only available in the given action
Instance variables: available everywhere in the current instance of the controller. Also made available to the view so it can be used in the template. This how we can pass data to the view.

Demonstration

demo#hello controller action - add this:
`@array = [1, 2, 3, 4, 5]`
use this in the view template instead of 3.times

This is a one way street! Controller sets up all data beforehand and hands it to the view. The view cannot go back to the controller to request more data.

## Links

Let's learn how to link from one view to another!

This is an HTML link:
`<a href="/demo/hello">Click me!</a>`

We don't often see this in Rails templates.
Instead we use a helper method:
`<%= link_to(text, target) %>`
The output will be an HTML link.

Demonstration

In index.html.erb write these:
`<a href="/demo/hello">Hello page 1</a>`
`<%= link_to('Hello page 2', { action: 'hello' }) %>`
Again, controller can be omitted as within same controller.

Show it in browser. Also show HTML source - same a href tag!
Add a backlink from hello to index to be able to switch back and forth.

## URL parameters

Relative URL with parameters:

/demo/hello/1?page=3&name=John

These URL parameters are available through params:

`params[:page]`
  or
`params['page']`

Demonstration

Add to index.html.erb:
`<%= link_to('Hello with params', { action: 'hello', page: 5, id: 20 }) %>`

Show this in browser

Now go back to demo_controller and read the params - also demonstrate that param name can be string or symbol

`@id = params['id']`
`@page = params[:page]`

Use these in the template

## Challenge

- add new DemoController actions: #about, #contact
- dont't forget about routes and templates!
- add links between the two new pages
- in DemoController#contact, check for a 'country' parameter
- if 'us' or 'ca' the phone number is '(800) 123-4567'
- if 'uk' use different phone number: '(020) 9876-5432'
- if anything else then a third phone number
