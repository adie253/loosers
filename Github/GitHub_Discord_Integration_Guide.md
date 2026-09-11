# GitHub + Discord Integration Guide

A simple step-by-step guide to connect a GitHub repository with a Discord channel and receive GitHub notifications.

---

# 1. What Are We Setting Up?

We want this:

```text
Developer
   |
   | git push
   v
GitHub Repository
   |
   | Webhook event
   v
Discord
   |
   v
#github channel
```

For example, when you push code:

```text
Aditya pushed 3 commits to main
```

Discord can show the notification automatically.

You can also receive notifications for:

- Pushes
- Pull Requests
- Issues
- Releases
- Workflow runs
- Branch/tag activity
- Other GitHub events

---

# 2. What Is a Webhook?

A webhook allows one application to send information to another application automatically.

In our case:

```text
GitHub = Sender
Discord = Receiver
```

When something happens on GitHub:

```text
New commit
New PR
New issue
New release
```

GitHub sends an HTTP request to Discord.

---

# 3. Recommended Discord Channel

Create a dedicated channel.

Example:

```text
📢 github
```

A small development server could look like:

```text
SERVER
│
├── 💬 general
├── 💻 development
├── 🐛 bugs
├── 🔀 pull-requests
└── 📢 github
```

For a small project, one `#github` channel is enough.

---

# 4. Create a Discord Webhook

Open your Discord server.

Go to:

```text
Server Settings
→ Integrations
→ Webhooks
```

Create a new webhook.

Give it a name:

```text
GitHub
```

Choose the channel:

```text
#github
```

Then click:

```text
Copy Webhook URL
```

The URL will look similar to:

```text
https://discord.com/api/webhooks/WEBHOOK_ID/WEBHOOK_TOKEN
```

IMPORTANT:

The webhook URL is a secret.

Do NOT:

- Post it publicly
- Put it in GitHub source code
- Put it in README files
- Share it in screenshots
- Commit it to Git

Anyone who has the webhook URL may be able to send messages to your Discord channel.

---

# 5. Connect Discord Webhook to GitHub

Open your GitHub repository.

Go to:

```text
Repository
→ Settings
→ Webhooks
→ Add webhook
```

You will see a form.

---

# 6. Payload URL

This is the MOST IMPORTANT PART.

For a Discord GitHub webhook, append:

```text
/github
```

to the Discord webhook URL.

Normal Discord webhook:

```text
https://discord.com/api/webhooks/WEBHOOK_ID/WEBHOOK_TOKEN
```

GitHub-compatible Discord webhook:

```text
https://discord.com/api/webhooks/WEBHOOK_ID/WEBHOOK_TOKEN/github
```

The final URL must end with:

```text
/github
```

Do not add spaces.

---

# 7. Content Type

Set:

```text
Content type:
application/json
```

This is important because GitHub sends the webhook payload as JSON.

---

# 8. Secret

For a basic Discord webhook integration, you can leave the GitHub webhook Secret field empty unless you are using a separate receiver/application that validates GitHub webhook signatures.

Do not put your Discord webhook token into GitHub's Secret field.

---

# 9. SSL Verification

Keep SSL verification enabled.

Use:

```text
Enable SSL verification
```

Do not disable SSL verification unless you have a specific reason and understand the security implications.

---

# 10. Which Events Should GitHub Send?

GitHub gives you different options.

You can initially choose:

```text
Send me everything
```

This is useful for testing.

Once the integration works, you can reduce the events.

For a normal development project, a good starting selection is:

```text
✓ Pushes
✓ Pull requests
✓ Issues
✓ Releases
✓ Workflow runs
```

You may add other events if your team needs them.

---

# 11. Recommended Setup

For our backend project:

```text
Payload URL:
https://discord.com/api/webhooks/WEBHOOK_ID/WEBHOOK_TOKEN/github

Content type:
application/json

SSL:
Enabled

Events:
Pushes
Pull requests
Issues
Releases
Workflow runs
```

