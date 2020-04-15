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
ms.openlocfilehash: 68dd976471b39d7f50c2f0378b2fce99ad3feeca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367602"
---
# <a name="cmfcdropdowntoolbar-class"></a>CMFCDropDownToolBar (clase)

Una barra de herramientas que aparece cuando el usuario presiona y mantiene presionado un botón de la barra de herramientas de nivel superior.

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

## <a name="syntax"></a>Sintaxis

```
class CMFCDropDownToolBar : public CMFCToolBar
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Invalida `CPane::AllowShowOnPaneMenu`).|
|[CMFCDropDownToolBar::LoadBitmap](#loadbitmap)|(Reemplaza [CMFCToolBar::LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap).)|
|[CMFCDropDownToolBar::LoadToolBar](#loadtoolbar)|(Reemplaza [CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar).)|
|[CMFCDropDownToolBar::OnlButtonUp](#onlbuttonup)||
|[CMFCDropDownToolBar::OnMouseMove](#onmousemove)||
|[CMFCDropDownToolBar::OnSendCommand](#onsendcommand)|(Invalida `CMFCToolBar::OnSendCommand`).|
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(Reemplaza [CMFCToolBar::OnUpdateCmdUI](cmfctoolbar-class.md).|

### <a name="remarks"></a>Observaciones

Un `CMFCDropDownToolBar` objeto combina la apariencia visual de una barra de herramientas con el comportamiento de un menú emergente. Cuando un usuario presiona y mantiene presionado un botón de barra de herramientas desplegable (consulte [CMFCDropDownToolbarButton (Clase)](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)), aparece una barra de herramientas desplegable y el usuario puede seleccionar un botón de la barra de herramientas desplegable desplazándose hasta él y soltando el botón del mouse. Después de que el usuario selecciona un botón en la barra de herramientas desplegable, ese botón se muestra como el botón actual en la barra de herramientas de nivel superior.

Una barra de herramientas desplegable no se puede personalizar ni acoplar, y no tiene un estado de desmontaje.

La siguiente ilustración muestra un `CMFCDropDownToolBar` objeto:

![Ejemplo de CMFCDropDownToolbar](../../mfc/reference/media/cmfcdropdown.png "Ejemplo de CMFCDropDownToolbar")

Crear un `CMFCDropDownToolBar` objeto de la misma manera que se crea una barra de herramientas normal (consulte [CMFCToolBar (Clase)](../../mfc/reference/cmfctoolbar-class.md)).

Para insertar la barra de herramientas desplegable en una barra de herramientas principal:

1. Reserve un id. de recurso ficticio para el botón en el recurso primario de la barra de herramientas.

2. Cree `CMFCDropDownToolBarButton` un objeto que contenga la barra de herramientas desplegable (para obtener más información, vea [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton)).

3. Reemplace el botón `CMFCDropDownToolBarButton` ficticio por el objeto mediante [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Para obtener más información acerca de los botones de la barra de herramientas, vea [Tutorial: colocar controles en barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md). Para obtener un ejemplo de una barra de herramientas desplegable, vea el proyecto de ejemplo VisualStudioDemo.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se `Create` muestra `CMFCDropDownToolBar` cómo utilizar el método en la clase. Este fragmento de código forma parte del [ejemplo de demostración](../../overview/visual-cpp-samples.md)de Visual Studio.

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

## <a name="cmfcdropdowntoolbarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFCDropDownToolBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcdropdowntoolbarloadbitmap"></a><a name="loadbitmap"></a>CMFCDropDownToolBar::LoadBitmap

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
[en] El identificador de recurso del mapa de bits que hace referencia a las imágenes de la barra de herramientas en caliente.

*uiColdResID*<br/>
[en] El identificador de recurso del mapa de bits que hace referencia a las imágenes de la barra de herramientas en frío.

*uiMenuResID*<br/>
[en] El identificador de recurso del mapa de bits que hace referencia a las imágenes de menú normales.

*Bloqueado*<br/>
[en] TRUE para bloquear la barra de herramientas; de lo contrario FALSO.

*uiDisabledResID*<br/>
[en] El identificador de recurso del mapa de bits que hace referencia a las imágenes de la barra de herramientas deshabilitada.

*uiMenuDisabledResID*<br/>
[en] El identificador de recurso del mapa de bits que hace referencia a las imágenes de menú deshabilitadas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método es correcto; de lo contrario, 0.

### <a name="remarks"></a>Observaciones

El método [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) llama a este método para cargar las imágenes asociadas a la barra de herramientas. Invalide este método para realizar la carga personalizada de recursos de imagen.

Llame al método `LoadBitmapEx` para cargar imágenes adicionales después de crear la barra de herramientas.

## <a name="cmfcdropdowntoolbarloadtoolbar"></a><a name="loadtoolbar"></a>CMFCDropDownToolBar::LoadToolBar

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

[en] *uiResID*<br/>

[en] *uiColdResID*<br/>

[en] *uiMenuResID*<br/>

[en] *BOOL*<br/>

[en] *uiDisabledResID*<br/>

[en] *uiMenuDisabledResID*<br/>

[en] *uiHotResID*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcdropdowntoolbaronlbuttonup"></a><a name="onlbuttonup"></a>CMFCDropDownToolBar::OnlButtonUp

```
afx_msg void OnLButtonUp(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

[en] *nFlags*<br/>

[en] *punto*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcdropdowntoolbaronmousemove"></a><a name="onmousemove"></a>CMFCDropDownToolBar::OnMouseMove

```
afx_msg void OnMouseMove(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

[en] *nFlags*<br/>

[en] *punto*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcdropdowntoolbaronsendcommand"></a><a name="onsendcommand"></a>CMFCDropDownToolBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parámetros

[en] *pButton*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcdropdowntoolbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCDropDownToolBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parámetros

[en] *pTarget*<br/>

[en] *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar (Clase)](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBar::Crear](../../mfc/reference/cmfctoolbar-class.md#create)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[CMFCDropDownToolbarButton (Clase)](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)<br/>
[Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)
