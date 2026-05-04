# Build Spec: Super Helper App — Elementary Career Day Demo

**Version:** 1.0  
**Project type:** Offline, kid-friendly web app demo  
**Primary audience:** Elementary school students  
**Presenter:** Software engineer / technology professional  
**Event context:** Career Day at Southridge Elementary School in Lewisville, Texas  
**Core message:** Apps are not magic. They are ideas plus instructions that help people.

---

## 1. Project Summary

Build a small, polished, offline web app called **Super Helper App** for an elementary school Career Day presentation. The app should help the presenter explain what a software engineer does by letting kids interact with a simple app that turns an **input** into an **output** by following **code/instructions**.

The app should feel playful, visual, and safe. It should not collect student data, require internet access, or rely on any external services. It should be simple enough to explain to kids but polished enough to feel like a real app.

The presentation experience should let the presenter:

1. Ask the class what kind of help they want.
2. Click a button in the app.
3. Show a fun response or “mission.”
4. Reveal a tiny code example.
5. Trigger a fake bug.
6. Fix the fake bug.
7. Let kids suggest and add a simple new feature live.

---

## 2. Objectives

### Primary Objectives

- Create a memorable Career Day demo that teaches elementary students what apps do.
- Make software engineering feel approachable, creative, and helpful.
- Give the presenter a reliable prop that works even without Wi-Fi.
- Support a short explanation of **Input → Code → Output**.
- Include a playful “bug and fix” moment to show that engineers test and improve things.

### Secondary Objectives

- Let students participate by choosing buttons and suggesting a feature.
- Make the app visually engaging when projected on a classroom screen.
- Keep all content age-appropriate, safe, and non-personal.
- Make the codebase simple enough to modify quickly before the event.

---

## 3. Non-Goals

This app should **not**:

- Use real AI APIs.
- Require authentication.
- Save student names, photos, audio, locations, or personal information.
- Depend on internet access.
- Explain complex engineering topics such as cloud infrastructure, databases, deployment pipelines, authentication, or security architecture.
- Be a production SaaS app.
- Include ads, analytics, tracking, cookies, or telemetry.
- Require a backend server.

---

## 4. Target User Experience

### Presenter Experience

The presenter should be able to open the app in a browser, go full screen, and run the entire session with minimal setup.

The presenter should be able to say:

> “Apps are not magic. They are ideas plus instructions.”

Then use the app to demonstrate:

> “The input is what we tell the app. The code is the instruction. The output is what the app gives back.”

### Student Experience

Students should feel like they are helping build or control the app. They should be able to vote on buttons, shout out feature ideas, and see immediate visual feedback.

They should leave with this idea:

> “Technology is something people build to help other people, and I can have app ideas too.”

---

## 5. Functional Requirements

### FR-001: Offline Operation

The app must run offline by opening a local HTML file or static build in a browser.

**Acceptance criteria:**

- App opens without internet access.
- No external network calls are required.
- No CDN dependencies are required unless also bundled locally.

---

### FR-002: Main App Screen

The app must have a main screen with:

- App title: **Super Helper App**
- Subtitle or explanation: “Pick what you need help with.”
- Presenter-friendly line: “Apps are not magic. They are ideas plus instructions.”
- A visible statement that no student data is saved.

**Acceptance criteria:**

- Title is large and readable from a classroom projector.
- The screen works on laptop, tablet, and projector-sized displays.
- The app looks complete and polished, not like a raw form.

---

### FR-003: Choice Buttons

The app must include at least these six choice buttons:

1. **I’m bored**
2. **I’m tired**
3. **I want a challenge**
4. **I need a brain break**
5. **Tell me a joke**
6. **Kindness mission**

Each button should show a playful icon or emoji.

**Acceptance criteria:**

- Clicking a button updates the output area.
- Each category has multiple possible responses.
- Repeated clicks can show different responses.
- Buttons are large enough to be visible and easy to click.

---

### FR-004: Mission Output Area

The app must display a large, readable output after the presenter clicks a choice button.

Example output:

> Draw a robot with cowboy boots.

The output area should also show a short explanation of the flow.

Example subtext:

> Input: “bored” → Code: pick a helpful response → Output: this mission.

**Acceptance criteria:**

- Output text is large enough for the back of a classroom.
- Output changes immediately after a button click.
- The subtext reinforces Input → Code → Output.

