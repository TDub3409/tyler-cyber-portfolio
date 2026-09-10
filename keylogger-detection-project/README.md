Endpoint Keylogger Defense Test

This is a defensive project. I built a basic, controlled keylogger in Python and ran it against my own machine's endpoint protections to see what a real-world security tool would detect, flag, or miss.

Show Image Show Image

<!-- HOW TO USE THIS TEMPLATE - Replace anything in [BRACKETS] with your own words. - (SCREENSHOT: ...) marks where an image goes. Save images in /images and reference them like: ![caption](images/filename.png) - CROP before uploading: no full source code visible, no file paths showing your Windows username (C:\Users\tawoo\...). - Only write what actually happened. A miss is a real, useful finding. - Delete every comment block like this one before you publish. -->
Overview

[2-3 sentences: what you wanted to find out. e.g. "I wanted to know whether a basic, self-written keylogger would be caught by the endpoint protection already running on my own machine — both passively, and when directly scanned — or whether it would slip past default defenses the way real-world simple malware often does."]

Environment
Item	Details
OS	Windows [Version 10.0.26200.9445]
Endpoint protection	Aura Antivirus
Where it ran	On my machine
What the tool does

A short Python script using the pynput library that captures keystrokes system-wide and writes them to a local text file (log.txt). No network transmission, no persistence, no packaging or obfuscation.

Tests performed

I ran three separate tests to check detection from different angles:

1. Auto-scan on vs. off. Compared Aura's real-time/auto-scan protection in both states while the keylogger ran and wrote to log.txt.

(SCREENSHOT: Aura showing Auto-scan snoozed/off) (SCREENSHOT: Aura showing Auto-scan on) (SCREENSHOT: log.txt actively capturing keystrokes in each state)
![caption](images/ScreenshotResults of first test.png)

2. Manual targeted scan — idle. Ran a custom Aura scan directly against the project folder while the keylogger was not running.

(SCREENSHOT: Scan options showing the targeted folder — crop out the code editor and username in the file path)

3. Manual targeted scan — while running. Ran the same targeted scan against the same folder while the keylogger was actively running and writing to the log file.

(SCREENSHOT: scan result while running — crop out the code editor and username in the file path)

Results
Test	Result
Auto-scan off, keylogger running	[what you observed]
Auto-scan on, keylogger running	[what you observed]
Manual scan, idle	No threats found — 1,006 files scanned
Manual scan, actively running	No threats found — 1,006 files scanned

The manual scan result was identical whether the keylogger was idle or actively capturing and writing keystrokes — no difference in outcome between the two states.

Analysis — why did this happen?

The fact that the scan result didn't change between the idle and running states is itself informative: it suggests Aura's scan engine here is doing static, signature-based file analysis rather than runtime or behavioral monitoring. A static scan checks whether a file's contents match known malware signatures — it doesn't watch what a process actually does while it executes. A custom script built from a common, legitimate library (pynput) has no matching signature in that database, so it passed the check regardless of whether it was sitting idle or live-writing keystrokes to disk.

This points to a real limitation of signature-based antivirus: it's built to catch known threats, not to evaluate behavior. A tool that behaves exactly like malware — capturing input, writing it to disk — can still pass a scan cleanly if nothing about its file signature has been seen before. Catching this kind of tool would require behavioral detection: watching for the pattern (a process hooking keyboard input and writing to a file), not matching a signature.

What I'd add next
Instrument the host with Sysmon and forward logs to a SIEM (Splunk) to see what telemetry exists even when antivirus stays silent
Write a behavior-based detection rule that flags the pattern (input capture + repeated file writes) rather than relying on signature matching
Test the same tool against a second AV product to compare detection approaches
What I learned

[2-3 honest sentences — e.g. what this taught you about the difference between signature-based and behavioral detection, and why that distinction matters for real SOC/endpoint defense work.]

Built by Tyler Wood · github.com/TDub3409 · LinkedIn
