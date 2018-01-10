---
title: Clase CDynamicChain | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDynamicChain
- ATLWIN/ATL::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CallChain
- ATLWIN/ATL::CDynamicChain::RemoveChainEntry
- ATLWIN/ATL::CDynamicChain::SetChainEntry
dev_langs: C++
helpviewer_keywords:
- message maps, chaining
- chaining message maps
- CDynamicChain class
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f57da02b764c1cbce6a97ecbea8aa84e4ffcce9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicchain-class"></a>Clase CDynamicChain
Esta clase proporciona métodos que admiten el encadenamiento dinámico de mapas de mensajes.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CDynamicChain
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDynamicChain::CDynamicChain](#cdynamicchain)|El constructor.|  
|[CDynamicChain:: ~ CDynamicChain](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDynamicChain::CallChain](#callchain)|Dirige un mensaje de Windows al mapa de mensajes de otro objeto.|  
|[CDynamicChain::RemoveChainEntry](#removechainentry)|Quita una entrada de mapa de mensajes de la colección.|  
|[CDynamicChain:: SetChainEntry](#setchainentry)|Agrega una entrada de mapa de mensajes a la colección o modifica una entrada existente.|  
  
## <a name="remarks"></a>Comentarios  
 `CDynamicChain`administra una colección de mapas de mensajes, lo que permite un mensaje de Windows para que se dirijan en tiempo de ejecución al mapa de mensajes de otro objeto.  
  
 Para agregar compatibilidad para el encadenamiento dinámico de mapas de mensajes, haga lo siguiente:  
  
-   Derive la clase de `CDynamicChain`. En el mapa de mensajes, especificar el [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) macro para encadenar al mapa de mensajes predeterminado de otro objeto.  
  
-   Derivan todas las clases que desee vincularse a desde [CMessageMap](../../atl/reference/cmessagemap-class.md). `CMessageMap`permite que un objeto exponer sus mapas de mensajes a otros objetos.  
  
-   Llame a `CDynamicChain::SetChainEntry` para identificar en qué objeto y asignar los mensajes desean encadenar a.  
  
 Por ejemplo, suponga que la clase se define como sigue:  
  
 [!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]  
  
 El cliente, a continuación, llama a `CMyWindow::SetChainEntry`:  
  
 [!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]  
  
 donde `chainedObj` es el objeto encadenado y es una instancia de una clase derivada de `CMessageMap`. Ahora, si `myCtl` recibe un mensaje que no esté controlado por `OnPaint` o `OnSetFocus`, el procedimiento de ventana dirige el mensaje a `chainedObj`del mapa de mensajes predeterminado.  
  
 Para obtener más información sobre el encadenamiento de mapa de mensajes, vea [mapas de mensajes](../../atl/message-maps-atl.md) en el artículo "Clases de ventana ATL".  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
##  <a name="callchain"></a>CDynamicChain::CallChain  
 Dirige el mensaje de Windows al mapa de mensajes de otro objeto.  
  
```
BOOL CallChain(  
    DWORD dwChainID,
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwChainID`  
 [in] El identificador único asociado con el objeto encadenado y su mapa de mensajes.  
  
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
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si el mensaje es totalmente procesado; en caso contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Para el procedimiento de ventana invocar `CallChain`, debe especificar el [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) macro en el mapa de mensajes. Para obtener un ejemplo, vea el [CDynamicChain](../../atl/reference/cdynamicchain-class.md) información general.  
  
 `CallChain`requiere una llamada anterior a [SetChainEntry](#setchainentry) para asociar el `dwChainID` valor con un objeto y el mapa de mensajes.  
  
##  <a name="cdynamicchain"></a>CDynamicChain::CDynamicChain  
 El constructor.  
  
```
CDynamicChain();
```  
  
##  <a name="dtor"></a>CDynamicChain:: ~ CDynamicChain  
 Destructor.  
  
```
~CDynamicChain();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados.  
  
##  <a name="removechainentry"></a>CDynamicChain::RemoveChainEntry  
 Quita la asignación de mensaje especificado de la colección.  
  
```
BOOL RemoveChainEntry(DWORD dwChainID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwChainID`  
 [in] El identificador único asociado con el objeto encadenado y su mapa de mensajes. Originalmente definir este valor mediante una llamada a [SetChainEntry](#setchainentry).  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si el mapa de mensajes se quita correctamente de la colección. En caso contrario, **FALSE**.  
  
##  <a name="setchainentry"></a>CDynamicChain:: SetChainEntry  
 Agrega el mapa de mensajes especificado a la colección.  
  
```
BOOL SetChainEntry(  
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwChainID`  
 [in] El identificador único asociado con el objeto encadenado y su mapa de mensajes.  
  
 `pObject`  
 [in] Un puntero al objeto encadenado declarar el mapa de mensajes. Este objeto debe derivarse de [CMessageMap](../../atl/reference/cmessagemap-class.md).  
  
 `dwMsgMapID`  
 [in] El identificador del mapa de mensajes en el objeto encadenado. El valor predeterminado es 0, que identifica el mapa de mensajes predeterminado declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Para especificar un mapa de mensajes alternativo declara con [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), pasar `msgMapID`.  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si el mapa de mensajes se agregó correctamente a la colección. En caso contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Si el `dwChainID` valor ya existe en la colección, su objeto asociado y el mapa de mensajes se reemplazan por `pObject` y `dwMsgMapID`, respectivamente. En caso contrario, se agrega una nueva entrada.  
  
## <a name="see-also"></a>Vea también  
 [Clase de CWindowImpl](../../atl/reference/cwindowimpl-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
