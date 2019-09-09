---
title: Clase COleDropTarget
ms.date: 11/04/2016
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
ms.openlocfilehash: 891b19112c8baf2efb088f064892e1ea19a7deab
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503975"
---
# <a name="coledroptarget-class"></a>Clase COleDropTarget

Proporciona el mecanismo de comunicación entre una ventana y las bibliotecas OLE.

## <a name="syntax"></a>Sintaxis

```
class COleDropTarget : public CCmdTarget
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleDropTarget::COleDropTarget](#coledroptarget)|Construye un objeto `COleDropTarget`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleDropTarget::OnDragEnter](#ondragenter)|Se llama cuando el cursor entra por primera vez en la ventana.|
|[COleDropTarget::OnDragLeave](#ondragleave)|Se le llama cuando se arrastra el cursor fuera de la ventana.|
|[COleDropTarget::OnDragOver](#ondragover)|Se llama repetidamente cuando se arrastra el cursor sobre la ventana.|
|[COleDropTarget::OnDragScroll](#ondragscroll)|Se llama para determinar si el cursor se arrastra en el área de desplazamiento de la ventana.|
|[COleDropTarget::OnDrop](#ondrop)|Se llama cuando los datos se colocan en el controlador predeterminado de la ventana.|
|[COleDropTarget::OnDropEx](#ondropex)|Se llama cuando los datos se colocan en la ventana, controlador inicial.|
|[COleDropTarget::Register](#register)|Registra la ventana como un destino de colocación válido.|
|[COleDropTarget::Revoke](#revoke)|Hace que la ventana deje de ser un destino de colocación válido.|

## <a name="remarks"></a>Comentarios

La creación de un objeto de esta clase permite que una ventana acepte datos a través del mecanismo de arrastrar y colocar de OLE.

Para obtener una ventana que acepte comandos Drop, primero debe crear un objeto de la `COleDropTarget` clase y, a continuación, llamar a la función [Register](#register) con un puntero al `CWnd` objeto deseado como único parámetro.

Para obtener más información sobre las operaciones de arrastrar y colocar con OLE, vea el artículo [arrastrar y colocar (OLE)](../../mfc/drag-and-drop-ole.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropTarget`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole. h

##  <a name="coledroptarget"></a>  COleDropTarget::COleDropTarget

Construye un objeto de clase `COleDropTarget`.

```
COleDropTarget();
```

### <a name="remarks"></a>Comentarios

