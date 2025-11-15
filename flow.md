# **PEARL MATCH – ROLES & FUNCTIONALITY FLOWS**  
*Full Platform (No MVP) – Role-Based Flow Guide*  
*Version: 1.0 (Aligned with Technical Specification Document)*

---

## **1. USER ROLES OVERVIEW**

| Role | Primary Goal | Key Permissions |
|------|--------------|-----------------|
| **Entrepreneur** | Post missions, find aligned freelancers, manage collaborations | Create/edit missions, view matches, message freelancers, pay via escrow |
| **Freelancer** | Build profile, get matched, apply, collaborate | Create/edit profile, view matches, apply to missions, message entrepreneurs |
| **Admin (Super Admin)** | Full system oversight & moderation | Manage users, missions, payments, analytics, security, logs |

---

## **2. FUNCTIONALITY FLOWS BY ROLE**

---

### **4.1 AUTHENTICATION & USER ACCOUNTS**

#### **All Roles (Shared Flow)**
1. **Sign Up**
   - Enter email + password
   - Select role: **Entrepreneur** or **Freelancer**
   - Receive verification email
   - Complete mandatory profile fields (role-specific)
2. **Login**
   - Email + password → JWT token
3. **Password Reset**
   - Request reset → email link → set new password
4. **Account Settings**
   - Update email, password, notification preferences

> *Admin*: Can log in via secure admin portal (separate endpoint)

---

### **4.2 USER PROFILES – DETAILED**

#### **Entrepreneur Profile Flow**
1. **Create / Edit Profile**
   - About section (text)
   - Type of business (dropdown)
   - Values & communication preferences (multi-select + custom)
   - Project intentions (tags + open text)
   - Collaboration preferences (remote/on-site, etc.)
   - Links (website, LinkedIn, Instagram)
2. **Save & Publish**
   - Profile visible in matching engine once ≥80% complete

#### **Freelancer Profile Flow**
1. **Create / Edit Profile**
   - Bio (rich text)
   - Skills & categories (hierarchical selection + custom)
   - Experience & portfolio (upload images/PDFs)
   - Availability (Immediate / Soon / Flexible)
   - Rates (optional, range or fixed)
   - Values & communication style (multi-select)
   - **Work style orientation** *(optional)*:
     - Creative  
     - Structured  
     - Reliable  
     - Relational  
     → *Not required, not weighted in matching if empty*
2. **Save & Publish**
   - Profile enters matching pool when complete

> *Admin*: Can view, edit, suspend, or delete any profile

---

### **4.3 PROJECT / MISSION CREATION SYSTEM**

#### **Entrepreneur Flow**
1. **Create Mission**
   - Click “Post a Mission”
   - Fill form:
     - Title
     - Description (rich text)
     - Tags (predefined + custom)
     - Project intention (text + tags)
     - Duration (days/weeks/months)
     - Required skills (multi-select)
     - Values / work style preference
     - Budget range *(optional)*
     - Remote / On-site
       - If on-site → enter location (city, country)
2. **Review & Publish**
   - Mission goes live → enters matching engine
   - Appears in Entrepreneur Dashboard under “Published Missions”

> *Admin*: Can edit, pause, or delete any mission

---

### **4.4 INTELLIGENT MATCHING ENGINE**

#### **Entrepreneur Flow**
1. **View Matches**
   - After posting mission → auto-matched freelancers appear
   - Each match shows:
     - Profile preview
     - **Matching Score (0–100)**
     - Breakdown: Intention, Skills, Values, Availability, Location (if applicable)
   - Apply filters: Availability, Rate, Work Style, etc.
2. **Invite or Message**
   - Click “Invite” → sends invitation + opens chat
   - Or start direct message (emails still hidden)

#### **Freelancer Flow**
1. **Discover Matches**
   - Dashboard → “Recommended Missions”
   - Same scoring logic applied in reverse
   - Filters: Budget, Duration, Location, Intention tags
2. **Apply**
   - Click “Apply” → optional cover message
   - Application sent to entrepreneur
3. **Receive Invitations**
   - Notifications → “You’ve been invited to [Mission]”

> *Admin*: Can view all matches, override scores (for moderation), export match data

---

### **4.5 MESSAGING SYSTEM**

#### **Entrepreneur & Freelancer Flow (Post-Match)**
1. **Access Chat**
   - Only after **match confirmed** (application accepted or invite accepted)
   - Dedicated channel per mission
2. **Real-Time Chat**
   - Send text, emojis
   - Attach files (PDF, image, doc ≤10MB)
   - See typing indicators, read receipts
3. **Safe Communication**
   - Emails & phones **hidden**
   - System scans messages:
     - Detects `@`, `+`, phone patterns → **warning popup**
     - Repeated attempts → flag for admin
