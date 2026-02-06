# Requirements Document

## Introduction

The Agri-Intelligence & Life-Cycle Management system is a Streamlit-based web application designed to empower farmers in Maharashtra with AI-driven insights across the complete agricultural lifecycle. The system provides multi-crop support with stage-specific guidance, predictive price analytics with market sentiment analysis, weather-based alerts, AI-powered disease diagnosis, marketplace connectivity, and an intelligent Marathi chatbot—all backed by simulated AWS cloud infrastructure.

## Glossary

- **System**: The Agri-Intelligence & Life-Cycle Management Streamlit application
- **User**: A farmer in Maharashtra using the application
- **Crop_Stage**: One of seven lifecycle phases: Sowing, Fertilizers, Protection, Harvesting, Grading, Storage, Sales
- **Supported_Crop**: One of five crops: Onion, Soybean, Cotton, Tur, Tomato
- **Price_Engine**: The AI-powered component that predicts crop prices and analyzes market sentiment
- **Disease_Diagnosis_Module**: The AI vision component that analyzes crop leaf images
- **Weather_Module**: The component that displays current weather and generates alerts
- **Marketplace_Module**: The component that connects farmers with buyers and transport services
- **Chatbot**: The Marathi AI assistant that responds to farmer queries
- **AWS_Logger**: The component that displays simulated AWS cloud operation logs
- **Market_Sentiment**: A classification of market conditions as Bullish, Bearish, or Neutral
- **Marathi_Advice**: Guidance text provided in the Marathi language
- **Sentiment_Gauge**: A visual indicator displaying market sentiment with color coding
- **Recommendation_System**: AI-driven advice system that suggests SELL or HOLD actions
- **Smart_Storage_Module**: IoT-enabled storage monitoring system for Onion crop
- **Storage_Quality_Score**: A calculated metric (0-100) representing storage condition quality
- **IoT_Sensor**: Simulated sensor providing real-time environmental data (Temperature, Humidity, Ammonia)
- **Profit_Calculator**: Interactive calculator for computing profit margins and recommendations
- **Voice_Mode**: Hands-free operation feature with Marathi voice command support
- **Sustainability_Score**: A metric (0-100) tracking environmental impact and wastage prevention
- **QR_Tracking_System**: Supply chain traceability system for individual onion bag tracking
- **Bag_Report**: Detailed tracking information for a specific storage bag including quality grade and shelf life
- **Quality_Grade**: Classification of storage bag quality as A+ (Excellent), A (Good), or B+ (Fair)

## Requirements

### Requirement 1: Multi-Crop Support

**User Story:** As a farmer, I want to select my crop type and receive stage-specific guidance, so that I can manage my farm effectively throughout the growing season.

#### Acceptance Criteria

1. THE System SHALL support exactly five crops: Onion, Soybean, Cotton, Tur, and Tomato
2. WHEN a User selects a Supported_Crop, THE System SHALL display all seven Crop_Stages for that crop
3. FOR each Supported_Crop and Crop_Stage combination, THE System SHALL provide specific Marathi_Advice
4. THE System SHALL organize Crop_Stages in the following order: Sowing, Fertilizers, Protection, Harvesting, Grading, Storage, Sales
5. WHEN a User switches between crops, THE System SHALL update the displayed advice to match the selected crop

### Requirement 2: AI Price Engine with Predictive Analytics

**User Story:** As a farmer, I want to see current and predicted prices with market sentiment, so that I can make informed decisions about when to sell my crops.

#### Acceptance Criteria

