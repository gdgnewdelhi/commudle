# How it works!

As **Commudle** is a platform (initially) for Tech Communities, from the experience and feedback of members we've begun on a journey to make it the most comprehensive and easy to use tool.

Let's take an overview of the way things work in the real world and then you can map it with each model created in the code!:


### User Roles
There are 2 roles majorly in a community:
- Members (Everyone who's filled a registration form for any event is a member)
- Organizers
  - Would include volunteers for now (we want to create another role for this too, specific for events probably)

Here we've also put up roles 'Attendance Managers' and 'System Administrator' in the code in the [DB seed](db/seeds.rb). You'll soon understand how they work.

### Permissions
These are based on the role of the user. Once the user has a role, the file [role_permission](https://github.com/gdgnewdelhi/commudle/blob/master/app/controllers/concerns/role_permission.rb) describes what controllers and actions can the user access.
Multiple roles can be allocated to one user (it's a Many to Many Relation).


### Community
Why is this at the third place is because a user needs to sign up before creating a community (in the DB it's Kommunity, we initially wanted to go with that name but then domain....)!
Each community has the following associated with it:
- events
- users (in different roles)
- data forms (example registration form, call for paper form, feedback form, or may be a general communication form)


### Event
An event has the following associated with it
- data form entities (objects referring to a data form)
  - These further translate to shorlisted speakers
- event entry passes
- event status
- event locations
  - tracks for each location
- comments

#### Now coming to the overall process flow for an Event:

1. Create an event
2. Create registration, call for paper, feedback forms for it (or we can reuse some past forms too)
3. Create a form set and assign a form (there's majorly 3 form sets)
   1. Call For Papers
   2. Registration
   3. Feedback
4. Share the Call For Paper form links with members on Social Media [this is done outside of the platform, but we'd really want to integrate it as well]
5. Finalize speakers from the entries received from Call For Paper (somehow we feel this step can be skipped for a number of events where we have already finalized the speakers)
6. Send RSVP and receive confirmation from the speakers 
   1. In the RSVP email, the speaker will also be prompted to fill the details and links to the slides/content for her/his session
7. By this time, location and track + agenda/schedule can be updated on the event
8. Roll out the registrations and continue with the shorlistings.
9. Close the Call For Paper and Registration forms by updating the status.
10. Send unique entry passes to the confirmed candidate (they confirmed on the RSVP email which has an automatic link for confirmation)
11. **EVENT DAY** : 
    1.  Mark attendance using the attendance page
    2.  You can choose to allow uninvited entries by changing the registration form's status (They'll automatically receive the entry passes)
    3.  At the end of the event, just click one button to send the feedback form to the attendees who've marked their attendance

This sums up almost everything, now it's time for you to get into the code and start making things!
