## Notifications Service

**This task must comply with the following requirements:** <br>

#### Model

**Notification**

  - id;
  - notification_type - _type of notification, string constant;_
  - email_title - _title of the email;_
  - email_text - _text of the email._

**Email Notification**

  - id;
  - notification_id;
  - email - _user email;_
  - sent_at - _time of successful email sending;_
  - status - _enum:_
    - WAIT_FOR_SENDING (default);
    - SUCCESSFULLY_SENT;
    - SENDING_SKIPPED;
  - number_of_attempts - _number of attempts to send email;_

Each notification must have its notification type.

When creating a notification, you must:

  - Get an email title by notification type;
  - Get an email template by notification type. The notification template must be a Jtwig file. All notification templates must be stored in the Jtwig templates directory in a separate notifications directory;
  - Get an email context from the related object;
  - Get the email of the user who needs to send the notification. Define by type of notification and by the related object.

After that, it is necessary to substitute the data from the context in the template notification to receive an email message.

The notification service must implement the `NotificationService` interface:

```
interface NotificationService
{
    /**
     * Create notifications for users, store it in the database and return an array of notification id
     * @param string $notificationType
     * @param object $relatedObject
     * @return array
     */
    public function createNotifications(string $notificationType, object $relatedObject): array;

    /**
     * Sends all notifications
     */
    public function sendAllNotifications(): void;

    /**
     * Send notifications by primary
     * @param int ...$ids
     */
    public function sendNotifications(int ...$ids): void;
}
```

Each of the notifications has a field - the number of attempts. This field stores the current number of attempts to send a notification. The value should increase by one with each attempt. The maximum number of attempts should be configured in environment variables.