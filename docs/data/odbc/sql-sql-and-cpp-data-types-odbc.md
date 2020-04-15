---
title: 'SQL: tipos de datos de SQL y C++ (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: cffe44b832ac1eb28d368072b8f0e92ea9f57feb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374473"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL: tipos de datos de SQL y C++ (ODBC)

> [!NOTE]
> Esta información es aplicable a las clases ODBC de MFC. Si está trabajando con las clases DAO de MFC, vea el tema "Comparación de Microsoft Jet Database Engine SQL y ANSI SQL" en la Ayuda de DAO.

En la tabla siguiente se asignan tipos de datos ANSI SQL a tipos de datos C++. Esto aumenta la información del lenguaje C proporcionada en el Apéndice D de la *Referencia del programador* del *SDK* ODBC en el CD de MSDN Library. Los asistentes administran la mayoría de la asignación de tipos de datos por usted. Si no utiliza un asistente, puede utilizar la información de asignación para ayudarle a escribir el código de intercambio de campos manualmente.

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>ANSI SQL Data Types Mapped to C++ Data Types

|Tipo de datos ANSI SQL|Tipo de datos de C++|
|------------------------|---------------------|
|**CHAR**|`CString`|
|**Decimal**|`CString`1|
|**Smallint**|**int**|
|**Real**|**Flotador**|
|**Entero**|**Largo**|
|**Flotador**|**double**|
|**Doble**|**double**|
|**Numérico**|`CString`1|
|**Varchar**|`CString`|
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|
|**Poco**|**Bool**|
|**Tinyint**|**Byte**|
|**Bigint**|`CString`1|
|**Binario**|`CByteArray`|
|**Varbinary**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|
|**Fecha**|`CTime`, `CString`|
|**hora**|`CTime`, `CString`|
|**Timestamp**|`CTime`, `CString`|

1. ANSI **DECIMAL** y `CString` **NUMERIC** se asignan a porque **SQL_C_CHAR** es el tipo de transferencia ODBC predeterminado.

2. Los datos de caracteres superiores a 255 caracteres se truncan de forma predeterminada cuando se asignan a `CString`. Puede ampliar la longitud de truncamiento estableciendo explícitamente el argumento *nMaxLength* de `RFX_Text`.

3. Los datos binarios que superen los 255 caracteres se truncan de forma predeterminada cuando se asignan a `CByteArray`. Puede ampliar la longitud de truncamiento estableciendo explícitamente el argumento *nMaxLength* de `RFX_Binary`.

Si no utiliza la biblioteca de cursores ODBC, es posible que encuentre un problema al intentar actualizar dos o más campos de longitud variable larga mediante el controlador ODBC de Microsoft SQL Server y las clases de base de datos ODBC de MFC. Los tipos ODBC, **SQL_LONGVARCHAR** y **SQL_LONGVARBINARY**, se asignan a los tipos de SQL Server de texto e imagen. A `CDBException` se produce si actualiza dos o más campos de `CRecordset::Update`longitud variable largos en la misma llamada a . Por lo tanto, no actualice `CRecordset::Update`varias columnas largas simultáneamente con . Puede actualizar varias columnas largas `SQLPutData`simultáneamente con la API ODBC. También puede usar la biblioteca de cursores ODBC, pero esto no se recomienda para los controladores, como el controlador de SQL ServerSQL Server , que admiten cursores y no necesitan la biblioteca de cursores.

Si utiliza la biblioteca de cursores ODBC con las clases de base de datos `CDBException` ODBC de `CRecordset::Update` MFC y el controlador ODBC de Microsoft SQL Server, puede producirse un **ASSERT** junto con una llamada if para seguir una llamada a `CRecordset::Requery`. En su `CRecordset::Close` `CRecordset::Open` lugar, `CRecordset::Requery`llame y en lugar de . Otra solución es no usar la biblioteca de cursores ODBC, porque sql ServerSQL Server y el controlador ODBC de SQL ServerSQL Server proporcionan compatibilidad nativa para cursores de forma nativa y la biblioteca de cursores ODBC no es necesaria.

## <a name="see-also"></a>Consulte también

[SQL](../../data/odbc/sql.md)<br/>
[SQL: Realizar llamadas directas a SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
