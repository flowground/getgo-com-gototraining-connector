# ![LOGO](logo.png) GoToTraining **flow**ground Connector

## Description

A generated **flow**ground connector for the GoToTraining API (version 1.0.0).

Generated from: https://api.apis.guru/v2/specs/getgo.com/gototraining/1.0.0/swagger.json<br/>
Generated at: 2019-05-07T17:40:53+03:00

## API Description

The GoToTraining API enables developers to use the stable and robust GoToTraining functionality as the basis for online trainings in a proprietary learning management system. The GoToTraining APIs provide the ability to access the scheduling, registration, management, and reporting functions of GoToTraining from external applications. With the ability to tightly integrate GoToTraining into your learning infrastructure, you can offer your learners a seamless user experience and provide them with a market leading virtual classroom environment.

## Authorization

This API does not require authorization.

## Actions

### DEPRECATED: Get Organizers

> DEPRECATED: Please use the Admin API call 'Get all users' instead. For details see https://goto-developer.logmein.com/get-all-users.

*Tags:* `Organizers`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `accountKey` - _required_ - The key of the multi-user account

### Get Trainings

> This call retrieves information on all scheduled trainings for a given organizer. The trainings are returned in the order in which they were created. Completed trainings are not included; ongoing trainings with past sessions are included along with the past sessions. If the organizer does not have any scheduled trainings, the response will be empty.

*Tags:* `Trainings`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `organizerKey` - _required_ - The key of the training organizer

### Create Training

> Schedules a training of one or more sessions. The call requires a training's name, at least one start and end time, and optionally may include additional sessions, a description, additional organizers (presenters), and registration settings. You can only add organizers to a training if you have a multi-user account. Once a training has been created with this method, you can accept registrations to the training. Registration is for the entire training - all sessions. (The GoToTraining admin site enables you to create trainings that allow participants to register for individual sessions as well as automatically create weekly or monthly events.) Registration settings controls whether you allow web registration for this training, and whether a confirmation email is sent to the registrant following registration. Disabling the confirmation email is an API-only setting. If the user registers through the GoToTraining website, a confirmation email is sent. If the user is manually approved by the training administrator through the GoToTraining web site, the confirmation email is sent. It is recommended that you disable web registration if you disable confirmation emails. The response contains a trainingKey for the scheduled training.

*Tags:* `Trainings`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `organizerKey` - _required_ - The key of the training organizer

### Delete Training

> Deletes a scheduled or completed training. For scheduled trainings, it deletes all scheduled sessions of the training. For completed trainings, the sessions remain in the database. No email is sent to organizers or registrants, but when participants attempt to start or join the training, they are directed to a page that states: Training Not Found: The training you are trying to join is no longer available.

*Tags:* `Trainings`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `organizerKey` - _required_ - The key of the training organizer
* `trainingKey` - _required_ - The key of the training

### Get Training

> Uses the organizer key and training key to retrieve information on a scheduled training.

*Tags:* `Trainings`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `organizerKey` - _required_ - The key of the training organizer
* `trainingKey` - _required_ - The key of the training

### Get Management URL for Training

> A request for a direct URL to the admin portal for a specific training. The request identifies the organizer and the training; the response provides a link the organizer can use to manage or launch the training in the admin portal. The training organizer will be required to log in. You can schedule and manage the training (e.g., add tests, polls and training materials) from the URL provided in the response.

*Tags:* `Trainings`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `organizerKey` - _required_ - The key of the training organizer
* `trainingKey` - _required_ - The key of the training

### Update Training Name and Description

> Request to update a scheduled training name and description.

*Tags:* `Trainings`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `organizerKey` - _required_ - The key of the training organizer
* `trainingKey` - _required_ - The key of the training

### Get Training Organizers

> Retrieves organizer details for a specific training. This is only applicable to multi-user accounts with sharing enabled (co-organizers).

*Tags:* `Trainings`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `organizerKey` - _required_ - The key of the training organizer
* `trainingKey` - _required_ - The key of the training

### Update Training Organizers

> Replaces the co-organizers for a specific training. The scheduling organizer cannot be unassigned. Organizers will be notified via email if the notifyOrganizers parameter is set to true. Replaced organizers are not notified. This method is only applicable to multi-user accounts with sharing enabled (co-organizers).

*Tags:* `Trainings`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `organizerKey` - _required_ - The key of the training organizer
* `trainingKey` - _required_ - The key of the training

### Get Training Registrants

