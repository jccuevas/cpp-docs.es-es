---
title: "Origen de datos: Determinar el esquema del origen de datos (ODBC) | Microsoft Docs"
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
  - "orígenes de datos [C++], determinar esquema"
  - "orígenes de datos ODBC [C++], esquema"
  - "esquemas [C++], orígenes de datos"
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Origen de datos: Determinar el esquema del origen de datos (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 Para configurar miembros de datos en los objetos `CRecordset`, es necesario conocer el esquema del origen de datos con el que se está estableciendo conexión.  La determinación del esquema de un origen de datos supone obtener una lista de las tablas del origen de datos, una lista de las columnas de cada tabla, el tipo de datos de cada columna y la existencia de índices.  
  
## Vea también  
 [Origen de datos \(ODBC\)](../../data/odbc/data-source-odbc.md)   
 [Origen de datos: Administrar conexiones \(ODBC\)](../../data/odbc/data-source-managing-connections-odbc.md)