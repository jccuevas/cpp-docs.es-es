---
title: Clase CStatusBar
ms.date: 11/04/2016
f1_keywords:
- CStatusBar
- AFXEXT/CStatusBar
- AFXEXT/CStatusBar::CStatusBar
- AFXEXT/CStatusBar::CommandToIndex
- AFXEXT/CStatusBar::Create
- AFXEXT/CStatusBar::CreateEx
- AFXEXT/CStatusBar::DrawItem
- AFXEXT/CStatusBar::GetItemID
- AFXEXT/CStatusBar::GetItemRect
- AFXEXT/CStatusBar::GetPaneInfo
- AFXEXT/CStatusBar::GetPaneStyle
- AFXEXT/CStatusBar::GetPaneText
- AFXEXT/CStatusBar::GetStatusBarCtrl
- AFXEXT/CStatusBar::SetIndicators
- AFXEXT/CStatusBar::SetPaneInfo
- AFXEXT/CStatusBar::SetPaneStyle
- AFXEXT/CStatusBar::SetPaneText
helpviewer_keywords:
- CStatusBar [MFC], CStatusBar
- CStatusBar [MFC], CommandToIndex
- CStatusBar [MFC], Create
- CStatusBar [MFC], CreateEx
- CStatusBar [MFC], DrawItem
- CStatusBar [MFC], GetItemID
- CStatusBar [MFC], GetItemRect
- CStatusBar [MFC], GetPaneInfo
- CStatusBar [MFC], GetPaneStyle
- CStatusBar [MFC], GetPaneText
- CStatusBar [MFC], GetStatusBarCtrl
- CStatusBar [MFC], SetIndicators
- CStatusBar [MFC], SetPaneInfo
- CStatusBar [MFC], SetPaneStyle
- CStatusBar [MFC], SetPaneText
ms.assetid: a3bde3db-e71c-4881-a3ca-1d5481c345ba
ms.openlocfilehash: 0549ee10faa15b80b18a0bee2f115425002e1479
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376258"
---
# <a name="cstatusbar-class"></a>Clase CStatusBar

Una barra de control con una fila de paneles de salida de texto o "indicadores".

## <a name="syntax"></a>Sintaxis

