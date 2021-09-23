<!-- DO NOT EDIT THIS FILE! -->
<!-- Instead edit contrib/ms-teams.php -->
<!-- Then run bin/docgen -->

# ms-teams

[Source](/contrib/ms-teams.php)


## Installing

Require ms-teams recipe in your `deploy.php` file:

Setup:
1. Open MS Teams
2. Navigate to Teams section
3. Select existing or create new team
4. Select existing or create new channel
5. Hover over channel to get tree dots, click, in menu select "Connectors"
6. Search for and configure "Incoming Webhook"
7. Confirm/create and copy your Webhook URL
8. Setup deploy.php
    Add in header:
```php
require 'contrib/ms-teams.php';
set('teams_webhook', 'https://outlook.office.com/webhook/...');
```
Add in content:
```php
before('deploy', 'teams:notify');
after('deploy:success', 'teams:notify:success');
after('deploy:failed', 'teams:notify:failure');
```
9.) Sip your coffee

## Configuration

- `teams_webhook` – teams incoming webhook url, **required**
  ```
  set('teams_webhook', 'https://outlook.office.com/webhook/...');
  ```
- `teams_title` – the title of application, default `{{application}}`
- `teams_text` – notification message template, markdown supported
  ```
  set('teams_text', '_{{user}}_ deploying `{{branch}}` to *{{target}}*');
  ```
- `teams_success_text` – success template, default:
  ```
  set('teams_success_text', 'Deploy to *{{target}}* successful');
  ```
- `teams_failure_text` – failure template, default:
  ```
  set('teams_failure_text', 'Deploy to *{{target}}* failed');
  ```

- `teams_color` – color's attachment
- `teams_success_color` – success color's attachment
- `teams_failure_color` – failure color's attachment

## Usage

If you want to notify only about beginning of deployment add this line only:

```php
before('deploy', 'teams:notify');
```

If you want to notify about successful end of deployment add this too:

```php
after('deploy:success', 'teams:notify:success');
```

If you want to notify about failed deployment add this too:

```php
after('deploy:failed', 'teams:notify:failure');
```



## Configuration
### teams_title
[Source](https://github.com/deployphp/deployer/blob/master/contrib/ms-teams.php#L78)

Title of project



### teams_text
[Source](https://github.com/deployphp/deployer/blob/master/contrib/ms-teams.php#L83)

Deploy message

```php title="Default value"
'_{{user}}_ deploying `{{branch}}` to *{{target}}*'
```


### teams_success_text
[Source](https://github.com/deployphp/deployer/blob/master/contrib/ms-teams.php#L84)



```php title="Default value"
'Deploy to *{{target}}* successful'
```


### teams_failure_text
[Source](https://github.com/deployphp/deployer/blob/master/contrib/ms-teams.php#L85)



```php title="Default value"
'Deploy to *{{target}}* failed'
```


### teams_color
[Source](https://github.com/deployphp/deployer/blob/master/contrib/ms-teams.php#L88)

Color of attachment

```php title="Default value"
'#4d91f7'
```


### teams_success_color
[Source](https://github.com/deployphp/deployer/blob/master/contrib/ms-teams.php#L89)



```php title="Default value"
'#00c100'
```


### teams_failure_color
[Source](https://github.com/deployphp/deployer/blob/master/contrib/ms-teams.php#L90)



```php title="Default value"
'#ff0909'
```



## Tasks

### teams:notify
[Source](https://github.com/deployphp/deployer/blob/master/contrib/ms-teams.php#L93)

Notifying Teams.




### teams:notify:success
[Source](https://github.com/deployphp/deployer/blob/master/contrib/ms-teams.php#L108)

Notifying Teams about deploy finish.




### teams:notify:failure
[Source](https://github.com/deployphp/deployer/blob/master/contrib/ms-teams.php#L123)

Notifying Teams about deploy failure.



