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
               