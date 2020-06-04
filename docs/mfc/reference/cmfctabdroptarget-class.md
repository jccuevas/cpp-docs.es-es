---
title: CMFCTabDropTarget (Clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragEnter
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragLeave
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragOver
- AFXBASETABCTRL/CMFCTabDropTarget::OnDropEx
- AFXBASETABCTRL/CMFCTabDropTarget::Register
helpviewer_keywords:
- CMFCTabDropTarget [MFC], OnDragEnter
- CMFCTabDropTarget [MFC], OnDragLeave
- CMFCTabDropTarget [MFC], OnDragOver
- CMFCTabDropTarget [MFC], OnDropEx
- CMFCTabDropTarget [MFC], Register
ms.assetid: 9777b7b6-10da-4c4b-b1d1-7ea795b0f1cb
ms.openlocfilehash: 83432fdb90fe28214fb1faaf843556deb2f44750
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367355"
---
# <a name="cmfctabdroptarget-class"></a>CMFCTabDropTarget (Clase)

Proporciona el mecanismo de comunicación entre un control de ficha y las bibliotecas OLE.

## <a name="syntax"></a>Sintaxis

```
class CMFCTabDropTarget : public COleDropTarget
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Nombre|Descripción|
|`CMFCTabDropTarget::CMFCTabDropTarget`|Constructor predeterminado.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Nombre|Descripción|
|[CMFCTabDropTarget::OnDragEnter](#ondragenter)|Llamado por el marco de trabajo cuando el usuario arrastra un objeto a una ventana de ficha. (Reemplaza [COleDropTarget::OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).)|
|[CMFCTabDropTarget::OnDragLeave](#ondragleave)|Llamado por el marco de trabajo cuando el usuario arrastra un objeto fuera de la ventana de ficha que tiene el foco. (Reemplaza [COleDropTarget::OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave).)|
|[CMFCTabDropTarget::OnDragOver](#ondragover)|Llamado por el marco de trabajo cuando el usuario arrastra un objeto a la ventana de ficha que tiene el foco. (Reemplaza [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover).)|
|[CMFCTabDropTarget::OnDropEx](#ondropex)|Llamado por el marco de trabajo cuando el usuario suelta el botón del mouse al final de una operación de arrastre. (Reemplaza [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).)|
|[CMFCTabDropTarget::Register](#register)|Registra el control como uno que puede ser el destino de una operación de arrastrar y colocar OLE.|

### <a name="remarks"></a>Observaciones

Esta clase proporciona compatibilidad con arrastrar `CMFCBaseTabCtrl` y colocar a la clase. Si la aplicación inicializa las bibliotecas OLE mediante la `CMFCBaseTabCtrl` función [AfxOleInit,](ole-initialization.md#afxoleinit) los objetos se registran para las operaciones de arrastrar y colocar.

La `CMFCTabDropTarget` clase extiende su clase base haciendo que la pestaña que está debajo del cursor cuando se produce una operación de arrastre activa. Para obtener más información acerca de las operaciones de arrastrar y colocar, vea [arrastrar y colocar OLE](../../mfc/drag-and-drop-ole.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto `CMFCTabDropTarget` y usar su método `Register`.

[!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)

[CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxbasetabctrl.h

## <a name="cmfctabdroptargetondragenter"></a><a name="ondragenter"></a>CMFCTabDropTarget::OnDragEnter

Llamado por el marco de trabajo cuando el usuario arrastra un objeto a una ventana de ficha.

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pWnd*|[in] Sin utilizar.|
|*pDataObject*|[en] Puntero al objeto que arrastra el usuario.|
|*dwKeyState*|[en] Contiene el estado de las teclas modificadoras. Esta es una combinación de cualquier número de los siguientes: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.|
|*Punto*|[en] La ubicación del cursor en las coordenadas de cliente.|

### <a name="return-value"></a>Valor devuelto

El efecto que se produce si la colocación se produce en la ubicación especificada por *el punto*. Puede ser uno o más de los siguientes:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Observaciones

Este método devuelve DROPEFFECT_NONE si el marco de trabajo de la barra de herramientas no está en modo de personalización o el formato de datos del Portapapeles no está disponible. De lo contrario, devuelve `CMFCBaseTabCtrl::OnDragEnter` el resultado de llamar con los parámetros proporcionados.

Para obtener más información sobre el modo de personalización, vea [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Para obtener más información acerca de los formatos de datos del Portapapeles, vea [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetondragleave"></a><a name="ondragleave"></a>CMFCTabDropTarget::OnDragLeave

Llamado por el marco de trabajo cuando el usuario arrastra un objeto fuera de la ventana de ficha que tiene el foco.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pWnd*|[in] Sin utilizar.|

### <a name="remarks"></a>Observaciones

Este método `CMFCBaseTabCtrl::OnDragLeave` llama al método para realizar la operación de arrastre.

## <a name="cmfctabdroptargetondragover"></a><a name="ondragover"></a>CMFCTabDropTarget::OnDragOver

Llamado por el marco de trabajo cuando el usuario arrastra un objeto a la ventana de ficha que tiene el foco.

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pWnd*|[in] Sin utilizar.|
|*pDataObject*|[en] Puntero al objeto que arrastra el usuario.|
|*dwKeyState*|[en] Contiene el estado de las teclas modificadoras. Esta es una combinación de cualquier número de los siguientes: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.|
|*Punto*|[en] La ubicación del puntero del mouse en las coordenadas de cliente.|

### <a name="return-value"></a>Valor devuelto

El efecto que se produce si la colocación se produce en la ubicación especificada por *el punto*. Puede ser uno o más de los siguientes:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Observaciones

Este método hace que la pestaña que está debajo del cursor cuando se produce una operación de arrastre activa. Devuelve DROPEFFECT_NONE si el marco de la barra de herramientas no está en modo de personalización o el formato de datos del Portapapeles no está disponible. De lo contrario, devuelve `CMFCBaseTabCtrl::OnDragOver` el resultado de llamar con los parámetros proporcionados.

Para obtener más información sobre el modo de personalización, vea [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Para obtener más información acerca de los formatos de datos del Portapapeles, vea [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetondropex"></a><a name="ondropex"></a>CMFCTabDropTarget::OnDropEx

Llamado por el marco de trabajo cuando el usuario suelta el botón del mouse al final de una operación de arrastre.

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pWnd*|[in] Sin utilizar.|
|*pDataObject*|[en] Puntero al objeto que arrastra el usuario.|
|*dropEffect*|[en] La operación de colocación predeterminada.|
|*dropList*|[in] Sin utilizar.|
|*Punto*|[en] La ubicación del puntero del mouse en las coordenadas de cliente.|

### <a name="return-value"></a>Valor devuelto

El efecto de caída resultante. Puede ser uno o más de los siguientes:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Observaciones

Este método `CMFCBaseTabCtrl::OnDrop` llama si el marco de la barra de herramientas está en modo de personalización y el formato de datos del Portapapeles está disponible. Si la `CMFCBaseTabCtrl::OnDrop` llamada a devuelve un valor distinto de cero, este método devuelve el efecto de colocación predeterminado especificado por *dropEffect*. De lo contrario, este método devuelve DROPEFFECT_NONE. Para obtener más información acerca de los efectos de colocación, vea [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).

Para obtener más información sobre el modo de personalización, vea [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Para obtener más información acerca de los formatos de datos del Portapapeles, vea [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetregister"></a><a name="register"></a>CMFCTabDropTarget::Register

Registra el control como uno que puede ser el destino de una operación de arrastrar y colocar OLE.

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pOwner*|[en] El control de ficha para registrarse como destino de colocación.|

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el registro se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Este método llama a [COleDropTarget::Register](../../mfc/reference/coledroptarget-class.md#register) para registrar el control para las operaciones de arrastrar y colocar.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Funciones OLE de arrastrar y colocar](../../mfc/drag-and-drop-ole.md)
