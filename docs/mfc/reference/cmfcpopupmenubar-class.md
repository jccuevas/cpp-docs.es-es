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
ms.openlocfilehash: acb1e2be7d40e5e0c569fffcc92c57c750be8f91
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58776783"
---
# <a name="cmfcpopupmenubar-class"></a>CMFCPopupMenuBar (clase)

Una barra de menús incrustada en un menú emergente.

## <a name="syntax"></a>Sintaxis

```
class CMFCPopupMenuBar : public CMFCToolBar
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCPopupMenuBar::AdjustSizeImmediate](#adjustsizeimmediate)|Inmediatamente vuelve a calcular el diseño de un panel. (Invalida [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).)|
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|Carga los elementos de menú emergente de un recurso de menú especificado.|
|[CMFCPopupMenuBar::CloseDelayedSubMenu](#closedelayedsubmenu)|Cierra un botón de menú emergente diferida.|
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|Compila un menú de los botones de menú emergente.|
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|Busca la barra de herramientas donde se encuentra un punto especificado.|
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|Indica el tamaño de imágenes de botón de menú.|
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|Devuelve el identificador del elemento de menú predeterminado.|
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|Obtiene el índice del comando de menú más recientemente invocado.|
|[CMFCPopupMenuBar::GetOffset](#getoffset)|Obtiene el desplazamiento de fila de la barra de menú emergente.|
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|Importa los botones de menú emergente de un menú especificado.|
|[CMFCPopupMenuBar::IsDropDownListMode](#isdropdownlistmode)|Indica si la barra de menú emergente está en modo de lista desplegable.|
|[CMFCPopupMenuBar::IsPaletteMode](#ispalettemode)|Indica si la barra de menú emergente está en modo de paleta.|
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|Indica si se trata de un panel de cinta (FALSE de forma predeterminada).|
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|Indica si se trata de un panel de cinta de opciones en el modo normal (FALSE de forma predeterminada).|
|[CMFCPopupMenuBar::LoadFromHash](#loadfromhash)|Carga un menú de archivado.|
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|Restaura un botón de menú diferida para cerrar la barra de menú emergente.|
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|Establece el estilo del botón de barra de herramientas en el índice especificado. (Invalida [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)|
|[CMFCPopupMenuBar::SetOffset](#setoffset)|Establece el desplazamiento de fila de la barra de menú emergente.|
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|Inicia el temporizador para un botón de menú emergente de retraso especificado.|

### <a name="data-members"></a>Miembros de datos

|Name|Descripción|
|----------|-----------------|
|[CMFCPopupMenuBar::m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|Especifica si la barra lateral deshabilitada se mostrará cuando la aplicación tiene una apariencia de Windows XP.|

## <a name="remarks"></a>Comentarios

El `CMFCPopupMenuBar` se crea al mismo tiempo que un [CMFCPopupMenu (clase)](../../mfc/reference/cmfcpopupmenu-class.md) e incrustados dentro de él. El `CMFCPopupMenuBar` cubre toda el área cliente de la `CMFCPopupMenu` objeto. Es compatible con teclado y mouse de entrada. También se comunica de entrada para el `CMFCPopupMenu` y a la ventana de marco de nivel superior.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo inicializar un `CMFCPopupMenuBar` objeto desde un `CMFCPopupMenu` objeto. Este fragmento de código forma parte del [Ejemplo de cliente de dibujo](../../overview/visual-cpp-samples.md).

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

##  <a name="adjustsizeimmediate"></a>  CMFCPopupMenuBar::AdjustSizeImmediate

Inmediatamente vuelve a calcular el diseño del panel de barra de menú emergente. (Invalida [CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate).

```
virtual void AdjustSizeImmediate(BOOL bRecalcLayout);
```

### <a name="parameters"></a>Parámetros

*bRecalcLayout*<br/>
[in] TRUE para volver a calcular automáticamente el diseño del panel de barra de menú emergente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="buildorigitems"></a>  CMFCPopupMenuBar::BuildOrigItems

Carga los elementos de menú emergente de un recurso de menú especificado.

```
BOOL BuildOrigItems(UINT uiMenuResID);
```

### <a name="parameters"></a>Parámetros

*uiMenuResID*<br/>
[in] Especifica el identificador de menú del recurso de menú para cargar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se realiza correctamente o FALSE si no.

### <a name="remarks"></a>Comentarios

##  <a name="closedelayedsubmenu"></a>  CMFCPopupMenuBar::CloseDelayedSubMenu

Cierra un botón de menú emergente que se ha retrasado.

```
virtual void CloseDelayedSubMenu();
```

### <a name="remarks"></a>Comentarios

##  <a name="exporttomenu"></a>  CMFCPopupMenuBar::ExportToMenu

Compila un menú de los botones del menú emergente.

```
virtual HMENU ExportToMenu() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador para el nuevo menú.

