---
title: Clase COleMessageFilter
ms.date: 11/04/2016
f1_keywords:
- COleMessageFilter
- AFXOLE/COleMessageFilter
- AFXOLE/COleMessageFilter::COleMessageFilter
- AFXOLE/COleMessageFilter::BeginBusyState
- AFXOLE/COleMessageFilter::EnableBusyDialog
- AFXOLE/COleMessageFilter::EnableNotRespondingDialog
- AFXOLE/COleMessageFilter::EndBusyState
- AFXOLE/COleMessageFilter::OnMessagePending
- AFXOLE/COleMessageFilter::Register
- AFXOLE/COleMessageFilter::Revoke
- AFXOLE/COleMessageFilter::SetBusyReply
- AFXOLE/COleMessageFilter::SetMessagePendingDelay
- AFXOLE/COleMessageFilter::SetRetryReply
helpviewer_keywords:
- COleMessageFilter [MFC], COleMessageFilter
- COleMessageFilter [MFC], BeginBusyState
- COleMessageFilter [MFC], EnableBusyDialog
- COleMessageFilter [MFC], EnableNotRespondingDialog
- COleMessageFilter [MFC], EndBusyState
- COleMessageFilter [MFC], OnMessagePending
- COleMessageFilter [MFC], Register
- COleMessageFilter [MFC], Revoke
- COleMessageFilter [MFC], SetBusyReply
- COleMessageFilter [MFC], SetMessagePendingDelay
- COleMessageFilter [MFC], SetRetryReply
ms.assetid: b1fd1639-fac4-4fd0-bf17-15172deba13c
ms.openlocfilehash: f6db5f012aedf08edd87980e304e181295bfb953
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374923"
---
# <a name="colemessagefilter-class"></a>Clase COleMessageFilter

Administra la simultaneidad requerida por la interacción de aplicaciones OLE.

## <a name="syntax"></a>Sintaxis

```
class COleMessageFilter : public CCmdTarget
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleMessageFilter::COleMessageFilter](#colemessagefilter)|Construye un objeto `COleMessageFilter`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleMessageFilter::BeginBusyState](#beginbusystate)|Coloca la aplicación en estado ocupado.|
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|Habilita y deshabilita el cuadro de diálogo que aparece cuando una aplicación llamada está ocupada.|
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|Habilita y deshabilita el cuadro de diálogo que aparece cuando una aplicación llamada no responde.|
|[COleMessageFilter::EndBusyState](#endbusystate)|Termina el estado ocupado de la aplicación.|
|[COleMessageFilter::OnMessagePending](#onmessagepending)|Llamado por el marco de trabajo para procesar mensajes mientras una llamada OLE está en curso.|
|[COleMessageFilter::Register](#register)|Registra el filtro de mensajes con los archivos DLL del sistema OLE.|
|[COleMessageFilter::Revoke](#revoke)|Revoca el registro del filtro de mensajes con los archivos DLL del sistema OLE.|
|[COleMessageFilter::SetBusyReply](#setbusyreply)|Determina la respuesta de la aplicación ocupada a una llamada OLE.|
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|Determina cuánto tiempo espera la aplicación una respuesta a una llamada OLE.|
|[COleMessageFilter::SetRetryReply](#setretryreply)|Determina la respuesta de la aplicación que realiza la llamada a una aplicación ocupada.|

## <a name="remarks"></a>Observaciones

La `COleMessageFilter` clase es útil en aplicaciones de servidor y contenedor de edición visual, así como en aplicaciones de automatización OLE. Para las aplicaciones de servidor a las que se llama, esta clase se puede usar para que la aplicación esté "ocupada" para que las llamadas entrantes de otras aplicaciones de contenedor se cancelen o se vuelvan a intentar más adelante. Esta clase también se puede utilizar para determinar la acción que debe realizar una aplicación que realiza la llamada cuando la aplicación llamada está ocupada.

Uso común es para una aplicación de servidor llamar a [BeginBusyState](#beginbusystate) y [EndBusyState](#endbusystate) cuando sería peligroso para un documento u otro objeto accesible OLE que se destruira. Estas llamadas se realizan en [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle) durante las actualizaciones de la interfaz de usuario.

De forma `COleMessageFilter` predeterminada, se asigna un objeto cuando se inicializa la aplicación. Se puede recuperar con [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).

Esta es una clase avanzada; rara vez necesita sordecir trabajar con él directamente.

Para obtener más información, consulte el artículo [Servidores: implementar un servidor](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleMessageFilter`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

## <a name="colemessagefilterbeginbusystate"></a><a name="beginbusystate"></a>COleMessageFilter::BeginBusyState

Llame a esta función para comenzar un estado de ocupado.

```
virtual void BeginBusyState();
```

### <a name="remarks"></a>Observaciones

