## For reference

* http://technet.microsoft.com/en-us/library/dn280950.aspx
* http://technet.microsoft.com/en-us/library/dn636121.aspx

## Customizing the SAML login screen

Copy the current directory to `c:\adfs_theme`

Copy default theme to a custom theme

    New-AdfsWebTheme -Name custom -SourceName default

Activate the custom theme

    Set-AdfsWebConfig -ActiveThemeName custom

Set company name

    Set-AdfsGlobalWebContent –CompanyName "Biola University"

Set logo and background

    Set-AdfsWebTheme -TargetName custom -Illustration @{path="c:\adfs_theme\illustration.jpg"}
    Set-AdfsWebTheme -TargetName custom -Logo @{path="c:\adfs_theme\logo.png"}

Apply custom stylesheet

    Set-AdfsWebTheme –TargetName custom –StyleSheet @{path=”c:\adfs_theme\style.css”}

Apply custom javascript

    Set-AdfsWebTheme -TargetName custom -AdditionalFileResource @{Uri="/adfs/portal/script/onload.js";path="c:\adfs_theme\onload.js"}

Add Home Link

    Set-AdfsGlobalWebContent -HomeLink http://www.biola.edu/ -HomeLinkText Home

Add Helpdesk link

    Set-AdfsGlobalWebContent -HelpDeskLink http://offices1.biola.edu/it/contact/ -HelpDeskLinkText Help

Add Privacy link

    Set-AdfsGlobalWebContent -PrivacyLink http://www.biola.edu/privacy/ -PrivacyLinkText Privacy

Add custom error messages *(I'm not sure what these should actually say, the default messages might be fine for now)*

    Set-AdfsGlobalWebContent -ErrorPageDescriptionText "An error occurred"
    Set-AdfsGlobalWebContent -ErrorPageGenericErrorMessage "An error occurred. Contact the IT helpdesk for more information."
    Set-AdfsGlobalWebContent -ErrorPageAuthorizationErrorMessage "You have received an Authorization error. Contact the IT helpdesk for assistance."
    Set-AdfsGlobalWebContent -ErrorPageDeviceAuthenticationErrorMessage "Your device is not authorized. Contact the IT helpdesk for assistance."
    Set-AdfsGlobalWebContent -ErrorPageSupportEmail  "it.helpdesk@biola.edu"

## Optional steps
*(these don't need to be run, they are just here for reference)*

Export custom theme

    Export-AdfsWebTheme -Name custom -Directory c:\adfs_theme

Sign in page description (not needed)

    Set-AdfsGlobalWebContent -SignInPageDescriptionText "<p>Sign-in to Contoso requires device registration. Click <A href='http://fs1.contoso.com/deviceregistration/'>here</A> for more information.</p>"

