## GROUPS - BASIC

> ### GET - /groups/{groupId}

User Action: _Fetch a specific group by id._

**Response Body:**

1. **Missing these properties:**
   - `isLeader` → **Is Leader flag** (Boolean indicating if current user is the leader of this group)
   - `isCoLeader` → **Is Co-Leader flag** (Boolean indicating if current user is a co-leader of this group)

<br />

## GROUPS - INVITATIONS

> ### GET - /groups/invites/{invitationId}

User Action: _Fetch a specific invitation by id._

**Note:** Backend has a separate path `/groups/:groupId/invites/:inviteId` but it does not return the required response structure.

**Response Body:**

1. **Missing these properties:**
   - `groupName` → **Group name**
   - `iconPath` → **Icon file path** (references file path in frontend)
   - `inviterName` → **Name of the user who sent the invitation**
   - `category` → **Category/tag** (e.g., "Bible study")
   - `privacy` → **Privacy status** ("public" or "private")
   - `description` → **Group description**
   - `memberCount` → **Current number of members in the group**

<br />

## GROUPS - MEMBERS

> ### POST - /groups/{groupId}/members/{userId}/remove

Leader / Co-leader Action: _Remove a member from the group (soft remove - can rejoin later)._

**Status:** This endpoint is not implemented in the backend.

**Required Implementation:**

The backend needs to implement this endpoint with the following specifications:

- **Path:** `/groups/:groupId/members/:userId/remove`
- **Method:** POST
- **Query Params:** None (empty object)
- **Request Body:** None (empty object)
- **Response Body:**
  ```json
  {
    "success": true,
    "message": "Member removed",
    "data": {
      "groupId": "b0f5c8a2-5678-4d79-9123-7e2c1c7e8d9f",
      "userId": "9a0b1c2d-6666-4a4b-9c9d-2e3f4a5b6c7d",
      "memberCount": 13
    }
  }
  ```

**File Locations for Implementation:**

- `backend/src/modules/group/management/group.management.schema.ts` (add schema)
- `backend/src/modules/group/management/group.management.service.ts` (add service function)
- `backend/src/modules/group/management/group.management.controller.ts` (add controller)
- `backend/src/modules/group/management/group.management.routes.ts` (add route)
