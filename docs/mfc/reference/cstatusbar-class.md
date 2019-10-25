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
ms.openlocfilehash: 48de31d95814ce5fc1fb015e69cf38d73337cb79
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502334"
---
# <a name="cstatusbar-class"></a>CStatusBar (clase)

Una barra de control con una fila de paneles de salida de texto o "indicadores".

## <a name="syntax"></a>Sintaxis

```
class CStatusBar : public CControlBar
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CStatusBar::CStatusBar](#cstatusbar)|Construye un objeto `CStatusBar`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CStatusBar::CommandToIndex](#commandtoindex)|Obtiene el índice de un identificador de indicador determinado.|
|[CStatusBar::Create](#create)|Crea la barra de estado, la adjunta al `CStatusBar` objeto y establece la fuente inicial y el alto de la barra.|
|[CStatusBar::CreateEx](#createex)|Crea un `CStatusBar` objeto con estilos adicionales para el objeto `CStatusBarCtrl` incrustado.|
|[CStatusBar::DrawItem](#drawitem)|Se le llama cuando cambia el aspecto visual de un control de barra de estado de dibujo del propietario.|
|[CStatusBar::GetItemID](#getitemid)|Obtiene el identificador de indicador para un índice determinado.|
|[CStatusBar::GetItemRect](#getitemrect)|Obtiene el rectángulo de presentación de un índice determinado.|
|[CStatusBar::GetPaneInfo](#getpaneinfo)|Obtiene el identificador de indicador, el estilo y el ancho de un índice determinado.|
|[CStatusBar::GetPaneStyle](#getpanestyle)|Obtiene el estilo de indicador para un índice determinado.|
|[CStatusBar::GetPaneText](#getpanetext)|Obtiene el texto del indicador para un índice determinado.|
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|Permite el acceso directo al control común subyacente.|
|[CStatusBar::SetIndicators](#setindicators)|Establece los identificadores de los indicadores.|
|[CStatusBar::SetPaneInfo](#setpaneinfo)|Establece el identificador de indicador, el estilo y el ancho de un índice determinado.|
|[CStatusBar::SetPaneStyle](#setpanestyle)|Establece el estilo de indicador para un índice determinado.|
|[CStatusBar::SetPaneText](#setpanetext)|Establece el texto del indicador para un índice determinado.|

## <a name="remarks"></a>Comentarios

Los paneles de salida suelen usarse como líneas de mensaje y como indicadores de estado. Entre los ejemplos se incluyen las líneas de mensajes de ayuda de menú que explican brevemente el comando de menú seleccionado y los indicadores que muestran el estado de Bloq Despl, BLOQ NUM y otras claves.

[CStatusBar:: GetStatusBarCtrl](#getstatusbarctrl), una función miembro nueva de MFC 4,0, le permite aprovechar la compatibilidad del control común de Windows con la personalización de la barra de estado y la funcionalidad adicional. `CStatusBar`las funciones miembro proporcionan la mayor parte de la funcionalidad de los controles comunes de Windows; sin embargo, al llamar `GetStatusBarCtrl`a, puede proporcionar a sus barras de estado incluso más características de una barra de estado de Windows 95/98. Cuando llame `GetStatusBarCtrl`a, devolverá una referencia a un `CStatusBarCtrl` objeto. Vea [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) para obtener más información sobre el diseño de barras de herramientas mediante controles comunes de Windows. Para obtener más información general sobre los controles comunes, vea [controles comunes](/windows/win32/Controls/common-controls-intro) en el Windows SDK.

El marco de trabajo almacena información de indicadores en una matriz con el indicador situado más a la izquierda en la posición 0. Al crear una barra de estado, se usa una matriz de identificadores de cadena que el marco de trabajo asocia a los indicadores correspondientes. Después, puede usar un identificador de cadena o un índice para tener acceso a un indicador.

De forma predeterminada, el primer indicador es "elástico": toma la longitud de la barra de estado no usada por los demás paneles del indicador, de modo que los demás paneles estén alineados a la derecha.

Para crear una barra de estado, siga estos pasos:

1. Construya el `CStatusBar` objeto.

1. Llame a la función [Create](#create) (o [CreateEx](#createex)) para crear la ventana de la barra de estado y adjuntarla al `CStatusBar` objeto.

1. Llame a [SetIndicators](#setindicators) para asociar un identificador de cadena a cada indicador.

Hay tres maneras de actualizar el texto en un panel de barra de estado:

1. Llame a [CWnd:: SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) para actualizar el texto solo en el panel 0.

1. Llame a [CCmdUI:: setText](../../mfc/reference/ccmdui-class.md#settext) en el controlador ON_UPDATE_COMMAND_UI de la barra de estado.

1. Llame a [SetPaneText](#setpanetext) para actualizar el texto de cualquier panel.

Llame a [SetPaneStyle](#setpanestyle) para actualizar el estilo de un panel de barra de estado.

Para obtener más información sobre `CStatusBar`el uso de, vea el artículo [implementación de la barra de estado en MFC](../../mfc/status-bar-implementation-in-mfc.md) y [Nota técnica 31: Barras](../../mfc/tn031-control-bars.md)de control.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext. h

##  <a name="commandtoindex"></a>  CStatusBar::CommandToIndex

Obtiene el índice del indicador para un identificador determinado.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parámetros

*nIDFind*<br/>
IDENTIFICADOR de cadena del indicador cuyo índice se va a recuperar.

### <a name="return-value"></a>Valor devuelto

Índice del indicador si es correcto; -1 si no se realiza correctamente.

### <a name="remarks"></a>Comentarios

El índice del primer indicador es 0.

##  <a name="create"></a>  CStatusBar::Create

Crea una barra de estado (una ventana secundaria) y la asocia al `CStatusBar` objeto.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Puntero al objeto [CWnd](../../mfc/reference/cwnd-class.md) cuya ventana de Windows es la primaria de la barra de estado.

*dwStyle*<br/>
Estilo de la barra de estado. Además de los [estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles)estándar de Windows, se admiten estos estilos.

- La barra de control CBRS_TOP se encuentra en la parte superior de la ventana marco.

- La barra de control CBRS_BOTTOM está en la parte inferior de la ventana de marco.

- La barra de control CBRS_NOALIGN no se recoloca cuando se cambia el tamaño del elemento primario.

*nID*<br/>
IDENTIFICADOR de la ventana secundaria de la barra de herramientas.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

También establece la fuente inicial y establece el alto de la barra de estado en un valor predeterminado.

##  <a name="createex"></a>  CStatusBar::CreateEx

Llame a esta función para crear una barra de estado (una ventana secundaria) y asociarla `CStatusBar` al objeto.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Puntero al objeto [CWnd](../../mfc/reference/cwnd-class.md) cuya ventana de Windows es la primaria de la barra de estado.

*dwCtrlStyle*<br/>
Estilos adicionales para la creación del objeto [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) incrustado. El valor predeterminado especifica una barra de estado sin compatibilidad con el control de tamaño o la información sobre herramientas. Los estilos de barra de estado admitidos son:

- SBARS_SIZEGRIP el control de barra de estado incluye un control de tamaño en el extremo derecho de la barra de estado. Un control de tamaño es similar a un borde de tamaño; es un área rectangular en la que el usuario puede hacer clic y arrastrar para cambiar el tamaño de la ventana primaria.

- SBT_TOOLTIPS la barra de estado admite información sobre herramientas.

Para obtener más información sobre estos estilos, vea [la configuración de CStatusBarCtrl](../../mfc/settings-for-the-cstatusbarctrl.md).

*dwStyle*<br/>
Estilo de la barra de estado. El valor predeterminado especifica que se cree una barra de estado visible en la parte inferior de la ventana de marco. Aplique cualquier combinación de estilos de control de barra de estado enumerada en [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) y [CDialogBar:: Create](../../mfc/reference/cdialogbar-class.md#create). Sin embargo, este parámetro siempre debe incluir los estilos WS_CHILD y WS_VISIBLE.

*nID*<br/>
IDENTIFICADOR de la ventana secundaria de la barra de estado.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función también establece la fuente inicial y establece el alto de la barra de estado en un valor predeterminado.

Use `CreateEx`, en lugar de [crear](#create), cuando determinados estilos deban estar presentes durante la creación del control de barra de estado incrustado. Por ejemplo, establezca *dwCtrlStyle* en SBT_TOOLTIPS para mostrar la información sobre herramientas en un objeto de barra de estado.

##  <a name="cstatusbar"></a>  CStatusBar::CStatusBar

Construye un `CStatusBar` objeto, crea una fuente de la barra de estado predeterminada si es necesario y establece las características de la fuente en los valores predeterminados.

```
CStatusBar();
```

##  <a name="drawitem"></a>  CStatusBar::DrawItem

El marco de trabajo llama a esta función miembro cuando cambia el aspecto visual de una barra de estado dibujada por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Puntero a una estructura [drawitemstruct (](/windows/win32/api/winuser/ns-winuser-drawitemstruct) que contiene información sobre el tipo de dibujo necesario.

### <a name="remarks"></a>Comentarios

El `itemAction` miembro de la `DRAWITEMSTRUCT` estructura define la acción de dibujo que se va a realizar. Invalide esta función miembro para implementar el dibujo de un `CStatusBar` objeto dibujado por el propietario. La aplicación debe restaurar todos los objetos de la interfaz de dispositivo gráfico (GDI) seleccionados para el contexto de presentación proporcionado en *lpDrawItemStruct* antes de la finalización de esta función miembro.

##  <a name="getitemid"></a>  CStatusBar::GetItemID

Devuelve el identificador del indicador especificado por *NINDEX*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del indicador cuyo identificador se va a recuperar.

### <a name="return-value"></a>Valor devuelto

IDENTIFICADOR del indicador especificado por *NINDEX*.

##  <a name="getitemrect"></a>  CStatusBar::GetItemRect

Copia las coordenadas del indicador especificado por *NINDEX* en la estructura a la que apunta *lpRect*.

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del indicador cuyas coordenadas del rectángulo se van a recuperar.

*lpRect*<br/>
Apunta a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) o a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) que recibirá las coordenadas del indicador especificado por *NINDEX*.

### <a name="remarks"></a>Comentarios

Las coordenadas están en píxeles en relación con la esquina superior izquierda de la barra de estado.

##  <a name="getpaneinfo"></a>  CStatusBar::GetPaneInfo

Establece *nID*, *nStyle*y *cxWidth* en el identificador, el estilo y el ancho del panel de indicadores en la ubicación especificada por *NINDEX*.

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del panel cuya información se va a recuperar.

*nID*<br/>
Referencia a un valor UINT que se establece en el identificador del panel.

*nStyle*<br/>
Referencia a un valor UINT que se establece en el estilo del panel.

*cxWidth*<br/>
Referencia a un entero que se establece en el ancho del panel.

##  <a name="getpanestyle"></a>  CStatusBar::GetPaneStyle

Llame a esta función miembro para recuperar el estilo del panel de la barra de estado.

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del panel cuyo estilo se va a recuperar.

### <a name="return-value"></a>Valor devuelto

Estilo del panel de la barra de estado especificado por *NINDEX*.

### <a name="remarks"></a>Comentarios

El estilo de un panel determina cómo se muestra el panel.

Para obtener una lista de los estilos disponibles para las barras de estado, consulte [Create](#create).

##  <a name="getpanetext"></a>  CStatusBar::GetPaneText

Llame a esta función miembro para recuperar el texto que aparece en un panel de la barra de estado.

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del panel cuyo texto se va a recuperar.

*rString*<br/>
Referencia a un objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene el texto que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

`CString` Objeto que contiene el texto del panel.

### <a name="remarks"></a>Comentarios

La segunda forma de esta función miembro rellena un `CString` objeto con el texto de la cadena.

##  <a name="getstatusbarctrl"></a>  CStatusBar::GetStatusBarCtrl

Esta función miembro permite el acceso directo al control común subyacente.

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

Contiene una referencia a un objeto [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) .

### <a name="remarks"></a>Comentarios

Utilice `GetStatusBarCtrl` para aprovechar las ventajas de la funcionalidad del control común de la barra de estado de Windows y para aprovechar las ventajas de [la compatibilidad de](../../mfc/reference/cstatusbarctrl-class.md) con la personalización de la barra de estado. Por ejemplo, mediante el control común, puede especificar un estilo que incluya un control de tamaño en la barra de estado, o puede especificar un estilo para que la barra de estado aparezca en la parte superior del área de cliente de la ventana primaria.

Para obtener más información general sobre los controles comunes, vea [controles comunes](/windows/win32/Controls/common-controls-intro) en el Windows SDK.

##  <a name="setindicators"></a>  CStatusBar::SetIndicators

Establece el identificador de cada indicador en el valor especificado por el elemento correspondiente de la matriz *lpIDArray*, carga el recurso de cadena especificado por cada identificador y establece el texto del indicador en la cadena.

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parámetros

*lpIDArray*<br/>
Puntero a una matriz de identificadores.

*nIDCount*<br/>
Número de elementos de la matriz a los que apunta *lpIDArray*.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

##  <a name="setpaneinfo"></a>  CStatusBar::SetPaneInfo

Establece el panel indicador especificado en un nuevo identificador, estilo y ancho.

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del panel indicador cuyo estilo se va a establecer.

*nID*<br/>
Nuevo identificador del panel de indicadores.

*nStyle*<br/>
Nuevo estilo para el panel de indicadores.

*cxWidth*<br/>
Nuevo ancho para el panel de indicadores.

### <a name="remarks"></a>Comentarios

Se admiten los siguientes estilos de indicador:

- SBPS_NOBORDERS: no hay borde 3D alrededor del panel.

- SBPS_POPOUT borde inverso para que el texto "emerge".

- SBPS_DISABLED no dibuja texto.

- SBPS_STRETCH para rellenar el espacio no utilizado. Solo un panel por barra de estado puede tener este estilo.

- SBPS_NORMAL no expanda, bordes ni elemento emergente.

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

El estilo de un panel determina cómo se muestra el panel.

Para obtener una lista de los estilos disponibles para las barras de estado, vea [SetPaneInfo](#setpaneinfo).

##  <a name="setpanetext"></a>  CStatusBar::SetPaneText

Llame a esta función miembro para establecer el texto del panel en la cadena a la que apunta *lpszNewText*.

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
Puntero al nuevo texto del panel.

*bUpdate*<br/>
Si es TRUE, el panel se invalida después de establecer el texto.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Después de llamar `SetPaneText`a, debe agregar un controlador de actualización de la interfaz de usuario para mostrar el nuevo texto en la barra de estado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo de MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CStatusBarCtrl (clase)](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)
