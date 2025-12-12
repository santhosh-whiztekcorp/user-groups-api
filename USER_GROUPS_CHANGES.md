## GROUPS - BASIC

> ### GET - /groups/my

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

**Request Body:**

1. **Change these properties:**
   - `imageUrl` → `iconPath` - Change from URL string to string (references file path in frontend)

<br />

> ### POST - /groups/{groupId}/join

<br />

> ### POST - /groups/{groupId}/leave

<br />

> ### PUT - /groups/{groupId}

<br />

> ### DELETE - /groups/{groupId}

<br />

## GROUPS - INVITATIONS

> ### GET - /groups/invites/my

This endpoint needs to be implemented

<br />

> ### GET - /groups/{groupId}/users-for-invitation

This endpoint needs to be implemented

<br />

> ### POST - /groups/{groupId}/invites

<br />

> ### POST - /groups/join

This endpoint needs to be implemented

<br />

> ### POST - /groups/decline

This endpoint needs to be implemented

<br />

> ### POST - /groups/{groupId}/invites/{invitationId}/cancel

This endpoint needs to be implemented

<br />

> ### POST - /groups/invites/{invitationId}/mark-as-seen

This endpoint needs to be implemented

<br />

## GROUPS - ANNOUNCEMENTS

> ### GET - /groups/{groupId}/announcements

<br />

> ### GET - /groups/{groupId}/announcements/{announcementId}

<br />

> ### POST - /groups/{groupId}/announcements

<br />

## GROUPS - ASSIGNMENTS

> ### GET - /groups/{groupId}/assignments

<br />

> ### GET - /groups/{groupId}/assignments/{assignmentId}

<br />

> ### GET - /groups/{groupId}/assignments/{assignmentId}/progress

<br />

> ### GET - /groups/{groupId}/assignments/quizzes

This endpoint needs to be implemented

<br />

> ### POST - /groups/{groupId}/assignments

<br />

## GROUPS - MEMBERS

> ### GET - /groups/{groupId}/members

<br />

> ### POST - /groups/{groupId}/members/{userId}/promote-co-leader

<br />

> ### POST - /groups/{groupId}/members/{userId}/demote-co-leader

<br />

> ### POST - /groups/{groupId}/members/{userId}/ban

<br />

## GROUPS - LEADERBOARD

> ### GET - /groups/{groupId}/leaderboard
