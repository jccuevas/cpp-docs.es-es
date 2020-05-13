---
title: Clase CFieldExchange
ms.date: 11/04/2016
f1_keywords:
- CFieldExchange
- AFXDB/CFieldExchange
- AFXDB/CFieldExchange::IsFieldType
- AFXDB/CFieldExchange::SetFieldType
helpviewer_keywords:
- CFieldExchange [MFC], IsFieldType
- CFieldExchange [MFC], SetFieldType
ms.assetid: 24c5c0b3-06a6-430e-9b6f-005a2c65e29f
ms.openlocfilehash: de9db2713a25b232bbd7f936958d1c10e96c511a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753171"
---
# <a name="cfieldexchange-class"></a>Clase CFieldExchange

Admite las rutinas de intercambio de campos de registro (RFX) y de intercambio masivo de campos de registro (RFX Masivo) utilizadas por las clases de base de datos.

## <a name="syntax"></a>Sintaxis

```
class CFieldExchange
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFieldExchange::IsFieldType](#isfieldtype)|Devuelve distinto de cero si la operación actual es adecuada para el tipo de campo que se va a actualizar.|
|[CFieldExchange::SetFieldType](#setfieldtype)|Especifica el tipo de miembro de datos de conjunto de registros (columna o `SetFieldType`parámetro) representado por todas las llamadas siguientes a funciones RFX hasta la siguiente llamada a .|

## <a name="remarks"></a>Observaciones

`CFieldExchange`no tiene una clase base.

Utilice esta clase si está escribiendo rutinas de intercambio de datos para tipos de datos personalizados o cuando está implementando la obtención masiva de filas; de lo contrario, no utilizará directamente esta clase. RFX y RFX masivo intercambia datos entre los miembros de datos de campo del objeto de conjunto de registros y los campos correspondientes del registro actual en el origen de datos.

> [!NOTE]
> Si está trabajando con las clases de objetos de acceso a datos (DAO) en lugar de las clases de conectividad de base de datos abierta (ODBC), utilice la clase [CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md) en su lugar. Para obtener más información, vea el artículo [Información general:Programación](../../data/data-access-programming-mfc-atl.md)de bases de datos .

Un `CFieldExchange` objeto proporciona la información de contexto necesaria para el intercambio de campos de registros o el intercambio masivo de campos de registros. `CFieldExchange`los objetos admiten una serie de operaciones, incluidos los parámetros de enlace y los miembros de datos de campo y la configuración de varias marcas en los campos del registro actual. Las operaciones RFX y RFX masivas se realizan en miembros `CFieldExchange`de datos de clase de conjunto de registros de tipos definidos por **enum** **FieldType** en . Los valores posibles **de FieldType** son:

- `CFieldExchange::outputColumn`para los miembros de datos de campo.

- `CFieldExchange::inputParam`o `CFieldExchange::param` para los miembros de datos de parámetros de entrada.

- `CFieldExchange::outputParam`para los miembros de datos de parámetros de salida.

- `CFieldExchange::inoutParam`para los miembros de datos de parámetros de entrada/salida.

La mayoría de las funciones miembro de la clase y los miembros de datos se proporcionan para escribir sus propias rutinas RFX personalizadas. Lo usará `SetFieldType` con frecuencia. Para obtener más información, vea los artículos Intercambio de campos de [registros (RFX)](../../data/odbc/record-field-exchange-rfx.md) y Conjunto de [registros (ODBC)](../../data/odbc/recordset-odbc.md). Para obtener información acerca de la obtención masiva de filas, vea el artículo [Conjunto de registros: obtención de registros en masa (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Para obtener más información acerca de las funciones globales RFX y RFX masivo, vea [Funciones](../../mfc/reference/record-field-exchange-functions.md) de intercambio de campos de registro en la sección Macros y valores globales de MFC de esta referencia.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CFieldExchange`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdb.h

## <a name="cfieldexchangeisfieldtype"></a><a name="isfieldtype"></a>CFieldExchange::IsFieldType

