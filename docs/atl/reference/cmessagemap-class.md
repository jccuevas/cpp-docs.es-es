---
title: Clase de CMessageMap | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMessageMap
- ATLWIN/ATL::CMessageMap
- ATLWIN/ATL::CMessageMap::ProcessWindowMessage
dev_langs:
- C++
helpviewer_keywords:
- CMessageMap class
- message maps, ATL
- ATL, message handlers
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 04aff6922358048fcbd330096eb26a412cdb75ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmessagemap-class"></a>Clase de CMessageMap
Esta clase permite a que los mapas de mensajes de un objeto para tener acceso a otro objeto.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class ATL_NO_VTABLE CMessageMap
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMessageMap::ProcessWindowMessage](#processwindowmessage)|Tiene acceso a un mapa de mensajes en el `CMessageMap`-clase derivada.|  
  
## <a name="remarks"></a>Comentarios  
 `CMessageMap`es una clase base abstracta que permite a los mensajes de un objeto que se asigna para tener acceso a otro objeto. En el orden de un objeto exponer sus mapas de mensajes, su clase debe derivarse de `CMessageMap`.  
  
 ATL usa `CMessageMap` para windows de soporte técnico de contenidos y encadenamiento de mapa de mensajes dinámicos. Por ejemplo, cualquier clase que contiene un [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) objeto debe derivarse de `CMessageMap`. El código siguiente se toma la [SUBEDIT](../../visual-cpp-samples.md) ejemplo. A través de [CComControl](../../atl/reference/ccomcontrol-class.md), `CAtlEdit` clase se deriva automáticamente `CMessageMap`.  
  
 [!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]  
  
 Dado que la ventana contenida, `m_EditCtrl`, usará un mapa de mensajes en la clase contenedora, `CAtlEdit` deriva de `CMessageMap`.  
  
 Para obtener más información acerca de los mapas de mensajes, vea [mapas de mensajes](../../atl/message-maps-atl.md) en el artículo "Clases de ventana ATL".  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
##  <a name="processwindowmessage"></a>CMessageMap::ProcessWindowMessage  
 Tiene acceso a la asignación de mensaje identificada por `dwMsgMapID` en un `CMessageMap`-clase derivada.  
  
```
virtual BOOL ProcessWindowMessage(  
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult,
    DWORD dwMsgMapID) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `hWnd`  
 [in] El identificador de la ventana recibe el mensaje.  
  
 `uMsg`  
 [in] El mensaje enviado a la ventana.  
  
 `wParam`  
 [in] Obtener información adicional específica de los mensajes.  
  
 `lParam`  
 [in] Obtener información adicional específica de los mensajes.  
  
 `lResult`  
 [out] El resultado del procesamiento del mensaje.  
  
 `dwMsgMapID`  
 [in] El identificador del mapa de mensajes que procesará el mensaje. El mapa de mensajes de forma predeterminada, se declara con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), identificado por 0. Un mapa de mensajes alternativo, declarado con [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), se identifica mediante `msgMapID`.  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si el mensaje es totalmente administrado; en caso contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Llamado por el procedimiento de ventana de un [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) de un objeto o de un objeto que está encadenando dinámicamente al mapa de mensajes.  
  
## <a name="see-also"></a>Vea también  
 [Clase CDynamicChain](../../atl/reference/cdynamicchain-class.md)   
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)   
 [Información general de clases](../../atl/atl-class-overview.md)
