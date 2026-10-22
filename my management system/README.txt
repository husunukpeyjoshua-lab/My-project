RICHES AUTO MANAGEMENT SYSTEM
=============================

A Windows desktop program for an auto workshop. It keeps one secure,
searchable record for every vehicle brought in for repair, logs each faulty
part found, and prints a receipt that shows the customer exactly what was
wrong with the car.

Built with Python, Tkinter (the windows) and SQLite (the database). It can
be packaged as a single .exe file that opens with a double-click.


1. FEATURES
-----------

  - Vehicle and customer records: customer name and phone, plate, make,
    model, year, VIN, mileage, complaint, work done, parts used, total cost,
    status and notes.
  - Sequential record numbers: 00001, 00002, 00003 and so on, assigned
    automatically. A deleted record's number is never reused.
  - Faulty parts tracking: log as many faulty parts as a car has, each with
    what is wrong, severity, action needed, resolution and estimated cost.
  - Costs and charges: list every part, labour charge and extra for a job,
    each with quantity and unit price. The total cost is worked out
    automatically.
  - Customer receipt: one button prints a receipt listing every faulty part
    and every cost, with signature lines for the customer and staff.
  - Search and filter: find jobs by customer name, phone, plate, make, model
    or VIN, and filter by status.
  - CSV export: save the current list, including faulty parts and cost
    items, for Excel.
  - User accounts: personal logins, simple account creation from the login
    screen, and a login lockout. Every account has full access, and every
    account has its own private records.
  - Company logo: add your logo in Business Settings and it is printed at
    the top of every receipt.
  - Show/hide password: click the eye icon in any password box to see what
    you are typing.

2. FILES IN THIS PROJECT
------------------------

  - riches_auto_management_system.py - the whole program (source code)
  - build_exe.bat - one-click script that builds the Windows program
  - README.txt - this file

Files created when the program runs (next to the program):

  - riches_auto_management_system.db - ALL records and user accounts. Back
    this file up.
  - receipts (folder) - one HTML file for every receipt printed, kept in a
    separate sub-folder for each account

3. QUICK START
--------------

Option A: use the finished program (.exe)

  1. Copy RichesAutoManagementSystem.exe into a permanent folder on the C:
     drive, for example C:\RichesAutoManagement. Do not use a OneDrive
     folder.
  2. Double-click it. If Windows shows "Windows protected your PC", click
     More info, then Run anyway. This appears because the program is not
     digitally signed.
  3. On the first launch, create your first account.
  4. From then on, log in with your own account.

Option B: run from the source code

Requirements: Python 3.8 or newer. Nothing else needs installing, because
Tkinter and SQLite come with Python. Then run:

    python riches_auto_management_system.py

4. BUILDING THE .EXE
--------------------

Do this once on a Windows computer that has Python installed (tick "Add
python.exe to PATH" when installing Python).

  1. Put riches_auto_management_system.py and build_exe.bat in the SAME
     folder.
  2. Double-click build_exe.bat and click Run on any security warning.
  3. Wait for the word SUCCESS. The first run needs internet and takes a few
     minutes.
  4. Your program is at dist\RichesAutoManagementSystem.exe

The script creates a private workspace folder called build_env so it never
changes your computer's own Python. You can delete build_env, build and the
.spec file later; keeping them makes the next build faster.

5. USING THE SYSTEM
-------------------

First launch and login

The first time the program opens, it asks you to create your first account
(name, username, and a password of at least 6 characters). After that,
every launch shows the login screen.

  - Five wrong attempts lock the login for 60 seconds, with a live
    countdown. The lock is saved in the database, so closing and reopening
    the program does not reset it.
  - "Create New Account" on the login screen lets anyone make an account
    by typing a name, a username and a password (twice). No approval is
    needed. Every account has the same full access: all the buttons and
    all the features.
  - Every account has its own private records. A new account opens on a
    fresh, empty page and cannot see the records, faulty parts, costs or
    business settings of any other account. The first account keeps all
    the records that were saved before accounts were separated.
  - Every password box has an eye icon on its right. Click it to show what
    you are typing, and click it again to hide it. A line through the eye
    means the password is hidden.

Recording a vehicle

  1. Fill in the form on the left. Customer name and plate number are
     required.
  2. Click Save New. The job gets the next record number and is selected
     automatically.
  3. Use Update to save later changes, and Clear to start a new form.

Logging faulty parts

  1. Select a vehicle in the list (or save a new one).
  2. In the Faulty Parts panel, pick or type the part, describe what is
     wrong, and set severity, action needed, resolution and estimated cost.
  3. Click Add Fault. Click a fault in the panel's list to edit it with
     Update Fault, or remove it with Delete Fault.

The main list shows how many faulty parts each vehicle has.

Recording costs and charges

  1. Select the vehicle, then click the "Costs and Charges" tab (next to
     the "Faulty Parts" tab).
  2. Choose the type (Part, Labour or Other), type a description such as
     "Brake pads (front set)", then enter the quantity and unit price.
     The amount is shown as you type.
  3. Click Add Item. Repeat for every part, labour charge and extra.
  4. Click an item in the list to change it with Update Item, or remove it
     with Delete Item.

The vehicle's Total Cost is worked out automatically from these items, and
the list at the top shows it. Once a vehicle has cost items, the total
always follows them and cannot be typed over. A vehicle with no cost items
keeps the Total Cost you type in the form.

Printing the customer receipt

  1. Select the vehicle.
  2. Click "Print Receipt for Customer".
  3. The receipt opens in your web browser and the print dialog appears.
     Print it, or choose "Save as PDF".
  4. The customer reads the list of faults and both sides sign.

The receipt shows the saved data, so click Update, Add Fault or Add Item
first if you have just typed changes. Each receipt is also saved in the
receipts folder so it can be reprinted.

The receipt lists every faulty part found, then a "Cost Summary (Amount
Charged)" table with every cost item (type, description, quantity, unit
price and amount), the subtotals for parts, labour and other charges, and
the total cost. The estimates in the faulty parts table are shown for
reference only; the amount charged is the total in the Cost Summary.

