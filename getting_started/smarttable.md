---
title: Smart table
description: 
published: true
date: 2020-04-01T08:19:21.821Z
tags: 
---

# Smart table
 
In Cashstory OS smart tables display data in a table with sorting, filtering, pagination & add/edit/delete functions. Smart tables are linked to boxes (from the left hand panel, see [boxes](https://docs.cashstory.com/en/getting_started/boxes)). 
To display smart tables we use the <a href="https://akveo.github.io/ng2-smart-table/#/" target="_blank">ng2-smart-table</a> library.  

## Overview
Smart tables are represented by a json object :
```json
"smartTable": {
	"database": "darkknight",
  "collection": "workspaces",
  "model": "workspace",
  "rights": [
  	"POST",
    "GET",
    "PUT",
    "DELETE"
  ],
  "settings": {
  	"actions": {
    	"custom": [
      	{
        	"name": "downloadAction",
          "title": "<i class=\"fal fa-arrow-alt-to-bottom fa-xs p-1 m-1\" title=\"Download\"></i>"
        }
        {
          "name": "seeWorkspaceAction",
          "title": "<i class=\"fal fa-eye fa-xs p-1 m-1\" title=\"See\"></i>"
        },
        {
          "name": "editJsonAction",
          "title": "<i class=\"fal fa-code fa-xs p-1 m-1\" title=\"Edit\"></i>"
        }
      ],
      "delete": true,
      "add": true,
      "edit": true
    },
    "columns": {
      "_id": {
        "title": "id"
      },
      "name": {
        "title": "Name"
      }
    }
  }
}
```
## Basic configuration

### First step
First step before starting configuring the smart table you need to know what collection you want to use from the MongoDB database. 

This is an example of a collection :

![image.png](/image.png =650x390)

The model is your data structure, in this example we have : id, member, siren, entity, type, units, dashboard. Model property is optional.

### Second step
Then you can start configuring the smart table by editing the workspace configuration file:

![capture_d’écran_2020-03-03_à_10.35.40.png](/capture_d’écran_2020-03-03_à_10.35.40.png =650x380) 

To make it easier all the basic smart table properties are described down below.

> ⚠️ Properties with a \* are mandatory
{.is-warning}

| Property    | Type   | Description                                                  |
| ----------- | ------ | ------------------------------------------------------------ |
| database*   | string | Name of the database we use to show data in the table.       |
| collection* | string | Name of the database collection you want to use for the table.        |
| model       | string | Name of the model you want to use from the database collection.       |
| rights      | array  | The rights people have on this smart table data <br />POST : add new data in the collection <br />GET : read data in the collection<br />PUT : update, edit some data in the collection<br />DELETE : delete data in the collection |
| settings*   | object | Contains the settings of the smart table described down below                    |
​
**```settings``` object basic properties**
​
| Property | Type   | Description                                                  |
| -------- | ------ | ------------------------------------------------------------ |
| actions  | object | Settings for the table actions. Add custom buttons to the smart table. Each button have a name property and a title that can contain a <a href="https://fontawesome.com/" target="_blank">Font awesome</a> icon. |
| pager    | number | Choose the number of table row you want to display per page. |
| columns  | object | Use this object to name the columns of the smart table. Example format: `columns: { **columnKey**: { title: 'Some Title' } }` or `columns: { 'data.subdata': { title: 'Some Title' } }`  |

### Result
After configuration the smart table should look like this with your own data and settings: 

![capture_d’écran_2020-03-03_à_15.49.36.png](/capture_d’écran_2020-03-03_à_15.49.36.png =750x160)

## Advanced configuration

This is some advanced parameters you can use to configure the settings object in your smart table object : 

**```settings``` object advanced properties**
| Property                                 | Type                                                        | Default         | Description                                                  |
| ---------------------------------------- | ----------------------------------------------------------- | --------------- | ------------------------------------------------------------ |
| *Required Table Settings*                |                                                             |                 |                                                              |
| columns                                  | Object                                                      | n/a             | Table column settings, by default an empty object. Example format: `columns: { **columnKey**: { title: 'Some Title' } }` or `columns: { 'data.subdata': { title: 'Some Title' } }` Please note, **columnKey** must be the same as a key in data array objects. |
| *Column Settings*                        |                                                             |                 | List of a column's settings                                  |
| title                                    | string                                                      | ''              | Column title                                                 |
| class                                    | string                                                      | ''              | Column class                                                 |
| width                                    | string                                                      | ''              | Column width, example: '20px', '20%'                         |
| editable                                 | boolean                                                     | true            | Whether this column is editable or not                       |
| type                                     | 'text'\|'html'\|'custom'                                    | 'text'          | If type is text then cell value will be inserted as text. If type is html then cell value will be inserted as html. If type is custom the `renderComponent` property must be defined. |
| renderComponent                          | any                                                         | null            | Custom component that will be responsible for rendering the cell content while in view mode. Type must be custom in order for this to work. You can see an <a href="https://github.com/akveo/ng2-smart-table/blob/master/src/app/pages/examples/custom-edit-view/advanced-example-custom-editor.component.ts" target="_blank">example here</a> |
| editor                                   | Object                                                      | n/a             | Editor attributes settings                                   |
| editor.type                              | 'text' \| 'textarea' \| 'completer' \| 'list' \| 'checkbox' | 'text'          | Editor used when new row is added or edited                  |
| editor.config                            | Object                                                      | n/a             | Editor configuration settings. Mandatory only for editor types completer, list |
| editor.config.true                       | string                                                      | ''              | Only on checkbox type. Defines the value to assign when the checkbox is checked. This parameter is optional, if omitted, `true` will be used. |
| editor.config.false                      | string                                                      | ''              | Only on checkbox type. Defines the value to assign when the checkbox is not checked. This parameter is optional, if omitted, `false` will be used. |
| editor.config.list                       | Array                                                       | [ ]             | Only on list type. Example format: `{ value: 'Element Value', title: 'Element Title' }` Html is supported if column type is 'html' |
| editor.config.completer                  | Object                                                      | n/a             | Only on completer type. Example format: Completer configuration settings |
| editor.config.completer.data             | Array                                                       | [ ]             | Autocomplete list data source. Example format: `{ id: 10, name: 'Nick', email: 'rey@karina.biz' }` |
| editor.config.completer.searchFields     | string                                                      | ''              | Comma separated list of fields to search on. Fields may contain dots for nested attributes; if empty or null all data will be returned |
| editor.config.completer.titleField       | string                                                      | ''              | Name of the field to use as title for the list item          |
| editor.config.completer.descriptionField | string                                                      | ''              | Name of the field to use as description for the list item    |
| filter                                   | Object                                                      | n/a             | Column filter attributes settings. This object accepts the same properties as the `editor` object. The available types are: `checkbox`, `select`, `completer`. The `checkbox` type accepts one more optional property compared to the `editor` version: resetText: string. It defines the text of the button to reset the checkbox selection.<a href="https://github.com/akveo/ng2-smart-table/blob/master/src/app/pages/examples/filter/advanced-example-filters.component.ts" target="_blank">Click here to see an example</a> on how to configure it. |
| sort                                     | boolean                                                     | true            | Column sort settings, enable/disable.                        |
| sortDirection                            | 'asc'\|'desc'                                               | n/a             | Sort table by this column with this direction by default. Applied only when sort = true. Note: multiple sort option is not supported yet, so sortDirection can be applied to only one column per table. |
| filter                                   | boolean                                                     | true            | Column filter settings, enable/disable                       |
| *Other Table Settings*                   |                                                             |                 |                                                              |
| mode                                     | 'external'\|'inline'                                        | 'inline'        | Determines how to react on action links (Add, Edit, Delete). 'external' - just trigger the events (LINK HERE). 'inline' - process internally, show forms/inputs/etc |
| hideHeader                               | 'boolean'                                                   | false           | Set to true to not display the table header (which includes table column titles) |
| hideSubHeader                            | 'boolean'                                                   | false           | Set to true to not display the table sub-header (which includes filters and global table actions (currently - Add action)) |
| noDataMessage                            | string                                                      | 'No data found' | Message shown when there is no data in the table             |
| attr                                     | Object                                                      | n/a             | Table attributes settings                                    |
| attr.id                                 | string                                                      | ''              | Table element id                                             |
| attr.class                               | string                                                      | ''              | Table element class                                          |
| actions                                  | Object                                                      | n/a             | Settings for the table actions                               |
| actions.columnTitle                      | string                                                      | 'Actions'       | Actions column title                                         |
| actions.add                              | boolean                                                     | true            | Show/not show Add button                                     |
| actions.edit                             | boolean                                                     | true            | Show/not show Edit button                                    |
| actions.delete                           | boolean                                                     | true            | Show/not show Delete button                                  |
| actions.position                         | 'left'\|'right'                                             | 'left'          | Choose actions column position                               |
| filter                                   | Object                                                      | n/a             | Settings for the table filter                                |
| filter.inputClass                        | string                                                      | ''              | Filter input class                                           |
| edit                                     | Object                                                      | n/a             | Edit action settings                                         |
| edit.inputClass                          | string                                                      | ''              | Editing form input class                                     |
| edit.editButtonContent                   | string                                                      | 'Edit'          | Edit row button content/title                                |
| edit.saveButtonContent                   | string                                                      | 'Update'        | Update button content/title                                  |
| edit.cancelButtonContent                 | string                                                      | 'Cancel'        | Cancel button content/title                                  |
| edit.confirmSave                         | boolean                                                     | false           | Enable/disable (confirmEdit) event. If enabled data will be edited only if confirm.resolve() called. |
| add                                      | Object                                                      | n/a             | Add action settings                                          |
| add.inputClass                           | string                                                      | ''              | New row input class                                          |
| add.addButtonContent                     | string                                                      | 'Add New'       | Add New button content/title                                 |
| add.createButtonContent                  | string                                                      | 'Create'        | Create button content/title                                  |
| add.cancelButtonContent                  | string                                                      | 'Cancel'        | Cancel button content/title                                  |
| add.confirmCreate                        | boolean                                                     | false           | Enable/disable (confirmCreate) event. If enabled data will be added only if confirm.resolve() called. |
| delete                                   | Object                                                      | n/a             | Delete action settings                                       |
| delete.deleteButtonContent               | string                                                      | 'Delete'        | Delete row input class                                       |
| delete.confirmDelete                     | boolean                                                     | false           | Enable/disable (confirmDelete) event. If enabled data will be deleted only if confirm.resolve() called. |
| pager                                    | Object                                                      | n/a             | Pager settings                                               |
| pager.display                            | boolean                                                     | true            | Whether to display the pager or not                          |
| pager.perPage                            | number                                                      | 10              | Rows per page                                                |

## Upload file in smart table 

You can upload your own file in the smart table to add data, this file needs to be in json format.

To visualize how to structure a json file you can go on the **</>** button in the first column to open the json code. 

![upload-smarttable.png](/upload-smarttable.png =650x120)

To upload your file click on the button on the left corner of the smart table, choose your json file and confirm. After refreshing the page your data should be added in the smart table.

## Configuration example

Here is a smart table configuration example to display users data :
```json
"smartTable": {
	"database": "darkknight",
  "collection": "users",
  "model": "user",
  "rights": [
  	"POST",
    "GET",
    "PUT",
    "DELETE"
   ],
   "settings": {
     "actions": {
       "custom": [
         {
           "name": "downloadAction",
           "title": "<i class=\"fal fa-arrow-alt-to-bottom fa-xs p-1 m-1\" title=\"Download\"></i>"
          },
          {
             "name": "editJsonAction",
             "title": "<i class=\"fal fa-code fa-xs p-1 m-1\" title=\"Edit\"></i>"
           }
         ],
         "delete": true,
         "add": true,
         "edit": true
       },
       "pager": {
         "perPage": 30
       },
       "columns": {
         "firstName": {
           "title": "Firstname"
         },
         "lastName": {
           "title": "Lastname"
         },
         "email": {
           "title": "Email"
         },
         "phoneNumber": {
           "title": "Phone"
         },
         "updatedAt": {
           "title": "Last Loggin"
         },
         "workspaceCurrent": {
           "title": "Workspace Current"
         }
       }
     }
   }
```





