---
title: CToolBar (clase)
ms.date: 11/04/2016
f1_keywords:
- CToolBar
- AFXEXT/CToolBar
- AFXEXT/CToolBar::CToolBar
- AFXEXT/CToolBar::CommandToIndex
- AFXEXT/CToolBar::Create
- AFXEXT/CToolBar::CreateEx
- AFXEXT/CToolBar::GetButtonInfo
- AFXEXT/CToolBar::GetButtonStyle
- AFXEXT/CToolBar::GetButtonText
- AFXEXT/CToolBar::GetItemID
- AFXEXT/CToolBar::GetItemRect
- AFXEXT/CToolBar::GetToolBarCtrl
- AFXEXT/CToolBar::LoadBitmap
- AFXEXT/CToolBar::LoadToolBar
- AFXEXT/CToolBar::SetBitmap
- AFXEXT/CToolBar::SetButtonInfo
- AFXEXT/CToolBar::SetButtons
- AFXEXT/CToolBar::SetButtonStyle
- AFXEXT/CToolBar::SetButtonText
- AFXEXT/CToolBar::SetHeight
- AFXEXT/CToolBar::SetSizes
helpviewer_keywords:
- CToolBar [MFC], CToolBar
- CToolBar [MFC], CommandToIndex
- CToolBar [MFC], Create
- CToolBar [MFC], CreateEx
- CToolBar [MFC], GetButtonInfo
- CToolBar [MFC], GetButtonStyle
- CToolBar [MFC], GetButtonText
- CToolBar [MFC], GetItemID
- CToolBar [MFC], GetItemRect
- CToolBar [MFC], GetToolBarCtrl
- CToolBar [MFC], LoadBitmap
- CToolBar [MFC], LoadToolBar
- CToolBar [MFC], SetBitmap
- CToolBar [MFC], SetButtonInfo
- CToolBar [MFC], SetButtons
- CToolBar [MFC], SetButtonStyle
- CToolBar [MFC], SetButtonText
- CToolBar [MFC], SetHeight
- CToolBar [MFC], SetSizes
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
ms.openlocfilehash: 4977cbe0b749724f999d6d7089d46f12d1e2963e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502391"
---
# <a name="ctoolbar-class"></a>CToolBar (clase)

Barras de control que tienen una fila de botones de mapas de bits y separadores opcionales.

## <a name="syntax"></a>Sintaxis