### <a name="remarks"></a>Comentarios

##  <a name="finddestintationtoolbar"></a>  CMFCPopupMenuBar::FindDestintationToolBar

Busca la barra de herramientas donde se encuentra un punto especificado.

```
CMFCToolBar* FindDestintationToolBar(CPoint point);
```

### <a name="parameters"></a>Parámetros

*point*<br/>
[in] Un punto en la pantalla.

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador a la barra de herramientas donde se encuentra el punto, si hay alguno, o NULL si no.

### <a name="remarks"></a>Comentarios

##  <a name="getcurrentmenuimagesize"></a>  CMFCPopupMenuBar::GetCurrentMenuImageSize

Indica el tamaño de imágenes de botón de menú.

```
virtual CSize GetCurrentMenuImageSize() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el tamaño de imágenes de botón de menú en la barra de herramientas.

### <a name="remarks"></a>Comentarios

##  <a name="getdefaultmenuid"></a>  CMFCPopupMenuBar::GetDefaultMenuId

Devuelve el identificador del elemento de menú predeterminado.

```
UINT GetDefaultMenuId() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador del elemento de menú predeterminado en la barra de menú emergente.

### <a name="remarks"></a>Comentarios

##  <a name="getlastcommandindex"></a>  CMFCPopupMenuBar::GetLastCommandIndex

Obtiene el índice del comando de menú más recientemente invocado.

```
static int __stdcall GetLastCommandIndex();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el índice del último comando de menú que se ha invocado.

### <a name="remarks"></a>Comentarios

##  <a name="getoffset"></a>  CMFCPopupMenuBar::GetOffset

Obtiene el desplazamiento de fila de la barra de menú emergente.

```
int GetOffset() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el desplazamiento de fila de la barra de menú emergente.

### <a name="remarks"></a>Comentarios

