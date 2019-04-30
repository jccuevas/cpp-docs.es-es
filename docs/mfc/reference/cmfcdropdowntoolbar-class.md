---
title: CMFCDropDownToolBar (clase)
ms.date: 11/19/2018
f1_keywords:
- CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::AllowShowOnPaneMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadBitmap
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnLButtonUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnMouseMove
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnSendCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnUpdateCmdUI
helpviewer_keywords:
- CMFCDropDownToolBar [MFC], AllowShowOnPaneMenu
- CMFCDropDownToolBar [MFC], LoadBitmap
- CMFCDropDownToolBar [MFC], LoadToolBar
- CMFCDropDownToolBar [MFC], OnLButtonUp
- CMFCDropDownToolBar [MFC], OnMouseMove
- CMFCDropDownToolBar [MFC], OnSendCommand
- CMFCDropDownToolBar [MFC], OnUpdateCmdUI
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
ms.openlocfilehash: f2c4135d2a27928dbde4299fa1f8eda42237d893
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62238070"
---
# <a name="cmfcdropdowntoolbar-class"></a>CMFCDropDownToolBar (clase)

Una barra de herramientas que aparece cuando el usuario presiona y mantiene presionado un botón de la barra de herramientas de nivel superior.

   Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.
## <a name="syntax"></a>Sintaxis

```
class CMFCDropDownToolBar : public CMFCToolBar
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Invalida `CPane::AllowShowOnPaneMenu`).|
|[CMFCDropDownToolBar::LoadBitmap](#loadbitmap)|(Invalida [CMFCToolBar::LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap).)|
|[CMFCDropDownToolBar::LoadToolBar](#loadtoolbar)|(Invalida [CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar).)|
|[CMFCDropDownToolBar::OnLButtonUp](#onlbuttonup)||
|[CMFCDropDownToolBar::OnMouseMove](#onmousemove)||
|[CMFCDropDownToolBar::OnSendCommand](#onsendcommand)|(Invalida `CMFCToolBar::OnSendCommand`).|
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(Invalida [CMFCToolBar::OnUpdateCmdUI](cmfctoolbar-class.md).|

### <a name="remarks"></a>Comentarios

Un `CMFCDropDownToolBar` objeto combina la apariencia visual de una barra de herramientas con el comportamiento de un menú emergente. Cuando un usuario presiona y mantiene un botón de barra de herramientas desplegable (consulte [CMFCDropDownToolbarButton (clase)](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)), aparece una barra de herramientas de la lista desplegable y el usuario puede seleccionar un botón de la barra de herramientas desplegable desplazándose hasta él y soltando el mouse botón. Después de que el usuario selecciona un botón en la barra de herramientas de la lista desplegable, ese botón se muestra como botón actual en la barra de herramientas de nivel superior.

No se pueden personalizar ni acoplada una barra de herramientas de la lista desplegable, y no tiene un estado desplazable.

La siguiente ilustración muestra un `CMFCDropDownToolBar` objeto:

![Ejemplo de CMFCDropDownToolbar](../../mfc/reference/media/cmfcdropdown.png "ejemplo de CMFCDropDownToolbar")

Crear un `CMFCDropDownToolBar` objeto del mismo modo, crear una barra de herramientas normal (vea [CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md)).

Para insertar la barra de herramientas desplegable en una barra de herramientas primario:

1. Reserve un id. de recurso ficticio para el botón en el recurso primario de la barra de herramientas.

2. Crear un `CMFCDropDownToolBarButton` objeto que contiene la barra de herramientas desplegable (para obtener más información, consulte [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton)).

3. Reemplazar el botón ficticio con la `CMFCDropDownToolBarButton` objeto mediante el uso de [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Para obtener más información acerca de los botones de barra de herramientas, consulte [Tutorial: Insertar controles en barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md). Para obtener un ejemplo de una barra de herramientas de la lista desplegable, vea el proyecto de ejemplo VisualStudioDemo.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar el `Create` método en el `CMFCDropDownToolBar` clase. Este fragmento de código forma parte de la [ejemplo de demostración de Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdropdowntoolbar.h

##  <a name="allowshowonpanemenu"></a>  CMFCDropDownToolBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="loadbitmap"></a>  CMFCDropDownToolBar::LoadBitmap

Carga las imágenes de la barra de herramientas desde los recursos de la aplicación.

```
virtual BOOL LoadBitmap(
    UINT uiResID,
    UINT uiColdResID=0,
    UINT uiMenuResID=0,
    BOOL bLocked=FALSE,
    UINT uiDisabledResID=0,
    UINT uiMenuDisabledResID=0);
```

### <a name="parameters"></a>Parámetros

*uiResID*<br/>
[in] El identificador de recurso del mapa de bits que hace referencia a las imágenes de barra de herramientas activa.

*uiColdResID*<br/>
[in] El identificador de recurso del mapa de bits que hace referencia a las imágenes de barra de herramientas inactiva.

*uiMenuResID*<br/>
[in] El identificador de recurso del mapa de bits que hace referencia a las imágenes de menú normal.

*bLocked*<br/>
[in] TRUE para bloquear la barra de herramientas; en caso contrario, FALSE.

*uiDisabledResID*<br/>
[in] El identificador de recurso del mapa de bits que hace referencia a las imágenes de barra de herramientas deshabilitada.

*uiMenuDisabledResID*<br/>
[in] El identificador de recurso del mapa de bits que hace referencia a las imágenes de menú deshabilitado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método es correcto; de lo contrario, 0.

### <a name="remarks"></a>Comentarios

El método [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) llama a este método para cargar las imágenes asociadas a la barra de herramientas. Invalide este método para realizar la carga personalizada de recursos de imagen.

Llame al método `LoadBitmapEx` para cargar imágenes adicionales después de crear la barra de herramientas.

##  <a name="loadtoolbar"></a>  CMFCDropDownToolBar::LoadToolBar

```
virtual BOOL LoadToolBar(
    UINT uiResID,
    UINT uiColdResID = 0,
    UINT uiMenuResID = 0,
    BOOL = FALSE,
    UINT uiDisabledResID = 0,
    UINT uiMenuDisabledResID = 0,
    UINT uiHotResID = 0);
```

### <a name="parameters"></a>Parámetros

[in] *uiResID*<br/>

[in] *uiColdResID*<br/>

[in] *uiMenuResID*<br/>

[in] *BOOL*<br/>

[in] *uiDisabledResID*<br/>

[in] *uiMenuDisabledResID*<br/>

[in] *uiHotResID*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="onlbuttonup"></a>  CMFCDropDownToolBar::OnLButtonUp

```
afx_msg void OnLButtonUp(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

[in] *nFlags*<br/>

[in] *point*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="onmousemove"></a>  CMFCDropDownToolBar::OnMouseMove

```
afx_msg void OnMouseMove(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

[in] *nFlags*<br/>

[in] *point*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="onsendcommand"></a>  CMFCDropDownToolBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parámetros

[in] *pButton*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="onupdatecmdui"></a>  CMFCDropDownToolBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parámetros

[in] *pTarget*<br/>

[in] *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBar::Create](../../mfc/reference/cmfctoolbar-class.md#create)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[CMFCDropDownToolbarButton (clase)](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)<br/>
[Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)
