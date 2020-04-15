---
title: Clase CDynamicChain
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
ms.openlocfilehash: 4a72b3b4308ed83dfdc4a2895a04d1fe9a177ce5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327033"
---
# <a name="cdynamicchain-class"></a>Clase CDynamicChain

Esta clase proporciona métodos que admiten el encadenamiento dinámico de mapas de mensajes.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CDynamicChain
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDynamicChain::CDynamicChain](#cdynamicchain)|El constructor.|
|[CDynamicChain::-CDynamicChain](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDynamicChain::CallChain](#callchain)|Dirige un mensaje de Windows al mapa de mensajes de otro objeto.|
|[CDynamicChain::RemoveChainEntry](#removechainentry)|Quita una entrada de mapa de mensajes de la colección.|
|[CDynamicChain::SetChainEntry](#setchainentry)|Agrega una entrada de mapa de mensajes a la colección o modifica una entrada existente.|

## <a name="remarks"></a>Observaciones

`CDynamicChain`administra una colección de mapas de mensajes, lo que permite que un mensaje de Windows se dirija, en tiempo de ejecución, al mapa de mensajes de otro objeto.

Para agregar compatibilidad para el encadenamiento dinámico de mapas de mensajes, haga lo siguiente:

- Derive su `CDynamicChain`clase de . En el mapa de mensajes, especifique la [macro de CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) que se va a encadenar al mapa de mensajes predeterminado de otro objeto.

- Derive cada clase a la que desee encadenar desde [CMessageMap](../../atl/reference/cmessagemap-class.md). `CMessageMap`permite que un objeto exponga sus mapas de mensajes a otros objetos.

- Llame `CDynamicChain::SetChainEntry` para identificar qué objeto y a qué mapa de mensajes desea encadenar.

Por ejemplo, supongamos que la clase se define de la siguiente manera:

[!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]

A continuación, `CMyWindow::SetChainEntry`el cliente llama a:

[!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]

donde `chainedObj` está el objeto encadenado y es `CMessageMap`una instancia de una clase derivada de . Ahora, `myCtl` si recibe un mensaje que `OnPaint` no `OnSetFocus`se controla por o `chainedObj`, el procedimiento de ventana dirige el mensaje al mapa de mensajes predeterminado .

Para obtener más información acerca del encadenamiento de mapas de mensajes, vea [Mapas](../../atl/message-maps-atl.md) de mensajes en el artículo "Clases de ventana ATL."

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="cdynamicchaincallchain"></a><a name="callchain"></a>CDynamicChain::CallChain

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
[en] Identificador único asociado con el objeto encadenado y su mapa de mensajes.

*hWnd*<br/>
[en] El identificador de la ventana que recibe el mensaje.

*uMsg*<br/>
[en] El mensaje enviado a la ventana.

*wParam*<br/>
[en] Información adicional específica del mensaje.

*lParam*<br/>
[en] Información adicional específica del mensaje.

*lResult*<br/>
[fuera] El resultado del procesamiento de mensajes.

### <a name="return-value"></a>Valor devuelto

TRUESi el mensaje está completamente procesado; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Para que el `CallChain`procedimiento de ventana se invoque , debe especificar la [macro CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) en el mapa de mensajes. Para obtener un ejemplo, consulte la información general [de CDynamicChain.](../../atl/reference/cdynamicchain-class.md)

`CallChain`requiere una llamada anterior a [SetChainEntry](#setchainentry) para asociar el valor *dwChainID* con un objeto y su mapa de mensajes.

## <a name="cdynamicchaincdynamicchain"></a><a name="cdynamicchain"></a>CDynamicChain::CDynamicChain

El constructor.

```
CDynamicChain();
```

## <a name="cdynamicchaincdynamicchain"></a><a name="dtor"></a>CDynamicChain::-CDynamicChain

Destructor.

```
~CDynamicChain();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados.

## <a name="cdynamicchainremovechainentry"></a><a name="removechainentry"></a>CDynamicChain::RemoveChainEntry

Quita el mapa de mensajes especificado de la colección.

```
BOOL RemoveChainEntry(DWORD dwChainID);
```

### <a name="parameters"></a>Parámetros

*dwChainID*<br/>
[en] Identificador único asociado con el objeto encadenado y su mapa de mensajes. Originalmente se define este valor mediante una llamada a [SetChainEntry](#setchainentry).

### <a name="return-value"></a>Valor devuelto

TRUESi el mapa de mensajes se quita correctamente de la colección. De lo contrario, FALSE.

## <a name="cdynamicchainsetchainentry"></a><a name="setchainentry"></a>CDynamicChain::SetChainEntry

Agrega el mapa de mensajes especificado a la colección.

```
BOOL SetChainEntry(
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```

### <a name="parameters"></a>Parámetros

*dwChainID*<br/>
[en] Identificador único asociado con el objeto encadenado y su mapa de mensajes.

*pObject*<br/>
[en] Puntero al objeto encadenado que declara el mapa de mensajes. Este objeto debe derivar de [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[en] Identificador del mapa de mensajes en el objeto encadenado. El valor predeterminado es 0, que identifica el mapa de mensajes predeterminado declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Para especificar un mapa de mensajes alternativo declarado `msgMapID`con [ALT_MSG_MAP(msgMapID),](message-map-macros-atl.md#alt_msg_map)pase .

### <a name="return-value"></a>Valor devuelto

TRUESi el mapa de mensajes se agrega correctamente a la colección. De lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Si el valor *dwChainID* ya existe en la colección, su objeto asociado y el mapa de mensajes se reemplazan por *pObject* y *dwMsgMapID*, respectivamente. De lo contrario, se agrega una nueva entrada.

## <a name="see-also"></a>Consulte también

[Clase CWindowImpl](../../atl/reference/cwindowimpl-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
