---
title: "Funciones globales de punto de conexión | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce7f6fc3d2a0b51f88952dd720955367b1dfe9d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="connection-point-global-functions"></a>Funciones globales de punto de conexión
Estas funciones proporcionan compatibilidad para puntos de conexión y mapas de receptor.  
  
> [!IMPORTANT]
>  Las funciones se enumeran en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
|||  
|-|-|  
|[AtlAdvise](#atladvise)|Crea una conexión entre el punto de conexión de un objeto y el receptor de un cliente.|  
|[AtlUnadvise](#atlunadvise)|Finaliza la conexión establecida a través de `AtlAdvise`.|  
|[AtlAdviseSinkMap](#atladvisesinkmap)|Le informa de o desaconseja las entradas de un mapa de receptores de eventos.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
   
##  <a name="atladvise"></a>AtlAdvise  
 Crea una conexión entre el punto de conexión de un objeto y el receptor de un cliente.  
  
> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```  
  
### <a name="parameters"></a>Parámetros  
 `pUnkCP`  
 [in] Un puntero a la **IUnknown** del objeto que el cliente desea conectarse con.  
  
 *pUnk*  
 [in] Un puntero para el cliente **IUnknown**.  
  
 `iid`  
 [in] El GUID del punto de conexión. Normalmente, esto es igual que la interfaz de salida administrada por el punto de conexión.  
  
 `pdw`  
 [out] Un puntero a la cookie que identifica de forma única la conexión.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 El receptor implementa la interfaz de salida compatible con el punto de conexión. El cliente utiliza la `pdw` cookies para quitar la conexión y la transfiere a [AtlUnadvise](#atlunadvise).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]  
  
##  <a name="atlunadvise"></a>AtlUnadvise  
 Finaliza la conexión establecida a través de [AtlAdvise](#atladvise).  
  
> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```  
  
### <a name="parameters"></a>Parámetros  
 `pUnkCP`  
 [in] Un puntero a la **IUnknown** del objeto que está conectado el cliente.  
  
 `iid`  
 [in] El GUID del punto de conexión. Normalmente, esto es igual que la interfaz de salida administrada por el punto de conexión.  
  
 `dw`  
 [in] La cookie que identifica de forma única la conexión.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]  
  
##  <a name="atladvisesinkmap"></a>AtlAdviseSinkMap  
 Llame a esta función para notificar o no notificar todas las entradas del mapa de eventos del receptor del objeto.  
  
> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```  
  
### <a name="parameters"></a>Parámetros  
 *pT*  
 [in] Un puntero al objeto que contiene el mapa de recepción.  
  
 `bAdvise`  
 [in] **true** si todas las entradas de receptor son recibir información; **false** si todas las entradas de receptor deben ser desaconsejarán.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT estándar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../atl/reference/atl-functions.md)   
 [Macros de punto de conexión](../../atl/reference/connection-point-macros.md)
