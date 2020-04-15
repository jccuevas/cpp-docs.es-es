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
ms.openlocfilehash: 324c4b7273f021b43c319fb0a494ac843856c78a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375024"
---
# <a name="coledropsource-class"></a>COleDropSource (clase)

Permite arrastrar los datos a un destino de colocación.

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
|[COleDropSource::OnBeginDrag](#onbegindrag)|Controla la captura del ratón durante una operación de arrastrar y colocar.|
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|Comprueba si el arrastre debe continuar.|

## <a name="remarks"></a>Observaciones

La [clase COleDropTarget](../../mfc/reference/coledroptarget-class.md) controla la parte receptora de la operación de arrastrar y colocar. El `COleDropSource` objeto es responsable de determinar cuándo comienza una operación de arrastre, proporcionar retroalimentación durante la operación de arrastre y determinar cuándo finaliza la operación de arrastre.

Para usar `COleDropSource` un objeto, simplemente llame al constructor. Esto simplifica el proceso de determinar qué eventos, como un clic del mouse, comienzan una operación de arrastre mediante [COleDataSource::DoDragDrop](../../mfc/reference/coledatasource-class.md#dodragdrop), [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)o [COleServerItem::DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop) función. Estas funciones `COleDropSource` crearán un objeto para usted. Es posible que desee modificar `COleDropSource` el comportamiento predeterminado de las funciones reemplazables. El marco de trabajo llamará a estas funciones miembro en los momentos adecuados.

Para obtener más información sobre las operaciones de arrastrar y colocar mediante OLE, vea el artículo [arrastrar y colocar OLE](../../mfc/drag-and-drop-ole.md).

Para obtener más información, consulte [IDropSource](/windows/win32/api/oleidl/nn-oleidl-idropsource) en el Windows SDK.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropSource`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

## <a name="coledropsourcecoledropsource"></a><a name="coledropsource"></a>COleDropSource::COleDropSource

Construye un objeto `COleDropSource`.

```
COleDropSource();
```

## <a name="coledropsourcegivefeedback"></a><a name="givefeedback"></a>COleDropSource::GiveFeedback

Llamado por el marco de trabajo después de llamar a [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover) o [COleDropTarget::DragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).

```
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```

### <a name="parameters"></a>Parámetros

*dropEffect*<br/>
El efecto que desea mostrar al usuario, normalmente indica lo que sucedería si se produjera una caída en este punto con los datos seleccionados. Normalmente, este es el valor devuelto por la llamada más reciente a [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter) o [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover). Puede ser uno o más de los siguientes:

- DROPEFFECT_NONE No se permitiría una caída.

- DROPEFFECT_COPY Se realizaría una operación de copia.

- DROPEFFECT_MOVE Se realizaría una operación de movimiento.

- DROPEFFECT_LINK Se establecería un vínculo de los datos eliminados a los datos originales.

- DROPEFFECT_SCROLL Una operación de desplazamiento de arrastre está a punto de producirse o se está produciendo en el destino.

### <a name="return-value"></a>Valor devuelto

Devuelve DRAGDROP_S_USEDEFAULTCURSORS si el arrastre está en curso, NOERROR si no lo está.

### <a name="remarks"></a>Observaciones

Invalide esta función para proporcionar comentarios al usuario sobre lo que sucedería si se produjera una colocación en este momento. La implementación predeterminada utiliza los cursores predeterminados OLE. Para obtener más información sobre las operaciones de arrastrar y colocar mediante OLE, vea el artículo [arrastrar y colocar OLE](../../mfc/drag-and-drop-ole.md).

Para obtener más información, vea [IDropSource::GiveFeedback](/windows/win32/api/oleidl/nf-oleidl-idropsource-givefeedback), [IDropTarget::DragOver](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover)e [IDropTarget::DragEnter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) en el Windows SDK.

## <a name="coledropsourceonbegindrag"></a><a name="onbegindrag"></a>COleDropSource::OnBeginDrag

Llamado por el marco de trabajo cuando se produce un evento que podría iniciar una operación de arrastre, como presionar el botón izquierdo del mouse.

```
virtual BOOL OnBeginDrag(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la ventana que contiene los datos seleccionados.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se permite arrastrar, de lo contrario 0.

### <a name="remarks"></a>Observaciones

Reemplace esta función si desea modificar la forma en que se inicia el proceso de arrastre. La implementación predeterminada captura el mouse y permanece en modo de arrastre hasta que el usuario hace clic en el botón izquierdo o derecho del ratón o pulsa ESC, momento en el que suelta el mouse.

## <a name="coledropsourcequerycontinuedrag"></a><a name="querycontinuedrag"></a>COleDropSource::QueryContinueDrag

Una vez iniciado el arrastre, el marco de trabajo llama a esta función repetidamente hasta que se cancela o se completa la operación de arrastre.

```
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed,
    DWORD dwKeyState);
```

### <a name="parameters"></a>Parámetros

*bEscapePressed*<br/>
Indica si se ha presionado la tecla `COleDropSource::QueryContinueDrag`ESC desde la última llamada a .

*dwKeyState*<br/>
Contiene el estado de las teclas modificadoras en el teclado. Esta es una combinación de cualquier número de los siguientes: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.

### <a name="return-value"></a>Valor devuelto

DRAGDROP_S_CANCEL si se pulsa la tecla ESC o el botón derecho, o se levanta el botón izquierdo antes de que se inicie el arrastre. DRAGDROP_S_DROP si se produce una operación de colocación. De lo contrario, S_OK.

### <a name="remarks"></a>Observaciones

Reemplace esta función si desea cambiar el punto en el que se cancela el arrastre o se produce una colocación.

La implementación predeterminada inicia la colocación o cancela el arrastre de la siguiente manera. Cancela una operación de arrastre cuando se pulsa la tecla ESC o el botón derecho del ratón. Inicia una operación de colocación cuando se levanta el botón izquierdo del ratón después de que se haya iniciado el arrastre. De lo contrario, devuelve S_OK y no realiza más operaciones.

Dado que esta función se llama con frecuencia, debe optimizarse tanto como sea posible.

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
