---
title: 'SQL: Realizar llamadas directas a SQL (ODBC) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SQL, direct calls from ODBC
- SQL, calling directly from ODBC
- ODBC, SQL calls
- SQL calls
- direct SQL calls from ODBC
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2134fc41b604ffd659f9ee075abc9d462ff4f0db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL: Realizar llamadas directas a SQL (ODBC)
En este tema se explica:  
  
-   Cuándo usar SQL directos llama.  
  
-   [Cómo hacer directa en SQL llama al origen de datos](#_core_making_direct_sql_function_calls).  
  
> [!NOTE]
>  Esta información se aplica a las clases ODBC de MFC. Si está trabajando con las clases DAO de MFC, vea el tema "Comparación de SQL del motor de base de datos de datos Microsoft Jet y SQL ANSI" en la Ayuda de DAO.  
  
##  <a name="_core_when_to_call_sql_directly"></a> Cuándo se debe llamar directamente a SQL  
 Para crear nuevas tablas, quitar (eliminar) tablas, modificar las tablas existentes, crear índices y realizar otras funciones SQL que cambien el [origen de datos (ODBC)](../../data/odbc/data-source-odbc.md) esquema, debe emitir una instrucción SQL directamente al origen de datos con la base de datos Lenguaje de definición (DDL). Cuando usa un Asistente para crear un conjunto de registros para una tabla (en tiempo de diseño), puede elegir qué columnas de la tabla para representar en el conjunto de registros. No se permite para las columnas que usted u otro usuario del origen de datos agregar a la tabla más adelante, después de que el programa se ha compilado. Las clases de base de datos no admiten DDL directamente, pero todavía puede escribir código para enlazar una nueva columna con el conjunto de registros dinámicamente, en tiempo de ejecución. Para obtener información acerca de cómo realizar este enlace, vea [conjunto de registros: enlace dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
 Puede utilizar el propio DBMS para modificar el esquema u otra herramienta que le permite realizar funciones DDL. También puede utilizar llamadas a funciones ODBC para enviar instrucciones SQL, como llamar a una consulta predefinida (procedimiento almacenado) que no devuelve ningún registro.  
  
##  <a name="_core_making_direct_sql_function_calls"></a> Realizar llamadas de función SQL directas  
 Se puede ejecutar directamente una llamada SQL usando un [CDatabase (clase)](../../mfc/reference/cdatabase-class.md) objeto. Configure la cadena de instrucción SQL (normalmente en un `CString`) y lo pasa a la [CDatabase:: ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) función miembro de su `CDatabase` objeto. Si utiliza llamadas a funciones ODBC para enviar una instrucción SQL que normalmente devuelve registros, se omiten los registros.  
  
## <a name="see-also"></a>Vea también  
 [SQL](../../data/odbc/sql.md)