```
class CToolBar : public CControlBar
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CToolBar::CToolBar](#ctoolbar)|Construye un objeto `CToolBar`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CToolBar::CommandToIndex](#commandtoindex)|Devuelve el índice de un botón con el identificador de comando especificado.|
|[CToolBar::Create](#create)|Crea la barra de herramientas de Windows y la `CToolBar` adjunta al objeto.|
|[CToolBar::CreateEx](#createex)|Crea un `CToolBar` objeto con estilos adicionales para el objeto `CToolBarCtrl` incrustado.|
|[CToolBar::GetButtonInfo](#getbuttoninfo)|Recupera el identificador, el estilo y el número de imagen de un botón.|
|[CToolBar::GetButtonStyle](#getbuttonstyle)|Recupera el estilo de un botón.|
|[CToolBar::GetButtonText](#getbuttontext)|Recupera el texto que aparecerá en un botón.|
|[CToolBar::GetItemID](#getitemid)|Devuelve el identificador de comando de un botón o separador en el índice dado.|
|[CToolBar::GetItemRect](#getitemrect)|Recupera el rectángulo de presentación del elemento en el índice especificado.|
|[CToolBar::GetToolBarCtrl](#gettoolbarctrl)|Permite el acceso directo al control común subyacente.|
|[CToolBar::LoadBitmap](#loadbitmap)|Carga el mapa de bits que contiene imágenes de botón de mapa de bits.|
|[CToolBar::LoadToolBar](#loadtoolbar)|Carga un recurso de la barra de herramientas creado con el editor de recursos.|
|[CToolBar::SetBitmap](#setbitmap)|Establece una imagen de mapa de imágenes.|
|[CToolBar::SetButtonInfo](#setbuttoninfo)|Establece el identificador, el estilo y el número de imagen de un botón.|
|[CToolBar::SetButtons](#setbuttons)|Establece los estilos de botón y un índice de las imágenes de botón en el mapa de bits.|
|[CToolBar::SetButtonStyle](#setbuttonstyle)|Establece el estilo de un botón.|
|[CToolBar::SetButtonText](#setbuttontext)|Establece el texto que aparecerá en un botón.|
|[CToolBar::SetHeight](#setheight)|Establece el alto de la barra de herramientas.|
|[CToolBar::SetSizes](#setsizes)|Establece los tamaños de los botones y sus mapas de bits.|

## <a name="remarks"></a>Comentarios

Los botones pueden actuar como pulsadores, botones de casilla o botones de radio. `CToolBar`los objetos suelen ser miembros incrustados de objetos de ventana de marco derivados de la clase [CFrameWnd](../../mfc/reference/cframewnd-class.md) o [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md).

[CToolBar:: GetToolBarCtrl](#gettoolbarctrl), una función miembro nueva de MFC 4,0, le permite aprovechar la compatibilidad del control común de Windows con la personalización de la barra de herramientas y la funcionalidad adicional. `CToolBar`las funciones miembro proporcionan la mayor parte de la funcionalidad de los controles comunes de Windows; sin embargo, al llamar `GetToolBarCtrl`a, puede dar a las barras de herramientas incluso más características de las barras de herramientas de Windows 95/98. Cuando llame `GetToolBarCtrl`a, devolverá una referencia a un `CToolBarCtrl` objeto. Vea [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) para obtener más información sobre el diseño de barras de herramientas mediante controles comunes de Windows. Para obtener más información general sobre los controles comunes, vea [controles comunes](/windows/win32/Controls/common-controls-intro) en el Windows SDK.

Visual C++ le proporciona dos métodos para crear una barra de herramientas. Para crear un recurso de barra de herramientas mediante el editor de recursos, siga estos pasos:

1. Cree un recurso de la barra de herramientas.

1. Construya el `CToolBar` objeto.

1. Llame a la función [Create](#create) (o [CreateEx](#createex)) para crear la barra de herramientas de Windows y `CToolBar` adjuntarla al objeto.

1. Llame a [LoadToolBar](#loadtoolbar) para cargar el recurso de la barra de herramientas.

De lo contrario, siga estos pasos:

1. Construya el `CToolBar` objeto.

1. Llame a la función [Create](#create) (o [CreateEx](#createex)) para crear la barra de herramientas de Windows y `CToolBar` adjuntarla al objeto.

1. Llame a [loadBitmap](#loadbitmap) para cargar el mapa de bits que contiene las imágenes de botón de la barra de herramientas.

1. Llame a [SetButtons](#setbuttons) para establecer el estilo de botón y asociar cada botón a una imagen en el mapa de bits.

Todas las imágenes de botón de la barra de herramientas se toman de un mapa de bits, que debe contener una imagen para cada botón. Todas las imágenes deben tener el mismo tamaño; el valor predeterminado es de 16 píxeles de ancho y 15 píxeles de alto. Las imágenes deben estar en paralelo en el mapa de bits.

La `SetButtons` función toma un puntero a una matriz de identificadores de control y un entero que especifica el número de elementos de la matriz. La función establece el identificador de cada botón en el valor del elemento correspondiente de la matriz y asigna a cada botón un índice de imagen, que especifica la posición de la imagen del botón en el mapa de bits. Si un elemento de matriz tiene el valor ID_SEPARATOR, no se asigna ningún índice de imagen.

El orden de las imágenes en el mapa de bits es normalmente el orden en que se dibujan en la pantalla, pero puede usar la función [SetButtonInfo](#setbuttoninfo) para cambiar la relación entre el orden de las imágenes y el orden de dibujo.

Todos los botones de una barra de herramientas tienen el mismo tamaño. El valor predeterminado es 24 x 22 píxeles, de acuerdo con las *directrices de la interfaz de Windows para el diseño de software*. Cualquier espacio adicional entre las dimensiones de imagen y de botón se usa para formar un borde alrededor de la imagen.

Cada botón tiene una imagen. Los distintos Estados y estilos de los botones (presionado, arriba, abajo, deshabilitado, deshabilitado, inactivo e indeterminado) se generan a partir de una imagen. Aunque los mapas de bits pueden ser cualquier color, puede obtener los mejores resultados con imágenes en negro y en tonalidades de gris.

> [!WARNING]
> `CToolBar`admite mapas de bits con un máximo de 16 colores. Cuando se carga una imagen en un editor de barras de herramientas, Visual Studio convierte automáticamente la imagen en un mapa de bits de 16 colores, si es necesario, y muestra un mensaje de advertencia si se ha convertido la imagen. Si usa una imagen con más de 16 colores (con un editor externo para editar la imagen), la aplicación podría comportarse de forma inesperada.

Los botones de la barra de herramientas imitan los pulsadores de forma predeterminada. Sin embargo, los botones de la barra de herramientas también pueden imitar botones de casilla o botones de radio. Los botones de casilla tienen tres Estados: activado, desactivado e indeterminado. Los botones de radio solo tienen dos Estados: activado y desactivado.

Para establecer un botón individual o un estilo de separador sin señalar a una matriz, llame a [GetButtonStyle](#getbuttonstyle) para recuperar el estilo y, a continuación `SetButtons`, llame a [SetButtonStyle](#setbuttonstyle) en lugar de a. `SetButtonStyle`resulta muy útil cuando se desea cambiar el estilo de un botón en tiempo de ejecución.

Para asignar texto para que aparezca en un botón, llame a [GetButtonText](#getbuttontext) para recuperar el texto que aparecerá en el botón y, a continuación, llame a [SetButtonText](#setbuttontext) para establecer el texto.

Para crear un botón de casilla, asígnele el estilo TBBS_CHECKBOX o use la función miembro `CCmdUI` de `SetCheck` un objeto en un controlador ON_UPDATE_COMMAND_UI. Llamar `SetCheck` a convierte un botón de control en un botón de casilla. Pase `SetCheck` un argumento de 0 para unchecked, 1 para checked o 2 para indeterminados.

Para crear un botón de radio, llame a la función miembro [SetRadio](../../mfc/reference/ccmdui-class.md#setradio) de un objeto [CCmdUI](../../mfc/reference/ccmdui-class.md) desde un controlador ON_UPDATE_COMMAND_UI. Pase `SetRadio` un argumento de 0 para unchecked o NonZero para Checked. Con el fin de proporcionar un comportamiento mutuamente excluyente del grupo de radio, debe tener controladores ON_UPDATE_COMMAND_UI para todos los botones del grupo.

Para obtener más información sobre `CToolBar`el uso de, vea el artículo implementación [de la barra de herramientas de [MFC](../../mfc/mfc-toolbar-implementation.md) y nota técnica 31: Barras](../../mfc/tn031-control-bars.md)de control.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext. h

##  <a name="commandtoindex"></a>  CToolBar::CommandToIndex

Esta función miembro devuelve el índice del primer botón de la barra de herramientas, a partir de la posición 0 `nIDFind`, cuyo identificador de comando coincide.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parámetros

*nIDFind*<br/>
IDENTIFICADOR de comando de un botón de la barra de herramientas.

### <a name="return-value"></a>Valor devuelto

Índice del botón o-1 si ningún botón tiene el identificador de comando especificado.

##  <a name="create"></a>  CToolBar::Create

Esta función miembro crea una barra de herramientas de Windows (una ventana secundaria) y la `CToolBar` asocia al objeto.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario de la barra de herramientas.

*dwStyle*<br/>
Estilo de la barra de herramientas. Los estilos de barra de herramientas adicionales admitidos son:

- La barra de control CBRS_TOP está en la parte superior de la ventana marco.

- La barra de control CBRS_BOTTOM está en la parte inferior de la ventana marco.

- La barra de control CBRS_NOALIGN no se recoloca cuando se cambia el tamaño del elemento primario.

- La barra de control de CBRS_TOOLTIPS muestra información sobre herramientas.

- La barra de control CBRS_SIZE_DYNAMIC es dinámica.

- La barra de control CBRS_SIZE_FIXED es fija.

- La barra de control CBRS_FLOATING es flotante.

- CBRS_FLYBY barra de estado muestra información sobre el botón.

- La barra de control CBRS_HIDE_INPLACE no se muestra al usuario.

*nID*<br/>
IDENTIFICADOR de la ventana secundaria de la barra de herramientas.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

También establece el alto de la barra de herramientas en un valor predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

##  <a name="createex"></a>  CToolBar::CreateEx

Llame a esta función para crear una barra de herramientas de Windows (una ventana secundaria) y `CToolBar` asociarla al objeto.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = TBSTYLE_FLAT,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_ALIGN_TOP,
    CRect rcBorders = CRect(
    0,
    0,
    0,
    0),
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario de la barra de herramientas.

*dwCtrlStyle*<br/>
Estilos adicionales para la creación del objeto [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) incrustado. De forma predeterminada, este valor se establece en TBSTYLE_FLAT. Para obtener una lista completa de los estilos de la barra de herramientas, vea *dwStyle*.

*dwStyle*<br/>
Estilo de la barra de herramientas. Vea el [control de barra de herramientas y los estilos de botón](/windows/win32/Controls/toolbar-control-and-button-styles) en el Windows SDK para obtener una lista de los estilos adecuados.

*rcBorders*<br/>
Objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) que define los anchos de los bordes de la ventana de la barra de herramientas. Estos bordes se establecen en 0, 0, 0, 0 de forma predeterminada, lo que resulta en una ventana de barra de herramientas sin bordes.

*nID*<br/>
IDENTIFICADOR de la ventana secundaria de la barra de herramientas.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

También establece el alto de la barra de herramientas en un valor predeterminado.

Use `CreateEx`, en lugar de [crear](#create), cuando determinados estilos deban estar presentes durante la creación del control de barra de herramientas incrustado. Por ejemplo, establezca *dwCtrlStyle* en TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT para crear una barra de herramientas similar a las barras de herramientas de Internet Explorer 4.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

##  <a name="ctoolbar"></a>  CToolBar::CToolBar

Esta función miembro crea un `CToolBar` objeto y establece los tamaños predeterminados.

```
CToolBar();
```

### <a name="remarks"></a>Comentarios

Llame a la función miembro [Create](#create) para crear la ventana de la barra de herramientas.

##  <a name="getbuttoninfo"></a>  CToolBar::GetButtonInfo

Esta función miembro recupera el identificador de control, el estilo y el índice de imagen del botón o separador de la barra de herramientas en la ubicación especificada por *NINDEX.*

```
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del botón o separador de la barra de herramientas cuya información se va a recuperar.

