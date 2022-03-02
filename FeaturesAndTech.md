# My Movies List

## Initial features

### Unregistered user

- Navigate through movies lists created by registered users

### Registered user

- Register a new user
  - Authentication with Google or e-mail/password
- Users search for movies
  - Use [API](ExternalMoviesAPI.md) to get movies data
  - Search directly in the API
- User can create, edit and delete lists of movies
- User can share its list with other users
- User can rate movies

## Future features

- List movies best rated
- List movies saved by more users
- User can create its own categories for movies
- User can list movies by category
- Show quantity of users by country in a map
- User can follow other users or specific lists
- User can receive email notifications when a list he follows is updated
- Mobile app

The features roadmap can be seen in the [GitHub repository issues](https://github.com/itamarc/mymovieslist/issues).

## Tools and Technologies

- Front-end with React.js
- AWS Amplify for the frontend
- Back-end with Spring
- AWS EC2 with Docker for the backend API
- AWS RDS MySQL
- Logging using the AWS tools
- Authentication with Google
- Unit testing with JUnit and code coverage with JaCoCo
- Automatic testing with CircleCI
