# How To Decide on an Entity ID ?

**How To create or decide on an Entity ID value in the onboarding request ?**

* An **Entity ID** is a unique identifier that represents a specific entity such as an FIU (Financial Information User), AA (Account Aggregator), or FIP (Financial Information Provider). It should follow a clear, readable naming convention that helps identify the entity.
* Best practice for naming Entity IDs:\
  Use a suffix-based naming convention like:
  * **For FIUs: XYZ\_FIU**
  * **For AAs: ABC\_AA**
  * **For FIPs: AXBYCZ\_FIP**
* For Lower environments you can even add the environment name as well&#x20;
  * **For FIU : XYZ\_UAT\_FIU or XYX\_SANDBOX\_FIU**
  * **For AA : ABC\_UAT\_AA or ABC\_SANDBOX\_AA**
  * **For FIP : AXBYCZ\_UAT\_FIP or AXBYCZ\_SANDBOX\_FIP**
* Ensure that the Entity ID is a unique and easily recognisable name of the organisation that is getting onboarded. It can include letters, numbers, or symbols, but a simple and meaningful string is recommended.
* **Do note,** the above examples and recommendations **use an underscore** ( \_ ) as the **delimiter**. You **can also use hyphens** ( - ) if preferred.
