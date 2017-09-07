---
title: Database Page
toc: false
feedback: false
---

The Databases page of the Admin UI provides details of the databases configured, the tables in each database, and the grants assigned to each user.

<div id="toc"></div>

## Tables View  

To view the tables view, [access the Admin UI](explore-the-admin-ui.html#access-the-admin-ui) and select **Databases** from the left-hand navigation bar. The **Tables** view is displayed.
<img src="{{ 'images/admin_ui_database_tables_view.png' | relative_url }}" alt="CockroachDB Admin UI Database Tables View" style="border:1px solid #eee;max-width:100%" />


## Grants View
To view the Grants view, [access the Admin UI](explore-the-admin-ui.html#access-the-admin-ui) and select **Databases** from the left-hand navigation bar. Then on the Database page, select **Grants** from the View drop-down menu.
The Grants view displays the privileges granted to users for each database. See [Grants](grant.html) for more information.

<img src="{{ 'images/admin_ui_database_grants_view.png' | relative_url }}" alt="CockroachDB Admin UI Database Grants View" style="border:1px solid #eee;max-width:100%" />