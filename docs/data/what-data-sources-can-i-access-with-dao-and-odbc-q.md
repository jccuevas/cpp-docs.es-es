---
title: "Or&#237;genes de datos a los que se puede obtener acceso con DAO y ODBC | Microsoft Docs"
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
  - "DAO [C++], tipos de orígenes de datos"
  - "datos [C++], DAO"
  - "datos [C++], ODBC"
  - "acceso a datos [C++], DAO"
  - "orígenes de datos [C++], accesible mediante DAO y ODBC"
  - "bases de datos [C++], obtener acceso en DAO"
  - "FAQ [C++], bases de datos accesibles"
  - "ODBC [C++], orígenes de datos accesibles"
  - "orígenes de datos ODBC [C++], accesibles"
ms.assetid: c88abb45-526a-467a-a01b-d9396bd63236
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Or&#237;genes de datos a los que se puede obtener acceso con DAO y ODBC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los dos conjuntos de clases MFC permiten tener acceso a una gran variedad de orígenes de datos y programar aplicaciones independientes del origen de datos.  
  
##  <a name="_core_databases_you_can_access_with_dao"></a> Bases de datos a las que puede obtener acceso con DAO  
 Utilizando DAO y las clases DAO de MFC puede obtener acceso a los siguientes orígenes de datos:  
  
-   Bases de datos que utilicen el motor de bases de datos Microsoft Jet, creadas con Microsoft Access o Microsoft Visual Basic, con las versiones 1.x, 2.x y 3.0 del motor de bases de datos.  
  
-   Bases de datos ISAM instalables, incluidas:  
  
    -   dBASE III, dBASE IV y dBASE 5.0  
  
    -   Paradox, versiones 3.x, 4.x y 5.x  
  
-   Bases de datos ODBC \(Open Database Connectivity\), incluidas Microsoft SQL Server, SYBASE SQL Server y ORACLE Server, entre otras.  Para tener acceso a una base de datos ODBC, debe tener un controlador ODBC apropiado para la base de datos a la que desea tener acceso.  Vea [Lista de controladores ODBC](../data/odbc/odbc-driver-list.md) para obtener una lista de los controladores ODBC incluidos en esta versión de Visual C\+\+ e información sobre cómo obtener controladores adicionales.  
  
-   Hojas de cálculo de Microsoft Excel, versiones 3.0, 4.0, 5.0 y 7.0.  
  
-   Hojas de cálculo de Lotus WKS, WK1, WK3 y WK4.  
  
-   Archivos de texto.  
  
 DAO se utiliza mejor con bases de datos que puede leer el motor de base de datos Microsoft Jet, que incluyen todas las anteriores excepto los orígenes de datos ODBC.  El mejor rendimiento se consigue con las bases de datos de Microsoft Jet \(.mdb\).  Asociar tablas externas \(especialmente en orígenes de datos ODBC\) a una base de datos .mdb es más eficaz que abrir la base de datos externa directamente mediante las clases DAO de MFC sin asociar.  
  
##  <a name="_core_databases_you_can_access_with_odbc"></a> Bases de datos a las que puede obtener acceso con ODBC  
 Utilizando ODBC y las clases ODBC de MFC, puede obtener acceso a cualquier origen de datos, local o remoto, para el que el usuario de la aplicación tenga un controlador ODBC. Hay controladores ODBC de 16, 32 y 64 bits para una gran variedad de orígenes de datos.  Si está trabajando con una base de datos de Microsoft Jet \(.mdb\), es más eficaz utilizar las clases DAO que el controlador ODBC de Microsoft Access.  
  
## Vea también  
 [Preguntas más frecuentes sobre Data Access](../data/data-access-frequently-asked-questions-mfc-data-access.md)