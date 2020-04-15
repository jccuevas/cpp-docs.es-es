---
title: Clase CDaoFieldExchange
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldExchange
- AFXDAO/CDaoFieldExchange
- AFXDAO/CDaoFieldExchange::IsValidOperation
- AFXDAO/CDaoFieldExchange::SetFieldType
- AFXDAO/CDaoFieldExchange::m_nOperation
- AFXDAO/CDaoFieldExchange::m_prs
helpviewer_keywords:
- CDaoFieldExchange [MFC], IsValidOperation
- CDaoFieldExchange [MFC], SetFieldType
- CDaoFieldExchange [MFC], m_nOperation
- CDaoFieldExchange [MFC], m_prs
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
ms.openlocfilehash: e1ce6e13b9c6045881cc0bb4114a6e11d58365c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368990"
---
# <a name="cdaofieldexchange-class"></a>Clase CDaoFieldExchange

Admite las rutinas de intercambio de campos del registro (DFX) de DAO utilizadas por las clases de base de datos DAO.

DAO se admite a través de Office 2013. DAO 3.6 es la versión final, y se considera obsoleto.

## <a name="syntax"></a>Sintaxis

```
class CDaoFieldExchange
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|Devuelve distinto de cero si la operación actual es adecuada para el tipo de campo que se va a actualizar.|
|[CDaoFieldExchange::SetFieldType](#setfieldtype)|Especifica el tipo de miembro de datos de conjunto de registros (columna o `SetFieldType`parámetro) representado por todas las llamadas posteriores a funciones DFX hasta la siguiente llamada a .|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoFieldExchange::m_nOperation](#m_noperation)|La operación DFX que realiza la llamada `DoFieldExchange` actual a la función miembro del conjunto de registros.|
|[CDaoFieldExchange::m_prs](#m_prs)|Puntero al conjunto de registros en el que se realizan operaciones DFX.|

## <a name="remarks"></a>Observaciones

`CDaoFieldExchange`no tiene una clase base.

Utilice esta clase si está escribiendo rutinas de intercambio de datos para tipos de datos personalizados; de lo contrario, no utilizará directamente esta clase. DFX intercambia datos entre los miembros de datos de campo del objeto [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) y los campos correspondientes del registro actual en el origen de datos. DFX administra el intercambio en ambas direcciones, desde el origen de datos y hasta el origen de datos. Consulte [la Nota técnica 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) para obtener información sobre cómo escribir rutinas DFX personalizadas.

> [!NOTE]
> Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Todavía puede tener acceso a orígenes de datos ODBC con las clases DAO. En general, las clases MFC basadas en DAO son más capaces que las clases MFC basadas en ODBC. Las clases basadas en DAO pueden tener acceso a los datos, incluso a través de controladores ODBC, a través de su propio motor de base de datos. También admiten operaciones de lenguaje de definición de datos (DDL), como agregar tablas a través de las clases en lugar de tener que llamar a DAO usted mismo.

> [!NOTE]
> El intercambio de campos de registros DAO (DFX) es muy similar al `CDatabase`intercambio `CRecordset`de campos de registros (RFX) en las clases de base de datos MFC basadas en ODBC ( , ). Si entiende RFX, le resultará fácil usar DFX.

Un `CDaoFieldExchange` objeto proporciona la información de contexto necesaria para que se lleve a cabo el intercambio de campos de registros DAO. `CDaoFieldExchange`los objetos admiten una serie de operaciones, incluidos los parámetros de enlace y los miembros de datos de campo y la configuración de varias marcas en los campos del registro actual. Las operaciones DFX se realizan en miembros de datos `CDaoFieldExchange`de clase de conjunto de registros de tipos definidos por **enum** **FieldType** en . Los valores posibles **de FieldType** son:

- `CDaoFieldExchange::outputColumn`para los miembros de datos de campo.

- `CDaoFieldExchange::param`para los miembros de datos de parámetros.

El [IsValidOperation](#isvalidoperation) función miembro se proporciona para escribir sus propias rutinas DFX personalizadas. Usará [SetFieldType](#setfieldtype) con frecuencia en las funciones [CDaoRecordset::DoFieldExchange.](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) Para obtener más información sobre las funciones globales de DFX, vea Funciones de intercambio de campos de [registros](../../mfc/reference/record-field-exchange-functions.md). Para obtener información sobre cómo escribir rutinas DFX personalizadas para sus propios tipos de datos, consulte [Nota técnica 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CDaoFieldExchange`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao.h

## <a name="cdaofieldexchangeisvalidoperation"></a><a name="isvalidoperation"></a>CDaoFieldExchange::IsValidOperation

Si escribe su propia función `IsValidOperation` DFX, llame al principio de la función para determinar si `CDaoFieldExchange::outputColumn` la `CDaoFieldExchange::param`operación actual se puede realizar en un tipo de miembro de datos de campo determinado (a o a ).

