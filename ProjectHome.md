### Abstract ###
django-reputation is a Django app that lets you track the reputation of your users on your site.

## Dependencies ##
  1. django-command-extensions(http://code.google.com/p/django-command-extensions/)
  1. django.contrib.auth (depends on request.user coming in from middleware)
  1. Django>=1.0
  1. Python>=2.4

### Functionality ###
  1. track and update user reputation based on user actions
  1. limit user access to sections of a site based on reputation access control
  1. limit reputation gains and losses to daily max and min\

## Usage ##

### User Reputation ###
The model models.Reputation defines a one to one relationship with the Users table in your project.  Currently, django-reputation assumes that it will be used in conjunction with django.contrib.auth, but this can be changed easily as long as the request.user is used by your custom auth app.

### Permissions ###
Permissions for restricting access are defined in models.Permission.  Each permission represents an action or level of permission.  Defining Permission(s) makes it easier to code reputation checks and to modify the amount of reputation needed to access parts of the site as you no longer have to hard code user.reputation > some\_integer.

### Reputation Actions ###
Reputation actions are actions by users that can affect the reputation of another user such as voting, commenting or flagging content.  The model models.ReputationAction define actions that can be taken on models in your project which would have an effect on a users reputation.  The model models.UserReputationAction represents instances of ReputationAction(s) which let's you keep a history of the reputation changes that have occurred in your project.