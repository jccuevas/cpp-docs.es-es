---
title: IConnectionPointImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl::Advise
- ATLCOM/ATL::IConnectionPointImpl::EnumConnections
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionInterface
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionPointContainer
- ATLCOM/ATL::IConnectionPointImpl::Unadvise
- ATLCOM/ATL::IConnectionPointImpl::m_vec
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], implementing
- IConnectionPointImpl class
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cf1f012067c3a3b85dd5168cf93521e4b2024e00
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884053"
---
# <a name="iconnectionpointimpl-class"></a>IConnectionPointImpl (clase)
Esta clase implementa un punto de conexión.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>  
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```  
  
#### <a name="parameters"></a>Parámetros  
 *T*  
 La clase derivada de `IConnectionPointImpl`.  
  
 *piid*  
 Un puntero para el IID de la interfaz representada por el objeto de punto de conexión.  
  
 *VCDTOX*  
 Una clase que administra las conexiones. El valor predeterminado es [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), lo que permite conexiones ilimitadas. También puede usar [CComUnkArray](../../atl/reference/ccomunkarray-class.md), que especifica un número fijo de conexiones.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IConnectionPointImpl::Advise](#advise)|Establece una conexión entre el punto de conexión y un receptor.|  
|[IConnectionPointImpl::EnumConnections](#enumconnections)|Crea un enumerador para recorrer en iteración las conexiones para el punto de conexión.|  
|[IConnectionPointImpl::GetConnectionInterface](#getconnectioninterface)|Recupera el IID de la interfaz representada por el punto de conexión.|  
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|Recupera un puntero de interfaz al objeto conectable.|  
|[IConnectionPointImpl::Unadvise](#unadvise)|Finaliza una conexión previamente establecida mediante `Advise`.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IConnectionPointImpl::m_vec](#m_vec)|Administra las conexiones para el punto de conexión.|  
  
## <a name="remarks"></a>Comentarios  
 `IConnectionPointImpl` implementa un punto de conexión, lo que permite a un objeto exponga una interfaz de salida al cliente. El cliente implementa esta interfaz en un objeto denominado receptor.  
  
 ATL utiliza [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) para implementar el objeto conectable. Cada punto de conexión dentro del objeto conectable representa una interfaz de salida, identificada por *piid*. Clase *VCDtox* administra las conexiones entre el punto de conexión y un receptor. Cada conexión se identifica por una "cookie".  
  
 Para obtener más información sobre el uso de puntos de conexión en ATL, vea el artículo [puntos de conexión](../../atl/atl-connection-points.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `_ICPLocator`  
  
 `IConnectionPointImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
##  <a name="advise"></a>  IConnectionPointImpl::Advise  
 Establece una conexión entre el punto de conexión y un receptor.  
  
```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```  
  
### <a name="remarks"></a>Comentarios  
 Use [Unadvise](#unadvise) para finalizar la llamada de conexión.  
  
 Consulte [IConnectionPoint:: Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815) en el SDK de Windows.  
  
##  <a name="enumconnections"></a>  IConnectionPointImpl::EnumConnections  
 Crea un enumerador para recorrer en iteración las conexiones para el punto de conexión.  
  
```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IConnectionPoint:: EnumConnections](http://msdn.microsoft.com/library/windows/desktop/ms680755) en el SDK de Windows.  
  
##  <a name="getconnectioninterface"></a>  IConnectionPointImpl::GetConnectionInterface  
 Recupera el IID de la interfaz representada por el punto de conexión.  
  
```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IConnectionPoint:: GetConnectionInterface](http://msdn.microsoft.com/library/windows/desktop/ms693468) en el SDK de Windows.  
  
##  <a name="getconnectionpointcontainer"></a>  IConnectionPointImpl::GetConnectionPointContainer  
 Recupera un puntero de interfaz al objeto conectable.  
  
```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IConnectionPoint:: GetConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms679669) en el SDK de Windows.  
  
##  <a name="m_vec"></a>  IConnectionPointImpl::m_vec  
 Administra las conexiones entre el objeto de punto de conexión y un receptor.  
  
```
CDV m_vec;
```     
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `m_vec` es de tipo [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md).  
  
##  <a name="unadvise"></a>  IConnectionPointImpl::Unadvise  
 Finaliza una conexión previamente establecida mediante [Advise](#advise).  
  
```
STDMETHOD(Unadvise)(DWORD dwCookie);
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IConnectionPoint:: Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms686608) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318)   
 [Información general de clases](../../atl/atl-class-overview.md)
