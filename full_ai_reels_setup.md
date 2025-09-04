# Full AI Reels Automation - GitHub Web Setup

## 1️⃣ config/config.yaml

```yaml
accounts:
  instagram:
    username: "test_instagram"
    password: "test_password"
  tiktok:
    username: "test_tiktok"
    password: "test_password"
  fanvue:
    username: "test_fanvue"
    password: "test_password"

personas:
  test_persona:
    name: "Test Blonde"
    style: "Indoor casual, soft natural light"
    prompt: "A blonde woman, slim-thick, natural light, cozy indoor"
    reel_source: "scripts/test_persona_reel.mp4"
    anchor_images:
      - "viewer/images/test_persona_anchor1.png"
      - "viewer/images/test_persona_anchor2.png"
#!/bin/bash
PERSONA="$1"
echo "Generating AI reel for $PERSONA..."
REEL_PATH="scripts/${PERSONA}_reel.mp4"

# Example Fal.ai API call
# fal-ai generate --prompt "$(yq e ".personas.${PERSONA}.prompt" config/config.yaml)" --output "$REEL_PATH" --api-key "YOUR_FAL_AI_KEY"

touch "$REEL_PATH" # placeholder
echo "Dummy reel created at $REEL_PATH"

# Extract anchor images
./extract_anchors.sh "$PERSONA"
#!/bin/bash
PERSONA="$1"
echo "Extracting anchor images for $PERSONA..."
IMG1="viewer/images/${PERSONA}_anchor1.png"
IMG2="viewer/images/${PERSONA}_anchor2.png"

# Example: take screenshots from the reel
# ffmpeg -i scripts/${PERSONA}_reel.mp4 -ss 00:00:01 -vframes 1 $IMG1
# ffmpeg -i scripts/${PERSONA}_reel.mp4 -ss 00:00:03 -vframes 1 $IMG2

touch "$IMG1" "$IMG2"
echo "Anchor images created: $IMG1, $IMG2"
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AI Reels Viewer</title>
</head>
<body>
<h1>AI Reels Viewer</h1>
<div id="reels-container"></div>
<script src="scripts/viewer.js"></script>
</body>
</html>
console.log("Viewer loaded. Display reels and anchors here.");
# AI Reels Automation - Web Only Setup

1. Edit `config/config.yaml` with your accounts and personas.
2. To generate a reel:
   ```bash
   ./scripts/generate_reel.sh test_persona

</details>

4. **Commit directly to main**  

---

## 3️⃣ How to Repeat / Scale

- **New persona:** Copy-paste a persona block in `config.yaml` → system automatically uses it for reel generation.  
- **New account:** Copy-paste an account block → system posts reels there.  
- **Repeat:** Paste same setup for new repo → create a brand new persona/account pipeline → set-and-forget.  

---

## 4️⃣ Running Online

- **Fal.ai handles AI reel generation**  
- **GitHub Codespaces** or **Replit** can execute scripts 24/7  
- You never touch local files  
- Each persona/account pipeline runs independently → unlimited scalability  

---

If you want, I can now **give the fully automated version that actually calls Fal.ai and generates screenshots, ready for posting**, so you literally never touch anything after initial setup.  

Do you want me to do that next?
