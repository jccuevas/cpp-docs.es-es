---
title: Clase IPropertyNotifySinkCP | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
dev_langs: C++
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 91e2bcff0b168e9238351cff623f888221b583b2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ipropertynotifysinkcp-class"></a>Clase IPropertyNotifySinkCP
Esta clase expone [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interfaz como una interfaz de salida en un objeto conectable.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T, class CDV = CComDynamicUnkArray>  
class IPropertyNotifySinkCP 
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```    
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IPropertyNotifySinkCP`.  
  
 `CDV`  
 Una clase que administra las conexiones entre un punto de conexión y sus receptores. El valor predeterminado es [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), lo que permite un número ilimitadas conexiones. También puede usar [CComUnkArray](../../atl/reference/ccomunkarray-class.md), que especifica un número fijo de conexiones.  
  
## <a name="remarks"></a>Comentarios  
 `IPropertyNotifySinkCP`hereda todos los métodos a través de su clase base, [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).  
  
 El [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interfaz permite que un objeto receptor recibir notificaciones acerca de los cambios de propiedad. Clase `IPropertyNotifySinkCP` expone esta interfaz como una interfaz de salida en un objeto conectable. El cliente debe implementar la `IPropertyNotifySink` métodos en el receptor.  
  
 Derive la clase de `IPropertyNotifySinkCP` cuando desee crear un punto de conexión que representa el `IPropertyNotifySink` interfaz.  
  
 Para obtener más información sobre el uso de puntos de conexión en ATL, vea el artículo [puntos de conexión](../../atl/atl-connection-points.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
## <a name="see-also"></a>Vea también  
 [Clase IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)   
 [Clase IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
