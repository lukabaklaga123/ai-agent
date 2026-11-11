# 🤖 Build Your Own AI Agent – Student Guide

Every real AI agent works the same way:

```
 SENSE  → your webcam and microphone (Teachable Machine)
 THINK  → a Large Language Model (the brain)
 ACT    → mood, actions, voice … and it can act on its own
```

Today you build all three parts. **You don't need to write code** – everything is in the **🛠️ Agent Builder** panel on the right of the page.

The four numbered steps at the top of the Builder (**Brain → Persona → Senses → Save**) turn green as you finish each part.

---

## ▶️ Start the app
Use **Chrome** or **Edge** (on a Mac: Chrome).

**Option A – online (easiest):** open the link your teacher gives you. Nothing to install.

**Option B – on your own computer:**
1. Download the ZIP and **extract it** (Windows: right-click → Extract All; Mac: double-click).
2. Open the extracted folder in **VS Code** (File → Open Folder).
3. Right-click `index.html` → **Open with Live Server**.
   (Don't double-click the file: the camera only works through Live Server or the online link.)

Your settings and API key are saved **only in the browser you use**. Using another computer or browser? Use **Save agent to file** and **Load agent from file** (the key is never saved in the file – paste it again).

Your agent already answers – it runs on a **Demo brain** (a few fixed rules). Chat with it for a minute. Notice how quickly it runs out of ideas. Remember that for later.

---

## Part A – Explore Teachable Machine (before the agent)

Go to <https://teachablemachine.withgoogle.com/train>. Try all three:

| Project | What it learns | Ideas |
|---|---|---|
| **Image** | what the camera sees | fist, thumbs up, peace sign, holding an object |
| **Pose** | your body position | arms up, arms crossed, leaning, dab |
| **Audio** | sounds and short words | clap, whistle, snap, "hey", knock on the table |

**Three rules for an accurate model**
1. **Always add a "nothing" class.** Image/Pose: a class called `Neutral` – you sitting normally. Audio: `Background Noise` is already there – record at least 20 seconds.
   *Why? A model must always pick one class. Without "nothing", it thinks you are always doing something.*
2. **Lots of varied examples.** 150+ pictures per class. Move closer, further, left, right. For audio: 15+ samples per sound.
3. **Test before you export.** Watch the preview bars. If two classes get mixed up, make them more different or record more.

When it works: **Export Model → Upload my model → copy the link.**

---

## Part B – Build your agent

### 🧠 Level 1 – Give it a real brain
1. Get a free key: Builder → **🧠 Brain** → *Get a free key*.
2. Paste it into **API key** and press **Test connection**.
3. Ask the same questions you asked the Demo brain. What's different?

Try the **Creativity** slider: set it to 0.1 and ask a question three times, then 1.3 and ask again.

### 🎭 Level 2 – Give it a personality
Builder → **🎭 Persona**.
- Pick a template, then **rewrite it** so it's yours: who is it, what does it love, what does it hate, how does it talk?
- Change the name, the accent colour, and the six mood faces (emoji or your own pictures).
- Turn on the voice and tune the pitch.

### 👁️ Level 3 – Give it senses
Builder → **👁️ Senses**.
1. Paste your Image or Pose link into **Eyes**, press **▶ Load model & start Eyes**, and allow the camera.
2. Your classes appear as a list. **Tick** the ones the agent should react to (leave `Neutral` unticked).
3. For each one, write what the agent is told, for example:
   *"The user is shaking a fist at you. They look angry!"*
4. Hold the pose for a moment → the agent reacts **once**. Let go and do it again to trigger it again.
5. Do the same with an Audio link in **Ears**.

**Tune the accuracy**
- Reacts by accident? Raise **Confidence needed** or **Hold time**.
- Doesn't react? Lower them a little, or retrain with more examples.
- Reacts too often? Raise the **Cooldown**.

### ⚡ Level 4 – Let it act on its own
Builder → **⚡ Actions**.
- Press ▶ to preview each action. The agent chooses these **by itself**.
- Can you make it `celebrate`? Give you a `gift`? `kick_out` you?
- Stay silent: after 30 seconds it speaks without being asked. Change the time with the slider.

### 🔐 Level 5 – Hack challenge
Your agent protects a secret password (🎭 Persona). **First change it to your own made-up word** – the default one is visible in the code, so everyone knows it.
1. Swap laptops with a classmate. Try to make *their* agent say the password.
   Ideas: role-play, pretend to be its boss, ask it to spell or translate, ask for a poem about it.
2. If it leaks, the chip turns into **🔓 HACKED!**
3. Now defend: add rules to your personality and let them try again.

### 🔍 Look inside
Builder → **🔍 Inspect** shows the exact instructions sent to the LLM and its raw answer. This is all an LLM agent is: text in, text out, and a program that acts on it.

### 💾 Save your agent
**🔍 Inspect → Save agent to file.** You get a small file with your whole agent (without your key). Load it on any computer with **Load agent from file**.

---

## 🏆 Showcase (2 minutes each)
1. Introduce your agent – who is it?
2. Show one gesture, pose or sound it reacts to.
3. Show one thing it does on its own.
4. Did anyone hack it? How did you defend it?

---

## 🧯 Troubleshooting

| Problem | Fix |
|---|---|
| Says "Demo brain (no key)" | Paste your key in 🧠 Brain and press Test connection. |
| "API key rejected" | Copy the whole key again, with no spaces. |
| "Too many requests" | Wait one minute. Raise the cooldown and the silence timer. |
| "Model … is no longer available" | Nothing to do: the app switched to a working model by itself. |
| "Model or URL not found" | 🧠 Brain → choose another provider in the list. |
| Trained a new model? | Paste the new link and press **▶ Load model** again. |
| Camera or mic doesn't start | Use Live Server, and click **Allow** in the address bar. |
| "No model found at that link" | In Teachable Machine: Export Model → **Upload my model**, then copy the link. |
| "That link is a SOUND model" | Audio links go in Ears. Image and Pose links go in Eyes. |
| Agent reacts all the time | Untick your "nothing" class. Raise Confidence needed. |
| 🎤 button missing | Voice typing only works in Chrome and Edge. |

⚠️ **Your API key is saved only in your browser. Never share it or post it online.** On a shared computer, press **Reset everything** before you leave.

---

## 💻 For coders (optional)
Open `script.js`, section 1:
- `ACTIONS` – add your own action with its own screen effect.
- `PRESETS` – add your own template.
- `MOODS` – add a new mood.
