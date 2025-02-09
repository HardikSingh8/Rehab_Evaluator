# AI-Powered Rehab Exercise Evaluator

This project is a web-based application that uses AI (via MediaPipe's Pose estimation) to evaluate rehabilitation exercises—in this case, squats. It captures a live webcam video, detects key body landmarks, calculates the knee angle, and provides real-time feedback on the quality of the squat.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [How It Works](#how-it-works)
  - [HTML Structure](#html-structure)
  - [CSS Styling](#css-styling)
  - [JavaScript Logic](#javascript-logic)
- [Setup & Usage](#setup--usage)
- [Deployment](#deployment)
- [Future Improvements](#future-improvements)
- [License](#license)
- [Acknowledgements](#acknowledgements)

## Overview

The application leverages MediaPipe's Pose solution to detect and track body landmarks in real time. It focuses on measuring the knee angle during a squat and provides feedback such as:

- **"Stand straight!"** when the knee angle is too wide (indicating a nearly straight leg).
- **"Too low, come up!"** when the knee angle is too narrow.
- **"Good squat!"** when the knee angle is within an acceptable range.
- An instructional message if the required landmarks (hip, knee, ankle) are not reliably visible.

## Features

- **Real-Time Pose Estimation:** Uses the webcam to capture live video and applies MediaPipe’s Pose model.
- **Overlay Visualization:** Draws the detected pose landmarks and connections on a canvas overlaying the video.
- **Knee Angle Calculation:** Computes the angle between the hip, knee, and ankle.
- **Feedback Mechanism:** Displays real-time feedback based on the knee angle or if the required landmarks are not clearly visible.
- **Responsive Design:** The application adjusts for different screen sizes.

## Technologies Used

- **HTML5 & CSS3:** For structuring and styling the web page.
- **JavaScript:** For handling video capture, pose estimation, angle calculations, and feedback logic.
- **MediaPipe (Pose, Drawing Utils, Camera Utils):** For AI-powered pose detection and drawing.
- **Webcam API:** To access the user’s webcam.
- **Python HTTP Server / VS Code Live Server:** For local testing of the web application.

## Project Structure


## How It Works

### HTML Structure

- **Header:** Displays the title of the application.
- **Container:** Holds instructions, the video container, and the feedback area.
- **Video Container:** Contains the `<video>` element (showing the live webcam feed) and the `<canvas>` element (used to draw the detected pose landmarks).
- **Feedback Area:** A `<div id="feedback">` that displays real-time messages.

### CSS Styling

- The CSS sets up a modern, centered layout with a header and a container.
- The video is styled to a fixed size (640×480 pixels) with the canvas absolutely positioned on top so that the drawn landmarks overlay the live video.
- The feedback area is clearly separated with its own styling to ensure it is visible below the video.

### JavaScript Logic

- **Webcam Setup:**  
  The application uses MediaPipe's `Camera` class to access the user's webcam and stream the video.

- **Pose Initialization:**  
  MediaPipe’s `Pose` model is initialized with parameters for model complexity and confidence thresholds. The model processes each video frame and returns the pose landmarks.

- **Visibility Check:**  
  Each landmark (hip, knee, ankle) comes with a `visibility` score. The code checks that these scores are above a set threshold (0.5) before calculating the knee angle.

- **Angle Calculation:**  
  The function `calculateAngle(a, b, c)` computes the angle at the knee using the coordinates of the hip, knee, and ankle with the cosine rule.

- **Feedback Display:**  
  - If all required landmarks are detected with sufficient visibility, the knee angle is calculated and feedback is given:
    - Angle > 160°: "Stand straight!"
    - Angle < 100°: "Too low, come up!"
    - Otherwise: "Good squat!"
  - If the landmarks are missing or not visible enough, a message instructing the user to adjust their position is displayed.

- **Drawing on Canvas:**  
  The pose landmarks and connections are drawn on the canvas using MediaPipe's drawing utilities, overlaying them on the video feed.

## Setup & Usage

### Prerequisites

- A modern web browser (Chrome, Firefox, etc.)
- A webcam for live video capture
- Optionally, Python 3 for running a local HTTP server

### Running Locally

1. **Clone or Download the Repository:**

   ```bash
   git clone https://github.com/yourusername/rehab-evaluator.git
   cd rehab-evaluator


## How It Works

### HTML Structure

- **Header:** Displays the title of the application.
- **Container:** Holds instructions, the video container, and the feedback area.
- **Video Container:** Contains the `<video>` element (showing the live webcam feed) and the `<canvas>` element (used to draw the detected pose landmarks).
- **Feedback Area:** A `<div id="feedback">` that displays real-time messages.

### CSS Styling

- The CSS sets up a modern, centered layout with a header and a container.
- The video is styled to a fixed size (640×480 pixels) with the canvas absolutely positioned on top so that the drawn landmarks overlay the live video.
- The feedback area is clearly separated with its own styling to ensure it is visible below the video.

### JavaScript Logic

- **Webcam Setup:**  
  The application uses MediaPipe's `Camera` class to access the user's webcam and stream the video.

- **Pose Initialization:**  
  MediaPipe’s `Pose` model is initialized with parameters for model complexity and confidence thresholds. The model processes each video frame and returns the pose landmarks.

- **Visibility Check:**  
  Each landmark (hip, knee, ankle) comes with a `visibility` score. The code checks that these scores are above a set threshold (0.5) before calculating the knee angle.

- **Angle Calculation:**  
  The function `calculateAngle(a, b, c)` computes the angle at the knee using the coordinates of the hip, knee, and ankle with the cosine rule.

- **Feedback Display:**  
  - If all required landmarks are detected with sufficient visibility, the knee angle is calculated and feedback is given:
    - Angle > 160°: "Stand straight!"
    - Angle < 100°: "Too low, come up!"
    - Otherwise: "Good squat!"
  - If the landmarks are missing or not visible enough, a message instructing the user to adjust their position is displayed.

- **Drawing on Canvas:**  
  The pose landmarks and connections are drawn on the canvas using MediaPipe's drawing utilities, overlaying them on the video feed.

## Setup & Usage

### Prerequisites

- A modern web browser (Chrome, Firefox, etc.)
- A webcam for live video capture
- Optionally, Python 3 for running a local HTTP server

### Running Locally

1. **Clone or Download the Repository:**

   ```bash
   git clone https://github.com/yourusername/rehab-evaluator.git
   cd rehab-evaluator
