# Movie Catalog

A Vue.js application for searching movies using the OMDB API, developed as a test assignment.

## Overview
This project is a responsive movie catalog app that allows users to search for movies, view results with pagination, and handle edge cases like no results or loading states. The design is inspired by a Figma mockup, featuring a clean UI with a search bar, movie cards, and dynamic pagination.

## Features
- **Search Functionality**: Search movies by title (e.g., "Batman") with debounced input.
- **Pagination**: Dynamic pagination with limited visible pages (e.g., 1, 2, 3, ..., 62 for 618 results), matching the Figma mockup.
- **Responsive Design**: Fully adaptive layout for desktop, tablet, and mobile devices (<768px).
- **Loading State**: Displays a spinner during API requests.
- **No Results**: Shows a message when no movies are found.
- **Placeholder Images**: Replaces missing movie posters with a placeholder.
- **Error Handling**: Displays errors if API fails or the key is invalid.

## Setup
1. **Clone the repository**:
   ```bash
   git clone https://github.com/rezniki/test-movie-catalog.git

2. **Navigate to the project directory:
   ```bash
    cd movie-catalog
   
3. **Install dependencies:
   ```bash
    npm install
   
4. **Run the development server:
   ```bash
    npm run dev
   
5. Open in browser:
     Visit http://localhost:5173 to see the app.

## Time Spent
I spent approximately 9-10 hours on this task, including:
  Setting up the development environment (1 hour).
  Writing and debugging Vue components (4 hours).
  Integrating the OMDB API and handling pagination (3 hours).
  Styling and ensuring responsiveness per Figma mockup (1-2 hours).

## Screenshot 

<img width="1920" height="881" alt="mooz-1" src="https://github.com/user-attachments/assets/cc58a73d-aa9d-4aee-bdc8-6f51ac4de073" />

<img width="1919" height="884" alt="mooz-2" src="https://github.com/user-attachments/assets/32a5369a-d0e3-4833-ae05-c8e5ab3bf658" />

