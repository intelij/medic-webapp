# Medic Mobile Release Notes

## 2.15.0

### Migration notes

- [#3910](https://github.com/medic/medic-webapp/issues/3910): the `POST /api/v1/users/{username}` API has had some significant changes. Importantly for scripting, an arguable bug was fixed where you didn't need to provide a user `type`. Check your scripts!

### Features

- [#3627](https://github.com/medic/medic-webapp/issues/3627): Generate scheduled messages just-in-time so changes to contacts are reflected in yet to be sent messages. NB: This feature only works with the `translation_key` configuration and not with the deprecated `messages` array so now is a good time to update your configuration.
- [#3657](https://github.com/medic/medic-webapp/issues/3657): Add permissions to control whether or not users see the call and message buttons on mobile.

### Bug fixes

- [#1359](https://github.com/medic/medic-webapp/issues/1359): Helpful error message not shown if no contact associated with current user when trying to submit a report.
- [#4144](https://github.com/medic/medic-webapp/issues/4144): Remove `can_access_directly` permission.

### UI/UX Improvements

- [#3910](https://github.com/medic/medic-webapp/issues/3910): users are required to provide their current password if they wish to change it

## 2.14.0

_February 5, 2017_

### Migration notes

- [#3449](https://github.com/medic/medic-webapp/issues/3449): We included a feature which makes it unnecessary to use a `repeat-relevant` node in Enketo forms to workaround a bug which created an empty child. This node should now be removed.
- [#3629](https://github.com/medic/medic-webapp/issues/3629): We added more configurable text to the target widgets. Also, configuring an array of target titles is now deprecated in favor specifying a single translation key. Reconfigure your targets to specify values for `translation_key`, `subtitle_translation_key`, and `percentage_count_translation_key` properties. [Full documentation](https://github.com/medic/medic-docs/blob/master/configuration/targets.md).
- [#3818](https://github.com/medic/medic-webapp/issues/3818): We changed the way groups of scheduled messages are silenced when using `silence_for`. Previously, only the first group found to be in the silence window was silenced. Now, all groups are.

### Features

- [#3096](https://github.com/medic/medic-webapp/issues/3096): Allow users to take a photo while filling in an xform in Enketo and upload the photo with the form.
- [#3459](https://github.com/medic/medic-webapp/issues/3459): Add format-date-tr() to our custom xpath functions to support translations of days and months in xforms.
- [#3450](https://github.com/medic/medic-webapp/issues/3450): Show the logout button in the hamburger menu for android users who have the new `can_log_out_on_android` permission set.

### Bug fixes

- [#3944](https://github.com/medic/medic-webapp/issues/3944): Unread reports bubble not working with deleted docs.
- [#3563](https://github.com/medic/medic-webapp/issues/3563): Sentinel scheduling EDDs on a Sunday for all ANC registrations.
- [#3821](https://github.com/medic/medic-webapp/issues/3821): Export api doesn't handle errors during export gracefully.

### UI/UX improvements

- [#3945](https://github.com/medic/medic-webapp/issues/3945): Update the icons used for contacts.
- [#3904](https://github.com/medic/medic-webapp/issues/3904): Make `user type` required in the edit user screen.
- [#3758](https://github.com/medic/medic-webapp/issues/3758): Title of form is misaligned in list of reports and reports detail pane.
- [#3736](https://github.com/medic/medic-webapp/issues/3736): Configurable profile field UI changes.
- [#3735](https://github.com/medic/medic-webapp/issues/3735): Reports content row improvements.
- [#3734](https://github.com/medic/medic-webapp/issues/3734): Tasks content row improvements.
- [#3732](https://github.com/medic/medic-webapp/issues/3732): Message content row improvements.
- [#3731](https://github.com/medic/medic-webapp/issues/3731): Update content row UI for consistency & improved readability.
- [#3720](https://github.com/medic/medic-webapp/issues/3720): Improve display of icons in configurable profile cards.
- [#3719](https://github.com/medic/medic-webapp/issues/3719): Person & place profile page UI changes.
- [#3704](https://github.com/medic/medic-webapp/issues/3704): Improve password strength validation error messages.
- [#3629](https://github.com/medic/medic-webapp/issues/3629): Update target widget cards and targets page layout.
- [#3597](https://github.com/medic/medic-webapp/issues/3597): Update fonts to Noto.
- [#3561](https://github.com/medic/medic-webapp/issues/3561): Display required fields when creating a "restricted to a place" user.
- [#2522](https://github.com/medic/medic-webapp/issues/2522): Percentage target values are confusing.

### Performance improvements

- [#3950](https://github.com/medic/medic-webapp/issues/3950): Remove stats collection in API as it's no longer used.
- [#3913](https://github.com/medic/medic-webapp/issues/3913): Sentinel's fetchHydratedDoc function should use only fetch contacts that aren't already present in the lineage list.

### Security

- [#3873](https://github.com/medic/medic-webapp/issues/3873): Escape output to defend against javascript injection.
- [#3239](https://github.com/medic/medic-webapp/issues/3239): Accessing webapp without logging in is possible.

## 2.13.0

_October 2, 2017_

### Migration notes

- [#2635](https://github.com/medic/medic-webapp/issues/2635) changes the context available to the configured contact summary script. The `contact` parameter no longer has information about parents. This information is now in an array called `lineage`. More information is available in the [configuration documentation](https://github.com/medic/medic-docs/blob/master/configuration/contact-summary.md).
- [#3546](https://github.com/medic/medic-webapp/issues/3546) changes the implementation of the `contact_summary` so instead of declaring the output on the last line of the script, now you have to return the output. Usually this is as easy as adding a return on the last line, so `output;` becomes `return output;`. More information is available in the [configuration documentation](https://github.com/medic/medic-docs/blob/master/configuration/contact-summary.md).

### Features

- multi_report_alerts transition added to sentinel. See the documentation in [medic-docs](https://github.com/medic/medic-docs/blob/master/configuration/transitions.md). Issue: [#3416](https://github.com/medic/medic-webapp/issues/3416)
- Specify which forms can be downloaded using Collect. Issue: [#3607](https://github.com/medic/medic-webapp/issues/3607)
- Validate sentinel transition configs at transition load time. Issue: [#3585](https://github.com/medic/medic-webapp/issues/3585)
- Information from the contact-summary is now available as input to forms. Issue: [#3413](https://github.com/medic/medic-webapp/issues/3413)
- Allow users to enter Bikram Sambat dates in Enketo forms on Android phones. Issue: [#3513](https://github.com/medic/medic-webapp/issues/3513)
- Allow users to enter Bikram Sambat dates in Enketo forms in the web app. Issue: [#3404](https://github.com/medic/medic-webapp/issues/3404)
- Registration of a person from a report/action form is now possible. Issue: [#2912](https://github.com/medic/medic-webapp/issues/2912)

### Bug fixes

- Couch responds with 200 when a bad app_settings file is uploaded. Issue: [#3674](https://github.com/medic/medic-webapp/issues/3674)
- Select All in bulk delete doesn't work. Issue: [#3646](https://github.com/medic/medic-webapp/issues/3646)
- Only serve collect-specific XML forms to collect. Issue: [#3642](https://github.com/medic/medic-webapp/issues/3642)
- Exporting when filtered by report type exports more reports than are displayed in the web app. Issue: [#3615](https://github.com/medic/medic-webapp/issues/3615)
- Bulk delete fails when deleting more than a few hundred records. Issue: [#3605](https://github.com/medic/medic-webapp/issues/3605)
- Exporting reports filtered by place results in an empty xml. Issue: [#3593](https://github.com/medic/medic-webapp/issues/3593)
- Requesting forms should respond with 4xx on client error. Issue: [#3569](https://github.com/medic/medic-webapp/issues/3569)
- Can't view contacts for restricted user. Issue: [#3517](https://github.com/medic/medic-webapp/issues/3517)
- Bad error message when associated contact is not available in the local DB. Issue: [#3499](https://github.com/medic/medic-webapp/issues/3499)
- Gardener bug on startup when module_name is undefined. Issue: [#3481](https://github.com/medic/medic-webapp/issues/3481)
- Reports list showing when user doesn't have proper permission. Issue: [#3452](https://github.com/medic/medic-webapp/issues/3452)
- select2 in a repeat group does not work as expected in an Xform. Issue: [#3430](https://github.com/medic/medic-webapp/issues/3430)
- {{patient_name}} not found when patient was created by xform. Issue: [#3419](https://github.com/medic/medic-webapp/issues/3419)
- Search doesn't work in Nepali or with accented characters. Issue: [#3392](https://github.com/medic/medic-webapp/issues/3392)
- Remove nested contacts. Issue: [#2635](https://github.com/medic/medic-webapp/issues/2635)

### UI/UX improvements

- Sync status cut off in mobile view. Issue: [#3703](https://github.com/medic/medic-webapp/issues/3703)
- Hide Collect XForms from filter list in History tab. Issue: [#3625](https://github.com/medic/medic-webapp/issues/3625)
- Split the form configuration page into JSON and XML tabs. Issue: [#3559](https://github.com/medic/medic-webapp/issues/3559)
- Wrap text in tasks list. Issue: [#3525](https://github.com/medic/medic-webapp/issues/3525)
- Task summary screen looks ugly on desktop. Issue: [#3521](https://github.com/medic/medic-webapp/issues/3521)
- Send Report dropdown menu items are misaligned. Issue: [#3469](https://github.com/medic/medic-webapp/issues/3469)
- Disable tasks tour for admins. Issue: [#3144](https://github.com/medic/medic-webapp/issues/3144)
- Confirmation popup should not show on 'Error loading form'. Issue: [#3045](https://github.com/medic/medic-webapp/issues/3045)
- 'May lose data' warning displayed when form has no fields. Issue: [#1601](https://github.com/medic/medic-webapp/issues/1601)

### Performance improvements

- Remove modules.js attachment. Issue: [#3684](https://github.com/medic/medic-webapp/issues/3684)
- Use alternative pagination method for running batched migrations. Issue: [#3553](https://github.com/medic/medic-webapp/issues/3553)
- The read status of documents is now stored in a user specific database to reduce unnecessary doc updates. Issue: [#2418](https://github.com/medic/medic-webapp/issues/2418)

### Security

- Password validation so when creating or updating users the new passwords have to be at least 8 characters long and reasonably complex. Issue: [#1472](https://github.com/medic/medic-webapp/issues/1472)
- Don't eval() user input. Issue: [#3546](https://github.com/medic/medic-webapp/issues/3546)
- Set `Secure` setting on AuthSession cookie for HTTPS pages. Issue: [#3182](https://github.com/medic/medic-webapp/issues/3182)

## 2.12.5

_August 18, 2017_

### Bug fixes

- Fix bug where id generation wouldn't automatically increase id length when it ran out of ids. Issue: #3790

## 2.12.4

_August 10, 2017_

### Bug fixes

- Fix issue with /api/v1/records. Issue: #3770

## 2.12.3

_August 8, 2017_

### Bug fixes

- Accept messages with empty from or content. See: https://github.com/medic/medic-api/pull/185

## 2.12.2

_August 2, 2017_

### Bug fixes

- Accept patient reports for patients created in app. Issue: #3740
- Stop accept_patient_reports transition clearing messages for unrelated registrations. Issue: #3742

## 2.12.1

_July 25, 2017_

### Bug fixes

- Improved error messages for SMS endpoint. Issue: #3587
- Allow for empty SMS message Content. Issue: #3656
- Implement 500 item max for bulk delete. Issue: #3605

### Security

- Fixed kanso packages that inadvertently cached credentials. Issue: #3648

## 2.12.0

_June 20, 2017_

### Features

- Add sync status indicator for offline users. Issue: #3357
- Add gateway message delivery statuses. Issue: #3073
- Add a replication_date property to records. Issue: #2180
- Change patient id generation to store the length of id it's generating. Issues: #3505
- Allow form upload through Form Configuration UI. Issue: #3433

### Bug fixes

- On small screen, cannot re-open date filter in history tab. Issue: #3467
- Debug section of the About screen has some weird extra text. Issue: #3463
- Medic Gateway runs into document update conflicts while trying to upload sms status. Issue: #3443
- Stop `maintain_info_doc` transition from writing sentinel metadata. Issue: #3424
- Webapp does not supply XML forms (XForms) to Collect. Issue: #3390
- Cannot render form in Firefox. Issue: #3354
- False positive error uploading translations. Issue: #3350
- Exporting server logs fails with api 500. Issue: #3209
- AWS EC2 AMI Regression: Does not currently boot. Issue: #3173
- Form exits on Refresh/Reload in Tasks tab. Issue: #3090
- Facility reference code fails to match when using integers and textforms. Issue: #1058

### UI/UX improvements

- Bullet displayed incorrectly. Issue: #3020
- File chooser for importing translations should filter for .properties files. Issue: #3474
- Show loading progress when app is starting. Issue: #3384

## 2.11.3

_June 9, 2017_

### Bug fixes

- The namespace-form-fields migration conflicts itself. Issue: #3534
- In the create-patient-contacts migration provide a more complete list of potential patient_name locations. Issue: #3372

## 2.11.2

_May 29, 2017_

### Performance improvements

- Slow initial replication for users with lots of docs. Issue: #3508

## 2.11.1

_May 9, 2017_

### Bug fixes

 - Cannot report via SMS about people who are registered in the web app. Issue: #3401
 - Results page CSS messed up in v2.11. Issue: #3369
 - The user needs an associated contact to create a contact. Issue: #3394
 - Error when adding Place with new person. Issue: #3420
 - Error after canceling and re-opening any contact creation form. Issue: #3448
 - namespace-form-fields migration : report bulk errors. Issue: #3371 (second part)

## 2.11.0

_April 12, 2017_

### Migration notes

- [#3230](https://github.com/medic/medic-webapp/issues/3230) changes patient ID generation so it automatically increases the length as needed, up to 13 digits. If you are validating incoming patient_ids in Sentinel, be sure to remove or correct any length restrictions, e.g. `^[0-9]{5}$` would become `^[0-9]{5,13}$`.
- [#3166](https://github.com/medic/medic-webapp/issues/3166) adds a new transition that adds patient_ids to every created person: `generate_patient_id_on_people`. Enable this transition if you want to send SMS about patients that may be created through the webapp.

### Features

- Drop id_format app setting in favour of auto-lengthening ids. Issue: #3230
- Support for Nepali number characters. Issue: #3192
- Show XForm in User's language. Issue: #3174
- Sentinel needs to support these patient_id use cases. Issue: #3166
- Enable users to export, even if they do not have permission to configure. Issue: #3113
- Support `required_message` and `required_message` translations in Enketo. Issue: #3056

### Bug fixes

- namespace-form-fields migration causing Express toString fail. Issue: #3371
- Cannot use Collect with username/password fields. Issue: #3118
- No permissions available for configuration on first run. Issue: #3251
- Fix outdated npm shrinkwrap entry for enketo-core. Issue: #3352
- Set user-agent header in Medic Collect. Issue: #3334
- Buttons in LHS FAB disappear. Issue: #3321
- Analytics tab Hindi text is not aligning properly. Issue: #3297
- Relative times are not translated. Issue: #3282
- Submitting feedback no longer works. Issue: #3273
- Full access users cannot create users, even when they have the appropriate permissions. Issue: #3262
- Sending a message from the Messages tab creates a message with uuid equal to database URL. Issue: #3242
- API does not check if `COUCH_NODE_NAME` is set at startup. Issue: #3226
- Support Nepali calendar in outgoing SMS. Issue: #3219
- New reports for same time period do not replace previous ones. Issue: #3160
- API is picky about trailing slashes for SMS endpoint. Issue: #3152
- Couchdb's startup.log does not include timestamps. Issue: #3131
- Exporting feedback crashed api and it didn't come back. Issue: #3107
- Export server logs from webapp does not work. Issue: #3089
- Requesting audit log makes server unresponsive. Issue: #1789
- Unrecognized input type found when trying to reset. Issue: #1655

### UI/UX improvements

- Contact profile fields collapse on mobile. Issue: #3306
- Disable cancel buttons when saving. Issue: #1650

### Performance improvements

- enketo-core package.json is included in inbox.js bundle. Issue: #3293
- Use enketo xml cache for contact forms too. Issue: #3325

## 2.10.3

_March 31, 2017_

### Bug fixes

- Unicode support for storing enketo xml. Issue: #3308
- Support negative values in xform fields better. Issue: medic/medic-projects#1624
- Trigger enketo calc updates when option names are changed. Issue: #3281
- New Household button missing. Issue: #3132
- Change report form language without requiring refresh. Issue: #3174
- Corrupted translation strings. Issue: #3305

### UI/UX improvements

- Show report subject name on patient page. Issue: #3309
- Translate task schedule group titles. Issue: #3283
- Add additional supported moment locales. Issue: #3282
- Translate contact forms. Issue: #3323

## 2.10.2

_March 24, 2017_

### Bug fixes

- Sentinel somehow infinitely loops and continually writes to its metadata file. Issue: #3275
- API crashes after `/medic/_bulk_docs` gets called. Issue: #3268

## 2.10.1

_March 15, 2017_

### Bug fixes

- Sending a message from the Messages tab creates a message with uuid equal to database URL. Issue: #3242

## 2.10.0

_March 10, 2017_

### Features

- Use reference to translation keys in app_settings. Issue: #3127
- Add date of birth to person created by SMS. Issue: #3100
- Configure the max number of SMS in multipart SMS. Issue: #3095
- Load messages script fails to use https. Issue: #3081
- Cannot access all fields for contact in select2. Issue: #3069
- Configurable contact summary cards. Issue: #3037
- Display additional information in contact profile. Issue: #2914
- Support additional context for hiding/showing actions. Issue: #2913
- Update Tour. Issue: #2212

### Bug fixes

- Targets aren't updated when no longer relevant. Issue: #3207
- Task issues for restricted user when a report is deleted on the server. Issue: #3189
- When navigating to the targets tab, I see a flash of the "no analytics modules configured" message. Issue: #3177
- Update reports when loading the tab. Issue: #3178
- Error after submitting form. Issue: #3157
- Deleted message persists until refresh. Issue: #3003
- Single delete and bulk delete does not immediately remove items from LHS in Reports tab. Issue: #3001
- Tasks list says "no tasks found" before it's loaded. Issue: #1935
- Labels not translated for generated report fields. Issue: #3154
- Getting 502s after submitting task; Tasks not cleared until refresh. Issue: #3111
- Do not know if patient ID is valid when processing Registrations/Report Actions. Issue: #3082
- Patient contact creation should happen if a patient contact doesn't already exist. Issue: #3115
- Task schedules created using the `reported_date` of a report do not show/hide at the expected time. Issue: #3097
- Patients reports accepted even if no person has the `patient_id`. Issue: #3075
- Registrations that clear previous registrations also clear themselves. Issue: #3074
- Ensure useful commands is on medic-os $PATH by default. Issue: #2750
- Family Members section header shows on person's profile. Issue: #3108
- Uncaught exception triggers 500 response for subsequent requests. Issue: #3099
- Broken links in app settings. Issue: #3088
- Edit function not working for reports sent by unknown number. Issue: #3087
- SMS reports do not show name in summary. Issue: #3084
- Auto replies and Scheduled SMS are truncated to fit in single SMS. Issue: #3083
- Bubble task count not showing on browser refresh. Issue: #3028
- Scheduled messages not showing accurate date. Issue: #3012
- SMS API sets messages to `scheduled` on POST. Issue: #3011
- Scheduled messages not being sent. Issue: #3010
- JavaRosa Parser should give a better error message when form definition on the web app is mismatched with the submitted message using medic collect. Issue: #2638
- Contact `person`s don't show up in their places. Issue: #2385
- `setup_complete` is set too fast, so setup wizard is likely to be skipped. Issue: #2376
- Submitting a family survey doesn't clear the task. Issue: #2265
- Ages of children showing up strangely. Issue: #2191
- Forms and icons fail to replicate on slow connections. Issue: #2113

### UI/UX improvements

- Clickable portion of action is smaller than item. Issue: #3104
- "Targets" tab blank for admin users. Issue: #3029
- Action button items get lost in RHS. Issue: #3005
- Action button should always be left-most button in FAB. Issue: #3004
- "Up" button at bottom of place/person pages. Issue: #2894
- Status icon for `delivered` is orange instead of green. Issue: #2752
- Display format for phone numbers. Issue: #1930

### Performance improvements

- medic-api migration to remove couchmark. Issue: #3068
- Extract XML forms into attachments. Issue: #3009

## 2.9.1

_January 27, 2017_

### Bug fixes

- Added a migration to fix scheduled messages so they can be sent by medic-gateway. Issue: #3015

## 2.9.0

_December 9, 2016_

### Features

- Redesign of People tab to introduce patient centric workflows.
- Create Task and Target based on reports using short `patient_id` format. Issue: #2986
- Calculate Z-Score within app workflow form. Issue: #2915
- Transitions do not run for XForms. Issue: #2864
- CHWs should not be able to edit their own area. Issue: #2844
- Allow for people-centric SMS workflows. Issue: #2700
- Unique "add person" forms to a place. Issue: #2693
- Store GPS failure. Issue: #2670
- Progressive Web App. Issue: #2626
- Remove XML parsing and replace it with JSON views. Issue: #2432
- Lowercase all user ids. Issue: #2369
- New person and new place buttons should add person/place to the part of the hierarchy in which they are clicked. Issue: #2335
- Create default Edit Place forms that allow users to edit a family's primary contact. Issue: #2333
- Initial replication feedback. Issue: #2279
- Make it easy to add translation keys. Issue: #1333

### UI/UX improvements

- Show parent place after deleting a place/person. Issue: #2936
- Clean up labels and translations. Issue: #2888
- First load: briefly displays "No people found" on the people and places tab even if you have contacts. Issue: #2835
- Add icons to forms. Issue: #2794
- Forms in Submit Report menu aren't sorted. Issue: #2760
- Reported Date is show in ms since epoch. Issue: #2699
- Add basic sync status to about page. Issue: #2415
- Display 'your place' card upon login. Issue: #2342
- Only show places you directly manage in LHS unless searching. Issue: #2339
- Lock 'Your Place' at top of left pane. Issue: #2337
- Remove all filters in Contacts. Issue: #2336
- Display "disabled for admins" message in tasks and targets page. Issue: #2292

### Bug fixes

- Rerun transitions on change if the previous run failed. Issue: #2978
- Allow replication of JSON reports. Issue: #2979
- On upgrade existing reports are not associated to person/place. Issue: #2970
- Queries from ANC Analytics do not work. Issue: #2975
- Set new permissions to the application default when updating. Issue: #2951
- `db-object` fields show as editable when `readonly="true()"`. Issue: #2910
- Calling the `doc_summaries_by_id` view results in an audit record being created. Issue: #2895
- Can't create new person as primary contact to existing place. Issue: #2884
- Mute button does not work. Issue: #2878
- Cannot fully replicate dbs behind medic-api due to badly named document. Issue: #2876
- Deregister Changes callbacks. Issue: #2870
- Non admins can edit translations. Issue: #2868
- Error when completing a task. Issue: #2851
- Editing a report from a person doesn't pre-populate the person. Issue: #2845
- Forms appear on the History page when they shouldn't, based on configuration. Issue: #2837
- When I click on a report from a contact profile, I see a flash of the History tab before getting to the report view. Issue: #2834
- When resources change all icons disappear. Issue: #2830
- Use default revs_limit. Issue: #2787
- ContactsContent controller modifies doc on render. Issue: #2782
- Alerts to `reporting_unit` not working. Issue: #2779
- Correct form not displayed when going to Submit Report. Issue: #2758
- Validations and Auto-Replies not triggered for Notifications. Issue: #2755
- Sending message from Reports tab doesn't prefill the modal. Issue: #2748
- Selecting a person's Report or Task doesn't load the actual item. Issue: #2718
- select2 form fields are not being prepopulated. Issue: #2703
- Exporting Feedback crashes API. Issue: #2692
- Cannot associate a user with a place. Issue: #2683
- Missing patient ids and CHW names. Sentinel not fully running on Strong Minds instance. Issue: #2675
- Cannot update a contact's phone number without an error. Issue: #2661
- Add recipients doesn't work. Issue: #2659
- Sometimes changes feed is told the wrong ID for user doc. Issue: #2640
- Submitting a report with an invalid ref id crashes sentinel. Issue: #2636
- Always use the same pouchdb configuration. Issue: #2625
- Branch Manager is not getting forms downloaded. Issue: #2620
- Can crash API with call to /api/v1/users. Issue: #2602
- TypeError on Messages tab. Issue: #2588
- `context_by_type_freetext` view seems to run with no search term. Issue: #2584
- Once viewing a stock report, clicking the area name makes area stats disappear. Issue: #2580
- Missing option to change time unit in reporting rate analytics. Issue: #2576
- Missing "district" selector in Reporting rates Analytics in v2.x. Issue: #2575
- Rename "stock" widget to "reporting rates". Issue: #2574
- No title shown for analytics stock table. Issue: #2573
- No loader showing when loading data on analytics stock report. Issue: #2572
- No loader shown when loading locations on Analytics Stock widget. Issue: #2566
- Back button is broken on analytics stock widget. Issue: #2565
- Stock widget shows time-period selector before a place has been selected. Issue: #2564
- Icons wrong on analytics stock widget. Issue: #2563
- No text labels displayed in analytics stock widget. Issue: #2562
- Analytics stock widget breaks on error. Issue: #2561
- No loading animation is displayed when waiting for list of locations on analytics stock widget. Issue: #2559
- Analytics page should not show menu if there is only one module. Issue: #2557
- Cannot choose one of the analytics modules. Issue: #2556
- Reporting Rates has changed name to Stock Monitoring. Issue: #2555
- Analytics screen has no information on it. Issue: #2554
- By default gateway users don't have the `can_access_gateway_api` permission. Issue: #2549
- Cannot view Targets configuration. Issue: #2548
- Send message uses a badly performing API. Issue: #2547
- Document conflict on starting sentinel. Issue: #2542
- Bad error when not authed for SMS api. Issue: #2540
- Editing your own user settings wipes out security settings. Issue: #2539
- Cannot send messages to unknown numbers. Issue: #2536
- medic-api doesn't seem to correctly expose all pending messages. Issue: #2535
- Outgoing messages are not well formatted in the report view. Issue: #2532
- SMS from medic-gateway do not appear in Messages tab. Issue: #2530
- Phantom SMS message response to invalid textform message. Issue: #2525
- sentinel keeps processing the same backlog. Issue: #2521
- Errors starting sentinel with DB name other than 'medic'. Issue: #2513
- You need to restart medic-api for new translations to make it through. Issue: #2511
- API connection refused. Issue: #2476
- Login page not translated. Issue: #2466
- Language dropdown is empty when adding or editing a user. Issue: #2462
- Language select modal is blank. Issue: #2459
- Broken migrations should prevent API from starting. Issue: #2456
- Geolocation information is not exposed in JSON. Issue: #2450
- Creating user fails due to invalid `reported_date`. Issue: #2449
- App takes minutes to load a `person` dropdown. Issue: #2445
- User can't change their own password. Issue: #2440
- When switching between reports in History, the "No report selected" page appears momentarily. Issue: #2433
- \\u0000 cannot be converted to text. Issue: #2426
- The tour keeps popping up on mobile. Issue: #2423
- In select mode, clicking on a report on the LHS to check the box also marks the report as read. Issue: #2422
- DeleteDocs modifies the given array. Issue: #2417
- DeleteDocs fails if the parent's contact is null. Issue: #2416
- After clicking "delete" on the RHS of bulk delete, reports do not disappear from the LHS. Issue: #2414
- Using "select all" when attempting to bulk delete, the number of records on the RHS doesn't match the LHS. Issue: #2411
- Logout option no longer works on the MM Android app. Issue: #2407
- national-admins should be able to edit contacts. Issue: #2395
- Initial replication gets stuck on Tecno. Issue: #2394
- Cannot have more than one repeat group that creates people within the same form. Issue: #2393
- Targets tab doesn't show correct progress. Issue: #2388
- Contacts tab takes forever to load on mobile. Issue: #2378
- RangeError: Maximum call stack size exceeded. Issue: #2377
- Don't audit docs that match `_local/*`. Issue: #2366
- Fix changes proxy to support heartbeat. Issue: #2363
- .4 analytics page crashes `develop` API. Issue: #2352
- Admin can't submit report (permissions). Issue: #2351
- DeleteDoc service breaks replication. Issue: #2331
- Phones with poor internet connections get an error page when trying to update. Issue: #2328
- Navigating straight to `medic/_design/medic/_rewrite/#/configuration/user` breaks editing. Issue: #2294
- Cannot select contact after bad search. Issue: #2252
- Incoming message not attributed to contact. Issue: #2230
- Form recognized, but label in list not updated. Issue: #2215
- Forms not showing in filter. Issue: #2214
- Schedule not assigned to registration form. Issue: #2213
- In date filter for Reports tab, the selected dates are being offset by 1 day. Issue: #2185
- Exceptions when indexing (presumably) views. Issue: #2173
- Form title disappears on page reload. Issue: #2156
- User configuration UI doesn't correctly load the attached contact / locale. Issue: #2116
- Display: block in or-appearance-h2 is overriding the disabled class. Issue: #2101
- Verify/Unverify button falls out of sync with left pane after being clicked. Issue: #1939
- Place contact should be a child of the place. Issue: #1710
- Default "New Person" form doesn't allow editing the parent place. Issue: #2704

### Performance improvements

- Make medic-audit's view generation 8-∞ times faster. Issue: #2879
- Deregister Changes callbacks. Issue: #2870
- Improve free text search views. Issue: #2853
- Admin performance on lg.app has regressed. Issue: #2744
- Improve application performance for high-utilization CHPs. Issue: #2665
- Create migration to remove obsolete ddocs. Issue: #2597
- Send message uses a badly performing API. Issue: #2547
- Consider refactoring how sentinel views are compiled. Issue: #2537
- sentinel duplicate views. Issue: #2534
- Remove XML parsing and replace it with JSON views. Issue: #2432
- Increase stability by looping over changes . Issue: #2430
- Replication since gets reset when new documents added. Issue: #2404
- Use db view pagination where possible. Issue: #2371
- Don't audit docs that match `_local/*`. Issue: #2366
- Create a client side ddoc. Issue: #2206
- Store translations in a separate doc. Issue: #1706
- Remove empty parents migration scalability. Issue: #2629

## 2.8.5

_December 15, 2016_

- No changes, only a bump in version number to trigger a new release.

## 2.8.4

_November 30, 2016_

### Bug fixes

- Debounce form submissions to stop duplicate submissions. Issue: #2909

## 2.8.3

_November 9, 2016_

### Performance improvements

- Remove traffic statistics collection. Issue: #2886

## 2.8.2

_October 13, 2016_

### Bug fixes

- Ensure PouchDB doesn't mis-label TECNO phones as devices running Safari. Issue: #2797

## 2.8.1

_October 10, 2016_

### Bug fixes

- If initial sync fails without syncing anything subsequent syncs get no results. Issue: #2770
- Initial sync fails if server doesn't respond within 30 seconds. Issue: #2771
- Targets tab is blank on first access. Issue: #2739

### Performance improvements

- Adding a space to a contact search term performs poorly. Issue: #2769
- Local DB grows without limit. Issue: #2434

## 2.8.0

_August 29, 2016_

### Features

- Pass user's info to rule to customize Tasks per user type or location. Issue: #2408
- Add context to target types and goals. Issue: #2409
- Update default translations
- Add ageInDays and ageInMonths functions to the XML forms context utilities. Issue: #2650
- Users can now only access an optionally configured number of hierarchy levels below their facility. Issue: #2648

### Bug fixes

- Android back button doesn't work as expected. Issue: #2600
- In date filter for Reports tab, the selected dates are being offset by 1 day. Issue: #2185
- 'New Contact' option does not appear without a search. Issue: #2516
- Place contact should be a child of the place. Issue: #1710
- Geolocation information is not included in submitted form. Issue: #2450
- Cannot update a contact's phone number without an error. Issue: #2420

## 2.7.3

_July 18, 2016_

### Bug fixes

- Remove maxSockets limit to allow more concurrent connections. Issue: #2492

## 2.7.2

_July 11, 2016_

### Bug fixes

- Connection refused when trying to load app. Issue: #2476

## 2.7.1

_July 4, 2016_

### Bug fixes

- Creating user via fails due to invalid reported_date. Issue: #2449

### Performance improvements

- App takes minutes to load a person dropdown. Issue: #2445
- Cannot load Configuration Users page. Issue: #2444

## 2.7.0

_June 8, 2016_

### Features

- Bulk delete reports. Issue: #1000

### Bug fixes

- Report list item summaries aren't translated. Issue: #2100
- Fix form type filter. Issue: #1409

### Performance improvements

- Replication performance. Issue: #2286
- Improve search performance. Issue: #2302
- Don't fetch form titles for each Contact report. Issue: #2300
- Only fetch relevant data for the Users service. Issue: #2262
- Remove clinics from the Facility filter dropdown. Issue: #2218
- Optimize admin bandwidth concerns. Issue: #2211
- We request facilities from the server over and over again. Issue: #2210
- Don't audit _local docs. Issue: #2366
- All requests to CouchDB time out after 10 seconds. Issue: #2325
- Long delay loading contact dropdowns. Issue: #2326

## 2.6.3

_May 23, 2016_

- "console not defined" error when loading page. Issue: #2277
- Pouch doesn't update seq unless something has changed. Issue: #2288
- Snackbar showing all the time. Issue: #2306
- Support external_id property on user-settings docs. Issue: #2310

## 2.6.2

_May 6, 2016_

- Update PouchDB to improve replication reliability and performance. Issue: #2134 #2167
- When editing a CHP Area, previously set values for CHP, Branch, and Supervisor do not show up. Issue: #2223
- Dropdowns in CHP Area create and edit forms have no blank option. Issue: #2227
- allow-new appearance in Enketo doesn't make the "New" option appear. Issue: #2251
- Improve performance of Enketo db-object-widget. Issue: #2161
- Ensure roles are always available on user-settings. Issue: #2199
- Form type filter doesn't include all forms. Issue: #1409
- Added APIs for creating Users, People, and Places. Issue: #2046

## 2.6.1

_April 21, 2016_

- User's fullname is not showing up in /configuration/users. Issue: #2200
- Deleted documents cause sentinel log spam. Issue: #1999
- Disable nools for unrestricted users. Issue: medic-projects#149
- Update libphonenumber and use strict validation. Issue: #2159 #2196
- Contacts export response garbled. Issue: #2187

## 2.6.0

_April 5, 2016_

This release contains breaking changes from 0.x versions. Updating from 0.x versions may result in the application no longer operating as expected.

- The app can now be used offline and synced back to the server later.
- Added an android app for accessing the webapp from mobile.
- Added Tasks feature for rich event scheduling.
- Forms can now be provided in XForm format for rich form UIs.
- Added a configurable Target analytics module.

## 0.4.15

_March 2, 2017_

- Fixed potential race condition with medic-gateway. Issue: medic-projects/issues/1243
- Bumped libphonenumber to make phone number validation more up to date. Issue: medic-projects/issues/1005

## 0.4.14

_December 16, 2016_

- Bug fix for medic-gateway sending scheduled messages. Issue: #2535

## 0.4.13

_October 21, 2016_

- Option to set birthdate using days old instead of weeks. Issue: #2756
- The week/month is off by 2 in the Reporting Rates analytics dashboard. Issue: #2781
- Remove socket limit in medic-api. Issue: #2632

## 0.4.12

_July 21, 2016_

- Fixed bug in reporting rates for weekly time unit. #2429
- Log warnings in sentinel when ID collisions happen. #1898
- Support integration with [medic-gateway](https://github.com/medic/medic-gateway) for sending and receiving SMS medic-api#69

## 0.4.11

_February 4, 2016_

- Security fix for leaking auth info.

## 0.4.10

_Nov 16, 2015_

- Added support for Outgoing Deny List, a comma separated list of phone numbers
  or strings to deny outgoing service to. #750

- Fixed bug in records export. #1273

- Fixed bugs in uniqueWithin validation. medic-sentinel#74

- Added link to Help page in main menu.

## 0.4.9

_Aug 26, 2015_

- Fixed bug on node 0.12 in felix-couchdb. #1145

- Improved error handling when notifications (start/stop) configs are
  misconfigured. #1144

- Fixed bug in `exists` validation where it fails on some unicode characters. #1147

- Fixed Reporting Rates interface that was neglected and broken. #1030

- Fixed bug in exporting data by date, it's now inclusive. #1104

## 0.4.8

_July 14, 2015_

- Added SMS parser fixes from dev branch:

  - parse string fields with exclamation marks
  - compact textforms format handles quotes in quotes

- Fixed export bug when using lowercase form codes. Please re-upload your forms
  so they are formatted correctly. #998

- Fixed bug where exporting yields same result with or without date
  filter. #1059, #1031

## 0.4.7

_June 16, 2015_

- Fixed ODK forms list bug when the list is empty. Issue #886

- Fixed compact textforms parser bug with exclamation points. Issue #989

- Fixed bug in compact textforms parser we ignored fields with uppercase
  letters in the key of the form definition.  Issue #991

- Fixed bug when creating record with empty message. Issue #990

- Moved raw message to bottom of report body.  Issue: #927


## 0.4.6

_June 4, 2015_

- Improved boolean expression evaluation in registration configuration.

## 0.4.5

_May 28, 2015_

- Fixed bug in schedules editor for LMP (last menstrual period) based
  schedules. #973

- Initial support for messages, records and forms API.  See
  https://github.com/medic/medic-api/blob/master/API_v1.md

## 0.4.4

_May 21, 2015_

- Added support for a new messages parser we're calling Javarosa prefixed with
  the `J1` format code.

## 0.4.3

_February 26, 2015_

### Features

- Major UI enhancements #370

  - Inbox Style with advanced search bar
  - Admin Panels
  - Mobile device support

- Configurable date format #577

- Built-in ANC Analytics #586

- Easy user feedback mechanism #19

- Added help and tour

- Refactored build process, added grunt, bower and jshint.

- No forms are included by default.  You must upload your forms.  As usual
  configuration (settings and forms) persists through upgrades.

- Added new translations

- Default auto-replies

- There are now two ways to export stuff: 1) from the reports screen click on
  export, or 2) on the Configuration > Export screen. The former is simplified
  and has no way of changing facility, form, or file format. The latter is
  functionally equivalent to 0.4.2.

### Upgrade Notes

- CouchDB Lucene >= 1.0.2

- Gardener >= 1.1.0

- New [Nginx configuration](https://github.com/medic/medic-os/blob/3aedf0622eb0669aee2e5bbfba95a42faf05b9da/platform/packages/medic-core/settings/medic-core/nginx/nginx.conf), close or redirect port 5984, proxy all requests through medic-api.


## 0.4.2

_September 4, 2014_

- Fixed bug: When searching for a patient identifier using the free-text search feature, results were not returned properly. Index the field appropriately.

## 0.4.1

_July 31, 2014_

- Minor UI clean up.

- Allow hash symbol to separate form code and data in structured textform message.

- Modified build to bundle npm dependencies with attached node modules.

## 0.4.0

_July 10, 2014_

### New Features

- User interface for common settings and translations #484

- User interface to configure basic ANC messaging workflows #487

- Nodejs module for API calls and to handle audit transactions

- Better language support on messages throughout configuration. e.g. you can
  define a reminder schedule using multiple languages and the right language
  will be used based on the locale of the message.  #486

- Added support to configure locales through settings screen #491

- Added support for custom forms and uploading JSON form definitions #283

- Supporting old/obsolete settings via migrations during restore #501

- Support minute setting for scheduled hours configuration

- Reduced files size of design doc by minifying javascript and combining files

- Added support for unique validations across multiple fields. #412

- External IDs can be added to facilities on the facility page.  #503

- Added `columns` query parameter to allow callers to messages and data_records
  exports to retrieve specific columns in a specific order. #503

- Added Patient ID field to default data record export

- Allow specifying of task columns in message export.

  To include the group column, include the parameter `columns=["task.group"]`
  (and any other columns you need, eg: `patient_id`). #432

- Allow range searches on number fields in lucene. #481

### Bug fixes

- Fixed bug stopping district admins from being able to delete documents. #509

- Corrected language Nepalese to Nepali

- Fixed too many requests for app_settings #511

- Fixed saving user password, was getting reset/wiped #509

- Render facilities controls on all facilities tabs. #338

### Deprecated and Backwards Incompatible changes

- deprecated `exclude_cols` parameter for export integrations. Migrate
  applications to use the `columns` parameter instead.

- No forms are included by default, you must upload your forms. As usual
  configuration (settings and forms) persists through upgrades.


## 0.3.11

_June 19, 2014_

- Fixed bug where scheduled messages were out of order on Chrome #527

- Fixed bug where app settings was ignored, and the app reverted to defaults. #524

- Added delivery form to generic ANC forms.

- Modified behavior of patient reports when `silence_for` option is empty we
  clear the entire schedule instead of a group.

- Fixed notifications to add the configured response #508

- Fixed bug and added support for multiple schedules in schedule silencing

    When `silence_for` is specified we should only silence/clear one group, I
    introduced a bug a few commits ago that would ignore the group and
    silence/clear based on date. Use the `silence_for` window to match and
    clear the first group.

    Also added support for comma separate string on `silence_type` option.
    In the MCH case we have two schedules that can be generated depending on
    the form submission/registration: ANC Reminders and ANC Reminders LMP.
    Now both schedules can be cleared with a single ANCV settings entry.


## 0.3.10

_June 12, 2014_

- updated intrahealth-senegal forms


## 0.3.9

_May 22, 2014_

- fixed a bug in settings parser, to conform to the latest app-settings
  changes, otherwise configs never get triggered.

## 0.3.8

_May 22, 2014_

- fixed bug in messages export filters to include all data records,
  unstructured messages were being ignored. #502

- added support for app-settings kanso package.

    Saving settings in dashboard was too slow for use because entire ddoc was
    being updated.  Using app-settings API fixes that.


## 0.3.7

_May 13, 2014_

- Modified KEMRI form fields to be ordered the same as KEMR form.


## 0.3.6

_April 28, 2014_

- Fixed bug in updating duplicate scheduled reports #483


## 0.3.5

_April 16, 2014_

- Major bug fix that was introduced in 0.3.3 where visit reports do not get processed.

    Fixed accept_patient_reports transition so it calls db for readonly actions
    instead of audit.

- Allow analytics role to download messages and forms. Issue: #477

- Updated user management to show role for analytics user. Issue: #478

- Initial version of forms for Miraclefeet India


## 0.3.4

_April 14, 2014_

- translate strings on user mgmt facilities select list #474

- Change ordering of messages export format for better readability based on
  when the state is triggered. #475

    From: Received, Sent, Pending, Scheduled Cleared, Muted
    To: Received, Scheduled, Pending, Sent, Cleared, Muted


## 0.3.3

_April 10, 2014_

- Fixed spreadsheet keyboard navigation. #448

- Validate 'Everyone at x' for at least one valid phone number. #333

- Audit support for data records and facility data #415

    Also includes support for export of audit data as XML or CSV file.

    Note: Only new records and record edits will have an audit log entry.  So
    this means your audit log will only contain changes to records after the
    upgrade.

    Similarly browsing old revision will stop working for old records because
    they lack audit log entries.  If this is a major problem for you let us
    know and we can add backwards compatible revision browsing in the next
    release.

    This has been released as a standalone re-useable module for Node and
    browser environments: https://github.com/medic/couchdb-audit

- Added support for compact version of TextForms format #428

    In compact Textforms fields are delimited by spaces and determined by order.
    So no hashes or field keys are required like in classic TextForms format.
    If your field value has spaces in it then it must be surrounded by quotes
    unless it is the last field.

    Examples:

        REG 4165550000 John Smith
        REG "John Smith" 4165550000

- Include state change timestamps and patient_id in messages export #453

    Old Columns:

    Record UUID, Reported Date, From, Clinic Contact Name, Clinic Name,  Health
    Center Contact Name, Health Center Name, District Hospital Name, Message
    Type, Message State, Message Timestamp/Due, Message UUID, Sent By, To
    Phone, Message Body

    New Columns:

    Record UUID, Patient ID, Reported Date, Reported From, Clinic Contact Name,
    Clinic Name, Health Center Contact Name, Health Center Name, District
    Hospital Name, Message Type, Message State, Received Timestamp, Sent
    Timestamp, Pending Timestamp, Scheduled Timestamp, Cleared Timestamp, Muted
    Timestamp, Message UUID, Sent By, To Phone, Message Body

    Note: These are the default column labels and they are configurable.

- Disable facility select and show loading message until data is loaded. #452

- Updated font-awesome to 3.2.1 to get extra icons

- Fixed Help button on the spreadsheet. #455

- Fixed spreadsheet duplicate rendering when quickly switching tabs. #362 #450

- Added permissions checks to export lists functions. #456

- Fixed bug where facility spreadsheet update records when field value is
  unchanged. #457

- Fixed bug where registrations was not using db-wide unique IDs. medic-sentinel#54

- Fixed duplicate records on ID search #430

- User Management UX refactor #385, #380, #462, #380, #379, #378, #377, #429

- Fixed bug on facilities screen where delete functions would stack up and
  inadvertantly delete a facility. #469


## 0.3.2

_March 11, 2014 _

- fixed facilities spreadsheet bug #451 in Chrome

- minor user interface tweaks on deletion of facilities modal


## 0.3.1

_March 3, 2014 _

- Fixed a bug where the facilities spreadsheet was holding focus so sending a message doesn't work. #440

- Added Bulk Messaging support, so you can send messages to multiple recipients. #333

- Fixed bug to include incoming messages in messages export. #436

- Fixed bug where it is possible to send a message twice by double clicking the submit button

- Fixed bug where we failed to retrieve settings on port 80 #438

    This was experienced when proxying to couchdb because http proxying will
    decode the URL including docid of the show parameter, so the show
    returns 404.  Solution is to always double URL encode if the show docid
    contains special characters.

- Confirm with user before deleting facility so they can't be deleted by accident. #371

- Added unique Patient ID validation support.  #411 medic-sentinel/pull/50

    Use unique('patient_id') in your registration validation rules to validate
    new form submissions that are setting the patient ID values via forms.

    Validation rules may consist of Pupil.js rules and custom rules.  These
    cannot be combined as part of the same rule.

    Not OK:

        rule: "regex('[0-9]{5}') && unique('patient_id')"

    OK:

        rule: "regex('[0-9]{5}') && max(11111)"

    If for example you want to validate that patient_id is 5 numbers and it
    is unique (or some other custom validation) you need to define two
    validation configs/separate rules in your settings. Example validation
    settings:

    ```
    [
      {
        property: "patient_id",
        rule: "regex('[0-9]{5}')",
        message: "Invalid: Patient ID {{patient_id}} must be 5 numbers."
      },
      {
        property: "patient_id",
        rule: "unique('patient_id')",
        message: "Invalid: Patient ID {{patient_id}} must be unique."
      }
    ]
    ```

- Added Conditional Alerts feature. #437  medic-sentinel/issue/52

    Configure the Alerts section of the App Settings to send a message when an
    incoming message meets the configured condition.


## 0.3.0-beta.39 (bugfix)

_February 25, 2014_

- Fixed textforms whitespace parser bug when using form list field types. #431

    Textforms parser wasn't trimming space correctly on a field value, so if
    you had a list defined using those values they would never get matched.

    Textforms was only matching numeric values of length 2 or more, so if
    you submitted a one digit number you would not get a numeric match.

    Also if the value didn't match numeric or a date format then the
    whitespace was not being trimmed correctly.


## 0.3.0-beta.38 (debug)

_February 13, 2014_

- added logging calls to help debug and identify whitespace parsing bug #431


## 0.3.0-beta.37

_January 21, 2014_

- Fixes to user roles (@marc)

    Matches Transitional V2 in
    https://docs.google.com/a/medicmobile.org/spreadsheet/ccc?key=0Ao9l2yegOFn7dEJRTEw1Z3RmZm0wTEo4Nk92NjVocnc

- Added support for Kemri Muvuku Form (KEMR)

- Added exclude_cols query param to csv/xml form exports. #421

    For example inlude `exclude_cols=1,5` in your query parameters to
    remove the first and fifth column of an export.

-  bugfix on export query params and UX adjustments

    Made English CSV export default. SpreadsheetML can be a little buggy
    because we're using HTML entities (not valid XML).

    Disabled default month value in exports screen since record count does
    not reflect the export row totals displayed.  It's probably better UX to
    have the user set the date knowing they are doing something than having a
    default that doesn't make sense with the totals on the screen and having
    to guess why that is.

- Added timezone support to exports #394

    Render page contents first and then load the fields data since that was
    holding up the page load.

    Indexing _id as `uuid` in field index so you can search for
    `uuid:10366976d62ab9a31257b2fad16113ee` now and it shows up in avaialble
    fields index.  For some reason I think underscore prefixed fields do
    show up in fields listing on Lucene for some reason.

- Fixed poor loading on search help #422


- added timezone support to exports #394

    Now dates in the exported spreadsheet should include your locale timezone. Controlled by the `tz` query param.


- Added new Messages Export and removed message data from Forms Export

    New http endpoint `/export/messages` to get messages export. Records are
    always latest first (reverse cronological).  Message export will include
    all records (valid and invalid), the point of the messages export is to
    give you access to all your message data, including outgoing error
    messages.

    **Warning**: the following URLs are no longer supported:

    ```
    /{form}/data_records.csv
    /{form}/data_records.xml
    /form_data_records.xml
    /form_data_records.csv
    ```

    Use `/export/forms/{form}` path instead.

    **Warning**: Existing form data export format has changed.  Included UUID of
    the related record so data among the two spreadsheets (messages and form
    data) can be correlated if need be.  Also removed the message
    data/columns from form data export. A record can be found via UUID by
    using `uuid:<the uuid string>` in the search box.

    Changed default column name of "From" to "Reported From".  Note if this
    shouldn't change if you have an existing install since it is generated
    based on your translation settings.

```
    The NEW columns (added UUID column and removed message data):

    Record UUID
    Reported Date
    Reported From
    Clinic Contact Name
    Clinic Name
    Health Center Contact Name
    Health Center Name
    District Hospital Name
    [columns for form fields data depending on form]

    The OLD columns:

    Reported Date
    From
    Clinic Contact Name
    Clinic Name
    Health Center Contact Name
    Health Center Name
    District Hospital Name
    [columns for form fields data depending on form]
    Incoming Message
    Responses
    Outgoing Messages
    Scheduled Tasks
```
