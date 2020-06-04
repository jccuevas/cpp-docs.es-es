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
ms.openlocfilehash: 01eb277da029d06ee44d8e048cf3244f4371a9ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374993"
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
|[COleDropTarget::OnDragEnter](#ondragenter)|Se llama cuando el cursor entra por primera vez en la ventana.|
|[COleDropTarget::OnDragLeave](#ondragleave)|Se llama cuando se arrastra el cursor fuera de la ventana.|
|[COleDropTarget::OnDragOver](#ondragover)|Se llama repetidamente cuando se arrastra el cursor sobre la ventana.|
|[COleDropTarget::OnDragScroll](#ondragscroll)|Se llama para determinar si el cursor se arrastra a la región de desplazamiento de la ventana.|
|[COleDropTarget::OnDrop](#ondrop)|Se llama cuando los datos se colocan en la ventana, controlador predeterminado.|
|[COleDropTarget::OnDropEx](#ondropex)|Se llama cuando los datos se colocan en la ventana, controlador inicial.|
|[COleDropTarget::Register](#register)|Registra la ventana como un destino de colocación válido.|
|[COleDropTarget::Revocar](#revoke)|Hace que la ventana deje de ser un destino de colocación válido.|

## <a name="remarks"></a>Observaciones

La creación de un objeto de esta clase permite que una ventana acepte datos a través del mecanismo OLE de arrastrar y colocar.

Para obtener una ventana para aceptar comandos de `COleDropTarget` colocación, primero debe crear un objeto `CWnd` de la clase y, a continuación, llamar a la [función Register](#register) con un puntero al objeto deseado como único parámetro.

Para obtener más información sobre las operaciones de arrastrar y colocar mediante OLE, vea el artículo [arrastrar y colocar OLE](../../mfc/drag-and-drop-ole.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropTarget`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

## <a name="coledroptargetcoledroptarget"></a><a name="coledroptarget"></a>COleDropTarget::COleDropTarget

Construye un objeto `COleDropTarget`de clase .

```
COleDropTarget();
```

### <a name="remarks"></a>Observaciones

Llame a [Register](#register) para asociar este objeto a una ventana.

## <a name="coledroptargetondragenter"></a><a name="ondragenter"></a>COleDropTarget::OnDragEnter

Llamado por el marco de trabajo cuando el cursor se arrastra por primera vez a la ventana.

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la ventana que el cursor está introduciendo.

*pDataObject*<br/>
Apunta al objeto de datos que contiene los datos que se pueden quitar.

*dwKeyState*<br/>
Contiene el estado de las teclas modificadoras. Esta es una combinación de cualquier número de los siguientes: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.

*Punto*<br/>
Contiene la ubicación actual del cursor en las coordenadas de cliente.

### <a name="return-value"></a>Valor devuelto

El efecto que se produciría si se intentara una colocación en la ubicación especificada por *el punto*. Puede ser uno o más de los siguientes:

- DROPEFFECT_NONE No se permitiría una caída.

- DROPEFFECT_COPY Se realizaría una operación de copia.

- DROPEFFECT_MOVE Se realizaría una operación de movimiento.

- DROPEFFECT_LINK Se establecería un vínculo de los datos eliminados a los datos originales.

- DROPEFFECT_SCROLL Una operación de desplazamiento de arrastre está a punto de producirse o se está produciendo en el destino.

### <a name="remarks"></a>Observaciones

Reemplace esta función para permitir que se produzcan operaciones de colocación en la ventana. La implementación predeterminada llama a [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter), que simplemente devuelve DROPEFFECT_NONE de forma predeterminada.

Para obtener más información, vea [IDropTarget::DragEnter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) en el Windows SDK.

## <a name="coledroptargetondragleave"></a><a name="ondragleave"></a>COleDropTarget::OnDragLeave

Llamado por el marco de trabajo cuando el cursor sale de la ventana mientras una operación de arrastre está en vigor.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la ventana que el cursor está dejando.

### <a name="remarks"></a>Observaciones

Reemplace esta función si desea un comportamiento especial cuando la operación de arrastre salga de la ventana especificada. La implementación predeterminada de esta función llama a [CView::OnDragLeave](../../mfc/reference/cview-class.md#ondragleave).

Para obtener más información, vea [IDropTarget::DragLeave](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragleave) en el Windows SDK.

## <a name="coledroptargetondragover"></a><a name="ondragover"></a>COleDropTarget::OnDragOver

Llamado por el marco de trabajo cuando el cursor se arrastra sobre la ventana.

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la ventana sobre la que se ha terminado el cursor.

*pDataObject*<br/>
Apunta al objeto de datos que contiene los datos que se van a quitar.

*dwKeyState*<br/>
Contiene el estado de las teclas modificadoras. Esta es una combinación de cualquier número de los siguientes: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.

*Punto*<br/>
Contiene la ubicación actual del cursor en las coordenadas de cliente.

### <a name="return-value"></a>Valor devuelto

El efecto que se produciría si se intentara una colocación en la ubicación especificada por *el punto*. Puede ser uno o más de los siguientes:

- DROPEFFECT_NONE No se permitiría una caída.

- DROPEFFECT_COPY Se realizaría una operación de copia.

- DROPEFFECT_MOVE Se realizaría una operación de movimiento.

- DROPEFFECT_LINK Se establecería un vínculo de los datos eliminados a los datos originales.

- DROPEFFECT_SCROLL Indica que una operación de desplazamiento de arrastre está a punto de producirse o se está produciendo en el destino.

### <a name="remarks"></a>Observaciones

Esta función debe reemplazarse para permitir que se produzcan operaciones de colocación en la ventana. La implementación predeterminada de esta función llama a [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover), que devuelve DROPEFFECT_NONE de forma predeterminada. Dado que esta función se llama con frecuencia durante una operación de arrastrar y colocar, debe optimizarse tanto como sea posible.

Para obtener más información, vea [IDropTarget::DragOver](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]

## <a name="coledroptargetondragscroll"></a><a name="ondragscroll"></a>COleDropTarget::OnDragScroll

Llamado por el marco de trabajo antes de llamar a [OnDragEnter](#ondragenter) o [OnDragOver](#ondragover) para determinar si *el punto* está en la región de desplazamiento.

```
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la ventana sobre la que se encuentra el cursor.

*dwKeyState*<br/>
Contiene el estado de las teclas modificadoras. Esta es una combinación de cualquier número de los siguientes: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.

*Punto*<br/>
Contiene la ubicación del cursor, en píxeles, en relación con la pantalla.

### <a name="return-value"></a>Valor devuelto

El efecto que se produciría si se intentara una colocación en la ubicación especificada por *el punto*. Puede ser uno o más de los siguientes:

- DROPEFFECT_NONE No se permitiría una caída.

- DROPEFFECT_COPY Se realizaría una operación de copia.

- DROPEFFECT_MOVE Se realizaría una operación de movimiento.

- DROPEFFECT_LINK Se establecería un vínculo de los datos eliminados a los datos originales.

- DROPEFFECT_SCROLL Indica que una operación de desplazamiento de arrastre está a punto de producirse o se está produciendo en el destino.

### <a name="remarks"></a>Observaciones

Invalide esta función cuando desee proporcionar un comportamiento especial para este evento. La implementación predeterminada de esta función llama a [CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll), que devuelve DROPEFFECT_NONE y desplaza la ventana cuando se arrastra el cursor a la región de desplazamiento predeterminada dentro del borde de la ventana.

## <a name="coledroptargetondrop"></a><a name="ondrop"></a>COleDropTarget::OnDrop

Llamado por el marco de trabajo cuando se va a producir una operación de colocación.

```
virtual BOOL OnDrop(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la ventana sobre la que se encuentra el cursor.

*pDataObject*<br/>
Apunta al objeto de datos que contiene los datos que se van a quitar.

*dropEffect*<br/>
El efecto que el usuario eligió para la operación de colocación. Puede ser uno o más de los siguientes:

- DROPEFFECT_COPY Se realizaría una operación de copia.

- DROPEFFECT_MOVE Se realizaría una operación de movimiento.

- DROPEFFECT_LINK Se establecería un vínculo de los datos eliminados a los datos originales.

*Punto*<br/>
Contiene la ubicación del cursor, en píxeles, en relación con la pantalla.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la caída es correcta; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama primero a [OnDropEx](#ondropex). Si `OnDropEx` la función no controla la colocación, `OnDrop`el marco de trabajo, a continuación, llama a esta función miembro, . Normalmente, la aplicación reemplaza [OnDropEx](../../mfc/reference/cview-class.md#ondropex) en la clase de vista para controlar el botón derecho del mouse arrastrar y colocar. Normalmente, la clase de vista [OnDrop](../../mfc/reference/cview-class.md#ondrop) se utiliza para controlar arrastrar y colocar simple.

La implementación `COleDropTarget::OnDrop` predeterminada de llamadas [CView::OnDrop](../../mfc/reference/cview-class.md#ondrop), que simplemente devuelve FALSE de forma predeterminada.

Para obtener más información, vea [IDropTarget::Drop](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) en el Windows SDK.

## <a name="coledroptargetondropex"></a><a name="ondropex"></a>COleDropTarget::OnDropEx

Llamado por el marco de trabajo cuando se va a producir una operación de colocación.

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
Apunta a la ventana sobre la que se encuentra el cursor.

*pDataObject*<br/>
Apunta al objeto de datos que contiene los datos que se van a quitar.

*dropDefault*<br/>
El efecto que el usuario eligió para la operación de colocación predeterminada en función del estado de clave actual. Se puede DROPEFFECT_NONE. Los efectos de caída se describen en la sección Comentarios.

*dropList*<br/>
Una lista de los efectos de colocación que admite el origen de colocación. Los valores de efecto de colocación se pueden combinar mediante la operación OR (**&#124;**) bit a bit. Los efectos de caída se describen en la sección Comentarios.

*Punto*<br/>
Contiene la ubicación del cursor, en píxeles, en relación con la pantalla.

### <a name="return-value"></a>Valor devuelto

El efecto de colocación resultante del intento de colocación en la ubicación especificada por *el punto*. Los efectos de caída se describen en la sección Comentarios.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama primero a esta función. Si no controla la colocación, el marco de trabajo, a continuación, llama a [OnDrop](#ondrop). Normalmente, invalidará [OnDropEx](../../mfc/reference/cview-class.md#ondropex) en la clase de vista para admitir arrastrar y colocar con el botón derecho del mouse. Normalmente, la clase de vista [OnDrop](../../mfc/reference/cview-class.md#ondrop) se utiliza para controlar el caso de soporte para arrastrar y colocar simple.

La implementación `COleDropTarget::OnDropEx` predeterminada de llamadas [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex). De forma predeterminada, [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex) simplemente devuelve un valor ficticio para indicar el [OnDrop](#ondrop) debe llamarse a la función miembro.

Los efectos de colocación describen la acción asociada a una operación de colocación. Consulte la siguiente lista de efectos de caída:

- DROPEFFECT_NONE No se permitiría una caída.

- DROPEFFECT_COPY Se realizaría una operación de copia.

- DROPEFFECT_MOVE Se realizaría una operación de movimiento.

- DROPEFFECT_LINK Se establecería un vínculo de los datos eliminados a los datos originales.

- DROPEFFECT_SCROLL Indica que una operación de desplazamiento de arrastre está a punto de producirse o se está produciendo en el destino.

Para obtener más información, vea [IDropTarget::Drop](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) en el Windows SDK.

## <a name="coledroptargetregister"></a><a name="register"></a>COleDropTarget::Register

Llame a esta función para registrar la ventana con los archivos DLL OLE como un destino de colocación válido.

```
BOOL Register(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la ventana que se va a registrar como destino de colocación.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el registro se realiza correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función debe llamarse para que se acepten las operaciones de colocación.

Para obtener más información, consulte [RegisterDragDrop](/windows/win32/api/ole2/nf-ole2-registerdragdrop) en el Windows SDK.

## <a name="coledroptargetrevoke"></a><a name="revoke"></a>COleDropTarget::Revocar

Llame a esta función antes de destruir cualquier ventana que se haya registrado como destino de colocación a través de una llamada a [Register](#register) para quitarla de la lista de destinos de colocación.

```
virtual void Revoke();
```

### <a name="remarks"></a>Observaciones

Esta función se llama automáticamente desde el [OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy) controlador para la ventana que se registró, por lo que normalmente no es necesario llamar a esta función explícitamente.

Para obtener más información, consulte [RevokeDragDrop](/windows/win32/api/ole2/nf-ole2-revokedragdrop) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleDropSource (clase)](../../mfc/reference/coledropsource-class.md)
