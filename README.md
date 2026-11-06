# Bagara Games: test prototypes

Two QR games for Bagara Biryani Cafe, played while customers wait for the bill. Each one takes about a minute: three questions, an optional selfie, and a shareable card at the end.

| Folder | Game | Card |
|---|---|---|
| `pot/` | **What's your Bagara?** Answers cook a biryani layer by layer; the selfie "seals the dum". | Biryani card with the customer's pot and personality |
| `talkies/` | **Bagara Talkies.** Filmy fusion (Telugu, Kannada, Hindi, English). Three scenes and a hero shot. | Movie poster with the customer's dialogue as a subtitle |

`index.html` at the root links to both.

## Putting it on a site

These are plain static files with no build step and no server code. Each game is a single `index.html`.

- Copy the folders to any web host, for example as `/bagara/pot/` and `/bagara/talkies/`.
- **HTTPS is required.** Phones only allow the in-page camera on secure pages.
- Fonts load from Google Fonts; nothing else is loaded from outside.
- Each QR code should point straight to one game's URL.

## What works in this test

- All questions, sounds (tap to play), drag and tap interactions
- Live selfie inside the page with a 3-2-1 countdown and a white screen flash for low light. If the camera is blocked, it falls back to the phone's camera app, and the customer can also skip the photo.
- The card is generated on the phone (1080 × 1350 PNG) from the customer's answers and photo
- Share opens the phone's share sheet (WhatsApp, Instagram and so on) with the card image; Save downloads it

## What is only shown, not working yet

- **WhatsApp number and opt-in:** the form validates the number but does not save or send it.
- **Sealed fortune and the pot or poster collection:** these show what a return visit will look like, but nothing is stored, so a second visit isn't recognised yet.
- No customer data leaves the phone. Photos are not uploaded.

## What the real build needs

1. Save the number, first name and consent (offers opt-in kept separate and unticked by default), with a way to delete on request.
2. Send the card on WhatsApp (WhatsApp Business API), with SMS as a fallback.
3. Store each play against the number: answers, persona and date, so a return visit can unlock the sealed fortune and add the next pot or poster.
4. Optional reward slot on the come-back page (for example on the 5th visit), switched on only once the restaurant approves an offer.
5. One QR per outlet (or per table) so plays can be counted by outlet.
6. A simple dashboard for the owner: scans, completed games, shares, numbers collected and repeat visits.

## Before showing it to the public

- Have a native Telugu, Kannada and Hindi speaker check every line in `talkies/`.
- Test on a low-end Android phone and an iPhone, in restaurant lighting.
