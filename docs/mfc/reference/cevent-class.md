---
title: CEvent (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CEvent
- AFXMT/CEvent
- AFXMT/CEvent::CEvent
- AFXMT/CEvent::PulseEvent
- AFXMT/CEvent::ResetEvent
- AFXMT/CEvent::SetEvent
- AFXMT/CEvent::Unlock
dev_langs:
- C++
helpviewer_keywords:
- synchronization objects, event
- synchronization classes, CEvent class
- CEvent class
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
caps.latest.revision: 27
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 9edadeec87cf04ae6166c173c65463d1509eb1d8
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cevent-class"></a>CEvent (clase)
Representa un evento, que es un objeto de sincronización que permite que un subproceso notifique a otro que se ha producido un evento.  
  
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
|[CEvent::PulseEvent](#pulseevent)|Establece señala el evento disponible (), libera los subprocesos en espera y establece el evento como no disponible (no señalado).|  
|[CEvent::ResetEvent](#resetevent)|Establece el evento como no disponible (no señalado).|  
|[CEvent::SetEvent](#setevent)|Establece el evento en disponibles (señalado) y libera todos los subprocesos en espera.|  
|[CEvent::Unlock](#unlock)|Libera el objeto de evento.|  
  
## <a name="remarks"></a>Comentarios  
 Los eventos son útiles cuando un subproceso debe saber cuándo se debe realizar su tarea. Por ejemplo, un subproceso que copia datos en un archivo de datos se notificará cuando hay nuevos datos disponibles. Mediante el uso de un `CEvent` objeto para notificar el subproceso de copia cuando hay nuevos datos disponibles, el subproceso puede realizar su tarea tan pronto como sea posible.  
  
 `CEvent`los objetos tienen dos tipos: manual y automático.  
  
 Automáticos `CEvent` objeto vuelve automáticamente a un estado (no disponible) no señalado después de libera al menos un subproceso. De forma predeterminada, un `CEvent` objeto es automático a menos que pase `TRUE` para el `bManualReset` parámetro durante la construcción.  
  
 Un manual `CEvent` objeto permanece en el estado establecido [SetEvent](#setevent) o [ResetEvent](#resetevent) hasta que se llama a otra función. Para crear un manual `CEvent` de objetos, pasar `TRUE` para el `bManualReset` parámetro durante la construcción.  
  
 Para usar un `CEvent` objeto, construir la `CEvent` objeto cuando sea necesario. Especifique el nombre del evento que desea esperar y especificar que la aplicación debe inicialmente el propietario. A continuación, puede tener acceso el evento cuando se devuelve el constructor. Llame a [SetEvent](#setevent) señal (hacer disponible) el objeto de evento y luego se llama [Unlock](#unlock) cuando haya terminado obtener acceso al recurso controlado.  
  
 Un método alternativo para el uso de `CEvent` objetos consiste en Agregar una variable de tipo `CEvent` como un miembro de datos a la clase que desea controlar. Durante la construcción del objeto controlado, llame al constructor de la `CEvent` miembro de datos y especificar si el evento se señala inicialmente y specifythe tipo de objeto de evento que desea, el nombre del evento (si se utilizará en los límites de proceso), y atributos de seguridad deseado.  
  
 Para obtener acceso a un recurso controlado por un `CEvent` de esta manera, primero cree una variable de cualquier tipo de [CSingleLock](../../mfc/reference/csinglelock-class.md) o tipo [CMultiLock](../../mfc/reference/cmultilock-class.md) en el método de acceso del recurso. A continuación, llame a la `Lock` método del objeto de bloqueo (por ejemplo, [CMultiLock::Lock](../../mfc/reference/cmultilock-class.md#lock)). En este punto, el subproceso se bien tener acceso a los recursos, espere a que el recurso se libera y obtener acceso o espere a que se libere el recurso de tiempo de espera y no se pudo obtener acceso al recurso. En cualquier caso, se tiene acceso a los recursos de una manera segura para subprocesos. Para liberar los recursos, llame a `SetEvent` el objeto de evento de señal y, a continuación, usar el `Unlock` método del objeto de bloqueo (por ejemplo, [CMultiLock::Unlock](../../mfc/reference/cmultilock-class.md#unlock)), o dejar que el objeto de bloqueo quedan fuera de ámbito.  
  
 Para obtener más información acerca de cómo usar `CEvent` los objetos, vea [subprocesamiento múltiple: cómo usar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_Utilities nº&45;](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]  
  
 [!code-cpp[NVC_MFC_Utilities nº&46;](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CEvent`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmt.h  
  
##  <a name="cevent"></a>CEvent::CEvent  
 Construye una con o sin nombre `CEvent` objeto.  
  
```  
CEvent(
    BOOL bInitiallyOwn = FALSE,  
    BOOL bManualReset = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `bInitiallyOwn`  
 Si **TRUE**, el subproceso de la **CMultilock** o `CSingleLock` objeto está habilitado. De lo contrario, deben esperar todos los subprocesos que deseen tener acceso al recurso.  
  
 *bManualReset*  
 Si **TRUE**, especifica que el objeto de evento es un evento manual, de lo contrario, el objeto de evento es un evento automático.  
  
 `lpszName`  
 Nombre del objeto `CEvent`. Se debe proporcionar si se utilizará el objeto a través de límites de proceso. Si el nombre coincide con un evento existente, el constructor genera una nueva `CEvent` objeto que hace referencia a los eventos de ese nombre. Si el nombre coincide con un objeto de sincronización existente que no es un evento, se producirá un error en la construcción. Si **NULL**, el nombre será null.  
  
 `lpsaAttribute`  
 Atributos de seguridad del objeto de evento. Para obtener una descripción completa de esta estructura, vea [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Para obtener acceso o liberar una `CEvent` , cree un [CMultiLock](../../mfc/reference/cmultilock-class.md) o [CSingleLock](../../mfc/reference/csinglelock-class.md) objeto y llamar a su [bloqueo](../../mfc/reference/csinglelock-class.md#lock) y [Unlock](../../mfc/reference/csinglelock-class.md#unlock) funciones miembro.  
  
 Para cambiar el estado de un `CEvent` objeto marcado (subprocesos no tienen que esperar), llame a [SetEvent](#setevent) o [PulseEvent](#pulseevent). Para establecer el estado de un `CEvent` objeto en no señalado (subprocesos deben esperar), llame a [ResetEvent](#resetevent).  
  
> [!IMPORTANT]
>  Después de crear el `CEvent` objeto, utilice [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) para asegurarse de que la exclusión mutua no existe. Si la exclusión mutua existía inesperadamente, puede indicar un proceso invasor es uso inapropiado y puede prevé utilizar la exclusión mutua de forma malintencionada. En este caso, el procedimiento recomendado de preocupados por la seguridad es cerrar el identificador y continuar como si se produjo un error en la creación del objeto.  
  
##  <a name="pulseevent"></a>CEvent::PulseEvent  
 Establece el estado del evento en señalado (disponible), libera todos los subprocesos en espera y que no señalado (no disponible) se restablece automáticamente.  
  
```  
BOOL PulseEvent();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si el evento es manual, se liberan todos los subprocesos en espera, el evento se establece en no señalado, y `PulseEvent` devuelve. Si el evento es automático, se libera un único subproceso, el evento está establecido en no señalado, y `PulseEvent` devuelve.  
  
 Si no hay subprocesos en espera o subprocesos no pueden liberarse inmediatamente, `PulseEvent` establece el estado del evento en no señalado y devuelve.  
  
 `PulseEvent`utiliza Win32 subyacente `PulseEvent` función, que se puede quitar temporalmente desde el estado de espera por una llamada a procedimiento asincrónico de modo kernel. Por lo tanto, `PulseEvent` es confiable y no debe utilizarse en aplicaciones nuevas. Para obtener más información, consulte el [función PulseEvent](http://msdn.microsoft.com/library/windows/desktop/ms684914).  
  
##  <a name="resetevent"></a>CEvent::ResetEvent  
 Establece el estado del evento en no señalado hasta que establezca explícitamente como señalado por el [SetEvent](#setevent) función miembro.  
  
```  
BOOL ResetEvent();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esto hace que todos los subprocesos que deseen tener acceso a este evento para esperar.  
  
 Esta función miembro no se utiliza por eventos automáticos.  
  
##  <a name="setevent"></a>CEvent::SetEvent  
 Establece el estado del evento en señalado, liberar los subprocesos en espera.  
  
```  
BOOL SetEvent();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realizó correctamente, de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si el evento es manual, el evento permanecerá señalado hasta [ResetEvent](#resetevent) se llama. Más de un subproceso puede liberarse en este caso. Si el evento es automático, el evento permanecerá señalado hasta que se libera un único subproceso. El sistema, a continuación, Establece el estado del evento en no señalado. Si no hay ningún subproceso en espera, el estado permanece señalado hasta que se libere un subproceso.  
  
##  <a name="unlock"></a>CEvent::Unlock  
 Libera el objeto de evento.  
  
```  
BOOL Unlock();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el subproceso propietario del objeto de evento y el evento es un evento automático; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Subprocesos que poseen actualmente un evento automático para liberar una vez terminados, si es su objeto de bloqueo que se reutilice llama a esta función miembro. Si el objeto de bloqueo no se puede volver a utilizar, esta función se llamará al destructor del objeto de bloqueo.  
  
## <a name="see-also"></a>Vea también  
 [CSyncObject (clase)](../../mfc/reference/csyncobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)