Llame a [Register](#register) para asociar este objeto a una ventana.

##  <a name="ondragenter"></a>  COleDropTarget::OnDragEnter

Lo llama el marco de trabajo cuando se arrastra el cursor por primera vez a la ventana.

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la ventana que el cursor está entrando.

*pDataObject*<br/>
Apunta al objeto de datos que contiene los datos que se pueden quitar.

*dwKeyState*<br/>
Contiene el estado de las teclas modificadoras. Se trata de una combinación de cualquier número de lo siguiente: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.

*point*<br/>
Contiene la ubicación actual del cursor en coordenadas de cliente.

### <a name="return-value"></a>Valor devuelto

Efecto que se produciría si se intentó una operación de colocar en la ubicación especificada por *Point*. Puede ser uno o varios de los siguientes:

- DROPEFFECT_NONE no se permite la eliminación.

- DROPEFFECT_COPY se realizará una operación de copia.

- DROPEFFECT_MOVE se realizará una operación de movimiento.

- DROPEFFECT_LINK se establecería un vínculo entre los datos colocados y los datos originales.

- DROPEFFECT_SCROLL una operación de desplazamiento de arrastre está a punto de producirse o se está produciendo en el destino.

### <a name="remarks"></a>Comentarios

Invalide esta función para permitir que se produzcan operaciones de colocación en la ventana. La implementación predeterminada llama a [CView:: OnDragEnter](../../mfc/reference/cview-class.md#ondragenter), que simplemente devuelve DROPEFFECT_NONE de forma predeterminada.

Para obtener más información, vea [IDropTarget::D ragenter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) en el Windows SDK.

##  <a name="ondragleave"></a>  COleDropTarget::OnDragLeave

Lo llama el marco de trabajo cuando el cursor sale de la ventana mientras está en vigor una operación de arrastre.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la ventana que el cursor está saliendo.

### <a name="remarks"></a>Comentarios

Invalide esta función si desea un comportamiento especial cuando la operación de arrastrar sale de la ventana especificada. La implementación predeterminada de esta función llama a [CView:: OnDragLeave](../../mfc/reference/cview-class.md#ondragleave).

Para obtener más información, vea [IDropTarget::D ragleave](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragleave) en el Windows SDK.

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

*pWnd*<br/>
Apunta a la ventana en la que se encuentra el cursor.

*pDataObject*<br/>
Apunta al objeto de datos que contiene los datos que se van a quitar.

*dwKeyState*<br/>
Contiene el estado de las teclas modificadoras. Se trata de una combinación de cualquier número de lo siguiente: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.

*point*<br/>
Contiene la ubicación actual del cursor en coordenadas de cliente.

### <a name="return-value"></a>Valor devuelto

Efecto que se produciría si se intentó una operación de colocar en la ubicación especificada por *Point*. Puede ser uno o varios de los siguientes:

- DROPEFFECT_NONE no se permite la eliminación.

- DROPEFFECT_COPY se realizará una operación de copia.

- DROPEFFECT_MOVE se realizará una operación de movimiento.

- DROPEFFECT_LINK se establecería un vínculo entre los datos colocados y los datos originales.

- DROPEFFECT_SCROLL indica que una operación de desplazamiento de arrastre está a punto de producirse o se está produciendo en el destino.

### <a name="remarks"></a>Comentarios

Esta función se debe invalidar para permitir que se produzcan operaciones de eliminación en la ventana. La implementación predeterminada de esta función llama a [CView:: OnDragOver](../../mfc/reference/cview-class.md#ondragover), que devuelve DROPEFFECT_NONE de forma predeterminada. Dado que se llama a esta función con frecuencia durante una operación de arrastrar y colocar, se debe optimizar tanto como sea posible.

Para obtener más información, vea [IDropTarget::D ragover](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]

##  <a name="ondragscroll"></a>  COleDropTarget::OnDragScroll

Lo llama el marco de trabajo antes de llamar a [OnDragEnter](#ondragenter) o [OnDragOver](#ondragover) para determinar si el *punto* está en la región de desplazamiento.

```
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la ventana en la que el cursor está actualmente.

*dwKeyState*<br/>
Contiene el estado de las teclas modificadoras. Se trata de una combinación de cualquier número de lo siguiente: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.

*point*<br/>
Contiene la ubicación del cursor, en píxeles, con respecto a la pantalla.

### <a name="return-value"></a>Valor devuelto

Efecto que se produciría si se intentó una operación de colocar en la ubicación especificada por *Point*. Puede ser uno o varios de los siguientes:

- DROPEFFECT_NONE no se permite la eliminación.

- DROPEFFECT_COPY se realizará una operación de copia.

- DROPEFFECT_MOVE se realizará una operación de movimiento.

- DROPEFFECT_LINK se establecería un vínculo entre los datos colocados y los datos originales.

- DROPEFFECT_SCROLL indica que una operación de desplazamiento de arrastre está a punto de producirse o se está produciendo en el destino.

### <a name="remarks"></a>Comentarios

Invalide esta función cuando desee proporcionar un comportamiento especial para este evento. La implementación predeterminada de esta función llama a [CView:: OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll), que devuelve DROPEFFECT_NONE y desplaza la ventana cuando el cursor se arrastra en la región de desplazamiento predeterminada dentro del borde de la ventana.

##  <a name="ondrop"></a>  COleDropTarget::OnDrop

Lo llama el marco de trabajo cuando se va a producir una operación de colocar.

```
virtual BOOL OnDrop(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la ventana en la que el cursor está actualmente.

*pDataObject*<br/>
Apunta al objeto de datos que contiene los datos que se van a quitar.

*dropEffect*<br/>
El efecto que el usuario eligió para la operación de colocar. Puede ser uno o varios de los siguientes:

- DROPEFFECT_COPY se realizará una operación de copia.

- DROPEFFECT_MOVE se realizará una operación de movimiento.

- DROPEFFECT_LINK se establecería un vínculo entre los datos colocados y los datos originales.

*point*<br/>
Contiene la ubicación del cursor, en píxeles, con respecto a la pantalla.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la eliminación es correcta; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama primero a [OnDropEx](#ondropex). Si la `OnDropEx` función no controla la eliminación, el marco de trabajo llama a esta función miembro `OnDrop`,. Normalmente, la aplicación invalida [OnDropEx](../../mfc/reference/cview-class.md#ondropex) en la clase de vista para controlar el arrastre y colocación del botón secundario del mouse. Normalmente, la clase de vista [allocate](../../mfc/reference/cview-class.md#ondrop) se utiliza para controlar la función de arrastrar y colocar simple.

La implementación predeterminada de `COleDropTarget::OnDrop` llama a [CView:: Allocate](../../mfc/reference/cview-class.md#ondrop), que simplemente devuelve false de forma predeterminada.

Para obtener más información, vea [IDropTarget::D ROP](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) en el Windows SDK.

##  <a name="ondropex"></a>  COleDropTarget::OnDropEx

Lo llama el marco de trabajo cuando se va a producir una operación de colocar.

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la ventana en la que el cursor está actualmente.

*pDataObject*<br/>
Apunta al objeto de datos que contiene los datos que se van a quitar.

*dropDefault*<br/>
El efecto que el usuario eligió para la operación de colocar predeterminada en función del estado de la clave actual. Puede ser DROPEFFECT_NONE. Los efectos de colocación se describen en la sección Comentarios.

*dropList*<br/>
Una lista de los efectos de colocación que admite el origen de colocación. Los valores de efecto de colocación se pueden combinar mediante la **&#124;** operación OR bit a bit (). Los efectos de colocación se describen en la sección Comentarios.

*point*<br/>
Contiene la ubicación del cursor, en píxeles, con respecto a la pantalla.

### <a name="return-value"></a>Valor devuelto

Efecto de colocar que resultó del intento de colocar en la ubicación especificada por *Point*. Los efectos de colocación se describen en la sección Comentarios.

### <a name="remarks"></a>Comentarios

El marco llama primero a esta función. Si no controla la colocación, el marco de trabajo llama entonces a [Drop](#ondrop). Normalmente, invalidará [OnDropEx](../../mfc/reference/cview-class.md#ondropex) en la clase de vista para admitir arrastrar y colocar con el botón secundario del mouse. Normalmente, la clase de vista [allocate](../../mfc/reference/cview-class.md#ondrop) se utiliza para controlar el caso de compatibilidad con la función de arrastrar y colocar simple.

La implementación predeterminada de `COleDropTarget::OnDropEx` llama a [CView:: OnDropEx](../../mfc/reference/cview-class.md#ondropex). De forma predeterminada, [CView:: OnDropEx](../../mfc/reference/cview-class.md#ondropex) simplemente devuelve un valor ficticio para indicar que se debe llamar a la función miembro [Drop](#ondrop) .

Los efectos de colocación describen la acción asociada a una operación de colocar. Vea la siguiente lista de efectos de colocación:

- DROPEFFECT_NONE no se permite la eliminación.

- DROPEFFECT_COPY se realizará una operación de copia.

- DROPEFFECT_MOVE se realizará una operación de movimiento.

- DROPEFFECT_LINK se establecería un vínculo entre los datos colocados y los datos originales.

- DROPEFFECT_SCROLL indica que una operación de desplazamiento de arrastre está a punto de producirse o se está produciendo en el destino.

Para obtener más información, vea [IDropTarget::D ROP](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) en el Windows SDK.

##  <a name="register"></a>  COleDropTarget::Register

Llame a esta función para registrar la ventana con los archivos dll de OLE como destino de colocación válido.

```
BOOL Register(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la ventana que se va a registrar como destino de colocación.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el registro se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Se debe llamar a esta función para que se acepten las operaciones de eliminación.

Para obtener más información, vea [RegisterDragDrop](/windows/win32/api/ole2/nf-ole2-registerdragdrop) en el Windows SDK.

##  <a name="revoke"></a>  COleDropTarget::Revoke

Llame a esta función antes de destruir cualquier ventana que se haya registrado como destino de colocación a través de una llamada a [Register](#register) para quitarla de la lista de destinos de colocación.

```
virtual void Revoke();
```

### <a name="remarks"></a>Comentarios

Se llama a esta función automáticamente desde el controlador de [Destroy](../../mfc/reference/cwnd-class.md#ondestroy) para la ventana que se registró, por lo que normalmente no es necesario llamar a esta función explícitamente.

Para obtener más información, vea [RevokeDragDrop](/windows/win32/api/ole2/nf-ole2-revokedragdrop) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo OCLIENT de MFC](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDropSource (clase)](../../mfc/reference/coledropsource-class.md)
