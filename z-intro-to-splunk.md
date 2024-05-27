
Intro to Splunk (eLearning)
https://www.splunk.com/en_us/training/course-catalog.html?sort=Newest&filters=filterGroup1FreeCourses

use all the data in the environment to solve in less time

at the heart is the index:
- think of the index like a factory
- data is the raw materials being fed inside
- the inspectors look at the data and decide how to process it
- when they  find a match, they label the data with a source type 
    - that source type is used to break data into single events
    - the time stamps are normalized to a consistent format
- once ingested, can be searched and analyzed

Search results can be saved to **reports**, reports can be used to power **dashboard panels**

Knowledge can be organized into structured **data models** which are then used to visualize data and pivot without having to write custom searches

**alerts** allow you set custom triggers, notify to respond to incidents as soon as they occur. 

## splunk web interface

apps sit on top of the web UI, extending it. Think of them as work spaces, built to solve a specific use case

apps are set up by admin role

3 predefined roles
- admin
    - most powerful, install apps, create Knowl Obj for all users, ingest data
- power
    - can create / share knowledge objects with all users of an app
    - perform real time searches
- user
    - only see their own knowl obj and those shared with them

splunk cloud has sc_admin instead of admin role
cloud specific roles:
- can_delete
- token_auth
- apps

### home app

- manage other apps
- find documentation
- set a custom dashboard as your default dashboard
- can add apps / data if you have access from home app

### search & reporting

splunk bar appears in **every page** in splunk
(the top level black bar)
- can switch apps, edit account, view system messages, edit splunk config, monitor jobs and get help

Search bar: 
- time range picker: default 24 hours, narrow time resultls
- how to search panel links to docs and tutorials, as well as **data summary** button
    - data summary indexed by host / sources / sourcetypes
        - source: the file path or location of data or script from where event originated 
        - host: hostname/ip addr/ or FQDN from where data came
        - sourcetypes based on how it ID'd it (a classification of your data)

Table Views:
- a UI driven way to explore & prep the data without using splunk's search processing language

Search History:
- view & re-run past searches, can filter 

## Using Search 

example:
someone logging into server using bad credentials & failing

workflow:
- type "failed" into search bar
    - as type splunk starts suggesting matching terms
    - contextual matches
    - syntax documentation 
- let's look only over past week in time range picker
    - **limiting search by time is key to faster results & is a best practice**

### looking at the search page in detail

- New search job now makes a new search page
    - now can save as
    - search result tabs
    - search action buttons like download / print etc
    - search mode selector 
    - timeline 
- results in event list below
- fields extracted show up in sidebar from the events
- Save As
    - allows to save search as a knowledge object
- Events is default tab, for field extracting terms 
- patterns tab is next 
    - see patterns
- statistics tab
- visualization tab
    - pivot table / quick reports / search command docs are options to generate

**Transforming Commands:** commands that create statistics & visualiztions
    - transform event data into data tables

- "no event sampling"
    - can sample a random selection of the events (on the events tab)
- Sharing event: **by default a search job will remain active for 10 minutes after it is run**
    - it will need run the job again to give results after 10 min
    - Shared search jobs remain active for 7 days

Search modes from selector
- fast
    - cut down field info returned 
    - **field discovery** disabled, only returning info on default fields & fields required to fulfill the search 
- smart
    - toggle behavior based on type of search running
- verbose
    - as much field and event data as possible 

Timeline
    - dynamic based on time range picker, example each hour over last 7 days
    - zoom in / out

## Exploring events
how to use events returned by a search

- after a search you get events
- use events to expand search & interact w/ data 
- search terms highlighted
- returned in reverse chronological order
- time is normalized
    - time seen is based on the time zone in your user account
- accross bottom of each event are **selected fields**
    - default selected fields
        - host
        - source
        - sourcetype
- can click on text to add it to search / exclude or new search, or open in new window
    - add password to search for our example
- clicking on an event
    - see all the extracted fields for it
    - check mark boxes next to selected fields 
    - event actions drop down 
    - down arrow link for field actions 

## Using Search Terms

### wildcard
fail*
- start with fail

- search terms not case senstive 
- Booleans
    - AND / OR / NOT
`failed NOT password`
failed but not password
`failed OR password`

