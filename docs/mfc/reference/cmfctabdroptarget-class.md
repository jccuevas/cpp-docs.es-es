---
title: CMFCTabDropTarget (clase)
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
ms.openlocfilehash: 8b24d7679edfaab4d4eeb6d59770f30cd4253580
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252989"
---
# <a name="cmfctabdroptarget-class"></a>CMFCTabDropTarget (clase)

Proporciona el mecanismo de comunicación entre un control de pestaña y las bibliotecas OLE.

## <a name="syntax"></a>Sintaxis

```
class CMFCTabDropTarget : public COleDropTarget
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Name|Descripción|
|`CMFCTabDropTarget::CMFCTabDropTarget`|Constructor predeterminado.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Name|Descripción|
|[CMFCTabDropTarget::OnDragEnter](#ondragenter)|Lo llama el marco cuando el usuario arrastra un objeto en una ventana de ficha. (Invalida [COleDropTarget::OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).)|
|[CMFCTabDropTarget::OnDragLeave](#ondragleave)|Lo llama el marco cuando el usuario arrastra un objeto fuera de la ventana de la pestaña que tiene el foco. (Invalida [COleDropTarget::OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave).)|
|[CMFCTabDropTarget::OnDragOver](#ondragover)|Lo llama el marco cuando el usuario arrastra un objeto a la pestaña de ventana que tiene el foco. (Invalida [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover).)|
|[CMFCTabDropTarget::OnDropEx](#ondropex)|Lo llama el marco cuando el usuario suelta el botón del mouse al final de una operación de arrastre. (Invalida [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).)|
|[CMFCTabDropTarget::Register](#register)|Registra el control como un tipo que puede ser el destino de una operación de arrastrar y colocar OLE.|

### <a name="remarks"></a>Comentarios

Esta clase proporciona compatibilidad con arrastrar y colocar para el `CMFCBaseTabCtrl` clase. Si la aplicación inicializa las bibliotecas OLE mediante el [AfxOleInit](ole-initialization.md#afxoleinit) función, `CMFCBaseTabCtrl` objetos se registran para operaciones de arrastrar y colocar.

La `CMFCTabDropTarget` clase extiende su clase base mediante la realización de la pestaña que está bajo el cursor cuando se produce activa una operación de arrastre. Para obtener más información acerca de las operaciones de arrastrar y colocar, vea [arrastrar y colocar (OLE)](../../mfc/drag-and-drop-ole.md).

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

##  <a name="ondragenter"></a>  CMFCTabDropTarget::OnDragEnter

Lo llama el marco cuando el usuario arrastra un objeto en una ventana de ficha.

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
|*pWnd*|[in] Sin usar.|
|*pDataObject*|[in] Un puntero al objeto que el usuario arrastra.|
|*dwKeyState*|[in] Contiene el estado de las teclas modificadoras. Se trata de una combinación de cualquier número de las siguientes acciones: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.|
|*point*|[in] La ubicación del cursor en coordenadas de cliente.|

### <a name="return-value"></a>Valor devuelto

El efecto que se produce si se produce la entrega en la ubicación especificada por *punto*. Puede ser uno o varios de los siguientes:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Comentarios

Este método devuelve DROPEFFECT_NONE si el marco de trabajo de la barra de herramientas no está en modo de personalización o el formato de datos del Portapapeles no está disponible. De lo contrario, devuelve el resultado de llamar a `CMFCBaseTabCtrl::OnDragEnter` con los parámetros proporcionados.

Para obtener más información acerca del modo de personalización, consulte [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Para obtener más información acerca de los formatos de datos del Portapapeles, consulte [COleDataObject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

##  <a name="ondragleave"></a>  CMFCTabDropTarget::OnDragLeave

Lo llama el marco cuando el usuario arrastra un objeto fuera de la ventana de la pestaña que tiene el foco.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pWnd*|[in] Sin usar.|

### <a name="remarks"></a>Comentarios

Este método llama a la `CMFCBaseTabCtrl::OnDragLeave` método para realizar la operación de arrastre.

##  <a name="ondragover"></a>  CMFCTabDropTarget::OnDragOver

Lo llama el marco cuando el usuario arrastra un objeto a la pestaña de ventana que tiene el foco.

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
|*pWnd*|[in] Sin usar.|
|*pDataObject*|[in] Un puntero al objeto que el usuario arrastra.|
|*dwKeyState*|[in] Contiene el estado de las teclas modificadoras. Se trata de una combinación de cualquier número de las siguientes acciones: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.|
|*point*|[in] La ubicación del puntero del mouse en coordenadas de cliente.|

### <a name="return-value"></a>Valor devuelto

El efecto que se produce si se produce la entrega en la ubicación especificada por *punto*. Puede ser uno o varios de los siguientes:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Comentarios

Este método realiza la pestaña que está bajo el cursor cuando se produce activa una operación de arrastre. Devuelve DROPEFFECT_NONE si el marco de trabajo de la barra de herramientas no está en modo de personalización o el formato de datos del Portapapeles no está disponible. De lo contrario, devuelve el resultado de llamar a `CMFCBaseTabCtrl::OnDragOver` con los parámetros proporcionados.

Para obtener más información acerca del modo de personalización, consulte [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Para obtener más información acerca de los formatos de datos del Portapapeles, consulte [COleDataObject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

##  <a name="ondropex"></a>  CMFCTabDropTarget::OnDropEx

Lo llama el marco cuando el usuario suelta el botón del mouse al final de una operación de arrastre.

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
|*pWnd*|[in] Sin usar.|
|*pDataObject*|[in] Un puntero al objeto que el usuario arrastra.|
|*dropEffect*|[in] La operación de colocar de forma predeterminada.|
|*dropList*|[in] Sin usar.|
|*point*|[in] La ubicación del puntero del mouse en coordenadas de cliente.|

### <a name="return-value"></a>Valor devuelto

El efecto resultante. Puede ser uno o varios de los siguientes:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Comentarios

Este método llama a `CMFCBaseTabCtrl::OnDrop` si el marco de trabajo de la barra de herramientas está en modo de personalización y el formato de datos está disponible. Si la llamada a `CMFCBaseTabCtrl::OnDrop` devuelve un valor distinto de cero, este método devuelve el efecto de colocación predeterminado especificado por *EfectoColocar*. En caso contrario, este método devuelve DROPEFFECT_NONE. Para obtener más información acerca de los efectos de colocar, consulte [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).

Para obtener más información acerca del modo de personalización, consulte [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Para obtener más información acerca de los formatos de datos del Portapapeles, consulte [COleDataObject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

##  <a name="register"></a>  CMFCTabDropTarget::Register

Registra el control como un tipo que puede ser el destino de una operación de arrastrar y colocar OLE.

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pOwner*|[in] Control de ficha que se va a registrar como un destino de colocación.|

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el registro se realiza correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método llama a [COleDropTarget::Register](../../mfc/reference/coledroptarget-class.md#register) para registrar el control para operaciones de arrastrar y colocar.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Arrastrar y colocar (OLE)](../../mfc/drag-and-drop-ole.md)
