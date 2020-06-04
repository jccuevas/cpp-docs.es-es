---
title: CMFCRibbonMiniToolBar (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsContextMenuMode
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::SetCommands
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::Show
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::ShowWithContextMenu
helpviewer_keywords:
- CMFCRibbonMiniToolBar [MFC], IsContextMenuMode
- CMFCRibbonMiniToolBar [MFC], IsRibbonMiniToolBar
- CMFCRibbonMiniToolBar [MFC], SetCommands
- CMFCRibbonMiniToolBar [MFC], Show
- CMFCRibbonMiniToolBar [MFC], ShowWithContextMenu
ms.assetid: 7017e963-aeaf-4fe9-b540-e15a7ed41e94
ms.openlocfilehash: 5e5ac6c923640b7584d89a9c6f75d941deadddf3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754079"
---
# <a name="cmfcribbonminitoolbar-class"></a>CMFCRibbonMiniToolBar (clase)

Implementa una barra de herramientas emergente contextual.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonMiniToolBar : public CMFCRibbonPanelMenu
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CMFCRibbonMiniToolBar`|Constructor predeterminado.|
|`CMFCRibbonMiniToolBar::~CMFCRibbonMiniToolBar`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CMFCRibbonMiniToolBar::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|[CMFCRibbonMiniToolBar::IsContextMenuMode](#iscontextmenumode)||
|[CMFCRibbonMiniToolBar::IsRibbonMiniToolBar](#isribbonminitoolbar)|(Invalida `CMFCPopupMenu::IsRibbonMiniToolBar`).|
|[CMFCRibbonMiniToolBar::SetCommands](#setcommands)|Establece la lista de comandos que se mostrarán en la barra de herramientas.|
|[CMFCRibbonMiniToolBar::Show](#show)|Muestra la minibarra de herramientas en las coordenadas de pantalla especificadas.|
|[CMFCRibbonMiniToolBar::ShowWithContextMenu](#showwithcontextmenu)|Muestra la minibarra de herramientas junto con un menú contextual.|

## <a name="remarks"></a>Observaciones

La minibarra de herramientas se muestra normalmente cuando el usuario selecciona un objeto en un documento. Por ejemplo, cuando el usuario selecciona un bloque de texto en un procesador de textos, la aplicación muestra una minibarra de herramientas que contiene los comandos de formato de texto.

La minibarra de herramientas se hace transparente cuando el puntero del mouse está fuera de los límites de la minibarra.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

`CMFCRibbonPanelMenu`

[CMFCRibbonMiniToolBar](../../mfc/reference/cmfcribbonminitoolbar-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxRibbonMiniToolBar.h

## <a name="cmfcribbonminitoolbarsetcommands"></a><a name="setcommands"></a>CMFCRibbonMiniToolBar::SetCommands

Establece la lista de comandos que se mostrarán en la barra de herramientas.

```cpp
void SetCommands(
    CMFCRibbonBar* pRibbonBar,
    const CList<UINT,UINT>& lstCommands);
```

### <a name="parameters"></a>Parámetros

*pRibbonBar*<br/>
[en] La barra de la cinta de opciones que la mini barra de herramientas busca para que se muestren los botones.

*lstCommands*<br/>
[en] La lista de comandos que se mostrarán en la minibarra de herramientas. Se buscan todas las categorías de la cinta de opciones para encontrar los botones asociados.

### <a name="remarks"></a>Observaciones

Utilice esta función para establecer la lista de comandos que se mostrarán en la minibarra de herramientas.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `SetCommands` muestra `CMFCRibbonMiniToolBar` cómo utilizar el método de la clase. Este fragmento de código forma parte del ejemplo de demostración de [MS Office 2007.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_MSOffice2007Demo#9](../../mfc/reference/codesnippet/cpp/cmfcribbonminitoolbar-class_1.cpp)]

## <a name="cmfcribbonminitoolbarshow"></a><a name="show"></a>CMFCRibbonMiniToolBar::Show

Muestra la minibarra de herramientas en las coordenadas de pantalla especificadas.

```
BOOL Show(
    int x,
    int y);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
[en] Especifica la posición horizontal de la mini barra de herramientas en coordenadas de pantalla.

*y y*<br/>
[en] Especifica la posición vertical de la mini barra de herramientas en coordenadas de pantalla.

### <a name="return-value"></a>Valor devuelto

TRUESi la mini barra de herramientas se mostró correctamente; de lo contrario, FALSE.

## <a name="cmfcribbonminitoolbarshowwithcontextmenu"></a><a name="showwithcontextmenu"></a>CMFCRibbonMiniToolBar::ShowWithContextMenu

Muestra la minibarra de herramientas junto con un menú contextual.

```
BOOL ShowWithContextMenu(
    int x,
    int y,
    UINT uiMenuResID,
    CWnd* pWndOwner);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
[en] Especifica la posición horizontal del menú contextual en coordenadas de pantalla.

*y y*<br/>
[en] Especifica la posición vertical del menú contextual en coordenadas de pantalla.

*uiMenuResID*<br/>
[en] Especifica el identificador de recurso del menú contextual que se va a mostrar.

*pWndOwner*<br/>
[en] Identifica la ventana que recibe mensajes desde el menú contextual.

### <a name="return-value"></a>Valor devuelto

TRUESi el menú contextual se ha mostrado correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Utilice esta función para mostrar una mini barra de herramientas que tenga un menú contextual. El menú contextual se coloca 15 píxeles debajo de la mini barra de herramientas.

## <a name="cmfcribbonminitoolbariscontextmenumode"></a><a name="iscontextmenumode"></a>CMFCRibbonMiniToolBar::IsContextMenuMode

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
BOOL IsContextMenuMode() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcribbonminitoolbarisribbonminitoolbar"></a><a name="isribbonminitoolbar"></a>CMFCRibbonMiniToolBar::IsRibbonMiniToolBar

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
virtual BOOL IsRibbonMiniToolBar() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