- no boolean AND is implied
- order of operation with (), use "" for precise 
- use escape \" to search for quotes

## What are commands?

search terms
- foundation of search queries

commands
- tell splunk what we want to do with the search results
- like create charts, compute stats, formatting

functions
- how we want to chart , compute and evaluate the results

arguments
- the variables we want to apply to the function

clauses
- how we want results grouped or defined

### example in a search 

`index=network sourcetype=cisco_wsa_squid usage=Violation | stats count(usage) as Visits`

index=network sourcetype=cisco_wsa_squid usage=Violation
- search terms


stats count(usage) as Visits
- stats: command
- count: function
- usage: argument
- as: clause

use | pipe to plug current results into next component

- this is searching cisco WSA for violations and counting over the last 30 days, then store that count in a field called `Visits` 

now append a `by` clause
`index=network sourcetype=cisco_wsa_squid usage=Violation | stats count(usage) as Visits by cs_username`
- can now filter by individual employees username 

the search command be used to filter results at any point in the search pipeline
    - the command behaves just like the search terms before the first pipe `...| search XYZ`
        - now allows you to search the results further down the search pipeline 
        - can use with Visits and Stats to find employees who violated more than once this month
            - `... | search Visits > 1`
        - *FYI better to filter before piping for better searches*

searching best practices:
1. no case senstive except:
    - if a command references a specific value, that value will be case sensitive
example:
`index=web sourcetype=access_combined purchase | replace www1 with server in host`

data:
Values      Count       %
www2        189         32.77%
www1        177         34.436%
ww3         148         28.794%

vs.
`index=web sourcetype=access_combined purchase | replace WWW1 with server1 in host`

use case:
replace host value www1
- the host value must be exact match in case sensitivity 

2. Using time to filter events is most effective, the less data you have to search the faster splunk will be

other fields to filter by that are good:
- default fields
    - index 
    - source 
    - host 
    - sourcetype
- these fields are extracted @ index time so not need extract for each search 

3. the more you tell the search engine, the better your results
example:
- better to search for "failed password", instead of just "password"

4. inclusion is generally better than exclusion
example:
searching for "access denied" is better than `NOT "access granted"`

5. when possible use the OR or IN operators instead of wildcards
example:
`user=admin OR user=administrator` vs `user IN (admin, administrator)`

6. apply filtering commands as early as possible in your search
filtering early limits the number of events, making future manipulations of the data faster
example:
sourcetype=*
(bad)
sourcetype=access_combined failed

## What are Knowledge Objects?

They help you discover and analyze your data

5 categories:
1. data interpretation
Some fields are automatically extracted from the data based on the selected sourcetype
- example:
    - action
    - categoryID
    - clientip
    - product_name
Field extractions: can add additional fields to extract to get more insight to data
calculated fields: added to events at searchtime & perform calcluations based on the values of existing fields

2. data classification
event types: allow you to categorize based on search terms
transaction: groups of conceptually related events that span time
3. data enrichment
lookups: allow you to add other fields and values to your events not included in the indexed data 
workflow actions: create links within events that interact with external resources or narrow our search
4. data normalization
tags: allow you to give descriptive names for key value pairs, search for events for particualr field values. AKA labels for your data 
field aliases: normalize data over multiple sources, assign one or more aliases to any extracted field & apply to fields in a lookup table
5. data models (searchtime matching of knowledge)
data models: hierarchicaly structured data sets, may consist of:
- events
- searches
- and/or transactions

KO are useful:
- can be created by one user and shared with permission settings
- saved and reused in different apps and searches 

Knowledge Manager Responsilities:
- oversee knowledge object creation
- implement best practices for naming conventions
- normalizing event data 
- creating data models for pivot users (keeping the toolbox clean and efficient)

## Creating Reports

what if we want to run the same search in the future or share with others?

example:
`index=security sourcetype=linux_secure host!=mail* "Failed password" src_ip=*`

one or two failed logins may just be user error, but multiple attempts may be a security incident. the team wants to know where these attempts happen

when looking at the sidebar, don't see any field for geography

