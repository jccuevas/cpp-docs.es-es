---
title: Clase IPropertyNotifySinkCP | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: feff2467d6d72e9d0a9186dc269f48eb26cbfee2
ms.lasthandoff: 03/17/2017

---
# <a name="ipropertynotifysinkcp-class"></a>Clase IPropertyNotifySinkCP
Esta clase expone [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interfaz como interfaz de salida en un objeto conectable.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
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
 Una clase que administra las conexiones entre un punto de conexión y sus receptores. El valor predeterminado es [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), lo que permite conexiones ilimitadas. También puede usar [CComUnkArray](../../atl/reference/ccomunkarray-class.md), que especifica un número fijo de conexiones.  
  
## <a name="remarks"></a>Comentarios  
 `IPropertyNotifySinkCP`hereda todos los métodos a través de su clase base, [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).  
  
 El [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interfaz permite que un objeto receptor recibir notificaciones acerca de los cambios de propiedad. Clase `IPropertyNotifySinkCP` expone esta interfaz como interfaz de salida en un objeto conectable. El cliente debe implementar la `IPropertyNotifySink` métodos en el receptor.  
  
 Derive la clase de `IPropertyNotifySinkCP` cuando desee crear un punto de conexión que representa el `IPropertyNotifySink` interfaz.  
  
 Para obtener más información acerca del uso de puntos de conexión en ATL, vea el artículo [puntos de conexión](../../atl/atl-connection-points.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
## <a name="see-also"></a>Vea también  
 [Clase IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)   
 [Clase IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