*nID*<br/>
Referencia a un valor UINT que se establece en el identificador de comando del botón.

*nStyle*<br/>
Referencia a un valor UINT que se establece en el estilo del botón.

*iImage*<br/>
Referencia a un entero que se establece en el índice de la imagen del botón en el mapa de bits.

### <a name="remarks"></a>Comentarios

Esos valores se asignan a las variables a las que se hace referencia mediante *nID*, *nStyle*y *iImage*. El índice de la imagen es la posición de la imagen en el mapa de bits que contiene las imágenes de todos los botones de la barra de herramientas. La primera imagen está en la posición 0.

Si *NINDEX* especifica un separador, *iImage* se establece en el ancho del separador en píxeles.

##  <a name="getbuttonstyle"></a>  CToolBar::GetButtonStyle

Llame a esta función miembro para recuperar el estilo de un botón o separador en la barra de herramientas.

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del botón de la barra de herramientas o del estilo de separador que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

Estilo del botón o separador especificado por *NINDEX*.

### <a name="remarks"></a>Comentarios

El estilo de un botón determina cómo aparece el botón y cómo responde a los datos proporcionados por el usuario. Consulte [SetButtonStyle](#setbuttonstyle) para obtener ejemplos de estilos de botón.

##  <a name="getbuttontext"></a>  CToolBar::GetButtonText

Llame a esta función miembro para recuperar el texto que aparece en un botón.

```
CString GetButtonText(int nIndex) const;

void GetButtonText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del texto que se va a recuperar.

*rString*<br/>
Referencia a un objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contendrá el texto que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

`CString` Objeto que contiene el texto del botón.

### <a name="remarks"></a>Comentarios

La segunda forma de esta función miembro rellena un `CString` objeto con el texto de la cadena.

##  <a name="getitemid"></a>  CToolBar::GetItemID

Esta función miembro devuelve el identificador de comando del botón o separador especificado por *NINDEX*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del elemento cuyo identificador se va a recuperar.

### <a name="return-value"></a>Valor devuelto

IDENTIFICADOR de comando del botón o separador especificado por *NINDEX*.

### <a name="remarks"></a>Comentarios

Los separadores devuelven ID_SEPARATOR.

##  <a name="getitemrect"></a>  CToolBar::GetItemRect

Esta función miembro rellena la `RECT` estructura cuya dirección está incluida en *lpRect* con las coordenadas del botón o separador especificados por *NINDEX*.

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del elemento (botón o separador) cuyas coordenadas del rectángulo se van a recuperar.

*lpRect*<br/>
Dirección de la estructura [Rect](/windows/win32/api/windef/ns-windef-rect) que contendrá las coordenadas del elemento.

### <a name="remarks"></a>Comentarios

Las coordenadas están en píxeles en relación con la esquina superior izquierda de la barra de herramientas.

Utilice `GetItemRect` para obtener las coordenadas de un separador que desea reemplazar con un cuadro combinado u otro control.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CToolBar:: SetSizes](#setsizes).

##  <a name="gettoolbarctrl"></a>  CToolBar::GetToolBarCtrl

Esta función miembro permite el acceso directo al control común subyacente.

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

Referencia a un objeto `CToolBarCtrl`.

### <a name="remarks"></a>Comentarios

Utilice `GetToolBarCtrl` para aprovechar las ventajas de la funcionalidad del control común de la barra de herramientas de Windows y para aprovechar la compatibilidad de [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) que proporciona la personalización de la barra de herramientas.

Para obtener más información sobre el uso de controles comunes, vea el artículo [controles](../../mfc/controls-mfc.md) y [controles comunes](/windows/win32/Controls/common-controls-intro) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

##  <a name="loadbitmap"></a>  CToolBar::LoadBitmap

Llame a esta función miembro para cargar el mapa de `lpszResourceName` bits `nIDResource`especificado por o.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parámetros

*lpszResourceName*<br/>
Puntero al nombre de recurso del mapa de bits que se va a cargar.

*nIDResource*<br/>
IDENTIFICADOR de recurso del mapa de bits que se va a cargar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El mapa de bits debe contener una imagen para cada botón de la barra de herramientas. Si las imágenes no tienen el tamaño estándar (16 píxeles de ancho y 15 píxeles de alto), llame a [SetSizes](#setsizes) para establecer los tamaños de los botones y sus imágenes.

> [!WARNING]
> `CToolBar`admite mapas de bits con un máximo de 16 colores. Cuando se carga una imagen en un editor de barras de herramientas, Visual Studio convierte automáticamente la imagen en un mapa de bits de 16 colores, si es necesario, y muestra un mensaje de advertencia si se ha convertido la imagen. Si usa una imagen con más de 16 colores (con un editor externo para editar la imagen), la aplicación podría comportarse de forma inesperada.

##  <a name="loadtoolbar"></a>  CToolBar::LoadToolBar

Llame a esta función miembro para cargar la barra de herramientas especificada por *lpszResourceName* o *nIDResource*.

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>Parámetros

*lpszResourceName*<br/>
Puntero al nombre de recurso de la barra de herramientas que se va a cargar.

*nIDResource*<br/>
IDENTIFICADOR de recurso de la barra de herramientas que se va a cargar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Vea [Editor de barras de herramientas](../../windows/toolbar-editor.md) en para obtener más información sobre cómo crear un recurso de barra de herramientas.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CToolBar:: CreateEx](#createex).

##  <a name="setbitmap"></a>  CToolBar::SetBitmap

Llame a esta función miembro para establecer la imagen de mapa de bits de la barra de herramientas.

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>Parámetros

*hbmImageWell*<br/>
Identificador de una imagen de mapa de bits que está asociada a una barra de herramientas.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Por ejemplo, llame `SetBitmap` a para cambiar la imagen de mapa de imágenes después de que el usuario realice una acción en un documento que cambie la acción de un botón.

##  <a name="setbuttoninfo"></a>  CToolBar::SetButtonInfo

Llame a esta función miembro para establecer el identificador de comando, el estilo y el número de imagen del botón.

```
void SetButtonInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int iImage);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de base cero del botón o separador cuya información se va a establecer.