4. **Notifications**
   - Push/email: new message, file, mention

> *Admin*: Can access **reported chats only**, search messages, export logs

---

### **4.6 DASHBOARDS**

#### **Freelancer Dashboard Flow**
| Section | Functionality |
|--------|---------------|
| **Matches** | View recommended missions with scores |
| **Invitations** | Accept/decline invites |
| **Applications** | Track sent applications (Pending, Accepted, Rejected) |
| **Ongoing Collaborations** | Active missions, chat access, payment status |
| **Saved Missions** | Bookmark missions for later |
| **Notifications** | All activity in one feed |

#### **Entrepreneur Dashboard Flow**
| Section | Functionality |
|--------|---------------|
| **Published Missions** | View, edit, pause, close missions |
| **Applications Received** | Review freelancer applications |
| **Matches** | Auto + manual matches |
| **Collaboration History** | Past missions, ratings, payouts |
| **Favorites** | Saved freelancers |
| **Notifications** | All updates |

> *Admin*: Full access to all dashboards + analytics overlay

---

### **4.7 ADMIN DASHBOARD (SUPER ADMIN)**

#### **Admin Flow**
1. **User Management**
   - Search, filter, view profiles
   - Suspend, delete, impersonate (for support)
   - Reset passwords
2. **Mission Management**
   - View all missions
   - Edit, pause, delete
   - Flag inappropriate content
3. **Moderation Tools**
   - Review reported messages
   - Issue warnings, temporary bans
4. **Analytics (Live)**
   - User sign-ups (daily/weekly)
   - Profile completion %
   - Mission creation rate
   - Matching activity
   - Message volume
   - Conversion: Match → Collaboration
   - Page views & retention
   - Filter usage in matching
5. **Payment Tracking**
   - View all transactions
   - Refund, retry failed payments
6. **System Health**
   - Server status, error logs, API response times

---

### **4.8 PAYMENTS SYSTEM**

#### **Entrepreneur Flow**
1. **Fund Escrow**
   - After accepting freelancer → prompted to pay
   - Enter amount → Stripe checkout
   - Funds held in escrow
2. **Release Payment**
   - Mission marked “Complete” → release funds
   - Platform deducts commission
   - Freelancer paid (payout schedule: instant or 3–5 days)

#### **Freelancer Flow**
1. **View Earnings**
   - Dashboard → “Earnings” tab
   - Pending (in escrow), Available, Paid
2. **Withdraw**
   - Connect Stripe/Bank → request payout

> *Admin*: Full transaction log, manual refund, commission override

---

### **4.9 SECURITY & ANTI-LEAK SYSTEM**

#### **All Users (Passive Enforcement)**
- Emails/phone **never visible** until collaboration ends
- Messaging filter:
  - Detects: `@`, `+33`, `http`, `www`, `contact me outside`
  - → **Popup warning**: “Stay safe — keep communication on Pearl Match”
  - 3+ violations → auto-flag + reduced visibility
- Escrow incentivizes on-platform payment
- Terms of Service: **Off-platform deals prohibited**

#### **Admin Flow**
- View flagged users/messages
- Apply penalties: warning, reduced trust score, suspension

---

### **4.10 ANALYTICS (DAY 1 REQUIREMENT)**

#### **Admin-Only Flow**
- Real-time dashboard with:
  - Charts: sign-ups, missions, matches
  - Funnel: Profile → Mission → Match → Collaboration
  - Heatmap: most used filters
  - Export: CSV / PDF

---

## **SUMMARY: ROLE PERMISSION MATRIX**

| Functionality | Entrepreneur | Freelancer | Admin |
|-------------|--------------|------------|-------|
| Sign up / Login | Yes | Yes | Yes (secure) |
| Edit own profile | Yes | Yes | Yes (all) |
| Create mission | Yes | No | Yes (all) |
| View matches | Yes | Yes | Yes (all) |
| Apply / Invite | Invite | Apply | No |
| Message (post-match) | Yes | Yes | Yes (reported only) |
| Pay via escrow | Yes | Receive | Monitor |
| View own dashboard | Yes | Yes | Yes (all) |
| Access admin panel | No | No | Yes |
| View analytics | No | No | Yes |
| Moderate content | No | No | Yes |
| Suspend users | No | No | Yes |

---

## **FUTURE-READY NOTES (For Devs)**

- All flows must be **API-driven** (REST/GraphQL)
- Matching engine: **modular scoring layers** → plug in AI later
- Messaging: **WebSocket-ready**, channel-based
- Database: **normalized + JSON fields** for flexible tags/values
- Analytics: **event tracking from day 1** (Mixpanel/Segment-ready)

---

**End of Roles & Functionality Flows**  
*Pearl Match – Ready for Development*  
*Last Updated: November 14, 2025*