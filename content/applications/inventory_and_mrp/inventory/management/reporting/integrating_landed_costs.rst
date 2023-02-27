==============================================
Landed Costs: Add additional costs to products
==============================================

When companies perform profit analyses, they need to know that they are as accurate as possible. To
make sure of that, all costs and expenses need to be included; this includes the sum of expenses
associated with shipping a product, also known as *Landed Costs*.

In Odoo, the landed costs feature allows the user to add and include additional costs on goods
they purchase. This can include the cost of freight, shipping, insurance, taxes, and more.

Configuration
=============

To use landed costs, go to :menuselection:`Inventory --> Configuration --> Settings`, scroll down to
the :guilabel:`Valuation` section, and click the checkbox to enable :guilabel:`Landed Costs`. A
default accounting journal can also be set, in which entries involving landed costs will be
recorded. After this has been enabled, click :guilabel:`Save`.

.. image:: integrating_landed_costs/integrating-landed-costs-settings.png
   :align: center
   :alt: Enabled Landed Costs feature in Inventory settings.

.. important::
   Landed costs can only be applied to products using a :abbr:`FIFO (First In First Out)` or
   :abbr:`AVCO (Average Cost)` costing method, and automated inventory valuation.

Create a Landed Cost product
============================

Landed costs can be manually entered each time a vendor bill is created. However, some products
might always have the same types of charges applied to them, and thus might always list landed
costs on vendor bills. In this case, it could be beneficial to create a landed cost product.

To create a landed cost product, go to :menuselection:`Inventory --> Products --> Products`, and
click :guilabel:`Create`.

Name and fill out the product information, and change the :guilabel:`Product Type` to
:guilabel:`Service`. Then, click the :guilabel:`Purchase` tab, and under the :guilabel:`Landed
Costs` section, select :guilabel:`Is a Landed Cost`. Once selected, a new field will appear below to
select the :guilabel:`Default Split Method`. Select :guilabel:`Equal`, then :guilabel:`Save`.

.. image:: integrating_landed_costs/integrating-landed-costs-split-method.png
   :align: center
   :alt: Landed costs and split method enabled on product form.

.. note::
   There is no need to set a price (or cost) on a landed cost product, because the
   price will change with each order, depending on the landed cost of each shipment.

Create a Request for Quotation
==============================

Before adding landed cost on goods, create a new :abbr:`RFQ (Request for Quotation)`. To do that,
navigate to the :menuselection:`Purchase` app, and click :guilabel:`Create`.

Add a :guilabel:`Vendor`, add a product to the :guilabel:`Product` lines, and fill out the
remaining information on the new :abbr:`RFQ (Request for Quotation)`. Then, click :guilabel:`Confirm
Order.` Once the quotation has been confirmed, it turns into a purchase order. Click
:guilabel:`Receive Products`, :guilabel:`Validate`, and set :guilabel:`Apply` to set the
:guilabel:`Done` quantities. Navigate back to the purchase order (via the breadcrumbs).

Create a Vendor Bill
====================

Now that goods have been received from the purchase order, a vendor bill can be created. To do so,
click :guilabel:`Create Bill.` The bill will automatically populate with the information from the
purchase order. To add a landed cost to the bill, click :guilabel:`Edit`.

While in :guilabel:`Edit` mode, click :guilabel:`Add a line` to add the landed cost product created
previously. Since this product was created as a landed cost, the checkbox under the
:guilabel:`Landed Costs` column will be selected by default.

.. image:: integrating_landed_costs/integrating-landed-costs-vendor-bill.png
   :align: center
   :alt: Landed cost added on product lines on vendor bill.

.. important::
   Since no :guilabel:`Price` was set on the product form for the landed cost, it must be set
   manually on the vendor bill.

Create Landed Costs
===================

Once all the information on the bill has been filled out, click :guilabel:`Create Landed Costs`.
This will navigate to a new accounting entry for the *Landed Cost*. From here, next to
:guilabel:`Transfers`, the warehouse receipt with which this landed cost is associated must be
specified. Additionally, an expenses :guilabel:`Account` must be selected, as well.

To see how the landed costs affect the items on the purchase order, click the :guilabel:`Valuation
Adjustments` tab. From here, the :guilabel:`Original Value` and :guilabel:`New Value` can be seen,
as well as the :guilabel:`Additional Landed Cost` that changed the original purchase order.

.. image:: integrating_landed_costs/integrating-landed-costs-valuation-adjustments.png
   :align: center
   :alt: Valuation adjustments tab for landed costs on vendor bill.

Once everything is set, :guilabel:`Validate` and :guilabel:`Save`. Then, click back to the
vendor bill (via the breadcrumbs).

.. note::
   When the :guilabel:`Default Split Method` is set to :guilabel:`Equal`, the landed cost will be
   split equally between all items included on the purchase order. Since this :abbr:`PO (Purchase
   Order)` has just one item, the full amount will be applied to this item.

To wrap up the vendor bill, :guilabel:`Confirm`, :guilabel:`Register Payment`, and :guilabel:`Create
Payment`.

.. tip::
   Landed costs don't always need to be created from the vendor bill. They can also be created by
   going to :menuselection:`Inventory --> Operations --> Landed Costs` and clicking
   :guilabel:`Create`.
