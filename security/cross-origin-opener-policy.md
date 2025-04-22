# Cross Origin Opener Policy

**Cross Origin Opener Policy** - Determines whether or not a new window opened by the current window is considered to be part of the same context group.

Directives
`unsafe-none` - any window opened will share javascript context
`same-origin` - windows can share context if they have the same origin (both come from youtube.com)
`same-origin-allow-popups` - you can open a popup window given that the new window has unsafe-none set for their COOP
`noopener-allow-popups` - even if they have same origin, the new window will be seperate from the old one.

### Sources

[MDN: COOP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Cross-Origin-Opener-Policy)
