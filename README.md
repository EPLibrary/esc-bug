# HeadlessUI Modal Escape key bug

This project demonstrates a bug with comboboxes in modal dialogs in recent versions of
HeadlessUI.

When the combobox input has focus, pressing esc does not close the dialog.

Pressing esc does work properly if you click just below the input inside of the modal.

HeadlessUI v.1.6.1 works fine, but v.1.6.2 does not.
You can test this by downgrading headlessui to v.1.6.1 and running npm install, then rebuilding this project