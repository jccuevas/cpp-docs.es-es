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
ms.openlocfilehash: a54dbc10e80e19f744bb58c23639a4376156d2e7
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077091"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>Intercambio de campos de registros: Utilizar las funciones de RFX

En este tema se explica cómo usar las llamadas de función de RFX que componen el cuerpo de la in`DoFieldExchange` invalidación.

> [!NOTE]
>  Este tema se aplica a las clases derivadas de [CRecordset](../../mfc/reference/crecordset-class.md) en las que no se ha implementado la obtención masiva de filas. Si usa la obtención masiva de filas, se implementará el intercambio masivo de campos de registros (RFX masivo). RFX masivo es similar a RFX. Para comprender las diferencias, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Las funciones globales de RFX intercambian datos entre las columnas del origen de datos y los miembros de datos de campo del conjunto de registros. Se escriben las llamadas de función RFX en la función miembro [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) del conjunto de registros. En este tema se describen brevemente las funciones y se muestran los tipos de datos para los que están disponibles las funciones de RFX. La [Nota técnica 43](../../mfc/tn043-rfx-routines.md) describe cómo escribir sus propias funciones de RFX para tipos de datos adicionales.

##  <a name="rfx-function-syntax"></a><a name="_core_rfx_function_syntax"></a>Sintaxis de la función RFX

Cada función de RFX toma tres parámetros (y otros toman un cuarto o quinto parámetro opcional):

- Un puntero a un objeto [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) . Basta con pasar el puntero `pFX` pasado a `DoFieldExchange`.

- El nombre de la columna tal y como aparece en el origen de datos.

- Nombre del miembro de datos de campo o del miembro de datos de parámetro correspondiente en la clase de conjunto de registros.

- Opta En algunas de las funciones, la longitud máxima de la cadena o matriz que se va a transferir. El valor predeterminado es 255 bytes, pero puede que desee cambiarlo. El tamaño máximo se basa en el tamaño máximo de un objeto de `CString`, **INT_MAX** (2.147.483.647) bytes, pero es probable que se encuentre con límites de controladores antes de ese tamaño.

- Opta En la función `RFX_Text`, a veces se utiliza un quinto parámetro para especificar el tipo de datos de una columna.

Para obtener más información, vea las funciones de RFX en [macros y globales](../../mfc/reference/mfc-macros-and-globals.md) en la referencia de la *biblioteca de clases*. Para obtener un ejemplo de Cuándo se puede hacer un uso especial de los parámetros, vea [conjunto de registros: obtener cálculos SUM y otros resultados agregados (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md).

##  <a name="rfx-data-types"></a><a name="_core_rfx_data_types"></a>Tipos de datos de RFX

La biblioteca de clases de proporciona funciones de RFX para transferir muchos tipos de datos diferentes entre el origen de datos y los conjuntos de registros. En la lista siguiente se resumen las funciones de RFX según el tipo de datos. En los casos en los que debe escribir sus propias llamadas de función RFX, seleccione entre estas funciones según el tipo de datos.

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

Para obtener más información, vea la documentación de la función RFX en [macros y globales](../../mfc/reference/mfc-macros-and-globals.md) en la referencia de la *biblioteca de clases*. Para obtener información sobre C++ cómo se asignan los tipos de datos a tipos de datos SQL, vea la tabla C++ tipos de datos SQL de ANSI asignados a tipos de datos de [SQL: SQL y C++ tipos de datos (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

## <a name="see-also"></a>Consulte también

[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Intercambio de campos de registros: Funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Conjunto de registros: Parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Conjunto de registros: Enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange (clase)](../../mfc/reference/cfieldexchange-class.md)