Manage Users

Every account can open Manage Users in the top bar. It lists all accounts
(username and full name).

  - Add User: type a full name, username and password and click Add User.
    The new account starts with an empty page.
  - Change Password: click an account, enter THAT account's current
    password, then type the new one.
  - Delete User: click an account and enter THAT account's password. The
    account AND all of its records, faulty parts, costs and settings are
    deleted for good. You cannot delete the account you are logged in
    with, and at least one account must always remain.

Because every account is private, changing or deleting another account
always needs that account's own password.

Business settings (each account has its own)

Click Business Settings to set the business name, the phone or address,
and your company logo. They are printed at the top of every receipt made
by your account. The default name is "Allocation Auto Service"; change it
to suit your business.

To add the logo:
  1. Click Choose Logo... and pick a PNG, JPG or GIF picture of your logo.
  2. The picture is shown in the window as a preview.
  3. Click Save. The logo now appears at the top of every receipt.
Use Remove Logo and Save to take it off. Big pictures are made smaller
automatically. The logo is saved inside the database file, so a backup of
the .db file keeps it.

6. BACKUPS
----------

Everything (records, faulty parts, user accounts and settings) is in the
single file riches_auto_management_system.db.

  - Copy it to a flash drive or another computer on a regular schedule, for
    example every week.
  - To move the system to another computer, copy the .exe and the .db file
    into the same folder there.
  - If you have a database from an earlier version named
    allocation_auto_service.db, put it next to the program before the first
    launch. It is renamed and kept automatically.

7. TROUBLESHOOTING
------------------

  - 'python' is not recognized when building: reinstall Python and tick "Add
    python.exe to PATH".
  - build_exe.bat shows a security warning: click Run. The file is unsigned,
    not harmful.
  - "Windows protected your PC" when opening the .exe: click More info, then
    Run anyway.
  - Antivirus removes the .exe: allow the file in your antivirus settings,
    then copy it again.
  - "Too many failed attempts": wait for the 60-second countdown to finish.
  - Forgot a password: it cannot be recovered. Nobody, including other
    accounts, can open an account without its password, because the
    records are private. Write the password down and keep it safe.
  - Receipt does not open: a web browser must be installed. Look in the
    receipts folder for the saved file.
  - Odd behaviour or errors with the database: make sure the program is not
    running from a OneDrive folder.

8. LIMITATIONS
--------------

  - Open sign-up: anyone who can open the program can create an account
    with full access. It starts empty and cannot see other accounts'
    records, but it can use every feature. Keep the computer where only
    your staff can reach it.
  - No password recovery: a forgotten password means that account's
    records cannot be opened.
  - One computer: data is stored on the computer that runs the program.
    Several computers cannot share the same records without a different
    design.
  - No automatic backup: if the .db file is lost, the records are lost.
  - No activity history: the system does not record which user created or
    changed a record.
  - Shared lockout: five wrong attempts by anyone lock the login screen for
    everyone for a minute.
  - Simple password rules: passwords need at least 6 characters; there is no
    expiry or complexity rule.
  - Unsigned program: Windows shows a warning on first launch.

9. POSSIBLE FUTURE IMPROVEMENTS
-------------------------------

  - Activity log showing who created or changed each record
  - Parts list with quantity and price per line, with the total calculated
    automatically
  - Customer list linking repeat visits to the same person and vehicle
  - One-click backup button
  - Shared version for several computers
  - Service reminders, a logo on the receipt, a receipt sized for a thermal
    printer
  - Digital signature on the program to remove the Windows warning

10. TECHNICAL NOTES
-------------------

  - Language and libraries: Python 3 standard library (tkinter, sqlite3,
    hashlib and others). Nothing extra is needed to run the program from
    the source code. Pillow is optional: if it is installed, big logo
    pictures are shrunk automatically.
  - Packaging: PyInstaller, used only when building the .exe. The build
    script also installs Pillow, so the finished .exe can shrink logos.
  - Database tables: records, faulty_parts, cost_items, users and settings.
    Every record belongs to the account that created it.
  - Passwords: stored only as salted PBKDF2-HMAC-SHA256 hashes (200,000
    rounds), never as typed.
  - Data location: next to the .exe when packaged, or next to the .py file
    when run from source.