---

### FR-005: Try Again Button

The app must include a **Try again** button.

**Behavior:**

- If a category has already been selected, show another response from the same category.
- If no category has been selected, default to the “challenge” category.

**Acceptance criteria:**

- Button never breaks if clicked before any category is selected.
- Button shows a valid mission every time.

---

### FR-006: Show Code / Hide Code

The app must include a **Show code** button that toggles a small code panel.

The code panel should show a tiny, kid-friendly example such as:

```js
if (choice === "bored") {
  show("Draw a robot with cowboy boots!");
}
```

**Acceptance criteria:**

- Button text changes between **Show code** and **Hide code**.
- Code example updates based on the selected category when possible.
- Code panel is visually distinct from the rest of the app.
- Code should be brief enough to explain in under 30 seconds.

---

### FR-007: Fake Bug Demo

The app must include a **Make a bug** button.

When clicked, it should intentionally show a silly error, such as:

> ERROR: Banana not found 🍌

It should also show a short explanation:

> A bug is when the app does something we did not want.

The code panel should reveal an intentionally broken-looking snippet such as:

```js
if (choice === "joke") {
  show(banana); // Oops. The app cannot find banana.
}
```

**Acceptance criteria:**

- Clicking **Make a bug** visibly changes the output area into an error/bug state.
- The **Fix bug** button becomes visible.
- The code panel opens automatically.
- The fake bug is silly, harmless, and easy to understand.

---

### FR-008: Fix Bug Demo

The app must include a **Fix bug** button that appears after **Make a bug** is clicked.

When clicked, it should replace the error with a working joke or mission.

Example:

> Bug fixed: Why did the tablet need a nap? It had too many tabs open.

It should also show:

> Engineers test, find bugs, fix them, and try again.

**Acceptance criteria:**

- **Fix bug** is hidden until a bug is created.
- Clicking **Fix bug** clears the bug/error visual state.
- The code panel updates to show a corrected version.
- The app returns to a success/good state.

---

### FR-009: Mystery Feature Button

The app must include a **Mystery feature** button.

When clicked, it should display something like:

> Mystery feature: Ask the class what button we should add next.

Subtext:

> This is how app ideas start: someone notices a need or has a fun idea.

**Acceptance criteria:**

- The mystery feature supports transitioning into the live feature-building section.
- It should not depend on any hidden or external data.

---

### FR-010: Build a Feature Together

The app must include a section where the presenter can type:

- App name
- Feature idea

Then click **Add feature**.

The app should create a new visible button using the feature idea.

Example:

- Presenter types: “pizza button”
- App creates button: **Pizza Button**
- Clicking that button shows: “The Pizza Button works!”

**Acceptance criteria:**

- Feature input is sanitized for display.
- Feature input is limited to a short length, recommended max 40 characters.
- If the presenter leaves it blank, the app uses a safe default such as “mystery helper.”
- New feature button appears immediately.
- Clicking the new feature button updates the output area.
- The app does not save feature ideas after page refresh.

---

### FR-011: App Name Customization

The app should let the presenter rename the app during the live demo.

**Acceptance criteria:**

- App name input has a safe default: **Super Helper App**.
- App name is used only for display text.
- App name is not persisted.
- App name max length is 40 characters.

---

### FR-012: Printable Cards

Create a printable companion file or section with large cards for:

- INPUT
- CODE
- OUTPUT
- BUG
- FIX

Each card should include one short description.

Examples:

- **INPUT** — What we tell the app.
- **CODE** — The app’s instructions.
- **OUTPUT** — What the app gives back.
- **BUG** — When the app does something we did not want.
- **FIX** — Change the instructions and try again.

**Acceptance criteria:**

- Cards are printable on standard letter paper.
- Each card is readable from across a classroom.
- Cards can be printed without color and still work.

---

### FR-013: Presenter Guide

Create a markdown presenter guide with 10-minute, 20–25-minute, and 40–45-minute versions of the activity.

**Acceptance criteria:**

- Guide includes a short opening script.
- Guide includes suggested questions to ask students.
- Guide includes the app demo sequence.
- Guide includes a backup plan if technology fails.
- Guide includes a privacy/safety reminder: do not type student names.

---

## 6. Content Requirements

### Mission Categories

