# ServiceNow Base PDI Setup

This repository contains a Batch Update Set containing some settings and tools that assist in quickly prepare a freshly deployed ServiceNow Personal Developer Instance (PDI).

# Installation

## Quick Overview
1. Import, preview and commit the "Base PDI Setup" Update Set
1. Install plugins with the "Install Base PDI Plugins" Fix Script

## Details

### Import, preview and commit Batch Update Set
1. Go to: System Update Sets -> Retrieved Update Sets
1. Click the "Import Update Set from XML" Related Link
1. Choose the "Base PDI Setup.xml" file
1. Click "Upload"
1. Find and open the "Base PDI Setup" Update Set
1. Preview the Update Set
1. Commit the Update Set
1. Log out and back in to activate the new admin user preferences

### Install desired plugins:
1. Go to: System Definition -> Fix Scripts
1. Find and open Fix Script "Install Base PDI Plugins"
1. Optionally add or remove any plugins to be installed by adding or removing "plugins.push(..)" lines
1. Save the Fix Script if you made any changes in the previous step
1. Run the fix Script in foreground. It does not need to be run in background since it finishes instantly.
1. If you want to follow the installation progress, copy and open the URLs displayed in the message popup (or progress worker output if the script was run in background)
1. Plugin activation is finished when all plugins have reached State=Active
1. Progress can also be monitored by refreshing the System Diagnostics -> Upgrade History list
(Total installation time has been observed to be somewhere between 30-40 minutes on a fresh PDI)

### Install plugin demo data:
The Fix Script does not install plugin demo data so if demo data is desired it needs to be installed separately for the relevant plugins:
1. Go to System Definition -> Plugins
1. Find the relevant plugin (example: PPM Standard / com.snc.financial_planning_pmo)
1. Select "Repair" from the three-dot menu
1. Check "Load demo data" as true and click Repair


# What's included in the package?

The Batch Update Set provides the following settings and features:

* A custom Favicon with "PDI" text over the ServiceNow logo
* Default timezone: GMT
* Browser tab title: "MY PDI"
* Fix script that can be used to install some additional plugins
* The following user preferences for the "admin" user:
    * Show update set picker in header
    * Show 100 rows per page
    * Show domain picker in header
    * Show application picker in header
* UI Action "Find Record References" from SN Guru / servicenowguru.com
* Following Code Search Tables added according to SN Utils (v 5.1.0.5) recommendations:
    * sys_ws_operation, sys_web_service, sys_variable_value, sys_ui_list_control, sys_ui_context_menu, sys_transform_entry, sys_script_fix, sys_script_email, sys_properties, sys_filter_option_dynamic, sys_dictionary_override, sys_dictionary, sys_app_quota, sp_widget, sp_search_source, sp_angular_provider, sc_cat_item_producer, metric_definition
* Update set from Share: [Add to Update Set Utility v7.1](https://developer.servicenow.com/connect.do#!/share/contents/9824957_add_to_update_set_utility?v=7.1&t=PRODUCT_DETAILS) (as a child update set)
* Update set from Share: [Xplore: Developer Toolkit 4.8.1](https://developer.servicenow.com/connect.do#!/share/contents/9650888_xplore_developer_toolkit?v=4.8&t=PRODUCT_DETAILS) (as a child update set)


# Future improvement ideas

Some interesting settings and things in the following Community post series:
https://community.servicenow.com/community?id=community_blog&sys_id=97d47697dbf09490feb1a851ca9619b2
