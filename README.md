# # ✨ Grace Gaynor Portfolio & Business Value

<div align="center">

<strong>A responsive, interactive analytics portfolio that turns research, dashboards, automation concepts, and business tools into a clear professional story.</strong>

<br><br>

![HTML](https://img.shields.io/badge/HTML5-Portfolio-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-Responsive-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-Interactive-F7DF1E?style=for-the-badge&logo=javascript&logoColor=111)
![Accessibility](https://img.shields.io/badge/Accessibility-Keyboard%20Ready-2E8B57?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Active%20Portfolio-08BED5?style=for-the-badge)

<br>

**Econometrics · Analytics · Power BI · Python · Web Development · Responsible AI**

</div>

---

## 👋 Welcome

This application is a single-page portfolio and business-value dashboard for **Grace Gaynor**. It presents analytical research, workforce and learning analytics, Power BI work, decision-support prototypes, development tooling, and an AI-builder learning journey in one navigable experience.

The application is intentionally built as a **single HTML file** with embedded CSS and JavaScript. That makes it easy to open locally, share for review, and publish to a static hosting platform after appropriate content and branding review.

> 💡 **Big idea:** great analysis should not stop at an answer. It should become a clear story, a reusable workflow, or a tool that helps someone make a better decision.

---

## 🧭 What is inside?

The site is organized as an accessible tabbed interface.

### 📁 My Portfolio

A project gallery featuring:

- **Estimating Demand Elasticities to Model Geographic Market Boundaries**
- **Early-Career Attrition Econometric Analysis**
- **LinkedIn Learning Engagement Analytics**
- **PVI Performance Advisor**
- **Attrition & Mobility Power BI Dashboard**
- **Pepsi vs. Coke Price & Diversion Model**
- **Analytics Developer Portfolio**

Each project card communicates the project status, business or research question, technical themes, and the intended contribution or next build.

### 📈 PVI Calculator Value

Explains the business problem behind the PVI Performance Advisor and describes how the concept supports:

- A more consistent review workflow
- Clear separation of official values and modeled scenarios
- Easier explanation of score drivers and thresholds
- Reduced repetitive data entry
- More transparent decision support
- Responsible use of analytical and AI-assisted recommendations

### 🤖 AI Builder Journey & Access

Describes the desired progression from analytics and prompting into governed applications, developer workflows, and responsible agents.

The section groups capabilities into:

- Enterprise AI and agents
- AI-assisted development
- Application development and delivery
- Emerging builder tools for formal evaluation
- Responsible-access commitments

### 🧰 Full Software List

A searchable and filterable software table covering:

- Core development tools
- Data-science packages
- Frontend frameworks
- Backend and API tools
- Business-intelligence tools
- AI platforms
- DevOps tools
- Visual Studio Code extensions

### 💻 VS Code Setup

Includes:

- A suggested extension bundle
- Recommended project folders
- Installation validation commands
- A starter `settings.json` configuration

### 🔗 Official Links

Collects official product and documentation destinations for the primary technologies referenced in the portfolio.

### 🎓 Learning Plan

Provides a staged learning path across:

- Python fundamentals
- Automation
- Databases and data modeling
- Power BI
- AI agents
- Retrieval-augmented generation
- Model Context Protocol
- Microsoft certifications

### 💼 Business Case

Provides reusable language explaining why a consolidated development environment supports reproducible analytics, dashboards, calculators, internal applications, documentation, testing, and responsible AI prototypes.

---

## 🌟 Core features

<div>

### 🎛️ Accessible tab navigation

The navigation uses ARIA tab roles and connects every tab to a corresponding panel. Users can move between tabs with a pointer, keyboard arrows, **Home**, or **End**.

### 🔍 Search and filtering

The software inventory can be filtered by:

- Search text
- Category
- Priority

### 📋 Copy-to-clipboard actions

Business-case and AI-builder text can be copied using dedicated buttons. A toast message confirms success or explains when manual selection is required.

### 🔗 Deep-link support

In a regular browser environment, a fragment such as `#pvi-value` can open the corresponding section directly.

### 🛡️ Sandbox-safe history handling

Some SharePoint, Teams, and embedded previews render HTML inside a sandboxed `about:srcdoc` document with a `null` origin. In that environment, `history.replaceState()` can throw a `SecurityError`.

The safe implementation treats URL synchronization as an enhancement rather than a requirement. Tab switching always works, while history updates are attempted only when the browser permits them.

### ♿ Accessibility details

- Skip-to-content link
- Visible keyboard focus
- Semantic headings
- ARIA tab relationships
- Keyboard tab navigation
- Screen-reader-friendly hidden labels
- Reduced-motion support
- Horizontally scrollable tables on smaller screens

### 📱 Responsive design

The CSS uses fluid typography, auto-fitting grids, flexible toolbars, and scroll-safe tables to support desktop, tablet, and mobile layouts.

</div>

---

## 🏗️ Application architecture

```text
Grace_Gaynor_Value_Portfolio_AI_Builder_Request.html
│
├── <head>
│   ├── SEO and social metadata
│   ├── Theme color
│   ├── Web-font connection
│   └── Embedded CSS design system
│
├── <body>
│   ├── Skip link
│   ├── Portfolio header
│   ├── ARIA tab navigation
│   ├── Main tab panels
│   │   ├── Projects
│   │   ├── PVI value
│   │   ├── AI-builder journey
│   │   ├── Software inventory
│   │   ├── VS Code setup
│   │   ├── Official links
│   │   ├── Learning plan
│   │   └── Business case
│   ├── Footer
│   ├── Toast notification
│   └── Embedded JavaScript
│       ├── Tab activation
│       ├── Keyboard navigation
│       ├── Hash/deep-link handling
│       ├── Software filtering
│       └── Clipboard actions
```

---

## 🚀 Run the application

No build tool or package installation is required.

```bash
# Option 1: open the file directly
open Grace_Gaynor_Value_Portfolio_AI_Builder_Request.html

# Option 2: serve it locally with Python
python -m http.server 8000

# Then visit the local server in a browser
# http://localhost:8000/Grace_Gaynor_Value_Portfolio_AI_Builder_Request.html
```

> ✅ Using a local server is recommended when testing browser APIs because it more closely resembles a deployed website than an embedded preview.

---

## 🧩 Key JavaScript behavior

All behavior is contained in one self-invoking function to avoid adding unnecessary global variables.

### Safe tab activation and URL synchronization

```javascript
function activate(id, setFocus) {
  tabs.forEach((tab) => {
    const isActive = tab.getAttribute('aria-controls') === id;
    tab.setAttribute('aria-selected', isActive);
    tab.tabIndex = isActive ? 0 : -1;

    if (isActive && setFocus) {
      tab.focus();
    }
  });

  panels.forEach((panel) => {
    const isActive = panel.id === id;
    panel.classList.toggle('active', isActive);
    panel.hidden = !isActive;
  });

  if (location.hash.slice(1) !== id) {
    try {
      history.replaceState(null, '', '#' + id);
    } catch (error) {
      // Embedded and sandboxed previews may block History API updates.
      // The selected tab still works because panel state is managed in the DOM.
    }
  }
}
```

### Software-table filtering

```javascript
function filterRows() {
  const searchValue = q.value.toLowerCase();
  const categoryValue = cat.value.toLowerCase();
  const priorityValue = pri.value.toLowerCase();

  document.querySelectorAll('#sw tbody tr').forEach((row) => {
    const allText = row.innerText.toLowerCase();
    const rowCategory = row.cells[1].innerText.toLowerCase();
    const rowPriority = row.cells[2].innerText.toLowerCase();

    const matches =
      allText.includes(searchValue) &&
      (!categoryValue || rowCategory === categoryValue) &&
      (!priorityValue || rowPriority === priorityValue);

    row.style.display = matches ? '' : 'none';
  });
}
```

### Clipboard action with user feedback

```javascript
async function copyText(elementId, successMessage) {
  try {
    const text = document.getElementById(elementId).innerText;
    await navigator.clipboard.writeText(text);
    showToast(successMessage);
  } catch (error) {
    showToast('Copy failed. Select the text manually.');
  }
}
```

---

## 🐛 Important preview issue and fix

### The error

```text
Uncaught SecurityError: Failed to execute 'replaceState' on 'History':
A history state object with URL 'blob:' cannot be created in a document
with origin 'null' and URL 'about:srcdoc'.
```

### The cause

The original tab function used `history.replaceState()` every time a tab was activated. That works on a normal hosted page, but a sandboxed HTML preview may have:

- An `about:srcdoc` URL
- A `null` origin
- Restricted history access
- A generated `blob:` wrapper

In that environment, changing the displayed fragment can be blocked by the browser's security model.

### The fix

Wrap the optional History API call in `try...catch`:

```javascript
try {
  history.replaceState(null, '', '#' + id);
} catch (error) {
  // Continue without URL synchronization.
}
```

The important design principle is:

> 🧠 **Navigation state belongs to the page. URL synchronization is progressive enhancement.**

The application therefore remains fully usable even when the preview prevents history changes.

---

## 🎨 Design system

The visual system is driven by reusable CSS custom properties.

```css
:root {
  --t: #005758;      /* Primary teal */
  --c: #08bed5;      /* Cyan accent */
  --l: #c7f35b;      /* Lime accent */
  --b: #f4fbfb;      /* Page background */
  --i: #073536;      /* Main text */
  --m: #5e7475;      /* Muted text */
  --x: #d7eeee;      /* Borders */
  --warn: #ffb454;   /* Warning accent */
  --radius: 20px;
  --radius-sm: 12px;
  --maxw: 1200px;
}
```

### Visual language

- **Teal:** credibility, analysis, and structure
- **Cyan:** technology, interaction, and forward motion
- **Lime:** research highlights and important project moments
- **Warm warning tone:** transparency notes and governance reminders
- **Rounded cards:** approachable, contemporary presentation
- **Subtle shadows:** hierarchy without making the interface feel heavy

---

## ✍️ Customize the content

### Add a project

Duplicate a project card inside the `#projects` grid and update:

```html
<div class="card">
  <span class="status">Project status</span>
  <h3>Project title</h3>
  <p>Short explanation of the problem, approach, and purpose.</p>

  <div>
    <span class="tag">Skill</span>
    <span class="tag">Method</span>
    <span class="tag">Tool</span>
  </div>

  <div class="out">
    <b>Contribution:</b> Explain the value, outcome, or next build.
  </div>
</div>
```

### Add a tab

A new tab requires both a button and a matching panel.

```html
<button
  class="tab"
  role="tab"
  id="tab-recommendations"
  aria-controls="recommendations"
  aria-selected="false"
  tabindex="-1">
  Recommendations
</button>

<section
  class="section"
  id="recommendations"
  role="tabpanel"
  aria-labelledby="tab-recommendations"
  tabindex="0"
  hidden>
  <h2>Recommendations</h2>
  <p>Add verified recommendation content here.</p>
</section>
```

Because the JavaScript discovers tabs and panels by their ARIA roles, a correctly connected pair automatically participates in the existing navigation behavior.

### Add verified recommendations

Use genuine, approved recommendation text only. Avoid invented quotes or implied endorsements.

```html
<article class="card thesis">
  <span class="status">LinkedIn recommendation</span>
  <h3>Recommendation author</h3>
  <p>Verified recommendation text.</p>
  <div class="out"><b>Relationship:</b> Title or project context.</div>
</article>
```

---

## ✅ Quality checklist

Before sharing or publishing the application:

- [ ] Confirm all project descriptions are accurate
- [ ] Remove or generalize confidential information
- [ ] Verify employer, partner, and product naming permissions
- [ ] Confirm that no internal links or restricted data are exposed
- [ ] Replace placeholders with verified content
- [ ] Test every tab with a pointer and keyboard
- [ ] Test search and category filters
- [ ] Test copy buttons in the target environment
- [ ] Test the `#pvi-value` deep link on a normal hosted page
- [ ] Confirm the sandbox preview no longer throws a History API error
- [ ] Review color contrast and focus visibility
- [ ] Test at mobile, tablet, and desktop widths
- [ ] Validate the final HTML
- [ ] Recheck spelling, dates, statuses, and claims

---

## 🔐 Governance and responsible use

This portfolio discusses analytics, employee-related research, partner programs, software tooling, and AI-enabled concepts. Before external publication:

- Keep confidential, employee, partner, customer, and restricted data out of the file
- Present modeled values and scenarios separately from official system values
- Document assumptions and limitations
- Use human review for analytical and AI-generated outputs
- Confirm branding, naming, data handling, licensing, security, and publication permissions
- Treat recommendations as verified testimonials, not marketing copy to be invented

> 🛡️ **Trust is part of the product.** A polished portfolio is strongest when every claim is accurate, appropriately scoped, and easy to verify.

---

## 🧪 Suggested browser testing

Test the application in:

- Microsoft Edge
- Google Chrome
- Mozilla Firefox
- Safari, if the portfolio will be viewed on Apple devices
- The intended SharePoint or Teams preview
- A locally served environment
- The final static-hosting environment

Also test:

- Keyboard-only navigation
- Reduced-motion mode
- Narrow mobile width
- Browser zoom at 200%
- Clipboard permissions denied
- Sandbox preview with History API restrictions

---

## 🗺️ Future enhancements

Potential next improvements include:

- 🖼️ A professional headshot and individual visual identity
- 💬 A verified LinkedIn recommendations section
- 📊 Project-specific screenshots with accessible captions
- 🔎 Project filtering by skill, status, or business area
- 🌗 Dark and light themes with sandbox-safe preference handling
- 📄 Downloadable résumé
- 🔗 Public project, GitHub, or case-study links where appropriate
- 🧠 A short personal philosophy section
- 🚀 A deployment workflow for GitHub Pages or another approved static host
- 🧪 Automated HTML, accessibility, and browser checks

---

## 📦 Deployment notes

The application is static and does not require a backend. It can be deployed to any approved platform that serves HTML, CSS, and JavaScript.

For a public version:

1. Create a sanitized external copy.
2. Remove internal business-case and access-request content unless approved.
3. Replace internal terminology with audience-appropriate language.
4. Confirm all links and recommendation text.
5. Validate security, privacy, intellectual-property, and branding requirements.
6. Publish through an approved static hosting platform.

---

## 🤝 Contribution philosophy

This is a personal portfolio, but improvements should still follow a disciplined workflow:

```text
1. Define the change
2. Preserve a backup
3. Update one section at a time
4. Test the interaction
5. Test the sandbox preview
6. Review accessibility
7. Review content accuracy
8. Publish only the approved version
```

---

## 📄 License and attribution

The portfolio content belongs to its author unless otherwise noted. Product names, trademarks, certifications, and logos belong to their respective owners.

Do not reuse internal business information, partner information, recommendation text, or employer branding without authorization.

---

<div align="center">

## 🌈 The portfolio in one sentence

<strong>Research the question. Validate the evidence. Find the story. Build something useful.</strong>

<br><br>

Made with curiosity, econometrics, thoughtful design, and a healthy respect for browser security. ✨

</div>
