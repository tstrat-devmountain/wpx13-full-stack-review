# Area 51 Kill Counter

## Client

### Dependencies
- axios
- react-router-dom
- redux
- react-redux
- node-sass
- react-icons
- http-proxy-middleware
- redux-promise-middleware

### Routes

- home => `/`
    - login.js
- profile => `/profile/:id`
    - Profile.js
- distanceMap => `/kill_map`
    - KillMap.js

### file-structure

- src /
    - components /
        - Profile
            - Profile.js
            - profile.scss
        - KillMap
            - KillMap.js
            - killMap.scss
        - Home
            - Login.js
            - login.scss
    - dux
        - store.js
        - reducer.js
    - App.js / Routes in here
    - index.js
    - index.css / reset
    - setupProxy.js


## Server

### Dependencies

- express
- massive
- dotenv
- express-session
- bcrypt

### Server File Structure
-   server /
    - index.js
    - middlewares /
        - middleware.js
    - controller /
        - killCountController

### Endpoints

**auth**
- login : POST =>  `/api/login`
- register: POST => `/api/register`
- logout: POST => `/api/logout`

**user**
- getAllUsers: GET => `/api/users`
- getOneUser: GET => `/api/users/:id`
- killUser: POST => `/api/users/:id`
- deleteUser: DELETE => `/api/users/:id`
- updateDistance: PATCH => `/api/distance`

**session**
- userSession: => GET => `/api/user_session`

## Database

- users

```sql
create table users ( {
    user_id serial primary key,
    username varchar(32) not null,
    password text not null,
    email text not null
});
```

- user profile
```sql
create table profile ( {
    profile_id serial primary key,
    image text default 'https://res.cloudinary.com/saturnslist/image/upload/q_auto/v1561159141/kcopfm6ygbyzgdu2mzxb.jpg',
    alive boolean default true,
    distance float,
    user_id int references users(user_id)
});
```
