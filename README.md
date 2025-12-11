# API Request Changes of User Groups

## GET: /groups/my

### Parameters:

- `page` (optional, number)
- `pageSize` (optional, number)

### Response:

```json
{
  "items": [
    {
      "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
      "name": "Downtown Bible Group",
      "description": "A community group studying the Bible weekly.",
      "imageUrl": "https://example.com/image.png",
      "type": "bible_study",
      "privacy": "public",
      "isArchived": false,
      "isBanned": false,
      "lastActivityAt": "2025-01-15T10:30:00.000Z",
      "memberCount": 25,
      "maxMembers": 300,
      "isLeader": true,
      "createdAt": "2025-01-15T10:30:00.000Z",
      "updatedAt": "2025-01-15T10:30:00.000Z"
    }
  ],
  "page": 1,
  "pageSize": 20,
  "total": 1,
  "totalPages": 1
}
```

---

## GET: /groups/public

### Parameters:

- `name` (optional, string)
- `type` (optional, string: `'church' | 'youth_group' | 'bible_study' | 'family' | 'prayer_group'`)
- `page` (optional, number)
- `pageSize` (optional, number)

### Response:

```json
{
  "items": [
    {
      "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
      "name": "Downtown Bible Group",
      "description": "A community group studying the Bible weekly.",
      "imageUrl": "https://example.com/image.png",
      "type": "bible_study",
      "privacy": "public",
      "isArchived": false,
      "isBanned": false,
      "lastActivityAt": "2025-01-15T10:30:00.000Z",
      "memberCount": 25,
      "maxMembers": 300,
      "isLeader": true,
      "createdAt": "2025-01-15T10:30:00.000Z",
      "updatedAt": "2025-01-15T10:30:00.000Z"
    }
  ],
  "page": 1,
  "pageSize": 20,
  "total": 1,
  "totalPages": 1
}
```

---

## GET: /groups/invites/my

### Parameters:

- `page` (optional, number)
- `pageSize` (optional, number)

### Response:

```json
{
  "items": [
    {
      "id": "b2c3d4e5-f6a7-8901-bcde-f12345678901",
      "groupId": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
      "inviterId": "c3d4e5f6-a7b8-9012-cdef-123456789012",
      "inviterName": "John Doe",
      "inviteeId": "d4e5f6a7-b8c9-0123-def0-234567890123",
      "token": "e5f6a7b8-c9d0-1234-ef01-345678901234",
      "status": "pending",
      "groupPrivacy": "public",
      "createdAt": "2025-01-15T10:30:00.000Z",
      "respondedAt": null,
      "expiresAt": "2025-02-14T10:30:00.000Z",
      "seenAt": "2025-01-15T11:00:00.000Z"
    }
  ],
  "page": 1,
  "pageSize": 20,
  "total": 1,
  "totalPages": 1
}
```

---

## POST: /groups

> **Note:** Needs to change the imageUrl type to string for uri

---


## POST: /groups/invites/decline

### Request Body:

```json
{
  "token": "e5f6a7b8-c9d0-1234-ef01-345678901234"
}
```

### Request Body Schema:

- `token` (required, string, valid UUID v4)

### Response:

```json
{
  "inviteId": "b2c3d4e5-f6a7-8901-bcde-f12345678901",
  "status": "declined"
}
```

### Response Schema:

- `inviteId` (string, UUID)
- `status` (string, always `'declined'`)

---

## POST: /groups/invites/seen

### Request Body:

```json
{
  "token": "e5f6a7b8-c9d0-1234-ef01-345678901234"
}
```

### Request Body Schema:

- `token` (required, string, valid UUID v4)

### Response:

```json
{
  "inviteId": "b2c3d4e5-f6a7-8901-bcde-f12345678901",
  "seenAt": "2025-01-15T10:30:00.000Z"
}
```

### Response Schema:

- `inviteId` (string, UUID)
- `seenAt` (string, ISO 8601 datetime)

### Description:

Marks an invitation as seen when a user views the individual invitation page. This tracks whether the user has viewed the invitation, regardless of whether they accept or decline it.