1. WHEN a User views price information, THE Price_Engine SHALL display the current price for the selected Supported_Crop
2. WHEN a User views price information, THE Price_Engine SHALL display a 15-day predicted price for the selected Supported_Crop
3. THE Price_Engine SHALL visualize current and predicted prices using a line chart
4. THE Price_Engine SHALL calculate and display a Market_Sentiment indicator as Bullish, Bearish, or Neutral
5. THE Price_Engine SHALL base Market_Sentiment on simulated news analysis factors such as export duty changes, weather patterns, and demand fluctuations
6. WHEN Market_Sentiment is Bullish, THE System SHALL display an indicator suggesting favorable selling conditions
7. WHEN Market_Sentiment is Bearish, THE System SHALL display an indicator suggesting caution in selling
8. THE Price_Engine SHALL display a sentiment gauge with color coding: Green for Bullish (तेजीचा बाजार), Red for Bearish (मंदीचा बाजार), and Orange for Neutral (स्थिर बाजार)
9. THE Price_Engine SHALL provide an AI recommendation box that displays either SELL or HOLD advice based on sentiment and price trend
10. WHEN sentiment is Bullish AND 15-day price change exceeds 2%, THE recommendation SHALL be SELL with bilingual text (English and Marathi)
11. WHEN sentiment is Bearish OR price change is negative, THE recommendation SHALL be HOLD with bilingual text
12. THE Price_Engine SHALL display a dual-line comparison chart showing Forecast Prices versus Last Week Average Prices
13. THE Price_Engine SHALL display professional metrics including Current Price, Forecast Average, Confidence Level, and 15-Day Trend in a multi-column layout
14. THE Price_Engine SHALL display price statistics including Minimum, Maximum, Average, and Volatility percentage
15. THE Price_Engine SHALL list contributing factors that influence the market sentiment

#### Profit Calculator (USP Feature)

16. THE Price_Engine SHALL provide an interactive Profit Calculator with input fields for Quantity, Purchase Cost, Selling Price, and Transport Cost
17. THE Profit Calculator SHALL display real-time calculations for Total Revenue, Total Cost, Gross Profit, and Profit Margin percentage
18. THE Profit Calculator SHALL display Profit per Quintal metric
19. THE Profit Calculator SHALL provide color-coded profit recommendations: Excellent (≥20% margin), Good (≥10% margin), Low (≥0% margin), Loss (<0% margin)
20. THE Profit Calculator SHALL display all labels in bilingual format (English and Marathi)
21. THE Profit Calculator SHALL pre-fill default values from current price data

### Requirement 3: User Profile and Authentication (Future Feature)

**User Story:** As a farmer, I want to register and login to the system, so that I can save my preferences and access personalized features in the future.

#### Acceptance Criteria

1. THE System SHALL display a "शेतकरी प्रोफाइल (User Profile)" section at the top of the sidebar
2. THE User Profile section SHALL include a "📝 नवीन नोंदणी (Register)" button
3. THE User Profile section SHALL include a "🔐 लॉगिन (Login)" button
4. WHEN a User clicks the Register button, THE System SHALL display a "प्रगतीपथावर (Coming Soon)" message
5. WHEN a User clicks the Login button, THE System SHALL display a "प्रगतीपथावर (Coming Soon)" message
6. THE User Profile section SHALL include a note indicating this is a future feature for personalized farmer profiles
7. THE User Profile section SHALL be displayed before the weather information in the sidebar

### Requirement 4: Live Weather Integration and Smart Alerts

**User Story:** As a farmer, I want to see current weather conditions and receive actionable alerts in Marathi, so that I can plan my daily farm activities appropriately.

#### Acceptance Criteria

1. THE Weather_Module SHALL display current temperature in Celsius in a sidebar
2. THE Weather_Module SHALL display rain probability as a percentage in a sidebar
3. THE Weather_Module SHALL display wind speed in km/h in a sidebar
4. THE Weather_Module SHALL display humidity percentage in a sidebar
5. WHEN rain probability exceeds 60%, THE Weather_Module SHALL generate a Marathi alert advising against spraying activities
6. WHEN temperature exceeds 35°C, THE Weather_Module SHALL generate a Marathi alert recommending increased irrigation
7. WHEN wind speed exceeds 25 km/h, THE Weather_Module SHALL generate a Marathi alert advising against spraying activities
8. WHEN all weather conditions are favorable, THE Weather_Module SHALL display a positive message in Marathi
9. THE Weather_Module SHALL update weather information to reflect current conditions
10. THE Weather_Module SHALL display all alerts in Marathi language

