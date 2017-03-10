# intercom-events
Python script that automates the extraction of event data from Intercom

# Overview

Intercom is a great platform, but it leaves a lot to be desired on the analysis front. With the current API implementation, you can only pull down events on a USER level, which means that analyzing events that have occurred for multiple users is basically impossible. This makes it really hard to determine which actions are critical in an onboarding process, which actions (or lack of actions) lead to churn, and a host of other activities.

The goal of this toolset is to automate the extraction of event data from Intercom given a list of valid user IDs. Eventually they'll probably release a workaround, but until then I'll need to get the data this way.

# Summary of Functions

The function should take in a CSV list of valid user ID's in Intercom and store them as an array. Next, the function should make an HTTP GET request to Intercom using both the `access-token` for the company and the `user-ID` of the user in question. Intercom will return a JSON of all of the events that have occurred for that user and their associated metadata. The function should parse this data and append it to some kind of local DB (or CSV). 

Once this has been done for the first user, the function should repeat until it has received events for all users in the list.

# Constraints

It should be noted that Intercom limits its requests to 500 per minute. If the list exceeds 500 users, then the function should pause so that the threshold isn't breached.
