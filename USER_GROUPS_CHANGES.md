## ENUMS

**GroupInviteStatus:**

Add these new enum values:

- `"seen"` → Status when invitation has been seen by the user
- `"cancelled"` → Status when invitation has been cancelled by leader/co-leader

<br />

## GROUPS - BASIC

> ### GET - /groups/my

User Action: _Fetch the groups the current user belongs to._

**Query Params:**

1. **Add these new properties:**
   - `page` → **Page Number** (default: 1)
   - `pageSize` → **Page Size** (default: 20)
   - `sort` → **Sort Order** (default: "-createdAt")
   - `name` → **Filter by group name**
   - `type` → **Filter by group type**

**Response Body:**

1. **Change from array to paginated object structure:**

   - `items` - Array of groups
   - `total` - Total number of groups
   - `page` - Current page number
   - `pageSize` - Items per page

2. **Add these new properties:**
   - `maxMembersCount` → **Maximum Members Count**
   - `isLeader` → **Is Leader flag** (Boolean indicating if current user is the leader)

<br />

> ### GET - /groups/public

User Action: _List all public groups available to join._

**Query Params:**

1. **Add these new properties:**
   - `page` → **Page Number** (default: 1)
   - `pageSize` → **Page Size** (default: 20)
   - `sort` → **Sort Order** (default: "-createdAt")
   - `name` → **Filter by group name**
   - `type` → **Filter by group type**

**Response Body:**

1. **Change from array to paginated object structure:**

   - `items` - Array of groups
   - `total` - Total number of groups
   - `page` - Current page number
   - `pageSize` - Items per page

2. **Add these new properties:**
   - `maxMembersCount` → **Maximum Members Count**
   - `isLeader` → **Is Leader flag** (Boolean indicating if current user is the leader, typically false for public groups)

<br />

> ### POST - /groups

User Action: _Create a new group._

**Request Body:**

1. **Change these properties:**
   - `imageUrl` → `iconPath` - Change from URL string to string (references file path in frontend)

<br />

## GROUPS - INVITATIONS

> ### GET - /groups/invites/my

User Action: _List invitations received by the current user._

This endpoint needs to be implemented

**Response Body:**

Add paginated response structure:

- `items` - Array of invitation objects
- `total` - Total number of invitations
- `page` - Current page number
- `pageSize` - Items per page

Add these properties to each invitation item:

- `id` → Invitation ID
- `groupId` → Group ID
- `groupName` → Group name
- `iconPath` → Icon file path (string)
- `inviterName` → Name of the user who sent the invitation
- `inviterId` → ID of the user who sent the invitation
- `category` → Category/tag (e.g., "Bible study")
- `privacy` → Privacy status ("private" or "public")
- `status` → Invitation status (e.g., "pending", "seen", "accepted", "declined", "cancelled", "expired")
- `createdAt` → Timestamp when invitation was created
- `updatedAt` → Timestamp when invitation was last updated

<br />

> ### GET - /groups/{groupId}/users-for-invitation

Leader / Co-leader Action: _List users eligible to be invited to a specific group._

This endpoint needs to be implemented

**Query Params:**

Add these new properties:

- `page` → Page Number (default: 1)
- `pageSize` → Page Size (default: 20)
- `sort` → Sort Order (default: "-createdAt")
- `name` → Filter by user name
- `username` → Filter by username

**Response Body:**

Add paginated response structure:

- `items` - Array of user objects
- `total` - Total number of users
- `page` - Current page number
- `pageSize` - Items per page

Add these properties to each user item:

- `id` → User ID
- `name` → User's full name
- `username` → User's username
- `email` → User's email address
- `image` → User's profile image URL

<br />

> ### POST - /groups/join

User Action: _Accept a group invitation or join via token._

This endpoint needs to be implemented

**Request Body:**

Add these properties:

- `invitationId` → Invitation ID to accept

**Response Body:**

Add these properties:

- `success` → Boolean indicating success
- `message` → Success message
- `data` → Object containing:
  - `groupId` → Group ID that was joined
  - `memberId` → Member ID created
  - `role` → User's role in the group (e.g., "member")
  - `joinedAt` → Timestamp when user joined

<br />

> ### POST - /groups/decline

User Action: _Decline/reject a pending group invitation._

This endpoint needs to be implemented

**Request Body:**

Add these properties:

- `invitationId` → Invitation ID to decline

**Response Body:**

Add these properties:

- `success` → Boolean indicating success
- `message` → Success message
- `data` → Object containing:
  - `invitationId` → Invitation ID that was declined
  - `status` → Status of invitation (e.g., "declined")
  - `declinedAt` → Timestamp when invitation was declined

<br />

> ### POST - /groups/{groupId}/invites/{invitationId}/cancel

Leader / Co-leader Action: _Cancel a sent group invitation._

This endpoint needs to be implemented

**Response Body:**

Add these properties:

- `success` → Boolean indicating success
- `message` → Success message
- `data` → Object containing:
  - `invitationId` → Invitation ID that was cancelled
  - `status` → Status of invitation (e.g., "cancelled")
  - `cancelledAt` → Timestamp when invitation was cancelled

<br />

> ### POST - /groups/invites/{invitationId}/mark-as-seen

User Action: _Mark a group invitation as seen._

This endpoint needs to be implemented

**Response Body:**

Add these properties:

- `success` → Boolean indicating success
- `message` → Success message
- `data` → Object containing:
  - `invitationId` → Invitation ID that was marked as seen
  - `status` → Status of invitation (set to "seen")
  - `seenAt` → Timestamp when invitation was marked as seen

<br />

## GROUPS - ANNOUNCEMENTS

> ### GET - /groups/{groupId}/announcements

User Action: _List announcements for a group._

**Query Params:**

Add these new properties:

- `page` → Page Number (default: 1)
- `pageSize` → Page Size (default: 20)
- `sort` → Sort Order (default: "-createdAt")

**Response Body:**

Change from array to paginated object structure:

- `items` - Array of announcements
- `total` - Total number of announcements
- `page` - Current page number
- `pageSize` - Items per page

<br />

## GROUPS - ASSIGNMENTS

> ### GET - /groups/{groupId}/assignments

User Action: _List assignments for a group._

**Query Params:**

Add these new properties:

- `page` → Page Number (default: 1)
- `pageSize` → Page Size (default: 20)
- `sort` → Sort Order (default: "-createdAt")

**Response Body:**

Change from array to paginated object structure:

- `items` - Array of assignments
- `total` - Total number of assignments
- `page` - Current page number
- `pageSize` - Items per page

<br />

> ### GET - /groups/{groupId}/assignments/quizzes

User Action: _List quizzes available for assignments in the group._

This endpoint needs to be implemented

**Query Params:**

Add these new properties:

- `page` → Page Number (default: 1)
- `pageSize` → Page Size (default: 20)
- `sort` → Sort Order (default: "-createdAt")
- `title` → Filter by quiz title
- `q` → Search query for quiz title/description

**Response Body:**

Add paginated response structure:

- `items` - Array of quiz objects
- `total` - Total number of quizzes
- `page` - Current page number
- `pageSize` - Items per page

Add these properties to each quiz item:

- `quizTypeId` → Quiz Type ID
- `title` → Quiz title
- `description` → Quiz description
- `totalPoints` → Total points available in the quiz
- `totalQuestions` → Total number of questions in the quiz
- `timeLimitType` → Time limit type (e.g., "TotalQuizTime", "PerQuestion", "None")
- `timeLimitValue` → Time limit value in seconds (if applicable)
- `createdAt` → Timestamp when quiz was created
- `updatedAt` → Timestamp when quiz was last updated

<br />

## GROUPS - MEMBERS

> ### GET - /groups/{groupId}/members

User Action: _List members of a group._

**Query Params:**

Add these new properties:

- `page` → Page Number (default: 1)
- `pageSize` → Page Size (default: 20)
- `sort` → Sort Order (default: "-createdAt")
- `role` → Filter by member role
- `q` → Search query for member name/username

**Response Body:**

Change from array to paginated object structure:

- `items` - Array of members
- `total` - Total number of members
- `page` - Current page number
- `pageSize` - Items per page

Add these properties to each member item:

- `image` → User's profile image URL
- `joinedAt` → Timestamp when user joined the group

<br />

## GROUPS - LEADERBOARD

> ### GET - /groups/{groupId}/leaderboard

User Action: _Fetch the leaderboard for a group._

**Query Params:**

Add these new properties:

- `page` → Page Number (default: 1)
- `pageSize` → Page Size (default: 20)
- `sort` → Sort Order (default: "-xp")

**Response Body:**

Change from `entries` array to paginated object structure:

- `items` - Array of leaderboard entries (renamed from `entries`)
- `total` - Total number of entries
- `page` - Current page number
- `pageSize` - Items per page

Add these properties to each leaderboard entry:

- `image` → User's profile image URL
- `role` → User's role in the group (e.g., "leader", "co_leader", "member")
