# Secure_PLC_Coding

## Top 20 Secure PLC Coding Practices

https://plc-security.com/

1. Modularize PLC Code
    - Split PLC code into modules, using different function blocks (sub-routines). Test modules independently.
2. Track operating modes
    - Keep the PLC in RUN mode. If PLCs are not in RUN mode, there should be an alarm to the operators
3. Leave operational logic in the PLC wherever feasible
    - Leave as much operational logic e.g., totalizing or integrating, as possible directly in the PLC. The HMI does not get enough updates to do this well.
4. Use PLC flags as integrity checks
    - Put counters on PLC error flags to capture any math problems.
5. Use cryptographic and / or checksum integrity checks for PLC code
    - Use cryptographic hashes, or checksums if cryptographic hashes are unavailable, to check PLC code integrity and raise an alarm when they change
6. Validate timers and counters
    - If timers and counters values are written to the PLC program, they should be validate by the PLC for reasonableness and verify backward counts below zero
7. Validate and alert for paired inputs / outputs
    - If you have paired signals, ensure that both signals are not asserted together. Alarm the operator when input / output states occur that are physically not feasible. Consider making paired signals independent or adding delay timers when toggling outputs could be damaging to actuators.
8. Validate HMI input variables at the PLC level, not only at HMI
    - HMI access to PLC variables can (and should) be restricted to a valid operational value range at the HMI, but further cross-checks in the PLC should be added to prevent, or alert on, values outside of the acceptable ranges which are programmed into the HMI.
9. Validate indirections
    - Validate indirections by poisoning array ends to catch fence-post errors
10. Assign designated register blocks by function (read/write/validate)
    - Assign designated register blocks for specific functions in order to validate data, avoid buffer overflows and block unauthorized external writes to protect controller data.
11. Instrument for plausibility checks
    - Instrument the process in a way that allows for plausibility checks by cross-checking different measurements.
12. Validate inputs based on physical plausibility
    - Ensure operators can only input what’s practical or physically feasible in the process. Set a timer for an operation to the duration it should physically take. Consider alerting when there are deviations. Also alert when there is unexpected inactivity.
13. Disable unneeded / unused communication ports and protocols
    - PLC controllers and network interface modules generally support multiple communication protocols that are enabled by default. Disable ports and protocols that are not required for the application.
14. Restrict third-party data interfaces
    - Restrict the type of connections and available data for 3rd party interfaces. The connections and/or data interfaces should be well defined and restricted to only allow read/write capabilities for the required data transfer.
15. Define a safe process state in case of a PLC restart
    - Define safe states for the process in case of PLC restarts (e.g., energize contacts, deenergize, keep previous state).
16. Summarize PLC cycle times and trend them on the HMI
    - Summarize PLC cycle time every 2-3 seconds and report to HMI for visualization on a graph
17. Log PLC uptime and trend it on the HMI
    - Log PLC uptime to know when it’s been restarted. Trend and log uptime on the HMI for diagnostics
18. Log PLC hard stops and trend them on the HMI
    - Store PLC hard stop events from faults or shutdowns for retrieval by HMI alarm systems to consult before PLC restarts. Time sync for more accurate data.
19. Monitor PLC memory usage and trend it on the HMI
    - Measure and provide a baseline for memory usage for every controller deployed in the production environment and trend it on the HMI.
20. Trap false negatives and false positives for critical alerts
    - Identify critical alerts and program a trap for those alerts. Set the trap to monitor the trigger conditions and the alert state for any deviation.


Copyright (c) 2021 admeritia GmbH, Langenfeld/Rheinland, Germany

Permission is hereby granted, free of charge, to any person obtaining a copy of “Top 20 Secure PLC Coding Practices” and associated documentation files, to deal in the “Top 20 Secure PLC Coding Practices” without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the “Top 20 Secure PLC Coding Practices”, and to permit persons to whom the “Top 20 Secure PLC Coding Practices” is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the “Top 20 Secure PLC Coding Practices”.

THE “Top 20 Secure PLC Coding Practices” IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE “Top 20 Secure PLC Coding Practices” OR THE USE OR OTHER DEALINGS IN THE “Top 20 Secure PLC Coding Practices”.
