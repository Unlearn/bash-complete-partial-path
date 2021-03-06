# Enhanced file path completion in bash

This project adds incomplete file path expansion to bash (the feature that was
originally unique to zsh).

When the Tab key is pressed bash expands only the last piece of the path by
default, but with the completion functions from this project it will assume any
of path elements might be incomplete. For example: `cd /u/s/app<Tab>` will
produce nothing by default, but will be expanded to `cd /usr/share/applications`
if you've configured bash to load this file.

Watch a demo screencast to see this feature in action:
[![asciicast](https://asciinema.org/a/0zhzOYbkF22pWLmbx1RHCYyqQ.png)](https://asciinema.org/a/0zhzOYbkF22pWLmbx1RHCYyqQ)

To enable the described behavior source [**this file**][main] from your
~/.bashrc. Supported features are:

- Special characters in completed path are automatically escaped if present
- Tilde expressions are properly expanded (as per [bash documentation])
- If user had started writing the path in quotes, no character escaping is
  applied. Instead the quote is closed with a matching character after expanding
  the path.
- If [bash-completion] package is already in use, this code will safely override
  its `_filedir` function. No extra configuration is required, just make sure
  you source this project *after* the main bash-completion.

Completion functions have been tested and reported to work on Debian 9 and
Windows (msys).


# Contributing

Thank you for taking an interest in this project! If you wish to improve it
please open an issue or create a pull request.

Your help is most needed in the following areas:

- Documenting the project
- Finding (and fixing) existing bugs
- Expanding OS support (if it's lacking)
- Adding better demo asciicasts and screenshots

The project was created to do one thing (autocomplete partial paths) and to do
it well. Please try to keep all code in one file and to keep it short. Major new
functionality is probably better suited for a separate project.

I'm open to dialog and I promise to behave responsibly and treat all
contributors with respect. Please try to do the same, and treat others the way
you want to be treated.

Thank you again!


# License and copyright

Copyright © 2018 Vitaly Potyarkin

```
   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use these files except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
```

[bash-completion]: https://salsa.debian.org/debian/bash-completion
[bash documentation]: https://www.gnu.org/software/bash/manual/html_node/Tilde-Expansion.html
[main]: bash_completion
