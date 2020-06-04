---
title: IDBPropertiesImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- IDBPropertiesImpl
- ATL.IDBPropertiesImpl
- ATL.IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl
- IDBPropertiesImpl::GetProperties
- IDBPropertiesImpl.GetProperties
- IDBPropertiesImpl::GetPropertyInfo
- IDBPropertiesImpl.GetPropertyInfo
- GetPropertyInfo
- IDBPropertiesImpl.SetProperties
- IDBPropertiesImpl::SetProperties
helpviewer_keywords:
- IDBPropertiesImpl class
- GetProperties method
- GetPropertyInfo method
- SetProperties method
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
ms.openlocfilehash: f873ec4f4eca434d0eb76df86c0891f1a99c2e2c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210709"
---
# <a name="idbpropertiesimpl-class"></a>IDBPropertiesImpl (Clase)

Proporciona una implementación para la interfaz `IDBProperties`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
class ATL_NO_VTABLE IDBPropertiesImpl
   : public IDBProperties, public CUtlProps<T>
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IDBPropertiesImpl`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[GetProperties](#getproperties)|Devuelve los valores de las propiedades en el origen de datos, la información de origen de datos y los grupos de propiedades de inicialización que están establecidos actualmente en el objeto de origen de datos o los valores de las propiedades en el grupo de propiedades de inicialización que están establecidos actualmente en el avanzó.|
|[GetPropertyInfo](#getpropertyinfo)|Devuelve información sobre todas las propiedades admitidas por el proveedor.|
|[SetProperties](#setproperties)|Establece las propiedades del origen de datos y los grupos de propiedades de inicialización, para los objetos de origen de datos o el grupo de propiedades de inicialización, para los enumeradores.|

## <a name="remarks"></a>Observaciones

[IDBProperties](/previous-versions/windows/desktop/ms719607(v=vs.85)) es una interfaz obligatoria para los objetos de origen de datos y una interfaz opcional para los enumeradores. Sin embargo, si un enumerador expone [IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85)), debe exponer `IDBProperties`. `IDBPropertiesImpl` implementa `IDBProperties` mediante el uso de una función estática definida por [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

## <a name="idbpropertiesimplgetproperties"></a><a name="getproperties"></a>Idbpropertiesimpl (:: GetProperties

Devuelve los valores de las propiedades en el origen de datos, la información de origen de datos y los grupos de propiedades de inicialización que están establecidos actualmente en el objeto de origen de datos o los valores de las propiedades en el grupo de propiedades de inicialización que están establecidos actualmente en el avanzó.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetProperties)(ULONG cPropertySets,
   const DBPROPIDSET rgPropertySets[],
   ULONG * pcProperties,
   DBPROPSET ** prgProperties);
```

#### <a name="parameters"></a>Parámetros

Vea [IDBProperties:: GetProperties](/previous-versions/windows/desktop/ms714344(v=vs.85)) en la *Referencia del programador de OLE DB*.

Algunos parámetros corresponden a los parámetros de *Referencia del programador de OLE DB* de nombres diferentes, que se describen en `IDBProperties::GetProperties`:

|OLE DB de los parámetros de plantilla|Parámetros *de referencia del programador de OLE DB*|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|
|*pcProperties*|*pcPropertySets*|
|*prgProperties*|*prgPropertySets*|

### <a name="remarks"></a>Observaciones

Si se inicializa el proveedor, este método devuelve los valores de las propiedades en el DBPROPSET_DATASOURCE, DBPROPSET_DATASOURCEINFO DBPROPSET_DBINIT los grupos de propiedades que están establecidos actualmente en el objeto de origen de datos. Si el proveedor no está inicializado, solo devolverá DBPROPSET_DBINIT propiedades del grupo.

## <a name="idbpropertiesimplgetpropertyinfo"></a><a name="getpropertyinfo"></a>Idbpropertiesimpl (:: GetPropertyInfo

Devuelve la información de propiedad que admite el origen de datos.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetPropertyInfo)(ULONG cPropertySets,
   const DBPROPIDSET rgPropertySets[],
   ULONG * pcPropertyInfoSets,
   DBPROPINFOSET ** prgPropertyInfoSets,
   OLECHAR ** ppDescBuffer);
```

#### <a name="parameters"></a>Parámetros

Vea [IDBProperties:: GetPropertyInfo](/previous-versions/windows/desktop/ms718175(v=vs.85)) en la *Referencia del programador de OLE DB*.

Algunos parámetros corresponden a los parámetros de *Referencia del programador de OLE DB* de nombres diferentes, que se describen en `IDBProperties::GetPropertyInfo`:

|OLE DB de los parámetros de plantilla|Parámetros *de referencia del programador de OLE DB*|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|

### <a name="remarks"></a>Observaciones

Usa [IDBInitializeImpl:: m_pCUtlPropInfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md) para implementar esta funcionalidad.

## <a name="idbpropertiesimplsetproperties"></a><a name="setproperties"></a>Idbpropertiesimpl (:: SetProperties

Establece las propiedades del origen de datos y los grupos de propiedades de inicialización, para los objetos de origen de datos o el grupo de propiedades de inicialización, para los enumeradores.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Parámetros

Vea [IDBProperties:: SetProperties](/previous-versions/windows/desktop/ms723049(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="remarks"></a>Observaciones

Si se inicializa el proveedor, este método establece los valores de las propiedades de los grupos de propiedades DBPROPSET_DATASOURCE, DBPROPSET_DATASOURCEINFO DBPROPSET_DBINIT para el objeto de origen de datos. Si el proveedor no está inicializado, solo establece DBPROPSET_DBINIT propiedades del grupo.

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
