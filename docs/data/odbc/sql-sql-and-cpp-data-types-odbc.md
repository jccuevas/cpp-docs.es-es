---
title: 'SQL: Tipos de datos de C++ (ODBC) y SQL | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 14afd27887368f07610fb1315d7b573c09382c49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL: tipos de datos de SQL y C++ (ODBC)
> [!NOTE]
>  Esta información se aplica a las clases ODBC de MFC. Si está trabajando con las clases DAO de MFC, vea el tema "Comparación de SQL del motor de base de datos de datos Microsoft Jet y SQL ANSI" en la Ayuda de DAO.  
  
 En la tabla siguiente asigna los tipos de datos de ANSI SQL a tipos de datos de C++. Esto aumenta la información del lenguaje C en el apéndice D de la *el SDK de ODBC* *referencia del programador* en el CD de MSDN Library. Los asistentes administran mayoría asignaciones de tipos de datos automáticamente. Si no usa a un asistente, puede utilizar la información de asignación para ayudarle a escribir el código de intercambio de campos manualmente.  
  
### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>Tipos de datos de ANSI SQL asignados a tipos de datos de C++  
  
|Tipo de datos de ANSI SQL|Tipo de datos de C++|  
|------------------------|---------------------|  
|**CHAR**|`CString`|  
|**DECIMAL**|`CString` 1|  
|**SMALLINT**|`int`|  
|`REAL`|**float**|  
|**ENTERO**|**long**|  
|**FLOAT**|**double**|  
|**DOUBLE**|**double**|  
|**NUMÉRICO**|`CString` 1|  
|**VARCHAR**|`CString`|  
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|  
|**BITS**|**BOOL**|  
|**TINYINT**|**BYTE**|  
|**BIGINT**|`CString` 1|  
|**BINARIO**|`CByteArray`|  
|**VARBINARY**|`CByteArray`|  
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|  
|**DATE**|`CTime`, `CString`|  
|**TIEMPO**|**CTime, CString**|  
|**MARCA DE TIEMPO**|**CTime, CString**|  
  
 1. ANSI **DECIMAL** y **numérico** se asignan a `CString` porque **SQL_C_CHAR** es el tipo de transferencia ODBC predeterminado.  
  
 2. Datos de caracteres más allá de 255 caracteres se truncan de forma predeterminada cuando se asigna a `CString`. Puede ampliar la longitud de truncación explícitamente, estableciendo el `nMaxLength` argumento de `RFX_Text`.  
  
 3. Datos binarios más allá de 255 caracteres se truncan de forma predeterminada cuando se asigna a `CByteArray`. Puede ampliar la longitud de truncación explícitamente, estableciendo el `nMaxLength` argumento de `RFX_Binary`.  
  
 Si no utiliza la biblioteca de cursores ODBC, puede tener problemas al intentar actualizar dos o más campos de longitud variable larga con el controlador ODBC de Microsoft SQL Server y las clases de base de datos ODBC de MFC. Los tipos ODBC, **SQL_LONGVARCHAR** y **SQL_LONGVARBINARY**, asigne al texto y tipos de SQL Server de la imagen. A `CDBException` se produce si actualiza dos o más campos de longitud variable larga en la misma llamada a `CRecordset::Update`. Por lo tanto, no se actualizan varias columnas long simultáneamente con `CRecordset::Update`. Puede actualizar varias columnas long simultáneamente con la API de ODBC **SQLPutData**. También puede usar la biblioteca de cursores ODBC, pero esto no se recomienda para controladores, como el controlador de SQL Server que admiten cursores y no necesitan la biblioteca de cursores.  
  
 Si usas la biblioteca de cursores ODBC con las clases de base de datos ODBC de MFC y el controlador ODBC de Microsoft SQL Server, un **ASSERT** puede ocurrir junto con un `CDBException` si una llamada a `CRecordset::Update` sigue a una llamada a `CRecordset::Requery`. En su lugar, llame a `CRecordset::Close` y `CRecordset::Open` en lugar de `CRecordset::Requery`. Otra solución es no usar la biblioteca de cursores ODBC, porque el servidor SQL Server y el controlador ODBC de SQL Server proporcionan compatibilidad nativa con los cursores y la biblioteca de cursores ODBC no es necesaria.  
  
## <a name="see-also"></a>Vea también  
 [SQL](../../data/odbc/sql.md)   
 [SQL: Realizar llamadas directas a SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)