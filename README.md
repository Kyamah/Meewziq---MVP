Meewziq
Meewziq is a web-based music recommendation system designed to help users discover new songs based on their preferences. By analyzing user-inputted data and leveraging external music APIs, Meewziq offers intelligent song suggestions. Unlike proprietary algorithms, Meewziq aims to provide transparency and customization in music discovery.
Problem Statement
With the vast array of songs available on streaming platforms, users often struggle to find music that matches their taste. Existing recommendation systems often rely on opaque algorithms. Meewziq addresses this by providing an open, web-based platform where users can input their favorite songs and receive personalized recommendations.
Objectives
Finalize system requirements and establish MVP features.
Research and implement suitable recommendation algorithms.
Set up a robust development environment with version control.
Design an interactive user interface using React.js.
Implement a scalable backend using Node.js and Express.js.
Integrate the Spotify API to fetch song data.
Technology Stack
Frontend: React.js
Backend: Node.js with Express.js
Database: MongoDB
External API: Spotify API
Recommendation Algorithm: Content-based filtering (with future plans for collaborative filtering)
System Architecture
Meewziq follows a structured architecture consisting of:
Frontend: Users input their favorite songs using a search bar.
Backend: API requests are processed, and song data is retrieved from the Spotify API.
Recommendation Engine: Songs are analyzed and recommendations are generated.
Database: Stores user preferences and interaction history.
Project Setup
Version Control
GitHub Repository: Maintained using Git with a branch strategy:
main: Stable production code.
development: Active development branch.
feature-branches: For individual features.
Environment Setup
Frontend Setup (React.js)
npx create-react-app meewziq
cd meewziq
npm install axios react-router-dom
npm start


Backend Setup (Node.js & Express.js)
mkdir backend
cd backend
npm init -y
npm install express cors dotenv axios


Express.js Server Configuration (backend/server.js)
const express = require('express');
const cors = require('cors');
require('dotenv').config();


const app = express();
app.use(cors());
app.use(express.json());


const PORT = process.env.PORT || 5000;
app.listen(PORT, () => console.log(`Server running on port ${PORT}`));
UI Design
Wireframing
Wireframes were created using Figma to illustrate the user journey. Key components include:
Homepage: Search bar for song input.
Recommendations Page: Displays recommended songs.
Search Component (React.js)
import React, { useState } from 'react';
import axios from 'axios';


const SearchBar = () => {
  const [query, setQuery] = useState('');
  const [results, setResults] = useState([]);


  const searchSongs = async () => {
    const response = await axios.get(`http://localhost:5000/search?q=${query}`);
    setResults(response.data);
  };


  return (
    <div>
      <input
        type="text"
        value={query}
        onChange={(e) => setQuery(e.target.value)}
        placeholder="Enter a song name"
      />
      <button onClick={searchSongs}>Search</button>
      <ul>
        {results.map(song => <li key={song.id}>{song.name}</li>)}
      </ul>
    </div>
  );
};


export default SearchBar;


Challenges Faced and Solutions
API Authentication Complexity:
Solution: Implemented a backend proxy for Spotify API authentication and token management.
Data Format Variability:
Solution: Developed a middleware to standardize API responses.
State Management Issues:
Solution: Integrated React Context API for efficient state management.
Contributors 

Peter Kyama


