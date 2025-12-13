## ENUMS

```json
{
  "GroupType": ["church", "youth_group", "bible_study", "family", "prayer_group"],
  "GroupPrivacy": ["public", "private"],
  "GroupMemberRole": ["leader", "co_leader", "member"],
  "GroupInviteStatus": ["pending", "accepted", "declined", "expired", "seen", "cancelled"],
  "GroupAssignmentType": ["Quiz", "Quest"],
  "GroupAssignmentUserStatus": ["NotStarted", "InProgress", "Completed", "Abandoned"],
  "GroupAssignmentQuestionStatus": ["NotAnswered", "Answered", "Skipped"],
  "TimeLimitType": ["None", "TotalQuizTime", "PerQuestion"],
  "LeaderboardPeriod": ["week", "month", "all_time"]
}
```

<br />

## GROUPS - BASIC

> ### GET - /groups/my

User Action: _Fetch the groups the current user belongs to._

#### Query Params

```json
{
  "page": 1,
  "pageSize": 20,
  "sort": "-createdAt",
  "name": "",
  "type": ""
}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Groups fetched",
  "data": {
    "items": [
      {
        "id": "7f6c1b6c-1234-4d3b-9e2f-15c5c9a89a10",
        "name": "Downtown Bible Group",
        "description": "A community group studying the Bible weekly.",
        "iconPath": "group-bible",
        "type": "bible_study",
        "privacy": "public",
        "isArchived": false,
        "isBanned": false,
        "lastActivityAt": "2025-12-10T18:22:31.000Z",
        "memberCount": 14,
        "maxMembersCount": 50,
        "isLeader": true,
        "isMember": false,
        "createdAt": "2025-12-01T05:10:00.000Z",
        "updatedAt": "2025-12-10T18:22:31.000Z"
      }
    ],
    "total": 25,
    "page": 1,
    "pageSize": 20
  }
}
```

<br />

> ### GET - /groups/public

User Action: _List all public groups available to join._

#### Query Params

```json
{
  "page": 1,
  "pageSize": 20,
  "sort": "-createdAt",
  "name": "",
  "type": ""
}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Public groups fetched",
  "data": {
    "items": [
      {
        "id": "f5f7adad-2222-4f83-90b6-6e1c82c1c111",
        "name": "City Youth",
        "description": "Youth fellowship and study.",
        "iconPath": "group-people",
        "type": "youth_group",
        "privacy": "public",
        "isArchived": false,
        "isBanned": false,
        "lastActivityAt": "2025-12-09T14:00:00.000Z",
        "memberCount": 52,
        "maxMembersCount": 100,
        "isLeader": false,
        "isMember": false,
        "createdAt": "2025-11-15T08:00:00.000Z",
        "updatedAt": "2025-12-09T14:00:00.000Z"
      }
    ],
    "total": 150,
    "page": 1,
    "pageSize": 20
  }
}
```

<br />

> ### GET - /groups/{groupId}

User Action: _Fetch a specific group by id._

#### Query Params

```json
{}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Group fetched",
  "data": {
    "group": {
      "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
      "name": "Downtown Bible Group",
      "description": "A community group studying the Bible weekly.",
      "iconPath": "string",
      "type": "bible_study",
      "privacy": "public",
      "isArchived": false,
      "isBanned": false,
      "lastActivityAt": "2025-01-15T10:30:00.000Z",
      "memberCount": 25,
      "createdAt": "2025-01-15T10:30:00.000Z",
      "updatedAt": "2025-01-15T10:30:00.000Z"
    },
    "leader": {
      "id": "b2c3d4e5-f6a7-8901-bcde-f12345678901",
      "username": "john_doe",
      "name": "John Doe"
    },
    "isLeader": false,
    "isCoLeader": false
  }
}
```

<br />

> ### POST - /groups

User Action: _Create a new group._

#### Query Params

```json
{}
```

#### Request Body

```json
{
  "name": "Downtown Bible Group",
  "description": "A community group studying the Bible weekly.",
  "iconPath": "string",
  "type": "bible_study",
  "privacy": "public"
}
```

#### Response Body

