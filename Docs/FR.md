| ID | Functional Requirement | Description |
|---|---|---|
| **FR001** | Independent Repository | Create a standalone public GitHub repository named `recipe-book-support-demo`, independent of `AI-Support-Bot` and `food-recipe-app-nextJS`. |
| **FR002** | Git Workflow | Protect `main`, develop each feature on a dedicated branch, make small commits, and merge changes through reviewed pull requests. |
| **FR003** | Project Scaffolding | Scaffold the application with Next.js App Router, TypeScript, ESLint, Tailwind CSS, and the `src/` directory convention. |
| **FR004** | Feature-Based Organization | Organize domain code under `src/features`, shared UI under `src/components`, utilities under `src/lib`, data under `src/data`, and shared types under `src/types`. |
| **FR005** | Application Layout | Create a root layout containing global styles, metadata, navigation, footer, privacy notice, and the single Chatwoot widget mount point. |
| **FR006** | Application Routing | Implement routes for Home, Recipes, Recipe Details, Search, Vegetarian Recipes, Favourites, Sign In, and Support. |
| **FR007** | Responsive Navigation | Provide desktop and mobile navigation with accessible links to all primary application routes. |
| **FR008** | Recipe Data Model | Define TypeScript types for recipes, ingredients, instructions, dietary categories, preparation time, difficulty, servings, and images. |
| **FR009** | Demo Recipe Dataset | Provide curated local recipe data containing enough believable entries to demonstrate search, filtering, recipe details, and favourites. |
| **FR010** | Recipe Listing | Display recipes using responsive cards containing an image, title, category, preparation time, difficulty, and favourite control. |
| **FR011** | Recipe Detail Page | Implement `/recipes/[slug]` to display the full recipe description, ingredients, instructions, preparation information, and dietary categories. |
| **FR012** | Recipe Search | Allow visitors to search recipes by title, ingredient, or category. |
| **FR013** | Search Result States | Display result counts, loading feedback, no-results guidance, and a way to clear the current search. |
| **FR014** | Dietary Filtering | Allow visitors to filter recipes by dietary category, including a visible Vegetarian option. |
| **FR015** | Vegetarian Page | Provide a dedicated `/vegetarian` route that displays vegetarian recipes and matches the bot’s support instructions. |
| **FR016** | Favourites Management | Allow visitors to add and remove recipes from their favourites. |
| **FR017** | Favourites Persistence | Persist favourites in browser storage so saved recipes remain available after refresh. |
| **FR018** | Favourites Page | Display saved recipes on `/favourites`, including an empty state and navigation back to recipe discovery. |
| **FR019** | Simulated Sign-In | Provide a clearly labelled demonstration sign-in flow without storing credentials or pretending to authenticate a real user. |
| **FR020** | Sign-In Troubleshooting State | Provide a predictable, demo-only sign-in problem that can be used to demonstrate approved troubleshooting guidance. |
| **FR021** | Support Page | Provide a `/support` page explaining supported topics, human-support availability, privacy expectations, and the purpose of the demonstration. |
| **FR022** | Loading States | Add route and component loading indicators where navigation or client-side initialization may take time. |
| **FR023** | Error States | Provide safe and understandable application, configuration, and route error messages. |
| **FR024** | Not-Found Handling | Provide a custom not-found page for invalid routes and unknown recipe slugs. |
| **FR025** | Chatwoot Instance Readiness | Confirm that the supported Chatwoot Community Edition v4.18.0 instance, PostgreSQL, Redis, workers, HTTPS, and public webhook endpoint are operational. |
| **FR026** | Dedicated Website Inbox | Create an isolated Chatwoot Website inbox named `Recipe Support`. |
| **FR027** | Inbox Domain Configuration | Configure the Website inbox with the production Vercel domain and document how preview and local environments are handled. |
| **FR028** | Widget Branding | Configure the widget name, colour, welcome heading, tagline, locale, launcher position, and availability behavior to match the website. |
| **FR029** | Employee Account | Create or invite the employee who will demonstrate human support and configure their display name, avatar, availability, and notifications. |
| **FR030** | Employee Inbox Membership | Add the employee to the Recipe Support inbox and verify that they can access and reply to its conversations. |
| **FR031** | Handoff Team | Create a Recipe Support team, add the appropriate employee, and record the team and optional individual-assignee identifiers. |
| **FR032** | Service User | Provision a dedicated, non-interactive Chatwoot service user for the backend operations that require broader read access. |
| **FR033** | Service User Restriction | Restrict the service user to the target account and inbox wherever Chatwoot permits and prevent interactive employee use. |
| **FR034** | Agent Bot Creation | Create a dedicated Recipe Support Agent Bot with a name, avatar, backend webhook URL, secret, and API access token. |
| **FR035** | Agent Bot Inbox Connection | Connect the Recipe Support Agent Bot to the Recipe Support inbox and verify that new conversations enter the bot workflow. |
| **FR036** | Chatwoot Identifier Configuration | Record and configure the Chatwoot account, inbox, Agent Bot, team, and optional employee identifiers in `AI-Support-Bot`. |
| **FR037** | Widget Component | Implement `src/features/support/components/ChatwootWidget.tsx` as a client component that asynchronously loads the Chatwoot SDK. |
| **FR038** | Single Widget Initialization | Mount the widget once from the root layout and prevent duplicate script insertion or initialization during remounting and navigation. |
| **FR039** | Public Widget Configuration | Configure the widget using `NEXT_PUBLIC_CHATWOOT_BASE_URL` and `NEXT_PUBLIC_CHATWOOT_WEBSITE_TOKEN`. |
| **FR040** | Missing Configuration Handling | If widget configuration is missing or invalid, keep the website operational and report only a safe diagnostic. |
| **FR041** | Widget Environment Isolation | Use separate inbox tokens or disable the widget for local, preview, and production environments as appropriate. |
| **FR042** | Anonymous Demo Identity | Keep widget visitors anonymous while the website uses simulated sign-in. Do not represent simulated users as verified Chatwoot contacts. |
| **FR043** | Authenticated Identity Validation | If real authentication is introduced, generate the Chatwoot identity HMAC server-side and expose only the resulting identifier hash to the browser. |
| **FR044** | Credential Isolation | Never expose Chatwoot API tokens, bot tokens, service-user tokens, webhook secrets, identity-validation secrets, or AI-provider credentials through `NEXT_PUBLIC_*`. |
| **FR045** | Signed Webhook Verification | Verify Chatwoot webhook signatures using the timestamp and exact raw request body before decoding the JSON payload. |
| **FR046** | Webhook Replay Protection | Reject expired timestamps and deduplicate webhook deliveries using the delivery identifier and permanent message business key. |
| **FR047** | Webhook Scope Validation | Accept processing only for the configured Chatwoot account and inbox while acknowledging validly signed out-of-scope events without creating work. |
| **FR048** | Webhook Event Filtering | Process only supported incoming, public customer text messages and safely ignore outgoing, private, updated, unknown, or unsupported events. |
| **FR049** | Durable Message Intake | Store accepted customer work durably before acknowledging the webhook so temporary worker failures do not lose messages. |
| **FR050** | Conversation State Reconciliation | Reconcile conversation status and assignment using fresh Chatwoot state rather than relying solely on webhook order or changed attributes. |
| **FR051** | Pending Bot Ownership | Verify that new Agent Bot conversations start in `pending` and are assigned to the configured Agent Bot before an automated response is allowed. |
| **FR052** | Conversation History Retrieval | Retrieve only the recent conversation history needed for context using the dedicated service user and prevent personal fields from entering model prompts. |
| **FR053** | Recipe Knowledge Snapshot | Create an immutable, versioned knowledge snapshot covering recipe search, vegetarian filtering, favourites, sign-in troubleshooting, and support availability. |
| **FR054** | Knowledge Provenance | Record the source, version, and approval status of every support answer included in the Recipe Support knowledge snapshot. |
| **FR055** | Knowledge Answer Scenario | Answer “How do I find vegetarian recipes?” using navigation and terminology that exist in the deployed website. |
| **FR056** | Feature Guidance Scenario | Answer “How do I save a recipe to my favourites?” consistently with the implemented favourite behavior. |
| **FR057** | Troubleshooting Scenario | Provide approved steps for “I cannot sign in” without asking the customer for a password or sensitive authentication information. |
| **FR058** | Grounding Requirement | Generate product answers only when supported by the approved Recipe Support knowledge snapshot. |
| **FR059** | Unsupported Request Boundary | Avoid inventing answers for unrelated, sensitive, unsupported, or insufficiently grounded questions and offer human assistance instead. |
| **FR060** | Public Bot Reply | Send the approved bot response to the Chatwoot conversation as one public outgoing message. |
| **FR061** | Duplicate Reply Prevention | Prevent duplicate customer-visible replies when Chatwoot retries a webhook or the worker retries an operation. |
| **FR062** | Human Handoff Detection | Detect explicit human requests and policy-triggered escalation conditions before generating another automated response. |
| **FR063** | Private Handoff Note | Add an employee-visible private note containing a concise reason for escalation and safe conversation context. |
| **FR064** | Handoff Status Transition | Change the conversation from `pending` to `open` so it becomes available to human support. |
| **FR065** | Handoff Assignment | Assign the conversation to the configured team and, when configured, the designated individual employee. |
| **FR066** | Handoff Labels and Priority | Preserve existing labels, add the approved handoff label, and set priority only when required by policy. |
| **FR067** | Bot Suppression After Handoff | Stop automated replies once handoff begins, a human owns the conversation, or the conversation is resolved. |
| **FR068** | Manual Dashboard Reply | Allow the employee to read the conversation and private note and send a public reply that appears in the customer widget. |
| **FR069** | Conversation Resolution | Allow the employee to resolve a completed conversation without deleting its history. |
| **FR070** | Customer Reply After Resolution | Verify and reconcile the behavior when a customer replies after resolution, preventing unintended or duplicate bot responses. |
| **FR071** | Return to Bot Queue | Document and test the controlled procedure for returning an eligible conversation to `pending` and restoring bot ownership. |
| **FR072** | Dashboard Operations | Verify assignment, status, priority, labels, private notes, inbox filters, and ownership from the employee dashboard. |
| **FR073** | Employee Notifications | Verify that the assigned employee receives the intended dashboard, browser, or email notification following handoff. |
| **FR074** | Demo Privacy Notice | Tell visitors that the site is a demonstration and that they must not enter real passwords, payment details, health information, or other sensitive data. |
| **FR075** | Personal Data Minimization | Collect only the contact and conversation data required for the demonstration. |
| **FR076** | Provider Data Minimization | Send only customer message content and minimum conversational context to the AI provider; exclude contact email, phone number, and unrelated attributes. |
| **FR077** | Safe Logging | Redact message content, credentials, contact data, and sensitive headers from application and infrastructure logs. |
| **FR078** | Data Retention | Define and enforce retention periods for demo contacts, conversations, message content, logs, and backend records. |
| **FR079** | Demo Data Deletion | Document how to remove demonstration contacts and conversations from Chatwoot and associated backend storage. |
| **FR080** | Security Headers | Configure Content Security Policy and related browser-security headers while allowing only required Chatwoot script, frame, API, and WebSocket origins. |
| **FR081** | HTTPS Requirement | Serve the website, Chatwoot instance, and bot webhook exclusively over HTTPS outside local development. |
| **FR082** | Environment Template | Commit a `.env.example` containing safe placeholders and explanations for required public configuration. |
| **FR083** | Secret Management | Store backend credentials in protected deployment environments or a secret manager, not in source control or frontend deployments. |
| **FR084** | Responsive Design | Ensure all primary routes and the Chatwoot launcher work on mobile, tablet, and desktop screen sizes. |
| **FR085** | Accessibility | Use semantic HTML, keyboard-accessible controls, visible focus states, labelled fields, alternative text, and sufficient colour contrast. |
| **FR086** | Unit Testing | Test recipe filtering, searching, formatting utilities, configuration validation, and other isolated logic. |
| **FR087** | Component Testing | Test recipe cards, search controls, favourites, sign-in states, privacy notices, and widget initialization behavior. |
| **FR088** | End-to-End Website Testing | Test browsing, searching, filtering, opening a recipe, saving a favourite, refreshing, and opening the support widget. |
| **FR089** | Webhook Contract Testing | Test valid, invalid, expired, duplicated, conflicting, private, outgoing, wrong-account, and wrong-inbox webhook cases. |
| **FR090** | Bot Response Testing | Test grounded answers, unsupported requests, processing failures, idempotency, and suppression after handoff. |
| **FR091** | Handoff Integration Testing | Test private-note creation, status opening, team or employee assignment, labels, priority, and bot suppression. |
| **FR092** | First Customer Message Test | Send a real message through the deployed widget and verify that exactly one contact, conversation, and incoming message appear in the intended inbox. |
| **FR093** | First Bot Response Test | Verify that the incoming message reaches `AI-Support-Bot` and that one grounded response appears in both Chatwoot and the widget. |
| **FR094** | Human Conversation Test | Verify that the employee can receive the handoff, reply from Chatwoot, and resolve the conversation while the bot remains suppressed. |
| **FR095** | Five-Scenario Acceptance Test | Run the knowledge, feature-guidance, troubleshooting, safety-boundary, and human-handoff scenarios against the deployed system. |
| **FR096** | Separate Vercel Project | Deploy the website as an independent Vercel project connected only to the `recipe-support-demo` repository. |
| **FR097** | Deployment Environments | Maintain distinct development, preview, and production configurations with appropriate Chatwoot inbox isolation. |
| **FR098** | Continuous Integration | Run formatting, linting, type checking, unit tests, component tests, and production build checks for every pull request. |
| **FR099** | Production Verification | Verify routes, layouts, widget loading, bot responses, handoff, console output, security headers, and credential isolation after deployment. |
| **FR100** | Operational Health Check | Provide a repeatable procedure for checking website availability, Chatwoot availability, webhook reachability, worker health, and bot-provider readiness. |
| **FR101** | Failure Handling | Provide safe customer and operator behavior when Chatwoot, the AI provider, the database, the queue, or the bot backend is unavailable. |
| **FR102** | Recovery Verification | Verify that accepted but interrupted work can be recovered without losing the customer message or sending duplicate replies. |
| **FR103** | Demo Reset Procedure | Document how to clear browser state, remove test conversations, restore bot ownership, reset employee availability, and prepare the environment. |
| **FR104** | Demonstration Script | Provide a timed five-minute script containing the exact customer prompts, expected bot answers, handoff actions, employee reply, and resolution step. |
| **FR105** | Operator Runbook | Document inbox setup, Agent Bot setup, credential rotation, failure diagnosis, handoff recovery, and demo reset procedures. |
| **FR106** | Project README | Document the project purpose, architecture, structure, local setup, commands, public variables, deployment, testing, and integration boundaries. |
| **FR107** | Architecture Diagram | Include a diagram showing the browser, Vercel website, Chatwoot inbox, signed webhook, AI-Support-Bot, provider, and employee dashboard. |
| **FR108** | Requirements Traceability | Map every automated test and manual acceptance check to one or more functional requirement IDs. |
| **FR109** | Final End-to-End Qualification | Execute the complete visitor-to-resolution workflow in production and retain a dated, non-sensitive qualification record. |
| **FR110** | Definition of Done | Declare the project complete only when all mandatory requirements pass, documentation is usable by another person, and the full demonstration can be repeated from a clean state. |