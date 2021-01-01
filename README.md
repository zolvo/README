<h1 align="center">
  <img src="documentation/Screen Shot 2020-12-31 at 11.23.31 AM.png" alt="firstdraftlogo" width="300">
  <br>
  Documentation
</h1>
<h1 align="center">
  <img src="https://cdn.worldvectorlogo.com/logos/react.svg" alt="js-logo" width="50">
  <img src="https://miro.medium.com/max/1400/1*Q5EUk28Xc3iCDoMSkrd1_w.png" alt="pug-logo" width="50">
  <img src="https://i.ibb.co/VpGfh8w/icons8-postgresql-96-1.png" alt="psql-logo" width="50">
  <img src="https://hakin9.org/wp-content/uploads/2019/08/connect-a-flask-app-to-a-mysql-database-with-sqlalchemy-and-pymysql.jpg" alt="psql-logo" width="50">
</h1>

<h1 align="center">
  Overview
</h1>
<h4>
first_draft is a web app that allows user to create an account to create stories and share their thoughts.
</h4>

---

<h1 align="center" >
 <img src="documentation/Screen Shot 2020-12-31 at 1.13.58 PM.png" alt="firstdraft-home" width="80%">
</h1>

<h4 align="center">'first_draft' is a web app inspired by 'Medium' that allows users to share thoughts, stories, and experience. A logged in users have the ability to create stories, giving comments, likes, & follows.
<pFirst_draft is built with React, Flask, Python and PostgreSQL, SQLAlchemy</h4>

---

<h1>Database Schema</h1>

 <img src="documentation/database-schema.png" alt="firstdraftlogo" width="300">

---

<h1>Features</h1>
<h3>Login</h3>

<h4 align='left'; font-size:2em;>

```js
@auth_routes.route('/login', methods=['POST'])
def login():
    """
    Logs a user in
    """
    form = LoginForm()
    print(request.get_json())
    # Get the csrf_token from the request cookie and put it into the
    # form manually to validate_on_submit can be used
    form['csrf_token'].data = request.cookies['csrf_token']
    if form.validate_on_submit():
        # Add the user to the session, we are logged in!
        user = User.query.filter(User.email == form.data['email']).first()
        login_user(user)
        return user.to_dict()
    return {'errors': validation_errors_to_error_messages(form.errors)}, 401

```
