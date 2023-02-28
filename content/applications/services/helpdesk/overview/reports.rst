=========
Reporting
=========

Odoo *Helpdesk* includes several reports that provide the opportunity to track trends for customer
support tickets, identify areas for improvement, manage employee workloads, and confirm when
customer expectations are met.

Available reports
=================

Details about the reports available in Odoo *Helpdesk* can be found below. To view the different
reports, go to :menuselection:`Helpdesk --> Reporting`.

Ticket Analysis
---------------

The *Ticket Analysis* report (:menuselection:`Helpdesk --> Reporting --> Ticket Analysis`) provides
an overview of every customer support ticket in the database. This includes the number of tickets
assigned among teams and individual users.

This report is useful in identifying where teams are spending the most time, and helps determine if
there is an uneven workload distribution among the support staff. The default report counts the
number of tickets per team and groups them by stage.

.. image:: reports/tickets-default.png
   :align: center
   :alt: View of Ticket Analysis report default view.

Alternative measures can be selected to track where the most time is spent at different points in
the workflow. To change the measures used for the report that is currently displayed, or to add
more, click the :guilabel:`Measures` button, and select one or more options from the drop-down
menu:

- :guilabel:`Average Hours to Respond`
- :guilabel:`Hours Open`
- :guilabel:`Hours Spent`
- :guilabel:`Hours to Assign`
- :guilabel:`Hours to Close`
- :guilabel:`Hours to First Response`
- :guilabel:`Hours to SLA Deadline`
- :guilabel:`Rating /5`
- :guilabel:`Count`

SLA Status Analysis
-------------------

The *SLA Status Analysis* report (:menuselection:`Helpdesk --> Reporting --> SLA Status Analysis`)
tracks how quickly an SLA (Service Level Agreement) is fulfilled, as well as the success rate of
individual policies.

By default, this report is filtered to show the number of :abbr:`SLAs (Service Level Agreements)`
failed, as well as the failure rate over the last 30 days, grouped by team.

.. image:: reports/sla-status.png
   :align: center
   :alt: View of Group by options of Ticket Analysis report.

To change the measures used for the report that is currently displayed, or to add more, click the
:guilabel:`Measures` button, and select one or more options from the drop-down menu:

- :guilabel:`% of Failed SLA`
- :guilabel:`% of SLA in Progress`
- :guilabel:`% of Successful SLA`
- :guilabel:`Number of SLA Failed`
- :guilabel:`Number of SLA Successful`
- :guilabel:`Number of SLA in Progress`
- :guilabel:`Working Hours to Assign`
- :guilabel:`Working Hours to Close`
- :guilabel:`Working to Reach SLA`
- :guilabel:`Count`

.. example::
   To see the number of tickets that were able to achieve the stated :abbr:`SLA (Service Level
   Agreement)` objectives, and track the amount of time it took to achieve those objectives, click
   :menuselection:`Measures --> Number of SLA Successful` and :menuselection:`Measures --> Workings
   Hours to Reach SLA`.

   To sort these results by the team members assigned to the tickets, select :menuselection:`Total
   --> Assigned to`.

.. seealso::
   :doc:`Service Level Agreements (SLA) </applications/services/helpdesk/overview/sla>`

Customer Ratings
----------------

The *Customer Ratings* report (:menuselection:`Helpdesk --> Reporting -- Customer Ratings`)
displays an overview of the ratings received on individual support tickets, as well as any
additional comments submitted with the rating.

.. image:: reports/customer-ratings.png
   :align: center
   :alt: View of the kanban display in the Customer Ratings report.

Click on an individual rating to see additional details about the rating assigned by the customer,
including a link to the original ticket.

.. image:: reports/ratings-details.png
   :align: center
   :alt: View of the details of an individual customer rating.

.. tip::
   On the rating's details page, select the :guilabel:`Visible Internally Only` option to hide the
   rating from the customer portal.

The *Customer Ratings* report is displayed in a kanban view by default, but can also be displayed
in graph, list, or pivot view.

.. seealso::
   :doc:`Ratings </applications/services/helpdesk/overview/ratings>`

View and filter options
=======================

On any Odoo report, the view and filter options vary, depending on what data is being analyzed,
measured, and grouped. See below for additional information on the available views for the
*Helpdesk* reports.

.. note::
   Only one measure may be selected at a time for graphs, but pivot tables can include multiple
   measures.

Pivot view
----------

The *pivot* view presents data in an interactive manner. All three *Helpdesk* reports are available
in pivot view.

The pivot view can be accessed on any report by selecting the :guilabel:`grid icon` at the top right
of the screen.

.. image:: reports/pivot-view.png
   :align: center
   :alt: View of the SLA status analysis report in Odoo Helpdesk.

To add a group to a row or column to the pivot view, click the :guilabel:`+ (plus sign)` next to
:guilabel:`Total`, and then select one of the groups. To remove one, click the :guilabel:`- (minus
sign)` and de-select the appropriate option.

Graph view
----------

The *graph* view presents data in either a *bar*, *line*, or *pie* chart.

Switch to the graph view by selecting the :guilabel:`line chart icon` at the top right of the
screen. To switch between the different charts, select the *related icon* at the top left of the
chart, while in graph view.

.. tabs::

   .. tab:: Bar chart

      .. image:: reports/bar-chart.png
         :align: center
         :alt: View of the SLA status analysis report in bar view.

   .. tab:: Line chart

      .. image:: reports/line-chart.png
         :align: center
         :alt: View of the Customer Ratings report in line view.

   .. tab:: Pie chart

      .. image:: reports/pie-chart.png
         :align: center
         :alt: View of the Ticket analysis report in pie chart view.

.. tip::
   Both the *bar chart* and *line chart* can utilize the *stacked* view option. This presents two
   (or more) groups of data on top of each other, instead of next to each other, making it easier
   to compare data.

Save and share a favorite search
--------------------------------

The *Favorites* feature found on *Helpdesk* reports allows users to save their most commonly used
filters without having to reconstruct them every time they are needed.

To create and save new *Favorites* on a report, follow the steps below:

- Set the necessary parameters using the :guilabel:`Filters`, :guilabel:`Group By` and
  :guilabel:`Measures` options.
- Click :menuselection:`Favorites --> Save current search`.
- Rename the search.
- Select :guilabel:`Use by default` to have these filter settings automatically displayed when the
  report is opened. Otherwise, leave it blank.
- Select :guilabel:`Share with all users` to make this filter available to all other database users.
  If this box is not checked, it will only be available to the user who creates it.
- Click :guilabel:`Save` to preserve the configuration for future use.

.. image:: reports/save-filters.png
   :align: center
   :alt: View of the save favorites option in Odoo Helpdesk.

.. seealso::
   - :doc:`Start receiving tickets </applications/services/helpdesk/overview/receiving_tickets>`
   - :doc:`Odoo reporting </applications/general/reporting>`
