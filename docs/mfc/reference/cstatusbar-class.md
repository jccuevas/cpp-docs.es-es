---
title: CStatusBar (clase)
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
ms.openlocfilehash: d714159aa9fd52df682b1e5f3dbf3957bbef1b91
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "58777342"
---
# <a name="cstatusbar-class"></a>CStatusBar (clase)

Una barra de control con una fila de paneles de salida de texto o "indicadores".

## <a name="syntax"></a>Sintaxis

```
class CStatusBar : public CControlBar
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CStatusBar::CStatusBar](#cstatusbar)|Construye un objeto `CStatusBar`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CStatusBar::CommandToIndex](#commandtoindex)|Obtiene el índice para un identificador determinado indicador.|
|[CStatusBar::Create](#create)|Crea la barra de estado, que se conecta a la `CStatusBar` de objetos y establece el alto de fuente y barra inicial.|
|[CStatusBar::CreateEx](#createex)|Crea un `CStatusBar` objeto estilos adicionales para el objeto incrustado `CStatusBarCtrl` objeto.|
|[CStatusBar::DrawItem](#drawitem)|Se llama cuando un aspecto visual de un cambios de control dibujado por el propietario de la barra de estado.|
|[CStatusBar::GetItemID](#getitemid)|Obtiene el identificador de indicador de un índice determinado.|
|[CStatusBar::GetItemRect](#getitemrect)|Obtiene mostrar el rectángulo de un índice determinado.|
|[CStatusBar::GetPaneInfo](#getpaneinfo)|Obtiene el Id. de indicador, estilo y ancho de un índice determinado.|
|[CStatusBar::GetPaneStyle](#getpanestyle)|Obtiene el estilo de indicador para un índice determinado.|
|[CStatusBar::GetPaneText](#getpanetext)|Obtiene el texto de indicador para un índice determinado.|
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|Permite el acceso directo al control subyacente común.|
|[CStatusBar::SetIndicators](#setindicators)|Establece los identificadores de indicador.|
|[CStatusBar::SetPaneInfo](#setpaneinfo)|Identificador de conjuntos de indicadores, estilo y ancho de un índice determinado.|
|[CStatusBar::SetPaneStyle](#setpanestyle)|Establece el estilo del indicador de un índice determinado.|
|[CStatusBar::SetPaneText](#setpanetext)|Establece el texto del indicador de un índice determinado.|

## <a name="remarks"></a>Comentarios

Los paneles de resultados se usan habitualmente como líneas de mensaje y como indicadores de estado. Algunos ejemplos son las líneas de mensaje de Ayuda de menú que se describe brevemente el comando de menú seleccionado y los indicadores que muestran el estado de otras claves, BLOQ NUM y Bloq Despl.

[CStatusBar:: GetStatusBarCtrl](#getstatusbarctrl), una función miembro nuevo a 4.0 de MFC, le permite aprovechar las ventajas de soporte técnico del control común de Windows para la barra de estado personalización y funcionalidad adicional. `CStatusBar` las funciones miembro proporcionan la mayoría de la funcionalidad de los controles comunes de Windows; Sin embargo, cuando se llama a `GetStatusBarCtrl`, puedes usar las barras de estado aún más las características de una barra de estado de Windows 95 ó 98. Cuando se llama a `GetStatusBarCtrl`, devolverá una referencia a un `CStatusBarCtrl` objeto. Consulte [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) para obtener más información sobre el diseño de las barras de herramientas con los controles comunes de Windows. Para obtener información general sobre los controles comunes, consulte [controles comunes](/windows/desktop/Controls/common-controls-intro) en el SDK de Windows.

El marco de trabajo almacena información de indicador en una matriz con el indicador situado en la posición 0. Cuando se crea una barra de estado, use una matriz de identificadores que el marco de trabajo se asocia a los indicadores correspondientes de cadena. A continuación, puede usar un identificador de cadena o un índice para tener acceso a un indicador.

De forma predeterminada, el primer indicador es "elastic": se tarda hasta la longitud de la barra de estado no utilizada por los paneles de indicadores, para que los otros paneles están alineados a la derecha.

Para crear una barra de estado, siga estos pasos:

1. Construir la `CStatusBar` objeto.

1. Llame a la [crear](#create) (o [CreateEx](#createex)) función para crear la ventana de la barra de estado y adjuntarlo a la `CStatusBar` objeto.

1. Llame a [SetIndicators](#setindicators) para asociar un identificador de cadena de cada indicador.

Hay tres maneras de actualizar el texto en un panel de barra de estado:

1. Llame a [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) para actualizar el texto en el panel 0.

1. Llame a [CCmdUI::SetText](../../mfc/reference/ccmdui-class.md#settext) en el controlador de la barra de estado ON_UPDATE_COMMAND_UI.

1. Llame a [denominada SetPaneText](#setpanetext) para actualizar el texto para cualquier panel.

Llame a [SetPaneStyle](#setpanestyle) para actualizar el estilo de un panel de barra de estado.

Para obtener más información sobre el uso de `CStatusBar`, consulte el artículo [implementación de la barra de estado en MFC](../../mfc/status-bar-implementation-in-mfc.md) y [Nota técnica 31: Barras de control](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext.h

##  <a name="commandtoindex"></a>  CStatusBar::CommandToIndex

Obtiene el índice de indicador para un identificador determinado.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parámetros

*nIDFind*<br/>
Identificador de cadena del indicador es cuyo índice va a recuperar.

### <a name="return-value"></a>Valor devuelto

El índice del indicador de si se realiza correctamente; -1 si no funciona correctamente.

### <a name="remarks"></a>Comentarios

El índice del primer indicador es 0.

##  <a name="create"></a>  CStatusBar::Create

Crea un estado de la barra (una ventana secundaria) y lo asocia a la `CStatusBar` objeto.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Puntero a la [CWnd](../../mfc/reference/cwnd-class.md) objeto cuya ventana de Windows es el elemento primario de la barra de estado.

*dwStyle*<br/>
El estilo de barra de estado. Además de la Windows estándar [estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles), se admiten estos estilos.

- Barra de Control de CBRS_TOP está en la parte superior de la ventana de marco.

- Barra de Control CBRS_BOTTOM es en parte inferior de la ventana de marco.

- Barra de Control CBRS_NOALIGN no se cambia de posición cuando se cambia el tamaño del elemento primario.

*nID*<br/>
Identificador de ventana secundaria de. la barra de herramientas

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

También establece la fuente inicial y establece el estado de alto de la barra en un valor predeterminado.

##  <a name="createex"></a>  CStatusBar::CreateEx

Llame a esta función para crear un estado de la barra (una ventana secundaria) y asócielo con el `CStatusBar` objeto.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Puntero a la [CWnd](../../mfc/reference/cwnd-class.md) objeto cuya ventana de Windows es el elemento primario de la barra de estado.

*dwCtrlStyle*<br/>
Estilos adicionales para la creación de los datos incrustados [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) objeto. El valor predeterminado especifica una barra de estado sin un control de tamaño o la información sobre herramientas admiten. Estilos de barra de estado admitidos son:

- El control de barra de estado SBARS_SIZEGRIP incluye un control de tamaño en el extremo derecho de la barra de estado. Un control de tamaño es similar a un borde de tamaño; es un área rectangular que el usuario hacer clic y arrastre para cambiar el tamaño de la ventana primaria.

- SBT_TOOLTIPS la barra de estado es compatible con la información sobre herramientas.

Para obtener más información acerca de estos estilos, consulte [configuración de CStatusBarCtrl](../../mfc/settings-for-the-cstatusbarctrl.md).

*dwStyle*<br/>
El estilo de barra de estado. El valor predeterminado especifica que se ha creado una barra de estado visible en la parte inferior de la ventana de marco. Aplicar cualquier combinación de los estilos de control que aparece en la barra de estado [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) y [CDialogBar::Create](../../mfc/reference/cdialogbar-class.md#create). Sin embargo, este parámetro siempre debe incluir los estilos WS_CHILD y WS_VISIBLE.

*nID*<br/>
Identificador de ventana secundaria de la barra de estado.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función también establece la fuente inicial y establece el estado de alto de la barra en un valor predeterminado.

Use `CreateEx`, en lugar de [crear](#create), cuando necesitan estar presente durante la creación del control de barra de estado incrustada determinados estilos. Por ejemplo, establecer *dwCtrlStyle* a SBT_TOOLTIPS para mostrar información sobre herramientas en un objeto de barra de estado.

##  <a name="cstatusbar"></a>  CStatusBar::CStatusBar

Construye un `CStatusBar` objeto, crea una fuente de barra de estado de forma predeterminada, si es necesario y establece las características de fuente para los valores predeterminados.

```
CStatusBar();
```

##  <a name="drawitem"></a>  CStatusBar::DrawItem

Esta función miembro se llama el marco de trabajo cuando un aspecto visual de una barra de estado dibujada por cambia.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Un puntero a un [DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) estructura que contiene información sobre el tipo de dibujo necesaria.

### <a name="remarks"></a>Comentarios

El `itemAction` miembro de la `DRAWITEMSTRUCT` estructura define la acción de dibujo que se realiza. Reemplace esta función miembro para implementar un dibujado por el propietario del dibujo `CStatusBar` objeto. La aplicación debe restaurar todos los objetos de interfaz (GDI) de dispositivo de gráficos seleccionados para proporciona el contexto de presentación en *lpDrawItemStruct* antes de la finalización de esta función miembro.

##  <a name="getitemid"></a>  CStatusBar::GetItemID

Devuelve el identificador del indicador especificado por *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del indicador cuyo identificador es va a recuperar.

### <a name="return-value"></a>Valor devuelto

El identificador del indicador especificado por *nIndex*.

##  <a name="getitemrect"></a>  CStatusBar::GetItemRect

Copia las coordenadas del indicador especificado por *nIndex* en la estructura que señala *lpRect*.

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del indicador son cuyas coordenadas del rectángulo va a recuperar.

*lpRect*<br/>
Apunta a un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura o un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que recibirá las coordenadas del indicador especificado por *nIndex*.

### <a name="remarks"></a>Comentarios

Las coordenadas están en píxeles con respecto a la esquina superior izquierda de la barra de estado.

##  <a name="getpaneinfo"></a>  CStatusBar::GetPaneInfo

Conjuntos de *nID*, *nStyle*, y *cxWidth* para el Id., estilo y ancho del panel de indicador en la ubicación especificada por *nIndex*.

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del panel es cuya información va a recuperar.

*nID*<br/>
Referencia a un tipo UINT que se establece en el identificador del panel.

*nStyle*<br/>
Referencia a un tipo UINT que se establece en el estilo del panel.

*cxWidth*<br/>
Referencia a un entero que se establece el ancho del panel.

##  <a name="getpanestyle"></a>  CStatusBar::GetPaneStyle

Llame a esta función miembro para recuperar el estilo del panel de la barra de estado.

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del panel cuyo estilo es va a recuperar.

### <a name="return-value"></a>Valor devuelto

El estilo del panel de barra de estado especificado por *nIndex*.

### <a name="remarks"></a>Comentarios

Estilo de un panel determina cómo aparece el panel.

Para obtener una lista de estilos disponibles para las barras de estado, vea [crear](#create).

##  <a name="getpanetext"></a>  CStatusBar::GetPaneText

Llame a esta función miembro para recuperar el texto que aparece en un panel de barra de estado.

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del panel cuyo texto está va a recuperar.

*rString*<br/>
Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el texto que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

Un `CString` objeto que contiene el texto del panel.

### <a name="remarks"></a>Comentarios

La segunda forma de este miembro de función se llena un `CString` objeto con el texto de cadena.

##  <a name="getstatusbarctrl"></a>  CStatusBar::GetStatusBarCtrl

Esta función miembro permite el acceso directo al control subyacente común.

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

Contiene una referencia a un [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) objeto.

### <a name="remarks"></a>Comentarios

Use `GetStatusBarCtrl` para aprovechar la funcionalidad del control común de barra de estado de Windows y para aprovechar la compatibilidad con [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) proporciona para la personalización de la barra de estado. Por ejemplo, mediante el control común, puede especificar un estilo que incluye un control de tamaño en la barra de estado, o puede especificar un estilo para que la barra de estado aparecen en la parte superior del área de cliente de la ventana primaria.

Para obtener información general sobre los controles comunes, consulte [controles comunes](/windows/desktop/Controls/common-controls-intro) en el SDK de Windows.

##  <a name="setindicators"></a>  CStatusBar::SetIndicators

Id. de cada indicador se establece en el valor especificado por el elemento correspondiente de la matriz *lpIDArray*, carga el recurso de cadena especificado por cada identificador y establece el texto del indicador en la cadena.

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parámetros

*lpIDArray*<br/>
Puntero a una matriz de identificadores.

*nIDCount*<br/>
Número de elementos de la matriz señalada por *lpIDArray*.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

##  <a name="setpaneinfo"></a>  CStatusBar::SetPaneInfo

El panel de indicador especificado se establece en un nuevo identificador, estilo y ancho.

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del panel de indicador cuyo estilo se va a establecer.

*nID*<br/>
Nuevo identificador para el panel de indicador.

*nStyle*<br/>
Nuevo estilo para el panel de indicador.

*cxWidth*<br/>
Nuevo ancho del panel de indicador.

### <a name="remarks"></a>Comentarios

Se admiten los siguientes estilos de indicador:

- Borde 3D de SBPS_NOBORDERS No alrededor del panel.

- Invertir SBPS_POPOUT de borde para que el texto "Emerge."

- No se SBPS_DISABLED hacer dibujar texto.

- Panel SBPS_STRETCH Stretch para rellenar el espacio no utilizado. Un solo panel por la barra de estado puede tener este estilo.

- Stretch No SBPS_NORMAL, bordes o emergente.

##  <a name="setpanestyle"></a>  CStatusBar::SetPaneStyle

Llame a esta función miembro para establecer el estilo del panel de la barra de estado.

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del panel cuyo estilo se va a establecer.

*nStyle*<br/>
Estilo del panel cuyo estilo se va a establecer.

### <a name="remarks"></a>Comentarios

Estilo de un panel determina cómo aparece el panel.

Para obtener una lista de estilos disponibles para las barras de estado, vea [SetPaneInfo](#setpaneinfo).

##  <a name="setpanetext"></a>  CStatusBar::SetPaneText

Llame a esta función miembro para establecer el texto del panel en la cadena señalada por *lpszNewText*.

```
BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del panel cuyo texto se va a establecer.

*lpszNewText*<br/>
Puntero en el nuevo texto del panel.

*bActualización*<br/>
Si es TRUE, se invalida el panel después de establece el texto.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Después de llamar a `SetPaneText`, debe agregar un controlador de actualización de la interfaz de usuario para mostrar el nuevo texto en la barra de estado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>Vea también

[CTRLBARS de ejemplo](../../overview/visual-cpp-samples.md)<br/>
[DLGCBR32 de ejemplo MFC](../../overview/visual-cpp-samples.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CStatusBarCtrl (clase)](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)
