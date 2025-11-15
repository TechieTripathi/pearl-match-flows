# Pearl Match - Complete Flow Diagrams

## 1. Authentication & User Account Flow

```mermaid
flowchart TD
    A[Start] --> B[Sign Up]
    B --> C{Select Role}
    C -->|Entrepreneur| D[Entrepreneur Profile Setup]
    C -->|Freelancer| E[Freelancer Profile Setup]
    D --> F[Email Verification]
    E --> F
    F --> G[Account Created]
    
    H[Login] --> I[Email + Password]
    I --> J[JWT Token Generated]
    J --> K[Dashboard Access]
    
    L[Password Reset] --> M[Request Reset Email]
    M --> N[Click Email Link]
    N --> O[Set New Password]
    O --> P[Password Updated]
    
    Q[Account Settings] --> R[Update Email/Password/Notifications]
    R --> S[Settings Saved]
```

## 2. Entrepreneur Profile Creation Flow

```mermaid
flowchart TD
    A[Create Profile] --> B[About Section]
    B --> C[Business Type Selection]
    C --> D[Values & Communication Preferences]
    D --> E[Project Intentions]
    E --> F[Collaboration Preferences]
    F --> G[Add Links]
    G --> H{Profile ≥80% Complete?}
    H -->|Yes| I[Save & Publish]
    H -->|No| J[Complete Required Fields]
    J --> H
    I --> K[Profile Visible in Matching Engine]
```

## 3. Freelancer Profile Creation Flow

```mermaid
flowchart TD
    A[Create Profile] --> B[Bio Section]
    B --> C[Skills & Categories]
    C --> D[Experience & Portfolio Upload]
    D --> E[Availability Status]
    E --> F[Rate Information]
    F --> G[Values & Communication Style]
    G --> H[Work Style Orientation - Optional]
    H --> I{Profile Complete?}
    I -->|Yes| J[Save & Publish]
    I -->|No| K[Complete Required Fields]
    K --> I
    J --> L[Profile Enters Matching Pool]
```

## 4. Mission Creation Flow (Entrepreneur)

```mermaid
flowchart TD
    A[Click 'Post a Mission'] --> B[Enter Title]
    B --> C[Write Description]
    C --> D[Add Tags]
    D --> E[Project Intention]
    E --> F[Set Duration]
    F --> G[Required Skills Selection]
    G --> H[Values/Work Style Preference]
    H --> I[Budget Range - Optional]
    I --> J{Remote or On-site?}
    J -->|On-site| K[Enter Location]
    J -->|Remote| L[Review & Publish]
    K --> L
    L --> M[Mission Goes Live]
    M --> N[Enters Matching Engine]
    N --> O[Appears in Dashboard]
```

## 5. Intelligent Matching Engine Flow

```mermaid
flowchart TD
    A[Mission Posted] --> B[Auto-Match Algorithm]
    B --> C[Calculate Matching Scores]
    C --> D[Score Breakdown: Intention + Skills + Values + Availability + Location]
    D --> E[Generate Match List 0-100 Score]
    
    F[Freelancer Views Matches] --> G[Recommended Missions Dashboard]
    G --> H[Apply Filters]
    H --> I[View Mission Details]
    I --> J{Interested?}
    J -->|Yes| K[Click Apply]
    J -->|No| L[Continue Browsing]
    K --> M[Optional Cover Message]
    M --> N[Application Sent]
    
    O[Entrepreneur Views Matches] --> P[Matched Freelancers List]
    P --> Q[View Profile Previews]
    Q --> R{Action Choice}
    R -->|Invite| S[Send Invitation + Open Chat]
    R -->|Message| T[Start Direct Message]
    R -->|Skip| U[View Next Match]
```

## 6. Messaging System Flow

```mermaid
flowchart TD
    A[Match Confirmed] --> B[Chat Channel Created]
    B --> C[Real-time Messaging Available]
    C --> D[Send Text/Emojis/Files]
    D --> E[Message Security Scan]
    E --> F{Contains Contact Info?}
    F -->|Yes| G[Warning Popup Displayed]
    F -->|No| H[Message Delivered]
    G --> I{Repeated Violations?}
    I -->|Yes| J[Flag for Admin Review]
    I -->|No| K[Warning Logged]
    J --> L[Reduced Visibility/Penalties]
    H --> M[Read Receipts & Typing Indicators]
    M --> N[Push/Email Notifications]
```

## 7. Freelancer Dashboard Flow

```mermaid
flowchart TD
    A[Freelancer Dashboard] --> B[Matches Section]
    A --> C[Invitations Section]
    A --> D[Applications Section]
    A --> E[Ongoing Collaborations]
    A --> F[Saved Missions]
    A --> G[Notifications]
    
    B --> H[View Recommended Missions with Scores]
    C --> I[Accept/Decline Invites]
    D --> J[Track Application Status]
    E --> K[Active Missions + Chat + Payment Status]
    F --> L[Bookmarked Missions]
    G --> M[Activity Feed]
```

