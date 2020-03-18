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
ms.openlocfilehash: cfffebd16c3c1d62dc4084b962c22911e4b46ae5
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426088"
---
# <a name="cdaofieldexchange-class"></a>Clase CDaoFieldExchange

Admite las rutinas de intercambio de campos del registro (DFX) de DAO utilizadas por las clases de base de datos DAO.

DAO es compatible con Office 2013. DAO 3,6 es la versión final y se considera obsoleta.

## <a name="syntax"></a>Sintaxis

```
class CDaoFieldExchange
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoFieldExchange:: IsValidOperation](#isvalidoperation)|Devuelve un valor distinto de cero si la operación actual es adecuada para el tipo de campo que se está actualizando.|
|[CDaoFieldExchange:: SetFieldType](#setfieldtype)|Especifica el tipo de miembro de datos de conjunto de registros (columna o parámetro) representado por todas las llamadas subsiguientes a funciones DFX hasta la siguiente llamada a `SetFieldType`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDaoFieldExchange:: m_nOperation](#m_noperation)|La operación DFX realizada por la llamada actual a la función miembro `DoFieldExchange` del conjunto de registros.|
|[CDaoFieldExchange:: m_prs](#m_prs)|Puntero al conjunto de registros en el que se realizan las operaciones DFX.|

## <a name="remarks"></a>Observaciones

`CDaoFieldExchange` no tiene una clase base.

Utilice esta clase si está escribiendo rutinas de intercambio de datos para tipos de datos personalizados; de lo contrario, no se usará directamente esta clase. DFX intercambia datos entre los miembros de datos de campo del objeto [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) y los campos correspondientes del registro actual en el origen de datos. DFX administra el intercambio en ambas direcciones, desde el origen de datos y hasta el origen de datos. Vea la [Nota técnica 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) para obtener información sobre cómo escribir rutinas DFX personalizadas.

> [!NOTE]
>  Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Conectividad abierta de bases de datos (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Todavía puede obtener acceso a los orígenes de datos ODBC con las clases DAO. En general, las clases MFC basadas en DAO son más capaces que las clases MFC basadas en ODBC. Las clases basadas en DAO pueden tener acceso a los datos, incluidos los controladores ODBC, a través de su propio motor de base de datos. También admiten operaciones de lenguaje de definición de datos (DDL), como agregar tablas a través de las clases en lugar de tener que llamar a DAO personalmente.

> [!NOTE]
>  El intercambio de campos de registros (DFX) de DAO es muy similar al intercambio de campos de registros (RFX) en las clases de base de datos MFC basadas en ODBC (`CDatabase`, `CRecordset`). Si entiende RFX, le resultará fácil usar DFX.

Un objeto `CDaoFieldExchange` proporciona la información de contexto necesaria para que el intercambio de campos de registros DAO tenga lugar. los objetos `CDaoFieldExchange` admiten una serie de operaciones, como los parámetros de enlace y los miembros de datos de campo, y el establecimiento de diversas marcas en los campos del registro actual. Las operaciones DFX se realizan en miembros de datos de clase de conjunto de registros de tipos definidos por la **enumeración** **FieldType** en `CDaoFieldExchange`. Los valores posibles de **FieldType** son:

- `CDaoFieldExchange::outputColumn` para los miembros de datos de campo.

- `CDaoFieldExchange::param` para los miembros de datos de parámetro.

La función miembro [IsValidOperation](#isvalidoperation) se proporciona para escribir sus propias rutinas DFX personalizadas. Usará [SetFieldType](#setfieldtype) con frecuencia en las funciones [CDaoRecordset::D ofieldexchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) . Para obtener más información sobre las funciones globales DFX, consulte [funciones de intercambio de campos de registros](../../mfc/reference/record-field-exchange-functions.md). Para obtener información sobre cómo escribir rutinas DFX personalizadas para sus propios tipos de datos, vea la [Nota técnica 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CDaoFieldExchange`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdao. h

##  <a name="isvalidoperation"></a>CDaoFieldExchange:: IsValidOperation

Si escribe su propia función DFX, llame a `IsValidOperation` al principio de la función para determinar si la operación actual se puede realizar en un tipo de miembro de datos de campo determinado (un `CDaoFieldExchange::outputColumn` o un `CDaoFieldExchange::param`).

