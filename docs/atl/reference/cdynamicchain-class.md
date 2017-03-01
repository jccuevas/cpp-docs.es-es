---
title: Clase CDynamicChain | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CDynamicChain
- ATL.CDynamicChain
- CDynamicChain
dev_langs:
- C++
helpviewer_keywords:
- message maps, chaining
- chaining message maps
- CDynamicChain class
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 4da97d0b3d72400d7e285fde187e6860759900af
ms.lasthandoff: 02/24/2017

---
# <a name="cdynamicchain-class"></a>Clase CDynamicChain
Esta clase proporciona métodos que admiten el encadenamiento dinámico de mapas de mensajes.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CDynamicChain
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDynamicChain::CDynamicChain](#cdynamicchain)|El constructor.|  
|[CDynamicChain:: ~ CDynamicChain](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDynamicChain::CallChain](#callchain)|Indica un mensaje de Windows al mapa de mensajes de otro objeto.|  
|[CDynamicChain::RemoveChainEntry](#removechainentry)|Quita una entrada de mapa de mensajes de la colección.|  
|[CDynamicChain:: SetChainEntry](#setchainentry)|Agrega una entrada de mapa de mensajes a la colección o modifica una entrada existente.|  
  
## <a name="remarks"></a>Comentarios  
 `CDynamicChain`administra una colección de mapas de mensajes, lo que permite un mensaje de Windows se envíen en tiempo de ejecución al mapa de mensajes de otro objeto.  
  
 Para agregar compatibilidad para el encadenamiento dinámico de mapas de mensajes, realice lo siguiente:  
  
-   Derive la clase de `CDynamicChain`. En el mapa de mensajes, especifique la [CHAIN_MSG_MAP_DYNAMIC](http://msdn.microsoft.com/library/7e5c72b7-cb31-4f3b-8a1b-6293804af220) macro para encadenar al mapa de mensajes predeterminado de otro objeto.  
  
-   Derivan todas las clases que desea para la cadena [CMessageMap](../../atl/reference/cmessagemap-class.md). `CMessageMap`permite a un objeto exponer sus mapas de mensajes a otros objetos.  
  
-   Llame a `CDynamicChain::SetChainEntry` para identificar qué objeto y qué mensaje de mapa desean cadena.  
  
 Por ejemplo, suponga que la clase se define como sigue:  
  
 [!code-cpp[NVC_ATL_Windowing&#88;](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]  
  
 El cliente luego llama `CMyWindow::SetChainEntry`:  
  
 [!code-cpp[NVC_ATL_Windowing&#89;](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]  
  
 donde `chainedObj` es el objeto encadenado y es una instancia de una clase derivada de `CMessageMap`. Ahora, si `myCtl` recibe un mensaje que no está controlado por `OnPaint` o `OnSetFocus`, el procedimiento de ventana dirige el mensaje a `chainedObj`del mapa de mensajes predeterminado.  
  
 Para obtener más información sobre el encadenamiento de mapa de mensajes, consulte [mapas de mensajes](../../atl/message-maps-atl.md) en el artículo "Clases de ventana ATL".  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlwin.h  
  
##  <a name="a-namecallchaina--cdynamicchaincallchain"></a><a name="callchain"></a>CDynamicChain::CallChain  
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
 [in] Identificador de la ventana de recepción del mensaje.  
  
 `uMsg`  
 [in] El mensaje enviado a la ventana.  
  
 `wParam`  
 [in] Obtener información adicional específica de los mensajes.  
  
 `lParam`  
 [in] Obtener información adicional específica de los mensajes.  
  
 `lResult`  
 [out] El resultado del procesamiento del mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si el mensaje es completamente procesado; en caso contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Para invocar el procedimiento de ventana `CallChain`, debe especificar el [CHAIN_MSG_MAP_DYNAMIC](http://msdn.microsoft.com/library/7e5c72b7-cb31-4f3b-8a1b-6293804af220) macro en el mapa de mensajes. Para obtener un ejemplo, consulte el [CDynamicChain](../../atl/reference/cdynamicchain-class.md) información general.  
  
 `CallChain`requiere una llamada anterior a [SetChainEntry](#setchainentry) para asociar el `dwChainID` valor con un objeto y su mapa de mensajes.  
  
##  <a name="a-namecdynamicchaina--cdynamicchaincdynamicchain"></a><a name="cdynamicchain"></a>CDynamicChain::CDynamicChain  
 El constructor.  
  
```
CDynamicChain();
```  
  
##  <a name="a-namedtora--cdynamicchaincdynamicchain"></a><a name="dtor"></a>CDynamicChain:: ~ CDynamicChain  
 Destructor.  
  
```
~CDynamicChain();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados.  
  
##  <a name="a-nameremovechainentrya--cdynamicchainremovechainentry"></a><a name="removechainentry"></a>CDynamicChain::RemoveChainEntry  
 Quita la asignación de mensaje especificado de la colección.  
  
```
BOOL RemoveChainEntry(DWORD dwChainID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwChainID`  
 [in] El identificador único asociado con el objeto encadenado y su mapa de mensajes. Originalmente define este valor mediante una llamada a [SetChainEntry](#setchainentry).  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si el mapa de mensajes se ha quitado correctamente de la colección. De lo contrario, **FALSE**.  
  
##  <a name="a-namesetchainentrya--cdynamicchainsetchainentry"></a><a name="setchainentry"></a>CDynamicChain:: SetChainEntry  
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
 [in] Un puntero al objeto encadenado declarar el mapa de mensajes. Este objeto debe derivar de [CMessageMap](../../atl/reference/cmessagemap-class.md).  
  
 `dwMsgMapID`  
 [in] El identificador del mapa de mensajes en el objeto encadenado. El valor predeterminado es 0, que identifica el mapa de mensajes predeterminado declarado con [BEGIN_MSG_MAP](http://msdn.microsoft.com/library/8bbb5af9-18b1-48c6-880e-166f599ee554). Para especificar un mapa de mensajes alternativo, declarado con [ALT_MSG_MAP(msgMapID)](http://msdn.microsoft.com/library/2c8871bf-abc0-4d52-bcf7-6b2ab9eb5af8), pasar `msgMapID`.  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si el mapa de mensajes se agrega correctamente a la colección. De lo contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Si el `dwChainID` valor ya existe en la colección, su objeto asociado y el mapa de mensajes se reemplazan por `pObject` y `dwMsgMapID`, respectivamente. De lo contrario, se agrega una nueva entrada.  
  
## <a name="see-also"></a>Vea también  
 [CWindowImpl (clase)](../../atl/reference/cwindowimpl-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

