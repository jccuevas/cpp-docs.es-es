---
title: Clase CMultiLock
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
ms.openlocfilehash: b2fe3ecf2197b8edb13e89600b16e550deff9af2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504551"
---
# <a name="cmultilock-class"></a>Clase CMultiLock

Representa el mecanismo de control de acceso utilizado para controlar el acceso a los recursos en un programa de multithreading.

## <a name="syntax"></a>Sintaxis

```
class CMultiLock
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMultiLock::CMultiLock](#cmultilock)|Construye un objeto `CMultiLock`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMultiLock::IsLocked](#islocked)|Determina si un objeto de sincronización concreto de la matriz está bloqueado.|
|[CMultiLock::Lock](#lock)|Espera en la matriz de objetos de sincronización.|
|[CMultiLock::Unlock](#unlock)|Libera cualquier objeto de sincronización de propiedad.|

## <a name="remarks"></a>Comentarios

`CMultiLock`no tiene una clase base.

Para usar las clases de sincronización [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md)y [CEvent](../../mfc/reference/cevent-class.md), puede crear un `CMultiLock` objeto o [CSingleLock](../../mfc/reference/csinglelock-class.md) para esperar y liberar el objeto de sincronización. Use `CMultiLock` cuando haya varios objetos que pueda usar en un momento determinado. Use `CSingleLock` cuando solo necesite esperar en un objeto cada vez.

Para usar un `CMultiLock` objeto, cree primero una matriz de los objetos de sincronización en los que desea esperar. A continuación, llame `CMultiLock` al constructor del objeto dentro de una función miembro en la clase del recurso controlado. A continuación, llame a la función miembro [Lock](#lock) para determinar si un recurso está disponible (señalado). Si una es, continúe con el resto de la función miembro. Si no hay ningún recurso disponible, espere durante un período de tiempo especificado para que se libere un recurso o devuelva un error. Una vez completado el uso de un recurso, puede llamar a la función de `CMultiLock` [desbloqueo](#unlock) si el objeto se va a usar `CMultiLock` de nuevo o permitir que se destruya el objeto.

`CMultiLock`los objetos son más útiles cuando un subproceso tiene un gran `CEvent` número de objetos a los que puede responder. Cree una matriz que contenga `CEvent` todos los punteros y `Lock`llame a. Esto hará que el subproceso espere hasta que se señale uno de los eventos.

Para obtener más información sobre cómo usar `CMultiLock` objetos, vea el artículo [multithreading: Cómo usar las clases](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)de sincronización.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CMultiLock`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmt. h

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
Matriz de punteros a los objetos de sincronización en los que se va a esperar. No puede ser nulo.

*dwCount*<br/>
Número de objetos de *ppObjects*. Debe ser mayor que 0.

*bInitialLock*<br/>
Especifica si se intentará inicialmente obtener acceso a cualquiera de los objetos proporcionados.

### <a name="remarks"></a>Comentarios

Se llama a esta función después de crear la matriz de objetos de sincronización en los que se va a esperar. Normalmente se llama desde dentro del subproceso que debe esperar a que uno de los objetos de sincronización esté disponible.

##  <a name="islocked"></a>  CMultiLock::IsLocked

Determina si el objeto especificado no tiene señal (no disponible).

```
BOOL IsLocked(DWORD dwItem);
```

### <a name="parameters"></a>Parámetros

*dwItem*<br/>
Índice de la matriz de objetos correspondiente al objeto cuyo estado se está consultando.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto especificado está bloqueado; de lo contrario, es 0.

##  <a name="lock"></a>  CMultiLock::Lock

Llame a esta función para obtener acceso a uno o varios de los recursos controlados por los objetos de sincronización suministrados al `CMultiLock` constructor.

```
DWORD Lock(
    DWORD dwTimeOut = INFINITE,
    BOOL bWaitForAll = TRUE,
    DWORD dwWakeMask = 0);
```

### <a name="parameters"></a>Parámetros

