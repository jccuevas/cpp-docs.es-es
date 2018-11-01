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
ms.openlocfilehash: 883f3065c9d15ad793e6c0d548b911f10d166c0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667906"
---
# <a name="cevent-class"></a>CEvent (clase)

Representa un evento, que es un objeto de sincronización que permite que un subproceso notifique a otro que se ha producido un evento.

## <a name="syntax"></a>Sintaxis

```
class CEvent : public CSyncObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CEvent::CEvent](#cevent)|Construye un objeto `CEvent`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CEvent::PulseEvent](#pulseevent)|Conjuntos de señala el evento a disponible (), libera los subprocesos en espera y establece el evento como no disponible (no señalizado).|
|[CEvent::ResetEvent](#resetevent)|Establece el evento como no disponible (no señalizado).|
|[CEvent::SetEvent](#setevent)|Establece el evento en disponibles (señalado) y libera todos los subprocesos en espera.|
|[CEvent::Unlock](#unlock)|Libera el objeto de evento.|

## <a name="remarks"></a>Comentarios

Los eventos son útiles cuando un subproceso debe saber cuándo se debe llevar a cabo su tarea. Por ejemplo, un subproceso que copia datos en un archivo de datos se notificará cuando hay nuevos datos disponibles. Mediante el uso de un `CEvent` objeto para notificarlo al subproceso de copia cuando hay nuevos datos disponibles, el subproceso puede realizar sus tareas tan pronto como sea posible.

`CEvent` los objetos tienen dos tipos: automática y manual.

Automáticos `CEvent` objeto vuelve automáticamente a un estado (no disponible) no señalado después del lanzamiento de al menos un subproceso. De forma predeterminada, un `CEvent` objeto es automático a menos que pase `TRUE` para el *bManualReset* parámetro durante la construcción.

Un manual `CEvent` objeto permanece en el estado establecido mediante [SetEvent](#setevent) o [ResetEvent](#resetevent) hasta que se llama a otra función. Para crear un manual `CEvent` de objetos, pasar `TRUE` para el `bManualReset` parámetro durante la construcción.

Para usar un `CEvent` objeto, construya el `CEvent` objeto cuando sea necesario. Especifique el nombre del evento que desea esperar y también especificar que la aplicación debe inicialmente el propietario. A continuación, puede tener acceso el evento cuando se devuelve el constructor. Llame a [SetEvent](#setevent) a señal (hacer disponible) el objeto de evento y, después, llame [Unlock](#unlock) cuando haya terminado acceder al recurso controlado.

Un método alternativo para el uso de `CEvent` objetos consiste en Agregar una variable de tipo `CEvent` como un miembro de datos a la clase que desea controlar. Durante la construcción del objeto controlado, llame al constructor de la `CEvent` miembro de datos y especificar si el evento se señala inicialmente y también specifythe tipo de objeto de evento que desea, el nombre del evento (si se usará en proceso los límites) y todos los atributos de seguridad que desee.

Para obtener acceso a un recurso controlado por un `CEvent` objeto de esta manera, primero cree una variable de cualquier tipo [CSingleLock](../../mfc/reference/csinglelock-class.md) o tipo [CMultiLock](../../mfc/reference/cmultilock-class.md) en el método de acceso del recurso. A continuación, llame a la `Lock` método del objeto de bloqueo (por ejemplo, [CMultiLock::Lock](../../mfc/reference/cmultilock-class.md#lock)). En este momento, el subproceso se ya sea obtener acceso a los recursos, espere a que el recurso para liberarse y obtener acceso o espere a que se libere el recurso, tiempo de espera y no se pudo obtener acceso al recurso. En cualquier caso, se obtuvo acceso a los recursos de una manera segura para subprocesos. Para liberar el recurso, llame a `SetEvent` para indicar el objeto de evento y, a continuación, utilice el `Unlock` método del objeto de bloqueo (por ejemplo, [CMultiLock::Unlock](../../mfc/reference/cmultilock-class.md#unlock)), o dejar que el objeto de bloqueo se encuentran fuera del ámbito.

Para obtener más información sobre cómo usar `CEvent` objetos, vea [Multithreading: uso de las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]

[!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CEvent`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmt.h

##  <a name="cevent"></a>  CEvent::CEvent

Construye una con o sin nombre `CEvent` objeto.

