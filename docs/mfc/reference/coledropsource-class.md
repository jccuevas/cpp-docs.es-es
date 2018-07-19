---
title: Clase COleDropSource | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- COleDropSource [MFC], COleDropSource
- COleDropSource [MFC], GiveFeedback
- COleDropSource [MFC], OnBeginDrag
- COleDropSource [MFC], QueryContinueDrag
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3f601c2b15f5f117f77b1f916027107708e8f19
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038233"
---
# <a name="coledropsource-class"></a>Clase COleDropSource
Permite que los datos que se arrastrarán a un destino de colocación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleDropSource : public CCmdTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDropSource::COleDropSource](#coledropsource)|Construye un objeto `COleDropSource`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDropSource::GiveFeedback](#givefeedback)|Cambia el cursor durante una operación de arrastrar y colocar.|  
|[COleDropSource::OnBeginDrag](#onbegindrag)|Controla la captura del mouse durante una operación de arrastrar y colocar.|  
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|Comprueba si arrastra debe continuar.|  
  
## <a name="remarks"></a>Comentarios  
 El [COleDropTarget](../../mfc/reference/coledroptarget-class.md) clase controla la parte receptora de la operación de arrastrar y colocar. La `COleDropSource` objeto es responsable de determinar cuándo comienza una operación de arrastre, proporcionar comentarios durante la operación de arrastre y determinar cuándo finaliza la operación de arrastre.  
  
 Para usar un `COleDropSource` de objetos, simplemente llame al constructor. Esto simplifica el proceso de determinar qué eventos, como un clic del mouse, comenzar una operación de arrastre mediante [COleDataSource:: DoDragDrop](../../mfc/reference/coledatasource-class.md#dodragdrop), [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop), o [ COleServerItem:: DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop) función. Estas funciones, se creará un `COleDropSource` objeto automáticamente. Puede modificar el comportamiento predeterminado de la `COleDropSource` funciones reemplazables. El marco de trabajo llamará estas funciones miembro en el momento adecuado.  
  
 Para obtener más información sobre operaciones de arrastrar y colocar utilizando OLE, vea el artículo [arrastrar y colocar (OLE)](../../mfc/drag-and-drop-ole.md).  
  
 Para obtener más información, consulte [IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071) del SDK de Windows.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropSource`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="coledropsource"></a>  COleDropSource::COleDropSource  
 Construye un objeto `COleDropSource`.  
  
```  
COleDropSource();
```  
  
##  <a name="givefeedback"></a>  COleDropSource::GiveFeedback  
 Lo llama el marco después de llamar a [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover) o [COleDropTarget::DragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).  
  
```  
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```  
  
### <a name="parameters"></a>Parámetros  
 *EfectoColocar*  
 El efecto que le gustaría mostrar al usuario, por lo general que indica lo que sucedería si se produjera una colocación en este momento con los datos seleccionados. Normalmente, esto es el valor devuelto por la llamada más reciente a [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter) o [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover). Puede ser una o varias de las siguientes acciones:  
  
- `DROPEFFECT_NONE` Una caída no estarían permitida.  
  
- `DROPEFFECT_COPY` Se realizará una operación de copia.  
  
- `DROPEFFECT_MOVE` Se realizará una operación de movimiento.  
  
- `DROPEFFECT_LINK` Se puede establecer un vínculo de los datos perdidos a los datos originales.  
  
- `DROPEFFECT_SCROLL` Una operación de arrastre del desplazamiento está a punto de producirse o se está produciendo en el destino.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **DRAGDROP_S_USEDEFAULTCURSORS** si arrastra está en curso, **NOERROR** si no lo está.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función para proporcionar comentarios al usuario acerca de lo que sucedería si se produjera una colocación en este momento. La implementación predeterminada usa los cursores predeterminados OLE. Para obtener más información sobre operaciones de arrastrar y colocar utilizando OLE, vea el artículo [arrastrar y colocar (OLE)](../../mfc/drag-and-drop-ole.md).  
  
 Para obtener más información, consulte [IDropSource::GiveFeedback](http://msdn.microsoft.com/library/windows/desktop/ms693723), [DoDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms680129), y [IDropTarget::DragEnter](http://msdn.microsoft.com/library/windows/desktop/ms680106) en el SDK de Windows.  
  
##  <a name="onbegindrag"></a>  COleDropSource::OnBeginDrag  
 Llamado por el marco de trabajo cuando produce un evento que pudiera iniciar una operación de arrastre, por ejemplo, al presionar el botón primario del mouse.  
  
```  
virtual BOOL OnBeginDrag(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 *pWnd*  
 Apunta a la ventana que contiene los datos seleccionados.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la arrastra puede, 0 en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si desea modificar la forma en que se inicia el proceso de arrastrar. La implementación predeterminada captura el mouse y permanece en modo de arrastre hasta que el usuario hace clic en el botón izquierdo o derecho del mouse o llega a ESC, momento en el que suelta el mouse.  
  
##  <a name="querycontinuedrag"></a>  COleDropSource::QueryContinueDrag  
 Una vez iniciada la arrastra, esta función se invoca varias veces por el marco de trabajo hasta que se cancela o finaliza la operación de arrastre.  
  
```  
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed, 
    DWORD dwKeyState);
```  
  
### <a name="parameters"></a>Parámetros  
 *bEscapePressed*  
 Indica si se ha presionado la tecla ESC desde la última llamada a `COleDropSource::QueryContinueDrag`.  
  
 *dwKeyState*  
 Contiene el estado de las teclas modificadoras del teclado. Se trata de una combinación de varios de los siguientes valores: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_ MBUTTON**, y **MK_RBUTTON**.  
  
### <a name="return-value"></a>Valor devuelto  
 **DRAGDROP_S_CANCEL** si se presiona la tecla ESC o el botón secundario, o el botón primario se produce antes de arrastrar se inicia. **DRAGDROP_S_DROP** si se debería ejecutar una operación de colocar. En caso contrario, `S_OK`.  
  
### <a name="remarks"></a>Comentarios  
 Se produce reemplazo que esta función si desea cambiar el punto en que arrastre se cancela o una eliminación.  
  
 La implementación predeterminada inicia la operación de colocar o cancela la operación de arrastre como se indica a continuación. Cancela una operación de arrastre cuando se presiona la tecla ESC o el botón secundario del mouse. Inicia una operación de colocar cuando el botón primario del mouse se produce después de arrastrar se ha iniciado. De lo contrario, devuelve `S_OK` y lleva a cabo ninguna operación adicional.  
  
 Dado que esta función se llama con frecuencia, se debe optimizar tanto como sea posible.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo HIERSVR](../../visual-cpp-samples.md)   
 [Ejemplo MFC OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



