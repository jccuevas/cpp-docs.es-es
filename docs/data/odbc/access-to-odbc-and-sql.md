---
title: "Acceso a ODBC y SQL | Microsoft Docs"
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
  - "llamadas API [C++], llamar a DAO u ODBC directamente"
  - "ODBC [C++], funciones API"
  - "funciones de la API de ODBC [C++]"
  - "funciones de la API de ODBC [C++], llamar desde MFC"
  - "SQL [C++], llamar a funciones de la API de ODBC"
  - "API de Windows [C++], llamar desde MFC"
ms.assetid: 5613d7dc-00b7-4646-99ae-1116c05c52b4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Acceso a ODBC y SQL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La biblioteca MFC \(Microsoft Foundation Class\) encapsula muchas llamadas API de Windows y permite seguir llamando directamente a cualquier función de la API de Windows.  Las clases de base de datos proporcionan la misma flexibilidad en lo que respecta a la API de ODBC.  Aunque las clases de base de datos evitan buena parte de la complejidad de ODBC, se puede llamar directamente a funciones de la API ODCB desde cualquier lugar del programa.  
  
 Del mismo modo, las clases de base de datos evitan tener que trabajar mucho con [SQL](../../data/odbc/sql.md), pero se puede usar SQL directamente si se desea.  Se pueden personalizar objetos de conjunto de registros pasando una instrucción SQL personalizada \(o estableciendo partes de la instrucción predeterminada\) al abrir el conjunto de registros.  También se pueden realizar directamente llamadas a SQL utilizando la función miembro [ExecuteSQL](../Topic/CDatabase::ExecuteSQL.md) de clase [CDatabase](../../mfc/reference/cdatabase-class.md).  
  
 Para obtener más información, vea [ODBC: Llamar directamente a funciones de la API de ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) y [SQL: Realizar llamadas directas a SQL \(ODBC\)](../../data/odbc/sql-making-direct-sql-calls-odbc.md).  
  
## Vea también  
 [ODBC y MFC](../../data/odbc/odbc-and-mfc.md)