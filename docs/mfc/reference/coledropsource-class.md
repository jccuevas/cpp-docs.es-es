---
title: COleDropSource (clase)
ms.date: 11/04/2016
f1_keywords:
- COleDropSource
- AFXOLE/COleDropSource
- AFXOLE/COleDropSource::COleDropSource
- AFXOLE/COleDropSource::GiveFeedback
- AFXOLE/COleDropSource::OnBeginDrag
- AFXOLE/COleDropSource::QueryContinueDrag
helpviewer_keywords:
- COleDropSource [MFC], COleDropSource
- COleDropSource [MFC], GiveFeedback
- COleDropSource [MFC], OnBeginDrag
- COleDropSource [MFC], QueryContinueDrag
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
ms.openlocfilehash: 51d524054b67a5cecc5aa7791b0aeea0cc076813
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457790"
---
# <a name="coledropsource-class"></a>COleDropSource (clase)

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
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|Comprueba si la operación de arrastre debería continuar.|

## <a name="remarks"></a>Comentarios

El [COleDropTarget](../../mfc/reference/coledroptarget-class.md) clase controla la parte receptora de la operación de arrastrar y colocar. La `COleDropSource` objeto es responsable de determinar cuándo comienza una operación de arrastre, proporcionar comentarios durante la operación de arrastrar y determinar cuándo finaliza la operación de arrastre.

Para usar un `COleDropSource` de objetos, simplemente llame al constructor. Esto simplifica el proceso de determinar qué eventos, como un clic del mouse, comenzar una operación de arrastre mediante [COleDataSource:: DoDragDrop](../../mfc/reference/coledatasource-class.md#dodragdrop), [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop), o [ COleServerItem:: DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop) función. Estas funciones se creará un `COleDropSource` objeto automáticamente. Es posible que desee modificar el comportamiento predeterminado de la `COleDropSource` funciones reemplazables. Estas funciones miembro se llamará en el momento adecuado, el marco de trabajo.

Para obtener más información sobre las operaciones de arrastrar y colocar mediante OLE, vea el artículo [arrastrar y colocar (OLE)](../../mfc/drag-and-drop-ole.md).

Para obtener más información, consulte [IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource) en el SDK de Windows.

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

Lo llama el marco de trabajo después de llamar a [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover) o [COleDropTarget::DragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).

```
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```

### <a name="parameters"></a>Parámetros

*EfectoColocar*<br/>
El efecto que le gustaría mostrar al usuario, normalmente, que indica lo que sucedería si se produjera una colocación en este momento con los datos seleccionados. Normalmente, esto es el valor devuelto por la llamada más reciente a [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter) o [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover). Puede ser uno o varios de los siguientes:

- DROPEFFECT_NONE no se permitiría un descenso.

- DROPEFFECT_COPY se realizará una operación de copia.

- DROPEFFECT_MOVE se realizará una operación de movimiento.

- ¿Se puede establecer vínculo de un DROPEFFECT_LINK de los datos colocados en los datos originales.

- Operación de desplazamiento DROPEFFECT_SCROLL un arrastre tiene lugar o se está produciendo en el destino.

### <a name="return-value"></a>Valor devuelto

Devuelve DRAGDROP_S_USEDEFAULTCURSORS si arrastra está en curso, NOERROR si no lo está.

### <a name="remarks"></a>Comentarios

Reemplace esta función para proporcionar comentarios al usuario sobre lo que sucedería si se produjera una colocación en este momento. La implementación predeterminada usa los cursores predeterminados OLE. Para obtener más información sobre las operaciones de arrastrar y colocar mediante OLE, vea el artículo [arrastrar y colocar (OLE)](../../mfc/drag-and-drop-ole.md).

Para obtener más información, consulte [IDropSource::GiveFeedback](/windows/desktop/api/oleidl/nf-oleidl-idropsource-givefeedback), [DoDragDrop](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragover), y [IDropTarget::DragEnter](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragenter) en el SDK de Windows.

##  <a name="onbegindrag"></a>  COleDropSource::OnBeginDrag

Lo llama el marco de trabajo cuando produce un evento que pudiera iniciar una operación de arrastre, por ejemplo, al presionar el botón primario del mouse.

```
virtual BOOL OnBeginDrag(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*conquistado*<br/>
Apunta a la ventana que contiene los datos seleccionados.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación de arrastre puede, 0 en caso contrario.

### <a name="remarks"></a>Comentarios

Reemplace esta función si desea modificar la forma en que se inicia el proceso de arrastrar. La implementación predeterminada, captura el mouse y permanece en modo de arrastre hasta que el usuario hace clic en el botón izquierdo o derecho del mouse o presiona ESC, momento en el que suelta el mouse.

##  <a name="querycontinuedrag"></a>  COleDropSource::QueryContinueDrag

Una vez iniciada la operación de arrastre, esta función se invoca varias veces el marco de trabajo hasta que se cancela o finaliza la operación de arrastre.

```
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed,
    DWORD dwKeyState);
```

### <a name="parameters"></a>Parámetros

*bEscapePressed*<br/>
Indica si se ha presionado la tecla ESC desde la última llamada a `COleDropSource::QueryContinueDrag`.

*dwKeyState*<br/>
Contiene el estado de las teclas modificadoras del teclado. Se trata de una combinación de cualquier número de las siguientes acciones: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.

### <a name="return-value"></a>Valor devuelto

DRAGDROP_S_CANCEL si la tecla ESC o el botón secundario está presionado o el botón se produce antes de arrastrar se inicia. DRAGDROP_S_DROP si debe producirse una operación de colocar. S_OK en caso contrario.

### <a name="remarks"></a>Comentarios

Invalidación de que esta función si desea cambiar el punto en el que arrastrar se cancela o una caída se produce.

La implementación predeterminada inicia la operación de colocar o cancela la operación de arrastre como sigue. Cancela una operación de arrastre cuando se presiona la tecla ESC o el botón secundario del mouse. Inicia una operación de colocar cuando el botón primario del mouse se produce después de que haya iniciado el arrastre. En caso contrario, devuelve S_OK y lleva a cabo ninguna operación adicional.

Dado que esta función se llama con frecuencia, se debe optimizar tanto como sea posible.

## <a name="see-also"></a>Vea también

[Ejemplo HIERSVR](../../visual-cpp-samples.md)<br/>
[Ejemplo MFC OCLIENT](../../visual-cpp-samples.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)

