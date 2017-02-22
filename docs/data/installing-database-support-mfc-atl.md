---
title: "Instalar compatibilidad con bases de datos (MFC/ATL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL [C++], compatibilidad con bases de datos"
  - "acceso a datos [C++], configurar compatibilidad con bases de datos"
  - "bases de datos [C++], configurar compatibilidad con bases de datos"
  - "instalar compatibilidad con bases de datos"
ms.assetid: 3820ba96-4fb8-4405-83dd-bb3bc5998667
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Instalar compatibilidad con bases de datos (MFC/ATL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se ejecuta el programa de instalación de Visual C\+\+ .NET, los siguientes componentes de base de datos se instalan automáticamente:  
  
-   Todos los componentes OLE DB de ATL necesarios.  Para obtener más información, consulte [Instalar compatibilidad con bases de datos ATL](../data/installing-atl-database-support.md).  
  
-   Un conjunto de controladores ODBC con el administrador de controladores ODBC y el programa administrador ODBC.  Para obtener más información, consulte "Controladores ODBC instalados" y "Componentes del SDK de ODBC instalados" en [Instalar compatibilidad con bases de datos MFC](../data/installing-mfc-database-support.md).  
  
-   Componentes necesarios del kit de desarrollo de software \(SDK\) de DAO.  Esto incluye los archivos de ayuda, que no están integrados en esta documentación.  Sin embargo, si trabaja con DAO, necesitará instalar una versión de Jet compatible con su sistema operativo.  Para obtener más información, consulte "Componentes del SDK de DAO instalados" en [Instalar compatibilidad con bases de datos MFC](../data/installing-mfc-database-support.md).  
  
 Como parte de la instalación básica, el programa de instalación también instala Componentes de Microsoft Data Access \(MDAC\), que son necesarios para admitir la programación del acceso a datos en Visual C\+\+ .NET.  
  
 Visual C\+\+ .NET instala el SDK de MDAC 2.7.  Debería consultar el sitio web de Microsoft Universal Data Access en [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=121548](http://go.microsoft.com/fwlink/?LinkId=121548) para obtener más información acerca de las actualizaciones y las noticias sobre el SDK de MDAC.  
  
 Si redistribuye aplicaciones de acceso a datos, debe tener también el programa de redistribución de MDAC 2.7.  El SDK de MDAC 2.7 está diseñado para su utilización con el programa de redistribución de MDAC 2.7 \(Mdac\_typ.exe\) incluido en el directorio MDAC del CD\-ROM de requisitos previos de Visual Studio .NET.  También puede descargar Mdac\_typ.exe desde el vínculo de descarga del SDK de MDAC 2.7 mencionado anteriormente.  Para obtener más información acerca de la redistribución de componentes, consulte [Redistribuir controles](../data/ado-rdo/redistributing-controls.md).  
  
## Vea también  
 [Acceso a datos en ASP.NET \(Visual Studio\)](../Topic/Data%20Access%20in%20Visual%20C++.md)