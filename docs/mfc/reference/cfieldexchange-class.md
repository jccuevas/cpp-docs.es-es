---
title: CFieldExchange (clase)
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
ms.openlocfilehash: e66b3ed16d4f21d46567c37bfaf7929d32f63b8e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425902"
---
# <a name="cfieldexchange-class"></a>CFieldExchange (clase)

Admite las rutinas de intercambio de campos de registro (RFX) y de intercambio masivo de campos de registro (RFX Masivo) utilizadas por las clases de base de datos.

## <a name="syntax"></a>Sintaxis

```
class CFieldExchange
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFieldExchange:: IsFieldType](#isfieldtype)|Devuelve un valor distinto de cero si la operación actual es adecuada para el tipo de campo que se está actualizando.|
|[CFieldExchange:: SetFieldType](#setfieldtype)|Especifica el tipo de miembro de datos de conjunto de registros (columna o parámetro) representado por todas las llamadas siguientes a las funciones de RFX hasta la siguiente llamada a `SetFieldType`.|

## <a name="remarks"></a>Observaciones

`CFieldExchange` no tiene una clase base.

Utilice esta clase si está escribiendo rutinas de intercambio de datos para tipos de datos personalizados o si está implementando la obtención masiva de filas; de lo contrario, no se usará directamente esta clase. RFX y RFX masivo intercambian datos entre los miembros de datos de campo del objeto de conjunto de registros y los campos correspondientes del registro actual en el origen de datos.

> [!NOTE]
>  Si está trabajando con las clases de objetos de acceso a datos (DAO) en lugar de las clases de conectividad abierta de bases de datos (ODBC), utilice la clase [CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md) en su lugar. Para obtener más información, vea el artículo [información general sobre la programación de bases de datos](../../data/data-access-programming-mfc-atl.md).

Un objeto `CFieldExchange` proporciona la información de contexto necesaria para que tenga lugar el intercambio de campos de registros o el intercambio masivo de campos de registros. los objetos `CFieldExchange` admiten una serie de operaciones, como los parámetros de enlace y los miembros de datos de campo, y el establecimiento de diversas marcas en los campos del registro actual. Las operaciones RFX y RFX masivo se realizan en miembros de datos de clase de conjunto de registros de tipos definidos por la **enumeración** **FieldType** en `CFieldExchange`. Los valores posibles de **FieldType** son:

- `CFieldExchange::outputColumn` para los miembros de datos de campo.

- `CFieldExchange::inputParam` o `CFieldExchange::param` para los miembros de datos de parámetros de entrada.

- `CFieldExchange::outputParam` para los miembros de datos del parámetro de salida.

- `CFieldExchange::inoutParam` para los miembros de datos de parámetros de entrada y salida.

La mayoría de las funciones miembro y miembros de datos de la clase se proporcionan para escribir sus propias rutinas RFX personalizadas. Usará `SetFieldType` con frecuencia. Para obtener más información, vea los artículos [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md) y [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md). Para obtener información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Para obtener más información sobre las funciones globales de RFX y de RFX masivo, consulte [funciones de intercambio de campos de registros](../../mfc/reference/record-field-exchange-functions.md) en la sección macros y variables globales de MFC de esta referencia.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CFieldExchange`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdb. h

##  <a name="isfieldtype"></a>CFieldExchange:: IsFieldType

Si escribe su propia función RFX, llame a `IsFieldType` al principio de la función para determinar si la operación actual se puede realizar en un tipo de miembro de datos de parámetro o campo determinado (un `CFieldExchange::outputColumn`, `CFieldExchange::inputParam`, `CFieldExchange::param`, `CFieldExchange::outputParam`o `CFieldExchange::inoutParam`).

```
BOOL IsFieldType(UINT* pnField);
```

### <a name="parameters"></a>Parámetros

*pnField*<br/>
En este parámetro se devuelve el número secuencial del miembro de datos de campo o parámetro. Este número corresponde al orden del miembro de datos en la función [CRecordset::D ofieldexchange](../../mfc/reference/crecordset-class.md#dofieldexchange) o [CRecordset::D obulkfieldexchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) .

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación actual se puede realizar en el campo o tipo de parámetro actual.

### <a name="remarks"></a>Observaciones

Siga el modelo de las funciones de RFX existentes.

##  <a name="setfieldtype"></a>CFieldExchange:: SetFieldType

Necesita una llamada a `SetFieldType` en la invalidación [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) o [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) de la clase de conjunto de registros.

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Parámetros

*nFieldType*<br/>
Un valor de la `enum FieldType`, declarado en `CFieldExchange`, que puede ser uno de los siguientes:

- `CFieldExchange::outputColumn`

- `CFieldExchange::inputParam`

- `CFieldExchange::param`

- `CFieldExchange::outputParam`

- `CFieldExchange::inoutParam`

### <a name="remarks"></a>Observaciones

En el caso de los miembros de datos de campo, debe llamar a `SetFieldType` con un parámetro de `CFieldExchange::outputColumn`, seguido de llamadas a las funciones de RFX o de RFX masivo. Si no ha implementado la obtención masiva de filas, ClassWizard coloca esta `SetFieldType` llamada en la sección de asignación de campos de `DoFieldExchange`.

Si realiza la parametrización de la clase de conjunto de registros, debe llamar de nuevo a `SetFieldType`, fuera de cualquier sección de asignación de campo, seguida de llamadas RFX para todos los miembros de datos de parámetro. Cada tipo de miembro de datos de parámetro debe tener su propia llamada `SetFieldType`. En la tabla siguiente se distinguen los distintos valores que se pueden pasar a `SetFieldType` para representar los miembros de datos de parámetro de la clase:

|Valor del parámetro SetFieldType|Tipo de miembro de datos de parámetro|
|----------------------------------|-----------------------------------|
|`CFieldExchange::inputParam`|Parámetro de entrada. Valor que se pasa a la consulta o al procedimiento almacenado del conjunto de registros.|
|`CFieldExchange::param` | igual que `CFieldExchange::inputParam`.|
|`CFieldExchange::outputParam`|Parámetro de salida. Valor devuelto del procedimiento almacenado del conjunto de registros.|
|`CFieldExchange::inoutParam`|Parámetro de entrada/salida. Valor que se pasa al procedimiento almacenado del conjunto de registros y lo devuelve.|

En general, cada grupo de llamadas de función RFX asociadas a miembros de datos de campo o a miembros de datos de parámetro debe ir precedido de una llamada a `SetFieldType`. El parámetro *nFieldType* de cada llamada `SetFieldType` identifica el tipo de los miembros de datos representados por las llamadas de función de RFX que siguen a la llamada a `SetFieldType`.

Para obtener más información sobre el control de los parámetros de salida y de entrada y salida, vea la `CRecordset` función miembro [FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset). Para obtener más información sobre las funciones de RFX y de RFX masivo, vea el tema [funciones de intercambio de campos de registro](../../mfc/reference/record-field-exchange-functions.md). Para obtener información relacionada sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Ejemplo

En este ejemplo se muestran varias llamadas a funciones de RFX con llamadas que acompañan a `SetFieldType`. Tenga en cuenta que se llama a `SetFieldType` a través del puntero `pFX` a un objeto `CFieldExchange`.

[!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)
