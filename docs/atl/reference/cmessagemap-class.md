---
title: Clase CMessageMap
ms.date: 11/04/2016
f1_keywords:
- CMessageMap
- ATLWIN/ATL::CMessageMap
- ATLWIN/ATL::CMessageMap::ProcessWindowMessage
helpviewer_keywords:
- CMessageMap class
- message maps, ATL
- ATL, message handlers
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
ms.openlocfilehash: a822f36d6b6fd49301d8240324e27f0ad9ce52e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326722"
---
# <a name="cmessagemap-class"></a>Clase CMessageMap

Esta clase permite que otro objeto acceda a los mapas de mensajes de un objeto.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class ATL_NO_VTABLE CMessageMap
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMessageMap::ProcessWindowMessage](#processwindowmessage)|Tiene acceso a un `CMessageMap`mapa de mensajes en la clase derivada.|

## <a name="remarks"></a>Observaciones

`CMessageMap`es una clase base abstracta que permite que otro objeto pueda acceder a los mapas de mensajes de un objeto. Para que un objeto exponga sus mapas de `CMessageMap`mensajes, su clase debe derivar de .

ATL `CMessageMap` se utiliza para admitir ventanas contenidas y encadenamiento dinámico de mapas de mensajes. Por ejemplo, cualquier clase que contenga un `CMessageMap`objeto [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) debe derivar de . El código siguiente se toma del ejemplo [SUBEDIT.](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit) A través de [CComControl](../../atl/reference/ccomcontrol-class.md), la `CAtlEdit` clase deriva automáticamente de `CMessageMap`.

[!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]

Dado que la `m_EditCtrl`ventana contenida, , usará un `CAtlEdit` mapa de `CMessageMap`mensajes en la clase contenedora, deriva de .

Para obtener más información acerca de los mapas de mensajes, vea [Mapas](../../atl/message-maps-atl.md) de mensajes en el artículo "Clases de ventana ATL."

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="cmessagemapprocesswindowmessage"></a><a name="processwindowmessage"></a>CMessageMap::ProcessWindowMessage

Tiene acceso al mapa de mensajes identificado `CMessageMap`por *dwMsgMapID* en una clase derivada.

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

*dwMsgMapID*<br/>
[en] Identificador del mapa de mensajes que procesará el mensaje. El mapa de mensajes predeterminado, declarado con [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), se identifica por 0. Un mapa de mensajes alternativo, declarado con [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), se identifica mediante `msgMapID`.

### <a name="return-value"></a>Valor devuelto

TRUESi el mensaje se controla completamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Llamado por el procedimiento de ventana de un [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) objeto o de un objeto que se encadena dinámicamente al mapa de mensajes.

## <a name="see-also"></a>Consulte también

[Clase CDynamicChain](../../atl/reference/cdynamicchain-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