```json
{
  "success": true,
  "message": "Group created",
  "data": {
    "id": "b0f5c8a2-5678-4d79-9123-7e2c1c7e8d9f",
    "name": "Downtown Bible Group",
    "description": "A community group studying the Bible weekly.",
    "iconPath": "group-bible",
    "type": "bible_study",
    "privacy": "public",
    "isArchived": false,
    "isBanned": false,
    "lastActivityAt": null,
    "memberCount": 1,
    "createdAt": "2025-12-10T18:22:31.000Z",
    "updatedAt": "2025-12-10T18:22:31.000Z"
  }
}
```

<br />

> ### POST - /groups/{groupId}/join

User Action: _Join a public group by id._

#### Query Params

```json
{}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Joined group",
  "data": {
    "groupId": "b0f5c8a2-5678-4d79-9123-7e2c1c7e8d9f",
    "memberCount": 12,
    "isReturningUser": false,
    "alreadyActive": false
  }
}
```

<br />

> ### POST - /groups/{groupId}/leave

User Action: _Leave a group by id._

#### Query Params

```json
{}
```

#### Request Body

```
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Left group",
  "data": {
    "groupId": "b0f5c8a2-5678-4d79-9123-7e2c1c7e8d9f",
    "memberCount": 11
  }
}
```

<br />

> ### PUT - /groups/{groupId}

Leader / Co-leader Action: _Update group details._

#### Query Params

```json
{}
```

#### Request Body

```json
{
  "name": "Downtown Bible Group",
  "description": "Updated description",
  "iconPath": "group-bible",
  "type": "church",
  "privacy": "private"
}
```

#### Response Body

```json
{
  "success": true,
  "message": "Group updated",
  "data": {
    "id": "b0f5c8a2-5678-4d79-9123-7e2c1c7e8d9f",
    "name": "Downtown Bible Group",
    "description": "Updated description",
    "iconPath": "group-bible",
    "type": "church",
    "privacy": "private",
    "isArchived": false,
    "isBanned": false,
    "lastActivityAt": "2025-12-10T19:00:00.000Z",
    "memberCount": 11,
    "createdAt": "2025-12-10T18:22:31.000Z",
    "updatedAt": "2025-12-10T19:00:00.000Z"
  }
}
```

<br />

> ### DELETE - /groups/{groupId}

Leader / Co-leader Action: _Delete a group._

#### Query Params

```json
{}
```

#### Request Body

```
{}
```

#### Response Body

```json
{
  "success": true,
  "deletedGroupId": "b0f5c8a2-5678-4d79-9123-7e2c1c7e8d9f"
}
```

<br />

## GROUPS - INVITATIONS

> ### GET - /groups/invites/my

User Action: _List invitations received by the current user._

#### Query Params

```json
{}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Invitations fetched successfully",
  "data": {
    "items": [
      {
        "id": "inv-123-456-789",
        "groupId": "group-123-456-789",
        "groupName": "Wednesday Night Study",
        "iconPath": "path/to/icon.png",
        "inviterName": "Rachel Martinez",
        "inviterId": "user-123-456",
        "category": "Bible study",
        "privacy": "private",
        "status": "pending",
        "createdAt": "2025-01-15T10:00:00.000Z",
        "updatedAt": "2025-01-15T10:00:00.000Z"
      }
    ],
    "total": 10,
    "page": 1,
    "pageSize": 20
  }
}
```

<br />

> ### GET - /groups/invites/{invitationId}

User Action: _Fetch a specific invitation by id._

#### Query Params

```json
{}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Invitation fetched successfully",
  "data": {
    "id": "inv-123-456-789",
    "groupId": "group-123-456-789",
    "groupName": "Wednesday Night Study",
    "iconPath": "path/to/icon.png",
    "inviterName": "Rachel Martinez",
    "inviterId": "user-123-456",
    "category": "Bible study",
    "privacy": "private",
    "status": "pending",
    "description": "A community group studying the Bible weekly.",
    "memberCount": 14,
    "createdAt": "2025-01-15T10:00:00.000Z",
    "updatedAt": "2025-01-15T10:00:00.000Z"
  }
}
```

<br />

> ### GET - /groups/{groupId}/users-for-invitation

Leader / Co-leader Action: _List users eligible to be invited to a specific group._

#### Query Params

```json
{
  "page": 1,
  "pageSize": 20,
  "sort": "-createdAt",
  "name": "",
  "username": ""
}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Users fetched successfully",
  "data": {
    "items": [
      {
        "id": "user-123-456-789",
        "name": "John Doe",
        "username": "johndoe",
        "email": "john.doe@example.com",
        "image": "https://example.com/profile.png",
        "isInvited": false
      }
    ],
    "total": 50,
    "page": 1,
    "pageSize": 20
  }
}
```

