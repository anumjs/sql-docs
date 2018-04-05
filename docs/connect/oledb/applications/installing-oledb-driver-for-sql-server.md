---
title: "Installing OLE DB Driver for SQL Server | Microsoft Docs"
description: "Installing and uninstalling OLE DB Driver for SQL Server"
ms.custom: ""
ms.date: "03/26/2018"
ms.prod: "sql-non-specified"
ms.prod_service: "database-engine, sql-database, sql-data-warehouse, pdw"
ms.service: ""
ms.component: "oledb|applications"
ms.reviewer: ""
ms.suite: "sql"
ms.technology:
  - "drivers"
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords:
  - "OLE DB Driver for SQL Server, uninstalling"
  - "MSOLEDBSQL, installing"
  - "MSOLEDBSQL, uninstalling"
  - "Setup [OLE DB Driver for SQL Server]"
  - "uninstalling OLE DB Driver for SQL Server"
  - "data access [OLE DB Driver for SQL Server], uninstalling OLE DB Driver for SQL Server"
  - "installing OLE DB Driver for SQL Server"
  - "OLE DB Driver for SQL Server, installing"
  - "data access [OLE DB Driver for SQL Server], installing OLE DB Driver for SQL Server"
  - "removing OLE DB Driver for SQL Server"
author: "pmasl"
ms.author: "Pedro.Lopes"
manager: "jhubbard"
ms.workload: "Active"
---
# Installing OLE DB Driver for SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

To install the OLE DB Driver for SQL Server you need msoledbsql.msi installer.
Run the installer and make your preferred selections. The OLE DB Driver for SQL Server can be installed side-by-side with earlier versions of Microsoft OLE DB providers.

To download the most recent version of the OLE DB Driver for SQL Server go to [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=56730).

The OLE DB Driver for SQL Server files (msoledbsql.dll, msoledbsqlr.rll) are installed to the following location:  

`%SYSTEMROOT%\system32\`  

> [!NOTE]  
> All appropriate registry settings for the OLE DB Driver for SQL Server are made as part of the installation process.  

The OLE DB Driver for SQL Server header and library files (msoledbsql.h and msoledbsql.lib) are installed in the follow location:  

`%PROGRAMFILES%\Microsoft SQL Server\Client SDK\OLEDB\180\SDK`  

You can distribute OLE DB Driver for SQL Server through msoledbsql.msi. You might have to install OLE DB Driver for SQL Server when you deploy an application. One way to install multiple packages in what seems to the user to be a single installation is to use chainer and bootstrapper technology. For more information, see [Authoring a Custom Bootstrapper Package for Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=115667) and [Adding Custom Prerequisites](http://go.microsoft.com/fwlink/?LinkId=115668).  
  
The x64 msoledbsql.msi also installs the 32-bit version of OLE DB Driver for SQL Server. If your application targets a platform other than the one it was developed on, you can download versions of msoledbsql.msi for x64 and x86.

When you invoke msoledbsql.msi, only the client components are installed by default. The client components are are files that support running an application that was developed using OLE DB Driver for SQL Server. To also install the SDK components, specify `ADDLOCAL=All` on the command line. For example:  

`msiexec /i msoledbsql.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  

## Silent Install  
 If you use the /passive, /qn, /qb, or /qr option with msiexec, you must also specify IACCEPTMSOLEDBSQLLICENSETERMS=YES, to explicitly indicate that you accept the terms of the end user license. This option must be specified in all capital letters.  

## Uninstalling OLE DB Driver for SQL Server  
Because applications such as [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] server and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tools depend on OLE DB Driver for SQL Server, it is important not to uninstall OLE DB Driver for SQL Server until all dependent applications are uninstalled. To provide users with a warning that your application depends on OLE DB Driver for SQL Server, use the APPGUID install option in your MSI, as follows:  

 `msiexec /i msoledbsql.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  

The value passed to APPGUID is your specific product code. A product code must be created when using Microsoft Installer to bundle your application setup program.  

## See Also  
 [Building Applications with OLE DB Driver for SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   