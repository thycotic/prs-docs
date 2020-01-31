[title]: # (Question Types)
[tags]: # (questions)
[priority]: # (2)
# Question Types

Password Reset Server supports multiple types of questions. This ensures variety to increase security.

## Text Question

A text question is displayed in the form of text which the user must supply an answer for. For example,
a text question could be “In which city have you lived in the longest?” Text questions should be personal and not easy to guess, such as “What color is your car?” A malicious user could easily guess a common
car color – or may even know the answer if they know the user personally.

## Image Question

An image question is set of images which the user is given and will need to recall when resetting their
password. During the enrollment process, the user will be shown a configurable number of images.
During the password reset process, they will be asked to recall the images they were displayed.

## Email Question

An email question will email the user a pin code during the password reset process. The user will then
have to type in the pin the email provided. This is common for users that have access to email with a
mobile device such as a smart phone.

## Phone Question

A phone question will call the user and tell them a five digit code during the password reset process.
They will then type in the five digit code to answer the question. During the enrollment process, the user
will provide their phone number.

## SMS Question

A phone question will send the user a PIN code SMS message during the password reset process. They
will then type in the code to answer the question. During the enrollment process, the user will provide
their phone number.

A phone or SMS question requires that Password Reset Server be configured with a phone provider. See
the sections on __Configuring TeleSign™__ or __Configuring ProxStop™__ for additional information on
configuration.
