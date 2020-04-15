---
title: Clase CEvent
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
ms.openlocfilehash: 009a17342cb92025d67bf2fe0df1b9d5c7c0c6f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373955"
---
# <a name="cevent-class"></a>Clase CEvent

Representa un evento, que es un objeto de sincronización que permite a un subproceso notificar a otro que se ha producido un evento.

## <a name="syntax"></a>Sintaxis

```
class CEvent : public CSyncObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CEvent::CEvent](#cevent)|Construye un objeto `CEvent`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CEvent::PulseEvent](#pulseevent)|Establece el evento en disponible (señalizado), libera subprocesos en espera y establece el evento en no disponible (sin señales).|
|[CEvent::ResetEvent](#resetevent)|Establece el evento en no disponible (sin señal).|
|[CEvent::SetEvent](#setevent)|Establece el evento en disponible (señalizado) y libera los subprocesos en espera.|
|[CEvent::Desbloqueo](#unlock)|Libera el objeto de evento.|

## <a name="remarks"></a>Observaciones

Los eventos son útiles cuando un subproceso debe saber cuándo realizar su tarea. Por ejemplo, un subproceso que copia datos en un archivo de datos debe recibir una notificación cuando haya nuevos datos disponibles. Mediante el `CEvent` uso de un objeto para notificar al subproceso de copia cuando hay nuevos datos disponibles, el subproceso puede realizar su tarea lo antes posible.

`CEvent`los objetos tienen dos tipos: manual y automático.

Un `CEvent` objeto automático vuelve automáticamente a un estado no señalizado (no disponible) después de liberar al menos un subproceso. De forma `CEvent` predeterminada, un objeto `TRUE` es automático a menos que pase el parámetro *bManualReset* durante la construcción.

Un `CEvent` objeto manual permanece en el estado establecido por [SetEvent](#setevent) o [ResetEvent](#resetevent) hasta que se llama a la otra función. Para crear `CEvent` un objeto `TRUE` manual, pase el parámetro durante la `bManualReset` construcción.

Para utilizar `CEvent` un objeto, construya el `CEvent` objeto cuando sea necesario. Especifique el nombre del evento en el que desea esperar y especifique también que la aplicación debe poseerlo inicialmente. A continuación, puede tener acceso al evento cuando se devuelve el constructor. Llame a [SetEvent](#setevent) para señalar (poner a disposición) el objeto de evento y, a continuación, llame a [Unlock](#unlock) cuando haya terminado de acceder al recurso controlado.

Un método alternativo `CEvent` para usar objetos `CEvent` es agregar una variable de tipo como miembro de datos a la clase que desea controlar. Durante la construcción del objeto controlado, `CEvent` llame al constructor del miembro de datos y especifique si el evento se señala inicialmente y también especifique el tipo de objeto de evento que desea, el nombre del evento (si se usará a través de los límites del proceso) y los atributos de seguridad que desee.

Para tener acceso a `CEvent` un recurso controlado por un objeto de esta manera, primero cree una variable de tipo [CSingleLock](../../mfc/reference/csinglelock-class.md) o [cMultiLock](../../mfc/reference/cmultilock-class.md) en el método de acceso del recurso. A continuación, llame al `Lock` método del objeto lock (por ejemplo, [CMultiLock::Lock](../../mfc/reference/cmultilock-class.md#lock)). En este punto, el subproceso obtendrá acceso al recurso, esperará a que el recurso se libere y obtenga acceso, o esperará a que el recurso se libere, tiempo de espera y no pueda obtener acceso al recurso. En cualquier caso, se ha tenido acceso al recurso de forma segura para subprocesos. Para liberar el `SetEvent` recurso, llame para señalar el `Unlock` objeto de evento y, a continuación, utilice el método del objeto lock (por ejemplo, [CMultiLock::Unlock](../../mfc/reference/cmultilock-class.md#unlock)) o deje que el objeto de bloqueo quede fuera del ámbito.

Para obtener más información `CEvent` sobre cómo utilizar objetos, vea [Multithreading: How to Use the Synchronization Classes](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]

[!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CEvent`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmt.h

## <a name="ceventcevent"></a><a name="cevent"></a>CEvent::CEvent

Construye un objeto con `CEvent` nombre o sin nombre.