*dwTimeOut*<br/>
Especifica la cantidad de tiempo que hay que esperar a que el objeto de sincronización esté disponible (señalado). Si es infinito `Lock` , esperará hasta que el objeto se señale antes de la devolución.

*bWaitForAll*<br/>
Especifica si todos los objetos esperados se deben señalizar al mismo tiempo antes de devolver. Si es false `Lock` , devolverá cuando se señale cualquiera de los objetos esperados.

*dwWakeMask*<br/>
Especifica otras condiciones que pueden anular la espera. Para obtener una lista completa de las opciones disponibles para este parámetro, vea [MsgWaitForMultipleObjects](/windows/win32/api/winuser/nf-winuser-msgwaitformultipleobjects) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Si `Lock` produce un error, devuelve-1. Si se realiza correctamente, devuelve uno de los siguientes valores:

- Entre WAIT_OBJECT_0 y WAIT_OBJECT_0 + (número de objetos-1)

   Si *bWaitForAll* es true, todos los objetos se señalizan (disponibles). Si *bWaitForAll* es false, el valor devuelto-WAIT_OBJECT_0 es el índice de la matriz de objetos del objeto que está señalado (disponible).

- WAIT_OBJECT_0 + (número de objetos)

   Un evento especificado en *dwWakeMask* está disponible en la cola de entrada del subproceso.

- Entre WAIT_ABANDONED_0 y WAIT_ABANDONED_0 + (número de objetos-1)

   Si *bWaitForAll* es true, se señalizan todos los objetos y al menos uno de los objetos es un objeto mutex abandonado. Si *bWaitForAll* es false, el valor devuelto-WAIT_ABANDONED_0 es el índice de la matriz de objetos del objeto de exclusión mutua abandonada que cumplía la espera.

- WAIT_TIMEOUT

   El intervalo de tiempo de espera especificado en *dwTimeOut* expiró sin la espera realizada correctamente.

### <a name="remarks"></a>Comentarios

Si *bWaitForAll* es true, `Lock` se devolverá correctamente en cuanto todos los objetos de sincronización se señalen simultáneamente. Si *bWaitForAll* es false, `Lock` devolverá en cuanto se señale uno o varios objetos de sincronización.

Si `Lock` no puede volver inmediatamente, esperará hasta que no haya más del número de milisegundos especificado en el parámetro *dwTimeOut* antes de devolver. Si *dwTimeOut* es infinito, `Lock` no devolverá hasta que se obtenga el acceso a un objeto o se cumpla una condición especificada en *dwWakeMask* . De lo contrario `Lock` , si era capaz de adquirir un objeto de sincronización, se devolverá correctamente; si no es así, devolverá un error.

##  <a name="unlock"></a>  CMultiLock::Unlock

Libera el objeto de sincronización que `CMultiLock`es propiedad de.

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Parámetros

*lCount*<br/>
Número de recuentos de referencias que se van a liberar. Debe ser mayor que 0. Si la cantidad especificada hiciera que el recuento del objeto superara su máximo, no se cambia el recuento y la función devuelve FALSE.

*lPrevCount*<br/>
Apunta a una variable para recibir el recuento anterior del objeto de sincronización. Si es NULL, no se devuelve el recuento anterior.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

El destructor `CMultiLock`de llama a esta función.

La primera forma de `Unlock` intenta desbloquear el objeto de sincronización administrado por `CMultiLock`. La segunda forma de `Unlock` intenta desbloquear los `CSemaphore` objetos que son propiedad `CMultiLock`de. Si `CMultiLock` no posee ningún objeto bloqueado `CSemaphore` , la función devuelve false; de lo contrario, devuelve true. *lCount* y *lpPrevCount* son exactamente iguales que los parámetros de [CSingleLock:: Unlock](../../mfc/reference/csinglelock-class.md#unlock). La segunda forma de `Unlock` no suele ser aplicable a las situaciones de multibloqueo.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
