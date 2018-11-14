---
title: IDBSchemaRowsetImpl (clase)
ms.date: 11/04/2016
f1_keywords:
- IDBSchemaRowsetImpl
- CheckRestrictions
- IDBSchemaRowsetImpl::CheckRestrictions
- IDBSchemaRowsetImpl.CheckRestrictions
- IDBSchemaRowsetImpl::CreateSchemaRowset
- ATL::IDBSchemaRowsetImpl::CreateSchemaRowset
- CreateSchemaRowset
- IDBSchemaRowsetImpl.CreateSchemaRowset
- ATL.IDBSchemaRowsetImpl.CreateSchemaRowset
- IDBSchemaRowsetImpl::SetRestrictions
- SetRestrictions
- IDBSchemaRowsetImpl.SetRestrictions
- ATL::IDBSchemaRowsetImpl::GetRowset
- ATL.IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl<SessionClass>::GetRowset
- IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl::GetRowset
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetRowset
- GetRowset
- ATL::IDBSchemaRowsetImpl::GetSchemas
- GetSchemas
- IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- ATL.IDBSchemaRowsetImpl.GetSchemas
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- IDBSchemaRowsetImpl.GetSchemas
- IDBSchemaRowsetImpl::GetSchemas
helpviewer_keywords:
- IDBSchemaRowsetImpl class
- CheckRestrictions method
- CreateSchemaRowset method
- SetRestrictions method
- GetRowset method
- GetSchemas method
ms.assetid: bd7bf0d7-a1c6-4afa-88e3-cfdbdf560703
ms.openlocfilehash: d9b0c5319c7eacbb2b5b4d40d5a936e680e82a89
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556938"
---
# <a name="idbschemarowsetimpl-class"></a>IDBSchemaRowsetImpl (clase)

Proporciona la implementación de conjuntos de filas de esquema.

## <a name="syntax"></a>Sintaxis

```cpp
template <class SessionClass>
class ATL_NO_VTABLE IDBSchemaRowsetImpl : public IDBSchemaRowset
```

### <a name="parameters"></a>Parámetros