*nID*<br/>
Valor en el que se establece el identificador de comando del botón.

*nStyle*<br/>
Nuevo estilo de botón. Se admiten los siguientes estilos de botón:

- Pushbutton estándar de TBBS_BUTTON (valor predeterminado)

- Separador TBBS_SEPARATOR

- TBBS_CHECKBOX botón de casilla de verificación automática

- TBBS_GROUP marca el inicio de un grupo de botones

- TBBS_CHECKGROUP marca el inicio de un grupo de botones de casilla

- TBBS_DROPDOWN crea un botón de lista desplegable.

- TBBS_AUTOSIZE el ancho del botón se calculará en función del texto del botón, no del tamaño de la imagen.

- TBBS_NOPREFIX el texto del botón no tendrá asociado un prefijo de acelerador.

*iImage*<br/>
Nuevo índice de la imagen del botón dentro del mapa de bits.

### <a name="remarks"></a>Comentarios

En el caso de los separadores, que tienen el estilo TBBS_SEPARATOR, esta función establece el ancho del separador en píxeles en el valor almacenado en *iImage*.

> [!NOTE]
>  También puede establecer los Estados de los botones mediante el parámetro *nStyle* . sin embargo, dado que el controlador [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) controla los Estados de los botones, cualquier estado `SetButtonInfo` que se establezca mediante se perderá durante el siguiente procesamiento inactivo. Vea [Cómo actualizar objetos de la interfaz de usuario](../../mfc/how-to-update-user-interface-objects.md) y [TN031: Barras](../../mfc/tn031-control-bars.md) de control para obtener más información.

