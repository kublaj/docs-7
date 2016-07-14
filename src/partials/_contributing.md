# Contributing
Simpla is open-source under the MIT license, visit our GitHub repos:

**[github.com/simplaio/simpla][simplaio/simpla]** 
The core Simpla library

**[github.com/SimplaElements][SimplaElements]** 
Simpla's element catalogue, hosted on elements.simpla.io

[simplaio/simpla]: https://github.com/simplaio/simpla
[SimplaElements]: https://github.com/SimplaElements

## The elements
The bulk of Simpla's functionality comes from elements in the ecosystem, each talking independently to Simpla's API.

### [`simpla-block`][simpla-block]
Structures data by creating namespaces for SIDs.

### [`simpla-text`][simpla-text]
Contains editable rich-text.

### [`simpla-img`][simpla-img]
An editable image.

### [`sm-module-save`][module-save]
Contains the UI and logic that request all elements save their data back to the API.

### [`sm-module-login`][module-login]
Contains the UI and logic to log a user in when entering edit mode.

### [`sm-module-notify`][module-notify]
Simpla's notification centre. Handles all success, warning, and error messages by logging them and/or notifying with toasts.

[simpla-block]: https://github.com/SimplaElements/simpla-block
[simpla-text]: https://github.com/SimplaElements/simpla-text
[simpla-img]: https://github.com/SimplaElements/simpla-img
[module-save]: https://github.com/SimplaElements/sm-module-save
[module-login]: https://github.com/SimplaElements/sm-module-login
[module-notify]: https://github.com/SimplaElements/sm-module-notify

## Reporting issues
If you find a bug, please report it! If you know which component in the ecosystem is causing the trouble, open a GitHub issue on the appropriate repository. Otherwise open an issue on [simplaio/simpla][simplaio/simpla] or jump on our [Slack] channel and let us know.

Thorough bug reports with expected behavior and steps required to duplicate the issue are greatly appreciated and will help us move quickly.

[slack]: https://slack.simpla.io
[simplaio/simpla]: https://github.com/simplaio/simpla
