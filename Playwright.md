# Architecture

code 
  --> playwright client
         (language binding and API layer)
         (converts code to structured messages -JSON format) 
         (Receive Responses from playwright core)
         (connects to playwright core via direct function calls(for inprocess)/websockets(Out-of-process))
         --> playwright core
            (executes browser automation)
            (Control browsers, manage contexts, execute commands)
            (connects to browser via websocket/pipe using Playwright Protocol(custom))
            --> Browser Driver
            (communicates to browser engine via native debugging protocols like CDP)
            --> (converts to playwright protocol command to browser native commands)
                --> Browser Engine
                (DOM / Render / JS Execution / Layout / Paint)

 ## Launches its own bundled Chromium build , stil can connect to actual install browser          
 ### limitations and subtle bottlenecks
  1. Not exactly the same as real end-user browsers
  2. Media, DRM, and OS-linked features missing
  3. Real-world browser updates aren’t reflected instantly
  4. Some real-user contexts aren’t replicated
      - No cookies or history across runs (isolated profile per launch).
      - Can’t test extensions, bookmarks, or saved logins.
      - Impact: affects workflows that depend on real user profiles or browser state.
  5. Limited system integration
    - Notifications, downloads, pop-up permissions, OS dialogs, or file pickers may behave slightly differently.
  
  # Playwrigt config
   ## defined in playwright.config
   ### an exported object that Playwright uses to control:

      Which browsers to test on

      Base URLs, timeouts, retries, etc.

      Test directory structure

      Reporter settings

      Parallel execution & sharding

      Project-level overrides (e.g. Chrome vs Safari)

      Fixtures and global setup/teardown
  ## configs: https://playwright.dev/docs/test-configuration
  ## Configuration priority
    1. CLI 
    2. Test Level
    3. config file

# test() = declarative test registration function
- provided by Playwright’s test runner (@playwright/test) and wraps:

  test metadata (title, timeout, retries, annotations),

  test hooks (fixtures, setup/teardown),

  and test execution logic (async function body).
  
  |         Concept         |                             Description                             |
|:-----------------------:|:-------------------------------------------------------------------:|
| test()                  | Defines a test unit (registered by the runner).                     |
| Input params ({ page }) | Injected fixtures from Playwright.                                  |
| Async body              | Actual test logic (steps, assertions).                              |
| Role                    | Core declarative function — main “test keyword.”                    |
| Analogy                 | Equivalent to it() in Jest/Mocha or “Test Case” in Robot Framework. |


|            Component           |                Purpose                |
|:------------------------------:|:-------------------------------------:|
| test()                         | Defines a test case.                  |
| test.describe()                | Groups tests logically.               |
| test.beforeEach/afterEach      | Setup/cleanup logic.                  |
| test.only/skip/fixme/fail/slow | Control test execution behavior.      |
| test.use()                     | Override context/fixtures for a test. |