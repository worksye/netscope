# NetScope

**NetScope** is a lightweight, bilingual (Persian/English) IP and network engineering dashboard built with HTML, CSS, and vanilla JavaScript. It is designed for static hosting and GitHub Pages.

## Features

- Public IPv4 retrieval and best-effort IPv6 endpoint check
- IP metadata lookup: country, region, city, timezone, ISP/organization, ASN, and approximate coordinates when provided
- IPv4 and IPv6 input validation
- Basic special-purpose address classification
- IPv4 CIDR subnet calculator, including `/31` and `/32`
- Browser online/offline status
- Honest diagnostics for DNS, WebRTC, and VPN/proxy limitations
- Local lookup history with deletion and JSON export
- JSON export for current IP and lookup results
- Copy-to-clipboard actions
- Light corporate theme and optional dark theme
- Persian RTL and English LTR interface
- Optional automatic refresh
- Responsive desktop, tablet, and mobile layout
- No backend, build process, or framework required

## Quick start

Because this project uses JavaScript ES modules, serve it over HTTP instead of opening `index.html` with `file://`.

For example, if Python is installed:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000/NetScope/` if serving the parent directory, or `http://localhost:8000/` if serving the project directory itself.

## GitHub Pages deployment

1. Create a GitHub repository, for example `netscope`.
2. Upload all files in this project to the repository root.
3. Open **Settings → Pages**.
4. Under the build/deployment source, choose **Deploy from a branch**.
5. Select your default branch and `/ (root)`, then save.
6. Wait for GitHub Pages to publish the site.

All assets use relative paths, so the project can be served from a repository subpath.

## Data providers

- [ipify](https://www.ipify.org/) — public IP observed by the service.
- [ipapi.co](https://ipapi.co/) — public IP metadata and approximate geolocation.

Provider availability, response fields, rate limits, CORS behavior, and terms can change. Check the provider documentation before deploying for high-volume or commercial use. This project has no embedded API secrets.

## Privacy

- Lookup history, preferences, and a short-lived metadata cache are stored in browser `localStorage`.
- IP retrieval and metadata requests are sent to third-party services; those services will observe the request and may process its IP address under their own policies.
- No application-owned backend receives user data.
- Use **Settings → Clear local data** to remove stored history and cached information.
- IP geolocation is approximate and should not be treated as an exact physical location.
- Shared lookup URLs may include an IP address in the query string. Avoid sharing URLs containing sensitive addresses.

## Diagnostics limitations

- `navigator.onLine` is a browser-reported connection hint, not proof that the internet or a specific site is reachable.
- IPv4/IPv6 endpoint results show whether a specific endpoint was reachable from the current browser environment. Failure does not always prove the interface lacks that protocol.
- A genuine DNS leak test requires controlled DNS infrastructure and query observation. This project labels it as not configured rather than inventing a result.
- WebRTC API availability does not prove that an address leaked.
- VPN/proxy detection is not definitive and is only shown when a metadata provider supplies a relevant field.

## Testing

Serve the project over HTTP and open `/tests/` (for example `http://localhost:8000/tests/`). The lightweight test page runs IP validation, classification, IPv6 compression, and subnet utility checks without calling external APIs.

## License

MIT. See `LICENSE`.
