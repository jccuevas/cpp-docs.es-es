---
title: "Funciones globales de punto de conexión | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
caps.latest.revision: 20
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 8271f512141e4d2cc274d180b31e1ad33bfc354e
ms.lasthandoff: 02/24/2017

---
# <a name="connection-point-global-functions"></a>Funciones globales de punto de conexión
Estas funciones proporcionan compatibilidad para puntos de conexión y mapas de receptor.  
  
> [!IMPORTANT]
>  Las funciones enumeradas en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
|||  
|-|-|  
|[AtlAdvise](#atladvise)|Crea una conexión entre el punto de conexión de un objeto y el receptor de un cliente.|  
|[AtlUnadvise](#atlunadvise)|Finaliza la conexión establecida mediante `AtlAdvise`.|  
|[AtlAdviseSinkMap](#atladvisesinkmap)|Aconseja o desaconseja las entradas de un mapa de receptores de eventos.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
   
##  <a name="a-nameatladvisea--atladvise"></a><a name="atladvise"></a>AtlAdvise  
 Crea una conexión entre el punto de conexión de un objeto y el receptor de un cliente.  
  
> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```  
  
### <a name="parameters"></a>Parámetros  
 `pUnkCP`  
 [in] Un puntero a la **IUnknown** del objeto desea conectar con el cliente.  
  
 *pUnk*  
 [in] Un puntero al cliente **IUnknown**.  
  
 `iid`  
 [in] El GUID del punto de conexión. Normalmente, esto es igual que la interfaz de salida administrada por el punto de conexión.  
  
 `pdw`  
 [out] Puntero a la cookie que identifica de forma única la conexión.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 El receptor implementa la interfaz de salida admitida por el punto de conexión. El cliente utiliza la `pdw` cookies para quitar la conexión pasándolo a [AtlUnadvise](#atlunadvise).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#91;](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]  
  
##  <a name="a-nameatlunadvisea--atlunadvise"></a><a name="atlunadvise"></a>AtlUnadvise  
 Finaliza la conexión establecida mediante [AtlAdvise](#atladvise).  
  
> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```  
  
### <a name="parameters"></a>Parámetros  
 `pUnkCP`  
 [in] Un puntero a la **IUnknown** del objeto que el cliente está conectado con.  
  
 `iid`  
 [in] El GUID del punto de conexión. Normalmente, esto es igual que la interfaz de salida administrada por el punto de conexión.  
  
 `dw`  
 [in] Cookie que identifica de forma única la conexión.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#96;](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]  
  
##  <a name="a-nameatladvisesinkmapa--atladvisesinkmap"></a><a name="atladvisesinkmap"></a>AtlAdviseSinkMap  
 Llame a esta función para notificar o no notificar todas las entradas del mapa de eventos del receptor del objeto.  
  
> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```  
  
### <a name="parameters"></a>Parámetros  
 *pT*  
 [in] Un puntero al objeto que contiene el mapa de receptores.  
  
 `bAdvise`  
 [in] **true** si todas las entradas de receptor a informamos; **false** si todas las entradas de receptor se van desaconsejarán.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing&#92;](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../atl/reference/atl-functions.md)   
 [Macros de punto de conexión](../../atl/reference/connection-point-macros.md)

