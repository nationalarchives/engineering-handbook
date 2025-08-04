# YouTube

Do not embed YouTube videos into a page unless:

- You are embedding a link using the domain `youtube-nocookie.com` rather than `youtube.com` (this is **not** a silver bullet to make YouTube GDPR compliant)
- The user has accepted optional marketing cookies
- [CSP has been added to the site](../technology/standards/security.md#csp)

Until all these criteria have been met, simply display a link to the YouTube video. Once the user has accepted marketing cookies, you can replace the link with the embedded video player.

Use the chosen [video player](../technology/frontend/html.md#player) with YouTube videos.
