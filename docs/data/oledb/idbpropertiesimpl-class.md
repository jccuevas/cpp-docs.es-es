---
title: IDBPropertiesImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBPropertiesImpl
- ATL.IDBPropertiesImpl
- ATL.IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl
- IDBPropertiesImpl::GetProperties
- IDBPropertiesImpl.GetProperties
- GetProperties
- IDBPropertiesImpl::GetPropertyInfo
- IDBPropertiesImpl.GetPropertyInfo
- GetPropertyInfo
- IDBPropertiesImpl.SetProperties
- SetProperties
- IDBPropertiesImpl::SetProperties
dev_langs:
- C++
helpviewer_keywords:
- IDBPropertiesImpl class
- GetProperties method
- GetPropertyInfo method
- SetProperties method
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fc27506657e1e2eeb7fdb7d0d5ef9147d5442dbc
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060799"
---
# <a name="idbpropertiesimpl-class"></a>IDBPropertiesImpl (Clase)

Proporciona una implementación para el `IDBProperties` interfaz.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
class ATL_NO_VTABLE IDBPropertiesImpl
   : public IDBProperties, public CUtlProps<T>
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IDBPropertiesImpl`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Miembros

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[GetProperties](#getproperties)|Devuelve los valores de propiedades de los grupos de propiedades de inicialización, información de origen de datos y origen de datos que actualmente se establecen en el objeto de origen de datos o los valores de propiedades en el grupo de propiedades de inicialización que actualmente se establecen en el enumerador.|
|[GetPropertyInfo](#getpropertyinfo)|Devuelve información sobre todas las propiedades admitidas por el proveedor.|
|[SetProperties](#setproperties)|Establece propiedades en los grupos de propiedades origen de datos y la inicialización de objetos de origen de datos, o el grupo de propiedades de inicialización para los enumeradores.|

## <a name="remarks"></a>Comentarios

[IDBProperties](/previous-versions/windows/desktop/ms719607) es una interfaz obligatoria para los objetos de origen de datos y una interfaz opcional para los enumeradores. Sin embargo, si expone un enumerador [IDBInitialize](/previous-versions/windows/desktop/ms713706), debe exponer `IDBProperties`. `IDBPropertiesImpl` implementa `IDBProperties` mediante el uso de una función estática definida por [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

## <a name="getproperties"></a> Idbpropertiesimpl:: GetProperties

Devuelve los valores de propiedades de los grupos de propiedades de inicialización, información de origen de datos y origen de datos que actualmente se establecen en el objeto de origen de datos o los valores de propiedades en el grupo de propiedades de inicialización que actualmente se establecen en el enumerador.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetProperties)(ULONG cPropertySets, 
   const DBPROPIDSET rgPropertySets[], 
   ULONG * pcProperties, 
   DBPROPSET ** prgProperties);
```

#### <a name="parameters"></a>Parámetros

Consulte [IDBProperties:: GetProperties](/previous-versions/windows/desktop/ms714344) en el *referencia del programador OLE DB*.

Algunos parámetros se corresponden con *referencia del programador de OLE DB* parámetros de nombres diferentes, que se describen en `IDBProperties::GetProperties`:

|Parámetros de plantilla OLE DB|*Referencia del programador de OLE DB* parámetros|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|
|*pcProperties*|*pcPropertySets*|
|*prgProperties*|*prgPropertySets*|

### <a name="remarks"></a>Comentarios

Si se inicializa el proveedor, este método devuelve los valores de propiedades en el DBPROPSET_DATASOURCE, DBPROPSET_DATASOURCEINFO, grupos de propiedades DBPROPSET_DBINIT que actualmente se establecen en el objeto de origen de datos. Si no se ha inicializado el proveedor, devuelve solo las propiedades de grupo DBPROPSET_DBINIT.

## <a name="getpropertyinfo"></a> Idbpropertiesimpl:: GetPropertyInfo

Devuelve información de propiedad admitida por el origen de datos.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetPropertyInfo)(ULONG cPropertySets, 
   const DBPROPIDSET rgPropertySets[], 
   ULONG * pcPropertyInfoSets, 
   DBPROPINFOSET ** prgPropertyInfoSets, 
   OLECHAR ** ppDescBuffer);
```

#### <a name="parameters"></a>Parámetros

Consulte [IDBProperties:: GetPropertyInfo](/previous-versions/windows/desktop/ms718175) en el *referencia del programador OLE DB*.

Algunos parámetros se corresponden con *referencia del programador de OLE DB* parámetros de nombres diferentes, que se describen en `IDBProperties::GetPropertyInfo`:

|Parámetros de plantilla OLE DB|*Referencia del programador de OLE DB* parámetros|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cPropertyIDSets*|
|*rgPropertySets*|*rgPropertyIDSets*|

### <a name="remarks"></a>Comentarios

Usa [idbinitializeimpl:: M_pcutlpropinfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md) para implementar esta funcionalidad.

## <a name="setproperties"></a> Idbpropertiesimpl:: SetProperties

Establece propiedades en los grupos de propiedades origen de datos y la inicialización de objetos de origen de datos, o el grupo de propiedades de inicialización para los enumeradores.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets, 
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Parámetros

Consulte [IDBProperties:: SetProperties](/previous-versions/windows/desktop/ms723049) en el *referencia del programador OLE DB*.

### <a name="remarks"></a>Comentarios

Si se inicializa el proveedor, este método establece los valores de propiedades en el DBPROPSET_DATASOURCE, DBPROPSET_DATASOURCEINFO, grupos de propiedades DBPROPSET_DBINIT para el objeto de origen de datos. Si no se ha inicializado el proveedor, Establece propiedades de grupo DBPROPSET_DBINIT solo.

## <a name="see-also"></a>Vea también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)