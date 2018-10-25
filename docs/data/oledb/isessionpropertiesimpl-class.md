---
title: ISessionPropertiesImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ISessionPropertiesImpl
- ISessionPropertiesImpl::GetProperties
- ISessionPropertiesImpl.GetProperties
- GetProperties
- ISessionPropertiesImpl.SetProperties
- SetProperties
- ISessionPropertiesImpl::SetProperties
dev_langs:
- C++
helpviewer_keywords:
- ISessionPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9880da2737ddd58d6521712252906c1431955173
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052907"
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl (Clase)

Proporciona una implementación de la [ISessionProperties](/previous-versions/windows/desktop/ms713721) interfaz.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ISessionPropertiesImpl :
   public ISessionProperties,  
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `ISessionPropertiesImpl`.

*PropClass*<br/>
Una clase de propiedad definidos por el usuario que el valor predeterminado es *T*.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Miembros

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[GetProperties](#getproperties)|Devuelve la lista de propiedades en el grupo de propiedades de sesión están establecidas actualmente en la sesión.|
|[SetProperties](#setproperties)|Establece las propiedades en el grupo de propiedades de la sesión.|

## <a name="remarks"></a>Comentarios

Una interfaz obligatoria en las sesiones. Esta clase implementa las propiedades de la sesión mediante una llamada a una función estática definida por el [mapa del conjunto de propiedades](../../data/oledb/begin-propset-map.md). La asignación de conjunto de propiedades se debe especificar en la clase de sesión.

## <a name="getproperties"></a> Isessionpropertiesimpl:: GetProperties

Devuelve la lista de propiedades en el `DBPROPSET_SESSION` grupo de propiedades que están establecidas actualmente en la sesión.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetProperties)(ULONG cPropertyIDSets, 
   const DBPROPIDSET rgPropertyIDSets[], 
   ULONG * pcPropertySets, 
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>Parámetros

Consulte [ISessionProperties::GetProperties](/previous-versions/windows/desktop/ms723643) en el *referencia del programador OLE DB*.

## <a name="setproperties"></a> Isessionpropertiesimpl:: SetProperties

Establece las propiedades en el `DBPROPSET_SESSION` grupo de propiedades.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets, 
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Parámetros

Consulte [ISessionProperties::SetProperties](/previous-versions/windows/desktop/ms714405) en el *referencia del programador OLE DB*.

## <a name="see-also"></a>Vea también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)