Este valor se establece mediante [CMFCPopupMenuBar::SetOffset](#setoffset).

##  <a name="importfrommenu"></a>  CMFCPopupMenuBar::ImportFromMenu

Importa los botones de menú emergente de un menú especificado.

```
virtual BOOL ImportFromMenu(
    HMENU hMenu,
    BOOL bShowAllCommands = FALSE);
```

### <a name="parameters"></a>Parámetros

*hMenu*<br/>
[in] El menú desde el que se va a importar los botones del menú emergente.

*bShowAllCommands*<br/>
[in] TRUE si todos los comandos del menú son importados, o FALSE si se pueden ocultar los usados con poca frecuencia.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si los botones de menú se han importado correctamente en el menú, o FALSE si no.

### <a name="remarks"></a>Comentarios

##  <a name="isdropdownlistmode"></a>  CMFCPopupMenuBar::IsDropDownListMode

Indica si la barra de menú emergente está en modo de lista desplegable.

```
BOOL IsDropDownListMode() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la barra de menú emergente no está en modo de lista desplegable, o si es FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="ispalettemode"></a>  CMFCPopupMenuBar::IsPaletteMode

Indica si la barra de menú emergente está en modo de paleta.

```
BOOL IsPaletteMode() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si está habilitado el modo de paleta o FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Cuando la barra de menús está establecida en modo de paleta, elementos de menú aparecen en varias columnas y un número limitado de filas.

##  <a name="isribbonpanel"></a>  CMFCPopupMenuBar::IsRibbonPanel

Indica si se trata de un panel de cinta (FALSE de forma predeterminada).

```
virtual BOOL IsRibbonPanel() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve FALSE de forma predeterminada, que indica que no es un panel de cinta de opciones.

### <a name="remarks"></a>Comentarios

##  <a name="isribbonpanelinregularmode"></a>  CMFCPopupMenuBar::IsRibbonPanelInRegularMode

Indica si se trata de un panel de cinta de opciones en el modo normal (FALSE de forma predeterminada).

```
virtual BOOL IsRibbonPanelInRegularMode() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve FALSE de forma predeterminada, que indica que esto no es un panel de cinta de opciones en el modo normal.

### <a name="remarks"></a>Comentarios

##  <a name="loadfromhash"></a>  CMFCPopupMenuBar::LoadFromHash

Carga un menú de archivado.

```
BOOL LoadFromHash(HMENU hMenu);
```

### <a name="parameters"></a>Parámetros

*hMenu*<br/>
[in] Un identificador del menú archivado para cargar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el menú está cargado correctamente o FALSE si no lo es.

### <a name="remarks"></a>Comentarios

##  <a name="m_bdisablesidebarinxpmode"></a>  CMFCPopupMenuBar::m_bDisableSideBarInXPMode

Un parámetro booleano que indica si la aplicación tiene una barra lateral deshabilitada cuando tiene una apariencia de Windows XP.

```
BOOL m_bDisableSideBarInXPMode;
```

### <a name="remarks"></a>Comentarios

Si esta variable de miembro se establece en FALSE y la aplicación tiene una apariencia de Windows XP, el marco de trabajo dibuja una barra lateral deshabilitada en la aplicación.

El valor predeterminado es FALSE.

##  <a name="restoredelayedsubmenu"></a>  CMFCPopupMenuBar::RestoreDelayedSubMenu

Restaura un botón de menú diferida para cerrar la barra de menú emergente.

```
virtual void RestoreDelayedSubMenu();
```

### <a name="remarks"></a>Comentarios

##  <a name="setbuttonstyle"></a>  CMFCPopupMenuBar::SetButtonStyle

Establece el estilo del botón de barra de herramientas en el índice especificado. (Invalida [CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)

```
virtual void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[in] Índice de base cero del botón de barra de herramientas cuyo estilo se va a establecer.

*nStyle*<br/>
[in] El estilo del botón. Consulte [estilos de Control de barra de herramientas](../../mfc/reference/toolbar-control-styles.md) para obtener la lista de estilos de botón de barra de herramientas disponibles.

### <a name="remarks"></a>Comentarios

##  <a name="setoffset"></a>  CMFCPopupMenuBar::SetOffset

Establece el desplazamiento de fila de la barra de menú emergente.

```
void SetOffset(int iOffset);
```

### <a name="parameters"></a>Parámetros

*iOffset*<br/>
[in] El número de filas que se debe desplazar la barra de menú emergente.

### <a name="remarks"></a>Comentarios

##  <a name="startpopupmenutimer"></a>  CMFCPopupMenuBar::StartPopupMenuTimer

Inicia el temporizador para un botón de menú emergente de retraso especificado.

```
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,
    int nDelayFactor = 1);
```

### <a name="parameters"></a>Parámetros

*pMenuButton*<br/>
[in] Puntero en el botón de menú que se va a establecer el temporizador de retraso.

*nDelayFactor*<br/>
[in] Un factor retraso, igual que al menos uno, para multiplicar por el tiempo de retraso de menú estándar (generalmente entre un medio segundo y cinco segundos).

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar (clase)](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCPopupMenu (clase)](../../mfc/reference/cmfcpopupmenu-class.md)
