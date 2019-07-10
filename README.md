# sitecore-Public-Access-Enable-From-IIS
Sitecore 9.1.0 Public Site Access From IIS

# Steps
  - 01. edit site bindings
  - 02. edit identity site bindings
  - 03. edit siteconfiguration
  - 04. edit Sitecore.Owin.Authentication.IdentityServer config
  - 05. add firewall inbound rules

# Assumptions
  - sitename test.x.local
  - identity site name test.x.local.identity
  - public site port 8090
  - public site identity port 8091

## 01. edit site bindings
  - goto iis in the site list find your site name in this case test.x.local.identity
  - right click to get "edit bindings" options and add one there
  - keep it http and for all unassigned ip with port 8090(or any other port you want)
  
## 02. edit identity site bindings
  - goto iis in the site list find your site name in this case test.x.local
  - right click to get "edit bindings" options and add one there
  - keep it https and for all unassigned ip with port 8091(or any other port you want)
  - also remember to add certificate as like default bindings of the 80 port

## 03. edit siteconfiguration
  - find the site configuration [If you have any then]
  - if the host is specified then please remove it and make it empty string

## 04. edit Sitecore.Owin.Authentication.IdentityServer config
  - in sitecore app_configurations find the Website\App_Config\Sitecore\Owin.Authentication.IdentityServer folder\Sitecore.Owin.Authentication.IdentityServer.config
  - find **<sc.variable name="identityServerAuthority" value="https://test.x.local.identity" />** and replace it with your_pc_ip:8091
  
## 05. add firewall inbound rules
  - from firewall inbound rules add two ports 8090 and 8091


This is all you are all set to see your site in the exposed network or if you have a public ip that will help you to make your site publicly available.
