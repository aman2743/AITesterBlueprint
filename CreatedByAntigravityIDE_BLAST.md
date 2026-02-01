# B.L.A.S.T. Protocol
## Selenium to Playwright Converter with Local LLM

---

## Phase 0: Blueprint 📋

### Project Overview
**Project Name:** Selenium2Playwright Converter  
**Purpose:** An intelligent code converter that transforms Selenium Java test automation code into Playwright JavaScript/TypeScript using local LLM (Ollama)

### Core Objectives
1. **Code Conversion Engine**
   - Parse Selenium Java test code
   - Analyze test structure and patterns
   - Generate equivalent Playwright JavaScript/TypeScript code
   - Preserve test logic and assertions

2. **LLM Integration**
   - Utilize Ollama for intelligent code transformation
   - Context-aware conversion with understanding of testing patterns
   - Handle complex scenarios and edge cases
   - Provide explanations for conversion decisions

3. **User Interface**
   - Web-based interface for code input/output
   - Side-by-side code comparison
   - Syntax highlighting for both languages
   - Download converted code
   - Conversion history and examples

4. **Quality Assurance**
   - Validate converted code syntax
   - Identify potential issues or limitations
   - Provide conversion confidence scores
   - Suggest manual review points

### Target Users
- QA Engineers migrating from Selenium to Playwright
- Development teams modernizing test automation
- Organizations transitioning testing frameworks
- Developers learning Playwright from Selenium background

### Success Metrics
- Accurate conversion of common Selenium patterns
- Functional Playwright code output
- User-friendly interface with clear feedback
- Fast conversion times (< 30 seconds for typical test)
- High user satisfaction with conversion quality

---

## Phase 1: Layout 🎨

### Application Structure

#### Frontend Architecture
```
frontend/
├── index.html          # Main application page
├── styles/
│   ├── main.css       # Core styles and design system
│   ├── editor.css     # Code editor styling
│   └── components.css # Component-specific styles
├── scripts/
│   ├── app.js         # Main application logic
│   ├── editor.js      # Code editor management
│   ├── api.js         # Backend API communication
│   └── utils.js       # Utility functions
└── assets/
    ├── icons/         # UI icons
    └── examples/      # Sample code snippets
```

#### Backend Architecture
```
backend/
├── server.py          # Flask/FastAPI server
├── converter/
│   ├── parser.py      # Selenium code parser
│   ├── transformer.py # Code transformation logic
│   ├── generator.py   # Playwright code generator
│   └── validator.py   # Output validation
├── llm/
│   ├── ollama_client.py  # Ollama integration
│   ├── prompts.py     # LLM prompt templates
│   └── context.py     # Context management
├── models/
│   ├── conversion.py  # Conversion data models
│   └── history.py     # Conversion history
└── utils/
    ├── logger.py      # Logging utilities
    └── config.py      # Configuration management
```

#### Database Schema (Optional - SQLite)
```
conversions:
  - id (PRIMARY KEY)
  - input_code (TEXT)
  - output_code (TEXT)
  - language_target (VARCHAR) # 'javascript' or 'typescript'
  - timestamp (DATETIME)
  - confidence_score (FLOAT)
  - status (VARCHAR)
```

### UI Layout Design

#### Main Interface Sections
1. **Header**
   - Application title and logo
   - Language selector (JavaScript/TypeScript)
   - Settings/configuration button
   - Theme toggle (light/dark)

2. **Code Input Panel (Left)**
   - Selenium Java code editor
   - Line numbers
   - Syntax highlighting
   - File upload option
   - Clear/Reset button
   - Example snippets dropdown

3. **Code Output Panel (Right)**
   - Playwright code display
   - Syntax highlighting
   - Copy to clipboard button
   - Download as file button
   - Confidence score indicator

4. **Control Panel (Center/Bottom)**
   - Convert button (primary action)
   - Loading indicator
   - Progress status
   - Error messages/warnings

5. **Additional Features Panel**
   - Conversion notes/explanations
   - Detected patterns
   - Manual review suggestions
   - Conversion history (collapsible)

### Navigation Flow
```
Landing Page
    ↓
Main Converter Interface
    ↓
[Input Code] → [Convert] → [Output Code]
    ↓
[Download/Copy] or [New Conversion]
```

---

## Phase 2: Aesthetics 🎨

### Design Philosophy
**Modern, Professional, Developer-Focused**
- Clean and minimalist interface
- Focus on code readability
- Smooth transitions and interactions
- Accessible and intuitive

### Color Palette

