---
title: "&#191;Se puede utilizar DDL y DML? | Microsoft Docs"
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
  - "Lenguaje de manipulación de datos en ODBC de MFC [C++]"
  - "bases de datos [C++], obtener acceso en DAO"
  - "bases de datos [C++], acceso con DDL"
  - "bases de datos [C++], acceso con DML"
  - "DDL [C++], compatibilidad con MFC"
  - "DML [C++]"
  - "DML [C++], ODBC de MFC"
ms.assetid: 07f96d81-78d4-4bec-9138-b15d68fd5ce0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &#191;Se puede utilizar DDL y DML?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las clases DAO de MFC admiten dos tipos de acceso a las bases de datos:  
  
-   **Lenguaje de definición de datos \(DDL\)** Permite crear y eliminar bases de datos, crear y eliminar tablas, definir campos de tabla e índices, y realizar otras acciones que afectan a la estructura de la base de datos.  
  
-   **Lenguaje de manipulación de datos \(DML\)** Permite ejecutar consultas, agregar, eliminar y editar registros, así como manipular de otras maneras el contenido de la base de datos.  
  
 Las clases ODBC de MFC sólo son compatibles con DML, pero es posible llamar directamente a las funciones de la API de ODBC para realizar tareas de DDL.  
  
## Vea también  
 [Preguntas más frecuentes sobre Data Access](../data/data-access-frequently-asked-questions-mfc-data-access.md)