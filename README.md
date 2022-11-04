# EF Core Benchmark Performance
I start studying and then implementing testing EF Core performance by benchmarking actions. As a base I use https://github.com/jernejk/EFCoreSamples.StabilityAndPerformance with video https://www.youtube.com/watch?v=C9Fnysvvgvg&ab_channel=SSWTV%7CVideosfordevelopers%2Cbydevelopers <br/><br/>
This should take a week or so. Have to see are thing going smoothly. 

## Basic requirements
-SQL Server for SalesDB (it's .bak file https://stackoverflow.com/questions/1535914/import-bak-file-to-a-database-in-sql-server)<br/>
-https://github.com/codesenberg/bombardier for http request (connections and request etc) benchmarking<br/>
-- https://go.dev/dl/ install go(programming language) before Bombardier<br/>
-- go install github.com/codesenberg/bombardier@latest <-- installs bombardier <br/>
--- To run bombardier scripts in powershell https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.2  --> Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope CurrentUser and remove after usage Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser <br/>
--- set Path to bombardier in powershell $env:Path += ';C:\Users\YourUsernameInWindows\go\bin' bombardier.exe is in that folder from installion <br/>
Now you are able to run scripts like .ps1 files. --http2 flag needs to added to bombardier command to work. <br/>
Overwhelmed my machine - used all memory and prosessor time. Processor	11th Gen Intel(R) Core(TM) i5-1135G7 @ 2.40GHz, 2419 Mhz, 4 Core(s), 8 Logical Processor(s) and 16GB RAM. Stopped API process to make computer usable. Have to reduce number of connections to 2. I tought that my machine is quite good - for laptop yes. Maybe I have to make my son gaming computer part time server to test endurance. Then the 16GB RAM expancion seems double interest. Due swapping at laptop made performance nowhere.

# Original readme.md
https://github.com/jernejk/EFCoreSamples.StabilityAndPerformance
# EFCoreSamples.StabilityAndPerformance
Showing bad and good examples for EF Core that impacts stability and performance of the applications

I have worked on quite a few projects and have seen a lot of EF Core queries.
On those projects it's not uncommon to have developers that complains about EF Core performance.
In a lot of cases, the problem is how the queries are written. :)

In this repo, I'm trying to show common mistakes I have found and some tricks on how to get better performance without writing much code.
Of course, I'll include some optimizations where more code is required.

The idea is to learn patterns that gives you *free performance with as little work as possible and applying more advance pattern when performance issue is identified.

We should never permaturerly optimize software however, that does mean we should not implement easy performance gains. (you can look at them as tech debt more than premature optimizations)

DB Source: https://www.sqlskills.com/sql-server-resources/sql-server-demos/

I used this DB because it's simple but has enough data to demonstrate why certain patterns are very dangerous and you should always use more optimum patterns. (which sometimes results in less code and better redability on top of better performance)
