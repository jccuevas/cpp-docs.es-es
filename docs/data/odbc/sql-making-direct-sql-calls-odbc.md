---
title: "SQL: Realizar llamadas directas a SQL (ODBC) | Microsoft Docs"
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
  - "llamadas directas a SQL desde ODBC"
  - "ODBC, llamadas SQL"
  - "llamadas SQL"
  - "SQL, llamar directamente desde ODBC"
  - "SQL, llamadas directas desde ODBC"
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SQL: Realizar llamadas directas a SQL (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este tema se explica:  
  
-   Cuándo utilizar llamadas directas a SQL.  
  
-   [Cómo realizar llamadas directas SQL a un origen de datos](#_core_making_direct_sql_function_calls).  
  
> [!NOTE]
>  Esta información es aplicable a las clases ODBC de MFC.  Si trabaja con las clases DAO de MFC, vea el tema "Comparación entre SQL del motor de bases de datos Microsoft Jet y SQL ANSI" en la Ayuda de DAO.  
  
##  <a name="_core_when_to_call_sql_directly"></a> Cuándo llamar a SQL directamente  
 Para crear nuevas tablas, quitar \(eliminar\) tablas, modificar las tablas existentes, crear índices y realizar otras funciones SQL que cambien el esquema del [Origen de datos \(ODBC\)](../../data/odbc/data-source-odbc.md), se debe enviar una instrucción SQL directamente al origen de datos mediante el Lenguaje de definición de base de datos \(DDL\).  Al usar un asistente para crear un conjunto de registros de una tabla \(en tiempo de diseño\), se puede elegir qué columnas de la tabla quedarán representadas en el conjunto de registros.  No se incluyen las columnas que el programador u otro usuario del origen de datos agregan posteriormente a la tabla, una vez compilado el programa.  Las clases de base de datos no son directamente compatibles con DDL, pero se puede escribir código para enlazar una nueva columna con el conjunto de registros dinámicamente, en tiempo de ejecución.  Para obtener más información sobre cómo hacer este enlace, vea [Conjunto de registros: Enlazar dinámicamente columnas de datos \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
 Se puede utilizar el propio DBMS para modificar el esquema u otra herramienta que permita realizar funciones DDL.  También se pueden usar llamadas de funciones ODBC para enviar instrucciones SQL, como por ejemplo llamar a una consulta predefinida \(procedimiento almacenado\) que no devuelve ningún registro.  
  
##  <a name="_core_making_direct_sql_function_calls"></a> Realizar llamadas de funciones SQL directas  
 Se puede ejecutar directamente una llamada SQL usando un objeto [CDatabase Class](../../mfc/reference/cdatabase-class.md).  Configure la cadena de instrucción SQL \(normalmente en un objeto `CString`\) y pásela a la función miembro [CDatabase::ExecuteSQL](../Topic/CDatabase::ExecuteSQL.md) del objeto `CDatabase`.  Si utiliza llamadas de función ODBC para enviar una instrucción SQL que suele devolver registros, se omiten los registros.  
  
## Vea también  
 [SQL](../../data/odbc/sql.md)