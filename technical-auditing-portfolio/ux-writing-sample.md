markdown \# UX Writing Improvement: Login Error States *Goal: Reduce
user frustration and support tickets by clarifying error messages.*

## The Problem

The current app displays a generic "Error 401" when a login fails. This
leaves users confused about whether they got their password wrong or if
the server is down.

### Before (System-Centric)

> **Headline:** Error 401 **Body:** Unauthorized access. Please check
> credentials or contact sys-admin. **Button:** OK

------------------------------------------------------------------------

## The Solution (User-Centric)

I redesigned the copy to be helpful, conversational, and actionable.

### After (My Redesign)

> **Headline:** We couldn't sign you in **Body:** That password doesn't
> match our records. You can try again or reset it if you've forgotten
> it. **Primary Button:** Try Again **Secondary Link:** Reset Password

## Why This Works

1.  **Empathy:** Replaced "Unauthorized" (which sounds like an
    accusation) with "We couldn't sign you in."
2.  **Clarity:** Specifically identifies that the *password* is the
    likely issue.
3.  **Next Steps:** Provides a direct link to "Reset Password" so the
    user isn't stuck.