```
BOOL IsValidOperation();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación actual es adecuada para el tipo de campo que se va a actualizar.

### <a name="remarks"></a>Observaciones

Algunas de las operaciones realizadas por el mecanismo DFX solo se aplican a uno de los tipos de campo posibles. Siga el modelo de las funciones DFX existentes.

Para obtener información adicional sobre cómo escribir rutinas DFX personalizadas, consulte [Nota técnica 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

## <a name="cdaofieldexchangem_noperation"></a><a name="m_noperation"></a>CDaoFieldExchange::m_nOperation

Identifica la operación que se va a realizar en el [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto asociado con el objeto de intercambio de campos.

### <a name="remarks"></a>Observaciones

El `CDaoFieldExchange` objeto proporciona el contexto para varias operaciones DFX diferentes en el conjunto de registros.

> [!NOTE]
> El valor PSEUDONULL descrito en las operaciones MarkForAddNew y SetFieldNull a continuación es un valor utilizado para marcar los campos Null. El mecanismo de intercambio de campos de registros DAO (DFX) utiliza este valor para determinar qué campos se han marcado explícitamente como Null. PSEUDONULL no es necesario para [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) y [COleCurrency](../../mfc/reference/colecurrency-class.md) campos.

Los valores `m_nOperation` posibles de son:

|Operación|Descripción|
|---------------|-----------------|
|`AddToParameterList`|Crea la cláusula **PARAMETERS** de la instrucción SQL.|
|`AddToSelectList`|Crea la cláusula **SELECT** de la instrucción SQL.|
|`BindField`|Enlaza un campo de la base de datos a una ubicación de memoria de la aplicación.|
|`BindParam`|Establece valores de parámetro para la consulta del conjunto de registros.|
|`Fixup`|Establece el estado Nulo de un campo.|
|`AllocCache`|Asigna la memoria caché utilizada para comprobar si hay campos "sucios" en el conjunto de registros.|
|`StoreField`|Guarda el registro actual en la memoria caché.|
|`LoadField`|Restaura las variables de miembro de datos almacenadas en caché en el conjunto de registros.|
|`FreeCache`|Libera la memoria caché utilizada para comprobar si hay campos "sucios" en el conjunto de registros.|
|`SetFieldNull`|Establece el estado de un campo en Null y value en PSEUDONULL.|
|`MarkForAddNew`|Marca los campos "sucios" si no PSEUDONULL.|
|`MarkForEdit`|Marca los campos "sucios" si no coinciden con la memoria caché.|
|`SetDirtyField`|Establece los valores de campo marcados como "sucios."|
|`DumpField`|Vuelca el contenido de un campo (solo depuración).|
|`MaxDFXOperation`|Se utiliza para la comprobación de entradas.|

## <a name="cdaofieldexchangem_prs"></a><a name="m_prs"></a>CDaoFieldExchange::m_prs

Contiene un puntero a la [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto asociado al `CDaoFieldExchange` objeto.

### <a name="remarks"></a>Observaciones

## <a name="cdaofieldexchangesetfieldtype"></a><a name="setfieldtype"></a>CDaoFieldExchange::SetFieldType

Llama `SetFieldType` a `CDaoRecordset` la `DoFieldExchange` anulación de tu clase.

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Parámetros

*nFieldType*<br/>
Un valor de **enum FieldType**, declarado en `CDaoFieldExchange`, que puede ser cualquiera de los siguientes:

- `CDaoFieldExchange::outputColumn`

- `CDaoFieldExchange::param`

### <a name="remarks"></a>Observaciones

Normalmente, ClassWizard escribe esta llamada por usted. Si escribe su propia función y utiliza `DoFieldExchange` el asistente para escribir la función, agregue llamadas a su propia función fuera del mapa de campo. Si no utiliza el asistente, no habrá un mapa de campo. La llamada precede a las llamadas a funciones DFX, una para `CDaoFieldExchange::outputColumn`cada miembro de datos de campo de la clase, e identifica el tipo de campo como .

Si parametriza la clase de conjunto de registros, debe agregar llamadas DFX para todos los `SetFieldType`miembros de datos de parámetro (fuera del mapa de campos) y preceder estas llamadas con una llamada a . Pase el `CDaoFieldExchange::param`valor . (En su lugar, puede usar un [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) y establecer sus valores de parámetro.)

En general, cada grupo de llamadas a funciones DFX asociadas con `SetFieldType`miembros de datos de campo o miembros de datos de parámetro deben ir precedidos de una llamada a . El *nFieldType* parámetro `SetFieldType` de cada llamada identifica el tipo de los miembros `SetFieldType` de datos representados por las llamadas de función DFX que siguen a la llamada.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)