<br />

> ### POST - /groups/{groupId}/invites

Leader / Co-leader Action: _Create invitations for a specific group._

#### Query Params

```
{}
```

#### Request Body

```json
{
  "inviteeId": "9d2c7c59-aaaa-4b5b-b111-836d10fd0c11"
}
```

#### Response Body

```json
{
  "success": true,
  "message": "Invite created",
  "data": {
    "id": "4b5d7f5f-0a31-4c3a-93bc-7f1e1d5c1c44",
    "groupId": "b0f5c8a2-5678-4d79-9123-7e2c1c7e8d9f",
    "inviterId": "3b2a1c4d-5555-4b8e-9a77-0dc5f4b43111",
    "inviteeId": "9d2c7c59-aaaa-4b5b-b111-836d10fd0c11",
    "token": "6e6f0c7c-efad-4312-b109-0a0d9e3f5af9",
    "status": "pending",
    "createdAt": "2025-12-10T18:30:00.000Z",
    "respondedAt": null,
    "expiresAt": "2026-01-09T18:30:00.000Z"
  }
}
```

<br />

> ### POST - /groups/join

User Action: _Accept a group invitation or join via token._

#### Query Params

```json
{}
```

#### Request Body

```json
{
  "invitationId": "inv-123-456-789"
}
```

#### Response Body

```json
{
  "success": true,
  "message": "Successfully joined the group",
  "data": {
    "groupId": "group-123-456-789",
    "memberId": "member-123-456-789",
    "role": "member",
    "joinedAt": "2025-01-15T10:00:00.000Z"
  }
}
```

<br />

> ### POST - /groups/decline

User Action: _Decline/reject a pending group invitation._

#### Query Params

```json
{}
```

#### Request Body

```json
{
  "invitationId": "inv-123-456-789"
}
```

#### Response Body

```json
{
  "success": true,
  "message": "Invitation declined successfully",
  "data": {
    "invitationId": "inv-123-456-789",
    "status": "declined",
    "declinedAt": "2025-01-15T10:00:00.000Z"
  }
}
```

<br />

> ### POST - /groups/{groupId}/invites/{invitationId}/cancel

Leader / Co-leader Action: _Cancel a sent group invitation._

#### Query Params

```json
{}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Invitation cancelled successfully",
  "data": {
    "invitationId": "inv-123-456-789",
    "status": "cancelled",
    "cancelledAt": "2025-01-15T10:00:00.000Z"
  }
}
```

<br />

> ### POST - /groups/invites/{invitationId}/mark-as-seen

User Action: _Mark a group invitation as seen._

#### Query Params

```json
{}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Invitation marked as seen",
  "data": {
    "invitationId": "inv-123-456-789",
    "status": "seen",
    "seenAt": "2025-01-15T10:00:00.000Z"
  }
}
```

<br />

## GROUPS - ANNOUNCEMENTS

> ### GET - /groups/{groupId}/announcements

User Action: _List announcements for a group._

#### Query Params

```json
{
  "page": 1,
  "pageSize": 20,
  "sort": "-createdAt"
}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Announcements fetched",
  "data": {
    "items": [
      {
        "id": "2c3d4e5f-1111-4a4b-9c9d-2e3f4a5b6c7d",
        "groupId": "b0f5c8a2-5678-4d79-9123-7e2c1c7e8d9f",
        "authorId": "3b2a1c4d-5555-4b8e-9a77-0dc5f4b43111",
        "content": "Meeting moved to 7pm tonight.",
        "createdAt": "2025-12-10T18:40:00.000Z",
        "author": {
          "id": "3b2a1c4d-5555-4b8e-9a77-0dc5f4b43111",
          "username": "leader1",
          "name": "Leader Name"
        }
      }
    ],
    "total": 12,
    "page": 1,
    "pageSize": 20
  }
}
```

<br />

> ### GET - /groups/{groupId}/announcements/{announcementId}

User Action: _Fetch a single announcement by id._

#### Query Params

