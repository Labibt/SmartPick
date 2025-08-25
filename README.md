# 🏆 Codeforces Interview Problem Recommender

A sophisticated web application that helps interviewers recommend coding problems to candidates based on their Codeforces solving patterns and competitive programming history.

![React](https://img.shields.io/badge/React-18.3.1-blue?logo=react)
![TypeScript](https://img.shields.io/badge/TypeScript-5.5.3-blue?logo=typescript)
![Firebase](https://img.shields.io/badge/Firebase-11.10.0-orange?logo=firebase)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.4.1-blue?logo=tailwindcss)
![Vite](https://img.shields.io/badge/Vite-5.4.2-purple?logo=vite)

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

## 🚀 Getting Started

### Prerequisites
- Node.js 18+ and npm
- Firebase project with Firestore enabled
- Basic understanding of React and TypeScript

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/codeforces-interview-recommender.git
   cd codeforces-interview-recommender
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Firebase Setup**
   - Create a Firebase project at [Firebase Console](https://console.firebase.google.com)
   - Enable Authentication (Email/Password)
   - Enable Firestore Database
   - Update `src/firebase/config.ts` with your Firebase configuration

4. **Configure Firestore Security Rules**
   ```javascript
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /users/{userId} {
         allow read, write: if request.auth != null && request.auth.uid == userId;
       }
       match /userStats/{document=**} {
         allow read: if request.auth != null;
       }
     }
   }
   ```

5. **Start the development server**
   ```bash
   npm run dev
   ```

6. **Create admin account**
   - Sign up with email: `admin@gmail.com`
   - This account will have admin privileges automatically

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

## 🔧 API Integration

### Rate Limiting Strategy
- **Exponential backoff** for failed requests
- **Request queuing** to avoid overwhelming APIs
- **Error handling** with user-friendly messages
- **Fallback mechanisms** for API failures

### Data Synchronization
- **Real-time updates** through Firebase
- **Lazy loading** for optimal performance
- **Caching** of processed statistics
- **Manual refresh** options for admins

## 📊 Database Schema

### Users Collection (`/users/{userId}`)
```typescript
interface FirebaseUser {
  uid: string;
  email: string;
  codeforcesHandle?: string;
  leetcodeHandle?: string;
  githubHandle?: string;
  isAdmin: boolean;
  createdAt: number;
}
```

### User Statistics (`/userStats/{userId}`)
```typescript
interface UserStats {
  handle: string;
  email: string;
  maxRating: number;
  problemsSolved: number;
  totalProblemsSolved: number;
  averageRating: number;
  bestRank: number;
  currentRating: number;
  lastUpdated: number;
}
```

## 🛠️ Development

### Project Structure
```
src/
├── components/          # React components
│   ├── Auth/           # Authentication forms
│   └── Dashboard/      # User and admin dashboards
├── hooks/              # Custom React hooks
├── services/           # API integration services
├── types/              # TypeScript type definitions
├── firebase/           # Firebase configuration
└── styles/             # Global styles
```

### Available Scripts
```bash
npm run dev      # Start development server
npm run build    # Build for production
npm run preview  # Preview production build
npm run lint     # Run ESLint
```

### Code Quality
- **TypeScript** for type safety
- **ESLint** for code linting
- **Consistent formatting** with Prettier
- **Component-based architecture**
- **Custom hooks** for state management

## 🚀 Deployment

### Build for Production
```bash
npm run build
```

### Deploy to Firebase Hosting
```bash
npm install -g firebase-tools
firebase login
firebase init hosting
firebase deploy
```

### Environment Variables
Ensure your Firebase configuration is properly set in `src/firebase/config.ts` for production deployment.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Contribution Guidelines
- Follow TypeScript best practices
- Add proper error handling
- Include loading states for async operations
- Write descriptive commit messages
- Test your changes thoroughly

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Codeforces** for providing comprehensive competitive programming APIs
- **Firebase** for robust backend infrastructure
- **React community** for excellent tooling and libraries
- **Tailwind CSS** for beautiful, responsive design system

## 📞 Contact

- **GitHub**: [@yourusername](https://github.com/yourusername)
- **Email**: your.email@example.com
- **LinkedIn**: [Your LinkedIn Profile](https://linkedin.com/in/yourprofile)

---

⭐ **Star this repository** if you find it helpful for your interview preparation or technical projects!

## 🔮 Future Enhancements

- [ ] **AtCoder Integration** - Add support for AtCoder competitive programming platform
- [ ] **Contest Recommendations** - Suggest upcoming contests based on user skill level
- [ ] **Team Formation** - Match candidates with complementary skills
- [ ] **Progress Tracking** - Monitor improvement over time
- [ ] **Mobile App** - React Native version for mobile access
- [ ] **AI-Powered Insights** - Machine learning for better recommendations
- [ ] **Interview Scheduling** - Integration with calendar systems
- [ ] **Video Conferencing** - Built-in interview capabilities