---
title: "Esquema (acceso a datos MFC) | Microsoft Docs"
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
  - "esquema de base de datos [C++]"
  - "esquema de base de datos [C++], acerca de los esquemas de bases de datos"
  - "bases de datos [C++], esquema"
  - "esquemas [C++], base de datos"
  - "estructuras [C++]"
  - "estructuras [C++], base de datos"
ms.assetid: 7d17e35f-1ccf-4853-b915-5b8c7a45b9ee
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Esquema (acceso a datos MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un esquema de base de datos describe la estructura actual de las tablas y vistas de base de datos en la base de datos.  En general, el código generado por el asistente supone que el esquema de la tabla o tablas a que accede un conjunto de registros no va a cambiar, pero las clases de base de datos pueden tratar algunos cambios de esquema, como agregar, reordenar o eliminar columnas sin enlazar.  Si una tabla cambia, debe actualizar manualmente el conjunto de registros de la tabla y, a continuación, volver a compilar la aplicación.  
  
 También puede complementar el código generado por el asistente para que actúe en caso de que una base de datos tenga un esquema que no se conoce por completo en el momento de la compilación.  Para obtener más información, consulte [Conjunto de registros: Enlazar dinámicamente columnas de datos \(ODBC\)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
## Vea también  
 [Programación del acceso a datos \(MFC\/ATL\)](../data/data-access-programming-mfc-atl.md)   
 [SQL](../data/odbc/sql.md)   
 [Conjunto de registros \(ODBC\)](../data/odbc/recordset-odbc.md)