Design/Behaviour Principles
===========================

1. Extensible, so both us and 3rd parties can easily add support of 3rd party extension (JomSocial, CB etc).

2. Work seamlessly with Joomla and all extensions we support: We define “maps” and then intercept local value changes and push the respective changes to IFS. We should support ALL value changes and not some (I.e: front-end but not back-end). When something mapped changes in IFS, it is the users responsibility to make an HTTP POST to JF which will then refresh all local data from IFS.

3. Core implementation provides vanilla Joomla integration. All other J extensions are supported by separate, purpose-built JF extensions that follow the same pattern: Map elements between the J extension and IFS, then upon value changes on either side, make the data push to the remote system.

4. Since intercepting all onBeforeSomeEvent events is not always guaranteed, we instead capture local mapped field values before any possible change can happen and after any possible change can happen. Then we compare them, if any change is observed we push all related data. All integration extensions deal with achieving those two requirements. We still intercept some onBeforeSomeEvent events in order to achieve the ‘before any change takes place’. Then we intercept the application termination and fetch the ‘after any changes can take place’. So our plugins are split into two groups:
 
 1. plg_[some-joomla-extension]_joomfuse: A plugin for the 3rd party J extension which provides:
  
  1. A way to map IFS fields to local-extension fields (e.g: The plg_cb_joomfuse extension holds the field maps between CB custom fields and IFS).
  
  2. Provide the mapped local values when requested from the JF core. The JF core will request these values twice per page-load to make the before/after-change comparison.
 
 2. plg_joomfuse_[some-joomla-extension]: A joomfuse plugin that is responsible for accepting IFS contact data and transforming/storing the given values to the appropriate extension format/location. This mechanism is utilized when importing/syncing data from InfusionSoft (e.g: an HTTP POST).

5. Key programmatic abstractions:
 
 1. The IFSContact objects are always available for a given J user, no matter whether the contact exists in IFS or not nor whether the Joomla/IFS user/contact map is present. JF will make sure that the contact is present and mapped upon accessing the contact object.
 
 2. We don’t normally make any direct API calls to IFS (with some exceptions). The programmer doesn’t need to worry about  how/when to make IFS API calls in order to implement a JF integration, all he needs to do is:
  
  1. Store the values in the local DB/extension when a POST comes from IFS
  
  2. Efficiently (we call this at least twice per pageload) provide the contact record values when JoomFuse request them. We do this because we don’t always 
