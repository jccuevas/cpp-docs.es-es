---
title: Clase COleDropSource | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDropSource
- AFXOLE/COleDropSource
- AFXOLE/COleDropSource::COleDropSource
- AFXOLE/COleDropSource::GiveFeedback
- AFXOLE/COleDropSource::OnBeginDrag
- AFXOLE/COleDropSource::QueryContinueDrag
dev_langs:
- C++
helpviewer_keywords:
- drag operations
- drop target, dragging data to
- COleDropSource class
- drag and drop, drop source
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
caps.latest.revision: 24
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: f3d0e5b7184cf305459173065b8e1cc07e032aef
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="coledropsource-class"></a>Clase COleDropSource
Permite que los datos que se arrastrarán a un destino de colocación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleDropSource : public CCmdTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleDropSource::COleDropSource](#coledropsource)|Construye un objeto `COleDropSource`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleDropSource::GiveFeedback](#givefeedback)|Cambia el cursor durante una operación de arrastrar y colocar.|  
|[COleDropSource::OnBeginDrag](#onbegindrag)|Controla la captura del mouse durante una operación de arrastrar y colocar.|  
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|Comprueba si arrastra debe continuar.|  
  
## <a name="remarks"></a>Comentarios  
 El [COleDropTarget](../../mfc/reference/coledroptarget-class.md) clase controla la parte receptora de la operación de arrastrar y colocar. La `COleDropSource` objeto es responsable de determinar cuándo comienza una operación de arrastre, proporcionar comentarios durante la operación de arrastre y determinar cuándo finaliza la operación de arrastre.  
  
 Para usar un `COleDropSource` de objeto, simplemente llame al constructor. Esto simplifica el proceso de determinar qué eventos, como un clic del mouse, inician una operación de arrastre mediante [COleDataSource:: DoDragDrop](../../mfc/reference/coledatasource-class.md#dodragdrop), [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop), o [COleServerItem:: DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop) (función). Estas funciones se creará un `COleDropSource` objeto. Puede modificar el comportamiento predeterminado de la `COleDropSource` funciones reemplazables. El marco de trabajo llamará estas funciones miembro en el momento adecuado.  
  
 Para obtener más información sobre las operaciones de arrastrar y colocar con OLE, vea el artículo [arrastrar y colocar (OLE)](../../mfc/drag-and-drop-ole.md).  
  
 Para obtener más información, consulte [IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropSource`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="coledropsource"></a>COleDropSource::COleDropSource  
 Construye un objeto `COleDropSource`.  
  
```  
COleDropSource();
```  
  
##  <a name="givefeedback"></a>COleDropSource::GiveFeedback  
 Llamado por el marco después de llamar a [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover) o [COleDropTarget::DragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).  
  
```  
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```  
  
### <a name="parameters"></a>Parámetros  
 `dropEffect`  
 El efecto que desea mostrar al usuario, normalmente que indica lo que sucedería si se produjera una colocación en este momento con los datos seleccionados. Normalmente, este es el valor devuelto por la llamada más reciente a [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter) o [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover). Puede ser uno o varios de los siguientes:  
  
- `DROPEFFECT_NONE`No se permitirá una caída.  
  
- `DROPEFFECT_COPY`Se realizará una operación de copia.  
  
- `DROPEFFECT_MOVE`Se realizará una operación de movimiento.  
  
- `DROPEFFECT_LINK`Se puede establecer un vínculo desde los datos colocados en los datos originales.  
  
- `DROPEFFECT_SCROLL`Una operación de desplazamiento de arrastrar tiene lugar o se está produciendo en el destino.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **DRAGDROP_S_USEDEFAULTCURSORS** si arrastra está en curso, **NOERROR** si no lo está.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para proporcionar comentarios al usuario acerca de lo que sucedería si se produjera una colocación en este momento. La implementación predeterminada usa los cursores predeterminados OLE. Para obtener más información sobre las operaciones de arrastrar y colocar con OLE, vea el artículo [arrastrar y colocar (OLE)](../../mfc/drag-and-drop-ole.md).  
  
 Para obtener más información, consulte [IDropSource::GiveFeedback](http://msdn.microsoft.com/library/windows/desktop/ms693723), [DoDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms680129), y [IDropTarget::DragEnter](http://msdn.microsoft.com/library/windows/desktop/ms680106) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="onbegindrag"></a>COleDropSource::OnBeginDrag  
 Llamado por el marco de trabajo cuando produce un evento que pudiera iniciar una operación de arrastre, como presionar el botón primario del mouse.  
  
```  
virtual BOOL OnBeginDrag(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Apunta a la ventana que contiene los datos seleccionados.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si arrastra está permitido, en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si desea modificar la forma en que se inicia el proceso de arrastre. La implementación predeterminada captura el mouse y permanece en modo de arrastre hasta que el usuario hace clic en el botón izquierdo o derecho del mouse o presiona ESC, momento en el que suelta el mouse.  
  
##  <a name="querycontinuedrag"></a>COleDropSource::QueryContinueDrag  
 Después de que comience a arrastrar, esta función se invoca varias veces por el marco de trabajo hasta que la operación de arrastre se cancela o finaliza.  
  
```  
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed, 
    DWORD dwKeyState);
```  
  
### <a name="parameters"></a>Parámetros  
 *bEscapePressed*  
 Indica si se ha presionado la tecla ESC desde la última llamada a `COleDropSource::QueryContinueDrag`.  
  
 `dwKeyState`  
 Contiene el estado de las teclas modificadoras del teclado. Se trata de una combinación de cualquier número de los siguientes: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_MBUTTON**, y **MK_RBUTTON**.  
  
### <a name="return-value"></a>Valor devuelto  
 **DRAGDROP_S_CANCEL** si se presiona la tecla ESC o el botón secundario, o el botón primario se produce antes de arrastrar se inicia. **DRAGDROP_S_DROP** si se produce una operación de colocar. De lo contrario, `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Se produce reemplazar que esta función si desea cambiar el punto en que arrastre se cancela o un menú.  
  
 La implementación predeterminada inicia la operación de colocar o cancela la operación de arrastre como sigue. Cancela una operación de arrastre cuando se presiona la tecla ESC o el botón secundario del mouse. Inicia una operación de colocar cuando se genera el botón primario del mouse después de arrastrar se ha iniciado. De lo contrario, devuelve `S_OK` y no realiza ninguna operación adicional.  
  
 Dado que esta función se llama con frecuencia, se debe optimizar tanto como sea posible.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo HIERSVR](../../visual-cpp-samples.md)   
 [Ejemplo MFC OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