```
CEvent(
    BOOL bInitiallyOwn = FALSE,
    BOOL bManualReset = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Parámetros

*bInitiallyOwn*<br/>
Si es TRUE, el subproceso para el `CMultilock` o `CSingleLock` objeto está habilitado. En caso contrario, deben esperar todos los subprocesos que deseen tener acceso al recurso.

*bManualReset*<br/>
Si es TRUE, especifica que el objeto de evento es un evento manual, de lo contrario, el objeto de evento es un evento automático.

*lpszName*<br/>
Nombre del objeto `CEvent`. Se debe proporcionar si el objeto que se va a utilizar los límites del proceso. Si el nombre coincide con un evento existente, el constructor crea un nuevo `CEvent` objeto que hace referencia a los eventos de ese nombre. Si el nombre coincide con un objeto de sincronización existente que no es un evento, se producirá un error en la construcción. Si es NULL, el nombre será null.

*lpsaAttribute*<br/>
Atributos de seguridad para el objeto de evento. Para obtener una descripción completa de esta estructura, vea [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) en el SDK de Windows.

### <a name="remarks"></a>Comentarios

Para obtener acceso a o liberar una `CEvent` , cree un [CMultiLock](../../mfc/reference/cmultilock-class.md) o [CSingleLock](../../mfc/reference/csinglelock-class.md) objeto y llamar a su [bloqueo](../../mfc/reference/csinglelock-class.md#lock) y [Unlock](../../mfc/reference/csinglelock-class.md#unlock) funciones de miembro.

Para cambiar el estado de un `CEvent` objeto marcado (subprocesos no tienen que esperar), llame a [SetEvent](#setevent) o [PulseEvent](#pulseevent). Para establecer el estado de un `CEvent` objeto en no señalado (subprocesos deben esperar), llame a [ResetEvent](#resetevent).

> [!IMPORTANT]
>  Después de crear el `CEvent` de objeto, utilice [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) para asegurarse de que ya no existe la exclusión mutua. Si la exclusión mutua existía inesperadamente, puede indicar un proceso invasor es uso inapropiado y es posible que pretende usar la exclusión mutua de forma malintencionada. En este caso, el procedimiento recomendado de preocupados por la seguridad es cerrar el identificador y continuar como si se produjo un error en la creación del objeto.

##  <a name="pulseevent"></a>  CEvent::PulseEvent

Establece el estado del evento en señalado (disponible), libera los subprocesos en espera y la restablece en no señalado (no disponible) automáticamente.

```
BOOL PulseEvent();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Si el evento es manual, se liberan todos los subprocesos en espera, el evento está establecido en no señalado, y `PulseEvent` devuelve. Si el evento es automático, se libera un único subproceso, el evento está establecido en no señalado, y `PulseEvent` devuelve.

Si no hay subprocesos en espera o no se puede liberar inmediatamente, no hay ningún subproceso `PulseEvent` establece el estado del evento en no señalado y devuelve.

`PulseEvent` usa Win32 subyacente `PulseEvent` función, que se puede quitar momentáneamente desde el estado de espera por una llamada a procedimiento asincrónico de modo kernel. Por lo tanto, `PulseEvent` es confiable y no debe usarse en aplicaciones nuevas. Para obtener más información, consulte el [PulseEvent función](/windows/desktop/api/winbase/nf-winbase-pulseevent).

##  <a name="resetevent"></a>  CEvent::ResetEvent

Establece el estado del evento en no señalado hasta que establezca explícitamente como señalado por el [SetEvent](#setevent) función miembro.

```
BOOL ResetEvent();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esto hace que todos los subprocesos que deseen tener acceso a este evento debe esperar.

Esta función miembro no se utiliza por eventos automáticos.

##  <a name="setevent"></a>  CEvent::SetEvent

Establece el estado del evento en señalado, liberar los subprocesos en espera.

```
BOOL SetEvent();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente, en caso contrario, 0.

### <a name="remarks"></a>Comentarios

Si el evento es manual, el evento permanecerá señalado hasta que [ResetEvent](#resetevent) se llama. Más de un subproceso puede liberarse en este caso. Si el evento es automático, el evento permanecerá señalado hasta que se libere un subproceso único. El sistema, a continuación, establecerá el estado del evento en no señalado. Si no hay ningún subproceso en espera, el estado permanece señalado hasta que se libere un subproceso.

##  <a name="unlock"></a>  CEvent::Unlock

Libera el objeto de evento.

```
BOOL Unlock();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el subproceso pertenece el objeto de evento y el evento es un evento automático; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función miembro llama a subprocesos que actualmente poseen un evento para liberar una vez terminados, si es su objeto de bloqueo para volverse a automático. Si el objeto de bloqueo no se reutilizan, esta función llamará al destructor del objeto de bloqueo.

## <a name="see-also"></a>Vea también

[CSyncObject (clase)](../../mfc/reference/csyncobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)

