---
title: CMFCColorPopupMenu (Clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CreateTearOffBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::GetMenuBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::SetPropList
helpviewer_keywords:
- CMFCColorPopupMenu [MFC], CMFCColorPopupMenu
- CMFCColorPopupMenu [MFC], CreateTearOffBar
- CMFCColorPopupMenu [MFC], GetMenuBar
- CMFCColorPopupMenu [MFC], SetPropList
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
ms.openlocfilehash: 901a44c8f5fdecd1b277ebdecc995722a3afe9a3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752493"
---
# <a name="cmfccolorpopupmenu-class"></a>CMFCColorPopupMenu (Clase)

Representa un menú emergente que los usuarios usan para seleccionar colores en un documento o aplicación.

## <a name="syntax"></a>Sintaxis

```
class CMFCColorPopupMenu : public CMFCPopupMenu
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Nombre|Descripción|
|[CMFCColorPopupMenu::CMFCColorPopupMenu](#cmfccolorpopupmenu)|Construye un objeto `CMFCColorPopupMenu`.|
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Nombre|Descripción|
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|Crea una barra de color de desgarro acoplable. (Reemplaza [CMFCPopupMenu::CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar).)|
|[CMFCColorPopupMenu::GetMenuBar](#getmenubar)|Devuelve el [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) que se incrusta dentro del menú emergente. (Reemplaza [CMFCPopupMenu::GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar).)|
|`CMFCColorPopupMenu::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|[CMFCColorPopupMenu::SetPropList](#setproplist)|Establece el objeto de control `CMFCColorBar` de cuadrícula de propiedades del objeto incrustado.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|Nombre|Descripción|
|`m_bEnabledInCustomizeMode`|Valor booleano que determina si se debe mostrar la barra de color.|
|`m_wndColorBar`|Objeto `CMFCColorBar` que proporciona selección de color.|

### <a name="remarks"></a>Observaciones

Esta clase hereda la funcionalidad del `CMFCPopupMenu` menú emergente `CMFCColorBar` de la clase y administra un objeto que proporciona selección de color. Cuando el marco de trabajo `m_bEnabledInCustomizeMode` de la barra de herramientas está en modo de personalización y el miembro se establece en FALSE, no se muestra el objeto de barra de color. Para obtener más información sobre el modo de personalización, vea [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)

Para obtener `CMFCColorBar`más información sobre , vea [CMFCColorBar (Clase)](../../mfc/reference/cmfccolorbar-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

[CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcolorpopupmenu.h

## <a name="cmfccolorpopupmenucmfccolorpopupmenu"></a><a name="cmfccolorpopupmenu"></a>CMFCColorPopupMenu::CMFCColorPopupMenu

Construye un objeto `CMFCColorPopupMenu`.

```
CMFCColorPopupMenu(
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    int nHorzDockRows,
    int nVertDockColumns,
    COLORREF colorAutomatic,
    UINT uiCommandID,
    BOOL bStdColorDlg = FALSE);

CMFCColorPopupMenu(
    CMFCColorButton* pParentBtn,
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic);

CMFCColorPopupMenu(
    CMFCRibbonColorButton* pParentBtn,
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*colores*<br/>
[en] Matriz de colores que el marco de trabajo muestra en el menú emergente.

*Color*<br/>
[en] El color seleccionado por defecto.

*lpszAutoColor*<br/>
[en] La etiqueta de texto del botón de color *automático* (predeterminado) o NULL.

La etiqueta estándar para el botón automático es **Automático**.

*lpszOtherColor*<br/>
[en] La etiqueta de texto del *otro* botón, que muestra más opciones de color, o NULL.

La etiqueta estándar para el otro botón es **Más colores...**.

*lpszDocColors*<br/>
[en] La etiqueta de texto del botón de colores del documento. La paleta de colores del documento muestra todos los colores que utiliza actualmente el documento.

*lstDocColors*<br/>
[en] Una lista de colores que el documento utiliza actualmente.

*nColumns*<br/>
[en] El número de columnas que tiene la matriz de colores.

*nHorzDockRows*<br/>
[en] El número de filas que tiene la barra de color cuando se acopla horizontalmente.

*nVertDockColumns*<br/>
[en] El número de columnas que tiene la barra de color cuando se acopla verticalmente.

*colorAutomático*<br/>
[en] El color predeterminado que se aplica al hacer clic en el botón automático.

*uiCommandID*<br/>
[en] El ID del comando de control de barra de color.

*bStdColorDlg*<br/>
[en] Un valor booleano que indica si se debe mostrar el cuadro de diálogo de color del sistema estándar o el cuadro de diálogo [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) .

*pParentBtn*<br/>
[en] Un puntero a un botón primario.

*nID*<br/>
[en] El id de comando.

### <a name="remarks"></a>Observaciones

Cada constructor sobrecargado `m_bEnabledInCustomizeMode` establece el miembro en FALSE.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `CMFCColorPopupMenu` muestra cómo construir un objeto.

[!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]

## <a name="cmfccolorpopupmenucreatetearoffbar"></a><a name="createtearoffbar"></a>CMFCColorPopupMenu::CreateTearOffBar

Crea una barra de color de desgarro acoplable.

```
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,
    UINT uiID,
    LPCTSTR lpszName);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pWndMain*|[en] Puntero a la ventana principal de la barra de desmontaje.|
|*uiID*|[en] El id de comando de la barra de desmontaje.|
|*lpszName*|[en] El texto de la ventana de la barra de desmontaje.|

### <a name="return-value"></a>Valor devuelto

Puntero al nuevo objeto de barra de control de desmontaje.

### <a name="remarks"></a>Observaciones

Este método crea un [CMFCColorBar clase](../../mfc/reference/cmfccolorbar-class.md) objeto y lo convierte en un [CPane clase](../../mfc/reference/cpane-class.md) puntero. Puede convertir este valor a un [CMFCColorBar (clase)](../../mfc/reference/cmfccolorbar-class.md) puntero mediante una de las macros de conversión de tipos descritas en [Conversión de tipos de objetos de clase MFC](../../mfc/reference/type-casting-of-mfc-class-objects.md).

## <a name="cmfccolorpopupmenugetmenubar"></a><a name="getmenubar"></a>CMFCColorPopupMenu::GetMenuBar

Devuelve el [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) que se incrusta dentro del menú emergente.

```
virtual CMFCPopupMenuBar* GetMenuBar();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a `CMFCPopupMenuBar`la incrustación .

### <a name="remarks"></a>Observaciones

El menú emergente de color tiene un objeto [de clase CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) incrustado. Invalide este método en una clase derivada si la aplicación usa un tipo incrustado diferente.

## <a name="cmfccolorpopupmenusetproplist"></a><a name="setproplist"></a>CMFCColorPopupMenu::SetPropList

Establece el objeto de control `CMFCColorBar` de cuadrícula de propiedades del objeto incrustado.

```cpp
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Parámetros

*pWndList*<br/>
[en] Puntero a un objeto de control de cuadrícula de propiedades.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
