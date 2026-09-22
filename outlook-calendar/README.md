# Outlook Calendar

Read Microsoft calendars, check availability, manage events, and respond to meeting invitations through Microsoft Graph.

Install this package in opencompany and connect your Microsoft account in the plugin's settings.
Work/school and personal Outlook accounts are supported. Organizations that restrict user consent
may require administrator approval. Every capability starts in `ask` mode.

Calendar views and your own availability work for both account types. Microsoft Graph's
`get_schedule` endpoint supports Microsoft 365 colleagues and resources only; personal users use
`check_availability`. Availability is for the selected calendar and is never reported as complete
until all pages have been read. Query windows are limited to 31 days.

Create timed events, update individual events or recurring occurrences, delete events, and respond
to invitations. Creating all-day or recurring events and changing an entire recurring series are
outside this version. Adding attendees sends invitations; deleting organizer events sends cancellations.
