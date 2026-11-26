---
name: verify-about-me
description: Launch, check, drive and screenshot the About Me static site to confirm a change works. Use after any edit to index.html or style.css.
---

# Verify About Me site

Static site: `index.html` + `style.css`. Feature map per section is in `feature-map/` (intro, what-i-do, projects, contact).

## Launch
Serve statically from the repo root (opening `index.html` directly also works):

    python3 -m http.server 8765 --directory . &   # note the PID
    echo $! > .fredrin/tmp/server.pid

## Doctor (readiness check)
    curl -fsS http://localhost:8765/index.html | grep -c '<section'     # expect 4
    curl -fsS -o /dev/null -w '%{http_code}\n' http://localhost:8765/style.css   # expect 200
    for id in intro what-i-do projects contact; do grep -q "id=\"$id\"" index.html || echo "missing $id"; done

## Drive
With `./.fredrin/fredrin browser` (navigate to http://localhost:8765/), scroll through intro → what-i-do → projects → contact, then confirm each link target against the feature map (read hrefs with `browser eval`; external links need not be clicked live if offline — check the href exactly). Check mobile width too.

## Evidence
    ./.fredrin/fredrin browser screenshot   # PNG of the rendered page; attach to the ticket if allowed

## Cleanup
    kill "$(cat .fredrin/tmp/server.pid)"; rm -f .fredrin/tmp/server.pid

## Feature map
- `feature-map/intro.md`
- `feature-map/what-i-do.md`
- `feature-map/projects.md`
- `feature-map/contact.md`
