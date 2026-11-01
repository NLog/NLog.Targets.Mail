# NLog Mail Target

[![Version](https://badge.fury.io/nu/NLog.Targets.Mail.svg)](https://www.nuget.org/packages/NLog.Targets.Mail)
[![CI](https://github.com/NLog/NLog.Targets.Mail/actions/workflows/ci.yml/badge.svg?branch=master)](https://github.com/NLog/NLog.Targets.Mail/actions/workflows/ci.yml)
[![codecov](https://codecov.io/gh/NLog/NLog.Targets.Mail/graph/badge.svg?token=EJD7UG230N)](https://codecov.io/gh/NLog/NLog.Targets.Mail)

NLog Mail Target for sending email using .NET SmtpClient for each logevent.
- Combine with [FallbackGroup](https://github.com/NLog/NLog/wiki/FallbackGroup-target) to fallback to alternative SMTP-server on error.
- Combine with [BufferingWrapper](https://github.com/NLog/NLog/wiki/BufferingWrapper-target) and [AutoFlushWrapper](https://github.com/NLog/NLog/wiki/AutoFlushWrapper-target) to group multiple logevents into a single email.
- Combine with [LimitingWrapper](https://github.com/NLog/NLog/wiki/LimitingWrapper-target) to throttle the number of emails.
- Combine with [FilteringWrapper](https://github.com/NLog/NLog/wiki/FilteringWrapper-target) to avoid repeating identical emails.

If having trouble with output, then check [NLog InternalLogger](https://github.com/NLog/NLog/wiki/Internal-Logging) for clues. See also [Troubleshooting NLog](https://github.com/NLog/NLog/wiki/Logging-Troubleshooting)

See the [NLog Wiki](https://github.com/NLog/NLog/wiki/Mail-target) for available options and examples.

Note there is also an alternative [NLog.MailKit](https://www.nuget.org/packages/NLog.MailKit)-nuget-package that depends on the MailKit-library.

> ⚠️ Microsoft recommends not to use the SmtpClient class for new development because SmtpClient doesn't support many modern protocols. Use MailKit or other libraries instead. For more information, see [SmtpClient shouldn't be used](https://learn.microsoft.com/dotnet/api/system.net.mail.smtpclient#remarks).

## Register Extension

NLog will only recognize type-alias `Mail` when loading from `NLog.config`-file, if having added extension to `NLog.config`-file:

```xml
<extensions>
    <add assembly="NLog.Targets.Mail"/>
</extensions>
```

Alternative register from code using [fluent configuration API](https://github.com/NLog/NLog/wiki/Fluent-Configuration-API):

```csharp
LogManager.Setup().SetupExtensions(ext => {
   ext.RegisterTarget<NLog.Targets.MailTarget>();
});
```
