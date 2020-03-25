---
title: 'SQL: tipos de datos de SQL y C++ (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: 1c1ce908b5c8d345906d49adc79e322225ed49f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212620"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL: tipos de datos de SQL y C++ (ODBC)

> [!NOTE]
>  Esta información es aplicable a las clases ODBC de MFC. Si está trabajando con las clases DAO de MFC, vea el tema "comparación de Microsoft Jet Motor de base de datos SQL y ANSI SQL" en la ayuda de DAO.

En la tabla siguiente se asignan los tipos C++ de datos ANSI SQL a los tipos de datos de. Esto aumenta la información del lenguaje C que se proporciona en el Apéndice D de la *Referencia del programador* del *SDK de ODBC* en el CD de MSDN Library. Los asistentes administran la mayoría de las asignaciones de tipos de datos. Si no usa un asistente, puede usar la información de asignación para ayudarle a escribir el código de intercambio de campos manualmente.

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>Tipos de datos de SQL ANSI C++ asignados a tipos de datos

|Tipo de datos ANSI SQL|Tipo de datos de C++|
|------------------------|---------------------|
|**CHAR**|`CString`|
|**DECIMAL**|`CString` 1|
|**SMALLINT**|**int**|
|**REAL**|**float**|
|**INTEGER**|**long**|
|**FLOAT**|**double**|
|**DOUBLE**|**double**|
|**NUMERIC**|`CString` 1|
|**VARCHAR**|`CString`|
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|
|**BIT**|**BOOL**|
|**TINYINT**|**BYTE**|
|**BIGINT**|`CString` 1|
|**BINARIO**|`CByteArray`|
|**VARBINARY**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|
|**DATE**|`CTime`, `CString`|
|**TIME**|`CTime`, `CString`|
|**TIMESTAMP**|`CTime`, `CString`|

1. Asignación **numérica** y **decimal** de ANSI a `CString` porque **SQL_C_CHAR** es el tipo de transferencia ODBC predeterminado.

2. Los datos de caracteres más allá de 255 caracteres se truncan de forma predeterminada cuando se asignan a `CString`. Puede extender la longitud de truncamiento estableciendo explícitamente el argumento *nMaxLength* de `RFX_Text`.

3. Los datos binarios más allá de 255 caracteres se truncan de forma predeterminada cuando se asignan a `CByteArray`. Puede extender la longitud de truncamiento estableciendo explícitamente el argumento *nMaxLength* de `RFX_Binary`.

Si no utiliza la biblioteca de cursores ODBC, podría encontrar un problema al intentar actualizar dos o más campos de longitud variable largos mediante el Microsoft SQL Server controlador ODBC y las clases de base de datos ODBC de MFC. Los tipos ODBC, **SQL_LONGVARCHAR** y **SQL_LONGVARBINARY**, se asignan a tipos de SQL Server de texto e imagen. Se produce una `CDBException` si actualiza dos o más campos de longitud variable larga en la misma llamada a `CRecordset::Update`. Por lo tanto, no actualice varias columnas Long simultáneamente con `CRecordset::Update`. Puede actualizar varias columnas Long simultáneamente con la API de ODBC `SQLPutData`. También puede utilizar la biblioteca de cursores ODBC, pero esto no se recomienda para los controladores, como el SQL Server controlador, que admiten cursores y no necesitan la biblioteca de cursores.

Si usa la biblioteca de cursores ODBC con las clases de base de datos ODBC de MFC y el controlador ODBC de Microsoft SQL Server, podría producirse una **aserción** junto con una `CDBException` si una llamada a `CRecordset::Update` sigue una llamada a `CRecordset::Requery`. En su lugar, llame a `CRecordset::Close` y `CRecordset::Open` en lugar de `CRecordset::Requery`. Otra solución consiste en no utilizar la biblioteca de cursores ODBC, ya que el SQL Server y el controlador ODBC de SQL Server proporcionan compatibilidad nativa para los cursores de forma nativa y no es necesaria la biblioteca de cursores ODBC.

## <a name="see-also"></a>Consulte también

[SQL](../../data/odbc/sql.md)<br/>
[SQL: Realizar llamadas directas a SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
