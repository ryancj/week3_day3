#Week 3 Day 3(Day 13)

###Sinatra Review
```html
<label for="full-name">Full Name</label>
<input type="text" id="full-name" name="full_name" placeholder="e.g. John Smith">
```
- Id to make the "Full Name" associate with the text box
```html
<label for="department">Department</label>
<input type="radio" name="department" value="sales"> Sales
<input type="radio" name="department" value="marketing"> Marketing
<input type="radio" name="department" value="technical"> Technical
```
- Must have the same name to enforce only one selection
```html
<input type="hidden" name="id" value="123">
```
- Hidden data that will not show on the page  

###Server Static File
- File that doesn't change during the application life
- Create a public folder
- Use href in the link to your style.css
- **/** style, the / is important, it is the root of the public folder

###Authetication
- Not for serious security measures
- You can't log out or design the pop-up window
- protected!
```ruby
helpers do
  def protected!
    return if authorized?
    headers['WWW-Authenticate'] = 'Basic realm="Please enter correct credentials"'
    halt 401, "Not authorized\n"
  end

  def authorized?
    @auth ||=  Rack::Auth::Basic::Request.new(request.env)
    @auth.provided? and @auth.basic? and @auth.credentials and @auth.credentials == ['admin', 'admin']
  end
end
```

###Render vs. Redirect
- Render: server to client, take data render on page
- Redirect: you send a code (3xx in sinatra) with a new URL (with code 2xx) which makes a new request to the server, it makes a third call to check if the site has changed since your last visit
- Variables are only accessible in a single server cycle