```
CEvent(
    BOOL bInitiallyOwn = FALSE,
    BOOL bManualReset = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Parámetros

*bInitiallyOwn*<br/>
Si es TRUE, `CMultilock` el `CSingleLock` subproceso para el objeto o está habilitado. De lo contrario, todos los subprocesos que deseen tener acceso al recurso deben esperar.

*bManualReset*<br/>
Si TRUE, especifica que el objeto de evento es un evento manual, de lo contrario el objeto de evento es un evento automático.

*lpszName*<br/>
Nombre del objeto `CEvent`. Debe proporcionarse si el objeto se utilizará a través de los límites del proceso. Si el nombre coincide con un evento `CEvent` existente, el constructor crea un nuevo objeto que hace referencia al evento de ese nombre. Si el nombre coincide con un objeto de sincronización existente que no es un evento, se producirá un error en la construcción. Si NULL, el nombre será null.

*lpsaAttribute*<br/>
Atributos de seguridad para el objeto de evento. Para obtener una descripción completa de esta estructura, vea [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) en el Windows SDK.

### <a name="remarks"></a>Observaciones

Para tener acceso `CEvent` o liberar un objeto, cree un [CMultiLock](../../mfc/reference/cmultilock-class.md) o [CSingleLock](../../mfc/reference/csinglelock-class.md) objeto y llame a su [Lock](../../mfc/reference/csinglelock-class.md#lock) y [Unlock](../../mfc/reference/csinglelock-class.md#unlock) funciones miembro.

Para cambiar el `CEvent` estado de un objeto a señalado (los subprocesos no tienen que esperar), llame a [SetEvent](#setevent) o [PulseEvent](#pulseevent). Para establecer el `CEvent` estado de un objeto en no señalizado (los subprocesos deben esperar), llame a [ResetEvent](#resetevent).

> [!IMPORTANT]
> Después `CEvent` de crear el objeto, use [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para asegurarse de que la exclusión mutua aún no existía. Si la exclusión mutua existió inesperadamente, puede indicar que un proceso pícaro está en cuclillas y puede tener la intención de utilizar la exclusión mutua maliciosamente. En este caso, el procedimiento recomendado para la seguridad es cerrar el identificador y continuar como si se hubiera producido un error al crear el objeto.

## <a name="ceventpulseevent"></a><a name="pulseevent"></a>CEvent::PulseEvent

Establece el estado del evento en señalado (disponible), libera los subprocesos en espera y lo restablece automáticamente a no señalizado (no disponible).

```
BOOL PulseEvent();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si el evento es manual, se liberan todos los subprocesos `PulseEvent` en espera, el evento se establece en sin señal y devuelve. Si el evento es automático, se libera un único subproceso, `PulseEvent` el evento se establece en nonsignaled y devuelve.

Si no hay subprocesos en espera o `PulseEvent` no se puede liberar ningún subproceso inmediatamente, establece el estado del evento en no señalizado y devuelve.

`PulseEvent`utiliza la función `PulseEvent` Win32 subyacente, que se puede quitar momentáneamente del estado de espera mediante una llamada a procedimiento asincrónico en modo kernel. Por `PulseEvent` lo tanto, no es confiable y no debe ser utilizado por nuevas aplicaciones. Para obtener más información, consulte la [función PulseEvent](/windows/win32/api/winbase/nf-winbase-pulseevent).

## <a name="ceventresetevent"></a><a name="resetevent"></a>CEvent::ResetEvent

Establece el estado del evento en no señalizado hasta que se establece explícitamente en señalado por el [SetEvent](#setevent) función miembro.

```
BOOL ResetEvent();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esto hace que todos los subprocesos que deseen tener acceso a este evento esperen.

Esta función miembro no se utiliza en eventos automáticos.

## <a name="ceventsetevent"></a><a name="setevent"></a>CEvent::SetEvent

Establece el estado del evento en señalado, liberando los subprocesos en espera.

```
BOOL SetEvent();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente, de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si el evento es manual, el evento permanecerá señalado hasta que se llame a [ResetEvent.](#resetevent) En este caso, se puede liberar más de un subproceso. Si el evento es automático, el evento permanecerá señalado hasta que se libere un único subproceso. A continuación, el sistema establecerá el estado del evento en no señalizado. Si no hay subprocesos en espera, el estado permanece señalado hasta que se libera un subproceso.

## <a name="ceventunlock"></a><a name="unlock"></a>CEvent::Desbloqueo

Libera el objeto de evento.

```
BOOL Unlock();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el subproceso es propietario del objeto de evento y el evento es un evento automático; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Los subprocesos que actualmente poseen un evento automático para liberarlo después de que se hayan realizado, llamen a esta función miembro si se va a reutilizar. Si el objeto de bloqueo no se va a reutilizar, el destructor del objeto de bloqueo llamará a esta función.

## <a name="see-also"></a>Consulte también

[Clase CSyncObject](../../mfc/reference/csyncobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
