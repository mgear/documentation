=============
Configuration
=============

Settings
========

The :guilabel:`Settings` section is where localization settings are configured, including a detailed
view of all  benefits provided to employees.

To access the settings, go to :menuselection:`Payroll --> Configuration --> Settings`. Whether or
not payslips should be posted in accounting, or if SEPA payments are created, is selected here.

.. image:: configuration/payroll-settings.png
   :align: center
   :alt: Settings available for payroll.

Any country specific localizations are set up in the localization section of the settings screen.
All localization items are pre-populated when the country is specified during the creation of the
database. It is not recommended to alter the specific localization settings unless specifically
required.

Work Entries
============

Work Entry Types
----------------

When creating a work entry in the :guilabel:`Payrol` application, or when an employee enters
information in the :guilabel:`Timesheets` application, a work entry type needs to be selected. This
list is automatically created based off the localization settings set in the database.

Work entry types all have a code to aid in the creation of payslips, and ensure all taxes and fees
are correctly entered.

Go to :menuselection:`Payroll --> Configuration --> Work Entry Types` to view the current work entry
types available.

.. image:: configuration/work-entry-types.png
   :align: center
   :alt: List of all work entry types currently available.

New Work Entry
~~~~~~~~~~~~~~

To create a new :guilabel:`Work Entry Type`, click the :guilabel:`Create` smart button. Enter the
information on the pop up form:

- **Work Entry Type Name:** The name should be short descriptive, such as “Sick Time” or “Public
  Holiday”.

- **Code:** This code will appear with the work entry type on timesheets and payslips. Since the
  code will be used in conjunction with the **Accounting** application, it is advised to check with
  the accounting department for a code to use.

- **Sequence:** The sequence will determine the order the work entry will be computed  in the
  payslip list.

- **Check Off Boxes:** If any of the items in the list applies to the work entry, check off the box
  by clicking it. If :guilabel:`Time Off` is checked off, a :guilabel:`Time Off Type` field will
  appear. This field will have a drop down to select the specific type of time off, or a new type of
  time off can be entered.

.. image:: configuration/new-work-entry.png
   :align: center
   :alt: New work entry type box.

- **Rounding:**

  - **No Rounding:** A time sheet entry will not have the time modified.
  - **Half Day:** A time sheet entry will be rounded to the closest half day amount.
  - **Day:**  A time sheet entry will be rounded ot the closest full day amount.

.. example::
   If an employee enters a time of 5.5 hours on a timesheet, and *Rounding* is set to *No Rounding*,
   the entry will be 5.5 hours. If *Rounding* is set to *Half Day*, the entry will change to 4
   hours. If it is set to *Day*, it will change to 8 hours.

Working Times
-------------

To view the currently configured :guilabel:`Working Times` go to :menuselection:`Payroll -->
Configuration --> Working Times`. The working times that are available for an employee's contracts
and work entries, is found in this list. **Working Times** are company specific. Each company must
identify each type of working time they will use. For example, a standard 40 hour work week will
need to have an entry for each company that uses a 40 hour standard work week.

.. image:: configuration/working-times.png
   :align: center
   :alt: All working times currently set up in the database.

New Working Time
~~~~~~~~~~~~~~~~

To create a new :guilabel:`Working Time`, click the :guilabel:`Create` smart button. Enter the
information on the pop up form.

.. image:: configuration/new-working-times.png
   :align: center
   :alt: New working type box.

The fields will be auto populated for a regular 40 hour work week but can be modified. Change the
name of the working time, and the days and items the working time applies to.

If the working time should be in a two-week configuration, click the :guilabel:`Switch To 2 Week
Calendar` smart button. This will create entries for an *even week* and and *odd week*.

Salary
======

Structure Types
---------------

The different types of structure types can be seen by going to :menuselection:`Payroll -->
Configuration --> Structure Types`.

There are two default structure types configured in Odoo: *Employee*, and *Worker*. Typically,
*Employee* is used for salaried employees, which is why the *Wage Type* is **Monthly Fixed Wage**,
and *Worker* is typically used for employees paid by the hour, so the  *Wage Type* is **Hourly**.

.. image:: configuration/structure-type.png
   :align: center
   :alt: List of all structure types.

