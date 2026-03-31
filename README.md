## RomComTHIS 
For the Love of RomComs

https://www.romcomthis.com/

I built this project for two reasons:

I wanted a dedicated platform for romcom enthusiasts
I was really interested in trying full-stack development, even though my main fields of interest are AI and Data Science.

This idea had been sitting on my "to-do and upload to github" list for a long time and it seemed like the perfect way to tackle both the tasks at once.
The application lets you discover, rate, and track romantic comedies, write reviews, interact with other users, and get a personalized romcom prescription based on your current mood. It is fully deployed and usable. I do intend to continue expanding it with new features but I wanted real users testing it first.

## Overview

For the Love of Romcoms is an online platform built specifically for the romantic comedy genre. The application pulls data from the TMDB API and organizes films by mood, season, holiday, and trope, making it easier for users to find exactly the kind of romcom they're in the mood for.

## Features

-- Discovery

Browse 2,000+ romantic comedies sourced from the TMDB API
Filter by season, holiday, mood, trope, decade, and minimum rating
Sort by popularity, rating, release date, or title
Seasonal and holiday collections (Winter, Spring, Summer, Autumn, Christmas, Valentine's, New Year)
Daily featured romcom, automatically rotated each day
Trending movies section

-- User Accounts

Register and login with JWT-based authentication
Email verification system with secure token-based flow
Password reset with expiring tokens (forgot/reset password)
Public profile pages with follower/following system
User search from the navbar
Profile picture upload via Cloudinary
Settings page for profile updates, change password
personalized share cards

-- Social

Write, edit, and delete reviews with 1-5 star ratings and spoiler warnings
Like reviews and comment on them
Follow other users and view their public profiles
Notifications when users you follow post reviews
Hover cards on reviewer usernames showing profile previews
Favorites and watchlist saved per user

-- Interactive Movie Experience

Ship Rating system with 5 animated heart-based options and expressive labels (e.g. “My forever OTP 💒”)
Displays community average ship rating
Personal Notebook ( The Notebook ) for logging ( Memory Lane ) thoughts with date and optional notes

-- Notifications

- Hybrid notification system:
- Local notifications (stored in localStorage) for:
- review creation and updates
- comments
- notebook entries
- Server notifications for:
- likes
- follows
- reviews from followed users
- Dedicated Notifications page with:
- “My Activity” (local) and “Social” (server) tabs
- unread indicators
- delete and mark-all-as-read functionality

-- Profile Insights

- Seasonal preferences automatically derived from favorites
- Review frequency metric (reviews / favorites)
- Review statistics with average rating and full star breakdown
- “Your Ship Type” personality system based on rating behavior

-- Romcom Prescriptor

Answer a series of questions about your current mood and preferences
Get matched with your top 3 romcom recommendations from the database
Download a shareable result card

-- Admin

- Protected admin panel (role-based access using isAdmin)
- Manage users, reviews, and movies
- Dashboard with platform statistics
- Ability to expand movie catalog via TMDB sync
- Tech Stack

## Frontend

- React 18 with TypeScript
- Tailwind CSS
- Framer Motion
- React Router v6
- Axios

##  Backend

- Node.js with Express
- Prisma ORM
- MySQL
- JWT authentication
- bcryptjs
- Nodemailer (email verification and password reset)

## APIs & Services

- TMDB API (movie data)
- Cloudinary (profile picture uploads)

# Infrastructure

- Frontend hosted on Vercel
- Backend and database hosted on Railway
- Profile picture storage via Cloudinary
- Movie data from The Movie Database (TMDB) API

## Architecture

The application follows a standard client-server architecture. The React frontend communicates with a REST API built in Express. Prisma handles all database queries against a MySQL instance. Authentication is stateless using signed JWT tokens stored in localStorage.

Movie data is synced from TMDB via a custom script that fetches romance and comedy genre films, automatically detects moods, seasons, holidays, and tropes from each film's metadata, and upserts everything into the database.

The platform also uses a hybrid notification architecture combining client-side (instant feedback) and server-side (social interactions) systems.

## Database Schema

Key models: User, Movie, Review, Comment, ReviewLike, CommentLike, Favorite, WatchlistItem, Follow, Notification, MovieMood, MovieTrope, QuizResult, PasswordResetToken.

API Endpoints
Method	Endpoint	Description
POST	/api/v1/auth/register	Register new user
POST	/api/v1/auth/login	Login
GET	/api/v1/auth/me	Get current user
PUT	/api/v1/auth/update-profile	Update profile
PUT	/api/v1/auth/change-password	Change password
POST	/api/v1/auth/upload-avatar	Upload profile picture
GET	/api/v1/movies	Get movies with filters
GET	/api/v1/movies/:id	Get single movie
GET	/api/v1/movies/trending	Get trending movies
GET	/api/v1/movies/romcom-of-the-day	Get daily featured movie
GET	/api/v1/movies/season/:season	Get movies by season
GET	/api/v1/movies/holiday/:holiday	Get movies by holiday
GET	/api/v1/movies/mood/:mood	Get movies by mood
POST	/api/v1/movies/:id/favorite	Toggle favorite
POST	/api/v1/movies/:id/watchlist	Toggle watchlist
GET	/api/v1/reviews/movies/:id/reviews	Get movie reviews
POST	/api/v1/reviews/movies/:id/reviews	Create review
PUT	/api/v1/reviews/:id	Update review
DELETE	/api/v1/reviews/:id	Delete review
POST	/api/v1/reviews/:id/like	Toggle review like
POST	/api/v1/reviews/:id/comments	Add comment
DELETE	/api/v1/reviews/comments/:id	Delete comment
GET	/api/v1/users/search	Search users
GET	/api/v1/users/:username	Get public profile
POST	/api/v1/users/:id/follow	Follow user
DELETE	/api/v1/users/:id/follow	Unfollow user
Author

## Built by 
aleesha-10  <3
