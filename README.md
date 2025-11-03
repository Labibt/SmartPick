

## 🎯 Problem Statement

Interviewers often struggle to find appropriate coding problems for candidates during technical interviews. This application solves that by:

1. **Analyzing candidate's solving patterns** from their Codeforces history
2. **Recommending problems they haven't solved** with appropriate difficulty
3. **Prioritizing problems with tags** the candidate is strong in
4. **Providing comprehensive comparison tools** between candidates

## ✨ Key Features

### 🔍 Smart Problem Recommendation Engine
- **Pattern Recognition**: Analyzes solved problems to identify preferred tags and difficulty levels
- **Intelligent Scoring**: Recommends problems based on tag frequency and rating compatibility
- **Difficulty Matching**: Suggests problems within candidate's skill range (≤ peak rating + 200)
- **Tag Filtering**: Filter recommendations by specific algorithmic concepts

### 👥 Multi-Platform Integration
- **Codeforces**: Primary competitive programming statistics
- **LeetCode**: Additional problem-solving metrics
- **GitHub**: Development activity and contribution analysis

### 📊 Advanced User Comparison
- **Side-by-side analysis** of any two candidates
- **Visual charts** for GitHub activity and language preferences
- **Comprehensive metrics** across all connected platforms
- **Winner determination** with detailed breakdowns

### 🛡️ Role-Based Access Control
- **User Dashboard**: Profile management and platform connections
- **Admin Dashboard**: Full leaderboard access and recommendation tools
- **Secure Authentication**: Firebase-powered user management

## 🏗️ Technical Architecture

### Frontend Stack
```
React 18 + TypeScript     → Type-safe component development
Tailwind CSS             → Modern, responsive styling
Vite                     → Fast development and building
React Router             → Client-side navigation
Recharts                 → Data visualization
Lucide React             → Consistent iconography
```

### Backend & Database
```
Firebase Authentication  → User management and security
Firestore               → NoSQL database for user data
Security Rules          → Fine-grained access control
```

### External APIs
```
Codeforces API          → Competitive programming data
LeetCode API            → Problem-solving statistics
GitHub API              → Development activity metrics
```



## 📖 Usage Guide

### For Regular Users
1. **Sign up** with your email and password
2. **Connect your accounts**:
   - Add your Codeforces handle
   - Optionally add LeetCode and GitHub usernames
3. **View your profile** with combined statistics

### For Admins
1. **Access the leaderboard** with sortable columns
2. **Compare any two users** with detailed analysis
3. **Generate problem recommendations**:
   - Select a candidate from the dropdown
   - View recommended problems sorted by relevance
   - Filter by specific algorithmic tags
   - Get direct links to problems

## 🧠 Recommendation Algorithm

The core recommendation engine works through these steps:

```typescript
1. Fetch user's submission history from Codeforces
2. Filter valid submissions (verdict = 'OK' or points > 0)
3. Extract unique solved problems within rating range
4. Analyze tag frequency patterns
5. Score unsolved problems based on tag preferences
6. Rank and return top recommendations
```

**Scoring Formula**: Each problem gets a score equal to the sum of tag frequencies from the user's solving history.


```

### Code Quality
- **TypeScript** for type safety
- **ESLint** for code linting
- **Consistent formatting** with Prettier
- **Component-based architecture**
- **Custom hooks** for state management





