# CytoDirect Companion PWA

A fully working Progressive Web App — your personal specialist, accessible via QR code.

---

## How to deploy (3 minutes)

### Option A — Netlify (recommended, free)
1. Go to netlify.com → drop the `/cytodirect-companion` folder onto the deploy area
2. You get a URL like `https://your-name.netlify.app`
3. Done. QR codes work immediately.

### Option B — GitHub Pages
1. Create a new GitHub repo, upload the files
2. Go to Settings → Pages → Deploy from main branch
3. URL: `https://yourusername.github.io/cytodirect-companion`

### Option C — Any static host
Upload `index.html` and `manifest.json` to any static hosting service.

---

## QR Code URL parameters

Personalise the experience by adding parameters to the URL:

| Parameter | Values | Effect |
|-----------|--------|--------|
| `focus` | `gmp` or `academic` | Selects Sara (GMP/BioPharma) or Erik (Academic) |
| `name` | Any first name | Specialist greets the user by name |
| `context` | Brief description | Added to Sara/Erik's context about this user |

### Example QR URLs

**For a BioPharma researcher at a QA evaluation stage:**
```
https://your-url.netlify.app/?focus=gmp&name=Sarah&context=CHO%20cells%2C%20GMP%20environment%2C%20QA%20review%20this%20week
```

**For an academic researcher exploring T-cell applications:**
```
https://your-url.netlify.app/?focus=academic&name=Magnus&context=Primary%20T-cells%2C%20Karolinska%2C%20grant%20application
```

**Generic — no personalisation:**
```
https://your-url.netlify.app/
```

---

## Generate a QR code

Use any QR generator with the URL above:
- qr-code-generator.com
- qrcode.me
- Or in Keynote/PowerPoint: Insert → QR Code

For the workshop / presentation, generate two QR codes — one for each case (Sarah = GMP focus, Magnus = Academic focus) — and place them in the companion app section of your deck.

---

## API Key

On first launch, the user is asked to enter an Anthropic API key (`sk-ant-api03-...`).

For a demo where you control the device:
- Enter your key once — it saves to localStorage
- All subsequent opens skip the setup screen

For a public demo (e.g. on a shared device):
- Consider hardcoding the key in the HTML for demo purposes only
- Find `const API_KEY = ''` in the script and set it to your key
- Remove the setup screen block from the HTML

---

## What the app does

- **Conversation tab**: Real AI chat via Anthropic Claude, with Sara or Erik as the specialist persona
- **Resources tab**: Curated documents relevant to the user's context — click any to open full content
- **Specialist tab**: Profile of Sara or Erik, their expertise, and their approach
- **Persistent memory**: Conversation is saved to localStorage — comes back exactly where it left off
- **Installable**: Works as a PWA — users can add to home screen on iOS/Android

---

## Customisation

To adjust what Sara or Erik knows, edit the `sysPrompt` function in the specialists config.
To add resources, add objects to the `resources` array in the relevant specialist config.
To change the visual theme, edit the CSS variables at the top of the `<style>` block.
