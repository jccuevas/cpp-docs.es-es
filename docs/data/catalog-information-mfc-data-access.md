---
title: "Informaci&#243;n del cat&#225;logo (acceso a datos MFC) | Microsoft Docs"
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
  - "base de datos con información de catálogo [C++]"
  - "DAO [C++], información de catálogo"
  - "bases de datos [C++], base de datos con información de catálogo"
  - "ODBC [C++], información de catálogo"
  - "tablas [C++]"
  - "tablas [C++], información de catálogo"
ms.assetid: c184e80f-ff17-409f-9df8-05275080bb8d
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Informaci&#243;n del cat&#225;logo (acceso a datos MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La información sobre las tablas de un origen de datos puede incluir los nombres de las tablas y las columnas, los privilegios de tabla, los nombres de claves principales y externas, información sobre consultas predefinidas o procedimientos almacenados, información sobre los índices de tablas y estadísticas sobre las tablas.  
  
 Para obtener más información, consulte [Origen de datos: determinar el esquema del origen de datos \(ODBC\)](../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md).  
  
> [!NOTE]
>  En las clases DAO de MFC, puede obtener información del catálogo de la siguiente manera: Use [CDaoDatabase::GetTableDefCount](../Topic/CDaoDatabase::GetTableDefCount.md) y [CDaoDatabase::GetTableDefInfo](../Topic/CDaoDatabase::GetTableDefInfo.md) para enumerar las tablas de la base de datos y obtener información sobre cada tabla en una estructura [CDaoTableDefInfo](../mfc/reference/cdaotabledefinfo-structure.md).  
  
## Vea también  
 [Programación del acceso a datos \(MFC\/ATL\)](../data/data-access-programming-mfc-atl.md)