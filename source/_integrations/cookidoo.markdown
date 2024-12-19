---
title: Cookidoo
description: Instructions on how to integrate the Cookidoo todo list with Home Assistant.
ha_category:
  - To-do list
ha_iot_class: Cloud Polling
ha_release: 2025.1
ha_config_flow: true
ha_codeowners:
  - '@miaucl'
ha_domain: cookidoo
ha_integration_type: service
ha_platforms:
  - todo
related:
  - docs: /integrations/todo
    title: To-do list integration documentation
  - docs: /integrations/#to-do-list
    title: List of to-do list integrations
  - docs: /dashboards/todo-list/
    title: To-do list card
  - url: https://cookidoo.international/
    title: Cookidoo the official Thermomix recipe platform
  - url: https://www.vorwerk.com/
    title: Vorwerk GmbH
---

The **Cookidoo** {% term integration %} allows you to interact with your shopping lists of [Cookidoo the official Thermomix recipe platform](https://cookidoo.international/) within Home Assistant.

{% configuration_basic %}
Email:
    description: "Enter the email address associated with your Cookidoo."
Password:
    description: "Enter the password for your Cookidoo account."
Localization:
    description: "Select the language and country for your Cookidoo account (e.g., English - United States)."
{% endconfiguration_basic %}

{% include integrations/config_flow.md %}

## To-do lists

This integration provides two non-sortable to-do lists:

1. **Shopping list**
   - Contains ingredients from recipes
   - Items can only be `checked`
   - Items cannot be `created`, `deleted`, or `renamed`

2. **Additional purchases**
   - Contains user-added items to purchase
   - Items can be `created`, `deleted`, and `updated`
   - Items do not have a `description` field

For example, if you add a pasta recipe, ingredients like "500g pasta" and "2 tomatoes" will appear in your "Shopping list". You can check these items off as you shop, but you cannot modify the label.

In contrast, in your "Additional purchases" list, you can freely add items like "Kitchen towels" or "Dish soap", and modify or remove them as needed.

## Buttons

The "clear shopping list and additional purchase" button allows to _reset_ both shopping lists, mirroring the same functionality available in the Cookidoo app.

## Known Limitations

{% important %}
As Cookidoo cannot share shopping lists between accounts and everybody interacting with it uses the same credentials, make sure you protect your credentials accordingly. All users of your Home Assistant instance will have access to the same Cookidoo account.
{% endimportant %}

The Home Assistant to-do list interface allows both renaming items and changing their state. However, for the "Shopping list", only state changes (checking/unchecking items) are supported. Any attempts to rename items will not be saved.

## Data updates

The Cookidoo integration fetches data from the device every 90 seconds by default.

## Remove integration

This integration follows standard integration removal, no extra steps are required.

{% include integrations/remove_device_service.md %}
