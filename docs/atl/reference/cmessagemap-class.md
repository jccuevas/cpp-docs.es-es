---
title: Clase de CMessageMap | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
caps.latest.revision: 22
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: f0b40c73101463b934e3fcf299171bea142fe838
ms.lasthandoff: 02/24/2017

---
# <a name="cmessagemap-class"></a>CMessageMap (clase)
Esta clase permite que los mapas de mensajes de un objeto para tener acceso a otro objeto.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class ATL_NO_VTABLE CMessageMap
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMessageMap::ProcessWindowMessage](#processwindowmessage)|Tiene acceso a un mapa de mensajes en el `CMessageMap`-clase derivada.|  
  
## <a name="remarks"></a>Comentarios  
 `CMessageMap`es una clase base abstracta que permite los mensajes de un objeto se asigna para tener acceso a otro objeto. Fin de un objeto exponer sus mapas de mensajes, debe derivar su clase de `CMessageMap`.  
  
 ATL utiliza `CMessageMap` contenido de soporte técnico de windows y el encadenamiento de mapa de mensajes dinámicos. Por ejemplo, cualquier clase que contiene un [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) objeto debe derivar de `CMessageMap`. El siguiente código se toma de la [SUBEDIT](../../visual-cpp-samples.md) ejemplo. A través de [CComControl](../../atl/reference/ccomcontrol-class.md), `CAtlEdit` automáticamente la clase se deriva de `CMessageMap`.  
  
 [!code-cpp[NVC_ATL_Windowing&#90;](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]  
  
 Dado que la ventana contenida, `m_EditCtrl`, usará un mapa de mensajes en la clase contenedora, `CAtlEdit` se deriva de `CMessageMap`.  
  
 Para obtener más información acerca de los mapas de mensajes, consulte [mapas de mensajes](../../atl/message-maps-atl.md) en el artículo "Clases de ventana ATL".  
  
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
 [in] Identificador de la ventana de recepción del mensaje.  
  
 `uMsg`  
 [in] El mensaje enviado a la ventana.  
  
 `wParam`  
 [in] Obtener información adicional específica de los mensajes.  
  
 `lParam`  
 [in] Obtener información adicional específica de los mensajes.  
  
 `lResult`  
 [out] El resultado del procesamiento del mensaje.  
  
 `dwMsgMapID`  
 [in] El identificador del mapa de mensajes que procesará el mensaje. El mapa de mensajes predeterminado declarado con [BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554), identificado por 0. Un mapa de mensajes alternativo, declarado con [ALT_MSG_MAP(msgMapID)](http://msdn.microsoft.com/library/2c8871bf-abc0-4d52-bcf7-6b2ab9eb5af8), se identifica mediante `msgMapID`.  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si el mensaje está totalmente controlado; en caso contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Llamado por el procedimiento de ventana de un [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) de objeto o de un objeto que está encadenando dinámicamente al mapa de mensajes.  
  
## <a name="see-also"></a>Vea también  
 [Clase CDynamicChain](../../atl/reference/cdynamicchain-class.md)   
 [BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554)   
 [ALT_MSG_MAP](http://msdn.microsoft.com/library/2c8871bf-abc0-4d52-bcf7-6b2ab9eb5af8)   
 [Información general de la clase](../../atl/atl-class-overview.md)

