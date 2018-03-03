---
title: Clase COleDropTarget | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDropTarget
- AFXOLE/COleDropTarget
- AFXOLE/COleDropTarget::COleDropTarget
- AFXOLE/COleDropTarget::OnDragEnter
- AFXOLE/COleDropTarget::OnDragLeave
- AFXOLE/COleDropTarget::OnDragOver
- AFXOLE/COleDropTarget::OnDragScroll
- AFXOLE/COleDropTarget::OnDrop
- AFXOLE/COleDropTarget::OnDropEx
- AFXOLE/COleDropTarget::Register
- AFXOLE/COleDropTarget::Revoke
dev_langs:
- C++
helpviewer_keywords:
- COleDropTarget [MFC], COleDropTarget
- COleDropTarget [MFC], OnDragEnter
- COleDropTarget [MFC], OnDragLeave
- COleDropTarget [MFC], OnDragOver
- COleDropTarget [MFC], OnDragScroll
- COleDropTarget [MFC], OnDrop
- COleDropTarget [MFC], OnDropEx
- COleDropTarget [MFC], Register
- COleDropTarget [MFC], Revoke
ms.assetid: a58c9a48-6a93-4357-b078-4594df258311
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fecdedc84f4fd93cbd9efe5e525c1771c5eb1c7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="coledroptarget-class"></a>Clase COleDropTarget
Proporciona el mecanismo de comunicación entre una ventana y las bibliotecas OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleDropTarget : public CCmdTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDropTarget::COleDropTarget](#coledroptarget)|Construye un objeto `COleDropTarget`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDropTarget::OnDragEnter](#ondragenter)|Se llama cuando el cursor entra por primera vez la ventana.|  
|[COleDropTarget::OnDragLeave](#ondragleave)|Se llama cuando se arrastra el cursor fuera de la ventana.|  
|[COleDropTarget::OnDragOver](#ondragover)|Llama repetidamente cuando se arrastra el cursor sobre la ventana.|  
|[COleDropTarget::OnDragScroll](#ondragscroll)|Se llama para determinar si se arrastra el cursor en la región de desplazamiento de la ventana.|  
|[COleDropTarget::OnDrop](#ondrop)|Se llama cuando se colocan datos en la ventana, el controlador predeterminado.|  
|[COleDropTarget::OnDropEx](#ondropex)|Se llama cuando se colocan datos en la ventana, controlador inicial.|  
|[COleDropTarget::Register](#register)|Registra la ventana como un destino de colocación válido.|  
|[COleDropTarget::Revoke](#revoke)|Hace que la ventana para dejar que se va a un destino de colocación válido.|  
  
## <a name="remarks"></a>Comentarios  
 Creación de un objeto de esta clase permite que una ventana Aceptar los datos a través del mecanismo de arrastrar y colocar OLE.  
  
 Para obtener una ventana para aceptar comandos drop, primero debe crear un objeto de la `COleDropTarget` clase y, a continuación, llame a la [registrar](#register) función con un puntero a lo que se desea `CWnd` objeto como único parámetro.  
  
 Para obtener más información sobre operaciones de arrastrar y colocar utilizando OLE, vea el artículo [arrastrar y colocar (OLE)](../../mfc/drag-and-drop-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropTarget`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="coledroptarget"></a>COleDropTarget::COleDropTarget  
 Construye un objeto de clase `COleDropTarget`.  
  
```  
COleDropTarget();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a [registrar](#register) para asociarlo a este objeto con una ventana.  
  
##  <a name="ondragenter"></a>COleDropTarget::OnDragEnter  
 Lo llama el marco cuando el cursor se arrastra en primer lugar en la ventana.  
  
```  
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Apunta a la ventana que está entrando en el cursor.  
  
 `pDataObject`  
 Señala al objeto de datos que contiene los datos que se pueden quitar.  
  
 `dwKeyState`  
 Contiene el estado de las teclas modificadoras. Se trata de una combinación de varios de los siguientes valores: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_ MBUTTON**, y **MK_RBUTTON**.  
  
 `point`  
 Contiene la ubicación actual del cursor en coordenadas de cliente.  
  
### <a name="return-value"></a>Valor devuelto  
 El efecto que se crearán si se intenta una caída en la ubicación especificada por `point`. Puede ser una o varias de las siguientes acciones:  
  
- `DROPEFFECT_NONE`Una caída no estarían permitida.  
  
- `DROPEFFECT_COPY`Se realizará una operación de copia.  
  
- `DROPEFFECT_MOVE`Se realizará una operación de movimiento.  
  
- `DROPEFFECT_LINK`Se puede establecer un vínculo de los datos perdidos a los datos originales.  
  
- `DROPEFFECT_SCROLL`Una operación de arrastre del desplazamiento está a punto de producirse o se está produciendo en el destino.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función para permitir las operaciones de colocación que se produzca en la ventana. La implementación predeterminada llama [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter), que simplemente devuelve `DROPEFFECT_NONE` de forma predeterminada.  
  
 Para obtener más información, consulte [IDropTarget::DragEnter](http://msdn.microsoft.com/library/windows/desktop/ms680106) en el SDK de Windows.  
  
##  <a name="ondragleave"></a>COleDropTarget::OnDragLeave  
 Lo llama el marco cuando el cursor sale de la ventana mientras una operación de arrastre está en vigor.  
  
```  
virtual void OnDragLeave(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Apunta a la ventana que está abandonando el cursor.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si desea un comportamiento especial cuando la operación de arrastre sale de la ventana especificada. La implementación predeterminada de esta función llama [CView::OnDragLeave](../../mfc/reference/cview-class.md#ondragleave).  
  
 Para obtener más información, consulte [IDropTarget::DragLeave](http://msdn.microsoft.com/library/windows/desktop/ms680110) en el SDK de Windows.  
  
##  <a name="ondragover"></a>COleDropTarget::OnDragOver  
 Llamado por el marco de trabajo cuando se arrastra el cursor sobre la ventana.  
  
```  
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Señala a la ventana que el cursor está sobre.  
  
 `pDataObject`  
 Señala al objeto de datos que contiene los datos que se va a quitar.  
  
 `dwKeyState`  
 Contiene el estado de las teclas modificadoras. Se trata de una combinación de varios de los siguientes valores: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_ MBUTTON**, y **MK_RBUTTON**.  
  
 `point`  
 Contiene la ubicación actual del cursor en coordenadas de cliente.  
  
### <a name="return-value"></a>Valor devuelto  
 El efecto que se crearán si se intenta una caída en la ubicación especificada por `point`. Puede ser una o varias de las siguientes acciones:  
  
- `DROPEFFECT_NONE`Una caída no estarían permitida.  
  
- `DROPEFFECT_COPY`Se realizará una operación de copia.  
  
- `DROPEFFECT_MOVE`Se realizará una operación de movimiento.  
  
- `DROPEFFECT_LINK`Se puede establecer un vínculo de los datos perdidos a los datos originales.  
  
- `DROPEFFECT_SCROLL`Indica que una operación de arrastre del desplazamiento está a punto de producirse o se está produciendo en el destino.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se debe invalidar para permitir operaciones de eliminación que se produzca en la ventana. La implementación predeterminada de esta función llama [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover), que devuelve `DROPEFFECT_NONE` de forma predeterminada. Dado que esta función se llama con frecuencia durante una operación de arrastrar y colocar, se debe optimizar tanto como sea posible.  
  
 Para obtener más información, consulte [DoDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms680129) del SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]  
  
##  <a name="ondragscroll"></a>COleDropTarget::OnDragScroll  
 Lo llama el marco antes de llamar a [OnDragEnter](#ondragenter) o [OnDragOver](#ondragover) para determinar si `point` está en la región desplazable.  
  
```  
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Apunta a la ventana que el cursor está actualmente por encima.  
  
 `dwKeyState`  
 Contiene el estado de las teclas modificadoras. Se trata de una combinación de varios de los siguientes valores: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_ MBUTTON**, y **MK_RBUTTON**.  
  
 `point`  
 Contiene la ubicación del cursor, en píxeles, relativo a la pantalla.  
  
### <a name="return-value"></a>Valor devuelto  
 El efecto que se crearán si se intenta una caída en la ubicación especificada por `point`. Puede ser una o varias de las siguientes acciones:  
  
- `DROPEFFECT_NONE`Una caída no estarían permitida.  
  
- `DROPEFFECT_COPY`Se realizará una operación de copia.  
  
- `DROPEFFECT_MOVE`Se realizará una operación de movimiento.  
  
- `DROPEFFECT_LINK`Se puede establecer un vínculo de los datos perdidos a los datos originales.  
  
- `DROPEFFECT_SCROLL`Indica que una operación de arrastre del desplazamiento está a punto de producirse o se está produciendo en el destino.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función cuando desea proporcionar un comportamiento especial para este evento. La implementación predeterminada de esta función llama [CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll), que devuelve `DROPEFFECT_NONE` y se desplaza la ventana cuando se arrastra el cursor en la región de desplazamiento predeterminado dentro del borde de la ventana.  
  
##  <a name="ondrop"></a>COleDropTarget::OnDrop  
 Lo llama el marco cuando tiene lugar una operación de colocar.  
  
```  
virtual BOOL OnDrop(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Apunta a la ventana que el cursor está actualmente por encima.  
  
 `pDataObject`  
 Señala al objeto de datos que contiene los datos que se va a quitar.  
  
 `dropEffect`  
 El efecto que el usuario ha elegido para la operación de colocar. Puede ser una o varias de las siguientes acciones:  
  
- `DROPEFFECT_COPY`Se realizará una operación de copia.  
  
- `DROPEFFECT_MOVE`Se realizará una operación de movimiento.  
  
- `DROPEFFECT_LINK`Se puede establecer un vínculo de los datos perdidos a los datos originales.  
  
 `point`  
 Contiene la ubicación del cursor, en píxeles, relativo a la pantalla.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la eliminación se realiza correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 El primer framework llama [OnDropEx](#ondropex). Si el `OnDropEx` función no controla la colocación, el marco de trabajo, a continuación, llama a esta función miembro, `OnDrop`. Normalmente, la aplicación reemplaza [OnDropEx](../../mfc/reference/cview-class.md#ondropex) en la clase de vista para administrar la derecha del botón del mouse, arrastrar y colocar. Normalmente, la clase de vista [OnDrop](../../mfc/reference/cview-class.md#ondrop) se utiliza para controlar simples de arrastrar y colocar.  
  
 La implementación predeterminada de `COleDropTarget::OnDrop` llamadas [CView::OnDrop](../../mfc/reference/cview-class.md#ondrop), que simplemente devuelve **FALSE** de forma predeterminada.  
  
 Para obtener más información, consulte [IDropTarget:: DROP](http://msdn.microsoft.com/library/windows/desktop/ms687242) del SDK de Windows.  
  
##  <a name="ondropex"></a>COleDropTarget::OnDropEx  
 Lo llama el marco cuando tiene lugar una operación de colocar.  
  
```  
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropDefault,  
    DROPEFFECT dropList,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Apunta a la ventana que el cursor está actualmente por encima.  
  
 `pDataObject`  
 Señala al objeto de datos que contiene los datos que se va a quitar.  
  
 `dropDefault`  
 El efecto que el usuario ha elegido para la operación de colocar de forma predeterminada en función del estado de la clave actual. Puede ser `DROPEFFECT_NONE`. Efectos de colocar se describen en la sección Comentarios.  
  
 `dropList`  
 Una lista de los efectos de colocación que admite el origen de colocación. Valores de efecto de colocar se pueden combinar mediante una operación OR bit a bit ( **&#124;**) operación. Efectos de colocar se describen en la sección Comentarios.  
  
 `point`  
 Contiene la ubicación del cursor, en píxeles, relativo a la pantalla.  
  
### <a name="return-value"></a>Valor devuelto  
 El efecto de colocación que dan como resultado del intento de colocar en la ubicación especificada por `point`. Efectos de colocar se describen en la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama primero a esta función. Si no se controla la acción de quitar, a continuación, llama el marco de trabajo [OnDrop](#ondrop). Por lo general, deberá reemplazar [OnDropEx](../../mfc/reference/cview-class.md#ondropex) en la clase de vista para admitir la derecha del botón del mouse, arrastrar y colocar. Normalmente, la clase de vista [OnDrop](../../mfc/reference/cview-class.md#ondrop) se utiliza para controlar el caso de soporte técnico para simples de arrastrar y colocar.  
  
 La implementación predeterminada de `COleDropTarget::OnDropEx` llamadas [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex). De forma predeterminada, [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex) simplemente devuelve un valor ficticio para indicar el [OnDrop](#ondrop) función miembro debe llamarse.  
  
 La acción asociada con una operación de colocar describen los efectos de colocación. Vea la siguiente lista de efectos de colocar:  
  
- `DROPEFFECT_NONE`Una caída no estarían permitida.  
  
- `DROPEFFECT_COPY`Se realizará una operación de copia.  
  
- `DROPEFFECT_MOVE`Se realizará una operación de movimiento.  
  
- `DROPEFFECT_LINK`Se puede establecer un vínculo de los datos perdidos a los datos originales.  
  
- `DROPEFFECT_SCROLL`Indica que una operación de arrastre del desplazamiento está a punto de producirse o se está produciendo en el destino.  
  
 Para obtener más información, consulte [IDropTarget:: DROP](http://msdn.microsoft.com/library/windows/desktop/ms687242) del SDK de Windows.  
  
##  <a name="register"></a>COleDropTarget::Register  
 Llame a esta función para registrar la ventana con las DLL OLE como un destino de colocación válido.  
  
```  
BOOL Register(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Apunta a la ventana que va a registrarse como un destino de colocación.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el registro es correcto; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función debe llamarse para que las operaciones de eliminación a ser aceptados.  
  
 Para obtener más información, consulte [RegisterDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms678405) en el SDK de Windows.  
  
##  <a name="revoke"></a>COleDropTarget::Revoke  
 Llame a esta función antes de destruir cualquier ventana que se ha registrado como un destino de colocación mediante una llamada a [registrar](#register) para quitarlo de la lista de destinos de colocación.  
  
```  
virtual void Revoke();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función se invoca automáticamente desde el [OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy) controlador de la ventana que se ha registrado, por lo que normalmente no es necesario llamar explícitamente a esta función.  
  
 Para obtener más información, consulte [RevokeDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms692643) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo HIERSVR](../../visual-cpp-samples.md)   
 [Ejemplo MFC OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleDropSource (clase)](../../mfc/reference/coledropsource-class.md)
