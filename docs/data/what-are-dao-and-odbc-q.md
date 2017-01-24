---
title: "&#191;Qu&#233; son DAO y ODBC? | Microsoft Docs"
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
  - "DAO (objetos de acceso a datos), y ODBC"
  - "ODBC, acerca de ODBC"
ms.assetid: 22cc2f75-7ff6-47bc-ac56-56a40591104c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &#191;Qu&#233; son DAO y ODBC?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

DAO \(Data Access Objects\) y ODBC \(Open Database Connectivity\) son API que ofrecen la capacidad de programar aplicaciones independientes de cualquier sistema de administración de bases de datos \(DBMS\).  
  
 La tecnología DAO es conocida por los programadores de bases de datos que utilizan Microsoft Access Basic o Microsoft Visual Basic.  DAO utiliza el motor de bases de datos Microsoft Jet para proporcionar un conjunto de objetos de acceso a datos: objetos de base de datos, objetos de definición de tabla, objetos de definición de consulta y objetos de conjunto de registros, entre otros.  DAO proporciona el mejor rendimiento con archivos .mdb como los que crea Microsoft Access, pero también puede tener acceso a orígenes de datos ODBC a través de DAO y del motor de bases de datos Microsoft Jet.  
  
 ODBC proporciona una API que implementan los distintos proveedores de bases de datos mediante controladores ODBC específicos para un DBMS determinado.  Los programas utilizan esta API para llamar al Administrador de controladores ODBC, que pasa las llamadas al controlador apropiado.  A su vez, el controlador utiliza SQL para interactuar con el DBMS.  
  
> [!NOTE]
>  ODBC es una parte importante de la Arquitectura de servicios abiertos de Microsoft \(WOSA\).  DAO está optimizado entorno al motor de bases de datos Microsoft Jet, pero aún se puede obtener acceso a ODBC y a otros orígenes de datos externos con ese motor, y las distintas clases de la API de ODBC y de MFC basadas en él también están disponibles y desempeñan su rol en la selección de herramientas de base de datos.  
  
## Vea también  
 [Preguntas más frecuentes sobre Data Access](../data/data-access-frequently-asked-questions-mfc-data-access.md)