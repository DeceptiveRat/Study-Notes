1. Event Tracing for Windows (ETW)
- provides mechanism to trace and log events by user-mode apps and kernel-mode drivers
- components:
   - provider - emits events
   - consumer - receives events written to trace session
   - event trace session - records events from provider and stores in buffers
   - controller - controls trace sessions

2. ETW providers types
- MOF provider
   - based on Managed Object Format (MOF)
   - capable of generating events according to predefined MOF schemas
   - offer flexible approach to event generation 
- WPP provider
   - stands for Windows Software Trace Preprocessor
   - leverage specialized macros and annotations within application's source code to generate events
   - often utilized for low-level kernel-mode tracing and debugging
- Manifest-based provider
   - rely on XML manifest files that define the structure and characteristics of events
   - enhanced flexibility
   - ease of management
   - dynamic event generation and customization
- tracelogging provider
   - leverage TraceLogging API
   - streamlines process of event generation with minimal code overhead

reference:
- Microsoft - ETW: <https://learn.microsoft.com/en-us/windows-hardware/drivers/devtest/event-tracing-for-windows--etw->
- <https://www.preludesecurity.com/blog/event-tracing-for-windows-etw-your-friendly-neighborhood-ipc-mechanism>
- hack the box academy