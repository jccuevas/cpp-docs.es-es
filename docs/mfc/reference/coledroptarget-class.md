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
- COleDropTarget class
- drag and drop, drop target
- drop commands, accepting
- drop commands
ms.assetid: a58c9a48-6a93-4357-b078-4594df258311
caps.latest.revision: 23
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
ms.openlocfilehash: 0e9429d531d6af86bc571b1f871fbcd4a8fe2532
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="coledroptarget-class"></a>Clase COleDropTarget
Proporciona el mecanismo de comunicación entre una ventana y las bibliotecas OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleDropTarget : public CCmdTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleDropTarget::COleDropTarget](#coledroptarget)|Construye un objeto `COleDropTarget`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleDropTarget::OnDragEnter](#ondragenter)|Se llama cuando el cursor entra por primera vez la ventana.|  
|[COleDropTarget::OnDragLeave](#ondragleave)|Se llama cuando se arrastra el cursor fuera de la ventana.|  
|[COleDropTarget::OnDragOver](#ondragover)|Se llama repetidamente cuando se arrastra el cursor sobre la ventana.|  
|[COleDropTarget::OnDragScroll](#ondragscroll)|Se llama para determinar si se arrastra el cursor en la región de desplazamiento de la ventana.|  
|[COleDropTarget::OnDrop](#ondrop)|Se llama cuando se colocan datos en la ventana, el controlador predeterminado.|  
|[COleDropTarget::OnDropEx](#ondropex)|Se llama cuando se colocan datos en la ventana, el controlador inicial.|  
|[COleDropTarget::Register](#register)|La ventana se registra como un destino de colocación válido.|  
|[COleDropTarget::Revoke](#revoke)|Hace que la ventana para dejar que se va a un destino de colocación válido.|  
  
## <a name="remarks"></a>Comentarios  
 Creación de un objeto de esta clase permite que una ventana Aceptar los datos a través del mecanismo de arrastrar y colocar OLE.  
  
 Para obtener una ventana para aceptar comandos drop, primero debe crear un objeto de la `COleDropTarget` de clase y, a continuación, llame a la [registrar](#register) función con un puntero a la `CWnd` objeto como el único parámetro.  
  
 Para obtener más información sobre las operaciones de arrastrar y colocar con OLE, vea el artículo [arrastrar y colocar (OLE)](../../mfc/drag-and-drop-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropTarget`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="coledroptarget"></a>COleDropTarget::COleDropTarget  
 Construye un objeto de la clase `COleDropTarget`.  
  
```  
COleDropTarget();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a [registrar](#register) para asociar a una ventana de este objeto.  
  
##  <a name="ondragenter"></a>COleDropTarget::OnDragEnter  
 Llamado por el marco cuando primero se arrastra el cursor en la ventana.  
  
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
 Contiene el estado de las teclas modificadoras. Se trata de una combinación de cualquier número de los siguientes: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_MBUTTON**, y **MK_RBUTTON**.  
  
 `point`  
 Contiene la ubicación actual del cursor en coordenadas de cliente.  
  
### <a name="return-value"></a>Valor devuelto  
 El efecto que resultaría si se intenta una colocación en la ubicación especificada por `point`. Puede ser uno o varios de los siguientes:  
  
- `DROPEFFECT_NONE`No se permitirá una caída.  
  
- `DROPEFFECT_COPY`Se realizará una operación de copia.  
  
- `DROPEFFECT_MOVE`Se realizará una operación de movimiento.  
  
- `DROPEFFECT_LINK`Se puede establecer un vínculo desde los datos colocados en los datos originales.  
  
- `DROPEFFECT_SCROLL`Una operación de desplazamiento de arrastrar tiene lugar o se está produciendo en el destino.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para permitir operaciones de colocar en la ventana. La implementación predeterminada llama [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter), que simplemente devuelve `DROPEFFECT_NONE` de forma predeterminada.  
  
 Para obtener más información, consulte [IDropTarget::DragEnter](http://msdn.microsoft.com/library/windows/desktop/ms680106) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="ondragleave"></a>COleDropTarget::OnDragLeave  
 Lo llama el marco de trabajo cuando el cursor sale de la ventana mientras una operación de arrastre está en vigor.  
  
```  
virtual void OnDragLeave(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Apunta a la ventana que deja el cursor.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si desea un comportamiento especial cuando la operación de arrastre sale de la ventana especificada. La implementación predeterminada de esta función llama [CView::OnDragLeave](../../mfc/reference/cview-class.md#ondragleave).  
  
 Para obtener más información, consulte [IDropTarget::DragLeave](http://msdn.microsoft.com/library/windows/desktop/ms680110) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="ondragover"></a>COleDropTarget::OnDragOver  
 Lo llama el marco de trabajo cuando se arrastra el cursor sobre la ventana.  
  
```  
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Apunta a la ventana que el cursor está sobre.  
  
 `pDataObject`  
 Señala al objeto de datos que contiene los datos que se va a quitar.  
  
 `dwKeyState`  
 Contiene el estado de las teclas modificadoras. Se trata de una combinación de cualquier número de los siguientes: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_MBUTTON**, y **MK_RBUTTON**.  
  
 `point`  
 Contiene la ubicación actual del cursor en coordenadas de cliente.  
  
### <a name="return-value"></a>Valor devuelto  
 El efecto que resultaría si se intenta una colocación en la ubicación especificada por `point`. Puede ser uno o varios de los siguientes:  
  
- `DROPEFFECT_NONE`No se permitirá una caída.  
  
- `DROPEFFECT_COPY`Se realizará una operación de copia.  
  
- `DROPEFFECT_MOVE`Se realizará una operación de movimiento.  
  
- `DROPEFFECT_LINK`Se puede establecer un vínculo desde los datos colocados en los datos originales.  
  
- `DROPEFFECT_SCROLL`Indica que una operación de desplazamiento de arrastrar tiene lugar o se está produciendo en el destino.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se debe invalidar para permitir operaciones de colocar en la ventana. La implementación predeterminada de esta función llama [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover), que devuelve `DROPEFFECT_NONE` de forma predeterminada. Dado que esta función se llama con frecuencia durante una operación de arrastrar y colocar, se debe optimizar tanto como sea posible.  
  
 Para obtener más información, consulte [DoDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms680129) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[21 NVC_MFCOleContainer](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]  
  
##  <a name="ondragscroll"></a>COleDropTarget::OnDragScroll  
 Llamado por el marco antes de llamar a [OnDragEnter](#ondragenter) o [OnDragOver](#ondragover) para determinar si `point` está en la región desplazable.  
  
```  
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Apunta a la ventana que el cursor está actualmente.  
  
 `dwKeyState`  
 Contiene el estado de las teclas modificadoras. Se trata de una combinación de cualquier número de los siguientes: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_MBUTTON**, y **MK_RBUTTON**.  
  
 `point`  
 Contiene la ubicación del cursor, en píxeles, relativo a la pantalla.  
  
### <a name="return-value"></a>Valor devuelto  
 El efecto que resultaría si se intenta una colocación en la ubicación especificada por `point`. Puede ser uno o varios de los siguientes:  
  
- `DROPEFFECT_NONE`No se permitirá una caída.  
  
- `DROPEFFECT_COPY`Se realizará una operación de copia.  
  
- `DROPEFFECT_MOVE`Se realizará una operación de movimiento.  
  
- `DROPEFFECT_LINK`Se puede establecer un vínculo desde los datos colocados en los datos originales.  
  
- `DROPEFFECT_SCROLL`Indica que una operación de desplazamiento de arrastrar tiene lugar o se está produciendo en el destino.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función cuando desea proporcionar un comportamiento especial para este evento. La implementación predeterminada de esta función llama [CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll), que devuelve `DROPEFFECT_NONE` y se desplaza la ventana cuando se arrastra el cursor en la región de desplazamiento predeterminado dentro del borde de la ventana.  
  
##  <a name="ondrop"></a>COleDropTarget::OnDrop  
 Llamado por el marco de trabajo cuando tiene lugar una operación de colocar.  
  
```  
virtual BOOL OnDrop(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Apunta a la ventana que el cursor está actualmente.  
  
 `pDataObject`  
 Señala al objeto de datos que contiene los datos que se va a quitar.  
  
 `dropEffect`  
 El efecto que el usuario ha elegido para la operación de colocar. Puede ser uno o varios de los siguientes:  
  
- `DROPEFFECT_COPY`Se realizará una operación de copia.  
  
- `DROPEFFECT_MOVE`Se realizará una operación de movimiento.  
  
- `DROPEFFECT_LINK`Se puede establecer un vínculo desde los datos colocados en los datos originales.  
  
 `point`  
 Contiene la ubicación del cursor, en píxeles, relativo a la pantalla.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la eliminación se realiza correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El marco llama primero [OnDropEx](#ondropex). Si el `OnDropEx` función no controla la colocación, el marco de trabajo, a continuación, llama a esta función miembro, `OnDrop`. Normalmente, la aplicación reemplaza [OnDropEx](../../mfc/reference/cview-class.md#ondropex) en la clase de vista para controlar el botón secundario del mouse, arrastrar y colocar. Normalmente, la clase de vista [OnDrop](../../mfc/reference/cview-class.md#ondrop) se utiliza para controlar simples de arrastrar y colocar.  
  
 La implementación predeterminada de `COleDropTarget::OnDrop` llamadas [CView::OnDrop](../../mfc/reference/cview-class.md#ondrop), que simplemente devuelve **FALSE** de forma predeterminada.  
  
 Para obtener más información, consulte [IDropTarget:: DROP](http://msdn.microsoft.com/library/windows/desktop/ms687242) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="ondropex"></a>COleDropTarget::OnDropEx  
 Llamado por el marco de trabajo cuando tiene lugar una operación de colocar.  
  
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
 Apunta a la ventana que el cursor está actualmente.  
  
 `pDataObject`  
 Señala al objeto de datos que contiene los datos que se va a quitar.  
  
 `dropDefault`  
 El efecto que el usuario ha elegido para la operación de colocar de forma predeterminada según el estado actual de la clave. Puede ser `DROPEFFECT_NONE`. Efectos de colocar se explican en la sección Comentarios.  
  
 `dropList`  
 Una lista de los efectos de colocación que admite el origen de colocación. Los valores de efecto de colocar se pueden combinar mediante una operación OR bit a bit ( **|**) operación. Efectos de colocar se explican en la sección Comentarios.  
  
 `point`  
 Contiene la ubicación del cursor, en píxeles, relativo a la pantalla.  
  
### <a name="return-value"></a>Valor devuelto  
 El efecto que dan como resultado del intento de colocar en la ubicación especificada por `point`. Efectos de colocar se explican en la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama primero a esta función. Si no controla la colocación, el marco de trabajo llama [OnDrop](#ondrop). Normalmente, se invalidarán [OnDropEx](../../mfc/reference/cview-class.md#ondropex) en la clase de vista para admitir el botón secundario del mouse, arrastrar y colocar. Normalmente, la clase de vista [OnDrop](../../mfc/reference/cview-class.md#ondrop) se utiliza para controlar el caso de la compatibilidad con sólo arrastrar y soltar.  
  
 La implementación predeterminada de `COleDropTarget::OnDropEx` llamadas [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex). De forma predeterminada, [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex) simplemente devuelve un valor ficticio para indicar la [OnDrop](#ondrop) se debe llamar la función miembro.  
  
 La acción asociada a una operación de colocar describen los efectos de colocación. Consulte la siguiente lista de efectos de colocar:  
  
- `DROPEFFECT_NONE`No se permitirá una caída.  
  
- `DROPEFFECT_COPY`Se realizará una operación de copia.  
  
- `DROPEFFECT_MOVE`Se realizará una operación de movimiento.  
  
- `DROPEFFECT_LINK`Se puede establecer un vínculo desde los datos colocados en los datos originales.  
  
- `DROPEFFECT_SCROLL`Indica que una operación de desplazamiento de arrastrar tiene lugar o se está produciendo en el destino.  
  
 Para obtener más información, consulte [IDropTarget:: DROP](http://msdn.microsoft.com/library/windows/desktop/ms687242) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="register"></a>COleDropTarget::Register  
 Llame a esta función para registrar la ventana con las DLL de OLE como un destino de colocación válido.  
  
```  
BOOL Register(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Apunta a la ventana que debe registrarse como un destino de colocación.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el registro es correcto; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función debe llamarse para que operaciones de colocar a ser aceptados.  
  
 Para obtener más información, consulte [RegisterDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms678405) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="revoke"></a>COleDropTarget::Revoke  
 Llame a esta función antes de destruir cualquier ventana que se ha registrado como un destino de colocación mediante una llamada a [registrar](#register) para quitar de la lista de destinos de colocación.  
  
```  
virtual void Revoke();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función se invoca automáticamente desde el [OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy) controlador de la ventana que se ha registrado, por lo que normalmente no es necesario llamar explícitamente a esta función.  
  
 Para obtener más información, consulte [RevokeDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms692643) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo HIERSVR](../../visual-cpp-samples.md)   
 [Ejemplo MFC OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase COleDropSource](../../mfc/reference/coledropsource-class.md)

