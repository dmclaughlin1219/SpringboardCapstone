# Project Proposal: Game Review Website

## Tech Stack

- **Frontend**
  - React (Create React App) for component-driven UI
  - CSS for styling
- **Backend**
  - Node.js with Express for REST API and Steam API proxying
  - JSON Web Tokens (JWT) for authentication
- **Database**
  - MongoDB to store users, articles, comments, and votes
- **Hosting & Deployment**
  - Vercel for frontend
  - Heroku for backend

---

## Focus

This will be an evenly focused full-stack application, demonstrating competency in frontend UI development and backend API design.

---

## Project Type

A responsive web application optimized for desktop and mobile browsers.

---

## Goal

Enable gaming enthusiasts to

1. Discover and read curated articles on popular and trending games
2. View real‐time Steam data (player counts, review summaries)
3. Engage by commenting and voting on articles

---

## User Demographic

- **Primary Audience:** Casual and hardcore gamers of all ages
- **Secondary Audience:** Indie developers, gaming journalists, and streamers seeking community feedback

---

## Data and API

- **External API:**
  - Steam Web API endpoints for game metadata, player counts, and aggregated review scores
  - Cached server-side (10-minute TTL) to avoid rate limits
- **Internal Data:**
  - Articles: Title, slug, body, coverImageURL, tags, authorId, createdAt
  - Users: username, email, hashedPassword, avatarURL, role (“admin” or “user”)
  - Comments: userId, articleId, body, score, createdAt
  - Votes: userId, commentId, voteType (+1/–1)

---

## Project Approach

### 1. Database Schema

- **User**
  - \_id, username, email, passwordHash, avatarURL, role, createdAt
- **Article**
  - \_id, title, slug, body, coverImageURL, tags[], authorId, createdAt
- **Comment**
  - \_id, articleId, userId, body, score, createdAt
- **Vote**
  - \_id, commentId, userId, voteType, createdAt

### 2. Potential API Issues

- **Rate Limits & Key Security**:
  - Mitigate via server-side proxy and caching
- **Data Inconsistency**:
  - Some games may lack public player data or review summaries
- **Schema Drift**:
  - Steam may change field names or endpoints; build resilient data‐mapping utilities

### 3. Sensitive Information

- Store only hashed passwords (bcrypt)
- Secure JWT secret in environment variables
- Never expose Steam API key to the client

### 4. Core Functionality (MVP)

- Article Management (admin only): create, edit, delete
- Steam Data Display: real-time player count, review ratios
- User Authentication: signup, login, protected routes
- Comments & Voting:
  - Post, edit, delete comments
  - Upvote/downvote with net score display

### 5. User Flow

1. Landing Page: shows trending articles with cover images and basic Steam stats
2. Article Detail: page displays full content, embedded Steam data, and comment feed
3. User Authentication: modal/page for signup / login
4. Commenting: inline form for authenticated users, with vote buttons beside each comment
5. Admin Dashboard: (hidden behind admin role) for managing articles and flagged comments

### 6. Stretch Goals

- Full-Text Search & Tag Filtering on articles
- Bookmarking: users can save favorite articles
- Dark Mode Toggle with CSS variables
- Simple Admin Moderation Panel to review flagged content

---

Once reviewed and approved, I’ll break these features into GitHub issues, estimate time per task, and begin with the Steam API proxy and core data models. Please let me know if you’d like adjustments before I proceed.