```
class CStatusBar : public CControlBar
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStatusBar::CStatusBar](#cstatusbar)|Construye un objeto `CStatusBar`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStatusBar::CommandToIndex](#commandtoindex)|Obtiene el índice de un ID de indicador determinado.|
|[CStatusBar::Crear](#create)|Crea la barra de estado, `CStatusBar` la adjunta al objeto y establece la fuente inicial y la altura de la barra.|
|[CStatusBar::CreateEx](#createex)|Crea `CStatusBar` un objeto con estilos `CStatusBarCtrl` adicionales para el objeto incrustado.|
|[CStatusBar::DrawItem](#drawitem)|Se llama cuando cambia un aspecto visual de un control de barra de estado de dibujo por el propietario.|
|[CStatusBar::GetItemID](#getitemid)|Obtiene el identificador del indicador para un índice determinado.|
|[CStatusBar::GetItemRect](#getitemrect)|Obtiene rectángulo de visualización para un índice determinado.|
|[CStatusBar::GetPaneInfo](#getpaneinfo)|Obtiene el identificador del indicador, el estilo y el ancho de un índice determinado.|
|[CStatusBar::GetPaneStyle](#getpanestyle)|Obtiene el estilo del indicador para un índice determinado.|
|[CStatusBar::GetPaneText](#getpanetext)|Obtiene el texto del indicador para un índice determinado.|
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|Permite el acceso directo al control común subyacente.|
|[CStatusBar::SetIndicators](#setindicators)|Establece los indicadores DE Identificación.|
|[CStatusBar::SetPaneInfo](#setpaneinfo)|Establece el ID del indicador, el estilo y el ancho de un índice determinado.|
|[CStatusBar::SetPaneStyle](#setpanestyle)|Establece el estilo del indicador para un índice determinado.|
|[CStatusBar::SetPaneText](#setpanetext)|Establece el texto del indicador para un índice determinado.|

## <a name="remarks"></a>Observaciones

Los paneles de salida se utilizan normalmente como líneas de mensaje y como indicadores de estado. Entre los ejemplos se incluyen las líneas de mensaje de ayuda del menú que explican brevemente el comando de menú seleccionado y los indicadores que muestran el estado del BLOQUEO SCROLL, BLOQUEO NUM y otras teclas.

[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl), una función miembro nueva en MFC 4.0, permite aprovechar la compatibilidad del control común de Windows para la personalización de la barra de estado y la funcionalidad adicional. `CStatusBar`Las funciones miembro proporcionan la mayor parte de la funcionalidad de los controles comunes de Windows; sin embargo, `GetStatusBarCtrl`cuando se llama , puede dar a sus barras de estado aún más de las características de una barra de estado de Windows 95/98. Cuando se `GetStatusBarCtrl`llama a , se `CStatusBarCtrl` devolverá una referencia a un objeto. Consulte [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) para obtener más información sobre el diseño de barras de herramientas mediante controles comunes de Windows. Para obtener más información general acerca de los controles comunes, vea [controles comunes](/windows/win32/Controls/common-controls-intro) en el Windows SDK.

El marco almacena la información del indicador en una matriz con el indicador más a la izquierda en la posición 0. Cuando se crea una barra de estado, se usa una matriz de id de cadena que el marco de trabajo asocia con los indicadores correspondientes. A continuación, puede utilizar un id de cadena o un índice para acceder a un indicador.

De forma predeterminada, el primer indicador es "elástico": ocupa la longitud de la barra de estado no utilizada por los otros paneles del indicador, por lo que los otros paneles están alineados a la derecha.

Para crear una barra de estado, siga estos pasos:

1. Construir `CStatusBar` el objeto.

1. Llame a la función [Create](#create) (o [CreateEx](#createex)) para `CStatusBar` crear la ventana de la barra de estado y adjuntarla al objeto.

1. Llame a [SetIndicators](#setindicators) para asociar un id de cadena con cada indicador.

Hay tres maneras de actualizar el texto en un panel de barra de estado:

1. Llame a [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) para actualizar el texto solo en el panel 0.

1. Llame a [CCmdUI::SetText](../../mfc/reference/ccmdui-class.md#settext) en el controlador de ON_UPDATE_COMMAND_UI de la barra de estado.

1. Llame a [SetPaneText](#setpanetext) para actualizar el texto de cualquier panel.

Llame a [SetPaneStyle](#setpanestyle) para actualizar el estilo de un panel de barra de estado.

Para obtener más `CStatusBar`información sobre el uso , vea el artículo [Implementación](../../mfc/status-bar-implementation-in-mfc.md) de la barra de estado en MFC y [Nota técnica 31 : Barras](../../mfc/tn031-control-bars.md)de control .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext.h

## <a name="cstatusbarcommandtoindex"></a><a name="commandtoindex"></a>CStatusBar::CommandToIndex

Obtiene el índice del indicador para un ID determinado.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parámetros

*nIDFind*<br/>
ID de cadena del indicador cuyo índice se va a recuperar.

### <a name="return-value"></a>Valor devuelto

El índice del indicador si se realiza correctamente; -1 si no se realiza correctamente.

### <a name="remarks"></a>Observaciones

El índice del primer indicador es 0.

## <a name="cstatusbarcreate"></a><a name="create"></a>CStatusBar::Crear

Crea una barra de estado (una ventana `CStatusBar` secundaria) y la asocia con el objeto.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Puntero al objeto [CWnd](../../mfc/reference/cwnd-class.md) cuya ventana de Windows es el elemento primario de la barra de estado.

*dwStyle*<br/>
El estilo de barra de estado. Además de los [estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles)estándar de Windows, se admiten estos estilos.

- CBRS_TOP barra de control está en la parte superior de la ventana del marco.

- CBRS_BOTTOM barra de control está en la parte inferior de la ventana del marco.

- CBRS_NOALIGN barra de control no se cambia de posición cuando se cambia el tamaño del elemento primario.

*nID*<br/>
Id. de ventana secundaria de la barra de herramientas.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

También establece la fuente inicial y establece la altura de la barra de estado en un valor predeterminado.

## <a name="cstatusbarcreateex"></a><a name="createex"></a>CStatusBar::CreateEx

Llame a esta función para crear una barra de `CStatusBar` estado (una ventana secundaria) y asociarla al objeto.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Puntero al objeto [CWnd](../../mfc/reference/cwnd-class.md) cuya ventana de Windows es el elemento primario de la barra de estado.

*dwCtrlStyle*<br/>
Estilos adicionales para la creación del objeto [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) incrustado. El valor predeterminado especifica una barra de estado sin un pinzamiento de tamaño o compatibilidad con información sobre herramientas. Los estilos de barra de estado admitidos son:

- SBARS_SIZEGRIP El control de barra de estado incluye un pinzamiento de tamaño en el extremo derecho de la barra de estado. Un pinzamiento de tamaño es similar a un borde de tamaño; es un área rectangular en la que el usuario puede hacer clic y arrastrar para cambiar el tamaño de la ventana principal.

- SBT_TOOLTIPS La barra de estado admite información sobre herramientas.

Para obtener más información sobre estos estilos, vea [Configuración de CStatusBarCtrl](../../mfc/settings-for-the-cstatusbarctrl.md).

*dwStyle*<br/>
El estilo de la barra de estado. El valor predeterminado especifica que se cree una barra de estado visible en la parte inferior de la ventana de marco. Aplique cualquier combinación de estilos de control de barra de estado enumerados en [Estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles) de ventana y [CDialogBar::Crear](../../mfc/reference/cdialogbar-class.md#create). Sin embargo, este parámetro siempre debe incluir los estilos WS_CHILD y WS_VISIBLE.

*nID*<br/>
Id. de ventana secundaria de la barra de estado.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función también establece la fuente inicial y establece la altura de la barra de estado en un valor predeterminado.

Usar `CreateEx`, en lugar de [Crear](#create), cuando ciertos estilos deben estar presentes durante la creación del control de barra de estado incrustado. Por ejemplo, establezca *dwCtrlStyle* en SBT_TOOLTIPS para mostrar información sobre herramientas en un objeto de barra de estado.

## <a name="cstatusbarcstatusbar"></a><a name="cstatusbar"></a>CStatusBar::CStatusBar

Construye un `CStatusBar` objeto, crea una fuente de barra de estado predeterminada si es necesario y establece las características de fuente en valores predeterminados.

```
CStatusBar();
```

## <a name="cstatusbardrawitem"></a><a name="drawitem"></a>CStatusBar::DrawItem

El marco de trabajo llama a esta función miembro cuando cambia un aspecto visual de una barra de estado dibujada por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Puntero a una estructura [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) que contiene información sobre el tipo de dibujo necesario.

### <a name="remarks"></a>Observaciones

El `itemAction` miembro `DRAWITEMSTRUCT` de la estructura define la acción de dibujo que se va a realizar. Invalidar esta función miembro para implementar `CStatusBar` el dibujo para un objeto de dibujo del propietario. La aplicación debe restaurar todos los objetos de interfaz de dispositivo gráfico (GDI) seleccionados para el contexto de visualización proporcionado en *lpDrawItemStruct* antes de la terminación de esta función miembro.

## <a name="cstatusbargetitemid"></a><a name="getitemid"></a>CStatusBar::GetItemID

Devuelve el identificador del indicador especificado por *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Indice del indicador cuyo ID se va a recuperar.

### <a name="return-value"></a>Valor devuelto

El identificador del indicador especificado por *nIndex*.

## <a name="cstatusbargetitemrect"></a><a name="getitemrect"></a>CStatusBar::GetItemRect

Copia las coordenadas del indicador especificado por *nIndex* en la estructura señalada por *lpRect*.

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Indice del indicador cuyas coordenadas rectangulares se van a recuperar.

*lpRect*<br/>
Apunta a una estructura [RECT](/previous-versions/dd162897\(v=vs.85\)) o a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) que recibirá las coordenadas del indicador especificado por *nIndex*.

### <a name="remarks"></a>Observaciones

Las coordenadas están en píxeles en relación con la esquina superior izquierda de la barra de estado.

## <a name="cstatusbargetpaneinfo"></a><a name="getpaneinfo"></a>CStatusBar::GetPaneInfo

Establece *nID*, *nStyle*y *cxWidth* en el identificador, estilo y ancho del panel del indicador en la ubicación especificada por *nIndex*.

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Indice del panel cuya información se va a recuperar.

*nID*<br/>
Referencia a un UINT que se establece en el identificador del panel.

*nStyle*<br/>
Referencia a un UINT que se establece en el estilo del panel.

*cxWidth*<br/>
Referencia a un entero que se establece en el ancho del panel.

## <a name="cstatusbargetpanestyle"></a><a name="getpanestyle"></a>CStatusBar::GetPaneStyle

Llame a esta función miembro para recuperar el estilo del panel de una barra de estado.

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Indice del panel cuyo estilo se va a recuperar.

### <a name="return-value"></a>Valor devuelto

El estilo del panel de barra de estado especificado por *nIndex*.

### <a name="remarks"></a>Observaciones

El estilo de un panel determina cómo aparece el panel.

Para obtener una lista de los estilos disponibles para las barras de estado, consulte [Crear](#create).

## <a name="cstatusbargetpanetext"></a><a name="getpanetext"></a>CStatusBar::GetPaneText

Llame a esta función miembro para recuperar el texto que aparece en un panel de barra de estado.

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Indice del panel cuyo texto se va a recuperar.

*rString*<br/>
Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el texto que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

Objeto `CString` que contiene el texto del panel.

### <a name="remarks"></a>Observaciones

La segunda forma de esta `CString` función miembro rellena un objeto con el texto de cadena.

## <a name="cstatusbargetstatusbarctrl"></a><a name="getstatusbarctrl"></a>CStatusBar::GetStatusBarCtrl

Esta función miembro permite el acceso directo al control común subyacente.

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

Contiene una referencia a un [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) objeto.

### <a name="remarks"></a>Observaciones

Se `GetStatusBarCtrl` usa para aprovechar la funcionalidad del control común de la barra de estado de Windows y para aprovechar la compatibilidad [que CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) proporciona para la personalización de la barra de estado. Por ejemplo, mediante el control común, puede especificar un estilo que incluya un pinzamiento de tamaño en la barra de estado, o puede especificar un estilo para que la barra de estado aparezca en la parte superior del área de cliente de la ventana primaria.

Para obtener más información general acerca de los controles comunes, vea [controles comunes](/windows/win32/Controls/common-controls-intro) en el Windows SDK.

## <a name="cstatusbarsetindicators"></a><a name="setindicators"></a>CStatusBar::SetIndicators

Establece el ID de cada indicador en el valor especificado por el elemento correspondiente de la matriz *lpIDArray*, carga el recurso de cadena especificado por cada ID y establece el texto del indicador en la cadena.

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parámetros

*lpIDArray*<br/>
Puntero a una matriz de iDe.

*nIDCount*<br/>
Número de elementos de la matriz a los que apunta *lpIDArray*.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

## <a name="cstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a>CStatusBar::SetPaneInfo

Establece el panel del indicador especificado en un nuevo identificador, estilo y ancho.

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Indice del panel del indicador cuyo estilo se va a establecer.

*nID*<br/>
Nuevo ID para el panel del indicador.

*nStyle*<br/>
Nuevo estilo para el panel del indicador.

*cxWidth*<br/>
Nuevo ancho para el panel del indicador.

### <a name="remarks"></a>Observaciones

Se admiten los siguientes estilos de indicador:

- SBPS_NOBORDERS No hay borde 3D alrededor del panel.

- SBPS_POPOUT borde inverso para que el texto "salga".

- SBPS_DISABLED No dibujar texto.

- SBPS_STRETCH panel Estirar para rellenar el espacio no utilizado. Solo un panel por barra de estado puede tener este estilo.

- SBPS_NORMAL Sin estiramiento, bordes o ventanas emergentes.

## <a name="cstatusbarsetpanestyle"></a><a name="setpanestyle"></a>CStatusBar::SetPaneStyle

Llame a esta función miembro para establecer el estilo del panel de una barra de estado.

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Indice del panel cuyo estilo se va a establecer.

*nStyle*<br/>
Estilo del panel cuyo estilo se va a establecer.

### <a name="remarks"></a>Observaciones

El estilo de un panel determina cómo aparece el panel.

Para obtener una lista de estilos disponibles para las barras de estado, vea [SetPaneInfo](#setpaneinfo).

## <a name="cstatusbarsetpanetext"></a><a name="setpanetext"></a>CStatusBar::SetPaneText

Llame a esta función miembro para establecer el texto del panel en la cadena señalada por *lpszNewText*.

```
BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Indice del panel cuyo texto se va a establecer.

*lpszNewText*<br/>
Puntero al nuevo texto del panel.

*bActualización*<br/>
Si es TRUE, el panel se invalida después de establecer el texto.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Después `SetPaneText`de llamar a , debe agregar un controlador de actualización de interfaz de usuario para mostrar el nuevo texto en la barra de estado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>Consulte también

[CTRLBARS de ejemplo de MFC](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CStatusBarCtrl (clase)](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)
