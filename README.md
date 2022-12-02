﻿# Our.Umbraco.BlockPreview

**Our.Umbraco.BlockPreview** enables easy to use rich HTML previews for the Umbraco Block List and Block Grid editors.

## Todo
- [x] Support for BlockList or BlockGrid with settings models
- [ ] Add support for ModelsBuilder modes other than `SourceCodeManual`/`SourceCodeAuto`
- [x] Add support for areas
- [x] Get it working with the [Umbraco Block Grid Example Website](https://github.com/umbraco/Umbraco.BlockGrid.Example.Website)
## Installation
The Umbraco 10.4+ version of this package is [available via NuGet](https://www.nuget.org/packages/Our.Umbraco.BlockPreview).

To install the package, you can use either .NET CLI:

```
dotnet add package Our.Umbraco.BlockPreview --version 1.0.0-alpha003
```

or the older NuGet Package Manager:

```
Install-Package Our.Umbraco.BlockPreview -Version 1.0.0-alpha003
```

## Usage
This package installs a custom Angular preview for both the Block List and Block Grid editors.

When setting up a block to be part of the List or Grid, setting the 'Custom View' property to the appropriate `block-[grid|list]-preview.html` file will generate preview HTML based on the respective partial view found in `/Views/Partials/blocklist/Components` or `/Views/Partials/blockgrid/Components`.

How to select the custom views when creating a Block List/Grid:
![Screenshot](https://github.com/rickbutterfield/Our.Umbraco.BlockPreview/blob/main/screenshots/screenshot1.png "The Umbraco backoffice showing a panel titled 'Select view', with two HTML files in a list available for selection")

Before and after of how components look within the Block Grid:
![Screenshot2](https://github.com/rickbutterfield/Our.Umbraco.BlockPreview/blob/main/screenshots/screenshot2.png "Before and after of how components look within the Block Grid")

### Grid-specific setup
When using the new Block Grid, any reference to
```
@await Html.GetBlockGridItemAreasHtmlAsync(Model)
```
should be replaced with
```
@await Html.GetPreviewBlockGridItemAreasHtmlAsync(Model)
```
which can be found in `Our.Umbraco.BlockPreview.Extensions`. This ensures that the grid editors correctly load in the back office.

## Thanks
This package is entirely based on the amazing work done by [Dave Woestenborghs for 24days in Umbraco 2021](https://archive.24days.in/umbraco-cms/2021/advanced-blocklist-editor/). His code has been extended to support the new Block Grid editor in v10.4/v11 and turned into this package.
