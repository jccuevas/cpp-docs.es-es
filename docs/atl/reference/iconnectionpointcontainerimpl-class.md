---
title: IConnectionPointContainerImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl::EnumConnectionPoints
- ATLCOM/ATL::IConnectionPointContainerImpl::FindConnectionPoint
dev_langs:
- C++
helpviewer_keywords:
- connectable objects
- connection points [C++], container
- IConnectionPointContainerImpl class
ms.assetid: 10db5a8d-8be9-4d9d-8a82-8ab9ffe3e9d6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d70989be8e8535336c831cb59fb9422c6e2c63e0
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37886237"
---
# <a name="iconnectionpointcontainerimpl-class"></a>IConnectionPointContainerImpl (clase)
Esta clase implementa un contenedor de punto de conexión para administrar una colección de [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) objetos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>  
class ATL_NO_VTABLE IConnectionPointContainerImpl 
   : public IConnectionPointContainer
```  
  
#### <a name="parameters"></a>Parámetros  
 *T*  
 La clase derivada de `IConnectionPointContainerImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|Crea un enumerador para recorrer en iteración los puntos de conexión admitidos en el objeto conectable.|  
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|Recupera un puntero de interfaz al punto de conexión que admite el IID especificado.|  
  
## <a name="remarks"></a>Comentarios  
 `IConnectionPointContainerImpl` implementa un contenedor de punto de conexión para administrar una colección de [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) objetos. `IConnectionPointContainerImpl` proporciona dos métodos que un cliente puede llamar para recuperar más información acerca de un objeto conectable:  
  
- `EnumConnectionPoints` permite al cliente determinar qué tipo de salida el objeto admite las interfaces.  
  
- `FindConnectionPoint` permite al cliente determinar si el objeto admite una interfaz de salida específica.  
  
 Para obtener información sobre el uso de puntos de conexión en ATL, vea el artículo [puntos de conexión](../../atl/atl-connection-points.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IConnectionPointContainer`  
  
 `IConnectionPointContainerImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="enumconnectionpoints"></a>  IConnectionPointContainerImpl::EnumConnectionPoints  
 Crea un enumerador para recorrer en iteración los puntos de conexión admitidos en el objeto conectable.  
  
```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IConnectionPointContainer:: EnumConnectionPoints](http://msdn.microsoft.com/library/windows/desktop/ms682460) en el SDK de Windows.  
  
##  <a name="findconnectionpoint"></a>  IConnectionPointContainerImpl::FindConnectionPoint  
 Recupera un puntero de interfaz al punto de conexión que admite el IID especificado.  
  
```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IConnectionPointContainer:: FindConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms692476) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)   
 [Información general de clases](../../atl/atl-class-overview.md)
