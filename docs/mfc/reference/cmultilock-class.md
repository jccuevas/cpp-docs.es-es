---
title: CMultiLock (clase)
ms.date: 11/04/2016
f1_keywords:
- CMultiLock
- AFXMT/CMultiLock
- AFXMT/CMultiLock::CMultiLock
- AFXMT/CMultiLock::IsLocked
- AFXMT/CMultiLock::Lock
- AFXMT/CMultiLock::Unlock
helpviewer_keywords:
- CMultiLock [MFC], CMultiLock
- CMultiLock [MFC], IsLocked
- CMultiLock [MFC], Lock
- CMultiLock [MFC], Unlock
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
ms.openlocfilehash: a051c6a510c53ac0c7c0a6efd8b4b5720080b264
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319709"
---
# <a name="cmultilock-class"></a>CMultiLock (clase)

Representa el mecanismo de control de acceso utilizado para controlar el acceso a los recursos en un programa de multithreading.

## <a name="syntax"></a>Sintaxis

```
class CMultiLock
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMultiLock::CMultiLock](#cmultilock)|Construye un objeto `CMultiLock`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMultiLock::Islocked](#islocked)|Determina si un objeto de sincronización específico de la matriz está bloqueado.|
|[CMultiLock::Bloqueo](#lock)|Espera en la matriz de objetos de sincronización.|
|[CMultiLock::Desbloquear](#unlock)|Libera los objetos de sincronización de propiedad.|

## <a name="remarks"></a>Observaciones

`CMultiLock`no tiene una clase base.

Para utilizar las clases de sincronización [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md)y [CEvent](../../mfc/reference/cevent-class.md), puede crear un `CMultiLock` objeto o [CSingleLock](../../mfc/reference/csinglelock-class.md) para esperar y liberar el objeto de sincronización. Utilícelo `CMultiLock` cuando haya varios objetos que pueda usar en un momento determinado. Utilícelo `CSingleLock` cuando solo necesite esperar en un objeto a la vez.

Para utilizar `CMultiLock` un objeto, primero cree una matriz de los objetos de sincronización en los que desea esperar. A continuación, `CMultiLock` llame al constructor del objeto dentro de una función miembro en la clase del recurso controlado. A continuación, llame a la [Lock](#lock) función miembro para determinar si un recurso está disponible (señalado). Si lo es, continúe con el resto de la función miembro. Si no hay ningún recurso disponible, espere a que se libere una cantidad de tiempo especificada para que se libere un recurso o devuelva un error. Una vez completado el uso de un recurso, llame a la función `CMultiLock` [Unlock](#unlock) si el `CMultiLock` objeto se va a utilizar de nuevo o permita que se destruya el objeto.

`CMultiLock`los objetos son más útiles `CEvent` cuando un subproceso tiene un gran número de objetos a los que puede responder. Cree una matriz `CEvent` que contenga todos `Lock`los punteros y llame a . Esto hará que el subproceso espere hasta que se señale uno de los eventos.

Para obtener más información `CMultiLock` sobre cómo utilizar objetos, vea el artículo [Multithreading: How to Use the Synchronization Classes](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CMultiLock`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmt.h

## <a name="cmultilockcmultilock"></a><a name="cmultilock"></a>CMultiLock::CMultiLock

Construye un objeto `CMultiLock`.

```
CMultiLock(
    CSyncObject* ppObjects [ ],
    DWORD dwCount,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Parámetros

*ppObjects*<br/>
Matriz de punteros a los objetos de sincronización que se van a esperar. No puede ser NULL.

*dwCount*<br/>
Número de objetos en *ppObjects*. Debe ser mayor que 0.

*bInitialLock*<br/>
Especifica si se debe intentar inicialmente tener acceso a cualquiera de los objetos proporcionados.

### <a name="remarks"></a>Observaciones

Esta función se llama después de crear la matriz de objetos de sincronización que se van a esperar. Normalmente se llama desde dentro del subproceso que debe esperar a que uno de los objetos de sincronización esté disponible.

## <a name="cmultilockislocked"></a><a name="islocked"></a>CMultiLock::Islocked

Determina si el objeto especificado no está señalizado (no está disponible).

```
BOOL IsLocked(DWORD dwItem);
```

### <a name="parameters"></a>Parámetros

*dwItem*<br/>
El índice de la matriz de objetos correspondiente al objeto cuyo estado se está consultando.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto especificado está bloqueado; de lo contrario 0.

## <a name="cmultilocklock"></a><a name="lock"></a>CMultiLock::Bloqueo

Llame a esta función para obtener acceso a uno o varios `CMultiLock` de los recursos controlados por los objetos de sincronización proporcionados al constructor.

```
DWORD Lock(
    DWORD dwTimeOut = INFINITE,
    BOOL bWaitForAll = TRUE,
    DWORD dwWakeMask = 0);
