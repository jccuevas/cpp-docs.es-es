---
title: "Instalar compatibilidad con bases de datos MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO [C++], instalar componentes"
  - "bases de datos [C++], configurar compatibilidad con bases de datos"
  - "bases de datos [C++], MFC"
  - "instalar DAO"
  - "instalar ODBC"
  - "componentes ODBC [C++], instalar"
  - "controladores ODBC [C++], instalar"
ms.assetid: a6c2fc84-9e0e-4f39-a464-0bcbc415b946
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Instalar compatibilidad con bases de datos MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

##  <a name="_core_odbc_drivers_installed"></a> Controladores ODBC instalados  
 El programa de instalación instala los siguientes controladores ODBC:  
  
-   Controlador de Microsoft Access  
  
-   Controlador de Microsoft dBASE  
  
-   Controlador de Microsoft Excel  
  
-   Controlador de Microsoft FoxPro  
  
-   Controlador de Microsoft Visual FoxPro  
  
-   Controlador ODBC para Oracle de Microsoft  
  
-   Controlador de Microsoft Paradox  
  
-   Controlador de texto de Microsoft  
  
-   Controlador de Microsoft SQL Server  
  
 Para obtener información sobre cómo obtener controladores adicionales y consultar una lista de los controladores ODBC incluidos en esta versión de C\+\+, vea [Lista de controladores ODBC](../data/odbc/odbc-driver-list.md).  
  
##  <a name="_core_odbc_sdk_components_installed"></a> Componentes instalados del SDK de ODBC  
 Visual C\+\+ incluye muchos otros componentes clave de ODBC, como los archivos de encabezado requeridos, bibliotecas, archivos DLL y herramientas.  Entre ellos se encuentran la aplicación Administrador ODBC del Panel de control, que se utiliza para configurar los orígenes de datos ODBC, y el administrador de controladores ODBC.  También se incluyen controladores ODBC para muchos DBMS conocidos, como se muestra en [Controladores ODBC instalados](#_core_odbc_drivers_installed).  
  
 El SDK de ODBC proporciona información adicional y herramientas para programar y probar controladores ODBC.  Observe que, a partir de Visual C\+\+ .NET, el SDK de ODBC ya no se incluye en el disco de instalación de Visual C\+\+ .NET, sino que está disponible como parte de [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)], que se instala con los requisitos previos de Visual Studio .NET.  
  
##  <a name="_core_dao_sdk_components_installed"></a> Componentes instalados del SDK de DAO  
  
> [!NOTE]
>  Microsoft recomienda el uso de OLE DB u ODBC para nuevos proyectos.  Sólo se debe utilizar DAO para mantener las aplicaciones existentes.  
  
 De forma predeterminada se instalan los siguientes componentes del SDK de DAO:  
  
-   Microsoft Jet \(4.0 SP3\)  
  
-   Microsoft Jet \(3.x MDB\)  
  
-   Microsoft Jet \(1.x, 2.x\)  
  
-   Todos los formatos de base de datos que aparecen en la lista [Bases de datos a las que se puede obtener acceso con DAO y ODBC](../data/what-data-sources-can-i-access-with-dao-and-odbc-q.md)  
  
 En Visual C\+\+ .NET, el SDK de DAO se incluye en los requisitos previos de Visual Studio .NET.  Ejecute \\Jet\\Jetsetup.exe.  
  
> [!NOTE]
>  Microsoft recomienda utilizar Jet 4.0 Service Pack 3 \(versión 2927.04\) o posterior.  Jet 4.0 Service Pack 3 se suministra con Windows 2000 y Windows Me.  Con esta versión de Jet, se reduce el número de versiones que se deben probar en la aplicación.  Es posible que Windows XP suministre otra versión de Jet.  Vea la "Nota sobre la redistribución de componentes DAO" en [Redistribuir controles](../data/ado-rdo/redistributing-controls.md).  
  
 Si desea instalar otros componentes del SDK de DAO, como las clases de C\+\+, los archivos de ejemplo o la versión de Windows Help del archivo de ayuda de DAO, instale el SDK de DAO desde el CD\-ROM de Visual C\+\+ 6.0.  
  
 Para las actualizaciones y novedades existentes sobre OLE DB, vea el sitio Web Universal data access en [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=121548](http://go.microsoft.com/fwlink/?LinkId=121548).  
  
## Vea también  
 [Programación del acceso a datos \(MFC\/ATL\)](../data/data-access-programming-mfc-atl.md)