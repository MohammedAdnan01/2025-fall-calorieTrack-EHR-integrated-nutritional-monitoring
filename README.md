# 2025-fall-calorieTrack-EHR-integrated-nutritional-monitoring

## Overview
--------

CalorieTrack is a native Android application designed for e-hospital patients to track their nutrition using AI-driven food analysis. It integrates the patient's Electronic Health Record (EHR) data to provide personalized, real-time health and safety recommendations against meal consumption.

This project is a collaborative effort focusing on robust patient safety and enhanced user experience.

## Key Features
------------

### 1\. Patient Safety & Risk Assessment

*   **EHR Integration:** Fetches patient data (allergies, conditions, vitals) upon login.
    
*   **Real-Time Safety Checks:** Uses AI to compare food ingredients and nutritional breakdown against the patient's EHR to provide instant **Risks, Warnings, and Benefits**.
    
*   **Final Verdict:** Provides a final verdict ("Recommended," "Not Recommended") based on a scoring mechanism that prioritizes health risks.
    
*   **Non-Food Handling:** Robust error handling prevents logging and clearly instructs the user to retry if the image does not contain food.
    

### 2\. Core Tracking & Logging

*   **Dual Input:** Supports instant camera capture and gallery upload feature for analysing meal images.
    
*   **Detailed Breakdown:** Provides dish name, estimated portions, detected ingredients, and macronutrient data (Calories, Protein, Fat, Carbs, Sodium, Sugar).
    
*   **Database Persistence:** Logs all meal records and AI insights to the centralized app\_nutrition\_log table in the e-hospital database.
    

### 3\. User Experience & Guidance

*   **Goal Management:** Allows users to set customizable daily goals for Calories and Macros.
    
*   **AI Nutrition Coach:** Aggregates meal history to provide personalized, actionable nutrition tips (e.g., suggestions for better alternatives or motivational advice).
    
*   **Smart History:** Implements filtering functionality for the meal log history (e.g., "Last 7 Days," "Last 30 Days") for quick access to consumption trends.
    

## Technical Setup
---------------

### Prerequisites

*   Android Studio (Latest Version)
    
*   JDK 11 or higher
    
*   Git
    

### 1\. Clone the Repository

`   git clone [YOUR_REPO_URL]   `
`   cd CalorieTrack   `

### 2\. API Key Configuration (CRITICAL STEP)

The application requires an **OpenAI API Key** to perform food analysis. **Modify the gradle.properties to add the OpenAI API key**

**Action:**

1.  In the root directory of the project, create a file named: gradle.properties.
    
2.  Add your private OpenAI API key to this file using the following format:
    

`   OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx   `

### 3\. Build and Run

1.  Open the project in Android Studio.
    
2.  Perform a Gradle sync.
    
3.  Run the application on an Android device or emulator (Min SDK 24+).
    
