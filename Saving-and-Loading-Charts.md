## Table of contents

- [Overview](#overview)
  - [What is a chart layout](#what-is-a-chart-layout)
  - [What is a study template](#what-is-a-study-template)
- [Saving of chart layouts and study templates](#saving-of-chart-layouts-and-study-templates)
- [Predefined REST API](#predefined-rest-api)
  - [Example of a storage](#example-of-a-storage)
  - [Developing your own backend](#developing-your-own-backend)
  - [Using Demo Charts and Study Templates Storage](#using-demo-charts-and-study-templates-storage)
  - [Managing Access to Saved Charts](#managing-access-to-saved-charts)
- [API handlers](#api-handlers)
  - [Chart layouts](#chart-layouts)
  - [Study Templates](#study-templates)
- [Low-level API](#low-level-api)
- [Additional use cases](#additional-use-cases)
  - [Saving charts automatically](#saving-charts-automatically)
  - [Restoring last saved chart](#restoring-last-saved-chart)

## Overview

From this article you will know how to save users' chart layouts and study templates, and restore them when users get back.

### What is a chart layout

Chart layout is a group of charts (in Trading Terminal) or a single chart (in Charting Library). Chart layout content includes drawings, indicators and chart settings like colors, styles etc.

### What is a study template

Study template is a set of applied indicators and their settings (inputs and styles).

## Saving of chart layouts and study templates

Usually, if your use cases assume the use of drawings, you'll need to think about storing users' chart layouts. Enabling study templates on the chart requires implementing a storage.
It is recommended to store chart layouts on a server, unless you want the users to have the only one chart layout.
In the case of one possible chart layout you can consider using LocalStorage. Otherwise, you shouldn't use LocalStorage, because its size is limited.

To simplify development of a storage for chart layouts and study templates, the library includes 3 layers:

1. Predefined REST API and a sample server-side storage in case you want to save chart layouts and study templates on a server and you don't have a general purpose storage that can be used for this
1. API handlers allows you to add custom processing of save/load commands coming from GUI
1. Low-level API to get/set current chart layout / study templates content

## Predefined REST API

The library supports a predefined REST API to save chart layouts and study templates on your server. It sends requests in a certain format that is described below. We provide an example of server-side storage that is a good point to start from.

### Example of a storage

We created a tiny storage sample with Python and PostgreSQL that can be found in [our GitHub](https://github.com/tradingview/saveload_backend).
You can use it and run on your own server so that you'll be able to have control over all your users' saved data.

Here are a few steps for those who want to have their own chart storage:

1. Clone our repository to your host
1. Run the data service or use our demo service. Here is a short to-do list for anyone who is not familiar with Django.
    1. Install Python 3.x and Pip.
    1. Install PostgreSQL or some other Django-friendly database engine.
    1. Go to you chart storage folder and run `pip install -r requirements.txt`
    1. Go to charting_library_charts folder and set up your database connection in settings.py (see `DATABASES` @ line #12). Please remember to create the appropriate database in your PostgreSQL.
    1. Run `python manage.py migrate` . This will create the database schema without any data.
    1. Run `python manage.py runserver` to run a TEST instance of your database. Don't use the command above in the production environment. Use some other program (i.e., Gunicorn).
1. Set up your Charting Library page: set `charts_storage_url = url-of-your-charts-storage`, also set `client_id` and `user_id` (see details below) in the widget constructor.
1. Enjoy!

**Remark**: Manual database filling/editing is not the intended usage. Please avoid doing this as you may hurt the Django infrastructure.

**Remark**: This example doesn't support an authorization so we do not recommend to use it without adding this layout of security in production.

### Developing your own backend

If you decided to develop your own storage that accepts predefined REST API requests, here is the description of the end-points that you'll need to implement.

- Charting Library sends HTTP/HTTPS commands to `charts_storage_url/charts_storage_api_version/charts?client=client_id&user=user_id` for charts and `charts_storage_url/charts_storage_api_version/study_templates?client=client_id&user=user_id` for study templates. `charts_storage_url`, `charts_storage_api_version`, `client_id` and `user_id` are the arguments of the [widget constructor](Widget-Constructor).
- You should implement the processing of 4 requests: save / load / delete / list.

#### LIST CHARTS

GET REQUEST: `charts_storage_url/charts_storage_api_version/charts?client=client_id&user=user_id`

RESPONSE: JSON Object

1. `status`: `ok` or `error`
1. `data`: Array of Objects
    1. `timestamp`: UNIX time when the chart was saved (example, `1449084321`)
    1. `symbol`: base symbol of the chart (example, `AA`)
    1. `resolution`: resolution of the chart (example, `1D`)
    1. `id`: unique integer identifier of the chart (example, `9163`)
    1. `name`: chart name (example, `Test`)

#### SAVE CHART

POST REQUEST: `charts_storage_url/charts_storage_api_version/charts?client=client_id&user=user_id`

1. `name`: name of the chart
1. `content`: content of the chart
1. `symbol`: chart symbol (example, `AA`)
1. `resolution`: chart resolution (example, `1D`)

RESPONSE: JSON Object

1. `status`: `ok` or `error`
1. `id`: unique integer identifier of the chart (example, `9163`)

#### SAVE AS CHART

POST REQUEST: `charts_storage_url/charts_storage_api_version/charts?client=client_id&user=user_id&chart=chart_id`

1. `name`: name of the chart
1. `content`: content of the chart
1. `symbol`: chart symbol (example, `AA`)
1. `resolution`: chart resolution (example, `1D`)

RESPONSE: JSON Object

1. `status`: `ok` or `error`

#### LOAD CHART

GET REQUEST: `charts_storage_url/charts_storage_api_version/charts?client=client_id&user=user_id&chart=chart_id`

RESPONSE: JSON Object

1. `status`: `ok` or `error`
1. `data`: Object
    1. `content`: saved content of the chart
    1. `timestamp`: UNIX time when the chart was saved (example, `1449084321`)
    1. `id`: unique integer identifier of the chart (example, `9163`)
    1. `name`: name of the chart

#### DELETE CHART

DELETE REQUEST: `charts_storage_url/charts_storage_api_version/charts?client=client_id&user=user_id&chart=chart_id`

RESPONSE: JSON Object

1. `status`: `ok` or `error`

#### LIST STUDY TEMPLATES

GET REQUEST: `charts_storage_url/charts_storage_api_version/study_tempates?client=client_id&user=user_id`

RESPONSE: JSON Object

1. `status`: `ok` or `error`
1. `data`: Array of Objects
    1. `name`: template name (example, `Test`)

#### SAVE STUDY TEMPLATE

POST REQUEST: `charts_storage_url/charts_storage_api_version/study_tempates?client=client_id&user=user_id`

1. `name`: name of the template
1. `content`: content of the template

RESPONSE: JSON Object

1. `status`: `ok` or `error`

#### LOAD STUDY TEMPLATE

GET REQUEST: `charts_storage_url/charts_storage_api_version/study_tempates?client=client_id&user=user_id&chart=chart_id&template=name`

1. `name`: name of the template

RESPONSE: JSON Object

1. `status`: `ok` or `error`
1. `data`: Object
    1. `name`: name of the template
    1. `content`: saved content of the template

#### DELETE STUDY TEMPLATES

DELETE REQUEST: `charts_storage_url/charts_storage_api_version/study_tempates?client=client_id&user=user_id&template=name`

1. `name`: name of the template

RESPONSE: JSON Object

1. `status`: `ok` or `error`

### Using Demo Charts and Study Templates Storage

We're running a demo chart storage service to let you save/load charts as soon as you build your Charting Library.
Here is the link <http://saveload.tradingview.com>. Note that it's provided as-is since it's a demo.

We do not guarantee its stability. Also, note that we delete the data in the storage on a regular basis.

### Managing Access to Saved Charts

You are responsible for the charts that your users are able to see and load.
A user can see/load charts that have the same `client_id` and `user_id` that the user has.
`client_id` is an identifier of the user's group.
The intended use is when you have a few groups of users or when you have a few sites that use the same chart storage.
So the common practice is to set `client_id = your-site's-URL`. It's up to you to decide.

`user_id` is a unique identifier of a user. Users ID belongs to a particular `client_id` group.
You can either set it for each user individually (private storage for each user) or set it for all users or user groups (public storage).

Here are a few examples:

`client_id`|`user_id`|Effect
---|---|---
Your site URL or other link|Unique user ID|Each user has a private chart storage that other users can't see.
Your site URL or other link|The same value for all users|Each user can see and load any saved chart.
Your site URL or other link|Unique user ID for registered users along with a separate setting for anonymous users|Each registered user has a private chart storage that other users can't see. All anonymous users share a single storage.

## API handlers

Prefer using the API handlers if you have your own back-end service that you can use for storing chart layouts and study templates.
[save_load_adapter](Widget-Constructor#save_load_adapter) is an object containing the save/load API handlers. Using of the API handlers prevents the library from sending the REST requests. These functions are called by the library when users click on save/load UI elements.

### Chart layouts

 1. `getAllCharts(): Promise<ChartMetaInfo[]>`

    A function to get all saved charts.

    `ChartMetaInfo` is an object with the following fields:
     - `id` - unique ID of the chart.
     - `name` - name of the chart.
     - `symbol` - symbol of the chart.
     - `resolution` - resolution of the chart.
     - `timestamp` - UNIX time when the chart was last modified.

 1. `removeChart(chartId): Promise<void>`

     A function to remove a chart. `chartId` is a unique ID of the chart (see `getAllCharts` above).

 1. `saveChart(chartData: ChartData): Promise<ChartId>`

     A function to save a chart.

    `ChartData` is an object with the following fields:
     - `id` - unique ID of the chart (may be `undefined` if it wasn't saved before).
     - `name` - name of the chart.
     - `symbol` - symbol of the chart.
     - `resolution` - resolution of the chart.
     - `content` - content of the chart.

    `ChartId` - unique ID of the chart (string)

 1. `getChartContent(chartId): Promise<ChartContent>`

     A function to load the chart from the server.

    `ChartContent` is a string with the chart content (see `ChartData::content` field in `saveChart` function).

### Study Templates

 1. `getAllStudyTemplates(): Promise<StudyTemplateMetaInfo[]>`

     A function to get all saved study templates.

    `StudyTemplateMetaInfo` is an object with the following fields:
     - `name` - name of the study template.

 1. `removeStudyTemplate(studyTemplateInfo: StudyTemplateMetaInfo): Promise<void>`

     A function to remove a study template.

 1. `saveStudyTemplate(studyTemplateData: StudyTemplateData): Promise<void>`

     A function to save a study template.

    `StudyTemplateData` is an object with the following fields:
     - `name` - name of the study template.
     - `content` - content of the study template.

 1. `getStudyTemplateContent(studyTemplateInfo: StudyTemplateMetaInfo): Promise<string>`

     A function to load a study template from the server.

 If both `charts_storage_url` and `save_load_adapter` are available  then `save_load_adapter` will be used.

**IMPORTANT:** All functions should return a `Promise` (or `Promise`-like objects).

[In-memory example](Save-Load-Adapter-Example) for testing purposes.

## Low-level API

Content of charts and study templates can be directly accessed using widget's [save() / load() methods](Widget-Methods#savecallback) and [createStudyTemplate() / applyStudyTemplate() methods](Chart-Methods#createstudytemplateoptions).

You are able to save the JSONs where you wish. For example, you may embed them to your saved pages or user's working area etc.

Commonly you might want to hide the save/load GUI elements if you use the Low-level API. You can disable [header_saveload featureset](Featuresets) to hide the save/load GUI elements from the header toolbar.

## Additional use cases

### Saving charts automatically

You might want to automatically save chart layouts. Here are the steps to implement it:

1. Set a [threshold delay](Widget-Constructor#auto_save_delay) in seconds that is used to reduce the number of onAutoSaveNeeded calls.
1. Subscribe to [onAutoSaveNeeded](Widget-Methods#subscribeevent-callback).
1. Call the [saveChartToServer](Widget-Methods#savecharttoserveroncompletecallback-onfailcallback-options) method.

### Restoring last saved chart

Usually users open an empty chart and load their chart layouts using the "Load Chart Layout..." dialog. But you may want to open the last saved chart layout on start. If you use the Low-level API, you can set the chart layout content to the [saved_data](Widget-Constructor#saved_data) field in the widget constructor. Otherwise, it is enough to assign `true` to the [load_last_chart](Widget-Constructor#load_last_chart) field.
