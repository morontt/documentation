
.. _user-guide-magento-channel:

Magento Channels and Default Magento Entities
=============================================

OroCRM supports out-of-the-box integration with Magento. Data can be loaded from Magento and back and processed in
OroCRM. :ref:`Channels <user-guide-channels>` of Magento type ("Magento Channels") represent sources of customer-related
data collected from Magento-based eCommerce stores.

.. hint::

    While Magento integration capabilities are pre-implemented, OroCRM can also be integrated with different third-party
    systems.

For each Magento Channel, you can:

- Define integration settings and rules, including synchronization priorities, as described in the
  :ref:`Magento Integration guide <user-guide-magento-channel-integration>`.

- Define :term:`entities <Entity>`, records of which can be loaded to OroCRM from Magento, processed and
  (subject to the synchronization settings) updated in Magento.


Default Entities of a Magento Channel
-------------------------------------

The following entity records can be loaded to OroCRM from a Magento channel by default:

- Web Customers
- Shopping Carts
- Orders
- Magento Newsletter Subscribers

.. hint::

    It is possible to add other system and custom entities to the channel, as well as delete most of the default
    entities from it, subject to you needs.
	
Details of the entity records are uploaded into OroCRM in the course of synchronization, can be
processed from the OroCRM UI and used to create
:ref:`reports <user-guide-reports>` and set up :ref:`related workflows <user-guide-magento-entities-workflows>`.

Detailed description of the entities is provided in the sections below.

.. _user-guide-magento-entities-customers:

*Web Customers*
---------------

The Web Customer records represent Magento customers the data is collected for within the channel. The entity must be 
assigned to a Magento channels

To see theMagento Customer :ref:`grid <user-guide-ui-components-grids>` go to the *Customer* → 
*Magento Customers*.

.. image:: ./img/magento_entities/mag_customers_grid.png

From the :ref:`grid <user-guide-ui-components-grids>` of Magento Customers you can:

- Subscribe or unsubscribe Magento customers to/from the Magento Newsletter: |IcSub| or |IcUns|

- Get to the :ref:`Edit form <user-guide-ui-components-create-pages>` of the list : |IcEdit| 

- Get to the :ref:`View page <user-guide-ui-components-view-pages>` of the list :  |IcView| 


.. note::

    Editing the customer details is posible, only if 
    :ref:`two-way synchronization <user-guide-magento-channel-integration-synchronization>` has been enabled. 

From the Edit page, you can change basic information and address details of the customer, as well as manage the 
password.

From the View page , you can perform the actions specified in the 
:ref:`Communication &  Collaboration section <user-guide-entity-management-create-commun-collab>` of the Web Customer 
entity (*System → Entities → Entity Management/Web Customer*):

.. image:: ./img/magento_entities/view_web_customer.png


*Shopping Carts*
----------------

The Shopping Cart records keep the details on the Magento Customer's actions with the |WT02|_

The only action available from the :ref:`grid <user-guide-ui-components-grids>` of Shopping Carts 
(*Sales → Shopping Carts*) is calling the :ref:`View page <user-guide-ui-components-view-pages>` of their records by 
clicking the |IcView| icon.

From the *View* page of any shopping cart you can

- Perform the actions specified in the 
  :ref:`Communication &  Collaboration section <user-guide-entity-management-create-commun-collab>` of the Shopping
  Cart entity (*System → Entities → Entity Management/Shopping Cart*):

- Synchronize Data, i.e. upload the latest information for the cart/order from Magento and back (as defined by the
  synchronization settings).

.. image:: ./img/magento_entities/view_carts.png

.. important::

    Information for all the carts is updated once in a predefined period (default value is 5 minutes).
    However, it is strongly recommended to update a specific Cart record before you perform any actions with it.

You can also place an order from the :ref:`View page <user-guide-ui-components-view-pages>` of every shopping cart with
*Open* status (items in the cart have not yet been purchased). Click the button to get to the Magento *Place an Order*
form.

.. image:: ./img/magento_entities/view_place_order.png

.. caution::

    Be careful not to confuse the cart status and step of the related workflow. For example, a cart at the step
    "Contacted" can still have the "Open" status (items in the carts have not yet been bought).

.. caution::

    You need to enter your credentials when referred to the Magento for the first time in the session.


*Manage Orders*
---------------

The Order records keep the details of items purchased and ordered by the customer within the channel, including the 
store details, personal and banking data, one-time and total credited, paid and taxed amounts, feed-backs, etc.

