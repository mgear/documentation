=============
Authorize.Net
=============

`Authorize.Net <https://www.authorize.net>`__ is a United States-based online payment solution
provider, allowing businesses to accept **credit cards**.

.. image:: authorize/authorize-net.png
   :align: center
   :alt: Authorize.Net logo

This Payment Acquirer offers additional options that are not available for other :doc:`Payment
Acquirers <../payment_acquirers>`, such as the ability to process your customer's payment after
delivery.

Authorize.Net account
=====================

If not done yet, choose a plan and `Sign Up for an Authorize.Net account
<https://www.authorize.net/sign-up.html>`__.

Odoo needs your **API Credentials & Keys** to connect with your Authorize.Net account, which
comprise:

- API Login ID
- Transaction Key
- Signature Key

To retrieve them, log into your Authorize.Net account, go to :menuselection:`Account --> Security
Settings --> General Security Settings --> API Credentials & Keys`, and generate your **Transaction
Key** and **Signature Key**.

.. image:: authorize/authorize-api-keys.png
   :align: center
   :alt: Generate your Transaction Key and Signature Key on your Authorize.Net account

.. seealso::

   - `Authorize.Net: Getting Started Guide
     <https://support.authorize.net/s/article/Authorize-Net-Getting-Started-Guide>`__

Payment Acquirer Configuration
==============================

To configure Authorize.Net as Payment Acquirer in Odoo, go to :menuselection:`Accounting -->
Configuration --> Payment Acquirers`, open **Authorize.Net**, and change the **State** to *Enabled*.
Don't forget to click on *Save* once you've set everything up.

.. note::
   Please refer to the :doc:`Payment Acquirers documentation <../payment_acquirers>` to read how to
   configure this payment acquirer.

Credentials
-----------

Copy your credentials from your Authorize.Net account (API Login Id, API Transaction Key, and API
Signature Key), paste them in the related fields under the **Credentials** tab, then click on
**Generate Client Key**.

.. note::
   The **API Client Key** is necessary only if you select *Payment from Odoo* option as
   :ref:`Payment Flow <payment_acquirers/payment_flow>`.

.. important::
   If you are trying Authorize.Net as a test, with a *sandbox account*, change the :guilabel:`State`
   to :guilabel:`Test Mode`. We recommend doing this on a test Odoo database, rather than on your
   main database.

   If you set :guilabel:`Test Mode` on Odoo and use an authorize.net account instead of a
   sandbox.authorize.net account, it results in the following error: *The merchant login ID or
   password is invalid or the account is inactive*.

Payment Flow
------------

The **Payment Flow** lets you decide if to redirect the user to the payment acquirer's portal to
authenticate the payment, or if to stay on the current page and authenticate the payment from Odoo.
This field is under the **Configuration** tab.

If you select *Redirection to the acquirer website*, make sure you add a **Default Receipt URL** and
a **Default Relay Response URL** to your Authorize.net account.

To do so, log into your Authorize.Net account, go to :menuselection:`Account --> Transaction Format
Settings --> Transaction Response Settings --> Response/Receipt URLs`, and set the default links:

- | Default Receipt URL:
  | *https://[yourcompany.odoo.com]*/**payment/authorize/return**
- | Default Relay Response URL:
  | *https://[yourcompany.odoo.com]*/**shop/confirmation**

.. note::
   | Failing to complete this step results in the following error:
   | *The referrer, relay response or receipt link URL is invalid.*

Capture the payment after the delivery
--------------------------------------

The **Capture Amount Manually** field is under the **Configuration** tab. If enabled, the funds are
reserved for 30 days on the customer's card, but not charged yet.

.. image:: authorize/authorize-configuration.png
   :align: center
   :alt: Authorize.Net Configuration tab on Odoo

To capture the payment, go to the related Sales Order and click on *Capture Transaction*. If the
order is canceled, you can click on *Void Transaction* to unlock the funds from the customer's card.

.. image:: authorize/authorize-capture.png
   :align: center
   :alt: Hold the credit card payment until you capture or revoke it on Odoo

.. warning::
   After **30 days**, the transaction is **voided automatically** by Authorize.net.

.. note::
   With other payment acquirers, you can manage the capture in their own interfaces, not from Odoo.

Authorize.Net statement export
==============================

.. admonition:: Template

   You can find the Excel template for the import here :ref:` iii `

To import a statement, first log into your Authorize.Net account, and go to :menuselection:`Account
--> Statements --> eCheck.Net Settlement Statement`. Second, a range of transactions must be
defined. To do so, search for the first and last settlement batches of the desired range. These will
be the exported transactions.

.. example::
   .. image:: authorize/authorize-settlement-batch.png
      :align: center
      :alt: Settlement batch of the an Authorize.Net statement

   In this case, the first batch (01/01/2021) belongs to the settlement of the 31/12/2020, so the
   **opening** settlement is from the 31/12/2020.

Once the range defined, copy (CTRL/COMMAND + C) all lines within the range and paste them
(CRTL/COMMAND + V) into the :guilabel:`Report 1 Download` tab of the Excel sheet.
Next, go to :menuselection:`Transaction Search --> Search for a Transaction`, enter the range of
settlement dates, and click :guilabel:`Search`.

When the list is generated, click :guilabel:`Download to File`. In the pop-up window, select
:guilabel:`Expanded Fields with CAVV Response/Comma Separated`, enable :guilabel:`Include Column
Headings`, and finally click :guilabel:`Submit`. Open the text file, select :guilabel:`All`, copy
the data and paste it into the :guilabel:`Report 2 Download` tab of the Excel sheet.

Transit lines are automatically filled-in and updated in the :guilabel:`transit for report 1` and
:guilabel:`transit for report 2` tabs of the Excel sheet. Make sure all entries are present, and if
not, copy the **formula** from previous filled-in lines and paste it into the empty lines.

.. important::
   To get the same closing balance, do *not* remove any line from the Excel sheet.

Import into Odoo
----------------

To import the data into Odoo, go to the Excel sheet, copy the data from the :guilabel:`transit
report 2` tab and **paste special** only the **values** in the :guilabel:`Odoo Import to CSV` tab.
Then, look for *blue*-highlighted cells in the :guilabel:`Odoo Import to CSV` tab. These are
**chargeback** entries without any **reference** number. To fix this, go to
:menuselection:`Authorize.Net --> Account --> Statements --> eCheck.Net Settlement Statement`, look
for :guilabel:`Charge Transaction/Chargeback`, and click it. Copy the **invoice description**, paste
it into the :guilabel:`Label` cell of the :guilabel:`Odoo Import to CSV` tab, and add "**Chargeback
/**" before the description. If you have multiple invoices, add a line into the Excel for each
invoice and copy/paste the description into each respective cell.

.. note::
   For **chargeback/returns** combined in the payouts, you need to create a new Excel line for each
   invoice.

.. example::
   .. image:: authorize/authorize-chargeback-desc.png
      :align: center
      :alt: Charge back description

Next, remove **zero transaction** and **void transaction** line items, and change the **format** of
the :guilabel:`Amount` column in the :guilabel:`Odoo Import to CSV` tab to *Number*. Go back to
:menuselection:`eCheck.Net Settlement Statement --> Search for a Transaction`,

search for batch settlements.
Change the date of payments received from this batch to the date of the **batch settlement**.

.. seealso::
   - `Authorize.Net: Getting Started Guide
     <https://support.authorize.net/s/article/Authorize-Net-Getting-Started-Guide>`__
   - :doc:`../payment_acquirers`
   - :doc:`../../websites/ecommerce/shopper_experience/payment_acquirer`