Si escribe su propia función `IsFieldType` RFX, llame al principio de la función para determinar si la `CFieldExchange::outputColumn`operación actual se puede realizar en un tipo de miembro de datos de campo o parámetro determinado (a `CFieldExchange::inputParam`, , `CFieldExchange::param`, `CFieldExchange::outputParam`, o `CFieldExchange::inoutParam`).

```
BOOL IsFieldType(UINT* pnField);
```

### <a name="parameters"></a>Parámetros

*pnField*<br/>
El número secuencial del miembro de datos de campo o parámetro se devuelve en este parámetro. Este número corresponde al orden del miembro de datos en la función [CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) o [CRecordset::DoBulkFieldExchange.](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación actual se puede realizar en el campo actual o el tipo de parámetro.

### <a name="remarks"></a>Observaciones

Siga el modelo de las funciones RFX existentes.

## <a name="cfieldexchangesetfieldtype"></a><a name="setfieldtype"></a>CFieldExchange::SetFieldType

Necesita una llamada `SetFieldType` a la invalidación [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) o [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) de la clase de conjunto de registros.

```cpp
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Parámetros

*nFieldType*<br/>
Un valor `enum FieldType`de , `CFieldExchange`declarado en , que puede ser uno de los siguientes:

- `CFieldExchange::outputColumn`

- `CFieldExchange::inputParam`

- `CFieldExchange::param`

- `CFieldExchange::outputParam`

- `CFieldExchange::inoutParam`

### <a name="remarks"></a>Observaciones

Para los miembros de `SetFieldType` datos de `CFieldExchange::outputColumn`campo, debe llamar con un parámetro de , seguido de llamadas a las funciones RFX o RFX masivo. Si no ha implementado la obtención masiva de `SetFieldType` filas, ClassWizard coloca `DoFieldExchange`esta llamada por usted en la sección de mapa de campo de .

Si parametriza la clase de conjunto `SetFieldType` de registros, debe llamar de nuevo, fuera de cualquier sección de mapa de campo, seguida de llamadas RFX para todos los miembros de datos de parámetro. Cada tipo de miembro de `SetFieldType` datos de parámetro debe tener su propia llamada. En la tabla siguiente se distinguen `SetFieldType` los diferentes valores a los que puede pasar para representar los miembros de datos de parámetro de la clase:

|Valor del parámetro SetFieldType|Tipo de miembro de datos de parámetro|
|----------------------------------|-----------------------------------|
|`CFieldExchange::inputParam`|Parámetro de entrada. Valor que se pasa a la consulta o al procedimiento almacenado del conjunto de registros.|
|`CFieldExchange::param` | igual `CFieldExchange::inputParam`que .|
|`CFieldExchange::outputParam`|Parámetro de salida. Un valor devuelto del procedimiento almacenado del conjunto de registros.|
|`CFieldExchange::inoutParam`|Parámetro de entrada/salida. Valor que se pasa y devuelve desde el procedimiento almacenado del conjunto de registros.|

En general, cada grupo de llamadas a funciones RFX asociadas con `SetFieldType`miembros de datos de campo o miembros de datos de parámetro deben ir precedidos de una llamada a . El *nFieldType* parámetro `SetFieldType` de cada llamada identifica el tipo de los miembros `SetFieldType` de datos representados por las llamadas de función RFX que siguen a la llamada.

Para obtener más información sobre el control `CRecordset` de los parámetros de salida y entrada/salida, vea la función miembro [FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset). Para obtener más información acerca de las funciones RFX y RFX masivo, vea el tema [Funciones](../../mfc/reference/record-field-exchange-functions.md)de intercambio de campos de registro . Para obtener información relacionada sobre la obtención masiva de filas, vea el artículo [Conjunto de registros: obtención de registros en masa (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Ejemplo

Este ejemplo muestra varias llamadas a funciones RFX con llamadas adjuntas a `SetFieldType`. Tenga `SetFieldType` en cuenta `pFX` que se `CFieldExchange` llama a través del puntero a un objeto.

[!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CRecordset](../../mfc/reference/crecordset-class.md)
