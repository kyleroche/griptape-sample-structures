This sample takes in a S3 URI pointing at a spreadsheet file and filters the spreadsheet only to relevant columns based on the natural language criteria you specify. It does this while keeping the spreadsheet data "off prompt" and away from the LLM if you wish to keep the spreadsheet contents away from 3P model providers.

[![Deploy_to_Griptape](https://github.com/griptape-ai/griptape-cloud/assets/2302515/4fd57873-5c93-44a8-8fa3-ac1bf7d73bcc)](https://cloud.griptape.ai/structures/create?sample-name=griptape-csv-filter&type=sample)

## Requirements

- [Anthropic API Key](https://console.anthropic.com/settings/keys)
- [Griptape Cloud Key](https://cloud.griptape.ai/configuration/api-keys)
- AWS Access Key and Secret with S3 Read/Write permissions

## Configuration

env
```
AWS_ACCESS_KEY_ID=
```

env_secrets
```
ANTHROPIC_API_KEY=
AWS_SECRET_ACCESS_KEY=
```

## Running this Sample

This sample filters spreadsheet data down to columns relating to a specific concept. For example, if you have a spreadsheet filled with employee information and you only wanted columns that called out demographic information you could specify `-d demographics` as the filter criteria.

### Locally

You can run this Structure locally by providing the following inputs:

```
python structure.py -i <s3_uri> -d <columns_to_filter>
```

You can optionally specify the `-o` to change the file name. It will always append the date and time the Structure ran to the end of the output file to ensure there is no collision if you run the Structure multiple times or on a schedule.

### Griptape Cloud

You can create a run via the API or the UI. When creating runs in the UI, you will need to specify parameters on their own lines.

```
-i
<s3_uri>
-d
<criteria>
```

#### As a Data Source

Once created in Griptape Cloud, you can specify this [Structure as a Data Source]() if you wish to ingest the filtered data as a Data Source. When running as a Data Source it will still save the output spreadsheet to your S3 bucket so you can validate the filtered information.