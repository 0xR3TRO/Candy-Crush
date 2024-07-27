## Project Description

### Goal:

The "Candy Crush Browser Game" project aims to create a browser-based game inspired by the iconic Candy Crush. The application will provide players with an engaging experience of matching colorful candies to score points and progress through various levels. The game will be accessible on multiple devices, ensuring smooth and captivating gameplay.

### Features:

- **Gameplay:** Players will swipe candies to form lines of at least three identical candies, earning points.
- **Levels:** The game will feature multiple levels with increasing difficulty.
- **Bonuses:** Special candies and bonuses for creating larger combinations or achieving specific goals.
- **Leaderboard:** Players can compare their scores with friends and other players.
- **Social Integration:** Ability to share scores and invite friends to play through social media.

## Requirements Analysis:

### Functional Requirements:

- **Gameplay:** Intuitive interface allowing players to swipe candies to form matching lines.
- **Levels:** Multi-level structure with increasing difficulty.
- **Bonuses:** Mechanics for creating and using special candies.
- **Leaderboard:** Feature for comparing scores with other players.
- **Social Integration:** Options for sharing scores and inviting friends.

### Non-Functional Requirements:

- **Smooth Gameplay:** The game should run smoothly on various browsers and devices.
- **Aesthetics:** Colorful and attractive graphics reminiscent of the original Candy Crush.
- **User Interface:** Intuitive and easy-to-use interface.

## User Interface Design:

### Sketches/Visualizations:

- _Home Page:_ Main menu with options to start the game, view levels, leaderboard, and settings.
- _Game Screen:_ Game board with candies, score counter, move counter, level progress bar.
- _Leaderboard:_ List of player scores, with the ability to filter by friends and global players.

### Sitemap:

- _Home Page_
  - Main Menu
  - Start Game
  - Leaderboard
  - Settings
- _Game Screen_
  - Game Board
  - Score Counter
  - Move Counter
  - Level Progress Bar
- _Leaderboard_
  - Friends' Scores
  - Global Scores

## System Architecture:

### Data Structure Description:

The application will store data related to levels, player scores, and game details, including:

- **Levels:** Information about candy layouts, level requirements, and bonuses.
- **Player Scores:** Storage of individual player scores.
- **Gameplay:** Current game state, player moves, earned points.

### Architecture Diagrams:

The architecture is based on the MVC (Model-View-Controller) structure, where:

- **Model:** Handles game logic, level management, and scores.
- **View:** Presents the user interface.
- **Controller:** Manages communication between the model and view.

## Implementation:

### Technology Description:

- **Frontend:** HTML, CSS, JavaScript (React.js).
- **Backend:** Node.js with Express.js (handling game logic and database integration).
- **Database:** MongoDB (storing data about levels, scores, and players).

### Code Structure:

- _Directories/Files:_ Separate files for game logic, user interface, data management.
- _Coding Style:_ Emphasis on modularity, readability, and code commenting.

## Testing:

### Test Plan:

- **Unit Tests:** Verify the correctness of game logic and level management functions.
- **Integration Tests:** Ensure that components interact correctly with each other.
- **User Interface Tests:** Test user interactions on various devices.
- **Performance Tests:** Assess game performance under different loads.

### Testing Procedures:

- Develop a set of test cases for each application function.
- Establish procedures for reporting and fixing discovered bugs.

## Deployment and Maintenance:

### Deployment Plan:

- **Deployment Stages:** Testing, fixes, publication on platforms accessible to users.
- **Timeline:** Define dates for planned stages.

### Maintenance Procedures:

- **Technical Support:** Establish communication channels for users to report issues.
- **Updates:** Plan regular updates based on user needs and feedback.

## Schedule:

### Project Plan:

- **Implementation Stages:** Breakdown of tasks (e.g., game logic implementation, UI development, testing).
- **Timeline:** Define the time required for each stage.

## Budget:

### Estimated Costs:

- **Application Development:** Based on hours worked or development team.
- **Maintenance Costs:** Servers, potential external service fees, technical support.

---

[Polish](<Documents/README(PL).md>)
