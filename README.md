# NLog Mail Target

[![Version](https://badge.fury.io/nu/NLog.Targets.Mail.svg)](https://www.nuget.org/packages/NLog.Targets.Mail)
[![AppVeyor](https://img.shields.io/appveyor/ci/nlog/NLog-Targets-Mail/master.svg)](https://ci.appveyor.com/project/nlog/NLog-Targets-Mail/branch/master)

NLog Mail Target for sending email using .NET SmtpClient for each logevent. Can also be combined with [BufferingWrapper](https://github.com/nlog/NLog/wiki/BufferingWrapper-target) to group multiple logevents into a single email. Can also be combined with [LimitingWrapper](https://github.com/NLog/NLog/wiki/LimitingWrapper-target) to throttle the number of emails.

If having trouble with output, then check [NLog InternalLogger](https://github.com/NLog/NLog/wiki/Internal-Logging) for clues. See also [Troubleshooting NLog](https://github.com/NLog/NLog/wiki/Logging-Troubleshooting)

See the [NLog Wiki](https://github.com/NLog/NLog/wiki/Mail-target) for available options and examples.

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