Then click:

```text
Add webhook
```

or:

```text
Update webhook
```

depending on whether you are creating or editing it.

---

# 12. Test the Connection

After creating the webhook, GitHub usually sends a `ping` event.

Go to:

```text
Repository
→ Settings
→ Webhooks
→ Your webhook
→ Recent Deliveries
```

You may see:

```text
X-GitHub-Event: ping
```

Click the delivery.

Look at the response.

A successful request should return a successful HTTP response.

---

# 13. Important: 400 / 50006 Error

You may see:

```json
{
  "message": "Cannot send an empty message",
  "code": 50006
}
```

This generally means Discord received the request but did not get a usable message payload.

For GitHub → Discord direct webhooks, first check the Payload URL.

It should end with:

```text
/github
```

Correct:

```text
https://discord.com/api/webhooks/ID/TOKEN/github
```

Incorrect:

```text
https://discord.com/api/webhooks/ID/TOKEN
```

Also verify:

```text
Content-Type = application/json
```

---

# 14. Don't Rely Only on the Ping Test

The GitHub `ping` event is mainly a webhook connectivity test.

After fixing the configuration, perform a real GitHub action.

For example, make a small commit.

```bash
git add .
git commit -m "Test Discord integration"
git push
```

Then check your Discord channel.

You should see a GitHub notification.

---

# 15. Test a Push Notification

Example workflow:

```bash
git status

git add .

git commit -m "Test Discord notification"

git push
```

GitHub receives the push.

GitHub sends a webhook.

Discord receives it.

Discord posts in:

```text
#github
```

---

# 16. Test a Pull Request

Create a branch:

```bash
git switch -c feature/test-discord
```

Make a change.

Then:

```bash
git add .
git commit -m "Test pull request notification"
git push -u origin feature/test-discord
```

Open GitHub.

Create:

```text
feature/test-discord → main
```

Pull Request.

Discord should receive a PR notification if Pull Request events are enabled.

---

# 17. Test an Issue

Create a GitHub Issue:

```text
Title:
Test Discord integration

Description:
Testing GitHub issue notifications.
```

If Issues are enabled, Discord should receive the event.

---

# 18. Test a Release

Create a GitHub Release.

For example:

```text
v1.0.0
```

If Releases are enabled, Discord can receive the release notification.

---

# 19. GitHub Actions Notifications

If your repository uses GitHub Actions, you can also send workflow-related notifications.

Example:

```text
git push
   |
   v
GitHub Actions
   |
   +---- Build
   |
   +---- Test
   |
   +---- Deploy
```

You can configure workflow-related events depending on the notification behavior you want.

---

# 20. Understanding Recent Deliveries

GitHub's webhook page contains:

```text
Recent Deliveries
```

Each delivery represents a webhook request.

Useful information includes:

```text
Request URL
Request method
Content-Type
X-GitHub-Event
Payload
Response
```

For example:

```text
X-GitHub-Event: push
```

means GitHub sent a push event.

Another:

```text
X-GitHub-Event: pull_request
```

means a pull request event was sent.

---

# 21. Understanding HTTP Status Codes

Common results:

```text
2xx = generally successful
4xx = request/configuration problem
5xx = server-side problem
```

Examples:

```text
200 OK
201 Created
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
500 Internal Server Error
```

For your Discord webhook, if GitHub shows:

```text
Response 400
```

inspect the request and Discord response.

---

# 22. Troubleshooting Checklist

If Discord doesn't receive notifications, check these in order.

## Step 1

Check Payload URL.

It should end with:

```text
/github
```

## Step 2

Check Content Type:

```text
application/json
```

## Step 3

Check GitHub events.

Make sure the event you are testing is enabled.

For a push:

```text
Pushes
```

For a PR:

```text
Pull requests
```

## Step 4

Make a real test event.

Don't rely only on the ping event.

## Step 5

Check Recent Deliveries.

Look at:

```text
Request
Response
```

## Step 6

Check Discord.

