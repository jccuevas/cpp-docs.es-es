---
title: "Intercambio de campos de registros: Utilizar las funciones de RFX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tipos de datos [C++], intercambio de campos de registros ODBC"
  - "DoFieldExchange (método), funciones de RFX"
  - "llamadas a funciones, funciones de RFX"
  - "ODBC [C++], tipos de datos"
  - "ODBC [C++], RFX"
  - "RFX (ODBC) [C++], tipos de datos"
  - "RFX (ODBC) [C++], sintaxis y parámetros de funciones"
ms.assetid: c594300b-5a29-4119-a68b-e7ca32def696
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Intercambio de campos de registros: Utilizar las funciones de RFX
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema explica cómo usar las llamadas de función RFX que componen el cuerpo de una función de reemplazo de `DoFieldExchange`.  
  
> [!NOTE]
>  Este tema es aplicable a las clases derivadas de [CRecordset](../../mfc/reference/crecordset-class.md) donde la obtención masiva de filas no está implementada.  Si usa esta obtención masiva, se implementará el intercambio masivo de campos de registros \(RFX masivo\).  RFX masivo es similar a RFX.  Para comprender mejor estas diferencias, vea [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Las funciones globales de RFX intercambian datos entre las columnas del origen de datos y los miembros de datos de campo del conjunto de registros.  Las llamadas de función RFX se escriben en la función miembro [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) del conjunto de registros.  Este tema describe las funciones brevemente y muestra los tipos de datos para los que están disponibles las funciones de RFX.  [La Nota técnica 43](../../mfc/tn043-rfx-routines.md) describe cómo escribir sus propias funciones RFX para tipos de datos adicionales.  
  
##  <a name="_core_rfx_function_syntax"></a> Sintaxis de las funciones RFX  
 Cada función RFX toma tres parámetros \(algunos toman un cuarto o quinto parámetro opcional\):  
  
-   Un puntero a un objeto [CFieldExchange](../../mfc/reference/cfieldexchange-class.md).  Basta con pasar el puntero `pFX` pasado a `DoFieldExchange`.  
  
-   El nombre de la columna tal como aparece en el origen de datos.  
  
-   El nombre del miembro de datos de campo o de parámetro correspondiente en la clase de conjunto de registros.  
  
-   \(Opcional\) En algunas funciones, la longitud máxima de la cadena o matriz que se está transfiriendo.  El valor predeterminado es 255 bytes, pero se puede modificar.  El tamaño máximo está basado en el tamaño máximo de un objeto `CString`: **INT\_MAX** \(2.147.483.647\) bytes, pero probablemente encontrará límites en el controlador antes de llegar a ese tamaño.  
  
-   \(Opcional\) En la función `RFX_Text`, a veces se utiliza un quinto parámetro para especificar el tipo de datos de una columna.  
  
 Para obtener más información, vea las funciones RFX en [Macros y funciones globales](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md) en la *Referencia de la biblioteca de clases*.  Para obtener un ejemplo de cuándo se puede hacer un uso especial de los parámetros, vea [Conjunto de registros: Obtener cálculos SUM y otros resultados agregados \(ODBC\)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md).  
  
##  <a name="_core_rfx_data_types"></a> Tipos de datos RFX  
 La biblioteca de clases proporciona funciones RFX para transferir varios tipos de datos diferentes entre el origen de datos y los conjuntos de registros.  La siguiente lista resume las funciones RFX por tipo de datos.  En los casos en que es necesario escribir sus propias llamadas de función RFX, seleccione funciones de esta lista por el tipo de datos.  
  
|Función|Tipo de datos|  
|-------------|-------------------|  
|`RFX_Bool`|**BOOL**|  
|`RFX_Byte`|**BYTE**|  
|`RFX_Binary`|`CByteArray`|  
|`RFX_Double`|**double**|  
|`RFX_Single`|**float**|  
|`RFX_Int`|`int`|  
|`RFX_Long`|**long**|  
|`RFX_LongBinary`|`CLongBinary`|  
|`RFX_Text`|`CString`|  
|`RFX_Date`|`CTime`|  
  
 Para obtener más información, vea la documentación de las funciones RFX en [Macros y funciones globales](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md) en la *Referencia de la biblioteca de clases*.  Para obtener más información sobre la correspondencia entre los tipos de datos de SQL y de C\+\+, vea la tabla Correspondencia entre tipos de datos de ANSI SQL y de C\+\+ en [SQL: tipos de datos de SQL y C\+\+ \(ODBC\)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).  
  
## Vea también  
 [Intercambio de campos de registros \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)   
 [Intercambio de campos de registros: Funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)   
 [Conjunto de registros: Parametrizar un conjunto de registros \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)   
 [Conjunto de registros: Enlazar dinámicamente columnas de datos \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange Class](../../mfc/reference/cfieldexchange-class.md)