Implement the following mission categories and starter content.

#### Bored

- Draw a robot with cowboy boots.
- Invent a new animal and give it a funny name.
- Pretend you are a news reporter for 10 seconds.
- Make up a superhero power that helps your teacher.
- Design a snack for astronauts.

#### Tired

- Take three slow breaths.
- Stretch your arms like a starfish.
- Roll your shoulders three times.
- Pretend you are charging your battery.
- Sit tall and take one quiet superhero breath.

#### Challenge

- Name five things that are blue.
- Count backward from 20.
- Think of three words that rhyme with cat.
- Make a pattern with claps: clap, clap, snap.
- Name three animals that live in Texas.

#### Brain Break

- Look left, look right, then blink three times.
- Touch your shoulders, knees, then head.
- Pretend your hands are tiny fireworks.
- Make your silliest thinking face.
- Take a quiet 5-second reset.

#### Joke

- Why did the computer go to school? To improve its byte-sized learning.
- Why was the math book sad? It had too many problems.
- What do you call a dinosaur that builds apps? A code-osaurus.
- Why did the robot bring a pencil? It wanted to draw its own conclusions.
- Why did the tablet need a nap? It had too many tabs open.

#### Kindness

- Tell someone, “Good job.”
- Give your teacher a quiet thumbs up.
- Smile at someone near you.
- Say thank you to someone today.
- Think of one way to help a friend.

---

## 7. UX and Visual Design Requirements

### Tone

The app should feel:

- Friendly
- Bright
- Classroom-safe
- Playful but not chaotic
- Clear from a projector
- Easy for an adult presenter to operate

### Layout

Recommended layout:

1. Header / hero section
   - Title
   - Short explanation
   - Safety note

2. Main grid
   - Left side: choice buttons and Input → Code → Output explanation
   - Right side: app output screen and controls

3. Feature builder section
   - App name input
   - Feature idea input
   - Add feature button
   - Newly created feature buttons

4. Footer reminder
   - Short presenter line tying the demo back to real work

### Visual Details

- Use large typography.
- Use rounded cards and buttons.
- Use high contrast text.
- Use clear success and bug states.
- Avoid tiny controls.
- Avoid dense paragraphs.
- Keep code snippets short and readable.

---

## 8. Accessibility Requirements

The app should be usable with keyboard and readable by screen readers.

**Requirements:**

- Use semantic HTML where possible.
- All buttons must be actual `<button>` elements.
- Inputs must have labels.
- The mission output area should use `aria-live="polite"` so updates are announced.
- Visible focus states must be present.
- Color should not be the only indicator of state.
- Text should have sufficient contrast.
- The app should remain usable at common browser zoom levels.

---

## 9. Privacy and Safety Requirements

This is for an elementary school setting. Keep privacy simple and strict.

**Requirements:**

- Do not collect student names.
- Do not collect photos.
- Do not collect audio.
- Do not collect location data.
- Do not store data in localStorage, sessionStorage, cookies, backend databases, or analytics tools.
- Do not send network requests.
- Do not include user tracking.
- Include a visible note: “No student names, photos, or data are saved.”
- Add a presenter reminder near the feature builder: “Keep ideas generic. Do not type student names.”

---

## 10. Recommended Technical Approach

### Preferred Implementation

A single static web app using:

- HTML
- CSS
- JavaScript

This is the safest and fastest approach because it runs by double-clicking `index.html`.

### Alternative Implementation

A small React/Vite app is acceptable if the final deliverable includes a built static version that can run offline.

If using React, keep the component structure simple:

```txt
src/
  App.tsx
  data/missions.ts
  components/
    Hero.tsx
    ChoiceGrid.tsx
    MissionScreen.tsx
    CodePanel.tsx
    FeatureBuilder.tsx
    ConceptCards.tsx
    PresenterNotes.tsx
  styles.css
```

### Dependencies

Avoid dependencies unless necessary.

Recommended:

- No UI framework required.
- No external icon package required; emojis are acceptable.
- No API client.
- No backend.
- No database.

---

## 11. Suggested File Structure

For a simple static implementation:

```txt
super-helper-career-day-app/
  index.html
  printable-cards.html
  presenter-guide.md
  README.md
  buildspec.md
```

For a Vite/React implementation:

```txt
super-helper-career-day-app/
  package.json
  index.html
  src/
    main.tsx
    App.tsx
    data/
      missions.ts
    components/
      Hero.tsx
      ChoiceGrid.tsx
      MissionScreen.tsx
      CodePanel.tsx
      FeatureBuilder.tsx
      ConceptCards.tsx
      PresenterNotes.tsx
    styles.css
  public/
    printable-cards.html
    presenter-guide.md
  buildspec.md
  README.md
```

---

## 12. State Model

The app can use simple local component state or plain JavaScript variables.

### State Fields

```ts
type Category = "bored" | "tired" | "challenge" | "brainBreak" | "joke" | "kindness";

type AppState = {
  selectedCategory: Category | null;
  missionText: string;
  missionSubtext: string;
  outputState: "neutral" | "good" | "bug";
  isCodeVisible: boolean;
  codeText: string;
  isFixButtonVisible: boolean;
  appName: string;
  featureInput: string;
  addedFeatures: AddedFeature[];
};

type AddedFeature = {
  id: string;
  label: string;
  responseText: string;
};
```

### Persistence

Do not persist state. Everything should reset on refresh.

---

## 13. Core Behaviors in Pseudocode

### Run a Category

```ts
function runCategory(category) {
  selectedCategory = category;
  isFixButtonVisible = false;
  outputState = "good";
  missionText = randomItem(missions[category]);
  missionSubtext = `Input: “${labelFor(category)}” → Code: pick a helpful response → Output: this mission.`;
  codeText = makeCodeExample(category, missionText);
}
```

### Try Again

```ts
function tryAgain() {
  runCategory(selectedCategory ?? "challenge");
}
```

### Toggle Code

```ts
function toggleCode() {
  isCodeVisible = !isCodeVisible;
}
```

### Make Bug