#### Primary Colors
- **Deep Blue:** `#1e3a8a` - Primary actions, headers
- **Bright Blue:** `#3b82f6` - Interactive elements, links
- **Accent Cyan:** `#06b6d4` - Success states, highlights

#### Secondary Colors
- **Dark Gray:** `#1f2937` - Dark mode background
- **Medium Gray:** `#6b7280` - Secondary text
- **Light Gray:** `#f3f4f6` - Light mode background
- **White:** `#ffffff` - Cards, panels

#### Semantic Colors
- **Success Green:** `#10b981` - Successful conversion
- **Warning Amber:** `#f59e0b` - Warnings, review needed
- **Error Red:** `#ef4444` - Errors, failures
- **Info Blue:** `#3b82f6` - Information, tips

### Typography
- **Primary Font:** 'Inter' (UI elements)
- **Code Font:** 'Fira Code' or 'JetBrains Mono' (code editors)
- **Headings:** Bold, 24px-32px
- **Body Text:** Regular, 14px-16px
- **Code Text:** 13px-14px with ligatures

### Visual Elements

#### Code Editors
- Monaco Editor or CodeMirror integration
- Syntax highlighting for Java and JavaScript/TypeScript
- Line numbers and code folding
- Minimap for large files
- Diff view for comparison

#### Buttons
- **Primary Button:** Solid blue, rounded corners, subtle shadow
- **Secondary Button:** Outlined, transparent background
- **Icon Buttons:** Minimal, hover effects
- **Hover States:** Slight scale, color shift

#### Cards & Panels
- Subtle shadows for depth
- Rounded corners (8px-12px)
- Border for light mode
- Smooth transitions on interactions

#### Animations
- Fade-in for content loading
- Slide transitions for panels
- Pulse effect for loading states
- Smooth scroll for navigation

### Responsive Design
- **Desktop (1920px+):** Full side-by-side layout
- **Laptop (1280px-1919px):** Comfortable side-by-side
- **Tablet (768px-1279px):** Stacked with tabs
- **Mobile (< 768px):** Single column, swipe between views

---

## Phase 3: Structure 🏗️

### Technology Stack

