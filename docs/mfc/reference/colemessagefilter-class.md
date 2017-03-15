---
title: Clase COleMessageFilter | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleMessageFilter
dev_langs:
- C++
helpviewer_keywords:
- COleMessageFilter class
- OLE [C++], managing concurrency
- message filters [C++]
- OLE applications [C++], managing interactions
- OLE messages
- applications [OLE], managing interactions
- messages [C++], OLE
ms.assetid: b1fd1639-fac4-4fd0-bf17-15172deba13c
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: d91ed300bb6cade5d804fe4a74dfe6cc2e4384fe
ms.lasthandoff: 02/24/2017

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
|[COleMessageFilter::BeginBusyState](#beginbusystate)|Ponga la aplicación en un estado ocupado.|  
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|Habilita y deshabilita el cuadro de diálogo que aparece cuando una aplicación de llamada está ocupada.|  
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|Habilita y deshabilita el cuadro de diálogo que aparece cuando una aplicación de llamada no responde.|  
|[COleMessageFilter::EndBusyState](#endbusystate)|Finaliza el estado de disponibilidad de la aplicación.|  
|[COleMessageFilter::OnMessagePending](#onmessagepending)|Lo llama el marco de trabajo para procesar los mensajes mientras una llamada OLE está en curso.|  
|[COleMessageFilter::Register](#register)|Registra el filtro de mensajes con las DLL del sistema OLE.|  
|[COleMessageFilter::Revoke](#revoke)|Revoca el registro del filtro de mensajes con las DLL del sistema OLE.|  
|[COleMessageFilter::SetBusyReply](#setbusyreply)|Determina la respuesta de la disponibilidad de la aplicación a una llamada de OLE.|  
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|Determina cuánto tiempo la aplicación espera una respuesta a una llamada OLE.|  
|[COleMessageFilter::SetRetryReply](#setretryreply)|Determina la respuesta de la aplicación que realiza la llamada a una aplicación ocupada.|  
  
## <a name="remarks"></a>Comentarios  
 La `COleMessageFilter` clase es útil en aplicaciones de servidor y contenedor de edición visual, así como aplicaciones de automatización OLE. Para aplicaciones de servidor que se llama, esta clase puede usarse para hacer que la aplicación "ocupado" para que las llamadas entrantes de otras aplicaciones de contenedor se cancelan o se vuelve a intentar más tarde. Esta clase también puede utilizarse para determinar la acción a emprender por una aplicación de llamada cuando la aplicación llamada está ocupada.  
  
 Uso común es para que una aplicación de servidor llamar a [BeginBusyState](#beginbusystate) y [EndBusyState](#endbusystate) que sería peligroso para un documento u otro objeto accesible de OLE se destruya. Estas llamadas se realizan en [CWinApp:: OnIdle](../../mfc/reference/cwinapp-class.md#onidle) durante las actualizaciones de la interfaz de usuario.  
  
 De forma predeterminada, un `COleMessageFilter` objeto se asigna cuando se inicializa la aplicación. Se puede recuperar con [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).  
  
 Esta es una clase avanzada; rara vez necesitará trabajar directamente con ella.  
  
 Para obtener más información, vea el artículo [servidores: implementar un servidor](../../mfc/servers-implementing-a-server.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleMessageFilter`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="a-namebeginbusystatea--colemessagefilterbeginbusystate"></a><a name="beginbusystate"></a>COleMessageFilter::BeginBusyState  
 Llame a esta función para comenzar a un estado de ocupado.  
  
```  
virtual void BeginBusyState();
```  
  
### <a name="remarks"></a>Comentarios  
 Funciona junto con [EndBusyState](#endbusystate) para controlar el estado de disponibilidad de la aplicación. La función [SetBusyReply](#setbusyreply) determina la respuesta de la aplicación para llamar a las aplicaciones cuando está ocupado.  
  
 El `BeginBusyState` y `EndBusyState` llamadas de incremento y decremento, respectivamente, un contador que determina si la aplicación está ocupada. Por ejemplo, dos llamadas a `BeginBusyState` y una llamada a `EndBusyState` resultante en un estado de ocupado. Para cancelar un estado de ocupado es necesario llamar a `EndBusyState` el mismo número de veces que `BeginBusyState` se ha llamado.  
  
 De forma predeterminada, el marco de trabajo entra en el estado ocupado durante el procesamiento en inactividad, que se realiza mediante [CWinApp:: OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Mientras la aplicación está controlando **ON_COMMANDUPDATEUI** notificaciones, las llamadas entrantes se tratan más adelante, una vez completado el procesamiento en inactividad.  
  
##  <a name="a-namecolemessagefiltera--colemessagefiltercolemessagefilter"></a><a name="colemessagefilter"></a>COleMessageFilter::COleMessageFilter  
 Crea un objeto `COleMessageFilter`.  
  
```  
COleMessageFilter();
```  
  
##  <a name="a-nameenablebusydialoga--colemessagefilterenablebusydialog"></a><a name="enablebusydialog"></a>COleMessageFilter::EnableBusyDialog  
 Habilita y deshabilita el cuadro de diálogo ocupado, que se muestra cuando caduca el retraso de espera de mensaje (consulte [SetRetryReply](#setretryreply)) durante una llamada OLE.  
  
```  
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *bEnableBusy*  
 Especifica si el cuadro de diálogo "ocupado" está habilitado o deshabilitado.  
  
##  <a name="a-nameenablenotrespondingdialoga--colemessagefilterenablenotrespondingdialog"></a><a name="enablenotrespondingdialog"></a>COleMessageFilter::EnableNotRespondingDialog  
 Habilita y deshabilita el cuadro de diálogo "no responde", que se muestra si está pendiente un mensaje del teclado o del mouse durante una OLE ha agotado llamada y la llamada.  
  
```  
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *bEnableNotResponding*  
 Especifica si el cuadro de diálogo "no responde" está habilitado o deshabilitado.  
  
##  <a name="a-nameendbusystatea--colemessagefilterendbusystate"></a><a name="endbusystate"></a>COleMessageFilter::EndBusyState  
 Llame a esta función para finalizar un estado de ocupado.  
  
```  
virtual void EndBusyState();
```  
  
### <a name="remarks"></a>Comentarios  
 Funciona junto con [BeginBusyState](#beginbusystate) para controlar el estado de disponibilidad de la aplicación. La función [SetBusyReply](#setbusyreply) determina la respuesta de la aplicación para llamar a las aplicaciones cuando está ocupado.  
  
 El `BeginBusyState` y `EndBusyState` llamadas de incremento y decremento, respectivamente, un contador que determina si la aplicación está ocupada. Por ejemplo, dos llamadas a `BeginBusyState` y una llamada a `EndBusyState` resultante en un estado de ocupado. Para cancelar un estado de ocupado es necesario llamar a `EndBusyState` el mismo número de veces que `BeginBusyState` se ha llamado.  
  
 De forma predeterminada, el marco de trabajo entra en el estado ocupado durante el procesamiento en inactividad, que se realiza mediante [CWinApp:: OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Mientras la aplicación está controlando `ON_UPDATE_COMMAND_UI` notificaciones, las llamadas entrantes se administran después de completar el procesamiento en inactividad.  
  
##  <a name="a-nameonmessagependinga--colemessagefilteronmessagepending"></a><a name="onmessagepending"></a>COleMessageFilter::OnMessagePending  
 Lo llama el marco de trabajo para procesar los mensajes mientras una llamada OLE está en curso.  
  
```  
virtual BOOL OnMessagePending(const MSG* pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 `pMsg`  
 Puntero al mensaje pendiente.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero en caso de éxito; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Cuando una aplicación que realiza la llamada está esperando una llamada a que se complete, el marco llama a `OnMessagePending` con un puntero al mensaje pendiente. De forma predeterminada, el marco de trabajo envía `WM_PAINT` mensajes, para que las actualizaciones de la ventana pueden producirse durante una llamada a la que esté tardando mucho tiempo.  
  
 Debe registrar el filtro de mensajes por medio de una llamada a [registrar](#register) antes de que pueda activarse.  
  
##  <a name="a-nameregistera--colemessagefilterregister"></a><a name="register"></a>COleMessageFilter::Register  
 Registra el filtro de mensajes con las DLL del sistema OLE.  
  
```  
BOOL Register();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero en caso de éxito; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Un filtro de mensajes no tiene ningún efecto a menos que esté registrado con el sistema de archivos DLL. Normalmente, el código de inicialización de la aplicación registra el filtro de mensajes de la aplicación. Antes de que finalice el programa mediante una llamada a cualquier otro filtro de mensaje registrado por la aplicación que se debe revocar [revocar](#revoke).  
  
 Filtro de mensaje predeterminado del marco de trabajo automáticamente se registrado durante la inicialización y revocado en la finalización.  
  
##  <a name="a-namerevokea--colemessagefilterrevoke"></a><a name="revoke"></a>COleMessageFilter::Revoke  
 Revoca un registro anterior realizado una llamada a [registrar](#register).  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>Comentarios  
 Un filtro de mensajes se debe revocar antes de que finalice el programa.  
  
 El filtro de mensajes predeterminado, que se crean y registran automáticamente por el marco de trabajo, automáticamente se ha revocado.  
  
##  <a name="a-namesetbusyreplya--colemessagefiltersetbusyreply"></a><a name="setbusyreply"></a>COleMessageFilter::SetBusyReply  
 Esta función establece "ocupado reply" la aplicación.  
  
```  
void SetBusyReply(SERVERCALL nBusyReply);
```  
  
### <a name="parameters"></a>Parámetros  
 *nBusyReply*  
 Un valor de la `SERVERCALL` enumeración, que se define en el archivo COMPOBJ. H. Puede tener uno de los siguientes valores:  
  
- **SERVERCALL_ISHANDLED** puede aceptar las llamadas de la aplicación, pero puede producir un error en el procesamiento de una determinada llamada.  
  
- **SERVERCALL_REJECTED** la aplicación probablemente nunca será capaz de procesar una llamada.  
  
- **SERVERCALL_RETRYLATER** la aplicación está temporalmente en un estado donde no se puede procesar una llamada.  
  
### <a name="remarks"></a>Comentarios  
 El [BeginBusyState](#beginbusystate) y [EndBusyState](#endbusystate) funciones controlan el estado de disponibilidad de la aplicación.  
  
 Cuando una aplicación se ha realizado ocupada con una llamada a `BeginBusyState`, responde a las llamadas de la DLL del sistema OLE con un valor determinado por el último valor de `SetBusyReply`. La aplicación de llamada usa esta respuesta ocupada para determinar qué acción realizar.  
  
 De forma predeterminada, es la respuesta ocupada **SERVERCALL_RETRYLATER**. Esta respuesta hace que la aplicación que realiza la llamada reintentar la llamada tan pronto como sea posible.  
  
##  <a name="a-namesetmessagependingdelaya--colemessagefiltersetmessagependingdelay"></a><a name="setmessagependingdelay"></a>COleMessageFilter::SetMessagePendingDelay  
 Determina cuánto tiempo la aplicación que realiza la llamada espera una respuesta de la aplicación llamada antes de realizar otra acción.  
  
```  
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```  
  
### <a name="parameters"></a>Parámetros  
 `nTimeout`  
 Número de milisegundos de retardo mensajes pendientes.  
  
### <a name="remarks"></a>Comentarios  
 Esta función funciona junto con [SetRetryReply](#setretryreply).  
  
##  <a name="a-namesetretryreplya--colemessagefiltersetretryreply"></a><a name="setretryreply"></a>COleMessageFilter::SetRetryReply  
 Determina la acción de la aplicación que realiza la llamada cuando recibe una respuesta ocupada desde una aplicación de llamada.  
  
```  
void SetRetryReply(DWORD nRetryReply = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `nRetryReply`  
 Número de milisegundos entre reintentos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando una aplicación llama indica que está ocupado, puede decidir la aplicación de llamada esperar hasta que el servidor ya no está ocupado, para reintentar inmediatamente o volver a intentar después de un intervalo especificado. También puede decidir cancelar la llamada por completo.  
  
 Respuesta del llamador se controla mediante las funciones de `SetRetryReply` y [SetMessagePendingDelay](#setmessagependingdelay). `SetRetryReply`determina cuánto tiempo la aplicación que realiza la llamada debe esperar entre reintentos para una determinada llamada. `SetMessagePendingDelay`determina cuánto tiempo la aplicación que realiza la llamada espera una respuesta del servidor antes de realizar una acción posterior.  
  
 Normalmente, los valores predeterminados son aceptables y no deben cambiarse. El marco de trabajo vuelve la llamada cada `nRetryReply` milisegundos hasta que pasa la llamada o el retraso de espera de mensaje ha caducado. Un valor de 0 para `nRetryReply` especifica un reintento inmediato y – 1 especifica la cancelación de la llamada.  
  
 Cuando ha caducado el retraso de espera de mensaje, la OLE "cuadro de diálogo ocupado" (consulte [clase COleBusyDialog](../../mfc/reference/colebusydialog-class.md)) se muestra para que el usuario puede optar por cancelar o reintentar la llamada. Llame a [EnableBusyDialog](#enablebusydialog) para habilitar o deshabilitar este cuadro de diálogo.  
  
 Cuando un mensaje de teclado o mouse está pendiente durante una llamada y la llamada ha agotado (supera el retraso de espera de mensaje), se muestra el cuadro de diálogo "no responde". Llame a [EnableNotRespondingDialog](#enablenotrespondingdialog) para habilitar o deshabilitar este cuadro de diálogo. Normalmente este estado de la situación indica que se ha producido un error y el usuario recibe impaciente.  
  
 Cuando se deshabilitan los cuadros de diálogo, el actual "reintento de respuesta" se utiliza siempre para las llamadas a aplicaciones ocupadas.  
  
## <a name="see-also"></a>Vea también  
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)

