# iOS Posts App - Technical Assessment

## 🎯 Core Requirements

**Technology Stack**

- SwiftUI
- SwiftData/Core Data for local storage
- DummyJSON API (no authentication required)
- Three build schemes: Dev/Staging/Production with XCConfig

**Architecture**

- MVVM + Repository Pattern
- SwiftData/Core Data for local storage
- Async/await networking
- Backend search with pagination
- Comprehensive error handling

## 🎨 Design Specifications

**Figma Design Reference**

- Design Link: [Figma](https://www.figma.com/design/V5MihxWGUW5NnKm6m47xkf/iOS-Posts-App---Technical-Assessment?node-id=3009-19782&t=kuVj5MpFQeWaRoGa-1)
- Follow the provided UI/UX designs exactly
- Implement responsive layouts for different screen sizes
- Match colors, typography, and spacing from Figma specs
- Ensure pixel-perfect implementation of all screens

## 📱 Features to Implement

### 1. Authentication System

**Login/Register Flow:**

- **Login Screen** - Use DummyJSON auth endpoint with hardcoded credentials:
    - Username: `emilys` Password: `emilyspass`
    - Username: `michaelw` Password: `michaelwpass`
    - Or any other valid credentials from DummyJSON users
- **Register Screen** - Mock registration (simulate API call, store locally)
- **API Integration:**
    - `POST https://dummyjson.com/auth/login` for authentication
    - Store JWT token locally using SwiftData/Core Data
    - Implement a token refresh mechanism
    - **Reference: https://dummyjson.com/docs for complete API documentation**
- **Features:**
    - SwiftData/Core Data local storage for user sessions
    - Persistent login state across app launches
    - Form validation and error handling
    - Design-compliant input fields and buttons
    - Secure token storage

### 2. Dashboard

- Search bar with real-time backend search (as per design)
- Featured posts section with design-specified layout
- "View All Posts" navigation following UI patterns
- Proper spacing and visual hierarchy from Figma
- Pull-to-refresh functionality

## ⚙️ Build Configuration Files

Create XCConfig files for each environment:

**Debug.xcconfig**

```
API_BASE_URL = https://dummyjson.com
PAGINATION_LIMIT = 10
SEARCH_DEBOUNCE_DELAY = 300
```

**Staging.xcconfig**

```
API_BASE_URL = https://dummyjson.com
PAGINATION_LIMIT = 15
SEARCH_DEBOUNCE_DELAY = 500
```

**Release.xcconfig**

```
API_BASE_URL = https://dummyjson.com
PAGINATION_LIMIT = 20
SEARCH_DEBOUNCE_DELAY = 800
```

## 🔌 API Integration

### Authentication Endpoints

```
# Login
POST https://dummyjson.com/auth/login
Headers: { "Content-Type": "application/json" }
Body: {
  "username": "emilys",
  "password": "emilyspass",
  "expiresInMins": 30
}

# Get current user
GET https://dummyjson.com/auth/me
Headers: { "Authorization": "Bearer [token]" }

# Reference: https://dummyjson.com/docs for complete API documentation

```

### Data Endpoints

```
# Paginated posts
GET https://dummyjson.com/posts?limit=10&skip=0

# Search with pagination
GET https://dummyjson.com/posts/search?q=love&limit=10&skip=0

# Single post
GET https://dummyjson.com/posts/1

# Users
GET https://dummyjson.com/users
GET https://dummyjson.com/users/1

```

### Sample Authentication Flow

1. User enters hardcoded credentials on login screen (emilys/emilyspass)
2. App sends POST to `/auth/login` with proper headers and body format
3. Store returned JWT token securely
4. Use token for authenticated requests
5. Handle token expiration and refresh
6. **Reference https://dummyjson.com/docs for complete API details**

## 📊 Evaluation Criteria (100 Points)

- **Code Quality** (25pts) - Clean, readable, maintainable code
- **Architecture** (20pts) - MVVM + Repository implementation
- **Functionality** (20pts) - All features working correctly including auth
- **SwiftUI Implementation** (15pts) - Modern SwiftUI best practices + Design accuracy
- **Data Management** (10pts) - SwiftData/Core Data integration
- **Error Handling** (10pts) - Comprehensive error management including auth errors

## 🎨 Design Implementation Requirements

- **Pixel-perfect UI** - Match Figma designs exactly
- **Responsive layouts** - Support multiple iOS device sizes
- **Design system compliance** - Consistent colors, fonts, spacing
- **Authentication UI** - Follow Figma designs for login/register screens

## 📋 Deliverables

1. Complete Xcode project with 3 build schemes
2. XCConfig configuration files
3. README with setup instructions and hardcoded credentials
4. **Design-accurate SwiftUI implementation**
5. **Fully functional authentication system**
6. **Timeline: 1-2 days**

## ✅ Success Criteria

- Fully functional SwiftUI application
- **Working authentication with DummyJSON API**
- **Pixel-perfect design implementation matching Figma**
- Proper MVVM + Repository architecture
- Backend search with pagination
- Local data persistence with SwiftData/Core Data
- Multiple build configurations
- Professional code quality and documentation
- **UI/UX excellence following the provided designs**

## 🔐 Authentication Clarifications

- Use DummyJSON's authentication endpoints
- **Hardcode credentials**: Use `emilys/emilyspass` or other valid DummyJSON user credentials
- Implement proper JWT token handling with `expiresInMins` parameter
- Mock the registration flow (UI only, store user data locally)
- Handle authentication states (logged in/out)
- Secure token storage using Keychain or SwiftData encryption
- **Reference: https://dummyjson.com/docs for complete API documentation and more user credentials**