#### Frontend
- **HTML5** - Semantic markup
- **CSS3** - Modern styling with CSS Grid and Flexbox
- **Vanilla JavaScript** (ES6+) - Core functionality
- **Optional:** TypeScript for type safety
- **Code Editor:** Monaco Editor (VS Code's editor)
- **Icons:** Lucide Icons or Heroicons

#### Backend
- **Python 3.9+**
- **FastAPI** - Modern, fast web framework
- **Uvicorn** - ASGI server
- **Pydantic** - Data validation
- **Ollama Python Client** - LLM integration

#### LLM
- **Ollama** - Local LLM runtime
- **Recommended Models:**
  - CodeLlama (13B or 34B)
  - DeepSeek Coder
  - Mistral (for general understanding)

#### Development Tools
- **Git** - Version control
- **npm** - Package management (if using build tools)
- **Python venv** - Virtual environment
- **pytest** - Testing framework

### API Endpoints

#### POST `/api/convert`
**Request:**
```json
{
  "code": "string",
  "target_language": "javascript" | "typescript",
  "options": {
    "include_comments": true,
    "preserve_structure": true
  }
}
```

**Response:**
```json
{
  "success": true,
  "converted_code": "string",
  "confidence_score": 0.95,
  "notes": ["array of conversion notes"],
  "warnings": ["array of warnings"],
  "conversion_id": "uuid"
}
```

#### GET `/api/examples`
**Response:**
```json
{
  "examples": [
    {
      "name": "Basic Navigation",
      "selenium_code": "string",
      "playwright_code": "string"
    }
  ]
}
```

#### GET `/api/history`
**Response:**
```json
{
  "conversions": [
    {
      "id": "uuid",
      "timestamp": "ISO-8601",
      "preview": "string",
      "target_language": "javascript"
    }
  ]
}
```

### Core Components

#### 1. Code Parser
- Extract test methods and structure
- Identify Selenium commands and locators
- Parse assertions and wait conditions
- Detect page object patterns

#### 2. LLM Converter
- Construct context-aware prompts
- Send code to Ollama with conversion instructions
- Parse LLM response
- Handle streaming responses

#### 3. Code Generator
- Format output code
- Add necessary imports
- Structure test files
- Apply code style conventions

#### 4. Validator
- Check syntax validity
- Verify Playwright API usage
- Identify potential runtime issues
- Calculate confidence scores

### Conversion Mapping Examples

#### WebDriver Initialization
**Selenium Java:**
```java
WebDriver driver = new ChromeDriver();
```

**Playwright JavaScript:**
```javascript
const browser = await chromium.launch();
const page = await browser.newPage();
```

#### Element Interaction
**Selenium Java:**
```java
driver.findElement(By.id("username")).sendKeys("testuser");
driver.findElement(By.cssSelector("button[type='submit']")).click();
```

**Playwright JavaScript:**
```javascript
await page.fill('#username', 'testuser');
await page.click('button[type="submit"]');
```

#### Assertions
**Selenium Java:**
```java
Assert.assertEquals(driver.getTitle(), "Dashboard");
```

**Playwright JavaScript:**
```javascript
await expect(page).toHaveTitle('Dashboard');
```

---

## Phase 4: Tasks ✅

### Development Phases

#### Phase 4.1: Environment Setup
- [ ] Create project directory structure
- [ ] Initialize Git repository
- [ ] Set up Python virtual environment
- [ ] Install Ollama and download model (CodeLlama 13B)
- [ ] Create requirements.txt
- [ ] Set up basic FastAPI server
- [ ] Create frontend HTML structure

#### Phase 4.2: Backend Core Development
- [ ] Implement Ollama client integration
- [ ] Create conversion prompt templates
- [ ] Build Selenium code parser
- [ ] Develop code transformation logic
- [ ] Implement Playwright code generator
- [ ] Add output validation
- [ ] Create API endpoints
- [ ] Add error handling and logging

#### Phase 4.3: Frontend Development
- [ ] Design and implement UI layout
- [ ] Integrate Monaco Editor
- [ ] Implement syntax highlighting
- [ ] Create conversion form and controls
- [ ] Build result display panel
- [ ] Add copy/download functionality
- [ ] Implement example snippets
- [ ] Add loading states and animations

#### Phase 4.4: LLM Integration
- [ ] Design effective conversion prompts
- [ ] Implement context building
- [ ] Add streaming response handling
- [ ] Create fallback mechanisms
- [ ] Optimize prompt engineering
- [ ] Test with various code patterns
- [ ] Fine-tune confidence scoring

#### Phase 4.5: Testing & Validation
- [ ] Unit tests for parser
- [ ] Unit tests for generator
- [ ] Integration tests for API
- [ ] End-to-end conversion tests
- [ ] Test with real Selenium code samples
- [ ] Validate Playwright output
- [ ] Performance testing
- [ ] Error handling verification

#### Phase 4.6: Enhancement & Polish
- [ ] Add conversion history
- [ ] Implement dark/light theme
- [ ] Add keyboard shortcuts
- [ ] Create user documentation
- [ ] Add example library
- [ ] Optimize performance
- [ ] Improve error messages
- [ ] Add analytics/metrics

#### Phase 4.7: Deployment
- [ ] Create deployment documentation
- [ ] Set up production configuration
- [ ] Create Docker container (optional)
- [ ] Write README.md
- [ ] Create user guide
- [ ] Prepare demo examples
- [ ] Final testing
- [ ] Release v1.0

---

## Current Status

**Phase:** 0 - Blueprint ✅ COMPLETED  
**Next Phase:** 1 - Layout  
**Last Updated:** 2026-02-01

---

## Notes & Decisions

### Key Design Decisions
1. **Local LLM Choice:** Using Ollama for privacy and offline capability
2. **Target Languages:** Supporting both JavaScript and TypeScript output
3. **Architecture:** Separated frontend/backend for flexibility
4. **Editor:** Monaco Editor for professional code editing experience

### Challenges to Address
1. Complex Selenium patterns may require manual review
2. Page Object Model conversion needs special handling
3. TestNG/JUnit annotations need framework-specific conversion
4. Implicit vs explicit waits conversion strategy

### Future Enhancements
- Batch conversion support
- CI/CD integration
- VS Code extension
- Support for other languages (Python, C#)
- Advanced pattern recognition
- Custom conversion rules

---

## Resources

### Documentation
- [Selenium WebDriver Docs](https://www.selenium.dev/documentation/)
- [Playwright Docs](https://playwright.dev/)
- [Ollama Documentation](https://ollama.ai/docs)
- [FastAPI Documentation](https://fastapi.tiangolo.com/)

### Code Examples Repository
- Common Selenium patterns
- Equivalent Playwright code
- Edge cases and solutions
- Best practices guide

---

**Blueprint Status:** ✅ COMPLETE  
**Ready for Phase 1:** YES
