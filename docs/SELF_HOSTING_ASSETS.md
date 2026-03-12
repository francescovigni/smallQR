# Self-Hosting Front-End Assets

Currently external CDNs are used for Bootstrap and JS. To tighten CSP and avoid third-party requests:

## Steps
1. Download assets:
   ```bash
   curl -L -o webapp/static/vendor/bootstrap.min.css https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css
   curl -L -o webapp/static/vendor/bootstrap.bundle.min.js https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js
   curl -L -o webapp/static/vendor/jquery-3.6.3.min.js https://code.jquery.com/jquery-3.6.3.min.js
   ```
2. Update `layout.html`:
   ```html
   <link href="{{ url_for('static', filename='vendor/bootstrap.min.css') }}" rel="stylesheet">
   <script src="{{ url_for('static', filename='vendor/jquery-3.6.3.min.js') }}" defer></script>
   <script src="{{ url_for('static', filename='vendor/bootstrap.bundle.min.js') }}" defer></script>
   ```
3. Adjust CSP in `app.py`:
   - Remove external domains from `style-src` and `script-src`.
   - Optionally add `'strict-dynamic'` or hashes if inline scripts remain.
4. Remove inline styles/JS that force `'unsafe-inline'`:
   - Move chevron transform + summary styling into `style.css`.
5. Tightened CSP example:
   ```python
   csp = "default-src 'self'; img-src 'self' data:; style-src 'self'; script-src 'self'; object-src 'none'; base-uri 'self'; form-action 'self'"
   ```
6. Test locally using browser dev tools (no blocked requests).

## Optional
- Subresource Integrity (SRI) not needed once self-hosted.
- Consider hashing large vendor files and referencing versioned filenames for cache busting.

## Rollback
Just revert `layout.html` to CDN links if any issue arises.