```json
{}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Announcement fetched",
  "data": {
    "id": "2c3d4e5f-1111-4a4b-9c9d-2e3f4a5b6c7d",
    "groupId": "b0f5c8a2-5678-4d79-9123-7e2c1c7e8d9f",
    "authorId": "3b2a1c4d-5555-4b8e-9a77-0dc5f4b43111",
    "content": "Meeting moved to 7pm tonight.",
    "createdAt": "2025-12-10T18:40:00.000Z",
    "author": {
      "id": "3b2a1c4d-5555-4b8e-9a77-0dc5f4b43111",
      "username": "leader1",
      "name": "Leader Name"
    }
  }
}
```

<br />

> ### POST - /groups/{groupId}/announcements

Leader / Co-leader Action: _Create a new announcement in a group._

#### Query Params

```json
{}
```

#### Request Body

```json
{
  "content": "Meeting moved to 7pm tonight."
}
```

#### Response Body

```json
{
  "success": true,
  "message": "Announcement created",
  "data": {
    "id": "2c3d4e5f-1111-4a4b-9c9d-2e3f4a5b6c7d",
    "groupId": "b0f5c8a2-5678-4d79-9123-7e2c1c7e8d9f",
    "authorId": "3b2a1c4d-5555-4b8e-9a77-0dc5f4b43111",
    "content": "Meeting moved to 7pm tonight.",
    "createdAt": "2025-12-10T18:40:00.000Z",
    "author": {
      "id": "3b2a1c4d-5555-4b8e-9a77-0dc5f4b43111",
      "username": "leader1",
      "name": "Leader Name"
    }
  }
}
```

<br />

## GROUPS - ASSIGNMENTS

> ### GET - /groups/{groupId}/assignments

User Action: _List assignments for a group._

#### Query Params

```json
{
  "page": 1,
  "pageSize": 20,
  "sort": "-createdAt"
}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Assignments fetched",
  "data": {
    "items": [
      {
        "id": "6a7b8c9d-2222-4a4b-9c9d-2e3f4a5b6c7d",
        "groupId": "b0f5c8a2-5678-4d79-9123-7e2c1c7e8d9f",
        "createdBy": "3b2a1c4d-5555-4b8e-9a77-0dc5f4b43111",
        "assignmentType": "Quiz",
        "quizTypeId": "8c9d0e1f-3333-4a4b-9c9d-2e3f4a5b6c7d",
        "questTypeId": null,
        "title": "Weekly Bible Quiz",
        "description": "Test your knowledge of this week's study",
        "dueDate": "2025-12-20T23:59:59.000Z",
        "isActive": true,
        "createdAt": "2025-12-10T18:50:00.000Z",
        "updatedAt": "2025-12-10T18:50:00.000Z",
        "quizType": {
          "id": "8c9d0e1f-3333-4a4b-9c9d-2e3f4a5b6c7d",
          "title": "Bible Study Quiz",
          "description": "Questions about this week's reading",
          "totalPoints": 100,
          "totalQuestions": 10,
          "timeLimitType": "TotalQuizTime",
          "timeLimitValue": 1800
        },
        "totalUsers": 15,
        "completedUsers": 8,
        "inProgressUsers": 3
      }
    ],
    "total": 5,
    "page": 1,
    "pageSize": 20
  }
}
```

<br />

> ### GET - /groups/{groupId}/assignments/{assignmentId}

User Action: _Fetch a specific assignment by id._

#### Query Params

```json
{}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Assignment fetched",
  "data": {
    "id": "6a7b8c9d-2222-4a4b-9c9d-2e3f4a5b6c7d",
    "groupId": "b0f5c8a2-5678-4d79-9123-7e2c1c7e8d9f",
    "createdBy": "3b2a1c4d-5555-4b8e-9a77-0dc5f4b43111",
    "assignmentType": "Quiz",
    "quizTypeId": "8c9d0e1f-3333-4a4b-9c9d-2e3f4a5b6c7d",
    "questTypeId": null,
    "title": "Weekly Bible Quiz",
    "description": "Test your knowledge of this week's study",
    "dueDate": "2025-12-20T23:59:59.000Z",
    "isActive": true,
    "createdAt": "2025-12-10T18:50:00.000Z",
    "updatedAt": "2025-12-10T18:50:00.000Z",
    "quizType": {
      "id": "8c9d0e1f-3333-4a4b-9c9d-2e3f4a5b6c7d",
      "title": "Bible Study Quiz",
      "description": "Questions about this week's reading",
      "totalPoints": 100,
      "totalQuestions": 10,
      "timeLimitType": "TotalQuizTime",
      "timeLimitValue": 1800
    },
    "totalUsers": 15,
    "completedUsers": 8,
    "inProgressUsers": 3
  }
}
```