```

### <a name="parameters"></a>Parámetros

*dwTimeOut*<br/>
Especifica la cantidad de tiempo que debe esperar a que el objeto de sincronización esté disponible (señalizado). Si INFINITE, `Lock` esperará hasta que se señale el objeto antes de volver.

*bWaitForAll*<br/>
Especifica si todos los objetos esperados deben ser señalados al mismo tiempo antes de volver. Si FALSE, `Lock` se devolverá cuando se señale cualquiera de los objetos esperados.

*dwWakeMask*<br/>
Especifica otras condiciones que pueden anular la espera. Para obtener una lista completa de las opciones disponibles para este parámetro, vea [MsgWaitForMultipleObjects](/windows/win32/api/winuser/nf-winuser-msgwaitformultipleobjects) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Si `Lock` falla, devuelve - 1. Si se realiza correctamente, devuelve uno de los siguientes valores:

- Entre WAIT_OBJECT_0 y WAIT_OBJECT_0 + (número de objetos - 1)

   Si *bWaitForAll* es TRUE, se señalan todos los objetos (disponibles). Si *bWaitForAll* es FALSE, el valor devuelto - WAIT_OBJECT_0 es el índice de la matriz de objetos del objeto que se señala (disponible).

- WAIT_OBJECT_0 + (número de objetos)

   Un evento especificado en *dwWakeMask* está disponible en la cola de entrada del subproceso.

- Entre WAIT_ABANDONED_0 y WAIT_ABANDONED_0 + (número de objetos - 1)

   Si *bWaitForAll* es TRUE, se señalan todos los objetos y al menos uno de los objetos es un objeto de exclusión mutua abandonado. Si *bWaitForAll* es FALSE, el valor devuelto - WAIT_ABANDONED_0 es el índice en la matriz de objetos del objeto mutex abandonado que satisfizo la espera.

- WAIT_TIMEOUT

   El intervalo de tiempo de espera especificado en *dwTimeOut* expiró sin que la espera se realizara correctamente.

### <a name="remarks"></a>Observaciones

Si *bWaitForAll* es `Lock` TRUE, volverá correctamente tan pronto como todos los objetos de sincronización se señalen simultáneamente. Si *bWaitForAll* es `Lock` FALSE, volverá tan pronto como uno o varios de los objetos de sincronización se señale.

Si `Lock` no puede devolver inmediatamente, no esperará más que el número de milisegundos especificado en el parámetro *dwTimeOut* antes de devolver. Si *dwTimeOut* es `Lock` INFINITE, no se devolverá hasta que se obtenga el acceso a un objeto o se cumpla una condición especificada en *dwWakeMask.* De lo `Lock` contrario, si pudo adquirir un objeto de sincronización, se devolverá correctamente; si no, devolverá el fracaso.

## <a name="cmultilockunlock"></a><a name="unlock"></a>CMultiLock::Desbloquear

Libera el objeto `CMultiLock`de sincronización propiedad de .

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Parámetros

*lCount*<br/>
Número de recuentos de referencias que se han de liberar. Debe ser mayor que 0. Si el importe especificado haría que el recuento del objeto supere su máximo, el recuento no cambia y la función devuelve FALSE.

*lPrevCount*<br/>
Apunta a una variable para recibir el recuento anterior del objeto de sincronización. Si NULL, no se devuelve el recuento anterior.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función `CMultiLock`es llamada por 's destructor.

La primera `Unlock` forma de intento sin `CMultiLock`desbloqueo del objeto de sincronización administrado por . La segunda `Unlock` forma de `CSemaphore` intento sin desbloqueo de los objetos propiedad de `CMultiLock`. Si `CMultiLock` no posee `CSemaphore` ningún objeto bloqueado, la función devuelve FALSE; de lo contrario, devuelve TRUE. *lCount* y *lpPrevCount* son exactamente los mismos que los parámetros de [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock). La segunda `Unlock` forma de rara vez es aplicable a situaciones multibloqueo.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