Para obtener información sobre los botones y las imágenes de mapa de bits, vea la información general de [CToolBar](../../mfc/reference/ctoolbar-class.md) y [CToolBar:: loadBitmap](#loadbitmap).

##  <a name="setbuttons"></a>  CToolBar::SetButtons

Esta función miembro establece el identificador de comando de cada botón de la barra de herramientas en el valor especificado por el elemento correspondiente de la matriz *lpIDArray*.

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parámetros

*lpIDArray*<br/>
Puntero a una matriz de identificadores de comando. Puede ser NULL para asignar botones vacíos.

*nIDCount*<br/>
Número de elementos de la matriz a los que apunta *lpIDArray*.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Si un elemento de la matriz tiene el valor ID_SEPARATOR, se crea un separador en la posición correspondiente de la barra de herramientas. Esta función también establece el estilo de cada botón en TBBS_BUTTON y el estilo de cada separador en TBBS_SEPARATOR, y asigna un índice de imagen a cada botón. El índice de la imagen especifica la posición de la imagen del botón en el mapa de bits.

No es necesario tener en cuenta los separadores en el mapa de bits porque esta función no asigna índices de imagen para los separadores. Si la barra de herramientas tiene botones en las posiciones 0, 1 y 3 y un separador en la posición 2, las imágenes de las posiciones 0, 1 y 2 del mapa de bits se asignan a los botones en las posiciones 0, 1 y 3, respectivamente.

Si *lpIDArray* es null, esta función asigna espacio para el número de elementos especificado por *nIDCount*. Use [SetButtonInfo](#setbuttoninfo) para establecer los atributos de cada elemento.

##  <a name="setbuttonstyle"></a>  CToolBar::SetButtonStyle

Llame a esta función miembro para establecer el estilo de un botón o separador, o para agrupar los botones.

```
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del botón o separador cuya información se va a establecer.

*nStyle*<br/>
Estilo de botón. Se admiten los siguientes estilos de botón:

- Pushbutton estándar de TBBS_BUTTON (valor predeterminado)

- Separador TBBS_SEPARATOR

- TBBS_CHECKBOX botón de casilla de verificación automática

- TBBS_GROUP marca el inicio de un grupo de botones

- TBBS_CHECKGROUP marca el inicio de un grupo de botones de casilla

- TBBS_DROPDOWN crea un botón de lista desplegable

- TBBS_AUTOSIZE el ancho del botón se calculará en función del texto del botón, no del tamaño de la imagen.

- TBBS_NOPREFIX el texto del botón no tendrá asociado un prefijo de acelerador

### <a name="remarks"></a>Comentarios

El estilo de un botón determina cómo aparece el botón y cómo responde a los datos proporcionados por el usuario.

Antes de `SetButtonStyle`llamar a, llame a la función miembro [GetButtonStyle](#getbuttonstyle) para recuperar el estilo del botón o del separador.

> [!NOTE]
>  También puede establecer los Estados de los botones mediante el parámetro *nStyle* . sin embargo, dado que el controlador [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) controla los Estados de los botones, cualquier estado `SetButtonStyle` que se establezca mediante se perderá durante el siguiente procesamiento inactivo. Vea [Cómo actualizar objetos de la interfaz de usuario](../../mfc/how-to-update-user-interface-objects.md) y [TN031: Barras](../../mfc/tn031-control-bars.md) de control para obtener más información.

##  <a name="setbuttontext"></a>  CToolBar::SetButtonText

Llame a esta función para establecer el texto de un botón.

```
BOOL SetButtonText(
    int nIndex,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del botón cuyo texto se va a establecer.

*lpszText*<br/>
Señala el texto que se va a establecer en un botón.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CToolBar:: GetToolBarCtrl](#gettoolbarctrl).

##  <a name="setheight"></a>  CToolBar::SetHeight

Esta función miembro establece el alto de la barra de herramientas en el valor, en píxeles, que se especifica en *cyHeight*.

```
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>Parámetros

*cyHeight*<br/>
Alto en píxeles de la barra de herramientas.

### <a name="remarks"></a>Comentarios

Después de llamar a [SetSizes](#setsizes), use esta función miembro para invalidar el alto de la barra de herramientas estándar. Si el alto es demasiado pequeño, los botones se recortarán en la parte inferior.

Si no se llama a esta función, el marco de trabajo utiliza el tamaño del botón para determinar el alto de la barra de herramientas.

##  <a name="setsizes"></a>  CToolBar::SetSizes

Llame a esta función miembro para establecer el tamaño, en píxeles, de los botones de la barra de herramientas en *sizeButton*.

```
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>Parámetros

*sizeButton*<br/>
Tamaño en píxeles de cada botón.

*sizeImage*<br/>
Tamaño en píxeles de cada imagen.

### <a name="remarks"></a>Comentarios

El parámetro *sizeImage* debe contener el tamaño, en píxeles, de las imágenes en el mapa de bits de la barra de herramientas. Las dimensiones de *sizeButton* deben ser suficientes para contener la imagen más 7 píxeles de ancho y 6 píxeles como alto. Esta función también establece el alto de la barra de herramientas para ajustarse a los botones.

Llame a esta función miembro solo para las barras de herramientas que no siguen las *directrices de la interfaz de Windows para* las recomendaciones de diseño de software para los tamaños de botón e imagen.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo de MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl (clase)](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)
