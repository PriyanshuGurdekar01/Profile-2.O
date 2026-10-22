# Requirements Document

## Introduction

A highly creative, premium, dynamic Bento-Grid portfolio website for Priyanshu Gurdekar. The site presents personal, project, education, tech stack, and social information through an interactive grid of cards with Apple-esque aesthetics — dark minimalist backgrounds, glassmorphism effects, smooth Framer Motion micro-interactions, and a fully responsive layout. Built with Next.js (App Router), Tailwind CSS, and Framer Motion.

## Glossary

- **Portfolio_App**: The Next.js application that serves the full portfolio website.
- **Bento_Grid**: The CSS grid layout container that arranges all cards in a bento-style arrangement.
- **Card**: An individual grid cell with glassmorphism styling and tilt interaction behavior.
- **Hero_Card**: The primary card spanning 2 columns × 2 rows, displaying name, tagline, and dynamic greeting.
- **Projects_Card**: The card spanning 2 columns × 2 rows, displaying interactive project entries.
- **TechStack_Card**: The card spanning 1 column × 2 rows, displaying floating technology badges.
- **Education_Card**: The card spanning 1 column × 2 rows, displaying the education timeline.
- **Social_Card**: The card spanning 1 column × 1 row, displaying social media links.
- **Gradient_Orb**: The animated background element inside the Hero_Card that follows cursor movement.
- **Greeting_Rotator**: The animated component that cycles through multilingual greeting strings.
- **Tilt_Effect**: The Framer Motion–powered 3D rotation applied to Cards on mouse movement.
- **Tech_Badge**: An individual technology pill/badge inside the TechStack_Card with drag and hover physics.
- **Timeline_Indicator**: The glowing pulsing dot used in the Education_Card timeline.
- **Radar_Animation**: The circular SVG or CSS animation that plays on hover of the "Autonomous Sensor Mini-Gun" project entry.
- **Fluid_Canvas**: The mini visualizer that plays on hover of the "Air Drawing & Gesture Canvas" project entry.
- **Flip_Card**: The score tracker element that plays on hover of the "Retro Smart Guessing Game" project entry.

---

## Requirements

### Requirement 1: Application Foundation

**User Story:** As a visitor, I want a fast, well-structured page, so that I can browse the portfolio without delays or layout issues.

#### Acceptance Criteria

1. THE Portfolio_App SHALL be built using Next.js App Router with a single-page layout served from the root route (`/`).
2. THE Portfolio_App SHALL use Tailwind CSS for all layout and styling, with a base background color of `#0B0F19`.
3. THE Portfolio_App SHALL load Framer Motion, Lucide React, and Simple Icons as runtime dependencies.
4. WHEN the page is loaded, THE Portfolio_App SHALL render all five Cards successfully within the Bento_Grid without layout shift (CLS score of 0); a page where fewer than five Cards are rendered SHALL NOT be considered compliant.
5. THE Portfolio_App SHALL set the document `<html>` element to `dark` mode class so Tailwind dark-mode utilities apply globally.

---

### Requirement 2: Bento Grid Layout

**User Story:** As a visitor, I want an elegant grid layout that adapts to my screen size, so that the portfolio looks great on any device.

#### Acceptance Criteria

1. THE Bento_Grid SHALL use CSS Grid with a 4-column base layout on screens ≥ 1024px (lg breakpoint).
2. THE Bento_Grid SHALL collapse to a 2-column layout on screens between 640px and 1023px (sm–md breakpoints).
3. THE Bento_Grid SHALL collapse to a 1-column layout on screens < 640px (mobile).
4. WHEN rendered at lg breakpoint, THE Hero_Card SHALL span 2 columns and 2 rows within the Bento_Grid.
5. WHEN rendered at lg breakpoint, THE Projects_Card SHALL span 2 columns and 2 rows within the Bento_Grid.
6. WHEN rendered at lg breakpoint, THE TechStack_Card SHALL span 1 column and 2 rows within the Bento_Grid.
7. WHEN rendered at lg breakpoint, THE Education_Card SHALL span 1 column and 2 rows within the Bento_Grid.
8. WHEN rendered at lg breakpoint, THE Social_Card SHALL span 1 column and 1 row within the Bento_Grid.
9. WHEN rendered below lg breakpoint, EACH Card SHALL span the full available column width of the collapsed layout.

