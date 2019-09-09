---
title: CEvent (clase)
ms.date: 11/04/2016
f1_keywords:
- CEvent
- AFXMT/CEvent
- AFXMT/CEvent::CEvent
- AFXMT/CEvent::PulseEvent
- AFXMT/CEvent::ResetEvent
- AFXMT/CEvent::SetEvent
- AFXMT/CEvent::Unlock
helpviewer_keywords:
- CEvent [MFC], CEvent
- CEvent [MFC], PulseEvent
- CEvent [MFC], ResetEvent
- CEvent [MFC], SetEvent
- CEvent [MFC], Unlock
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
ms.openlocfilehash: fbf2d834163199107aae44bd5723ceff79e36f91
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506688"
---
# <a name="cevent-class"></a>CEvent (clase)

Representa un evento, que es un objeto de sincronización que permite que un subproceso notifique a otro que se ha producido un evento.

## <a name="syntax"></a>Sintaxis

```
class CEvent : public CSyncObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CEvent::CEvent](#cevent)|Construye un objeto `CEvent`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CEvent::PulseEvent](#pulseevent)|Establece el evento en disponible (señalado), libera los subprocesos en espera y establece el evento en no disponible (no señalado).|
|[CEvent::ResetEvent](#resetevent)|Establece el evento en no disponible (no señalado).|
|[CEvent::SetEvent](#setevent)|Establece el evento en disponible (señalado) y libera los subprocesos en espera.|
|[CEvent::Unlock](#unlock)|Libera el objeto de evento.|

## <a name="remarks"></a>Comentarios

Los eventos son útiles cuando un subproceso debe saber cuándo realizar su tarea. Por ejemplo, un subproceso que copia datos en un archivo de datos debe recibir una notificación cuando haya nuevos datos disponibles. Al usar un `CEvent` objeto para notificar al subproceso de copia cuando hay nuevos datos disponibles, el subproceso puede realizar su tarea lo antes posible.

`CEvent`los objetos tienen dos tipos: manual y automático.

Un objeto `CEvent` automático vuelve automáticamente a un estado no señalado (no disponible) después de que se libere al menos un subproceso. De forma predeterminada, `CEvent` un objeto es automático a menos `TRUE` que se pase para el parámetro *bManualReset* durante la construcción.

Un objeto `CEvent` manual permanece en el estado establecido por [SetEvent](#setevent) o [ResetEvent](#resetevent) hasta que se llama a la otra función. Para crear un objeto `CEvent` manual, pase `TRUE` para el `bManualReset` parámetro durante la construcción.

Para usar un `CEvent` objeto, construya el `CEvent` objeto cuando sea necesario. Especifique el nombre del evento que desea esperar y especifique también que la aplicación debe ser la propietaria inicialmente. Después, puede tener acceso al evento cuando el constructor vuelva. Llame a [SetEvent](#setevent) para indicar (poner a disposición) el objeto de evento y, a continuación, llame a [Unlock](#unlock) cuando haya terminado de tener acceso al recurso controlado.

Un método alternativo para usar `CEvent` objetos es agregar una variable de tipo `CEvent` como miembro de datos a la clase que desea controlar. Durante la construcción del objeto controlado, llame al constructor del miembro `CEvent` de datos y especifique si el evento se señaliza inicialmente, y también specifythe el tipo de objeto de evento que desee, el nombre del evento (si se va a usar en el proceso. límites) y cualquier atributo de seguridad que desee.

Para tener acceso a un recurso controlado `CEvent` por un objeto de esta manera, cree primero una variable de tipo [CSingleLock](../../mfc/reference/csinglelock-class.md) o escriba [CMultiLock](../../mfc/reference/cmultilock-class.md) en el método de acceso del recurso. A continuación, `Lock` llame al método del objeto de bloqueo (por ejemplo, [CMultiLock:: Lock](../../mfc/reference/cmultilock-class.md#lock)). En este momento, el subproceso obtendrá acceso al recurso, esperará a que se libere el recurso y obtendrá acceso, o bien a esperar a que se libere el recurso, se agote el tiempo de espera y se produzca un error al obtener acceso al recurso. En cualquier caso, se ha tenido acceso a su recurso de una manera segura para subprocesos. Para liberar el recurso, llame `SetEvent` a para indicar el objeto de evento y, a `Unlock` continuación, use el método del objeto de bloqueo (por ejemplo, [CMultiLock:: Unlock](../../mfc/reference/cmultilock-class.md#unlock)) o deje que el objeto de bloqueo quede fuera del ámbito.

Para obtener más información sobre cómo usar `CEvent` objetos, vea [multithreading: Cómo usar las clases](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)de sincronización.

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]

[!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CEvent`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmt. h

##  <a name="cevent"></a>  CEvent::CEvent

Construye un `CEvent` objeto con nombre o sin nombre.