*SessionClass*<br/>
La clase por la que `IDBSchemaRowsetImpl` se hereda. Normalmente, esta clase será la clase de sesión del usuario.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[CheckRestrictions](#checkrestrictions)|Comprueba la validez de las restricciones en un conjunto de filas de esquema.|
|[CreateSchemaRowset](#createschemarowset)|Implementa una función de creación de objetos COM para el objeto especificado por el parámetro de la plantilla.|
|[SetRestrictions](#setrestrictions)|Especifica qué restricciones se admiten en un conjunto de filas de esquema determinado.|

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[GetRowset](#getrowset)|Devuelve un conjunto de filas de esquema.|
|[GetSchemas](#getschemas)|Devuelve una lista de conjuntos de filas de esquema accesibles por [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md).|

## <a name="remarks"></a>Comentarios

Esta clase implementa la interfaz [IDBSchemaRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms713686(v=vs.85)) y la función de creador de plantillas [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md).

OLE DB usa conjuntos de filas de esquema para devolver datos sobre los datos de un proveedor. Estos datos se suelen denominar "metadatos". De forma predeterminada, un proveedor siempre debe admitir `DBSCHEMA_TABLES`, `DBSCHEMA_COLUMNS`, y `DBSCHEMA_PROVIDER_TYPES`, tal y como se describe en [IDBSchemaRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms713686(v=vs.85)) en el *referencia del programador de OLE DB*. Conjuntos de filas de esquema se designan en una asignación de esquema. Para obtener información sobre las entradas de asignación de esquema, vea [SCHEMA_ENTRY](../../data/oledb/schema-entry.md).

El Asistente para proveedores OLE DB, en el Asistente para objetos ATL, genera automáticamente el código para los conjuntos de filas de esquema en el proyecto. (De forma predeterminada, el asistente admite conjuntos de filas de esquema obligatorios mencionados anteriormente). Cuando crea un consumidor mediante el Asistente para objetos ATL, el asistente usa conjuntos de filas de esquema para enlazar los datos correctos a un proveedor. Si no implementa los conjuntos de filas de esquema para proporcionar los metadatos correctos, el asistente no enlazará los datos correctos.

Para obtener más información sobre la compatibilidad del proveedor con los conjuntos de filas de esquema, vea [Admitir conjuntos de filas de esquema](../../data/oledb/supporting-schema-rowsets.md).

Para obtener más información sobre los conjuntos de filas de esquema, vea [Conjuntos de filas de esquema](https://docs.microsoft.com/previous-versions/windows/desktop/ms712921(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="checkrestrictions"></a> IDBSchemaRowsetImpl:: CheckRestrictions

Comprueba la validez de las restricciones en un conjunto de filas de esquema.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CheckRestrictions(REFGUID rguidSchema,
   ULONG cRestrictions,  const VARIANT rgRestrictions[]);
```

#### <a name="parameters"></a>Parámetros

*rguidSchema*<br/>
[in] Referencia al GUID del conjunto de filas de esquema solicitado (por ejemplo, `DBSCHEMA_TABLES`).

*cRestrictions*<br/>
[in] Número de restricciones que el consumidor pasó para el conjunto de filas de esquema.

*rgRestrictions*<br/>
[in] Matriz de longitud *cRestrictions* de los valores de restricción que se van a establecer. Para obtener más información, vea la descripción de la *rgRestrictions* parámetro [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).

### <a name="remarks"></a>Comentarios

Use `CheckRestrictions` para comprobar la validez de las restricciones en un conjunto de filas de esquema. Comprueba las restricciones para `DBSCHEMA_TABLES`, `DBSCHEMA_COLUMNS`, y `DBSCHEMA_PROVIDER_TYPES` conjuntos de filas de esquema. Llámelo para determinar si un consumidor de la llamada a `IDBSchemaRowset::GetRowset` es correcta. Si quiere admitir conjuntos de filas de esquema distintos de los mencionados anteriormente, debe crear su propia función para llevar a cabo esta tarea.

`CheckRestrictions` Determina si el consumidor llama a [GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) con la restricción correcta y el tipo de restricción correcto (por ejemplo, VT_BSTR una cadena) que admite el proveedor. También determina si se admite el número correcto de restricciones. De forma predeterminada, `CheckRestrictions` le preguntará al proveedor mediante la llamada [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) cuáles son las restricciones que admite en un conjunto de filas determinado. Después, compara las restricciones del consumidor con las que admite el proveedor y la operación se realiza correctamente o bien se produce un error.

Para obtener más información sobre los conjuntos de filas de esquema, vea [IDBSchemaRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms713686(v=vs.85)) en el *referencia del programador de OLE DB* en el SDK de Windows.

## <a name="createschemarowset"></a> IDBSchemaRowsetImpl:: CreateSchemaRowset

Implementa una función de creación de objetos COM para el objeto especificado por el parámetro de la plantilla.

### <a name="syntax"></a>Sintaxis

```cpp
template template <class SchemaRowsetClass>
HRESULT CreateSchemaRowset(IUnknown *pUnkOuter,
   ULONG cRestrictions,
   const VARIANT rgRestrictions[],
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset,
   SchemaRowsetClass*& pSchemaRowset);
```

#### <a name="parameters"></a>Parámetros

*pUnkOuter*<br/>
[in] Un exterior [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) al agregar; en caso contrario, NULL.

*cRestrictions*<br/>
[in] El recuento de restricciones aplicado al conjunto de filas de esquema.

*rgRestrictions*<br/>
[in] Una matriz de `cRestrictions`**VARIANT**se aplicará al conjunto de filas.

*riid*<br/>
[in] La interfaz a [QueryInterface](../../atl/queryinterface.md) para en la salida `IUnknown`.

*cPropertySets*<br/>
[in] Número de conjuntos de propiedad que se van a establecer.

*rgPropertySets*<br/>
[in] Una matriz de estructuras [DBPROPSET](https://docs.microsoft.com/previous-versions/windows/desktop/ms714367(v=vs.85)) que especifica las propiedades que se están estableciendo.

*ppRowset*<br/>
[out] Salida `IUnknown` solicitado por *riid*. Esto `IUnknown` es una interfaz en el objeto de conjunto de filas de esquema.

*pSchemaRowset*<br/>
[out] Un puntero a una instancia de la clase de conjunto de filas de esquema. Normalmente, este parámetro no se usa, pero se puede usar si debe realizar más trabajo en el conjunto de filas de esquema antes de entregarlo a un objeto COM. La duración de *pSchemaRowset* está limitado por *ppRowset*.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Esta función implementa un creador genérico para todos los tipos de conjuntos de filas de esquema. Normalmente, el usuario no llama a esta función. Se llama mediante la implementación de la asignación de esquema.

## <a name="setrestrictions"></a> IDBSchemaRowsetImpl:: SetRestrictions

Especifica qué restricciones se admiten en un conjunto de filas de esquema determinado.

### <a name="syntax"></a>Sintaxis

```cpp
void SetRestrictions(ULONG cRestrictions,
   GUID* /* rguidSchema */,
   ULONG* rgRestrictions);
```

#### <a name="parameters"></a>Parámetros

*cRestrictions*<br/>
[in] El número de restricciones en el *rgRestrictions* matriz y el número de GUID en la *rguidSchema* matriz.

*rguidSchema*<br/>
[in] Una matriz de GUID de conjuntos de filas de esquema para los que se deben obtener restricciones. Cada elemento de la matriz contiene el GUID de un conjunto de filas de esquema (por ejemplo, `DBSCHEMA_TABLES`).

*rgRestrictions*<br/>
[in] Matriz de longitud *cRestrictions* de los valores de restricción que se van a establecer. Cada elemento corresponde a las restricciones en el conjunto de filas de esquema identificado por el GUID. Si el proveedor no admite un conjunto de filas de esquema, el elemento se establece en cero. De otro modo, el valor de **ULONG** contiene una máscara de bits que representa las restricciones admitidas en ese conjunto de filas de esquema. Para obtener más información sobre qué restricciones corresponden a un conjunto de filas de esquema determinado, consulte la tabla del conjunto de filas de esquema GUID en [IDBSchemaRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms713686(v=vs.85)) en el *referencia del programador de OLE DB* en el Windows SDK DE.

### <a name="remarks"></a>Comentarios

El `IDBSchemaRowset` de objeto llama `SetRestrictions` para determinar qué restricciones se admiten en un conjunto de filas de esquema determinado (se llama mediante [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) mediante un puntero de conversión hacia arriba). Las restricciones permiten a los clientes obtener solo las filas coincidentes (por ejemplo, buscar todas las columnas de la tabla "MyTable"). Las restricciones son opcionales y, en caso de que no se admita ninguna (comportamiento predeterminado), se devuelven siempre todos los datos.

La implementación predeterminada de este método establece el *rgRestrictions* elementos en 0 de la matriz. Reemplace el valor predeterminado en la clase de sesión para establecer restricciones distintas de las predeterminadas.

Para obtener información sobre cómo implementar la compatibilidad de conjunto de filas de esquema, vea [Admitir conjuntos de filas de esquema](../../data/oledb/supporting-schema-rowsets.md).

Para obtener un ejemplo de un proveedor que admite conjuntos de filas de esquema, vea el ejemplo [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) .

Para obtener más información sobre los conjuntos de filas de esquema, vea [IDBSchemaRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms713686(v=vs.85)) en el *referencia del programador de OLE DB* en el SDK de Windows.

## <a name="getrowset"></a> IDBSchemaRowsetImpl:: GetRowset

Devuelve un conjunto de filas de esquema.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (GetRowset)(IUnknown *pUnkOuter,
   REFGUID rguidSchema,
   ULONG cRestrictions,
   const VARIANT rgRestrictions[],
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown **ppRowset);
```

#### <a name="parameters"></a>Parámetros

*pUnkOuter*<br/>
[in] Un exterior `IUnknown` al agregar; de lo contrario, NULL.

*rguidSchema*<br/>
[in] Referencia al GUID del conjunto de filas de esquema solicitado (por ejemplo, `DBSCHEMA_TABLES`).

*cRestrictions*<br/>
[in] Recuento de restricciones que se aplicarán al conjunto de filas.

*rgRestrictions*<br/>
[in] Matriz de `cRestrictions`**cRestrictions**que representa las restricciones.

*riid*<br/>
[in] IID que se va a solicitar del conjunto de filas de esquema recién creado.

*cPropertySets*<br/>
[in] Número de conjuntos de propiedad que se van a establecer.

*rgPropertySets*<br/>
[in/out] Matriz de estructuras [DBPROPSET](https://docs.microsoft.com/previous-versions/windows/desktop/ms714367(v=vs.85)) que se van a establecer en el conjunto de filas de esquema recién creado.

*ppRowset*<br/>
[out] Puntero a la interfaz solicitada en el conjunto de filas de esquema recién creado.

### <a name="remarks"></a>Comentarios

Este método exige que el usuario tenga una asignación de esquema en la clase de sesión. Con la información de asignación de esquema `GetRowset` crea un objeto de conjunto de filas determinado si el *rguidSchema* parámetro es igual a uno de los GUID de las entradas de mapa. Vea [SCHEMA_ENTRY](../../data/oledb/schema-entry.md) para obtener una descripción de la entrada de asignación.

Consulte [IDBSchemaRowset:: GetRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms722634(v=vs.85)) en el SDK de Windows.

## <a name="getschemas"></a> IDBSchemaRowsetImpl:: GetSchemas

Devuelve una lista de conjuntos de filas de esquema accesibles por [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md).

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (GetSchema s )(ULONG * pcSchemas,
   GUID ** prgSchemas,
   ULONG** prgRest);
```

#### <a name="parameters"></a>Parámetros

*pcSchemas*<br/>
[out] Puntero a un **ULONG** que se rellena con el número de esquemas.

*prgSchemas*<br/>
[out] Puntero a una matriz de GUID que se rellena con un puntero a una matriz de GUID de conjuntos de filas de esquema.

*prgRest*<br/>
[out] Puntero a una matriz de **ULONG**que se va a rellenar con la matriz de restricciones.

### <a name="remarks"></a>Comentarios

Este método devuelve una matriz de todos los conjuntos de filas de esquema admitidos por el proveedor. Consulte [IDBSchemaRowset:: GetSchemas](https://docs.microsoft.com/previous-versions/windows/desktop/ms719605(v=vs.85)) en el SDK de Windows.

La implementación de esta función exige que el usuario tenga una asignación de esquema en la clase de sesión. Luego, con la información de la asignación de esquema, responde con la matriz de GUID de los esquemas de la asignación. Representa los esquemas admitidos por el proveedor.

## <a name="see-also"></a>Vea también

[Clases de conjunto de filas de esquema y clases typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)<br/>
[Admitir conjuntos de filas de esquema](../../data/oledb/supporting-schema-rowsets.md)<br/>
[SCHEMA_ENTRY](../../data/oledb/schema-entry.md)<br/>
[UpdatePV](https://github.com/Microsoft/VCSamples)