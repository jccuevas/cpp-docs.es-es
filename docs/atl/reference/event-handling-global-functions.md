---
title: Funciones globales de control de eventos
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
ms.openlocfilehash: 02066f2e6cd215fdb68fcdb594307b646ee69cad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660400"
---
# <a name="event-handling-global-functions"></a>Funciones globales de control de eventos

Esta función proporciona un controlador de eventos.

> [!IMPORTANT]
>  La función aparece en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

|||
|-|-|
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|Espera a que un objeto que se señalice, mientras envía mensajes de ventana según sea necesario.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="atlwaitwithmessageloop"></a>  AtlWaitWithMessageLoop

Espera el objeto que se va a señalizar mientras envía mensajes de ventana según sea necesario.

> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```

### <a name="parameters"></a>Parámetros

*hEvent*<br/>
[in] El identificador de objeto que se va a esperar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el objeto se haya señalado.

### <a name="remarks"></a>Comentarios

Esto es útil si desea esperar a suceder y recibir una notificación de lo que ocurre el evento de un objeto, pero permitir que los mensajes de ventana se distribuyan mientras espera.

## <a name="see-also"></a>Vea también

[Funciones](../../atl/reference/atl-functions.md)
