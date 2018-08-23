---
title: ICommandPropertiesImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
- ICommandPropertiesImpl::GetProperties
- ICommandPropertiesImpl.GetProperties
- GetProperties
- ICommandPropertiesImpl.SetProperties
- ICommandPropertiesImpl::SetProperties
- SetProperties
dev_langs:
- C++
helpviewer_keywords:
- ICommandPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c2f3f4c32e2e87fdd905949ffd6cebac89a5023a
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42571720"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl (Clase)
Proporciona una implementación de la [ICommandProperties](/previous-versions/windows/desktop/ms723044\(v=vs.85\)) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ICommandPropertiesImpl   
   : public ICommandProperties, public CUtlProps<PropClass>  
```  
  
### <a name="parameters"></a>Parámetros  
 *T*  
 La clase, derivada de  
  
 *PropClass*  
 La clase de propiedades.  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="members"></a>Miembros  
  
### <a name="interface-methods"></a>Métodos de interfaz  
  
|||  
|-|-|  
|[GetProperties](#getproperties)|Devuelve la lista de propiedades en el grupo de propiedades de conjunto de filas que se solicitan actualmente para el conjunto de filas.|  
|[SetProperties](#setproperties)|Establece las propiedades en el grupo de propiedades del conjunto de filas.|  
  
## <a name="remarks"></a>Comentarios  
 Esto es obligatorio en los comandos. Proporciona la implementación de una función estática definida por el [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) macro.  

## <a name="getproperties"></a> Icommandpropertiesimpl:: GetProperties
Devuelve todos los conjuntos de propiedades solicitado mediante la asignación de propiedad del comando.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD(GetProperties)(const ULONG cPropertyIDSets,   
   const DBPROPIDSET rgPropertyIDSets[],   
   ULONG * pcPropertySets,   
   DBPROPSET ** prgPropertySets);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Consulte [ICommandProperties:: GetProperties](/previous-versions/windows/desktop/ms723119\(v=vs.85\)) en el *referencia del programador OLE DB*.  
  
### <a name="remarks"></a>Comentarios  
 Vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="setproperties"></a> Icommandpropertiesimpl:: SetProperties
Establece las propiedades para el objeto de comando.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Consulte [ICommandProperties:: SetProperties](/previous-versions/windows/desktop/ms711497\(v=vs.85\)) en el *referencia del programador OLE DB*.  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)