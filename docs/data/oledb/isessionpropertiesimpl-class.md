---
title: ISessionPropertiesImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- ISessionPropertiesImpl
- ISessionPropertiesImpl::GetProperties
- ISessionPropertiesImpl.GetProperties
- ISessionPropertiesImpl.SetProperties
- ISessionPropertiesImpl::SetProperties
helpviewer_keywords:
- ISessionPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
ms.openlocfilehash: 0b36e4f85b855f162e11d96f8fef296c6c07597f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210306"
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl (Clase)

Proporciona una implementación de la interfaz [ISessionProperties](/previous-versions/windows/desktop/ms713721(v=vs.85)) .

## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ISessionPropertiesImpl :
   public ISessionProperties,
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `ISessionPropertiesImpl`.

*PropClass*<br/>
Una clase de propiedad definible por el usuario que tiene como valor predeterminado *T*.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[GetProperties](#getproperties)|Devuelve la lista de propiedades del grupo de propiedades de sesión actualmente establecidas en la sesión.|
|[SetProperties](#setproperties)|Establece las propiedades en el grupo de propiedades de sesión.|

## <a name="remarks"></a>Observaciones

Una interfaz obligatoria en las sesiones. Esta clase implementa las propiedades de la sesión mediante una llamada a una función estática definida por la [asignación del conjunto de propiedades](../../data/oledb/begin-propset-map.md). La asignación del conjunto de propiedades debe especificarse en la clase de sesión.

## <a name="isessionpropertiesimplgetproperties"></a><a name="getproperties"></a>Isessionpropertiesimpl (:: GetProperties

Devuelve la lista de propiedades del `DBPROPSET_SESSION` grupo de propiedades que están establecidas actualmente en la sesión.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetProperties)(ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>Parámetros

Vea [ISessionProperties:: GetProperties](/previous-versions/windows/desktop/ms723643(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="isessionpropertiesimplsetproperties"></a><a name="setproperties"></a>Isessionpropertiesimpl (:: SetProperties

Establece las propiedades del grupo de propiedades `DBPROPSET_SESSION`.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Parámetros

Vea [ISessionProperties:: SetProperties](/previous-versions/windows/desktop/ms714405(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