<br />

> ### GET - /groups/{groupId}/assignments/{assignmentId}/progress

User Action: _Get progress for a specific assignment._

#### Query Params

```json
{}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "User assignments fetched",
  "data": [
    {
      "id": "9e0f1a2b-4444-4a4b-9c9d-2e3f4a5b6c7d",
      "assignmentId": "6a7b8c9d-2222-4a4b-9c9d-2e3f4a5b6c7d",
      "userId": "7f8g9h0i-5555-4a4b-9c9d-2e3f4a5b6c7d",
      "status": "Completed",
      "score": 85,
      "totalPoints": 100,
      "xpEarned": 85,
      "startedAt": "2025-12-11T10:00:00.000Z",
      "completedAt": "2025-12-11T10:25:00.000Z",
      "timeLimitType": "TotalQuizTime",
      "timeLimitValue": 1800,
      "expiresAt": "2025-12-11T10:30:00.000Z",
      "timeTakenSeconds": 1500,
      "questions": [
        {
          "id": "1a2b3c4d-6666-4a4b-9c9d-2e3f4a5b6c7d",
          "questionTypeId": "2b3c4d5e-7777-4a4b-9c9d-2e3f4a5b6c7d",
          "status": "Answered",
          "points": 10,
          "answeredAt": "2025-12-11T10:05:00.000Z",
          "answerData": {
            "selectedOptionIds": ["3c4d5e6f-8888-4a4b-9c9d-2e3f4a5b6c7d"]
          },
          "order": 0
        }
      ],
      "createdAt": "2025-12-11T10:00:00.000Z",
      "updatedAt": "2025-12-11T10:25:00.000Z",
      "user": {
        "id": "7f8g9h0i-5555-4a4b-9c9d-2e3f4a5b6c7d",
        "username": "member1",
        "name": "Member Name"
      }
    }
  ]
}
```

<br />

> ### GET - /groups/{groupId}/assignments/quizzes

User Action: _List quizzes available for assignments in the group._

#### Query Params

```json
{
  "page": 1,
  "pageSize": 20,
  "sort": "-createdAt",
  "title": "",
  "q": ""
}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Quizzes fetched successfully",
  "data": {
    "items": [
      {
        "quizTypeId": "8c9d0e1f-3333-4a4b-9c9d-2e3f4a5b6c7d",
        "title": "Bible Study Quiz",
        "description": "Questions about this week's reading",
        "totalPoints": 100,
        "totalQuestions": 10,
        "timeLimitType": "TotalQuizTime",
        "timeLimitValue": 1800,
        "createdAt": "2025-12-01T10:00:00.000Z",
        "updatedAt": "2025-12-01T10:00:00.000Z"
      }
    ],
    "total": 25,
    "page": 1,
    "pageSize": 20
  }
}
```

<br />

> ### POST - /groups/{groupId}/assignments

Leader / Co-leader Action: _Create a new assignment for a group._

#### Query Params

```json
{}
```

#### Request Body

```json
{
  "assignmentType": "Quiz",
  "quizTypeId": "8c9d0e1f-3333-4a4b-9c9d-2e3f4a5b6c7d",
  "title": "Weekly Bible Quiz",
  "description": "Test your knowledge of this week's study",
  "dueDate": "2025-12-20T23:59:59.000Z"
}
```

#### Response Body

```json
{
  "success": true,
  "message": "Assignment created",
  "data": {
    "id": "6a7b8c9d-2222-4a4b-9c9d-2e3f4a5b6c7d",
    "groupId": "b0f5c8a2-5678-4d79-9123-7e2c1c7e8d9f",
    "createdBy": "3b2a1c4d-5555-4b8e-9a77-0dc5f4b43111",
    "assignmentType": "Quiz",
    "quizTypeId": "8c9d0e1f-3333-4a4b-9c9d-2e3f4a5b6c7d",
    "questTypeId": null,
    "title": "Weekly Bible Quiz",
    "description": "Test your knowledge of this week's study",
    "dueDate": "2025-12-20T23:59:59.000Z",
    "isActive": true,
    "createdAt": "2025-12-10T18:50:00.000Z",
    "updatedAt": "2025-12-10T18:50:00.000Z",
    "quizType": {
      "id": "8c9d0e1f-3333-4a4b-9c9d-2e3f4a5b6c7d",
      "title": "Bible Study Quiz",
      "description": "Questions about this week's reading",
      "totalPoints": 100,
      "totalQuestions": 10,
      "timeLimitType": "TotalQuizTime",
      "timeLimitValue": 1800
    }
  }
}
```