New *Structure Types* can be created by clicking the :guilabel:`Create` smart button. Most fields
will be pre-populated, but all fields can be edited. Once the fields are edited, click the
:guilabel:`Save` smart button to save the changes, or :guilabel:`Discard` to delete the entry.

.. image:: configuration/new-structure.png
   :align: center
   :alt: New structure type box.

Structures
----------

:guilabel:`Structures` displays all the various structures for each **Structure Type**. To view the
structures, go to :menuselection:`Payroll --> Configuration --> Structures`.

.. image:: configuration/salary-structure.png
   :align: center
   :alt: All available salary structures.

Each *structure* will lit the various *Structure Types* associated with that specific *Structure*.
Each record listed for a structure is a specific rule for that particular structure.

The default structures for the Employee are **Regular Pay**, and **13th month - End of the year
bonus**. Each specific structure lists how many rules that structure has. For example, *Regular Pay*
has 11 rules.

.. image:: configuration/structure-regular-pay-rules.png
   :align: center
   :alt: Salary structure details for Regular Pay.

Rules
-----

Each structure type has a set of rules to follow for accounting purposes. These rules are configured
by the localization, and affect the *Accounting* application, so modifications to the default rules,
or the creation of new rules, should only be done when necessary.

To view all the rules, go to :menuselection:`Payroll --> Configuration --> Rules`. Click on the drop
down arrow next to the listed Structure (such as **Regular Pay**) to view all the *Rules* for that
specific **Structure**.

.. image:: configuration/rules.png
   :align: center
   :alt: Rules for each salary structure type.

Rule Parameters
---------------

Salary Rule Parameters affect the various Rules for salary configuration. New Rule Parameters are
not recommended to create unless specifically needed by the *Accounting* department. To access the
parameters, go to :menuselection:`Payroll --> Configuration --> Rule Parameters`.

Other Input Types
-----------------

When creating payslips, it is sometimes necessary to add other entries for specific circumstances,
like expenses, reimbursements, or deductions. These other inputs can be seen by going to
:menuselection:`Payroll --> Configuration --> Other Input Types`.

.. image:: configuration/other-input.png
   :align: center
   :alt: Other input types for payroll.

A new *Input Type* can be created by clicking the :guilabel:`Create` smart button. Enter the
description, the code, and which structure type it applies to. Click the :guilabel:`Save` smart
button when donesmart button to save the changes, or :guilabel:`Discard` to delete the entry.

.. image:: configuration/input-type-new.png
   :align: center
   :alt: Create a new Input Type.

Salary Package Configurator
===========================

Advantages
----------

When offering potential employees a position, there can be certain **advantages** to make the offer
more appealing. Any specific advantage is listed in the advantages section of the configuration
menu. To see the advantages, go to  :menuselection:`Payroll --> Configuration --> Advantages`.

.. image:: configuration/advantages.png
   :align: center
   :alt: Settings available for payroll.

To make a new advantage, click the :guilabel:`Create` smart button. A pop up appears for the
advantage. Enter the information in the fields, then click the :guilabel:`Save` smart button to save
the changes, or :guilabel:`Discard` to delete the entry.

.. image:: configuration/new-advantage.png
   :align: center
   :alt: List of advantages employee's can have.


Personal Info
-------------

The *Personal Information* section lists all of the fields that are available to enter on the
employee's card.

.. image:: configuration/personal-info.png
   :align: center
   :alt: Personal information that appear on employee cards to enter.

To edit an entry, click on the line, and a box with the configuration for that piece of information
will appear. To edit the information, click the :guilabel:`Edit` smart button, and modify the entry.
When done, click :guilabel:`Save` or :guilabel:`Discard` to save the information or cancel the
edits.

To create a new entry, click the :guilabel:`Create` smart button. A box will appear with all of the
fields to enter.

.. image:: configuration/personal-new.png
   :align: center
   :alt: New personal information entry.

The two most important fields are the *Is Required* checkbox, and the *Display Type* drop down
selection. Checking the *Is Required* box will make the field mandatory on the Employee's card.

The *Display Type* drop down allows for the information to be entered in a variety of ways, from a
text box, a customizable radio button, a check box, a document, and more. This will affect how the
field appears.

Once the information is entered, click the :guilabel:`Save` or :guilabel:`Discard` smart buttons to
either save or delete the entry.