> Retrieves details on all registrants for a specific training. Registrants can be:<br>WAITING - registrant registered and is awaiting approval (where organizer has required approval)<br>APPROVED - registrant registered and is approved<br>DENIED - registrant registered and was not approved.<br><br>IMPORTANT: The registrant data caches are typically updated immediately and the data will be returned in the response. However, the update can take as long as two hours.

*Tags:* `Registrations`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `organizerKey` - _required_ - The key of the training organizer
* `trainingKey` - _required_ - The key of the training

### Register for Training

> Registers one person, identified by a unique email address, for a training. Approval is automatic unless payment or approval is required. The response contains the Confirmation page URL and Join URL for the registrant. NOTE: If some registrants do not receive a confirmation email, the emails could be getting blocked by their email server due to spam filtering or a grey-listing setting.

*Tags:* `Registrations`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `organizerKey` - _required_ - The key of the training organizer
* `trainingKey` - _required_ - The key of the training

### Cancel Registration

> This call cancels a registration in a scheduled training for a specific registrant. If the registrant has paid for the training, a cancellation cannot be completed with this method; it must be completed on the external admin site. No notification is sent to the registrant or the organizer by default. The registrant can re-register if needed.

*Tags:* `Registrations`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `organizerKey` - _required_ - The key of the training organizer
* `trainingKey` - _required_ - The key of the training
* `registrantKey` - _required_ - The key of the registrant

### Get Registrant

> Retrieves details for specific registrant in a specific training. Registrants can be:<br>WAITING - registrant registered and is awaiting approval (where organizer has required approval)<br>APPROVED - registrant registered and is approved<br>DENIED - registrant registered and was not approved.<br><br>IMPORTANT: The registrant data caches are typically updated immediately and the data will be returned in the response. However, the update can take as long as two hours.

*Tags:* `Registrations`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `organizerKey` - _required_ - The key of the training organizer
* `trainingKey` - _required_ - The key of the training
* `registrantKey` - _required_ - The key of the registrant

### Update Training Registration Settings

> An API request to automatically enable or disable web registrations and confirmation emails to registrants.

*Tags:* `Trainings`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `organizerKey` - _required_ - The key of the training organizer
* `trainingKey` - _required_ - The key of the training

### Get Start Url

> Returns a URL that can be used to start a training. When this URL is opened in a web browser, the GoToTraining client will be downloaded and launched and the training will start after the organizer logs in with its credentials.

*Tags:* `Trainings`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `organizerKey` - _required_ - The key of the training organizer
* `trainingKey` - _required_ - The key of the training

### Update Training Times

> A request to update a scheduled training's start and end times. If the request contains 'notifyTrainers = true' and 'notifyRegistrants = true', both organizers and registrants are notified. The response provides the number of notified trainers and registrants.

*Tags:* `Trainings`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `organizerKey` - _required_ - The key of the training organizer
* `trainingKey` - _required_ - The key of the training

### Get Sessions by Date Range

> This call returns all session details over a given date range for a given organizer. A session is a completed training event.

*Tags:* `Reports`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `organizerKey` - _required_ - The key of the training organizer

### Get Attendance Details

> This call retrieves a list of registrants from a specific completed training session. The response includes the registrants' email addresses, and if they attended, it includes the duration of each period of their attendance in minutes, and the times at which they joined and left. If a registrant does not attend, they appear at the bottom of the listing with timeInSession = 0.

*Tags:* `Reports`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `organizerKey` - _required_ - The key of the training organizer
* `sessionKey` - _required_ - The key of the training session

### Get Sessions By Training

> This call returns session details for a given training. A session is a completed training event. Each training may contain one or more sessions.

*Tags:* `Reports`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `organizerKey` - _required_ - The key of the training organizer
* `trainingKey` - _required_ - The key of the training

### Get Online Recordings for Training

> This call retrieves information on all online recordings for a given training. If there are none, it returns an empty list.

*Tags:* `Recordings`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `trainingKey` - _required_ - The key of the training

### Get Download for Online Recordings

> This call provides the download for the given recording by returning a 302 redirect to the original file.

*Tags:* `Recordings`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `trainingKey` - _required_ - The key of the training
* `recordingId` - _required_ - the unique id of the recording

### Start Training

> Returns a URL that can be used to start a training. When this URL is opened in a web browser, the GoToTraining client will be downloaded and launched and the training will start. A login of the organizer is not required.

*Tags:* `Trainings`

#### Input Parameters
* `Authorization` - _required_ - Access token
* `trainingKey` - _required_ - The key of the training

## License

**flow**ground :- Telekom iPaaS / getgo-com-gototraining-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
