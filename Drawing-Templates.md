Traiding Terminal sends HTTP/HTTPS commands to `charts_storage_url/charts_storage_api_version/drawing_templates?client=client_id&user=user_id`. `charts_storage_url`, `charts_storage_api_version`, `client_id` and `user_id` are the arguments of the [widget constructor](Widget-Constructor).
You should implement the processing of 4 requests: save template / load template / delete template / list templates.

#### LIST TEMPLATES

GET REQUEST: `charts_storage_url/charts_storage_api_version/drawing_templates?client=client_id&user=user_id&tool=toolName`

1. `toolName`: name of the drawing tool

RESPONSE: JSON Object

1. `status`: `ok` or `error`
1. `data`: Array of drawing templates names
    1. `name`: the drawing template name (example, `Test`)

#### SAVE TEMPLATE

POST REQUEST: `charts_storage_url/charts_storage_api_version/drawing_templates?client=client_id&user=user_id&tool=toolName&name=templateName`

1. `toolName`: name of the drawing tool
1. `templateName`: custom template name

1. `body`: { content: content }
    1. `content`: saved content of the template

RESPONSE: JSON Object

1. `status`: `ok` or `error`

#### LOAD TEMPLATE

GET REQUEST: `charts_storage_url/charts_storage_api_version/drawing_templates?client=client_id&user=user_id&chart=chart_id&tool=toolName&name=templateName`

1. `toolName`: name of the drawing tool
1. `templateName`: template name to get

RESPONSE: JSON Object

1. `status`: `ok` or `error`
1. `data`: Object
    1. `content`: saved content of the template

#### DELETE TEMPLATE

DELETE REQUEST: `charts_storage_url/charts_storage_api_version/drawing_templates?client=client_id&user=user_id&chart=chart_id&tool=toolName&name=templateName`

1. `toolName`: name of the drawing tool
1. `templateName`: name of template to remove

RESPONSE: JSON Object

1. `status`: `ok` or `error`

### Using Demo Drawing Templates Storage

We're running a demo drawing templates storage service to let you save/load drawing templates as soon as you build your Trading Terminal.
Here is the link <http://saveload.tradingview.com>. Note that it's provided as-is since it's a demo.

We do not guarantee its stability. Also, note that we delete the data in the storage on a regular basis.

## save_load_adapter

*Starting from version 1.12.*

One of the parameters in [Widget Constructor](Widget-Constructor#save_load_adapter), this is basically an object containing the save/load functions. It is used to customize the `Templates` dropdown behaviour on Drawing settings floating panel. In adition to required fields you should add drawing templates methods:

1. `getDrawingTemplates(toolName: string): Promise<string[]>`

     A function to get names of all saved drawing templates.

    * `toolName` - name of the drawing tool.

1. `removeDrawingTemplate(toolName: string, templateName: string): Promise<void>`

     A function to remove a drawing template.

1. `saveDrawingTemplate(toolName: string, templateName: string, content: string): Promise<void>`

     A function to save a study template.

     * `toolName` - name of the drawing tool.
     * `content` - content of the study template.

1. `loadDrawingTemplate(toolName: string, templateName: string): Promise<string>`

    * `toolName` - name of the drawing tool.
    * `templateName` - name of the template.

    A function to load a drawing template from the server.

**IMPORTANT:** All functions should return a `Promise` (or `Promise`-like objects).

[In-memory example](Save-Load-Adapter-Example) for testing purposes.