The only action available from the :ref:`grid <user-guide-ui-components-grids>` of Orders (*Sales → Orders*), is calling
the :ref:`View page <user-guide-ui-components-view-pages>` of their records by clicking the |IcView| icon.

From the :ref:`View page <user-guide-ui-components-view-pages>` of any order you can:

- Perform the actions specified in the 
  :ref:`Communication &  Collaboration section <user-guide-entity-management-create-commun-collab>` of the Order entity 
  (*System → Entities → Entity Management/Order*).

- Synchronize Data: upload the latest information for the cart/order from Magento and back (if so is specified by the
  synchronization settings).

.. image:: ./img/magento_entities/view_orders.png


.. _user-guide-magento-entities-newsletters:
  
*Magento Newsletter Subscribers*
--------------------------------

The Magento Newsletter Subscriber keep details of subscription to the Magento Newsletter for the Web Customers. 

.. caution::

    The Magento Newsletter Subscribers are only supported with OroBridge version 1.1.5 or higher.

To see the Magento Newsletter Subscribers :ref:`grid <user-guide-ui-components-grids>` go to the *Marketing* → 
*Magento Newsletter Subscribers*.

.. image:: ./img/magento_entities/nl_menu.png

From the :ref:`grid <user-guide-ui-components-grids>` of Magento Customers you can:

- Subscribe or unsubscribe Magento customers to/from the Magento Newsletter: |IcSub| or |IcUns|

- Get to the :ref:`View page <user-guide-ui-components-view-pages>` of the list :  |IcView| 

  - You can also unsubscribe/subscribe customers to the newsletter with the button in the View page.

.. note::

    Editing the subscription list is only possible, if 
    :ref:`two-way synchronization <user-guide-magento-channel-integration-synchronization>` has been enabled. 


.. _user-guide-magento-entities-workflows:

Default Workflows with Magento Entities
---------------------------------------

To provide a consistent and customer-oriented approach, you can define a specific workflow within which the actions can be
performed for each shopping cart or order. The following two workflows are pre-implemented in OroCRM
for Magento-based shops:


*Abandoned Shopping Cart* Workflow
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The workflow is aimed at boosting sales from carts. Basically, once the managers sees a cart that has not been
converted into an order, the manager can:

1. Contact the customer. Multiple calls an/or emails can be made/sent.

2. Convert the cart into an Order or Abandon the cart

This way, the workflow allows converting the cart into an order without contacting the customer, but within the workflow
it is impossible to abandon the cart without getting in touch with the customer.

.. image:: ./img/magento_entities/cart_workflow_diagram.png

The workflow helps to improve customer-oriented communications and to increase the amount of actual orders. At the
same time, the managers can see all the information on the relevant items (no long search during the call), switch to
the customer and account info and even check if the customer has already been contacted.


*Order Follow Up* Workflow
^^^^^^^^^^^^^^^^^^^^^^^^^^

The workflow aims to keep track of the customer feedback on the purchase. For each order, the manager can:

1. Contact the customer by email. You can contact the customer by email only once.

2. If there is no response to the email, it is possible to contact the customer by phone.
   It is also possible to skip sending an email and start with a call.

3. Once a call has been logged, there are two options:

  - Record Feedback: the *Record Feedback* form will appear. Fill it out, and click :guilabel:`Submit` to save it in the
    system.

    There can be no more calls or emails to the customer related to this cart.

  - No Reply: if it has not been possible to get in touch with the customer, it is possible to make a note on the case
    (e.g. "an answering machine", "no parents at home, call back after six").

.. image:: ./img/magento_entities/order_followup_workflow_diagram.png

The workflow provides for consistent feedback collection and eliminates excessive calls, as each manager can see
the log of emails and call-attempts.


.. |WT02| replace:: Shopping Cart
.. _WT02: http://www.magentocommerce.com/magento-connect/customer-experience/shopping-cart.html

.. |IcView| image:: ./img/buttons/IcView.png
   :align: middle
   
.. |IcDelete| image:: ./img/buttons/IcDelete.png
   :align: middle

.. |IcEdit| image:: ./img/buttons/IcEdit.png
   :align: middle

.. |IcMove| image:: ./img/buttons/IcMove.png
   :align: middle

.. |IcSub| image:: ./img/buttons/IcSub.png
   :align: middle

.. |IcUns| image:: ./img/buttons/IcUns.png
   :align: middle
