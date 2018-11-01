---
title: CDynamicChain (clase)
ms.date: 11/04/2016
f1_keywords:
- CDynamicChain
- ATLWIN/ATL::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CallChain
- ATLWIN/ATL::CDynamicChain::RemoveChainEntry
- ATLWIN/ATL::CDynamicChain::SetChainEntry
helpviewer_keywords:
- message maps, chaining
- chaining message maps
- CDynamicChain class
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
ms.openlocfilehash: 57bbd009bbcbe0ea3352ab27c5d6fbb630b7d050
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668018"
---
# <a name="cdynamicchain-class"></a>CDynamicChain (clase)

Esta clase proporciona métodos que admiten el encadenamiento dinámico de mapas de mensajes.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

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
|[CDynamicChain::RemoveChainEntry](#removechainentry)|Quita una entrada de asignación de mensaje de la colección.|
|[CDynamicChain:: SetChainEntry](#setchainentry)|Agrega una entrada de asignación de mensaje a la colección o modifica una entrada existente.|

## <a name="remarks"></a>Comentarios

`CDynamicChain` administra una colección de mapas de mensajes, lo que permite un mensaje de Windows para que se dirijan en tiempo de ejecución al mapa de mensajes de otro objeto.

Para agregar compatibilidad para el encadenamiento dinámico de mapas de mensajes, realice lo siguiente:

- Derive la clase de `CDynamicChain`. En el mapa de mensajes, especificar la [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) macro encadenar a mapa de mensajes predeterminado de otro objeto.

- Derivar todas las clases que desee vincularse a desde [CMessageMap](../../atl/reference/cmessagemap-class.md). `CMessageMap` permite que un objeto exponer sus mapas de mensajes a otros objetos.

- Llame a `CDynamicChain::SetChainEntry` para identificar qué objeto y qué mensaje de mapa desea encadenar a.

Por ejemplo, suponga que la clase se define como sigue:

[!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]

El cliente luego llama `CMyWindow::SetChainEntry`:

[!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]

donde `chainedObj` es el objeto encadenado y es una instancia de una clase derivada de `CMessageMap`. Ahora, si `myCtl` recibe un mensaje que no está controlado por `OnPaint` o `OnSetFocus`, el procedimiento de ventana dirige el mensaje a `chainedObj`del mapa de mensajes predeterminado.

Para obtener más información sobre el encadenamiento de mapa de mensajes, vea [mapas de mensajes](../../atl/message-maps-atl.md) en el artículo "Clases de ventana ATL".

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="callchain"></a>  CDynamicChain::CallChain

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

*dwChainID*<br/>
[in] El identificador único asociado con el objeto encadenado y su mapa de mensajes.

*hWnd*<br/>
[in] El identificador de la ventana que recibe el mensaje.

*uMsg*<br/>
[in] El mensaje enviado a la ventana.

*wParam*<br/>
[in] Información adicional específica del mensaje.

*lParam*<br/>
[in] Información adicional específica del mensaje.

*lResult*<br/>
[out] El resultado del procesamiento del mensaje.

### <a name="return-value"></a>Valor devuelto

TRUE si el mensaje se procese por completo; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Para invocar el procedimiento de ventana `CallChain`, debe especificar el [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) macro en el mapa de mensajes. Para obtener un ejemplo, vea el [CDynamicChain](../../atl/reference/cdynamicchain-class.md) información general.

`CallChain` requiere una llamada anterior a [SetChainEntry](#setchainentry) para asociar el *dwChainID* valor con un objeto y su mapa de mensajes.

##  <a name="cdynamicchain"></a>  CDynamicChain::CDynamicChain

El constructor.

```
CDynamicChain();
```

##  <a name="dtor"></a>  CDynamicChain:: ~ CDynamicChain

Destructor.

```
~CDynamicChain();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados.

##  <a name="removechainentry"></a>  CDynamicChain::RemoveChainEntry

Quita la asignación de mensaje especificado de la colección.

```
BOOL RemoveChainEntry(DWORD dwChainID);
```

### <a name="parameters"></a>Parámetros

*dwChainID*<br/>
[in] El identificador único asociado con el objeto encadenado y su mapa de mensajes. Originalmente define este valor mediante una llamada a [SetChainEntry](#setchainentry).

### <a name="return-value"></a>Valor devuelto

TRUE si el mapa de mensajes se quitó correctamente de la colección. En caso contrario, FALSE.

##  <a name="setchainentry"></a>  CDynamicChain:: SetChainEntry

Agrega el mapa de mensajes especificado a la colección.

```
BOOL SetChainEntry(
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```

### <a name="parameters"></a>Parámetros

*dwChainID*<br/>
[in] El identificador único asociado con el objeto encadenado y su mapa de mensajes.

*pObject*<br/>
[in] Un puntero al objeto encadenado declarar el mapa de mensajes. Este objeto debe derivarse de [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[in] El identificador del mapa de mensajes en el objeto encadenado. El valor predeterminado es 0, que identifica el mapa de mensajes predeterminado declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Para especificar un mapa de mensajes alternativo declarado con [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), pasar `msgMapID`.

### <a name="return-value"></a>Valor devuelto

TRUE si el mapa de mensajes se agregó correctamente a la colección. En caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Si el *dwChainID* valor ya existe en la colección, su objeto asociado y un mapa de mensajes se reemplazan por *pObject* y *dwMsgMapID*, respectivamente. En caso contrario, se agrega una nueva entrada.

## <a name="see-also"></a>Vea también

[CWindowImpl (clase)](../../atl/reference/cwindowimpl-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
