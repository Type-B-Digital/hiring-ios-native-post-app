# iOS Posts App - Technical Assessment

## 🎯 Core Requirements

### Technology Stack
- SwiftUI
- SwiftData/Core Data for local storage
- DummyJSON API (no authentication required)
- Three build schemes: Dev/Staging/Production with XCConfig
- XCTest for unit testing

### Architecture
- MVVM + Repository Pattern
- SwiftData/Core Data for local storage
- Async/await networking
- Backend search with pagination
- Comprehensive error handling
- Unit test coverage for business logic

## 🎨 Design Specifications

### Figma Design Reference
- **Design Link:** Figma
- Follow the provided UI/UX designs exactly
- Implement responsive layouts for different screen sizes
- Match colors, typography, and spacing from Figma specs
- Ensure pixel-perfect implementation of all screens

## 📱 Features to Implement

### 1. Authentication System

#### Login/Register Flow:
- **Login Screen** - Use DummyJSON auth endpoint with hardcoded credentials:
  - Username: `emilys` Password: `emilyspass`
  - Username: `michaelw` Password: `michaelwpass`
  - Or any other valid credentials from DummyJSON users
- **Register Screen** - Mock registration (simulate API call, store locally)

#### API Integration:
- `POST https://dummyjson.com/auth/login` for authentication
- Store JWT token locally using SwiftData/Core Data
- Implement a token refresh mechanism
- Reference: https://dummyjson.com/docs for complete API documentation

#### Features:
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

## 🧪 Unit Testing Requirements

### Mandatory Test Coverage
- **Authentication Services**: Test login/logout functionality, token handling, and error scenarios
- **Repository Layer**: Test API calls, data parsing, and error handling
- **Data Models**: Test Core Data/SwiftData operations, relationships, and validation
- **ViewModels**: Test business logic, state changes, and data transformation
- **Network Layer**: Test API request formation, response parsing, and error cases

### Testing Best Practices
- Use XCTest framework
- Mock external dependencies (API calls, persistent storage)
- Aim for 70%+ code coverage on business logic
- Include both positive and negative test cases
- Test edge cases and error scenarios

### Test Structure
```swift
// Example test structure
class AuthenticationRepositoryTests: XCTestCase {
    // Test successful login
    // Test failed login with invalid credentials  
    // Test token storage and retrieval
    // Test logout functionality
}

class PostsViewModelTests: XCTestCase {
    // Test fetching posts
    // Test search functionality
    // Test pagination
    // Test error handling
    // Test loading states
}
```

## ⚙️ Build Configuration Files

Create XCConfig files for each environment:

### Debug.xcconfig
```
API_BASE_URL = https://dummyjson.com
PAGINATION_LIMIT = 10
SEARCH_DEBOUNCE_DELAY = 300
```

### Staging.xcconfig
```
API_BASE_URL = https://dummyjson.com
PAGINATION_LIMIT = 15
SEARCH_DEBOUNCE_DELAY = 500
```

### Release.xcconfig
```
API_BASE_URL = https://dummyjson.com
PAGINATION_LIMIT = 20
SEARCH_DEBOUNCE_DELAY = 800
```

## 🔌 API Integration

### Authentication Endpoints
```bash
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
```

### Data Endpoints
```bash
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
2. App sends POST to /auth/login with proper headers and body format
3. Store returned JWT token securely
4. Use token for authenticated requests
5. Handle token expiration and refresh

Reference https://dummyjson.com/docs for complete API details

## 📊 Evaluation Criteria (130 Points)

- **Code Quality (10pts)** - Clean, readable, maintainable code with proper documentation
- **Architecture (20pts)** - MVVM + Repository implementation
- **Functionality (20pts)** - All features working correctly including auth
- **Visual Accuracy (25pts)** - Pixel-perfect Figma implementation
- **SwiftUI Implementation (10pts)** - Modern SwiftUI best practices
- **Data Management (15pts)** - SwiftData/Core Data integration
- **Error Handling (10pts)** - Comprehensive error management
- **Unit Testing (15pts)** - Comprehensive test coverage with proper mocking
- **Build Configuration (5pts)** - Professional multi-environment setup

## 🎨 Design Implementation Requirements

- **Pixel-perfect UI** - Match Figma designs exactly
- **Responsive layouts** - Support multiple iOS device sizes
- **Design system compliance** - Consistent colors, fonts, spacing
- **Authentication UI** - Follow Figma designs for login/register screens

## 📋 Deliverables

- Complete Xcode project with 3 build schemes
- XCConfig configuration files
- **Comprehensive unit test suite**
- **Test coverage report**
- README with setup instructions and hardcoded credentials
- Design-accurate SwiftUI implementation
- Fully functional authentication system

**Timeline: 2-3 days** (extended due to testing requirements)

## ✅ Success Criteria

- Fully functional SwiftUI application
- Working authentication with DummyJSON API
- Pixel-perfect design implementation matching Figma
- Proper MVVM + Repository architecture
- Backend search with pagination
- Local data persistence with SwiftData/Core Data
- Multiple build configurations
- **70%+ unit test coverage on business logic**
- **All critical paths covered by tests**
- Professional code quality and documentation
- UI/UX excellence following the provided designs

## 🔐 Authentication Clarifications

- Use DummyJSON's authentication endpoints
- Hardcode credentials: Use emilys/emilyspass or other valid DummyJSON user credentials
- Implement proper JWT token handling with expiresInMins parameter
- Mock the registration flow (UI only, store user data locally)
- Handle authentication states (logged in/out)
- Secure token storage using Keychain or SwiftData encryption
- **Unit test all authentication flows and edge cases**

Reference: https://dummyjson.com/docs for complete API documentation and more user credentials

## 🧪 Testing Guidelines

### What to Test
- **Repository Methods**: API calls, data transformation, error handling
- **ViewModels**: Business logic, state management, user interactions
- **Authentication**: Login, logout, token refresh, persistence
- **Data Models**: Validation, relationships, Core Data operations
- **Utilities**: Helper functions, extensions, formatting

### What NOT to Test
- SwiftUI Views (focus on ViewModels instead)
- Third-party library internals
- Simple getters/setters without logic

### Mock Requirements
- Create mock implementations for:
  - Network layer (URLSession)
  - Persistent storage (Core Data/SwiftData)
  - Authentication service
- Use dependency injection to enable testing

### Test Naming Convention
```swift
func test_methodName_scenario_expectedResult()
// Example:
func test_login_withValidCredentials_returnsSuccessAndStoresToken()
func test_fetchPosts_withNetworkError_returnsFailure()
```

**“Please note that the use of generative AI tools (such as ChatGPT, Claude, or GitHub Copilot) to write code for this assignment is strictly prohibited. You may seek guidance from an AI tool, but all code must be written by you. Also, do not share this Type-B assignment with anyone else.”**
