---
title: Clase CMFCTabDropTarget
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
ms.openlocfilehash: d0090386b1ebb4d89b9a7613a0b2a28529decbe5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127436"
---
# <a name="cmfctabdroptarget-class"></a>Clase CMFCTabDropTarget

Proporciona el mecanismo de comunicación entre un control de ficha y las bibliotecas OLE.

## <a name="syntax"></a>Sintaxis

```
class CMFCTabDropTarget : public COleDropTarget
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Nombre|Descripción|
|`CMFCTabDropTarget::CMFCTabDropTarget`|Constructor predeterminado.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Nombre|Descripción|
|[CMFCTabDropTarget:: OnDragEnter](#ondragenter)|Lo llama el marco de trabajo cuando el usuario arrastra un objeto a una ventana de tabulación. (Invalida [COleDropTarget:: OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter)).|
|[CMFCTabDropTarget:: OnDragLeave](#ondragleave)|Lo llama el marco de trabajo cuando el usuario arrastra un objeto fuera de la ventana de pestaña que tiene el foco. (Invalida [COleDropTarget:: OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave)).|
|[CMFCTabDropTarget:: OnDragOver](#ondragover)|Lo llama el marco de trabajo cuando el usuario arrastra un objeto a la ventana de pestaña que tiene el foco. (Invalida [COleDropTarget:: OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover)).|
|[CMFCTabDropTarget::OnDropEx](#ondropex)|Lo llama el marco de trabajo cuando el usuario suelta el botón del mouse al final de una operación de arrastre. (Invalida [COleDropTarget:: OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)).|
|[CMFCTabDropTarget:: Register](#register)|Registra el control como un que puede ser el destino de una operación OLE de arrastrar y colocar.|

### <a name="remarks"></a>Observaciones

Esta clase proporciona compatibilidad de arrastrar y colocar con la clase `CMFCBaseTabCtrl`. Si la aplicación inicializa las bibliotecas OLE mediante la función [AfxOleInit](ole-initialization.md#afxoleinit) , `CMFCBaseTabCtrl` objetos se registran en las operaciones de arrastrar y colocar.

La clase `CMFCTabDropTarget` extiende su clase base mediante la tabulación que está bajo el cursor cuando se produce una operación de arrastre activa. Para obtener más información sobre las operaciones de arrastrar y colocar, vea [arrastrar y colocar de OLE](../../mfc/drag-and-drop-ole.md).

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

##  <a name="ondragenter"></a>CMFCTabDropTarget:: OnDragEnter

Lo llama el marco de trabajo cuando el usuario arrastra un objeto a una ventana de tabulación.

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
|*pDataObject*|de Puntero al objeto que el usuario arrastra.|
|*dwKeyState*|de Contiene el estado de las teclas modificadoras. Se trata de una combinación de cualquier número de los siguientes: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.|
|*Elija*|de Ubicación del cursor en coordenadas de cliente.|

### <a name="return-value"></a>Valor devuelto

Efecto que se produce si la colocación se produce en la ubicación especificada por *Point*. Puede ser uno o varios de los siguientes:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Observaciones

Este método devuelve DROPEFFECT_NONE si el marco de la barra de herramientas no está en modo de personalización o el formato de datos del portapapeles no está disponible. De lo contrario, devuelve el resultado de llamar a `CMFCBaseTabCtrl::OnDragEnter` con los parámetros proporcionados.

Para obtener más información sobre el modo de personalización, vea [CMFCToolBar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Para obtener más información sobre los formatos de datos del portapapeles, vea [COleDataObject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

##  <a name="ondragleave"></a>CMFCTabDropTarget:: OnDragLeave

Lo llama el marco de trabajo cuando el usuario arrastra un objeto fuera de la ventana de pestaña que tiene el foco.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pWnd*|[in] Sin utilizar.|

### <a name="remarks"></a>Observaciones

Este método llama al método `CMFCBaseTabCtrl::OnDragLeave` para realizar la operación de arrastre.

##  <a name="ondragover"></a>CMFCTabDropTarget:: OnDragOver

Lo llama el marco de trabajo cuando el usuario arrastra un objeto a la ventana de pestaña que tiene el foco.

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
|*pDataObject*|de Puntero al objeto que el usuario arrastra.|
|*dwKeyState*|de Contiene el estado de las teclas modificadoras. Se trata de una combinación de cualquier número de los siguientes: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.|
|*Elija*|de Ubicación del puntero del mouse en coordenadas de cliente.|

### <a name="return-value"></a>Valor devuelto

Efecto que se produce si la colocación se produce en la ubicación especificada por *Point*. Puede ser uno o varios de los siguientes:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Observaciones

Este método hace que la pestaña que se encuentra debajo del cursor cuando se produce una operación de arrastre activa. Devuelve DROPEFFECT_NONE si el marco de la barra de herramientas no está en modo de personalización o el formato de datos del portapapeles no está disponible. De lo contrario, devuelve el resultado de llamar a `CMFCBaseTabCtrl::OnDragOver` con los parámetros proporcionados.

Para obtener más información sobre el modo de personalización, vea [CMFCToolBar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Para obtener más información sobre los formatos de datos del portapapeles, vea [COleDataObject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

##  <a name="ondropex"></a>CMFCTabDropTarget::OnDropEx

Lo llama el marco de trabajo cuando el usuario suelta el botón del mouse al final de una operación de arrastre.

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
|*pDataObject*|de Puntero al objeto que el usuario arrastra.|
|*dropEffect*|de La operación Drop predeterminada.|
|*Plegable*|[in] Sin utilizar.|
|*Elija*|de Ubicación del puntero del mouse en coordenadas de cliente.|

### <a name="return-value"></a>Valor devuelto

Efecto de eliminación resultante. Puede ser uno o varios de los siguientes:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Observaciones

Este método llama `CMFCBaseTabCtrl::OnDrop` si el marco de la barra de herramientas está en modo de personalización y el formato de datos del Portapapeles está disponible. Si la llamada a `CMFCBaseTabCtrl::OnDrop` devuelve un valor distinto de cero, este método devuelve el efecto de colocación predeterminado especificado por *dropEffect*. De lo contrario, este método devuelve DROPEFFECT_NONE. Para obtener más información sobre los efectos de colocación, vea [COleDropTarget:: OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).

Para obtener más información sobre el modo de personalización, vea [CMFCToolBar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Para obtener más información sobre los formatos de datos del portapapeles, vea [COleDataObject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

##  <a name="register"></a>CMFCTabDropTarget:: Register

Registra el control como un que puede ser el destino de una operación OLE de arrastrar y colocar.

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pOwner*|de Control de ficha que se va a registrar como destino de colocación.|

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el registro se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Este método llama a [COleDropTarget:: Register](../../mfc/reference/coledroptarget-class.md#register) para registrar el control para las operaciones de arrastrar y colocar.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Arrastrar y colocar de OLE](../../mfc/drag-and-drop-ole.md)
