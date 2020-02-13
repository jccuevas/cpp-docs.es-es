---
title: Clase COleDropSource
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
ms.openlocfilehash: d93eb3de87b50f337f0d3edad65f5dc3013e8327
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127462"
---
# <a name="coledropsource-class"></a>Clase COleDropSource

Permite arrastrar datos a un destino de colocación.

## <a name="syntax"></a>Sintaxis

```
class COleDropSource : public CCmdTarget
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDropSource::COleDropSource](#coledropsource)|Construye un objeto `COleDropSource`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleDropSource:: GiveFeedback](#givefeedback)|Cambia el cursor durante una operación de arrastrar y colocar.|
|[COleDropSource::OnBeginDrag](#onbegindrag)|Controla la captura del mouse durante una operación de arrastrar y colocar.|
|[COleDropSource:: QueryContinueDrag](#querycontinuedrag)|Comprueba si el arrastre debería continuar.|

## <a name="remarks"></a>Observaciones

La clase [COleDropTarget](../../mfc/reference/coledroptarget-class.md) controla la parte de recepción de la operación de arrastrar y colocar. El objeto `COleDropSource` es responsable de determinar cuándo comienza una operación de arrastre, proporcionar comentarios durante la operación de arrastre y determinar cuándo finaliza la operación de arrastre.

Para usar un objeto `COleDropSource`, simplemente llame al constructor. Esto simplifica el proceso de determinar qué eventos, como un clic del mouse, comienza una operación de arrastre mediante [COleDataSource::D odragdrop](../../mfc/reference/coledatasource-class.md#dodragdrop), [COleClientItem::D odragdrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)o [COleServerItem::D función odragdrop](../../mfc/reference/coleserveritem-class.md#dodragdrop) . Estas funciones crearán un objeto de `COleDropSource`. Es posible que desee modificar el comportamiento predeterminado de las funciones reemplazables `COleDropSource`. El marco de trabajo llamará a estas funciones miembro en el momento adecuado.

Para obtener más información sobre las operaciones de arrastrar y colocar con OLE, vea el artículo [OLE: arrastrar y colocar](../../mfc/drag-and-drop-ole.md).

Para obtener más información, vea [IDropSource](/windows/win32/api/oleidl/nn-oleidl-idropsource) en el Windows SDK.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropSource`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole. h

##  <a name="coledropsource"></a>COleDropSource::COleDropSource

Construye un objeto `COleDropSource`.

```
COleDropSource();
```

##  <a name="givefeedback"></a>COleDropSource:: GiveFeedback

Lo llama el marco de trabajo después de llamar a [COleDropTarget:: OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover) o [COleDropTarget::D ragenter](../../mfc/reference/coledroptarget-class.md#ondragenter).

```
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```

### <a name="parameters"></a>Parámetros

*dropEffect*<br/>
El efecto que le gustaría mostrar al usuario, lo que suele indicar lo que sucedería si se produjera una caída en este punto con los datos seleccionados. Normalmente, este es el valor devuelto por la llamada más reciente a [CView:: OnDragEnter](../../mfc/reference/cview-class.md#ondragenter) o [CView:: OnDragOver](../../mfc/reference/cview-class.md#ondragover). Puede ser uno o varios de los siguientes:

- DROPEFFECT_NONE no se permitiría la eliminación.

- DROPEFFECT_COPY se realizaría una operación de copia.

- DROPEFFECT_MOVE se realizará una operación de movimiento.

- DROPEFFECT_LINK se establecería un vínculo entre los datos colocados y los datos originales.

- DROPEFFECT_SCROLL una operación de desplazamiento de arrastre está a punto de producirse o se está produciendo en el destino.

### <a name="return-value"></a>Valor devuelto

Devuelve DRAGDROP_S_USEDEFAULTCURSORS si el arrastre está en curso, si no lo está.

### <a name="remarks"></a>Observaciones

Invalide esta función para proporcionar información al usuario sobre lo que sucedería si se produjera una caída en este momento. La implementación predeterminada utiliza los cursores predeterminados de OLE. Para obtener más información sobre las operaciones de arrastrar y colocar con OLE, vea el artículo [OLE: arrastrar y colocar](../../mfc/drag-and-drop-ole.md).

Para obtener más información, vea [IDropSource:: GiveFeedback](/windows/win32/api/oleidl/nf-oleidl-idropsource-givefeedback), [IDropTarget::D ragover](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover)y [IDropTarget::D ragenter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) en el Windows SDK.

##  <a name="onbegindrag"></a>COleDropSource::OnBeginDrag

Lo llama el marco de trabajo cuando se produce un evento que puede iniciar una operación de arrastre, como presionar el botón primario del mouse.

```
virtual BOOL OnBeginDrag(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la ventana que contiene los datos seleccionados.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si se permite arrastrar; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Invalide esta función si desea modificar la forma en que se inicia el proceso de arrastre. La implementación predeterminada captura el mouse y permanece en modo de arrastre hasta que el usuario hace clic con el botón primario o secundario del mouse o presiona ESC, momento en el que suelta el mouse.

##  <a name="querycontinuedrag"></a>COleDropSource:: QueryContinueDrag

Una vez que se ha iniciado el arrastre, el marco de trabajo llama a esta función repetidamente hasta que la operación de arrastrar se cancela o se completa.

```
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed,
    DWORD dwKeyState);
```

### <a name="parameters"></a>Parámetros

*bEscapePressed*<br/>
Indica si se ha presionado la tecla ESC desde la última llamada a `COleDropSource::QueryContinueDrag`.

*dwKeyState*<br/>
Contiene el estado de las teclas modificadoras del teclado. Se trata de una combinación de cualquier número de los siguientes: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.

### <a name="return-value"></a>Valor devuelto

DRAGDROP_S_CANCEL si se presiona la tecla ESC o el botón derecho, o el botón primario se produce antes de que se inicie el arrastre. DRAGDROP_S_DROP si se debe realizar una operación de colocar. De lo contrario S_OK.

### <a name="remarks"></a>Observaciones

Invalide esta función si desea cambiar el punto en el que se cancela el arrastre o se produce una caída.

La implementación predeterminada inicia la eliminación o cancela el arrastre del modo siguiente. Cancela una operación de arrastre cuando se presiona la tecla ESC o el botón secundario del mouse. Inicia una operación de colocar cuando se produce el botón primario del mouse después de que se haya iniciado el arrastre. De lo contrario, Devuelve S_OK y no realiza ninguna operación adicional.

Dado que se llama a esta función con frecuencia, debe optimizarse tanto como sea posible.

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo OCLIENT de MFC](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
