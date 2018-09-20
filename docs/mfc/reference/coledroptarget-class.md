---
title: COleDropTarget (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7947f5fd9b958d6c317c198cc2e34498b89104f6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415543"
---
# <a name="coledroptarget-class"></a>COleDropTarget (clase)

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
|[COleDropTarget::OnDragOver](#ondragover)|Llamado repetidamente cuando se arrastra el cursor sobre la ventana.|
|[COleDropTarget::OnDragScroll](#ondragscroll)|Se llama para determinar si se arrastra el cursor en la región de desplazamiento de la ventana.|
|[COleDropTarget::OnDrop](#ondrop)|Se llama cuando se colocan datos en la ventana, el controlador predeterminado.|
|[COleDropTarget::OnDropEx](#ondropex)|Se llama cuando se colocan datos en la ventana, el controlador inicial.|
|[COleDropTarget::Register](#register)|Registra la ventana como un destino de colocación válido.|
|[COleDropTarget::Revoke](#revoke)|Hace que la ventana para dejar que se va a un destino de colocación válido.|

## <a name="remarks"></a>Comentarios

Creación de un objeto de esta clase permite que una ventana Aceptar los datos a través del mecanismo de arrastrar y colocar OLE.

Para obtener una ventana para aceptar comandos drop, primero debe crear un objeto de la `COleDropTarget` clase y, a continuación, llame a la [registrar](#register) función con un puntero a deseado `CWnd` objeto como el único parámetro.

Para obtener más información sobre las operaciones de arrastrar y colocar mediante OLE, vea el artículo [arrastrar y colocar (OLE)](../../mfc/drag-and-drop-ole.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropTarget`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

##  <a name="coledroptarget"></a>  COleDropTarget::COleDropTarget

Crea un objeto de clase `COleDropTarget`.

```
COleDropTarget();
```

### <a name="remarks"></a>Comentarios

Llame a [registrar](#register) para asociar a una ventana de este objeto.

##  <a name="ondragenter"></a>  COleDropTarget::OnDragEnter

Lo llama el marco cuando primero se arrastra el cursor en la ventana.

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*conquistado*<br/>
Apunta a la ventana que está entrando en el cursor.

*pDataObject*<br/>
Señala al objeto de datos que contiene los datos que se pueden quitar.

*dwKeyState*<br/>
Contiene el estado de las teclas modificadoras. Se trata de una combinación de cualquier número de las siguientes acciones: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.

*punto*<br/>
Contiene la ubicación actual del cursor en coordenadas de cliente.

### <a name="return-value"></a>Valor devuelto

El efecto que tendría como resultado si se han intentado una disminución en la ubicación especificada por *punto*. Puede ser uno o varios de los siguientes:

- DROPEFFECT_NONE no se permitiría un descenso.

- DROPEFFECT_COPY se realizará una operación de copia.

- DROPEFFECT_MOVE se realizará una operación de movimiento.

- ¿Se puede establecer vínculo de un DROPEFFECT_LINK de los datos colocados en los datos originales.

- Operación de desplazamiento DROPEFFECT_SCROLL un arrastre tiene lugar o se está produciendo en el destino.

### <a name="remarks"></a>Comentarios

Reemplace esta función para permitir las operaciones de colocación que se produzca en la ventana. La implementación predeterminada llama [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter), que simplemente devuelve DROPEFFECT_NONE de forma predeterminada.

Para obtener más información, consulte [IDropTarget::DragEnter](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragenter) en el SDK de Windows.

##  <a name="ondragleave"></a>  COleDropTarget::OnDragLeave

Lo llama el marco cuando el cursor sale de la ventana mientras una operación de arrastrar está vigente.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*conquistado*<br/>
Apunta a la ventana que está abandonando el cursor.

### <a name="remarks"></a>Comentarios

Reemplace esta función si desea un comportamiento especial cuando sale de la operación de arrastrar la ventana especificada. La implementación predeterminada de esta función llama [CView::OnDragLeave](../../mfc/reference/cview-class.md#ondragleave).

Para obtener más información, consulte [IDropTarget::DragLeave](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragleave) en el SDK de Windows.

##  <a name="ondragover"></a>  COleDropTarget::OnDragOver

Lo llama el marco de trabajo cuando se arrastra el cursor sobre la ventana.

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*conquistado*<br/>
Apunta a la ventana que el cursor está sobre.

*pDataObject*<br/>
Señala al objeto de datos que contiene los datos que se va a quitar.

*dwKeyState*<br/>
Contiene el estado de las teclas modificadoras. Se trata de una combinación de cualquier número de las siguientes acciones: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.

*punto*<br/>
Contiene la ubicación actual del cursor en coordenadas de cliente.

### <a name="return-value"></a>Valor devuelto

El efecto que tendría como resultado si se han intentado una disminución en la ubicación especificada por *punto*. Puede ser uno o varios de los siguientes:

- DROPEFFECT_NONE no se permitiría un descenso.

- DROPEFFECT_COPY se realizará una operación de copia.

- DROPEFFECT_MOVE se realizará una operación de movimiento.

- ¿Se puede establecer vínculo de un DROPEFFECT_LINK de los datos colocados en los datos originales.

- DROPEFFECT_SCROLL indica que está a punto de producirse una operación de desplazamiento de arrastre o que se está produciendo en el destino.

### <a name="remarks"></a>Comentarios

Esta función se debe invalidar para permitir las operaciones de colocación que se produzca en la ventana. La implementación predeterminada de esta función llama [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover), que devuelve DROPEFFECT_NONE de forma predeterminada. Dado que esta función se llama con frecuencia durante una operación de arrastrar y colocar, se debe optimizar tanto como sea posible.

Para obtener más información, consulte [DoDragDrop](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragover) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]

##  <a name="ondragscroll"></a>  COleDropTarget::OnDragScroll

Lo llama el marco antes de llamar a [OnDragEnter](#ondragenter) o [OnDragOver](#ondragover) para determinar si *punto* está en la región desplazable.

```
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*conquistado*<br/>
Apunta a la ventana que el cursor está actualmente.

*dwKeyState*<br/>
Contiene el estado de las teclas modificadoras. Se trata de una combinación de cualquier número de las siguientes acciones: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.

*punto*<br/>
Contiene la ubicación del cursor, en píxeles, relativo a la pantalla.

### <a name="return-value"></a>Valor devuelto

El efecto que tendría como resultado si se han intentado una disminución en la ubicación especificada por *punto*. Puede ser uno o varios de los siguientes:

- DROPEFFECT_NONE no se permitiría un descenso.

- DROPEFFECT_COPY se realizará una operación de copia.

- DROPEFFECT_MOVE se realizará una operación de movimiento.

- ¿Se puede establecer vínculo de un DROPEFFECT_LINK de los datos colocados en los datos originales.

- DROPEFFECT_SCROLL indica que está a punto de producirse una operación de desplazamiento de arrastre o que se está produciendo en el destino.

### <a name="remarks"></a>Comentarios

Reemplace esta función cuando desea proporcionar un comportamiento especial para este evento. La implementación predeterminada de esta función llama [CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll), que devuelve DROPEFFECT_NONE y se desplaza la ventana cuando se arrastra el cursor en la región de desplazamiento predeterminado dentro del borde de la ventana.

##  <a name="ondrop"></a>  COleDropTarget::OnDrop

Lo llama el marco de trabajo cuando tiene lugar una operación de colocar.

```
virtual BOOL OnDrop(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*conquistado*<br/>
Apunta a la ventana que el cursor está actualmente.

*pDataObject*<br/>
Señala al objeto de datos que contiene los datos que se va a quitar.

*EfectoColocar*<br/>
El efecto que el usuario ha elegido para la operación de colocar. Puede ser uno o varios de los siguientes:

- DROPEFFECT_COPY se realizará una operación de copia.

- DROPEFFECT_MOVE se realizará una operación de movimiento.

- ¿Se puede establecer vínculo de un DROPEFFECT_LINK de los datos colocados en los datos originales.

*punto*<br/>
Contiene la ubicación del cursor, en píxeles, relativo a la pantalla.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación de colocar se realiza correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

La primera de marco de trabajo llama a [OnDropEx](#ondropex). Si el `OnDropEx` función no controla la colocación, el marco de trabajo, a continuación, llama a esta función miembro, `OnDrop`. Normalmente, la aplicación reemplaza [OnDropEx](../../mfc/reference/cview-class.md#ondropex) en la clase de vista para controlar el botón secundario del mouse, arrastrar y colocar. Normalmente, la clase de vista [OnDrop](../../mfc/reference/cview-class.md#ondrop) se usa para controlar tan sólo arrastrar y colocar.

La implementación predeterminada de `COleDropTarget::OnDrop` llamadas [CView::OnDrop](../../mfc/reference/cview-class.md#ondrop), que simplemente devuelve FALSE de forma predeterminada.

Para obtener más información, consulte [IDropTarget:: DROP](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-drop) en el SDK de Windows.

##  <a name="ondropex"></a>  COleDropTarget::OnDropEx

Lo llama el marco de trabajo cuando tiene lugar una operación de colocar.

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*conquistado*<br/>
Apunta a la ventana que el cursor está actualmente.

*pDataObject*<br/>
Señala al objeto de datos que contiene los datos que se va a quitar.

*dropDefault*<br/>
El efecto que el usuario ha elegido para la operación de colocar de forma predeterminada, según el estado actual de la clave. Puede ser DROPEFFECT_NONE. Efectos de colocar se tratan en la sección Comentarios.

*lista desplegable*<br/>
Una lista de los efectos de colocar que admite el origen de colocación. Los valores de efecto de colocar se pueden combinar con la operación OR bit a bit (**&#124;**) operación. Efectos de colocar se tratan en la sección Comentarios.

*punto*<br/>
Contiene la ubicación del cursor, en píxeles, relativo a la pantalla.

### <a name="return-value"></a>Valor devuelto

El efecto que dan como resultado del intento de colocar en la ubicación especificada por *punto*. Efectos de colocar se tratan en la sección Comentarios.

### <a name="remarks"></a>Comentarios

En primer lugar, el marco llama a esta función. Si no controla la colocación, a continuación, llama el marco de trabajo [OnDrop](#ondrop). Por lo general, deberá reemplazar [OnDropEx](../../mfc/reference/cview-class.md#ondropex) en la clase de vista para admitir el botón secundario del mouse, arrastrar y colocar. Normalmente, la clase de vista [OnDrop](../../mfc/reference/cview-class.md#ondrop) se usa para controlar el caso de la compatibilidad con tan sólo arrastrar y colocar.

La implementación predeterminada de `COleDropTarget::OnDropEx` llamadas [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex). De forma predeterminada, [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex) simplemente devuelve un valor ficticio para indicar el [OnDrop](#ondrop) debe llamar a la función miembro.

Efectos de colocar describen la acción asociada con una operación de colocar. Consulte la siguiente lista de efectos de colocación:

- DROPEFFECT_NONE no se permitiría un descenso.

- DROPEFFECT_COPY se realizará una operación de copia.

- DROPEFFECT_MOVE se realizará una operación de movimiento.

- ¿Se puede establecer vínculo de un DROPEFFECT_LINK de los datos colocados en los datos originales.

- DROPEFFECT_SCROLL indica que está a punto de producirse una operación de desplazamiento de arrastre o que se está produciendo en el destino.

Para obtener más información, consulte [IDropTarget:: DROP](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-drop) en el SDK de Windows.

##  <a name="register"></a>  COleDropTarget::Register

Llame a esta función para registrar la ventana con las DLL OLE como un destino de colocación válido.

```
BOOL Register(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*conquistado*<br/>
Apunta a la ventana que va a registrarse como un destino de colocación.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el registro se realiza correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función debe llamarse para que las operaciones de colocación que se acepte.

Para obtener más información, consulte [RegisterDragDrop](/windows/desktop/api/ole2/nf-ole2-registerdragdrop) en el SDK de Windows.

##  <a name="revoke"></a>  COleDropTarget::Revoke

Llame a esta función antes de destruir cualquier ventana que se ha registrado como un destino de colocación mediante una llamada a [registrar](#register) para quitarlo de la lista de destinos de colocación.

```
virtual void Revoke();
```

### <a name="remarks"></a>Comentarios

Esta función se llama automáticamente desde el [OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy) controlador para la ventana que se registró, por lo que normalmente no es necesario llamar explícitamente a esta función.

Para obtener más información, consulte [RevokeDragDrop](/windows/desktop/api/ole2/nf-ole2-revokedragdrop) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Ejemplo HIERSVR](../../visual-cpp-samples.md)<br/>
[Ejemplo MFC OCLIENT](../../visual-cpp-samples.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDropSource (clase)](../../mfc/reference/coledropsource-class.md)