Make sure the webhook points to the correct channel.

---

# 23. If You See "Cannot Send an Empty Message"

Error:

```json
{
  "message": "Cannot send an empty message",
  "code": 50006
}
```

Check:

```text
1. Payload URL ends with /github
2. Content type is application/json
3. Correct Discord webhook was copied
4. Webhook still exists in Discord
5. GitHub event is enabled
6. Test with a real push event
```

The first thing to check is the `/github` suffix.

---

# 24. If You See 404

A 404 can mean the webhook endpoint is no longer valid.

Possible causes:

- Discord webhook was deleted
- Wrong webhook URL
- URL was copied incorrectly
- Webhook token was regenerated/invalidated

Create a new Discord webhook and update GitHub if necessary.

---

# 25. If You See 401 or 403

Check:

- Discord webhook configuration
- GitHub permissions
- Whether the webhook is still valid
- Whether your repository/team policies restrict the action

Do not expose your webhook URL while troubleshooting.

---

# 26. If GitHub Shows 200 but Nothing Appears

If GitHub reports a successful response but you don't see a message:

Check:

```text
1. Correct Discord server
2. Correct Discord channel
3. Webhook still points to that channel
4. Discord channel permissions
5. Whether the event actually contains information Discord can display
6. Whether another integration/filter is involved
```

Also check Discord's server integration settings.

---

# 27. Regenerating a Leaked Webhook

If you accidentally expose the webhook URL:

Treat it as compromised.

Do not simply assume that deleting the message/screenshot makes the token safe.

Recommended approach:

```text
Delete/rotate the Discord webhook
        ↓
Create a new webhook
        ↓
Copy the new URL
        ↓
Update GitHub Payload URL
```

Never put the new webhook URL into your source code.

---

# 28. Webhook Security

A webhook URL is similar to a secret credential.

Do not store it like this:

```java
String webhook =
    "https://discord.com/api/webhooks/ID/TOKEN";
```

Do not put it in:

```text
GitHub README
Java source code
React source code
.env committed to Git
Screenshots
Public documentation
```

If your own application needs to use a webhook, store it as a secret/environment variable.

---

# 29. GitHub Repository Secrets

If you need to use a Discord webhook from GitHub Actions, use GitHub Actions Secrets instead of putting the URL directly in the workflow.

Concept:

```text
GitHub Secret
      |
      v
GitHub Actions
      |
      v
Discord Webhook
```

Example secret name:

```text
DISCORD_WEBHOOK_URL
```

The actual URL should remain hidden.

---

# 30. Direct GitHub → Discord vs GitHub Actions

There are two common approaches.

## Option A — GitHub Webhook

```text
GitHub
   ↓
Discord Webhook
```

Good for:

- Simple notifications
- Pushes
- PRs
- Issues
- Releases

## Option B — GitHub Actions

```text
GitHub
   ↓
GitHub Actions
   ↓
Custom logic
   ↓
Discord
```

Better when you want custom notifications.

For example:

```text
Build failed
Test failed
Deployment successful
Production deployment failed
```

For beginners, start with Option A.

---

# 31. Recommended Discord Structure for a Development Team

Example:

```text
MY PROJECT
│
├── 💬 general
│
├── 💻 development
│
├── 🐛 bugs
│
├── 🔀 pull-requests
│
└── 📢 github
```

Use:

```text
#github
```

for automated GitHub notifications.

Keep normal conversations out of that channel.

---

# 32. Example GitHub Notification Flow

Developer:

```bash
git add .
git commit -m "Add product API"
git push
```

GitHub:

```text
Push event
```

Webhook:

```text
GitHub → Discord
```

Discord:

```text
📢 GitHub

Aditya pushed commits to main

Add product API
Fix product validation
Add product repository
```

---

# 33. Pull Request Flow

Developer:

```bash
git switch -c feature/product-api
```

Write code.

```bash
git add .
git commit -m "Add product API"
git push -u origin feature/product-api
```

GitHub:

```text
Pull Request #12
feature/product-api → main
```

Discord:

```text
🔀 Pull Request #12

Add Product API
```

Team reviews the PR.

Then:

```text
Approved
   ↓
Merged
   ↓
Discord notification
```

---

# 34. Recommended Events for Our Project

For a Java + Spring Boot backend:

```text
✓ Pushes
✓ Pull requests
✓ Issues
✓ Releases
✓ Workflow runs
```

Later, depending on your workflow:

```text
✓ Deployments
✓ Deployment status
✓ Discussions
✓ Create/Delete
✓ Branch protection events
```

Don't enable every event permanently unless you actually need them.

Too many notifications can make the channel noisy.

---

# 35. Example Team Workflow

```text
Developer
    |
    v
Feature branch
    |
    v
Commit
    |
    v
Push
    |
    v
GitHub
    |
    +----> Discord: Push notification
    |
    v
Pull Request
    |
    +----> Discord: PR opened
    |
    v
Code Review
    |
    v
Approval
    |
    v
Merge
    |
    +----> Discord: PR merged
```

---

# 36. Recommended Setup for Our Backend Project

Our project can eventually look like:

```text
GitHub
│
├── main
├── feature/authentication
├── feature/products
├── feature/orders
└── feature/users
        |
        v
     Discord
        |
        └── #github
```

Notifications will help us know what is happening without constantly opening GitHub.

---

# 37. Quick Setup Checklist

Use this checklist:

```text
[ ] Create Discord #github channel
[ ] Create Discord webhook
[ ] Copy webhook URL
[ ] Keep webhook URL private
[ ] Open GitHub repository
[ ] Settings → Webhooks
[ ] Add webhook
[ ] Paste Discord URL
[ ] Append /github
[ ] Set application/json
[ ] Keep SSL verification enabled
[ ] Select required events
[ ] Save webhook
[ ] Check Recent Deliveries
[ ] Make a real test push
[ ] Confirm Discord notification
```

---

# 38. Final Configuration Example

Do NOT copy this exact URL.

Use your own Discord webhook:

```text
Payload URL:
https://discord.com/api/webhooks/YOUR_ID/YOUR_TOKEN/github

Content type:
application/json

SSL verification:
Enabled

Events:
Pushes
Pull requests
Issues
Releases
Workflow runs
```

---

# 39. Final Mental Model

Remember:

```text
Discord Webhook
    =
A special URL that accepts messages/events

GitHub Webhook
    =
GitHub sending event information to a URL

GitHub → Discord
    =
GitHub sends repository events to Discord
```

The most important configuration for direct GitHub → Discord integration is:

```text
Discord Webhook URL
        +
      /github
```

Example:

```text
https://discord.com/api/webhooks/ID/TOKEN/github
```

---

# 40. When You Are Ready for Advanced Notifications

Once basic notifications work, you can build a more advanced setup:

```text
GitHub
   |
   +--> Push
   +--> Pull Request
   +--> Issue
   +--> CI/CD
   +--> Deployment
          |
          v
      Notification
          |
          v
       Discord
```

You can then create separate notifications for:

```text
✅ Build passed
❌ Build failed
🚀 Deployment successful
🔥 Production deployment failed
🔀 PR opened
✅ PR merged
🐛 New bug
```

At that point, GitHub Actions or a small backend service can provide more customized messages.

---

# 41. What to Learn Next

After setting up GitHub + Discord, learn:

```text
Git
 ↓
GitHub
 ↓
Branches
 ↓
Pull Requests
 ↓
Code Reviews
 ↓
GitHub Actions
 ↓
CI/CD
 ↓
Docker
 ↓
Deployment
```

For our Java + Spring Boot project, this will eventually become:

```text
React
   ↓
Spring Boot
   ↓
PostgreSQL
   ↓
GitHub
   ↓
GitHub Actions
   ↓
Docker
   ↓
AWS

GitHub events
   ↓
Discord
```

This is a useful foundation for working like a real development team.