<br />

## GROUPS - MEMBERS

> ### GET - /groups/{groupId}/members

User Action: _List members of a group._

#### Query Params

```json
{
  "page": 1,
  "pageSize": 20,
  "sort": "-createdAt",
  "role": "",
  "q": ""
}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Members fetched",
  "data": {
    "items": [
      {
        "id": "3b2a1c4d-5555-4b8e-9a77-0dc5f4b43111",
        "username": "leader1",
        "name": "Leader Name",
        "image": "https://example.com/profile.png",
        "role": "leader",
        "joinedAt": "2025-11-15T08:00:00.000Z"
      },
      {
        "id": "7f8g9h0i-5555-4a4b-9c9d-2e3f4a5b6c7d",
        "username": "coleader1",
        "name": "Co-Leader Name",
        "image": "https://example.com/profile2.png",
        "role": "co_leader",
        "joinedAt": "2025-11-20T10:00:00.000Z"
      },
      {
        "id": "9a0b1c2d-6666-4a4b-9c9d-2e3f4a5b6c7d",
        "username": "member1",
        "name": "Member Name",
        "image": "https://example.com/profile3.png",
        "role": "member",
        "joinedAt": "2025-12-01T14:00:00.000Z"
      }
    ],
    "total": 14,
    "page": 1,
    "pageSize": 20
  }
}
```

<br />

> ### POST - /groups/{groupId}/members/{userId}/promote-co-leader

Leader Action: _Promote a member to co-leader._

#### Query Params

```json
{}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Member promoted to co-leader",
  "data": {
    "groupId": "b0f5c8a2-5678-4d79-9123-7e2c1c7e8d9f",
    "userId": "9a0b1c2d-6666-4a4b-9c9d-2e3f4a5b6c7d",
    "role": "co_leader"
  }
}
```

<br />

> ### POST - /groups/{groupId}/members/{userId}/demote-co-leader

Leader Action: _Demote a co-leader back to member._

#### Query Params

```json
{}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Co-leader demoted to member",
  "data": {
    "groupId": "b0f5c8a2-5678-4d79-9123-7e2c1c7e8d9f",
    "userId": "7f8g9h0i-5555-4a4b-9c9d-2e3f4a5b6c7d",
    "role": "member"
  }
}
```

<br />

> ### POST - /groups/{groupId}/members/{userId}/ban

Leader / Co-leader Action: _Ban a member from the group._

#### Query Params

```json
{}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Member banned",
  "data": {
    "groupId": "b0f5c8a2-5678-4d79-9123-7e2c1c7e8d9f",
    "userId": "9a0b1c2d-6666-4a4b-9c9d-2e3f4a5b6c7d",
    "isBanned": true,
    "bannedAt": "2025-12-10T19:00:00.000Z"
  }
}
```

<br />

## GROUPS - LEADERBOARD

> ### GET - /groups/{groupId}/leaderboard

User Action: _Fetch the leaderboard for a group._

#### Query Params

```json
{
  "period": "all_time",
  "page": 1,
  "pageSize": 20,
  "sort": "-xp"
}
```

#### Request Body

```json
{}
```

#### Response Body

```json
{
  "success": true,
  "message": "Leaderboard fetched",
  "data": {
    "items": [
      {
        "userId": "3b2a1c4d-5555-4b8e-9a77-0dc5f4b43111",
        "username": "leader1",
        "name": "Leader Name",
        "image": "https://example.com/profile.png",
        "role": "leader",
        "xp": 1250,
        "rank": 1
      },
      {
        "userId": "7f8g9h0i-5555-4a4b-9c9d-2e3f4a5b6c7d",
        "username": "member1",
        "name": "Member Name",
        "image": "https://example.com/profile2.png",
        "role": "member",
        "xp": 980,
        "rank": 2
      },
      {
        "userId": "9a0b1c2d-6666-4a4b-9c9d-2e3f4a5b6c7d",
        "username": "member2",
        "name": "Another Member",
        "image": "https://example.com/profile3.png",
        "role": "co_leader",
        "xp": 750,
        "rank": 3
      }
    ],
    "total": 50,
    "page": 1,
    "pageSize": 20
  }
}
```