## 8. Entrepreneur Dashboard Flow

```mermaid
flowchart TD
    A[Entrepreneur Dashboard] --> B[Published Missions]
    A --> C[Applications Received]
    A --> D[Matches Section]
    A --> E[Collaboration History]
    A --> F[Favorites]
    A --> G[Notifications]
    
    B --> H[View/Edit/Pause/Close Missions]
    C --> I[Review Freelancer Applications]
    D --> J[Auto + Manual Matches]
    E --> K[Past Missions + Ratings + Payouts]
    F --> L[Saved Freelancers]
    G --> M[All Updates Feed]
```

## 9. Payment System Flow

```mermaid
flowchart TD
    A[Freelancer Accepted] --> B[Entrepreneur Prompted to Pay]
    B --> C[Enter Amount]
    C --> D[Stripe Checkout]
    D --> E[Funds Held in Escrow]
    E --> F[Work Begins]
    F --> G[Mission Completed]
    G --> H[Entrepreneur Releases Payment]
    H --> I[Platform Deducts Commission]
    I --> J[Freelancer Receives Payment]
    
    K[Freelancer Earnings Dashboard] --> L[View Pending/Available/Paid]
    L --> M[Connect Stripe/Bank]
    M --> N[Request Payout]
    N --> O[Payment Processed 3-5 Days]
```

## 10. Admin Dashboard Flow

```mermaid
flowchart TD
    A[Admin Login] --> B[Admin Dashboard]
    B --> C[User Management]
    B --> D[Mission Management]
    B --> E[Moderation Tools]
    B --> F[Analytics]
    B --> G[Payment Tracking]
    B --> H[System Health]
    
    C --> I[Search/Filter/View Profiles]
    C --> J[Suspend/Delete/Impersonate Users]
    
    D --> K[View All Missions]
    D --> L[Edit/Pause/Delete Missions]
    
    E --> M[Review Reported Messages]
    E --> N[Issue Warnings/Bans]
    
    F --> O[Live Analytics Dashboard]
    F --> P[User Sign-ups/Mission Creation/Matching Activity]
    
    G --> Q[View All Transactions]
    G --> R[Manual Refunds/Retry Payments]
    
    H --> S[Server Status/Error Logs/API Response Times]
```

## 11. Security & Anti-Leak System Flow

```mermaid
flowchart TD
    A[User Sends Message] --> B[Automatic Content Scan]
    B --> C{Contains Prohibited Content?}
    C -->|Email/Phone/External Links| D[Warning Popup]
    C -->|Clean Content| E[Message Delivered]
    D --> F[Log Violation]
    F --> G{Violation Count ≥ 3?}
    G -->|Yes| H[Auto-Flag User]
    G -->|No| I[Continue Monitoring]
    H --> J[Reduced Trust Score]
    J --> K[Admin Review Required]
    E --> L[Normal Communication Flow]
```

## 12. Complete User Journey Flow

```mermaid
flowchart TD
    A[User Visits Platform] --> B{New or Returning?}
    B -->|New| C[Sign Up Process]
    B -->|Returning| D[Login]
    
    C --> E{Role Selection}
    E -->|Entrepreneur| F[Create Business Profile]
    E -->|Freelancer| G[Create Freelancer Profile]
    
    F --> H[Post Mission]
    G --> I[Browse Missions]
    
    H --> J[Matching Engine Processes]
    I --> J
    
    J --> K[Matches Generated]
    K --> L{User Action}
    L -->|Entrepreneur| M[Review/Invite Freelancers]
    L -->|Freelancer| N[Apply to Missions]
    
    M --> O[Match Confirmed]
    N --> O
    
    O --> P[Messaging Enabled]
    P --> Q[Project Discussion]
    Q --> R[Payment Setup]
    R --> S[Work Begins]
    S --> T[Project Completion]
    T --> U[Payment Release]
    U --> V[Rating & Review]
    V --> W[End of Cycle]
```

## 13. Role Permission Matrix Flow

```mermaid
flowchart TD
    A[User Role Determined] --> B{Role Type}
    B -->|Entrepreneur| C[Entrepreneur Permissions]
    B -->|Freelancer| D[Freelancer Permissions]
    B -->|Admin| E[Admin Permissions]
    
    C --> F[Create Missions]
    C --> G[View Matches]
    C --> H[Send Invitations]
    C --> I[Make Payments]
    C --> J[Access Entrepreneur Dashboard]
    
    D --> K[Create Profile]
    D --> L[Apply to Missions]
    D --> M[Receive Invitations]
    D --> N[Receive Payments]
    D --> O[Access Freelancer Dashboard]
    
    E --> P[Full System Access]
    E --> Q[User Management]
    E --> R[Content Moderation]
    E --> S[Analytics Access]
    E --> T[Payment Management]
```