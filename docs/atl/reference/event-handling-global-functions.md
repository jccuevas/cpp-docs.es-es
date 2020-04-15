---
title: Funciones globales de gestión de eventos
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
ms.openlocfilehash: f2f8269dcf0f59a5d0794d3f16d4c4f85d8841ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330137"
---
# <a name="event-handling-global-functions"></a>Funciones globales de gestión de eventos

Esta función proporciona un controlador de eventos.

> [!IMPORTANT]
> La función enumerada en la tabla siguiente no se puede utilizar en aplicaciones que se ejecutan en Windows Runtime.

|||
|-|-|
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|Espera a que se señale un objeto, mientras tanto, distribuye mensajes de ventana según sea necesario.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="atlwaitwithmessageloop"></a><a name="atlwaitwithmessageloop"></a>AtlWaitWithMessageLoop

Espera el objeto que se va a señalizar mientras envía mensajes de ventana según sea necesario.

> [!IMPORTANT]
> Esta función no se puede utilizar en aplicaciones que se ejecutan en Windows Runtime.

```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```

### <a name="parameters"></a>Parámetros

*hEvent*<br/>
[en] El identificador del objeto que se va a esperar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ha señalado el objeto.

### <a name="remarks"></a>Observaciones

Esto es útil si desea esperar a que se produzca el evento de un objeto y recibir una notificación de que sucede, pero permite que los mensajes de ventana se distribuyan mientras se espera.

## <a name="see-also"></a>Consulte también

[Functions](../../atl/reference/atl-functions.md)
