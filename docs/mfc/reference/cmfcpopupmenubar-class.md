---
title: CMFCPopupMenuBar (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::AdjustSizeImmediate
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::BuildOrigItems
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::CloseDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ExportToMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::FindDestintationToolBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetCurrentMenuImageSize
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetDefaultMenuId
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetLastCommandIndex
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ImportFromMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsDropDownListMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsPaletteMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanel
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanelInRegularMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::LoadFromHash
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::RestoreDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetButtonStyle
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::StartPopupMenuTimer
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::m_bDisableSideBarInXPMode
helpviewer_keywords:
- CMFCPopupMenuBar [MFC], AdjustSizeImmediate
- CMFCPopupMenuBar [MFC], BuildOrigItems
- CMFCPopupMenuBar [MFC], CloseDelayedSubMenu
- CMFCPopupMenuBar [MFC], ExportToMenu
- CMFCPopupMenuBar [MFC], FindDestintationToolBar
- CMFCPopupMenuBar [MFC], GetCurrentMenuImageSize
- CMFCPopupMenuBar [MFC], GetDefaultMenuId
- CMFCPopupMenuBar [MFC], GetLastCommandIndex
- CMFCPopupMenuBar [MFC], GetOffset
- CMFCPopupMenuBar [MFC], ImportFromMenu
- CMFCPopupMenuBar [MFC], IsDropDownListMode
- CMFCPopupMenuBar [MFC], IsPaletteMode
- CMFCPopupMenuBar [MFC], IsRibbonPanel
- CMFCPopupMenuBar [MFC], IsRibbonPanelInRegularMode
- CMFCPopupMenuBar [MFC], LoadFromHash
- CMFCPopupMenuBar [MFC], RestoreDelayedSubMenu
- CMFCPopupMenuBar [MFC], SetButtonStyle
- CMFCPopupMenuBar [MFC], SetOffset
- CMFCPopupMenuBar [MFC], StartPopupMenuTimer
- CMFCPopupMenuBar [MFC], m_bDisableSideBarInXPMode
ms.assetid: 4c93c459-7f70-4240-8c63-280bb811e374
ms.openlocfilehash: c0ba90246d19e8dd07c856eec6a518a8513ee665
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751921"
---
# <a name="cmfcpopupmenubar-class"></a>CMFCPopupMenuBar (clase)

Una barra de menús incrustada en un menú emergente.

## <a name="syntax"></a>Sintaxis

```
class CMFCPopupMenuBar : public CMFCToolBar
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCPopupMenuBar::AdjustSizeImmediate](#adjustsizeimmediate)|Recalcula inmediatamente el diseño de un panel. (Reemplaza [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).)|
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|Carga elementos de menú emergente desde un recurso de menú especificado.|
|[CMFCPopupMenuBar::CloseDelayedSubMenu](#closedelayedsubmenu)|Cierra un botón de menú emergente retrasado.|
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|Crea un menú a partir de los botones del menú emergente.|
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|Busca la barra de herramientas donde se encuentra un punto especificado.|
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|Indica el tamaño de las imágenes de botón de menú.|
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|Devuelve el identificador del elemento de menú predeterminado.|
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|Obtiene el índice del comando de menú invocado más recientemente.|
|[CMFCPopupMenuBar::GetOffset](#getoffset)|Obtiene el desplazamiento de fila de la barra de menús emergente.|
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|Importa los botones del menú emergente desde un menú especificado.|
|[CMFCPopupMenuBar::IsDropDownListMode](#isdropdownlistmode)|Indica si la barra de menús emergentes está en modo de lista desplegable.|
|[CMFCPopupMenuBar::IsPaletteMode](#ispalettemode)|Indica si la barra de menús emergente está en modo de paleta.|
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|Indica si se trata de un panel de la cinta de opciones (FALSE de forma predeterminada).|
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|Indica si se trata de un panel de la cinta de opciones en modo normal (FALSE de forma predeterminada).|
|[CMFCPopupMenuBar::LoadFromHash](#loadfromhash)|Carga un menú archivado.|
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|Restaura un botón de menú retrasado para cerrar la barra de menú emergente.|
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|Establece el estilo del botón de la barra de herramientas en el índice especificado. (Reemplaza [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)|
|[CMFCPopupMenuBar::SetOffset](#setoffset)|Establece el desplazamiento de fila de la barra de menús emergente.|
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|Inicia el temporizador para un botón de menú emergente retrasado especificado.|

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCPopupMenuBar::m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|Especifica si la barra lateral gris se mostrará cuando la aplicación tenga una apariencia de Windows XP.|

## <a name="remarks"></a>Observaciones

El `CMFCPopupMenuBar` se crea al mismo tiempo que un [CMFCPopupMenu clase](../../mfc/reference/cmfcpopupmenu-class.md) e incrustado dentro de ella. Cubre `CMFCPopupMenuBar` todo el área `CMFCPopupMenu` de cliente del objeto. Es compatible con la entrada de teclado y ratón. También comunica esa entrada `CMFCPopupMenu` a la ventana de marco de nivel superior y a la ventana de marco superior.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se `CMFCPopupMenuBar` muestra `CMFCPopupMenu` cómo inicializar un objeto desde un objeto. Este fragmento de código forma parte del [Ejemplo de cliente de dibujo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#7](../../mfc/reference/codesnippet/cpp/cmfcpopupmenubar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpopupmenubar.h

## <a name="cmfcpopupmenubaradjustsizeimmediate"></a><a name="adjustsizeimmediate"></a>CMFCPopupMenuBar::AdjustSizeImmediate

Inmediatamente vuelve a calcular el diseño del panel de la barra de menús emergente. (Reemplaza [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).

```
virtual void AdjustSizeImmediate(BOOL bRecalcLayout);
```

### <a name="parameters"></a>Parámetros

*bRecalcLayout*<br/>
[en] TRUE para volver a calcular automáticamente el diseño del panel de la barra de menús emergente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cmfcpopupmenubarbuildorigitems"></a><a name="buildorigitems"></a>CMFCPopupMenuBar::BuildOrigItems

Carga elementos de menú emergente desde un recurso de menú especificado.

```
BOOL BuildOrigItems(UINT uiMenuResID);
```

### <a name="parameters"></a>Parámetros

*uiMenuResID*<br/>
[en] Especifica el identificador de menú del recurso de menú que se va a cargar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se realiza correctamente o FALSE si no.

### <a name="remarks"></a>Observaciones

## <a name="cmfcpopupmenubarclosedelayedsubmenu"></a><a name="closedelayedsubmenu"></a>CMFCPopupMenuBar::CloseDelayedSubMenu

Cierra un botón de menú emergente que se ha retrasado.

```
virtual void CloseDelayedSubMenu();
```

### <a name="remarks"></a>Observaciones

## <a name="cmfcpopupmenubarexporttomenu"></a><a name="exporttomenu"></a>CMFCPopupMenuBar::ExportToMenu

Crea un menú a partir de los botones del menú emergente.

```
virtual HMENU ExportToMenu() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador al nuevo menú.

### <a name="remarks"></a>Observaciones

## <a name="cmfcpopupmenubarfinddestintationtoolbar"></a><a name="finddestintationtoolbar"></a>CMFCPopupMenuBar::FindDestintationToolBar

Busca la barra de herramientas donde se encuentra un punto especificado.

```
CMFCToolBar* FindDestintationToolBar(CPoint point);
```

### <a name="parameters"></a>Parámetros

*Punto*<br/>
[en] Un punto en la pantalla.

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador a la barra de herramientas donde se encuentra el punto, si hay uno, o NULL si no.

### <a name="remarks"></a>Observaciones

## <a name="cmfcpopupmenubargetcurrentmenuimagesize"></a><a name="getcurrentmenuimagesize"></a>CMFCPopupMenuBar::GetCurrentMenuImageSize

Indica el tamaño de las imágenes de botón de menú.

```
virtual CSize GetCurrentMenuImageSize() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el tamaño de las imágenes de botón de menú en la barra de herramientas.

### <a name="remarks"></a>Observaciones

## <a name="cmfcpopupmenubargetdefaultmenuid"></a><a name="getdefaultmenuid"></a>CMFCPopupMenuBar::GetDefaultMenuId

Devuelve el identificador del elemento de menú predeterminado.

```
UINT GetDefaultMenuId() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador del elemento de menú predeterminado en la barra de menús emergente.

### <a name="remarks"></a>Observaciones

## <a name="cmfcpopupmenubargetlastcommandindex"></a><a name="getlastcommandindex"></a>CMFCPopupMenuBar::GetLastCommandIndex

Obtiene el índice del comando de menú invocado más recientemente.

```
static int __stdcall GetLastCommandIndex();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el índice del último comando de menú que se ha invocado.

### <a name="remarks"></a>Observaciones

## <a name="cmfcpopupmenubargetoffset"></a><a name="getoffset"></a>CMFCPopupMenuBar::GetOffset

Obtiene el desplazamiento de fila de la barra de menús emergente.

```
int GetOffset() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el desplazamiento de fila de la barra de menús emergente.

### <a name="remarks"></a>Observaciones

Este valor se establece mediante [CMFCPopupMenuBar::SetOffset](#setoffset).

## <a name="cmfcpopupmenubarimportfrommenu"></a><a name="importfrommenu"></a>CMFCPopupMenuBar::ImportFromMenu

Importa los botones del menú emergente desde un menú especificado.

```
virtual BOOL ImportFromMenu(
    HMENU hMenu,
    BOOL bShowAllCommands = FALSE);
```

### <a name="parameters"></a>Parámetros

*hMenú*<br/>
[en] El menú desde el que se importaron los botones del menú emergente.

*bShowAllCommands*<br/>
[en] TRUESi todos los comandos del menú se van a importar, o FALSE si se usan raramente puede estar oculto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si los botones de menú se importaron correctamente desde el menú, o FALSE si no.

### <a name="remarks"></a>Observaciones

## <a name="cmfcpopupmenubarisdropdownlistmode"></a><a name="isdropdownlistmode"></a>CMFCPopupMenuBar::IsDropDownListMode

Indica si la barra de menús emergentes está en modo de lista desplegable.

```
BOOL IsDropDownListMode() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la barra de menús emergente está en modo de lista desplegable, o FALSE si no.

### <a name="remarks"></a>Observaciones

## <a name="cmfcpopupmenubarispalettemode"></a><a name="ispalettemode"></a>CMFCPopupMenuBar::IsPaletteMode

Indica si la barra de menús emergente está en modo de paleta.

```
BOOL IsPaletteMode() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el modo de paleta está habilitado, o FALSE si no.

### <a name="remarks"></a>Observaciones

Cuando la barra de menús se establece en modo de paleta, los elementos de menú aparecen en varias columnas y un número limitado de filas.

## <a name="cmfcpopupmenubarisribbonpanel"></a><a name="isribbonpanel"></a>CMFCPopupMenuBar::IsRibbonPanel

Indica si se trata de un panel de la cinta de opciones (FALSE de forma predeterminada).

```
virtual BOOL IsRibbonPanel() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve FALSE de forma predeterminada, lo que indica que no se trata de un panel de la cinta de opciones.

### <a name="remarks"></a>Observaciones

## <a name="cmfcpopupmenubarisribbonpanelinregularmode"></a><a name="isribbonpanelinregularmode"></a>CMFCPopupMenuBar::IsRibbonPanelInRegularMode

Indica si se trata de un panel de la cinta de opciones en modo normal (FALSE de forma predeterminada).

```
virtual BOOL IsRibbonPanelInRegularMode() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve FALSE de forma predeterminada, lo que indica que no se trata de un panel de la cinta de opciones en modo normal.

### <a name="remarks"></a>Observaciones

## <a name="cmfcpopupmenubarloadfromhash"></a><a name="loadfromhash"></a>CMFCPopupMenuBar::LoadFromHash

Carga un menú archivado.

```
BOOL LoadFromHash(HMENU hMenu);
```

### <a name="parameters"></a>Parámetros

*hMenú*<br/>
[en] Identificador del menú archivado para cargar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el menú se carga correctamente o FALSE si no.

### <a name="remarks"></a>Observaciones

## <a name="cmfcpopupmenubarm_bdisablesidebarinxpmode"></a><a name="m_bdisablesidebarinxpmode"></a>CMFCPopupMenuBar::m_bDisableSideBarInXPMode

Parámetro booleano que indica si la aplicación tiene una barra lateral gris cuando tiene una apariencia de Windows XP.

```
BOOL m_bDisableSideBarInXPMode;
```

### <a name="remarks"></a>Observaciones

Si esta variable miembro se establece en FALSE y la aplicación tiene una apariencia de Windows XP, el marco de trabajo dibuja una barra lateral gris en la aplicación.

El valor predeterminado es FALSE.

## <a name="cmfcpopupmenubarrestoredelayedsubmenu"></a><a name="restoredelayedsubmenu"></a>CMFCPopupMenuBar::RestoreDelayedSubMenu

Restaura un botón de menú retrasado para cerrar la barra de menú emergente.

```
virtual void RestoreDelayedSubMenu();
```

### <a name="remarks"></a>Observaciones

## <a name="cmfcpopupmenubarsetbuttonstyle"></a><a name="setbuttonstyle"></a>CMFCPopupMenuBar::SetButtonStyle

Establece el estilo del botón de la barra de herramientas en el índice especificado. (Reemplaza [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)

```
virtual void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[en] El índice de base cero del botón de barra de herramientas cuyo estilo se va a establecer.

*nStyle*<br/>
[en] El estilo del botón. Consulte [Estilos](../../mfc/reference/toolbar-control-styles.md) de control de barra de herramientas para obtener la lista de estilos de botón de barra de herramientas disponibles.

### <a name="remarks"></a>Observaciones

## <a name="cmfcpopupmenubarsetoffset"></a><a name="setoffset"></a>CMFCPopupMenuBar::SetOffset

Establece el desplazamiento de fila de la barra de menús emergente.

```cpp
void SetOffset(int iOffset);
```

### <a name="parameters"></a>Parámetros

*iOffset*<br/>
[en] El número de filas que se debe desplazar a la barra de menús emergente.

### <a name="remarks"></a>Observaciones

## <a name="cmfcpopupmenubarstartpopupmenutimer"></a><a name="startpopupmenutimer"></a>CMFCPopupMenuBar::StartPopupMenuTimer

Inicia el temporizador para un botón de menú emergente retrasado especificado.

```cpp
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,
    int nDelayFactor = 1);
```

### <a name="parameters"></a>Parámetros

*pMenuButton*<br/>
[en] Puntero al botón de menú para el que se debe configurar el temporizador de retardo.

*nDelayFactor*<br/>
[en] Un factor de retardo, igual a al menos uno, para multiplicar por el tiempo de retardo del menú estándar (generalmente entre medio segundo y cinco segundos).

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar Clase](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCPopupMenu (clase)](../../mfc/reference/cmfcpopupmenu-class.md)
