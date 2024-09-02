# Data Contract Manager (Community Edition)

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fdatacontract-manager%2Fdatacontract-manager-ce%2Fmain%2Fazure%2Fdatacontract-manager-ce.json)

Data Contract Manager (Community Edition) is a free version of the [Data Contract Manager](https://www.datacontract-manager.com) that you can host yourself.

In the Community Edition, every user can change any data product or data contract.  
If you need advanced role and permission management, SSO, or customizations, consider the [Enterprise Edition](https://www.datacontract-manager.com/#pricing).

Community support is offered [in Slack in the channel #datacontract-manager](https://datacontract.com/slack).

## Demo

Play with our [demo app](https://demo.datacontract-manager.com/)!


## Getting Started

Data Contract Manager (Community Edition) is available as Docker image `datacontractmanager/datacontract-manager-ce` on [Docker Hub](https://hub.docker.com/r/datacontractmanager/datacontract-manager-ce).

[Deploy to Azure](azure/) or start Data Contract Manager (Community Edition) locally with Docker Compose:

```bash
git clone https://github.com/datacontract-manager/datacontract-manager-ce.git
cd datacontract-manager-ce
docker compose up --detach
```

Now you can access the Data Contract Manager (Community Edition) at [http://localhost:8081](http://localhost:8081).

> **_NOTE:_**  The Docker Compose configuration uses a dummy mail server, so no mails are actually sent. Configure our SMTP host accordingly as environment variables.

## Requirements

- Docker Resources: 1 CPU and 1 GB of RAM, more is better
- PostgreSQL version 16 or newer
- PostgreSQL with the extensions available: `vector`, `hstore`, `uuid-ossp`
- SMTP server for transactional emails, such as SendGrid, AWS SES, Azure Communication Services email (Office 365 / Exchange is not recommended, as [SMTP Basic Auth is deprecated](https://learn.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-online/deprecation-of-basic-authentication-exchange-online))


## Configuration

Configure an external database and mail server for production use.

| Environment Variable                             | Example                                       | Description                                                                                 |
|--------------------------------------------------|-----------------------------------------------|---------------------------------------------------------------------------------------------|
| APPLICATION_HOST_WEB                             | `http://localhost:8081`                       | The host of the application, used e.g., in email templates build URLs to Data Contract Manager. |
| APPLICATION_MAIL_FROM                            | `Data Contract Manager <noreply@example.com>` | The sender email address for emails.                                                        |
| SPRING_DATASOURCE_URL                            | `jdbc:postgresql://postgres:5432/postgres`    | JDBC URL of the database                                                                    |
| SPRING_DATASOURCE_USERNAME                       | `postgres`                                    | Login username of the database                                                              |
| SPRING_DATASOURCE_PASSWORD                       | `postgres`                                    | Login password of the database                                                              |
| SPRING_MAIL_HOST                                 | `smtp.example.com`                            | SMTP server host                                                                            |
| SPRING_MAIL_PORT                                 | `587`                                         | SMTP server port                                                                            |
| SPRING_MAIL_USERNAME                             |                                               | Login user of the SMTP server                                                               |
| SPRING_MAIL_PASSWORD                             |                                               | Login password of the SMTP server                                                           |
| SPRING_MAIL_PROPERTIES_MAIL_SMTP_AUTH            | `true`                                        | Use basic authentication for SMTP                                                           |
| SPRING_MAIL_PROPERTIES_MAIL_SMTP_STARTTLS_ENABLE | `true`                                        | Ensure that TLS is used                                                                     |

## Deploy on Azure

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fdatacontract-manager%2Fdatacontract-manager-ce%2Fmain%2Fazure%2Fdatacontract-manager-ce.json)

Use the Azure Resource Manager [template](azure/datacontract-manager-ce.json) to deploy Data Contract Manager as WebApp, together with a Postgres database in a virtual network.
You need to provide SMTP server configuration.


## Get help, reporting bugs and feature requests

Community support is offered [in Slack in the channel #datacontract-manager](https://datacontract.com/slack).

Want to report a bug or request a feature? Open an [issue](https://github.com/datacontract-manager/datacontract-manager-ce/issues/new).

## License

The Data Contract Manager (Community Edition), being made available as a Docker image, is licensed under the [Community License](https://www.datacontract-manager.com/COMMUNITY-LICENSE.txt).