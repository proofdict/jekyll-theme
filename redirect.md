---
layout: redirect
---

# Redirecting…

Redirecting you to the appropriate playground.

If the redirect doesn’t work, <a href="javascript:history.back()">go back</a>.

<script>
const match = /^https:\/\/github\.com\/(\w+)\//.exec(
  document.referrer
);
if (match !== null) {
  const [, /* url */ owner] = match;
  const url = new URL(document.referrer);
  const searchParams = new URLSearchParams(url.search);
  const type = searchParams.get("type");
  switch (type) {
    case "api": {
      location.replace(
        `https://${owner}.github.io/proof-dictionary/dictionary.json`
      );
      break;
    }
    case "editor": {
      location.replace(
        `https://${owner}.github.io/proof-dictionary/editor/`
      );
      break;
    }
    case "dictionary":
    default: {
      location.replace(
        `https://${owner}.github.io/proof-dictionary`
      );
      break;
    }
  }

} else {
  const el = document.createElement("p");
  el.textContent = `The referrer URL (${
    document.referrer
    }) was not recognized. Sorry :(`;
  document.body.appendChild(el);
}
</script>