### Requirement 5: AI Disease Diagnosis with Vision Simulation

**User Story:** As a farmer, I want to upload a photo of a diseased crop leaf and receive a diagnosis with remedies in Marathi, so that I can treat crop diseases effectively.

#### Acceptance Criteria

1. THE Disease_Diagnosis_Module SHALL provide an image upload interface for crop leaf photos
2. WHEN a User uploads a leaf image, THE Disease_Diagnosis_Module SHALL simulate AI vision analysis
3. WHEN analysis is complete, THE Disease_Diagnosis_Module SHALL identify the disease name
4. WHEN a disease is identified, THE Disease_Diagnosis_Module SHALL provide remedy suggestions in Marathi
5. THE Disease_Diagnosis_Module SHALL display confidence level for the diagnosis
6. THE Disease_Diagnosis_Module SHALL support common image formats including JPG, PNG, and JPEG
7. IF an uploaded image cannot be analyzed, THEN THE Disease_Diagnosis_Module SHALL display an error message in Marathi

### Requirement 6: Marketplace Connectivity

**User Story:** As a farmer, I want to find nearby buyers and book transport services, so that I can efficiently sell and deliver my crops.

#### Acceptance Criteria

1. THE Marketplace_Module SHALL display a list of nearby buyers with their contact information
2. WHEN displaying buyers, THE Marketplace_Module SHALL show buyer name, location, and crop preferences
3. THE Marketplace_Module SHALL provide a "Book Transport" button for arranging logistics
4. WHEN a User clicks "Book Transport", THE System SHALL display transport booking options
5. THE Marketplace_Module SHALL filter buyers based on the currently selected Supported_Crop
6. THE Marketplace_Module SHALL display buyer information in a clear, organized format

### Requirement 7: AWS Cloud Architecture Simulation

**User Story:** As a farmer, I want to see that the system uses professional cloud infrastructure, so that I can trust the reliability and accuracy of the information provided.

#### Acceptance Criteria

1. THE AWS_Logger SHALL display simulated cloud operation logs in the user interface
2. WHEN the Price_Engine performs analysis, THE AWS_Logger SHALL display "SageMaker Sentiment Analysis..." log messages
3. WHEN the System retrieves data, THE AWS_Logger SHALL display "Fetching S3 Data..." log messages
4. WHEN the System executes background operations, THE AWS_Logger SHALL display "Lambda Execution..." log messages
5. THE AWS_Logger SHALL display logs with timestamps
6. THE AWS_Logger SHALL present logs in a professional, non-intrusive manner
7. THE AWS_Logger SHALL update logs in real-time as operations occur

### Requirement 8: Marathi AI Chatbot

**User Story:** As a farmer, I want to ask questions in Marathi and receive context-aware responses, so that I can get immediate help with my farming queries.

#### Acceptance Criteria

1. THE Chatbot SHALL provide a text input interface for User queries
2. WHEN a User submits a query, THE Chatbot SHALL respond in Marathi language
3. THE Chatbot SHALL maintain conversation context across multiple queries
4. THE Chatbot SHALL provide responses relevant to the currently selected Supported_Crop
5. THE Chatbot SHALL provide responses relevant to the current Crop_Stage
6. WHEN a User asks about prices, THE Chatbot SHALL reference current Price_Engine data
7. WHEN a User asks about weather, THE Chatbot SHALL reference current Weather_Module data
8. THE Chatbot SHALL display conversation history in a chat interface format

### Requirement 9: User Interface Design

**User Story:** As a farmer, I want a clean, professional interface with agricultural theming, so that the application is pleasant and easy to use.

#### Acceptance Criteria

1. THE System SHALL use a green color theme throughout the interface
2. THE System SHALL organize functionality into clearly labeled tabs or sections
3. THE System SHALL display the Weather_Module in a sidebar for constant visibility
4. THE System SHALL use clear, readable fonts appropriate for users with varying literacy levels
5. THE System SHALL provide visual feedback for all user interactions
6. THE System SHALL maintain consistent styling across all components
7. THE System SHALL be responsive and functional on different screen sizes

