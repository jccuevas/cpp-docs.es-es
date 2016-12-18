---
title: "Origen de datos (ODBC) | Microsoft Docs"
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
  - "CDatabase (clase), conexiones a orígenes de datos"
  - "configurar orígenes de datos ODBC"
  - "orígenes de datos ODBC"
  - "orígenes de datos ODBC, configurar"
  - "orígenes de datos ODBC, representados por CDatabase"
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Origen de datos (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 En términos de bases de datos, un origen de datos comprende un conjunto de datos específico, la información requerida para tener acceso a esos datos y la ubicación del origen de datos, que se puede describir por medio de un nombre de origen de datos.  Para trabajar con la clase [CDatabase](../../mfc/reference/cdatabase-class.md), el origen de datos debe ser uno de los que se han configurado mediante el Administrador de ODBC.  Ejemplos de orígenes de datos son una base de datos remota que funciona en Microsoft SQL Server a través de una red o un archivo de Microsoft Access de un directorio local.  Desde la aplicación se puede tener acceso a cualquier origen de datos para el que se tenga un controlador ODBC.  
  
 Se pueden tener uno o varios orígenes de datos activos en la aplicación al mismo tiempo, cada uno de ellos representado por un objeto `CDatabase`.  También se pueden tener varias conexiones simultáneas a cualquier origen de datos.  La conexión se puede establecer tanto con orígenes de datos remotos como locales, dependiendo de los controladores que estén instalados y de las capacidades de los controladores ODBC.  Para obtener más información sobre los orígenes de datos y el Administrador de ODBC, vea [ODBC](../../data/odbc/odbc-basics.md) y [Administrador de ODBC](../../data/odbc/odbc-administrator.md).  
  
 Los siguientes temas explican con más detalle los orígenes de datos:  
  
-   [Origen de datos: Administrar conexiones \(ODBC\)](../../data/odbc/data-source-managing-connections-odbc.md)  
  
-   [Origen de datos: Determinar el esquema del origen de datos \(ODBC\)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)  
  
## Vea también  
 [Conectividad abierta de bases de datos \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)