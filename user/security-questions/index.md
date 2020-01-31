[title]: # (Security Questions)
[tags]: # (questions)
[priority]: # (1)
# Security Questions

Password Reset Server uses questions to confirm the identity of a user before they can reset their
password. As part of the enrollment process, a user will answer all of the questions that are a part of the
security policy they are assigned. They must also answer all questions correctly before resetting their
password.
Password Reset Server stores all of the answers to a question using an irreversible algorithm called SHA512. This ensures that all answers are kept confidential. Even a malicious user that has access to
Password Reset Server’s database will be unable to extract the users’ answers.