---
title: IPropertyNotifySinkCP (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66fd7b267a70b962bb5c28bb5835bd96d44a92f0
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879194"
---
# <a name="ipropertynotifysinkcp-class"></a>IPropertyNotifySinkCP (clase)
Esta clase expone [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interfaz como una interfaz de salida en un objeto conectable.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T, class CDV = CComDynamicUnkArray>  
class IPropertyNotifySinkCP 
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```    
  
#### <a name="parameters"></a>Parámetros  
 *T*  
 La clase derivada de `IPropertyNotifySinkCP`.  
  
 *VCDTOX*  
 Una clase que administra las conexiones entre un punto de conexión y sus receptores. El valor predeterminado es [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), lo que permite conexiones ilimitadas. También puede usar [CComUnkArray](../../atl/reference/ccomunkarray-class.md), que especifica un número fijo de conexiones.  
  
## <a name="remarks"></a>Comentarios  
 `IPropertyNotifySinkCP` hereda todos los métodos a través de su clase base, [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).  
  
 El [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interfaz permite a un objeto receptor recibir notificaciones sobre cambios de propiedad. Clase `IPropertyNotifySinkCP` expone esta interfaz como una interfaz de salida en un objeto conectable. El cliente debe implementar la `IPropertyNotifySink` métodos en el receptor.  
  
 Derive la clase de `IPropertyNotifySinkCP` cuando desee crear un punto de conexión que representa el `IPropertyNotifySink` interfaz.  
  
 Para obtener más información sobre el uso de puntos de conexión en ATL, vea el artículo [puntos de conexión](../../atl/atl-connection-points.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
## <a name="see-also"></a>Vea también  
 [IConnectionPointImpl (clase)](../../atl/reference/iconnectionpointimpl-class.md)   
 [IConnectionPointContainerImpl (clase)](../../atl/reference/iconnectionpointcontainerimpl-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