---

### Requirement 3: Card Base Styling and Tilt Effect

**User Story:** As a visitor, I want every card to feel premium and interactive, so that the portfolio communicates craft and attention to detail.

#### Acceptance Criteria

1. EACH Card SHALL have a glassmorphism background using a semi-transparent dark fill (`rgba(255,255,255,0.03)` to `rgba(255,255,255,0.07)`), a subtle border (`border: 1px solid rgba(255,255,255,0.08)`), and a `backdrop-filter: blur(12px)` effect.
2. EACH Card SHALL have a `border-radius` of at least `16px`.
3. WHEN the user moves the cursor over a Card, THE Card SHALL apply the Tilt_Effect, rotating up to ±8 degrees on the X and Y axes using Framer Motion `useMotionValue` and `useTransform`.
4. WHEN the cursor leaves a Card, THE Card SHALL smoothly return to 0 degrees rotation using a spring animation with `stiffness: 300` and `damping: 30`.
5. THE Tilt_Effect SHALL be disabled on touch devices (screens with no hover capability) to avoid sticky tilt states.

---

### Requirement 4: Hero Profile Card

**User Story:** As a visitor, I want to immediately see Priyanshu's name, tagline, and a warm multilingual greeting, so that I understand who this portfolio belongs to.

#### Acceptance Criteria

1. THE Hero_Card SHALL display the text "Priyanshu Gurdekar" as the primary heading using a font size of at least `2.5rem` on desktop.
2. THE Hero_Card SHALL display the tagline "Bridging the gap between creative design and clean, scalable engineering." as a secondary text element below the name.
3. THE Hero_Card SHALL render the Gradient_Orb as an absolutely-positioned element behind the text content.
4. WHEN the cursor moves within the Hero_Card, THE Gradient_Orb SHALL translate its position to follow the cursor using Framer Motion `useMotionValue` with a `damping: 25` spring, with movement capped at ±60px from center. WHEN the cursor leaves the Hero_Card, THE Gradient_Orb SHALL stop following and remain at its last position.
5. THE Gradient_Orb SHALL continuously animate a soft pulsing scale (between `0.95` and `1.05`) with a 4-second loop using Framer Motion `animate`.
6. THE Greeting_Rotator SHALL cycle through at minimum the greetings: "Hello", "Namaste 🙏", "Bonjour", "Hola", "こんにちは" with each greeting displayed for 2500ms.
7. WHEN transitioning between greetings, THE Greeting_Rotator SHALL use a fade-out then fade-in animation with an `opacity` transition duration of 400ms.

---

### Requirement 5: Interactive Projects Card

**User Story:** As a visitor, I want to explore Priyanshu's projects with engaging hover interactions, so that each project feels alive and memorable.

#### Acceptance Criteria

1. THE Projects_Card SHALL display three project entries: "Autonomous Sensor Mini-Gun", "Air Drawing & Gesture Canvas", and "Retro Smart Guessing Game".
2. EACH project entry SHALL display a project title and a one-line description.
3. WHEN the user hovers over the "Autonomous Sensor Mini-Gun" entry, THE Projects_Card SHALL display the Radar_Animation — a CSS/SVG circular scan with a rotating sweep arm rendered inside that entry.
4. THE Radar_Animation SHALL complete one full 360° rotation every 2 seconds.
5. WHEN the user hovers over the "Air Drawing & Gesture Canvas" entry, THE Projects_Card SHALL display the Fluid_Canvas — an animated looping path or particle effect mimicking a brushstroke or fluid trace.
6. WHEN the user hovers over the "Retro Smart Guessing Game" entry, THE Projects_Card SHALL display the Flip_Card — a 3D CSS flip card animation revealing a mock score or stat on the back face.
7. WHEN the user stops hovering over a project entry, THE Projects_Card SHALL smoothly hide the hover animation within 300ms.

---

### Requirement 6: Dynamic Tech Stack Card

**User Story:** As a visitor, I want to see Priyanshu's technical skills in an engaging visual format, so that I can quickly grasp his capabilities.

#### Acceptance Criteria

