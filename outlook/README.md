# Outlook

Search and read Outlook mail, download attachments, create drafts, and organize messages through Microsoft Graph.

Install this package in opencompany and connect your Microsoft account in the plugin's settings.
Work/school and personal Outlook accounts are supported. Organizations that restrict user consent
may require administrator approval. Every capability starts in `ask` mode.

Mail is drafts-only: there is no send tool or `Mail.Send` permission. Open saved drafts in Outlook
to review and send them. Moving a message may change its id; use the returned id afterward.
Trash moves messages to Deleted Items and does not permanently delete them. Categories are set
by display name on messages; managing the master category list is outside this package.
File attachment downloads are limited to 20 MB and use private links that expire after five minutes.
Embedded Outlook items and reference attachments are not downloadable.