### Requirement 10: Data Persistence and State Management

**User Story:** As a farmer, I want my selections and inputs to be remembered during my session, so that I don't have to re-enter information repeatedly.

#### Acceptance Criteria

1. WHEN a User selects a Supported_Crop, THE System SHALL maintain that selection across different tabs
2. WHEN a User navigates between sections, THE System SHALL preserve the current Crop_Stage selection
3. THE System SHALL maintain Chatbot conversation history throughout the user session
4. THE System SHALL preserve uploaded images in the Disease_Diagnosis_Module until the session ends
5. WHEN a User refreshes the page, THE System SHALL reset to default selections

### Requirement 11: Error Handling and User Feedback

**User Story:** As a farmer, I want clear error messages and feedback in Marathi, so that I understand what went wrong and how to fix it.

#### Acceptance Criteria

1. WHEN an error occurs, THE System SHALL display error messages in Marathi
2. WHEN a User performs an action, THE System SHALL provide visual confirmation of success
3. IF weather data is unavailable, THEN THE Weather_Module SHALL display a fallback message in Marathi
4. IF price data is unavailable, THEN THE Price_Engine SHALL display a fallback message in Marathi
5. WHEN the System is processing a request, THE System SHALL display a loading indicator
6. THE System SHALL handle network failures gracefully without crashing

### Requirement 12: Conditional Smart Storage for Onion

**User Story:** As an onion farmer, I want to monitor my storage facility with IoT sensors and receive AI-driven storage recommendations, so that I can minimize post-harvest losses and maintain onion quality.

#### Acceptance Criteria

#### Smart Storage Module Display

1. WHEN a User selects Onion as the Supported_Crop, THE System SHALL display a "Smart Storage (कांदा चाळ)" tab
2. WHEN a User selects any crop other than Onion, THE System SHALL NOT display the Smart Storage tab

#### IoT Sensor Monitoring

3. THE Smart Storage module SHALL display real-time simulated IoT sensor readings for Temperature, Humidity, and Ammonia levels
4. THE Smart Storage module SHALL display Temperature in Celsius with optimal range indicator (22-28°C)
5. THE Smart Storage module SHALL display Humidity as percentage with optimal range indicator (65-75%)
6. THE Smart Storage module SHALL display Ammonia levels in ppm with safe threshold indicator (< 10 ppm)

#### Alert Generation

7. WHEN Temperature is below 22°C OR above 28°C, THE System SHALL generate a warning alert in Marathi with recommended action
8. WHEN Humidity is below 65% OR above 75%, THE System SHALL generate a warning alert in Marathi with recommended action
9. WHEN Ammonia level exceeds 10 ppm, THE System SHALL generate a critical alert in Marathi indicating decay risk

#### Storage Quality Scoring

10. THE Smart Storage module SHALL calculate an overall Storage_Quality_Score (0-100) based on all sensor readings
11. WHEN Storage_Quality_Score is above 90, THE System SHALL display "Excellent Storage Conditions" message in English and Marathi
12. WHEN Storage_Quality_Score is between 75-90, THE System SHALL display "Good Storage Conditions" message
13. WHEN Storage_Quality_Score is between 60-75, THE System SHALL display "Fair Storage Conditions" warning
14. WHEN Storage_Quality_Score is below 60, THE System SHALL display "Poor Storage Conditions" error message

#### Best Practices and Integration

15. THE Smart Storage module SHALL provide expandable sections with best practices for Temperature Management, Humidity Control, and Regular Inspection in bilingual format
16. THE Chatbot SHALL recognize storage-related queries for Onion crop and reference the Smart Storage tab in responses

#### QR Tracking System - Scanning

