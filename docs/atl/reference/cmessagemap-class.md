---
title: CMessageMap (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae6f41c2e8e8d142ee143d7ba0829751e1c230a3
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42573266"
---
# <a name="cmessagemap-class"></a>CMessageMap (clase)
Esta clase permite que los mapas de mensajes de un objeto que se acceda por otro objeto.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
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
 `CMessageMap` es una clase base abstracta que permite a los mensajes de un objeto que se asigna para tener acceso a otro objeto. En el orden de un objeto exponer sus mapas de mensajes, debe derivar su clase de `CMessageMap`.  
  
 ATL utiliza `CMessageMap` contenido de soporte técnico de windows y el encadenamiento de asignación de mensaje dinámicos. Por ejemplo, cualquier clase que contiene un [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) objeto debe derivarse de `CMessageMap`. El código siguiente se toma de la [SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit) ejemplo. A través de [CComControl](../../atl/reference/ccomcontrol-class.md), `CAtlEdit` clase se deriva automáticamente `CMessageMap`.  
  
 [!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]  
  
 Dado que la ventana contenida, `m_EditCtrl`, usará un mapa de mensajes en la clase contenedora, `CAtlEdit` deriva `CMessageMap`.  
  
 Para obtener más información acerca de mapas de mensajes, vea [mapas de mensajes](../../atl/message-maps-atl.md) en el artículo "Clases de ventana ATL".  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
##  <a name="processwindowmessage"></a>  CMessageMap::ProcessWindowMessage  
 Tiene acceso a la asignación de mensaje identificada por *dwMsgMapID* en un `CMessageMap`-clase derivada.  
  
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
 *hWnd*  
 [in] El identificador de la ventana que recibe el mensaje.  
  
 *uMsg*  
 [in] El mensaje enviado a la ventana.  
  
 *wParam*  
 [in] Información adicional específica del mensaje.  
  
 *lParam*  
 [in] Información adicional específica del mensaje.  
  
 *lResult*  
 [out] El resultado del procesamiento del mensaje.  
  
 *dwMsgMapID*  
 [in] El identificador del mapa de mensajes que procesará el mensaje. El mapa de mensajes de forma predeterminada, se declara con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), identificado por 0. Un mapa de mensajes alternativo, declarado con [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), se identifica mediante `msgMapID`.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el mensaje lo controla totalmente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Lo llama el procedimiento de ventana de un [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) de objeto o de un objeto que está encadenando dinámicamente al mapa de mensajes.  
  
## <a name="see-also"></a>Vea también  
 [CDynamicChain (clase)](../../atl/reference/cdynamicchain-class.md)   
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)   
 [Información general de clases](../../atl/atl-class-overview.md)