```
BOOL IsValidOperation();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación actual es adecuada para el tipo de campo que se está actualizando.

### <a name="remarks"></a>Observaciones

Algunas de las operaciones realizadas por el mecanismo DFX se aplican solo a uno de los tipos de campo posibles. Siga el modelo de las funciones DFX existentes.

Para obtener información adicional sobre cómo escribir rutinas DFX personalizadas, vea la [Nota técnica 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

##  <a name="m_noperation"></a>CDaoFieldExchange:: m_nOperation

Identifica la operación que se va a realizar en el objeto [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) asociado al objeto de intercambio de campo.

### <a name="remarks"></a>Observaciones

El objeto `CDaoFieldExchange` proporciona el contexto para varias operaciones DFX diferentes en el conjunto de registros.

> [!NOTE]
>  El valor PSEUDONULL descrito en las operaciones MarkForAddNew y SetFieldNull siguiente es un valor que se usa para marcar los campos como null. El mecanismo de intercambio de campos de registros (DFX) de DAO usa este valor para determinar qué campos se han marcado explícitamente como null. PSEUDONULL no es necesario para los campos [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) y [COleCurrency](../../mfc/reference/colecurrency-class.md) .

Los valores posibles de `m_nOperation` son:

|Operación|Descripción|
|---------------|-----------------|
|`AddToParameterList`|Compila la cláusula **Parameters** de la instrucción SQL.|
|`AddToSelectList`|Crea la cláusula **Select** de la instrucción SQL.|
|`BindField`|Enlaza un campo de la base de datos a una ubicación de memoria en la aplicación.|
|`BindParam`|Establece los valores de parámetro para la consulta del conjunto de registros.|
|`Fixup`|Establece el estado null de un campo.|
|`AllocCache`|Asigna la memoria caché que se usa para comprobar los campos "sucios" en el conjunto de registros.|
|`StoreField`|Guarda el registro actual en la memoria caché.|
|`LoadField`|Restaura las variables de miembro de datos almacenadas en caché en el conjunto de registros.|
|`FreeCache`|Libera la memoria caché utilizada para comprobar los campos "sucios" en el conjunto de registros.|
|`SetFieldNull`|Establece el estado de un campo en NULL y el valor en PSEUDONULL.|
|`MarkForAddNew`|Marca los campos "sucios" si no se PSEUDONULL.|
|`MarkForEdit`|Marca los campos "sucios" si no coinciden con la memoria caché.|
|`SetDirtyField`|Establece los valores de campo marcados como "sucios".|
|`DumpField`|Vuelca el contenido de un campo (solo depuración).|
|`MaxDFXOperation`|Se usa para la comprobación de entrada.|

##  <a name="m_prs"></a>CDaoFieldExchange:: m_prs

Contiene un puntero al objeto [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) asociado al objeto `CDaoFieldExchange`.

### <a name="remarks"></a>Observaciones

##  <a name="setfieldtype"></a>CDaoFieldExchange:: SetFieldType

Llame a `SetFieldType` en la invalidación de `DoFieldExchange` de la clase `CDaoRecordset`.

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Parámetros

*nFieldType*<br/>
Un valor de la **enumeración FieldType**, declarado en `CDaoFieldExchange`, que puede ser cualquiera de los siguientes:

- `CDaoFieldExchange::outputColumn`

- `CDaoFieldExchange::param`

### <a name="remarks"></a>Observaciones

Normalmente, ClassWizard escribe esta llamada. Si escribe su propia función y está usando el Asistente para escribir la función de `DoFieldExchange`, agregue llamadas a su propia función fuera del mapa de campos. Si no usa el asistente, no habrá ninguna asignación de campo. La llamada precede a las llamadas a funciones DFX, una para cada miembro de datos de campo de la clase e identifica el tipo de campo como `CDaoFieldExchange::outputColumn`.

Si Parametriza la clase de conjunto de registros, debe agregar llamadas DFX para todos los miembros de datos de parámetro (fuera del mapa de campos) y preceder a estas llamadas con una llamada a `SetFieldType`. Pase el valor `CDaoFieldExchange::param`. (En su lugar, puede usar un [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) y establecer sus valores de parámetro).

En general, cada grupo de llamadas a funciones DFX asociadas a miembros de datos de campo o a miembros de datos de parámetro debe ir precedido de una llamada a `SetFieldType`. El parámetro *nFieldType* de cada llamada `SetFieldType` identifica el tipo de los miembros de datos representados por las llamadas a funciones DFX que siguen a la llamada a `SetFieldType`.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset (clase)](../../mfc/reference/cdaorecordset-class.md)