17. THE Smart Storage module SHALL provide a QR_Tracking_System for individual bag traceability
18. WHEN a User clicks "Scan QR Code", THE System SHALL simulate QR code scanning with a 1-second delay
19. THE QR_Tracking_System SHALL display a Bag_Report with unique Bag ID, Storage Date, Quality_Grade, and Predicted Shelf Life
20. THE QR_Tracking_System SHALL display detailed tracking information including Batch Number, Farm Location, Harvest Date, Weight, Storage Facility, Last Inspection, and Next Inspection
21. THE QR_Tracking_System SHALL calculate Quality_Grade as A+ (Excellent), A (Good), or B+ (Fair) based on storage conditions
22. THE QR_Tracking_System SHALL predict Shelf Life in days based on quality grade and storage duration
23. THE QR_Tracking_System SHALL display a Quality Trend chart showing quality degradation over 15 days

#### QR Tracking System - Generation

24. THE QR_Tracking_System SHALL provide a "Generate QR" tab for creating new QR codes for storage bags
25. WHEN a User clicks "Generate QR Code", THE System SHALL create a unique Bag ID in format "#ON2026-XXX" where XXX is between 200-299
26. THE QR_Tracking_System SHALL display the generated QR code visual with Bag ID, generation date, and crop type
27. THE QR_Tracking_System SHALL provide print instructions in Marathi including steps for screenshot, printing, plastic cover protection, and bag attachment
28. THE QR_Tracking_System SHALL display success messages in bilingual format after QR generation
29. THE QR_Tracking_System SHALL provide bilingual labels throughout (English and Marathi)

### Requirement 13: Voice Command Support

**User Story:** As a farmer, I want to use voice commands in Marathi to navigate the application, so that I can operate the system hands-free while working in the field.

#### Acceptance Criteria

#### Voice Mode Toggle

1. THE System SHALL display a "Voice Mode" toggle in the sidebar
2. WHEN Voice Mode is enabled, THE System SHALL display a visual status indicator showing "Enabled" (सक्षम) in bilingual format
3. WHEN Voice Mode is disabled, THE System SHALL display a visual status indicator showing "Disabled" (अक्षम) in bilingual format

#### Command Reference

4. WHEN Voice Mode is enabled, THE System SHALL display a command reference card with supported voice commands
5. THE command reference card SHALL list at least four commands: "किंमत दाखवा" (Show prices), "हवामान सांगा" (Tell weather), "रोग शोधा" (Detect disease), "बाजार दाखवा" (Show market)

#### UI Placement

6. THE Voice Mode toggle SHALL be positioned in the sidebar for easy access
7. THE Voice Mode feature SHALL display as a demonstration feature with future integration capability

### Requirement 14: Sustainability Tracking

**User Story:** As an environmentally conscious farmer, I want to track my sustainability metrics and wastage prevention, so that I can understand my environmental impact and improve my farming practices.

#### Acceptance Criteria

#### System Profile Display

1. THE System SHALL display a "System Profile" section in the sidebar as an expandable component
2. THE System Profile SHALL display a Sustainability_Score (0-100) with color coding

#### Score Status Indicators

3. WHEN Sustainability_Score is above 85, THE System SHALL display "Excellent" (उत्कृष्ट) status in green with bilingual labels
4. WHEN Sustainability_Score is between 70-85, THE System SHALL display "Good" (चांगले) status in yellow with bilingual labels
5. WHEN Sustainability_Score is below 70, THE System SHALL display "Fair" (सामान्य) status in orange with bilingual labels

#### Wastage Metrics

6. THE System Profile SHALL display Wastage Prevented metric in kilograms
7. THE System Profile SHALL calculate Wastage Prevented based on Smart_Storage_Module efficiency for Onion crop

#### Visual Design

8. THE System Profile SHALL display a visual progress bar for the Sustainability_Score
9. THE System Profile SHALL provide bilingual labels (English and Marathi) for all metrics

#### Calculation Logic

10. THE Sustainability_Score SHALL be calculated based on storage efficiency and quality maintenance
11. THE System Profile SHALL be positioned in the sidebar below the Voice Mode toggle
