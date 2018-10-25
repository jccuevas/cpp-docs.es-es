---
title: CMultiLock (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMultiLock
- AFXMT/CMultiLock
- AFXMT/CMultiLock::CMultiLock
- AFXMT/CMultiLock::IsLocked
- AFXMT/CMultiLock::Lock
- AFXMT/CMultiLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CMultiLock [MFC], CMultiLock
- CMultiLock [MFC], IsLocked
- CMultiLock [MFC], Lock
- CMultiLock [MFC], Unlock
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 097f6173faad4f99f64c5dac45e2a0d1292a07eb
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076365"
---
# <a name="cmultilock-class"></a>CMultiLock (clase)

Representa el mecanismo de control de acceso utilizado para controlar el acceso a los recursos en un programa de multithreading.

## <a name="syntax"></a>Sintaxis

```
class CMultiLock
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMultiLock::CMultiLock](#cmultilock)|Construye un objeto `CMultiLock`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMultiLock::IsLocked](#islocked)|Determina si un objeto de sincronización específico de la matriz está bloqueado.|
|[CMultiLock::Lock](#lock)|Se espera en la matriz de objetos de sincronización.|
|[CMultiLock::Unlock](#unlock)|Libera todos los objetos de sincronización que se poseen.|

## <a name="remarks"></a>Comentarios

`CMultiLock` no tiene una clase base.

Para usar las clases de sincronización [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), y [CEvent](../../mfc/reference/cevent-class.md), puede crear un `CMultiLock` o [CSingleLock](../../mfc/reference/csinglelock-class.md)objeto se va a esperar y liberar el objeto de sincronización. Usar `CMultiLock` cuando hay varios objetos que puede usar en un momento determinado. Use `CSingleLock` cuando sólo deba esperar en un objeto a la vez.

Para usar un `CMultiLock` , primero cree una matriz de los objetos de sincronización que desea esperar. A continuación, llame a la `CMultiLock` constructor del objeto dentro de una función miembro de clase del recurso controlado. A continuación, llame a la [bloqueo](#lock) función miembro para determinar si un recurso está disponible (señalado). Si hay alguno, continúe con el resto de la función miembro. Si no hay ningún recurso está disponible, espere durante un período de tiempo para un recurso que liberarse especificado o devolver un error. Una vez completado el uso de un recurso, llame a la [Unlock](#unlock) funcionar si el `CMultiLock` objeto consiste en volver a utilizar o permitir el `CMultiLock` destrucción del objeto.

`CMultiLock` los objetos son más útiles cuando un subproceso tiene un gran número de `CEvent` pueda responder a los objetos. Crear una matriz que contiene todos los `CEvent` punteros y llamada `Lock`. Esto hará que el subproceso espere hasta que uno de los eventos se señala.

Para obtener más información sobre cómo usar `CMultiLock` objetos, consulte el artículo [Multithreading: uso de las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CMultiLock`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmt.h

##  <a name="cmultilock"></a>  CMultiLock::CMultiLock

Construye un objeto `CMultiLock`.

```
CMultiLock(
    CSyncObject* ppObjects [ ],
    DWORD dwCount,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Parámetros

*ppObjects*<br/>
Matriz de punteros a los objetos de sincronización al que se espera. No puede ser nulo.

*dwCount*<br/>
Número de objetos de *ppObjects*. Debe ser mayor que 0.

*bInitialLock*<br/>
Especifica si un intento de acceder a cualquiera de los objetos proporcionados.

### <a name="remarks"></a>Comentarios

Esta función se llama después de crear la matriz de objetos de sincronización al que se espera. Normalmente, se llama desde dentro del subproceso que debe esperar a que uno de los objetos de sincronización esté disponible.

##  <a name="islocked"></a>  CMultiLock::IsLocked

Determina si el objeto especificado es no señalado (no disponible).

```
BOOL IsLocked(DWORD dwItem);
```

### <a name="parameters"></a>Parámetros

*dwItem*<br/>
Índice de la matriz de objetos correspondiente al objeto cuyo estado se está consultando.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto especificado está bloqueado; en caso contrario, es 0.

##  <a name="lock"></a>  CMultiLock::Lock

Llame a esta función para obtener acceso a uno o varios de los recursos controlados por los objetos de sincronización proporcionados a la `CMultiLock` constructor.

```
DWORD Lock(
    DWORD dwTimeOut = INFINITE,
    BOOL bWaitForAll = TRUE,
    DWORD dwWakeMask = 0);
```

### <a name="parameters"></a>Parámetros

*dwTimeOut*<br/>
Especifica la cantidad de tiempo de espera para que el objeto de sincronización esté disponible (señalado). Si es infinito, `Lock` esperará hasta que se señaliza el objeto antes de devolver.

*bWaitForAll*<br/>
Especifica si todos los objetos que se espera deben señalarse al mismo tiempo antes de devolver. Si es FALSE, `Lock` devolverá cuando se señala a cualquiera de los objetos que se espera.

*dwWakeMask*<br/>
Especifica otras condiciones que pueden anular la espera. Para obtener una lista completa de las opciones disponibles para este parámetro, vea [MsgWaitForMultipleObjects](/windows/desktop/api/winuser/nf-winuser-msgwaitformultipleobjects) en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Si `Lock` se produce un error, devuelve - 1. Si se realiza correctamente, devuelve uno de los valores siguientes:

- Entre WAIT_OBJECT_0 y WAIT_OBJECT_0 + (número de objetos - 1)

   Si *bWaitForAll* es TRUE, todos los objetos se señalizan (disponible). Si *bWaitForAll* es FALSE, el valor devuelto - WAIT_OBJECT_0 es el índice de la matriz de objetos del objeto que se señala (disponible).

- WAIT_OBJECT_0 + (número de objetos)

   Un evento especificado en *dwWakeMask* está disponible en la cola de entrada del subproceso.

- Entre WAIT_ABANDONED_0 y WAIT_ABANDONED_0 + (número de objetos - 1)

   Si *bWaitForAll* es TRUE, todos los objetos se señalizan y al menos uno de los objetos es un objeto de exclusión mutua abandonada. Si *bWaitForAll* es FALSE, el valor devuelto - WAIT_ABANDONED_0 es el índice de la matriz de objetos del objeto de exclusión mutua abandonada que satisfizo la espera.

- WAIT_TIMEOUT

   El intervalo de tiempo de espera especificado en *dwTimeOut* caducado sin espera subsiguientes.

### <a name="remarks"></a>Comentarios

Si *bWaitForAll* es TRUE, `Lock` devolverá correctamente en cuanto se señalicen todos los objetos de sincronización al mismo tiempo. Si *bWaitForAll* es FALSE, `Lock` devolverá tan pronto como se señaliza uno o varios de los objetos de sincronización.

Si `Lock` no es capaz de devolver resultados inmediatamente, esperará que no supere el número de milisegundos especificado en el *dwTimeOut* parámetro antes de devolver. Si *dwTimeOut* es infinito, `Lock` no regresará hasta que se obtiene acceso a un objeto o una condición especificada en *dwWakeMask* se cumplió. De lo contrario, si `Lock` fue capaz de adquirir un objeto de sincronización, devolverá correctamente; si no, devolverá un error.

##  <a name="unlock"></a>  CMultiLock::Unlock

Libera el objeto de sincronización que pertenecen a `CMultiLock`.

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Parámetros

*lCount*<br/>
Número de referencia recuentos liberar. Debe ser mayor que 0. Si la cantidad especificada produciría el recuento del objeto supere el máximo, no se cambia el recuento y la función devuelve FALSE.

*lPrevCount*<br/>
Señala a una variable que recibirá el recuento anterior para el objeto de sincronización. Si es NULL, no se devuelve el recuento anterior.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función se invoca `CMultiLock`del destructor.

El primer formulario del `Unlock` intenta desbloquear el objeto de sincronización administrado `CMultiLock`. La segunda forma de `Unlock` intenta desbloquear el `CSemaphore` objetos que pertenecen a `CMultiLock`. Si `CMultiLock` no posee cualquiera bloqueado `CSemaphore` objeto, la función devuelve FALSE; en caso contrario, devuelve TRUE. *lCount* y *lpPrevCount* son exactamente los mismos que los parámetros de [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock). La segunda forma de `Unlock` es rara vez aplicable a situaciones multilock.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)