append the `ip_location` command with the source ip field to add geo context to the returned events
`index=security sourcetype=linux_secure host!=mail* "Failed password" src_ip=* | iplocation src_ip | top limit=20 Country`
- now have new fields on the results. a country field shows up, expand it, top 10 values and count of where
- at the top of the pop up see 4 links to quick reports:
    - top values
    - top values by time
    - rare values
    - events with this field
- selecting the `top values` report, appends the `top` command to the search
    - now can visualize with bar / pie charts, but want a map
- replace top with geostats command to get map
`index=security sourcetype=linux_secure host!=mail* "Failed password" src_ip=* | iplocation src_ip | geostats count by Country`
- geostats allows us to use the context provided by the ip location comamnd to plot on a cluster or map

Now ready to share with ops. Share:
- Save as
    - report
        - title
        - desc
        - display in cluster map
        - whether to show time range picker or not
**best for your org to determine a naming convention**
- keep reports organized & easy to find
    - example: group the report is for, the type of object it is, and simple desc of what report contains:
        - `Security_report_FailedSshAttempts`

You can access all reports from the reports tab at the top in the application menu
- run the report again by clicking the name, or open in search 
- can clone, embed or delete
- reports by default just for owner 
    - can change permissions:
        - display for: 
            - app 
                - can share with all other users for the app it was created (search & reporting this example)
            - all apps: only avail for admin role
    - run as:
        - owner 
        - user 
            - if sensitive materials and want folks to not see sensitive data, run as user instead of owner 
    - edit schedule
        - run at timed intervals
        - good to reduce strain on environment for new ad hoc searches all the time 
        - especially good for broad audience reports or one in a dashboard embeded 
        - can define cron schedule
        - schedule window: in case multiple concurrent searches scheudled at same time
        - trigger actions:
            - log event
            - output results to lookup (to a CSV lookup file)
            - output results to telemetry endpoint
            - run a script
            - send email
            - send to splunk mobile\

## Creating Dashboards

visualizations can help use your data to tella  better story. 
let's figure out which accounts are associated with those events

start with same search terms (history, Add to Search)

example:
`index=security sourcetype=linux_secure host!=mail* "Failed password" src_ip=* | top limit=20 user`
expand user field in the side bar 
- use quick reports: `Top values` to find accounts most common getting login failures

Visualization
- bar chart or customize with format menu
    - pie chart
        - 20 is too crowded (default is 20 from search)
change to top 10
`index=security sourcetype=linux_secure host!=mail* "Failed password" src_ip=* | top limit=10 user`
share with coworkers by saving to dashboard
    - save as
        - new or existing dashboard
            - new (BCG logins)
            - title, permissions (private while developing)
            - classic dashboard or dashboard studio (classic for now)
            - panel title (Failed Logins by User)
            - pie chart 
            - advanced panel settings
                - powered by inline search, drilldown not enabled (can be configured to make it interactive), can be changed later

add more panels to tell a more comprehensive story, let's look at events by time to see if any spikes in login attempts
`index=security sourcetype=linux_secure host!=mail* "Failed password" src_ip=*`
a spike in accepted login attempts can also hint at a potential security incident
- take out failed password requirement to return all events related to login activity
`index=security sourcetype=linux_secure host!=mail* src_ip=*`
- in left field sidebar, expand `action` field (shows failures and success as values)
    - select top values by time report quick report, this appends the timechart command to the search 
`index=security sourcetype=linux_secure host!=mail* "Failed password" src_ip=* | timechart count by action limit=10`
- visualize data as line chart to see logins over time
- before saving, lets change the visual
    - options vary based on visual type
    - example column has stack mode, how fail vs success compare to one another 
    - example x/y axis, chart overlay, legend
        - move legend to left side, and set min and max data points
        - save to existing dashboard 
- can view and edit source XML for dashboard

## Dashboard studio

can take existing d-board and clone into d-board studio
- absolute (pixel perfect placement)
- grid (snap to alignment in rows)
    - good for charts, but custom shapes and icons and big images will need Absoulte 

splunk how to youtube
https://www.youtube.com/channel/UCjwOFZzLPnji1EstaVyyvAw
Splunk fundamentals playlist:
https://www.youtube.com/playlist?list=PL7zWAA-DF0k_sxswRiB7_GUTyI0FoV7lc

tour of splunk training platform:
https://www.splunk.com/en_us/resources/videos/take-a-tour-of-step.html