```
CEvent(
    BOOL bInitiallyOwn = FALSE,
    BOOL bManualReset = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Parámetros

*bInitiallyOwn*<br/>
Si es true, se habilita el `CMultilock` subproceso para el objeto o `CSingleLock` . De lo contrario, todos los subprocesos que deseen tener acceso al recurso deben esperar.

*bManualReset*<br/>
Si es TRUE, especifica que el objeto de evento es un evento manual; de lo contrario, el objeto de evento es un evento automático.

*lpszName*<br/>
Nombre del objeto `CEvent`. Se debe proporcionar si el objeto se va a utilizar en los límites del proceso. Si el nombre coincide con un evento existente, el constructor crea un `CEvent` nuevo objeto que hace referencia al evento de ese nombre. Si el nombre coincide con un objeto de sincronización existente que no es un evento, se producirá un error en la construcción. Si es NULL, el nombre será null.

*lpsaAttribute*<br/>
Atributos de seguridad para el objeto de evento. Para obtener una descripción completa de esta estructura, vea [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) en el Windows SDK.

### <a name="remarks"></a>Comentarios

Para obtener acceso a un `CEvent` objeto o liberarlo, cree un objeto [CMultiLock](../../mfc/reference/cmultilock-class.md) o [CSingleLock](../../mfc/reference/csinglelock-class.md) y llame a sus funciones miembro [Lock](../../mfc/reference/csinglelock-class.md#lock) y [unlock.](../../mfc/reference/csinglelock-class.md#unlock)

Para cambiar el estado de un `CEvent` objeto a señalado (los subprocesos no tienen que esperar), llame a [SetEvent](#setevent) o [PulseEvent](#pulseevent). Para establecer el estado de un `CEvent` objeto en no señalado (los subprocesos deben esperar), llame a [ResetEvent](#resetevent).

> [!IMPORTANT]
>  Después de crear `CEvent` el objeto, utilice [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para asegurarse de que la exclusión mutua todavía no existe. Si la exclusión mutua existía de manera inesperada, puede indicar que un proceso no autorizado es Squatting y puede estar intentando usar la exclusión mutua de forma malintencionada. En este caso, el procedimiento recomendado para la seguridad es cerrar el identificador y continuar como si se produjera un error al crear el objeto.

##  <a name="pulseevent"></a>  CEvent::PulseEvent

Establece el estado del evento en señalado (disponible), libera todos los subprocesos en espera y lo restablece en no señalado (no disponible) automáticamente.

```
BOOL PulseEvent();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Si el evento es manual, se liberan todos los subprocesos en espera, el evento se establece en `PulseEvent` no señalado y devuelve. Si el evento es automático, se libera un único subproceso, el evento se establece en no señalado y `PulseEvent` devuelve.

Si no hay subprocesos en espera, o no se puede liberar `PulseEvent` ningún subproceso inmediatamente, establece el estado del evento en no señalado y devuelve.

`PulseEvent`usa la función de `PulseEvent` Win32 subyacente, que se puede quitar momentáneamente del estado de espera mediante una llamada a procedimiento asincrónico en modo kernel. Por lo `PulseEvent` tanto, no es confiable y no debe usarse en las nuevas aplicaciones. Para obtener más información, vea la [función PulseEvent](/windows/win32/api/winbase/nf-winbase-pulseevent).

##  <a name="resetevent"></a>  CEvent::ResetEvent

Establece el estado del evento en no señalado hasta que se establece explícitamente en señalado por la función miembro [SetEvent](#setevent) .

```
BOOL ResetEvent();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Esto hace que todos los subprocesos que deseen tener acceso a este evento esperen.

Los eventos automáticos no utilizan esta función miembro.

##  <a name="setevent"></a>  CEvent::SetEvent

Establece el estado del evento en señalado, liberando todos los subprocesos en espera.

```
BOOL SetEvent();
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Si el evento es manual, el evento permanecerá señalado hasta que se llame a [ResetEvent](#resetevent) . En este caso se puede liberar más de un subproceso. Si el evento es automático, el evento permanecerá señalado hasta que se libere un único subproceso. El sistema establecerá el estado del evento en no señalado. Si no hay subprocesos en espera, el estado permanece señalado hasta que se libera un subproceso.

##  <a name="unlock"></a>  CEvent::Unlock

Libera el objeto de evento.

```
BOOL Unlock();
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si el subproceso poseía el objeto de evento y el evento es un evento automático; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La llamada a esta función miembro la realizan los subprocesos que actualmente poseen un evento automático para liberarla una vez que se han hecho, si el objeto de bloqueo se va a volver a usar. Si el objeto de bloqueo no se va a volver a usar, el destructor del objeto de bloqueo llamará a esta función.

## <a name="see-also"></a>Vea también

[CSyncObject (clase)](../../mfc/reference/csyncobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