```ts
function makeBug() {
  outputState = "bug";
  missionText = "ERROR: Banana not found 🍌";
  missionSubtext = "A bug is when the app does something we did not want.";
  isCodeVisible = true;
  isFixButtonVisible = true;
  codeText = `if (choice === "joke") {\n  show(banana); // Oops. The app cannot find banana.\n}`;
}
```

### Fix Bug

```ts
function fixBug() {
  outputState = "good";
  missionText = "Bug fixed: Why did the tablet need a nap? It had too many tabs open.";
  missionSubtext = "Engineers test, find bugs, fix them, and try again.";
  isFixButtonVisible = false;
  codeText = `if (choice === "joke") {\n  show("Why did the tablet need a nap? It had too many tabs open.");\n}`;
}
```

### Add Feature

```ts
function addFeature() {
  const cleanName = sanitize(featureInput) || "mystery helper";
  addedFeatures.push({
    id: createId(),
    label: titleCase(cleanName),
    responseText: `The ${titleCase(cleanName)} works!`
  });
  missionText = `Feature added: ${titleCase(cleanName)}`;
  missionSubtext = "Now test it by pressing the new button.";
  outputState = "good";
  featureInput = "";
}
```

---

## 14. Input Sanitization

The app does not save or transmit data, but display inputs should still be cleaned.

**Rules:**

- Trim leading/trailing whitespace.
- Collapse repeated spaces.
- Limit to 40 characters.
- Escape by rendering as text, not HTML.
- Do not use `innerHTML` for user-provided feature names.
- Default blank feature input to “mystery helper.”

---

## 15. Testing Requirements

### Manual Tests

1. Open app offline.
2. Click each of the six category buttons.
3. Confirm output appears and subtext matches category.
4. Click **Try again** before selecting a category.
5. Click **Try again** after selecting a category.
6. Click **Show code** and **Hide code**.
7. Click **Make a bug**.
8. Confirm bug output appears and **Fix bug** becomes visible.
9. Click **Fix bug**.
10. Confirm bug state clears.
11. Type a feature idea and click **Add feature**.
12. Confirm new feature button appears.
13. Click the new feature button.
14. Refresh page and confirm added features are gone.
15. Test with no internet connection.
16. Test projected/full-screen view if possible.
17. Test keyboard tab order.
18. Test browser zoom at 125% and 150%.

### Accessibility Checks

- All interactive elements can be reached with the keyboard.
- Focus outline is visible.
- Inputs have labels.
- Output updates are announced via `aria-live` where supported.
- Text remains readable at classroom distance.

---

## 16. Acceptance Criteria Summary

The build is complete when:

- The app runs offline.
- The six main buttons work.
- Missions are displayed clearly.
- **Try again** works.
- **Show code** / **Hide code** works.
- **Make a bug** works.
- **Fix bug** works.
- **Mystery feature** works.
- Feature builder creates new buttons live.
- No data is persisted or sent anywhere.
- The printable cards exist.
- The presenter guide exists.
- The README includes setup instructions.
- The app is visually polished and projector-friendly.

---

## 17. Presenter Guide Content

Create `presenter-guide.md` with the following sections.

### 10-Minute Version

1. Ask: “Who here uses apps?”
2. Say: “Apps are ideas plus instructions.”
3. Show the app.
4. Let the class pick a button.
5. Explain Input → Code → Output.
6. Trigger the fake bug.
7. Fix the bug.
8. Close with: “Technology is something people build to help other people.”

### 20–25-Minute Version

1. Ask students what apps or games they know.
2. Explain your job in one sentence: “I build technology that helps people solve problems.”
3. Show the Super Helper App.
4. Let the class vote on buttons.
5. Show the tiny code example.
6. Trigger and fix the bug.
7. Ask them for a feature idea.
8. Add the feature live.
9. Let them test the new button.
10. Close with the core message.

### 40–45-Minute Version

Add a paper activity:

> Design your own app that helps someone.

Students should draw:

1. App name
2. Who it helps
3. One button on the app
4. What happens when the button is pressed

### Backup Plan

If the projector, browser, or laptop fails, use printed cards and act as the app manually:

1. Hold up **INPUT**.
2. Ask a student for a need, such as “I’m bored.”
3. Hold up **CODE**.
4. Say: “My instructions say: if someone is bored, give them a creative mission.”
5. Hold up **OUTPUT**.
6. Say: “Draw a dog driving a spaceship.”

Then explain:

> “That is how apps work. They take input, follow instructions, and give output.”

---

## 18. README Requirements

Create `README.md` with:

- Project name
- One-paragraph description
- How to run locally
- How to present
- Files included
- Privacy note
- Troubleshooting tips

Example run instructions for static build:

```txt
1. Download or clone the project.
2. Open index.html in a browser.
3. Put the browser in full-screen mode.
4. Test all buttons before presenting.
```

---

## 19. Optional Stretch Goals

Only add these if the base app is done first.

### Stretch Goal A: Presentation Mode

Add a toggle that hides the feature builder and notes so only the app screen is visible.

### Stretch Goal B: Big Screen Mode

Add a button that increases font sizes and spacing for projection.

### Stretch Goal C: Sound-Free Animation

Add small animations for output changes, bug state, and bug fix. Keep animations subtle and avoid flashing.

### Stretch Goal D: Printable Activity Sheet

Create a printable worksheet titled **Design Your Own App** with four boxes:

1. My app is called...
2. My app helps...
3. My app has this button...
4. When you press it...

### Stretch Goal E: Theme Switcher

Add simple themes:

- Classic
- Space
- Robots
- Texas

No theme should require external assets.

---

## 20. Build Order for Coding Agent

Build in this order:

1. Create static project structure.
2. Build main layout and styles.
3. Add mission data.
4. Implement category button behavior.
5. Implement output state and subtext.
6. Implement Try Again.
7. Implement Show Code / Hide Code.
8. Implement Make Bug.
9. Implement Fix Bug.
10. Implement Mystery Feature.
11. Implement Feature Builder.
12. Add accessibility attributes and keyboard support.
13. Create printable cards.
14. Create presenter guide.
15. Create README.
16. Run manual test checklist.
17. Package final folder as a ZIP.

---

## 21. Final Deliverables

The final project should include:

```txt
super-helper-career-day-app/
  index.html
  printable-cards.html
  presenter-guide.md
  README.md
  buildspec.md
```

A React/Vite implementation may also include source files, but it must still provide a final static/offline build.

---

## 22. Success Definition

This project succeeds if the presenter can walk into an elementary classroom with a laptop, open the app without Wi-Fi, and guide students through a simple, fun explanation of software engineering:

> Input → Code → Output → Bug → Fix → New Feature

The app should help students understand that software engineers build tools, solve problems, test ideas, and improve things over time.