1. THE TechStack_Card SHALL display Tech_Badge elements for: HTML5, CSS3, JavaScript, C++, Python, and Arduino.
2. EACH Tech_Badge SHALL display the technology name and its corresponding icon (from Simple Icons or Lucide React).
3. WHEN the user hovers over a Tech_Badge, THE Tech_Badge SHALL scale to `1.15` and display a glow matching the technology's brand color using a `box-shadow` animation.
4. THE brand glow colors SHALL be: HTML5 → `#E34F26`, CSS3 → `#1572B6`, JavaScript → `#F7DF1E`, C++ → `#00599C`, Python → `#3776AB`, Arduino → `#00979D`.
5. EACH Tech_Badge SHALL support Framer Motion drag within the bounds of the TechStack_Card, with a `dragConstraints` set to the card container ref.
6. WHEN a Tech_Badge is dragged and released, THE Tech_Badge SHALL spring back to its origin position using a Framer Motion spring with `stiffness: 400` and `damping: 30`.

---

### Requirement 7: Education Timeline Card

**User Story:** As a visitor, I want to see Priyanshu's educational background in a clean visual timeline, so that I can understand his academic context.

#### Acceptance Criteria

1. THE Education_Card SHALL display a vertical timeline entry for "B.Tech in Computer Science and Technology (CST)".
2. THE Education_Card SHALL display the institution name and expected graduation year alongside the program name.
3. EACH timeline entry SHALL include a Timeline_Indicator — a circular dot on the left edge connected to a vertical line.
4. WHEN the user hovers over a timeline entry, THE Timeline_Indicator SHALL scale from `1.0` to `1.4` and display a pulsing glow animation using Framer Motion `animate` with a 1-second repeat.
5. THE vertical timeline line SHALL use a gradient from the accent color (`#6366F1`) to transparent toward the bottom.

---

### Requirement 8: Social Connect Card

**User Story:** As a visitor, I want quick access to Priyanshu's professional profiles, so that I can connect with him on relevant platforms.

#### Acceptance Criteria

1. THE Social_Card SHALL display link entries for LinkedIn, GitHub, and Instagram.
2. EACH link entry SHALL display the platform name and its corresponding icon.
3. EACH link entry SHALL be a functional anchor element (`<a>`) that opens the respective profile URL in a new browser tab (`target="_blank"` with `rel="noopener noreferrer"`).
4. WHEN the user hovers over a link entry, THE Social_Card SHALL animate an arrow icon sliding in from the left while the platform label slides slightly to the right, using a Framer Motion `x` translate transition of 6px over 200ms.
5. EACH link entry SHALL have a visible focus ring for keyboard navigation accessibility.

---

### Requirement 9: Typography and Color System

**User Story:** As a visitor, I want a consistent, high-contrast visual language, so that the content is easy to read and the design feels cohesive.

#### Acceptance Criteria

1. THE Portfolio_App SHALL use a primary background color of `#0B0F19` for the page and `#111827` as the Card surface color.
2. THE Portfolio_App SHALL use white (`#FFFFFF`) for primary headings and `rgba(255,255,255,0.6)` for secondary/body text.
3. THE Portfolio_App SHALL use `#6366F1` (indigo) as the primary accent color for glows, borders, and indicators.
4. THE Portfolio_App SHALL load and apply a premium sans-serif typeface (Inter or Geist) for all text content.
5. EACH Card heading SHALL use a font weight of 600 or higher to maintain readability against dark backgrounds.

---

### Requirement 10: Accessibility and Performance

**User Story:** As a visitor using assistive technology or a slow connection, I want the portfolio to be usable and fast, so that I'm not excluded from accessing the content.

#### Acceptance Criteria

1. EACH Card SHALL have a meaningful `aria-label` or contain semantic HTML elements (`<section>`, `<h2>`, `<article>`) so screen readers can navigate the content.
2. EACH interactive element (link, draggable badge, project entry) SHALL be focusable via keyboard and have a visible focus indicator.
3. THE Portfolio_App SHALL achieve a Lighthouse Performance score of 85 or higher on desktop.
4. ALL animations SHALL respect the `prefers-reduced-motion` media query — WHEN the user has reduced motion enabled, THE Portfolio_App SHALL disable or minimize all Framer Motion animations.
5. EACH image or icon used SHALL have an appropriate `alt` attribute or `aria-label`.
