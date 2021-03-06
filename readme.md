# TotalFinder.osax

This source code implements scripting additions used by [TotalFinder](http://totalfinder.binaryage.com).

**TotalFinder** is a plugin for Apples's Finder.app which brings tabs, dual panels and more!

<a href="http://totalfinder.binaryage.com"><img width="500" src="http://totalfinder.binaryage.com/images/showcase/showcase-dual-mode.png"></a>

## Is this a replacement for SIMBL?

Yes, this is SIMBL-lite tailored specifically for TotalFinder.

You might want to read this article about my motivations:
[http://blog.binaryage.com/totalfinder-without-simbl](http://blog.binaryage.com/totalfinder-without-simbl)

## BATFinit event

Installs TotalFinder.bundle into running Finder.app (/Applications/TotalFinder.app is just a wrapper app for this script)

```AppleScript
tell application "Finder"
    -- give Finder some time to launch if it wasn't running (rare case)
    delay 1 -- this delay is important to prevent random "Connection is Invalid -609" AppleScript errors 
    try
        «event BATFinit»
    on error msg number num
        display dialog "Unable to launch TotalFinder." & msg & " (" & (num as text) & ")"
    end try
end tell
```

## BATFchck event

Check if TotalFinder is present in running Finder image.

```AppleScript
tell application "Finder"
    -- give Finder some time to launch if it wasn't running (rare case)
    delay 1 -- this delay is important to prevent random "Connection is Invalid -609" AppleScript errors 
    try
        «event BATFchck»
        set res to "present"
    on error msg number num
        set res to "not present"
    end try
    res
end tell
```
