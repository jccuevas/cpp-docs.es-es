---
title: 'SQL: SQL y tipos de datos de C++ (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8b978356cead1f9b74ce59e58ab0191f5e00105b
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340773"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL: tipos de datos de SQL y C++ (ODBC)
> [!NOTE]
>  Esta información se aplica a las clases ODBC de MFC. Si está trabajando con las clases DAO de MFC, vea el tema "Comparación de Microsoft Jet base de datos de motor de SQL y ANSI SQL" en la Ayuda de DAO.  
  
 La siguiente tabla asigna los tipos de datos de ANSI SQL a tipos de datos de C++. Esto complementa la información del lenguaje C en el apéndice D de la *ODBC SDK* *referencia del programador* en el CD de MSDN Library. Los asistentes para administran asignar la mayoría de tipos de datos por usted. Si no usa a un asistente, puede usar la información de asignación que le ayudarán a escribir el código de intercambio de campos manualmente.  
  
### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>Tipos de datos de ANSI SQL se asignan a tipos de datos de C++  
  
|Tipo de datos SQL ANSI|Tipo de datos de C++|  
|------------------------|---------------------|  
|**CHAR**|`CString`|  
|**DECIMAL**|`CString` 1|  
|**SMALLINT**|**int**|  
|**REAL**|**float**|  
|**ENTERO**|**long**|  
|**FLOAT**|**double**|  
|**DOUBLE**|**double**|  
|**NUMÉRICO**|`CString` 1|  
|**VARCHAR**|`CString`|  
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|  
|**BIT**|**BOOL**|  
|**TINYINT**|**BYTE**|  
|**BIGINT**|`CString` 1|  
|**BINARIO**|`CByteArray`|  
|**VARBINARY**|`CByteArray`|  
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|  
|**DATE**|`CTime`, `CString`|  
|**TIEMPO**|`CTime`, `CString`|  
|**MARCA DE TIEMPO**|`CTime`, `CString`|  
  
 1. ANSI **DECIMAL** y **numérico** se asignan a `CString` porque **SQL_C_CHAR** es el tipo de transferencia predeterminado ODBC.  
  
 2. Datos de caracteres más allá de 255 caracteres se truncan de forma predeterminada cuando se asigna a `CString`. Puede ampliar la longitud de truncamiento si se establece explícitamente el *nMaxLength* argumento de `RFX_Text`.  
  
 3. Datos binarios más allá de 255 caracteres se truncan de forma predeterminada cuando se asigna a `CByteArray`. Puede ampliar la longitud de truncamiento si se establece explícitamente el *nMaxLength* argumento de `RFX_Binary`.  
  
 Si no usa la biblioteca de cursores ODBC, podría encontrar un problema al intentar actualizar dos o más campos de longitud variable largo con el controlador ODBC de Microsoft SQL Server y las clases de base de datos ODBC de MFC. Los tipos ODBC **SQL_LONGVARCHAR** y **SQL_LONGVARBINARY**, asigne a texto y tipos de SQL Server de la imagen. Un `CDBException` se produce si actualiza dos o más campos de longitud variable long en la misma llamada a `CRecordset::Update`. Por lo tanto, no se actualizan varias columnas long simultáneamente con `CRecordset::Update`. Puede actualizar varias columnas long simultáneamente con la API de ODBC `SQLPutData`. También puede usar la biblioteca de cursores ODBC, pero esto no se recomienda para los controladores, al igual que el controlador de SQL Server que admiten cursores y no necesitan la biblioteca de cursores.  
  
 Si usa la biblioteca de cursores ODBC con las clases de base de datos ODBC de MFC y el controlador ODBC de Microsoft SQL Server, un **ASSERT** produzcan junto con un `CDBException` si una llamada a `CRecordset::Update` sigue una llamada a `CRecordset::Requery`. En su lugar, llame a `CRecordset::Close` y `CRecordset::Open` lugar `CRecordset::Requery`. Otra solución es no usar la biblioteca de cursores ODBC, porque el servidor SQL Server y el controlador ODBC de SQL Server proporcionan compatibilidad nativa con los cursores y la biblioteca de cursores ODBC no es necesaria.  
  
## <a name="see-also"></a>Vea también  
 [SQL](../../data/odbc/sql.md)   
 [SQL: Realizar llamadas directas a SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)