Funciona junto con [EndBusyState](#endbusystate) para controlar el estado ocupado de la aplicación. La función [SetBusyReply](#setbusyreply) determina la respuesta de la aplicación a las aplicaciones que llaman cuando está ocupada.

El `BeginBusyState` `EndBusyState` y llama incrementan y disminuyen, respectivamente, un contador que determina si la aplicación está ocupada. Por ejemplo, dos `BeginBusyState` llamadas `EndBusyState` y una llamada para seguir resultando en un estado ocupado. Para cancelar un estado ocupado `EndBusyState` es necesario llamar `BeginBusyState` al mismo número de veces que se ha llamado.

De forma predeterminada, el marco de trabajo entra en el estado de disponibilidad durante el procesamiento inactivo, que se realiza mediante [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Mientras la aplicación controla las notificaciones ON_COMMANDUPDATEUI, las llamadas entrantes se controlan más adelante, una vez completado el procesamiento inactivo.

## <a name="colemessagefiltercolemessagefilter"></a><a name="colemessagefilter"></a>COleMessageFilter::COleMessageFilter

Crea un objeto `COleMessageFilter` .

```
COleMessageFilter();
```

## <a name="colemessagefilterenablebusydialog"></a><a name="enablebusydialog"></a>COleMessageFilter::EnableBusyDialog

Habilita y deshabilita el cuadro de diálogo ocupado, que se muestra cuando expira el retraso pendiente de mensaje (consulte [SetRetryReply](#setretryreply)) durante una llamada OLE.

```
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnableBusy*<br/>
Especifica si el cuadro de diálogo "ocupado" está habilitado o deshabilitado.

## <a name="colemessagefilterenablenotrespondingdialog"></a><a name="enablenotrespondingdialog"></a>COleMessageFilter::EnableNotRespondingDialog

Habilita y deshabilita el cuadro de diálogo "no responde", que se muestra si un mensaje de teclado o mouse está pendiente durante una llamada OLE y se ha agotado el tiempo de espera de la llamada.

```
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnableNotResponding*<br/>
Especifica si el cuadro de diálogo "no responder" está habilitado o deshabilitado.

## <a name="colemessagefilterendbusystate"></a><a name="endbusystate"></a>COleMessageFilter::EndBusyState

Llame a esta función para finalizar un estado de ocupado.

```
virtual void EndBusyState();
```

### <a name="remarks"></a>Observaciones

Funciona junto con [BeginBusyState](#beginbusystate) para controlar el estado ocupado de la aplicación. La función [SetBusyReply](#setbusyreply) determina la respuesta de la aplicación a las aplicaciones que llaman cuando está ocupada.

El `BeginBusyState` `EndBusyState` y llama incrementan y disminuyen, respectivamente, un contador que determina si la aplicación está ocupada. Por ejemplo, dos `BeginBusyState` llamadas `EndBusyState` y una llamada para seguir resultando en un estado ocupado. Para cancelar un estado ocupado `EndBusyState` es necesario llamar `BeginBusyState` al mismo número de veces que se ha llamado.

De forma predeterminada, el marco de trabajo entra en el estado de disponibilidad durante el procesamiento inactivo, que se realiza mediante [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Mientras la aplicación controla ON_UPDATE_COMMAND_UI notificaciones, las llamadas entrantes se controlan una vez completado el procesamiento inactivo.

## <a name="colemessagefilteronmessagepending"></a><a name="onmessagepending"></a>COleMessageFilter::OnMessagePending

Llamado por el marco de trabajo para procesar mensajes mientras una llamada OLE está en curso.

```
virtual BOOL OnMessagePending(const MSG* pMsg);
```

### <a name="parameters"></a>Parámetros

*Pmsg*<br/>
Puntero al mensaje pendiente.

### <a name="return-value"></a>Valor devuelto

Distinto de cero en caso de éxito; en caso contrario, es 0.

### <a name="remarks"></a>Observaciones

Cuando una aplicación que realiza la llamada está `OnMessagePending` esperando a que se complete una llamada, el marco de trabajo llama con un puntero al mensaje pendiente. De forma predeterminada, el marco de trabajo distribuye WM_PAINT mensajes, por lo que pueden producirse actualizaciones de ventana durante una llamada que tarda mucho tiempo.

Debe registrar el filtro de mensajes mediante una llamada a [Register](#register) antes de que pueda activarse.

## <a name="colemessagefilterregister"></a><a name="register"></a>COleMessageFilter::Register

Registra el filtro de mensajes con los archivos DLL del sistema OLE.

```
BOOL Register();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero en caso de éxito; en caso contrario, es 0.

### <a name="remarks"></a>Observaciones

Un filtro de mensajes no tiene ningún efecto a menos que esté registrado con los archivos DLL del sistema. Normalmente, el código de inicialización de la aplicación registra el filtro de mensajes de la aplicación. Cualquier otro filtro de mensajes registrado por la aplicación debe revocarse antes de que el programa finalice mediante una llamada a [Revoke](#revoke).

El filtro de mensajes predeterminado del marco de trabajo se registra automáticamente durante la inicialización y se revoca al finalizar.

## <a name="colemessagefilterrevoke"></a><a name="revoke"></a>COleMessageFilter::Revoke

Revoca un registro anterior realizado por una llamada a [Register](#register).

```
void Revoke();
```

### <a name="remarks"></a>Observaciones

Se debe revocar un filtro de mensajes antes de que finalice el programa.

El filtro de mensajes predeterminado, que el marco de trabajo crea y registra automáticamente.

## <a name="colemessagefiltersetbusyreply"></a><a name="setbusyreply"></a>COleMessageFilter::SetBusyReply

Esta función establece la "respuesta ocupada" de la aplicación.

```
void SetBusyReply(SERVERCALL nBusyReply);
```

### <a name="parameters"></a>Parámetros

*nBusyReply*<br/>
Un valor `SERVERCALL` de la enumeración, que se define en COMPOBJ. H. Puede tener cualquiera de los siguientes valores:

- SERVERCALL_ISHANDLED La aplicación puede aceptar llamadas, pero puede producir un error en el procesamiento de una llamada determinada.

- SERVERCALL_REJECTED La aplicación probablemente nunca será capaz de procesar una llamada.

- SERVERCALL_RETRYLATER La aplicación se encuentra temporalmente en un estado en el que no puede procesar una llamada.

### <a name="remarks"></a>Observaciones

Las funciones [BeginBusyState](#beginbusystate) y [EndBusyState](#endbusystate) controlan el estado ocupado de la aplicación.

Cuando una aplicación se ha ocupado `BeginBusyState`con una llamada a , responde a las llamadas de `SetBusyReply`los archivos DLL del sistema OLE con un valor determinado por la última configuración de . La aplicación que realiza la llamada utiliza esta respuesta ocupada para determinar qué acción realizar.

De forma predeterminada, la respuesta ocupada es SERVERCALL_RETRYLATER. Esta respuesta hace que la aplicación que realiza la llamada vuelva a intentar la llamada lo antes posible.

## <a name="colemessagefiltersetmessagependingdelay"></a><a name="setmessagependingdelay"></a>COleMessageFilter::SetMessagePendingDelay

Determina cuánto tiempo espera la aplicación que realiza la llamada una respuesta de la aplicación llamada antes de realizar más acciones.

```
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```

### <a name="parameters"></a>Parámetros

*nTimeout*<br/>
Número de milisegundos para el retraso pendiente de mensaje.

### <a name="remarks"></a>Observaciones

Esta función funciona en conjunto con [SetRetryReply](#setretryreply).

## <a name="colemessagefiltersetretryreply"></a><a name="setretryreply"></a>COleMessageFilter::SetRetryReply

Determina la acción de la aplicación que realiza la llamada cuando recibe una respuesta ocupada de una aplicación llamada.

```
void SetRetryReply(DWORD nRetryReply = 0);
```

### <a name="parameters"></a>Parámetros

*nRetryReply*<br/>
Número de milisegundos entre reintentos.

### <a name="remarks"></a>Observaciones

Cuando una aplicación llamada indica que está ocupada, la aplicación que realiza la llamada puede decidir esperar hasta que el servidor ya no esté ocupado, volver a intentarlo de inmediato o reintentar después de un intervalo especificado. También puede decidir cancelar la llamada por completo.

La respuesta del autor de la `SetRetryReply` llamada se controla mediante las funciones y [SetMessagePendingDelay](#setmessagependingdelay). `SetRetryReply`determina cuánto tiempo debe esperar la aplicación que realiza la llamada entre reintentos para una llamada determinada. `SetMessagePendingDelay`determina cuánto tiempo espera la aplicación que realiza la llamada una respuesta del servidor antes de realizar más acciones.

Por lo general, los valores predeterminados son aceptables y no es necesario cambiarlos. El marco de trabajo reintenta la llamada cada *nRetryReply* milisegundos hasta que se realiza la llamada o el retraso pendiente de mensaje ha expirado. Un valor de 0 para *nRetryReply* especifica un reintento inmediato y - 1 especifica la cancelación de la llamada.

Cuando el retraso pendiente de mensaje ha expirado, se muestra el "cuadro de diálogo ocupado" OLE (consulte [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)) para que el usuario pueda optar por cancelar o volver a intentar la llamada. Llame a [EnableBusyDialog](#enablebusydialog) para habilitar o deshabilitar este cuadro de diálogo.

Cuando un mensaje de teclado o mouse está pendiente durante una llamada y se ha agotado el tiempo de espera de la llamada (se ha superado el retraso pendiente de mensaje), se muestra el cuadro de diálogo "no responde". Llame a [EnableNotRespondingDialog](#enablenotrespondingdialog) para habilitar o deshabilitar este cuadro de diálogo. Por lo general, este estado de cosas indica que algo ha salido mal y el usuario se está impacientando.

Cuando los cuadros de diálogo están deshabilitados, la "respuesta de reintento" actual siempre se utiliza para las llamadas a aplicaciones ocupadas.

## <a name="see-also"></a>Consulte también

[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)
