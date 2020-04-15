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
ms.openlocfilehash: e2421e047d217fdc7a138509385399fa37d36a1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374501"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL: Realizar llamadas directas a SQL (ODBC)

En este tema se explica:

- Cuándo usar llamadas SQL directas.

- [Cómo realizar llamadas SQL directas al origen](#_core_making_direct_sql_function_calls)de datos.

> [!NOTE]
> Esta información es aplicable a las clases ODBC de MFC. Si está trabajando con las clases DAO de MFC, vea el tema "Comparación de Microsoft Jet Database Engine SQL y ANSI SQL" en la Ayuda de DAO.

## <a name="when-to-call-sql-directly"></a><a name="_core_when_to_call_sql_directly"></a>Cuándo llamar a SQL directamente

Para crear nuevas tablas, quitar (eliminar) tablas, modificar tablas existentes, crear índices y realizar otras funciones SQL que cambian el esquema del origen de [datos (ODBC),](../../data/odbc/data-source-odbc.md) debe emitir una instrucción SQL directamente al origen de datos mediante el lenguaje de definición de base de datos (DDL). Cuando se utiliza un asistente para crear un conjunto de registros para una tabla (en tiempo de diseño), puede elegir qué columnas de la tabla se representarán en el conjunto de registros. Esto no permite las columnas que usted u otro usuario del origen de datos agregue a la tabla más adelante, después de compilar el programa. Las clases de base de datos no admiten DDL directamente, pero todavía puede escribir código para enlazar una nueva columna al conjunto de registros dinámicamente, en tiempo de ejecución. Para obtener información sobre cómo realizar este enlace, vea [Conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Puede utilizar el propio DBMS para modificar el esquema u otra herramienta que le permita realizar funciones DDL. También puede usar llamadas de función ODBC para enviar instrucciones SQL, como llamar a una consulta predefinida (procedimiento almacenado) que no devuelve registros.

## <a name="making-direct-sql-function-calls"></a><a name="_core_making_direct_sql_function_calls"></a>Realización de llamadas directas a funciones SQL

Puede ejecutar directamente una llamada SQL mediante un [CDatabase clase](../../mfc/reference/cdatabase-class.md) objeto. Configure la cadena de instrucción `CString`SQL (normalmente en un ) y pásela a la función miembro [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) del `CDatabase` objeto. Si utiliza llamadas a funciones ODBC para enviar una instrucción SQL que normalmente devuelve registros, se omiten los registros.

## <a name="see-also"></a>Consulte también

[SQL](../../data/odbc/sql.md)
