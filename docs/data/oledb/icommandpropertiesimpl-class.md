---
title: ICommandPropertiesImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
- ICommandPropertiesImpl::GetProperties
- ICommandPropertiesImpl.GetProperties
- ICommandPropertiesImpl.SetProperties
- ICommandPropertiesImpl::SetProperties
helpviewer_keywords:
- ICommandPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
ms.openlocfilehash: 165f7124657cbaf0c0f94171eaf9394011796aea
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545976"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl (Clase)

Proporciona una implementación de la interfaz [ICommandProperties](/previous-versions/windows/desktop/ms723044(v=vs.85)) .

## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ICommandPropertiesImpl
   : public ICommandProperties, public CUtlProps<PropClass>
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de

*PropClass*<br/>
Clase de propiedades.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[GetProperties](#getproperties)|Devuelve la lista de propiedades del grupo de propiedades de conjunto de filas que se solicitan actualmente para el conjunto de filas.|
|[SetProperties](#setproperties)|Establece las propiedades en el grupo de propiedades de conjunto de filas.|

## <a name="remarks"></a>Observaciones

Esto es obligatorio en los comandos. La implementación la proporciona una función estática definida por la macro [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) .

## <a name="icommandpropertiesimplgetproperties"></a><a name="getproperties"></a>Icommandpropertiesimpl (:: GetProperties

Devuelve todos los conjuntos de propiedades solicitados mediante la asignación de propiedades del comando.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetProperties)(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>Parámetros

Vea [ICommandProperties:: GetProperties](/previous-versions/windows/desktop/ms723119(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="remarks"></a>Observaciones

Consulte [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

## <a name="icommandpropertiesimplsetproperties"></a><a name="setproperties"></a>Icommandpropertiesimpl (:: SetProperties

Establece las propiedades del objeto de comando.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Parámetros

Vea [ICommandProperties:: SetProperties](/previous-versions/windows/desktop/ms711497(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)