*To read this in a pretty version, press **⌘ + ⇧ + V** (Mac) or **Ctrl + Shift + V** (Windows)*

# GetShitDone 🚀

A full-stack to-do list application built as learning material for **Introduction to Back-End Web Development**.

High visual impact. Simple, readable code. Every line commented.

---

## Student Checklist 📝

Follow these steps to get your project live and ready for submission:

1.  **Configure Database**: Add your MongoDB Atlas URI to the `.env` file.
2.  **Configure Email**: Add your Gmail App Password credentials to the `.env` file.
3.  **Install Dependencies**: Run `npm install` in your terminal.
4.  **Start the App**: Run `npm run dev` to start the live development server.
5.  **Test Functionality**: Open [http://localhost:3000/dashboard](http://localhost:3000/dashboard) and verify you can add/edit tasks.
6.  **Customise**: Update styling, icons, fonts, and colours in the `public/` folder to make it your own!
7.  **Submit**: Upload your completed project to **Subject 3** in the [Student Hub](https://study.equinimcollege.com).
8.  **Celebrate**: Congrats team! You did it! 🥳

---

## Quick Start

```bash
# 1. Clone and enter the project
git clone <your-repo-url>
cd getshitdone

# 2. Edit .env with your MongoDB URI and Gmail credentials (see Environment Variables below)

# 3. Run the setup script (installs dependencies + starts server automatically)
npm run setup
```

That's it. Open `http://localhost:3000` in your browser.

> **First time?** You need [Node.js](https://nodejs.org/) v18+ installed. Get a free [MongoDB Atlas](https://cloud.mongodb.com/) account and a [Gmail App Password](https://myaccount.google.com/apppasswords).

---
**TASKS
1. check that your mongodb uri works (add uri to .env file)
2. check that your gmail app password works (add gmail credentials to .env file)
3. run npm install if you haven't already
4. start server in terminal (npm run dev)
5. make sure that the app works (go to http://localhost:3000/dashboard)
6. update styling, icon, fonts, colours etc. ( all in the front end folders )
7. upload this project to subject 3 in the student hub! (this is done online at https://study.equinimcollege.com)
8. congrats team! you did it!!!
**

---

## Design Philosophy

> *Design with emotion — build more usable and engaging products with emotion-driven UX.*

Dark immersive UI with an interactive animated gradient background, indigo/pink palette, material-web iconography, and smooth micro-interactions. Looks professional, reads simply.

---

## Tech Stack

### Front End
| Technology | Purpose |
|---|---|
| **HTML5** | Semantic page structure |
| **CSS3** (`style.css`) | Custom styles with CSS variables, layered on Pico CSS |
| **Pico CSS** (CDN) | Classless base framework for clean defaults |
| **Google Material Symbols** (CDN) | Iconography throughout the app |
| **Vanilla JavaScript** | DOM manipulation, fetch API, animations |
| **Inter + Space Grotesk** (Google Fonts) | Typography |

### Back End
| Technology | Purpose |
|---|---|
| **Node.js + Express.js** | Web server |
| **Mongoose + MongoDB Atlas** | Cloud NoSQL database |
| **CORS** | Cross-origin middleware |
| **Nodemailer** | Gmail SMTP for contact form |
| **dotenv** | Environment variable management |
| **nodemon** | Auto-restart in development |

---

## Project Structure

```
getshitdone/
│
├── public/                     # Front-end (served as static files by Express)
│   ├── index.html              # Landing page — hero, features, about, CTA
│   ├── dashboard.html          # Task dashboard — add, edit, delete, filter tasks
│   ├── features.html           # Pricing plans page
│   ├── login.html              # Login form (redirects to dashboard)
│   ├── register.html           # Registration form (redirects to dashboard)
│   ├── contact.html            # Contact form (sends email via /api/mail)
│   ├── privacy.html            # Privacy policy
│   ├── 404.html                # Error page
│   ├── css/
│   │   └── style.css           # All styles — colours & fonts labelled at top
│   └── js/
│       ├── background.js       # Animated gradient background (mouse-tracking)
│       ├── main.js             # Nav toggle, contact form, scroll reveals
│       └── app.js              # Dashboard CRUD — tasks via fetch API
│
├── server/
│   ├── index.js                # Express server — middleware, routes, DB connection
│   ├── routes/
│   │   ├── taskRoutes.js       # GET, POST, PUT, DELETE /api/tasks
│   │   └── mailRoute.js        # POST /api/mail/send-email
│   └── models/
│       └── task.js             # Mongoose schema — title, description, dueDate, completed
│
├── .env                        # Environment variables (NEVER commit this)
├── .gitignore                  # Ignores node_modules and .env
├── package.json                # Dependencies and npm scripts
└── README.md                   # This file
```

---

## What Each File Does

### Server Files

| File | Purpose |
|---|---|
| `server/index.js` | The main entry point. Sets up Express, connects to MongoDB, mounts API routes, serves the `public/` folder as static files. Prints coloured emoji status messages to the terminal on startup. |
| `server/models/task.js` | Defines the Mongoose schema for tasks — what fields each task has (`title`, `description`, `dueDate`, `completed`, `dateCreated`) and database indexes for fast sorting. |
| `server/routes/taskRoutes.js` | All CRUD routes for tasks: GET all, GET one, POST create, PUT update, DELETE remove. Each route talks to MongoDB through the Mongoose Task model. |
| `server/routes/mailRoute.js` | Single POST route that receives contact form data (name, email, message) and sends it as an email using Nodemailer and Gmail SMTP. |

### Front-End Files

| File | Purpose |
|---|---|
| `public/css/style.css` | Every style in the app. Colour variables and font variables are at the very top with links to tools for easy swapping. Sections are separated by clear comment banners. |
| `public/js/background.js` | Creates a full-screen animated gradient that follows the mouse (indigo glow) with two ambient blobs (pink + indigo) that drift independently. Uses `requestAnimationFrame` for 60fps. |
| `public/js/main.js` | Handles the mobile nav toggle, contact form submission (sends to `/api/mail/send-email`), toast notifications, and scroll-reveal animations on landing pages. |
| `public/js/app.js` | The dashboard brain. Loads tasks from the API, renders them as cards, handles add/edit/delete/toggle, manages filter tabs (All/Active/Completed), updates the progress bar, and controls the edit modal. |

### HTML Pages

| Page | What It Shows |
|---|---|
| `index.html` | Landing page — animated hero, feature cards, about section, CTA |
| `dashboard.html` | Task management — add bar, progress bar, filter tabs, task list, edit modal |
| `features.html` | Four pricing tier cards with feature lists |
| `login.html` | Login form (currently redirects to dashboard) |
| `register.html` | Registration form (currently redirects to dashboard) |
| `contact.html` | Contact form that sends a real email via the back end |
| `privacy.html` | Privacy policy page |
| `404.html` | Error page with big "404" and home link |

---

## Environment Variables (`.env`)

```env
# --- Database ---
# Get your connection string from MongoDB Atlas: https://cloud.mongodb.com
MONGO_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/getshitdone

# --- Email (Contact Form) ---
# Uses Gmail with an App Password (not your real password)
# Generate one at: https://myaccount.google.com/apppasswords
GMAIL_USER=youremail@gmail.com
GMAIL_PASS=your-16-char-app-password
MAIL_RECIPIENT=recipient@gmail.com

# --- Server ---
PORT=3000
```

| Variable | Purpose |
|----------|---------|
| `MONGO_URI` | MongoDB Atlas connection string |
| `GMAIL_USER` | Gmail address for sending contact emails |
| `GMAIL_PASS` | Gmail App Password (16 characters, not your real password) |
| `MAIL_RECIPIENT` | Email address that receives contact form submissions |
| `PORT` | Server port (defaults to 3000) |

---

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/tasks` | Get all tasks (sorted newest first) |
| `GET` | `/api/tasks/:id` | Get a single task by ID |
| `POST` | `/api/tasks` | Create a new task |
| `PUT` | `/api/tasks/:id` | Update a task |
| `DELETE` | `/api/tasks/:id` | Delete a task |
| `POST` | `/api/mail/send-email` | Send a contact form email |

### Example: Create a Task

```bash
curl -X POST http://localhost:3000/api/tasks \
  -H "Content-Type: application/json" \
  -d '{"title":"Buy groceries","description":"Milk, eggs, bread","dueDate":"2026-03-01"}'
```

---

## Mongoose Schema — Task

```javascript
{
  title:       { type: String, required: true },
  description: { type: String, required: true },
  dueDate:     { type: Date, required: true },
  dateCreated: { type: Date, default: Date.now },
  completed:   { type: Boolean, default: false }
}
```

---

## How It Works

```
Browser (HTML/CSS/JS)
    ↓ fetch('/api/tasks')
Express Server (server/index.js)
    ↓ routes → taskRoutes.js
Mongoose (models/task.js)
    ↓ .find() / .save() / .findByIdAndUpdate() / .findByIdAndDelete()
MongoDB Atlas (cloud database)
```

1. User interacts with the dashboard in their browser
2. JavaScript (`app.js`) sends `fetch()` requests to the Express API
3. Express routes (`taskRoutes.js`) handle the request
4. Mongoose talks to MongoDB Atlas to read/write data
5. Response flows back to the browser and updates the page

---

## Colour Scheme

All colours are CSS custom properties at the top of `style.css`:

```css
/* Tool: https://m3.material.io/theme-builder  |  https://coolors.co */
:root {
    --primary:         #6366F1;   /* Indigo — buttons, links, accents          */
    --primary-hover:   #4F46E5;   /* Deep Indigo — hover states                */
    --secondary:       #EC4899;   /* Pink — secondary accents, highlights      */
    --accent:          #10B981;   /* Emerald — success, completed states       */
    --bg-dark:         #020617;   /* Slate Black — page base                   */
    --card-bg:         #334155;   /* Slate — card surfaces                     */
    --text-main:       #F8FAFC;   /* Near White — headings, body               */
    --text-muted:      #CBD5E1;   /* Light Slate — descriptions, labels        */
    --border:          #475569;   /* Mid Slate — borders, dividers             */
    --danger:          #F43F5E;   /* Rose — delete, errors                     */
    --warning:         #FBBF24;   /* Amber — warnings                          */
}
```

Change any variable to re-theme the entire app instantly.

---

## Typography

Directly below the colours in `style.css`:

```css
/* Browse & swap: https://fonts.google.com  |  Guide: https://fonts.google.com/knowledge */
:root {
    --font-heading: 'Space Grotesk', sans-serif;  /* Bold, modern — headings */
    --font-body:    'Inter', sans-serif;           /* Clean, readable — body  */
}
```

To change fonts: swap the `@import` URL and update the variable values.

---

## Animations & UX

| Element | Effect | Method |
|---------|--------|--------|
| Background | Mouse-tracking glow + ambient drift | `requestAnimationFrame` in `background.js` |
| Hero text | Staggered fade-up | CSS `@keyframes fadeUp` + `animation-delay` |
| Buttons | Lift on hover | CSS `transform: translateY(-1px)` |
| Cards | Border glow on hover | CSS `transition` on `border-color` |
| Nav | Sticky + backdrop blur | CSS `backdrop-filter: blur(12px)` |
| Task add | Slide down into list | CSS `@keyframes slideDown` |
| Task complete | Strikethrough + opacity | CSS class `.completed` |
| Task delete | Fade + slide out | CSS `@keyframes fadeOut` |
| Toasts | Slide in from right | CSS `@keyframes slideInRight` |
| Inputs | Indigo focus ring | `box-shadow: 0 0 0 3px var(--shadow)` |
| Reduced motion | All animations disabled | `prefers-reduced-motion` query |

---

## NPM Scripts

| Command | What It Does |
|---------|-------------|
| `npm run setup` | Installs dependencies + starts the dev server in one command |
| `npm run dev` | Starts with nodemon (auto-restarts on file changes) |
| `npm start` | Starts without nodemon (for production) |
| `npm install` | Installs dependencies only |

---

## Learning Objectives

Students will learn:
- How a **web server** (Express) receives and responds to HTTP requests
- How a **NoSQL database** (MongoDB) stores and retrieves structured data
- How **Mongoose schemas** define data structure and validation
- How the **fetch API** connects front-end JavaScript to back-end endpoints
- How **environment variables** keep secrets out of source code
- How **Nodemailer** sends emails programmatically
- How **CSS variables** create maintainable, themeable stylesheets
- How a **REST API** follows GET/POST/PUT/DELETE conventions

---

## Credits

- [Pico CSS](https://picocss.com/) — Classless CSS framework
- [Google Fonts](https://fonts.google.com/) — Inter & Space Grotesk
- [Google Material Symbols](https://fonts.google.com/icons) — Iconography
- [MongoDB Atlas](https://cloud.mongodb.com/) — Cloud database

---
<!--  Built for EQC Institute of Technology by Intake 25g   -->
