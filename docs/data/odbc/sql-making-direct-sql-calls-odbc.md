---
title: 'SQL: Realizar llamadas directas a SQL (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- SQL, direct calls from ODBC
- SQL, calling directly from ODBC
- ODBC, SQL calls
- SQL calls
- direct SQL calls from ODBC
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
ms.openlocfilehash: 9240a227cdc4004d1e6e2b7ac26946ca233b71ec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212633"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL: Realizar llamadas directas a SQL (ODBC)

En este tema se explica:

- Cuándo usar llamadas directas a SQL.

- [Cómo realizar llamadas directas a SQL al origen de datos](#_core_making_direct_sql_function_calls).

> [!NOTE]
>  Esta información es aplicable a las clases ODBC de MFC. Si está trabajando con las clases DAO de MFC, vea el tema "comparación de Microsoft Jet Motor de base de datos SQL y ANSI SQL" en la ayuda de DAO.

##  <a name="when-to-call-sql-directly"></a><a name="_core_when_to_call_sql_directly"></a>Cuándo llamar directamente a SQL

Para crear nuevas tablas, quitar (eliminar) tablas, modificar tablas existentes, crear índices y realizar otras funciones SQL que cambian el esquema de [origen de datos (ODBC)](../../data/odbc/data-source-odbc.md) , debe emitir una instrucción SQL directamente al origen de datos mediante el lenguaje de definición de base de datos (DDL). Al utilizar un asistente para crear un conjunto de registros para una tabla (en tiempo de diseño), puede elegir las columnas de la tabla que se representarán en el conjunto de registros. Esto no permite que las columnas que usted u otro usuario del origen de datos agreguen a la tabla más adelante, una vez compilado el programa. Las clases de base de datos no admiten DDL directamente, pero todavía puede escribir código para enlazar dinámicamente una nueva columna al conjunto de registros en tiempo de ejecución. Para obtener información sobre cómo realizar este enlace, vea [conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Puede usar el propio DBMS para modificar el esquema u otra herramienta que le permita realizar funciones DDL. También puede utilizar las llamadas a funciones ODBC para enviar instrucciones SQL, como llamar a una consulta predefinida (procedimiento almacenado) que no devuelve registros.

##  <a name="making-direct-sql-function-calls"></a><a name="_core_making_direct_sql_function_calls"></a>Realizar llamadas directas a funciones SQL

Puede ejecutar directamente una llamada SQL mediante un objeto de [clase CDatabase](../../mfc/reference/cdatabase-class.md) . Configure la cadena de instrucción SQL (normalmente en una `CString`) y pásela a la función miembro [CDatabase:: ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) del objeto `CDatabase`. Si usa llamadas a funciones ODBC para enviar una instrucción SQL que normalmente devuelve registros, se omiten los registros.

## <a name="see-also"></a>Consulte también

[SQL](../../data/odbc/sql.md)
