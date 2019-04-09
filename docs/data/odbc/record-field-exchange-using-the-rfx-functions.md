---
title: 'Intercambio de campos de registro: Uso de las funciones de RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC [C++], data types
- data types [C++], ODBC record field exchange
- RFX (ODBC) [C++], function syntax and parameters
- DoFieldExchange method, and RFX functions
- ODBC [C++], RFX
- RFX (ODBC) [C++], data types
- function calls, RFX functions
ms.assetid: c594300b-5a29-4119-a68b-e7ca32def696
ms.openlocfilehash: dc717336a5279e7eda1b7c39b19a7c76f9055cd3
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035989"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>Intercambio de campos de registro: Uso de las funciones de RFX

En este tema se explica cómo usar las llamadas de función RFX que componen el cuerpo de la `DoFieldExchange` invalidar.

> [!NOTE]
>  En este tema se aplica a las clases derivadas de [CRecordset](../../mfc/reference/crecordset-class.md) en qué fila de forma masiva captura no se ha implementado. Si usas la obtención masiva de filas, se implementa el intercambio masivo de campos de registros (RFX masivo). RFX masivo es similar a RFX. Para comprender las diferencias, consulte [conjunto de registros: Obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Las funciones globales de RFX intercambian datos entre las columnas en los miembros de datos de origen y el campo de datos en el conjunto de registros. Escribir llamadas de función RFX en su conjunto de registros [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) función miembro. En este tema se describe brevemente las funciones y se muestra los tipos de datos para el cual RFX funciones están disponibles. [La nota técnica 43](../../mfc/tn043-rfx-routines.md) describe cómo escribir sus propias funciones RFX para tipos de datos adicionales.

##  <a name="_core_rfx_function_syntax"></a> Sintaxis de funciones RFX

Cada función RFX toma tres parámetros (y algunos toman un cuarto o quinto parámetro opcional):

- Un puntero a un [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objeto. Basta con pasar el `pFX` puntero pasado a `DoFieldExchange`.

- El nombre de la columna tal y como aparece en el origen de datos.

- El nombre del miembro de datos de campo correspondiente o miembro de datos de parámetro en la clase de conjunto de registros.

- (Opcional) En algunas de las funciones, la longitud máxima de la cadena o matriz que se transfieren. El valor predeterminado es 255 bytes, pero desea cambiarla. El tamaño máximo se basa en el tamaño máximo de un `CString` objeto: **INT_MAX** (2.147.483.647) bytes, pero probablemente encontrará límites en el controlador antes de que el tamaño.

- (Opcional) En el `RFX_Text` función, a veces se utiliza un quinto parámetro para especificar el tipo de datos de una columna.

Para obtener más información, vea las funciones RFX en [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md) en el *Class Library Reference*. Para obtener un ejemplo de cuándo se podría hacer especial uso de los parámetros, vea [conjunto de registros: Obtener cálculos SUM y otros resultados agregados (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md).

##  <a name="_core_rfx_data_types"></a> Tipos de datos RFX

La biblioteca de clases proporciona funciones RFX para transferir muchos tipos de datos diferentes entre el origen de datos y los conjuntos de registros. En la lista siguiente se resume las funciones de RFX por tipo de datos. En casos donde debe escribir sus propias llamadas de función RFX, seleccione una de estas funciones por tipo de datos.

|Función|Tipo de datos|
|--------------|---------------|
|`RFX_Bool`|**BOOL**|
|`RFX_Byte`|**BYTE**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**double**|
|`RFX_Single`|**float**|
|`RFX_Int`|**int**|
|`RFX_Long`|**long**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|


Para obtener más información, consulte la documentación de función RFX en [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md) en el *Class Library Reference*. Para obtener información acerca de cómo se asignan los tipos de datos de C++ a tipos de datos SQL, vea la tabla ANSI SQL datos tipos asignan a tipos de datos de C++ en [SQL: Tipos de datos de C++ (ODBC) y SQL](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

## <a name="see-also"></a>Vea también

[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Intercambio de campos de registro: Funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Conjunto de registros: Parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Conjunto de registros: Enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange (clase)](../../mfc/reference/cfieldexchange-class.md)