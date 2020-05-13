---
title: 'Intercambio de campos de registros: Utilizar las funciones de RFX'
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
ms.openlocfilehash: f1afded360cfeff564f1f3d8bb9b294aa33cb733
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367133"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>Intercambio de campos de registros: Utilizar las funciones de RFX

En este tema se explica cómo usar las llamadas `DoFieldExchange` a la función RFX que componen el cuerpo de la invalidación.

> [!NOTE]
> Este tema se aplica a las clases derivadas de [CRecordset](../../mfc/reference/crecordset-class.md) en las que no se ha implementado la obtención masiva de filas. Si usa la obtención masiva de filas, se implementará el intercambio masivo de campos de registros (RFX masivo). RFX masivo es similar a RFX. Para comprender las diferencias, vea [Conjunto de registros: obtención de registros en masa (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Las funciones globales de RFX intercambian datos entre columnas en el origen de datos y los miembros de datos de campo del conjunto de registros. Escribir las llamadas de función RFX en el conjunto de registros [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) función miembro. En este tema se describen brevemente las funciones y se muestran los tipos de datos para los que están disponibles las funciones RFX. [Nota técnica 43](../../mfc/tn043-rfx-routines.md) describe cómo escribir sus propias funciones RFX para tipos de datos adicionales.

## <a name="rfx-function-syntax"></a><a name="_core_rfx_function_syntax"></a>Sintaxis de la función RFX

Cada función RFX toma tres parámetros (y algunos toman un cuarto o quinto parámetro opcional):

- Un puntero a un [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objeto. Simplemente pase a `pFX` lo `DoFieldExchange`largo del puntero pasado a .

- El nombre de la columna tal como aparece en el origen de datos.

- El nombre del miembro de datos de campo o miembro de datos de parámetro correspondiente en la clase de conjunto de registros.

- (Opcional) En algunas de las funciones, la longitud máxima de la cadena o matriz que se transfiere. El valor predeterminado es 255 bytes, pero es posible que desee cambiarlo. El tamaño máximo se basa en `CString` el tamaño máximo de un objeto **(INT_MAX** (2.147.483.647) bytes), pero probablemente se encontrará con límites de controlador antes de ese tamaño.

- (Opcional) En `RFX_Text` la función, a veces se utiliza un quinto parámetro para especificar el tipo de datos de una columna.

Para obtener más información, consulte las funciones RFX en [Macros y globales](../../mfc/reference/mfc-macros-and-globals.md) en la Referencia de biblioteca de *clases*. Para obtener un ejemplo de cuándo puede hacer un uso especial de los parámetros, vea [Conjunto de registros: obtención de SUM y otros resultados agregados (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md).

## <a name="rfx-data-types"></a><a name="_core_rfx_data_types"></a>Tipos de datos RFX

La biblioteca de clases proporciona funciones RFX para transferir muchos tipos de datos diferentes entre el origen de datos y los conjuntos de registros. En la lista siguiente se resumen las funciones RFX por tipo de datos. En los casos en los que debe escribir sus propias llamadas a funciones RFX, seleccione una de estas funciones por tipo de datos.

|Función|Tipo de datos|
|--------------|---------------|
|`RFX_Bool`|**Bool**|
|`RFX_Byte`|**Byte**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**double**|
|`RFX_Single`|**Flotador**|
|`RFX_Int`|**int**|
|`RFX_Long`|**Largo**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|

Para obtener más información, consulte la documentación de la función RFX en [Macros y globales](../../mfc/reference/mfc-macros-and-globals.md) en la Referencia de biblioteca de *clases*. Para obtener información sobre cómo los tipos de datos C++ se asignan a tipos de datos SQL, vea la tabla AnSI SQL Data Types Mapped to C++ Data Types in [SQL: SQL and C++ Data Types (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

## <a name="see-also"></a>Consulte también

[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Intercambio de campos de registros: Funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Conjunto de registros: Parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Conjunto de registros: Enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Clase CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Clase CFieldExchange](../../mfc/reference/cfieldexchange-class.md)
