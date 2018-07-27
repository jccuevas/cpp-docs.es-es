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
ms.openlocfilehash: 13f170aa27cdc52b98729b0953568575292f6f6b
ms.sourcegitcommit: b0d6777cf4b580d093eaf6104d80a888706e7578
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2018
ms.locfileid: "39269591"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl (Clase)
Proporciona una implementación de la [ICommandProperties](https://msdn.microsoft.com/library/ms723044.aspx) interfaz.  
  
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
 Consulte [ICommandProperties:: GetProperties](https://msdn.microsoft.com/library/ms723119.aspx) en el *referencia del programador OLE DB*.  
  
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
 Consulte [ICommandProperties:: SetProperties](https://msdn.microsoft.com/library/ms711497.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
