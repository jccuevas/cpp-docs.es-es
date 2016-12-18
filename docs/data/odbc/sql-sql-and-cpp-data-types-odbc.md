---
title: "SQL: tipos de datos de SQL y C++ (ODBC) | Microsoft Docs"
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
  - "tipos de datos [C++], SQL y C++"
  - "SQL [C++], tipos de datos de C++"
  - "tipos de datos de SQL [C++]"
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SQL: tipos de datos de SQL y C++ (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  Esta información es aplicable a las clases ODBC de MFC.  Si trabaja con las clases DAO de MFC, vea el tema "Comparación entre SQL del motor de bases de datos Microsoft Jet y SQL ANSI" en la Ayuda de DAO.  
  
 La tabla siguiente muestra la correspondencia entre los tipos de datos de ANSI SQL y los tipos de datos de C\+\+.  Esto complementa la información del lenguaje C incluida en el Apéndice D de la *Referencia del programador del SDK de ODBC*,en el CD de MSDN Library.  Los asistentes administran por el usuario la mayoría de las asignaciones de tipos de datos.  Si no utiliza un asistente, puede usar la información de asignación para ayudarle a escribir manualmente el código de intercambio de campos.  
  
### Correspondencia entre tipos de datos de ANSI SQL y de C\+\+  
  
|Tipo de datos ANSI SQL|Tipo de datos de C\+\+|  
|----------------------------|----------------------------|  
|**CHAR**|`CString`|  
|**DECIMAL**|`CString` 1|  
|**SMALLINT**|`int`|  
|`REAL`|**float**|  
|**INTEGER**|**long**|  
|**FLOAT**|**double**|  
|**DOUBLE**|**double**|  
|**NUMERIC**|`CString` 1|  
|**VARCHAR**|`CString`|  
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|  
|**BIT**|**BOOL**|  
|**TINYINT**|**BYTE**|  
|**BIGINT**|`CString` 1|  
|**BINARY**|`CByteArray`|  
|**VARBINARY**|`CByteArray`|  
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|  
|**DATE**|`CTime`, `CString`|  
|**TIME**|**CTime, CString**|  
|**TIMESTAMP**|**CTime, CString**|  
  
 1.  Los tipos de datos ANSI **DECIMAL** y **NUMERIC** se corresponden con `CString`, ya que **SQL\_C\_CHAR** es el tipo de transferencia ODBC predeterminado.  
  
 2.  Los datos de caracteres más allá de 255 caracteres se truncan de forma predeterminada al asignarse a `CString`.  Se puede extender la longitud de truncación explícitamente, estableciendo el argumento `nMaxLength` de `RFX_Text`.  
  
 3.  Los datos binarios más allá de 255 caracteres se truncan de forma predeterminada al asignarse a `CByteArray`.  Se puede extender la longitud de truncación explícitamente, estableciendo el argumento `nMaxLength` de `RFX_Binary`.  
  
 Si no se utiliza la biblioteca de cursores de ODBC, se puede producir un problema al intentar actualizar dos o más campos de longitud de variable long mientras se usa el controlador ODBC para Microsoft SQL Server y las clases de base de datos ODBC de MFC.  Los tipos ODBC **SQL\_LONGVARCHAR** y **SQL\_LONGVARBINARY** se corresponden con los tipos de SQL Server de texto e imagen.  Se produce una excepción `CDBException` al actualizar dos o más campos de longitud de variable long en la misma llamada a `CRecordset::Update`.  Por lo tanto, no se deben actualizar varias columnas long simultáneamente mediante `CRecordset::Update`.  Para ello, utilice la función de la API ODBC **SQLPutData**.  También se puede usar la biblioteca de cursores ODBC, pero no se recomienda para controladores como el de SQL Server que admiten cursores y no necesitan de la biblioteca de cursores.  
  
 Si utiliza la biblioteca de cursores de ODBC con las clases de base de datos ODBC de MFC y el controlador ODBC de Microsoft SQL Server ODBC, se puede producir una aserción **ASSERT** junto con una excepción `CDBException` si después de una llamada a `CRecordset::Update` sigue otra llamada a `CRecordset::Requery`.  Para evitarlo, llame a `CRecordset::Close` y `CRecordset::Open` en lugar de a `CRecordset::Requery`.  Otra solución es no usar la biblioteca de cursores ODBC, ya que SQL Server y el controlador ODBC de SQL Server proporcionan compatibilidad nativa con los cursores y no es necesario el uso de la biblioteca.  
  
## Vea también  
 [SQL](../../data/odbc/sql.md)   
 [SQL: Realizar llamadas directas a SQL \(ODBC\)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)