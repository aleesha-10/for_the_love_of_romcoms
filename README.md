# for_the_love_of_romcoms
https://for-the-love-of-romcoms.vercel.app/

# For the Love of Romcoms
I built this project for two reasons: 
1) I wanted a dedicated platform for romcom enthusiasts
2) I was really interested in trying full-stack development, even though my main fields of interest are AI and Data Science.

   
---
This idea had been sitting on my "to-do and upload on github" list for a long time and it seemed like the perfect way to tackle both the tasks at once.
The application lets you discover, rate, and track romantic comedies, write reviews, interact with other users, and get a personalized romcom prescription based on your current mood. It is fully deployed and usable. I do intend to continue expanding it with new features but I wanted real users testing it first.

---

## Overview

For the Love of Romcoms is an online platform built specifically for the romantic comedy genre. The application pulls data from the TMDB API and organizes films by mood, season, holiday, and trope, making it easier for users to find exactly the kind of romcom they're in the mood for.

---

## Features

**Discovery**
- Browse 2,000+ romantic comedies sourced from the TMDB API
- Filter by season, holiday, mood, trope, decade, language, and minimum rating
- Sort by popularity, rating, release date, or title
- Seasonal and holiday collections (Winter, Spring, Summer, Autumn, Christmas, Valentine's, New Year)
- Daily featured romcom, automatically rotated each day
- Trending movies section

**User Accounts**
- Register and login with JWT-based authentication
- Public profile pages with follower/following system
- User search from the navbar
- Profile picture upload via Cloudinary
- Settings page for profile updates,change password
- personalized share cards 

**Social**
- Write, edit, and delete reviews with 1-5 star ratings and spoiler warnings
- Like reviews and comment on them
- Follow other users and view their public profiles
- Hover cards on reviewer usernames showing profile previews
- Favorites and watchlist saved per user

**Romcom Prescriptor**
- Answer a series of questions about your current mood and preferences
- Get matched with your top 3 romcom recommendations from the database
- Download a shareable result card

---

## Tech Stack

**Frontend**
- React 18 with TypeScript
- Tailwind CSS
- Framer Motion
- React Router v6
- Axios

**Backend**
- Node.js with Express
- Prisma ORM
- MySQL
- JWT authentication
- bcryptjs

**Infrastructure**
- Frontend hosted on Vercel
- Backend and database hosted on Railway
- Profile picture storage via Cloudinary
- Movie data from The Movie Database (TMDB) API

---

## Architecture

The application follows a standard client-server architecture. The React frontend communicates with a REST API built in Express. Prisma handles all database queries against a MySQL instance. Authentication is stateless using signed JWT tokens stored in localStorage.

Movie data is synced from TMDB via a custom script that fetches romance and comedy genre films, automatically detects moods, seasons, holidays, and tropes from each film's metadata, and upserts everything into the database.

---

## Database Schema

Key models: User, Movie, Review, Comment, ReviewLike, CommentLike, Favorite, WatchlistItem, Follow, MovieMood, MovieTrope, QuizResult, PasswordResetToken.

---

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/v1/auth/register | Register new user |
| POST | /api/v1/auth/login | Login |
| GET | /api/v1/auth/me | Get current user |
| PUT | /api/v1/auth/update-profile | Update profile |
| PUT | /api/v1/auth/change-password | Change password |
| POST | /api/v1/auth/upload-avatar | Upload profile picture |
| GET | /api/v1/movies | Get movies with filters |
| GET | /api/v1/movies/:id | Get single movie |
| GET | /api/v1/movies/trending | Get trending movies |
| GET | /api/v1/movies/romcom-of-the-day | Get daily featured movie |
| GET | /api/v1/movies/season/:season | Get movies by season |
| GET | /api/v1/movies/holiday/:holiday | Get movies by holiday |
| GET | /api/v1/movies/mood/:mood | Get movies by mood |
| POST | /api/v1/movies/:id/favorite | Toggle favorite |
| POST | /api/v1/movies/:id/watchlist | Toggle watchlist |
| GET | /api/v1/reviews/movies/:id/reviews | Get movie reviews |
| POST | /api/v1/reviews/movies/:id/reviews | Create review |
| PUT | /api/v1/reviews/:id | Update review |
| DELETE | /api/v1/reviews/:id | Delete review |
| POST | /api/v1/reviews/:id/like | Toggle review like |
| POST | /api/v1/reviews/:id/comments | Add comment |
| DELETE | /api/v1/reviews/comments/:id | Delete comment |
| GET | /api/v1/users/search | Search users |
| GET | /api/v1/users/:username | Get public profile |
| POST | /api/v1/users/:id/follow | Follow user |
| DELETE | /api/v1/users/:id/follow | Unfollow user |

---

## Notable Implementation Details

**TMDB Sync Script**
A custom Node.js script fetches all romance/comedy films from TMDB, runs keyword detection on each film's overview and title to automatically assign seasons, holidays, moods, and tropes, fetches YouTube trailer keys, and upserts everything into the database using Prisma. The script handles pagination across up to 100 pages (~2,000 films) with rate limiting and error recovery per movie.

**JWT Authentication**
Stateless authentication using signed tokens with a 7-day expiry. The token is stored in localStorage and attached to every API request via an Axios interceptor. Expired or invalid tokens are caught by a response interceptor that clears local state and redirects to login.

**Follow System**
Users can follow each other with a self-referential many-to-many relationship on the User model. Public profile pages show follower/following counts, recent reviews, and favorite movies.

**Hover Profile Cards**
Reviewer usernames on movie detail pages show a popup card on hover, fetching live profile stats (favorites, reviews, followers) from the API with a 400ms delay to avoid unnecessary requests on accidental hover.

---

## Data Attribution

Movie data is provided by The Movie Database (TMDB). This product uses the TMDB API but is not endorsed or certified by TMDB.

---

## Author

Built by [aleesha-10](https://github.com/aleesha-10) <3

## Sign up

<img width="343" height="517" alt="image" src="https://github.com/user-attachments/assets/a42e59f7-31f5-4a56-9613-b166c4d4343d" />


## Homepage

<img width="875" height="815" alt="image" src="https://github.com/user-attachments/assets/bd900f40-ecaf-403e-a947-031dd6c1d66b" />


## Movies

<img width="797" height="895" alt="image" src="https://github.com/user-attachments/assets/d450e7fe-50bb-4c5f-aa8d-da4a0f6c5eb1" />

## Seasons

<img width="806" height="804" alt="image" src="https://github.com/user-attachments/assets/727d59b1-6c14-4424-a9c5-ecdd8ece49de" />

## Romcom Prescriptor


<img width="831" height="471" alt="image" src="https://github.com/user-attachments/assets/5da68a82-bf66-48c9-95e2-059d0e86006c" />








