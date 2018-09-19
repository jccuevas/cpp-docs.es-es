---
title: COleMessageFilter (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a35f73405340b1ad66b004efcab49ac4c569c560
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852138"
---
# <a name="colemessagefilter-class"></a>COleMessageFilter (clase)
Administra la simultaneidad requerida por la interacción de aplicaciones OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleMessageFilter : public CCmdTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleMessageFilter::COleMessageFilter](#colemessagefilter)|Construye un objeto `COleMessageFilter`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleMessageFilter::BeginBusyState](#beginbusystate)|Pone la aplicación en el estado de ocupado.|  
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|Habilita y deshabilita el cuadro de diálogo que aparece cuando una aplicación de llamada está ocupada.|  
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|Habilita y deshabilita el cuadro de diálogo que aparece cuando una aplicación de llamada no responde.|  
|[COleMessageFilter::EndBusyState](#endbusystate)|Finaliza el estado de disponibilidad de la aplicación.|  
|[COleMessageFilter::OnMessagePending](#onmessagepending)|Lo llama el marco de trabajo para procesar los mensajes mientras una llamada OLE está en curso.|  
|[COleMessageFilter::Register](#register)|Registra el filtro de mensajes con la DLL del sistema OLE.|  
|[COleMessageFilter::Revoke](#revoke)|Revoca el registro del filtro de mensajes con la DLL del sistema OLE.|  
|[COleMessageFilter::SetBusyReply](#setbusyreply)|Determina la respuesta de la disponibilidad de la aplicación a una llamada OLE.|  
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|Determina cuánto tiempo espera la aplicación para una respuesta a una llamada OLE.|  
|[COleMessageFilter::SetRetryReply](#setretryreply)|Determina la respuesta de la aplicación que realiza la llamada a una aplicación ocupada.|  
  
## <a name="remarks"></a>Comentarios  
 La `COleMessageFilter` clase es útil en aplicaciones de servidor y un contenedor de edición visual, así como aplicaciones de automatización OLE. Para las aplicaciones de servidor que se llama a esta clase puede utilizarse para hacer que la aplicación "ocupado" para que las llamadas entrantes desde otras aplicaciones de contenedor se cancelan o se vuelve a intentar más tarde. Esta clase también puede utilizarse para determinar la acción a emprender por una aplicación que realiza la llamada cuando la aplicación llamada está ocupada.  
  
 Uso común es para que una aplicación de servidor llamar a [BeginBusyState](#beginbusystate) y [EndBusyState](#endbusystate) que sería peligroso para un documento u otro objeto accesible de OLE que se va a destruir. Estas llamadas se realizan en [CWinApp:: OnIdle](../../mfc/reference/cwinapp-class.md#onidle) durante las actualizaciones de la interfaz de usuario.  
  
 De forma predeterminada, un `COleMessageFilter` se asigna el objeto cuando se inicializa la aplicación. Se puede recuperar con [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).  
  
 Se trata de una clase avanzada; rara vez deba trabajar directamente con él.  
  
 Para obtener más información, vea el artículo [servidores: implementar un servidor](../../mfc/servers-implementing-a-server.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleMessageFilter`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="beginbusystate"></a>  COleMessageFilter::BeginBusyState  
 Llame a esta función para empezar a un estado de ocupado.  
  
```  
virtual void BeginBusyState();
```  
  
### <a name="remarks"></a>Comentarios  
 Funciona junto con [EndBusyState](#endbusystate) para controlar el estado de disponibilidad de la aplicación. La función [SetBusyReply](#setbusyreply) determina la respuesta de la aplicación a llamar a las aplicaciones cuando está ocupado.  
  
 El `BeginBusyState` y `EndBusyState` llamadas incrementar y disminuir, respectivamente, un contador que determina si la aplicación está ocupada. Por ejemplo, dos llamadas a `BeginBusyState` y una llamada a `EndBusyState` todavía el resultado en un estado de ocupado. Para cancelar un estado de ocupado es necesario llamar a `EndBusyState` el mismo número de veces `BeginBusyState` se ha llamado.  
  
 De forma predeterminada, el marco de trabajo entra en el estado ocupado durante el procesamiento en inactividad, que se realiza mediante [CWinApp:: OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Mientras la aplicación está controlando las notificaciones ON_COMMANDUPDATEUI, las llamadas entrantes se tratan más adelante, una vez completado el procesamiento en inactividad.  
  
##  <a name="colemessagefilter"></a>  COleMessageFilter::COleMessageFilter  
 Crea un objeto `COleMessageFilter`.  
  
```  
COleMessageFilter();
```  
  
##  <a name="enablebusydialog"></a>  COleMessageFilter::EnableBusyDialog  
 Habilita y deshabilita el cuadro de diálogo ocupado que se muestra cuando expira el retraso de espera de mensaje (consulte [SetRetryReply](#setretryreply)) durante una llamada OLE.  
  
```  
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *bEnableBusy*  
 Especifica si el cuadro de diálogo "ocupado" está habilitado o deshabilitado.  
  
##  <a name="enablenotrespondingdialog"></a>  COleMessageFilter::EnableNotRespondingDialog  
 Habilita y deshabilita el cuadro de diálogo "no responde", que se muestra si hay pendiente un mensaje de teclado o mouse durante una OLE ha agotado llamada y la llamada.  
  
```  
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *bEnableNotResponding*  
 Especifica si el cuadro de diálogo "no responde" está habilitado o deshabilitado.  
  
##  <a name="endbusystate"></a>  COleMessageFilter::EndBusyState  
 Llame a esta función para finalizar un estado de ocupado.  
  
```  
virtual void EndBusyState();
```  
  
### <a name="remarks"></a>Comentarios  
 Funciona junto con [BeginBusyState](#beginbusystate) para controlar el estado de disponibilidad de la aplicación. La función [SetBusyReply](#setbusyreply) determina la respuesta de la aplicación a llamar a las aplicaciones cuando está ocupado.  
  
 El `BeginBusyState` y `EndBusyState` llamadas incrementar y disminuir, respectivamente, un contador que determina si la aplicación está ocupada. Por ejemplo, dos llamadas a `BeginBusyState` y una llamada a `EndBusyState` todavía el resultado en un estado de ocupado. Para cancelar un estado de ocupado es necesario llamar a `EndBusyState` el mismo número de veces `BeginBusyState` se ha llamado.  
  
 De forma predeterminada, el marco de trabajo entra en el estado ocupado durante el procesamiento en inactividad, que se realiza mediante [CWinApp:: OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Mientras la aplicación está controlando las notificaciones ON_UPDATE_COMMAND_UI, las llamadas entrantes se administran una vez completado el procesamiento en inactividad.  
  
##  <a name="onmessagepending"></a>  COleMessageFilter::OnMessagePending  
 Lo llama el marco de trabajo para procesar los mensajes mientras una llamada OLE está en curso.  
  
```  
virtual BOOL OnMessagePending(const MSG* pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 *pMsg*  
 Puntero al mensaje pendiente.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero en caso de éxito; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Cuando una aplicación que realiza la llamada está esperando una llamada se complete, el marco llama a `OnMessagePending` con un puntero al mensaje pendiente. De forma predeterminada, el marco de trabajo envía mensajes WM_PAINT, para que puedan realizarse las actualizaciones de la ventana durante una llamada a la que está tardando mucho tiempo.  
  
 Debe registrar el filtro de mensajes por medio de una llamada a [registrar](#register) antes de que puede activarse.  
  
##  <a name="register"></a>  COleMessageFilter::Register  
 Registra el filtro de mensajes con la DLL del sistema OLE.  
  
```  
BOOL Register();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero en caso de éxito; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Un filtro de mensajes no tiene ningún efecto a menos que se registra con el sistema de archivos DLL. Normalmente, código de inicialización de la aplicación registra el filtro de mensajes de la aplicación. Antes de que termine el programa mediante una llamada a cualquier otro filtro de mensaje registrado por la aplicación que se debe revocar [revocar](#revoke).  
  
 Filtro de mensajes predeterminado de .NET framework registrado durante la inicialización y revocado al finalizar automáticamente.  
  
##  <a name="revoke"></a>  COleMessageFilter::Revoke  
 Revoca un registro previo realizado una llamada a [registrar](#register).  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>Comentarios  
 Un filtro de mensajes se debe revocar antes de que el programa finaliza.  
  
 El filtro de mensajes de forma predeterminada, que se crea y registra automáticamente el marco de trabajo, automáticamente se ha revocado.  
  
##  <a name="setbusyreply"></a>  COleMessageFilter::SetBusyReply  
 Esta función establece "ocupado responder." la aplicación  
  
```  
void SetBusyReply(SERVERCALL nBusyReply);
```  
  
### <a name="parameters"></a>Parámetros  
 *nBusyReply*  
 Un valor de la `SERVERCALL` enumeración, que se define en COMPOBJ. H. Puede tener uno de los siguientes valores:  
  
- SERVERCALL_ISHANDLED la aplicación puede aceptar las llamadas, pero puede producir un error en el procesamiento de una llamada determinada.  
  
- Probablemente SERVERCALL_REJECTED la aplicación nunca será capaz de procesar una llamada.  
  
- La aplicación SERVERCALL_RETRYLATER está temporalmente en un estado en el que no puede procesar una llamada.  
  
### <a name="remarks"></a>Comentarios  
 El [BeginBusyState](#beginbusystate) y [EndBusyState](#endbusystate) control de las funciones de estado de disponibilidad de la aplicación.  
  
 Cuando una aplicación se ha realizado ocupada con una llamada a `BeginBusyState`, responde a las llamadas desde la DLL del sistema OLE con un valor determinado por el último valor de `SetBusyReply`. La aplicación que realiza la llamada usa esta respuesta ocupada para determinar qué acción realizar.  
  
 De forma predeterminada, la respuesta a la disponibilidad es SERVERCALL_RETRYLATER. Esta respuesta hace que la aplicación que realiza la llamada a reintentar la llamada tan pronto como sea posible.  
  
##  <a name="setmessagependingdelay"></a>  COleMessageFilter::SetMessagePendingDelay  
 Determina cuánto tiempo la aplicación que realiza la llamada espera una respuesta de la aplicación llamada antes de realizar otra acción.  
  
```  
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```  
  
### <a name="parameters"></a>Parámetros  
 *nTimeout*  
 Número de milisegundos de retardo mensajes pendientes.  
  
### <a name="remarks"></a>Comentarios  
 Esta función funciona junto con [SetRetryReply](#setretryreply).  
  
##  <a name="setretryreply"></a>  COleMessageFilter::SetRetryReply  
 Determina la acción de la aplicación que realiza la llamada cuando recibe una respuesta de ocupado desde una aplicación de llamada.  
  
```  
void SetRetryReply(DWORD nRetryReply = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 *nRetryReply*  
 Número de milisegundos entre los reintentos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando una aplicación llamada indica que está ocupado, la aplicación que realiza la llamada puede optar por esperar hasta que el servidor ya no está ocupado, reintentar inmediatamente o volver a intentar después de un intervalo especificado. También puede decidir cancelar la llamada por completo.  
  
 Respuesta del llamador se controla mediante las funciones `SetRetryReply` y [SetMessagePendingDelay](#setmessagependingdelay). `SetRetryReply` determina cuánto tiempo la aplicación que realiza la llamada debe esperar entre reintentos de una llamada determinada. `SetMessagePendingDelay` determina cuánto tiempo la aplicación que realiza la llamada espera una respuesta del servidor antes de realizar una acción posterior.  
  
 Normalmente, los valores predeterminados son aceptables y no deben cambiarse. El marco de trabajo vuelve a intentar la llamada cada *nRetryReply* milisegundos hasta que la llamada pasa por o ha expirado el retraso de mensajes pendientes. Un valor de 0 para *nRetryReply* especifica un reintento inmediato y - 1 especifica la cancelación de la llamada.  
  
 Cuando ha expirado el retraso de espera de mensaje, la OLE "cuadro de diálogo ocupado" (consulte [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)) se muestra para que el usuario puede optar por cancelar o vuelva a intentar la llamada. Llame a [EnableBusyDialog](#enablebusydialog) para habilitar o deshabilitar este cuadro de diálogo.  
  
 Cuando está pendiente un mensaje del teclado o mouse durante una llamada y la llamada ha agotado (supera el retraso de mensaje pendiente), se muestra el cuadro de diálogo "no responde". Llame a [EnableNotRespondingDialog](#enablenotrespondingdialog) para habilitar o deshabilitar este cuadro de diálogo. Normalmente, este estado de la situación indica que ha producido un error y el usuario recibe impaciente.  
  
 Cuando se deshabilitan los cuadros de diálogo, el actual "vuelva a intentar responder" se utiliza siempre para las llamadas a las aplicaciones ocupadas.  
  
## <a name="see-also"></a>Vea también  
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)
