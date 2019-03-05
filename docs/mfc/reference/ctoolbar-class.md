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
ms.openlocfilehash: ee1820601f80ed270221b3186188793f7fdcbe08
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301459"
---
# <a name="ctoolbar-class"></a>CToolBar (clase)

Barras de control que tienen una fila de botones de mapas de bits y separadores opcionales.

## <a name="syntax"></a>Sintaxis

```
class CToolBar : public CControlBar
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CToolBar::CToolBar](#ctoolbar)|Construye un objeto `CToolBar`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CToolBar::CommandToIndex](#commandtoindex)|Devuelve el índice de un botón con el identificador de comando especificado.|
|[CToolBar::Create](#create)|Crea la barra de herramientas de Windows y lo adjunta a la `CToolBar` objeto.|
|[CToolBar::CreateEx](#createex)|Crea un `CToolBar` objeto estilos adicionales para el objeto incrustado `CToolBarCtrl` objeto.|
|[CToolBar::GetButtonInfo](#getbuttoninfo)|Recupera el identificador, el estilo y el número de la imagen de un botón.|
|[CToolBar::GetButtonStyle](#getbuttonstyle)|Recupera el estilo para un botón.|
|[CToolBar::GetButtonText](#getbuttontext)|Recupera el texto que aparecerá en un botón.|
|[CToolBar::GetItemID](#getitemid)|Devuelve el identificador de comando de un botón o un separador en el índice especificado.|
|[CToolBar::GetItemRect](#getitemrect)|Recupera el rectángulo de presentación para el elemento en el índice especificado.|
|[CToolBar::GetToolBarCtrl](#gettoolbarctrl)|Permite el acceso directo al control subyacente común.|
|[CToolBar::LoadBitmap](#loadbitmap)|Carga el mapa de bits que contiene imágenes de los botones de mapa de bits.|
|[CToolBar::LoadToolBar](#loadtoolbar)|Carga un recurso de barra de herramientas creado con el editor de recursos.|
|[CToolBar::SetBitmap](#setbitmap)|Establece una imagen de mapa de bits.|
|[CToolBar::SetButtonInfo](#setbuttoninfo)|Establece el identificador, el estilo y el número de la imagen de un botón.|
|[CToolBar::SetButtons](#setbuttons)|Conjuntos de estilos y un índice de imágenes de botón en el mapa de bits de botón.|
|[CToolBar::SetButtonStyle](#setbuttonstyle)|Establece el estilo de un botón.|
|[CToolBar::SetButtonText](#setbuttontext)|Establece el texto que aparecerá en un botón.|
|[CToolBar::SetHeight](#setheight)|Establece el alto de la barra de herramientas.|
|[CToolBar::SetSizes](#setsizes)|Establece los tamaños de los botones y sus mapas de bits.|

## <a name="remarks"></a>Comentarios

Los botones pueden actuar como botones de comando, los botones de casilla de verificación o botones de radio. `CToolBar` los objetos son normalmente incrustados miembros de objetos de ventana de marco derivados de la clase [CFrameWnd](../../mfc/reference/cframewnd-class.md) o [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md).

[CToolBar:: GetToolBarCtrl](#gettoolbarctrl), una función miembro nuevo a 4.0 de MFC, podrá aprovechar las ventajas de soporte técnico del control común de Windows para la personalización de la barra de herramientas y funcionalidades adicionales. `CToolBar` las funciones miembro proporcionan la mayoría de la funcionalidad de los controles comunes de Windows; Sin embargo, cuando se llama a `GetToolBarCtrl`, puedes usar las barras de herramientas aún más las características de las barras de herramientas de Windows 95 ó 98. Cuando se llama a `GetToolBarCtrl`, devolverá una referencia a un `CToolBarCtrl` objeto. Consulte [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) para obtener más información sobre el diseño de las barras de herramientas con los controles comunes de Windows. Para obtener información general sobre los controles comunes, consulte [controles comunes](/windows/desktop/Controls/common-controls-intro) en el SDK de Windows.

Visual C++ proporciona dos métodos para crear una barra de herramientas. Para crear un recurso de barra de herramientas mediante el Editor de recursos, siga estos pasos:

1. Crear un recurso de barra de herramientas.

1. Construir la `CToolBar` objeto.

1. Llame a la [crear](#create) (o [CreateEx](#createex)) función para crear la barra de herramientas de Windows y adjuntarlo a la `CToolBar` objeto.

1. Llame a [LoadToolBar](#loadtoolbar) para cargar el recurso de la barra de herramientas.

En caso contrario, siga estos pasos:

1. Construir la `CToolBar` objeto.

1. Llame a la [crear](#create) (o [CreateEx](#createex)) función para crear la barra de herramientas de Windows y adjuntarlo a la `CToolBar` objeto.

1. Llame a [LoadBitmap](#loadbitmap) para cargar el mapa de bits que contiene las imágenes de botón de barra de herramientas.

1. Llame a [SetButtons](#setbuttons) para establecer el estilo de botón y asociar cada botón con una imagen del mapa de bits.

Todas las imágenes de botón en la barra de herramientas proceden de un mapa de bits, que debe contener una imagen para cada botón. Todas las imágenes deben ser del mismo tamaño; el valor predeterminado es 16 píxeles de ancho y 15 píxeles de alto. Las imágenes deben estar en paralelo en el mapa de bits.

El `SetButtons` función toma un puntero a una matriz de identificadores de control y un entero que especifica el número de elementos de la matriz. La función establece el identificador de cada botón en el valor del elemento correspondiente de la matriz y asigna un índice de imagen, que especifica la posición de la imagen del botón en el mapa de bits de cada botón. Si un elemento de matriz tiene el valor ID_SEPARATOR, no se asigna ningún índice de imagen.

El orden de las imágenes en el mapa de bits es normalmente el orden en el que se dibujan en la pantalla, pero puede usar el [SetButtonInfo](#setbuttoninfo) función para cambiar la relación entre la imagen y orden de dibujo.

Todos los botones de una barra de herramientas tienen el mismo tamaño. El valor predeterminado es 24 x 22 píxeles, de acuerdo con *directrices de interfaz de Windows para el diseño de Software*. Los espacios adicionales entre las dimensiones de imagen y el botón se usan para formar un borde alrededor de la imagen.

Cada botón tiene una imagen. Los distintos Estados de botón y estilos (presionado, arriba, abajo, deshabilitado, deshabilitado hacia abajo e indeterminado) se generan a partir de una imagen. Aunque los mapas de bits pueden ser cualquier color, puede conseguir los mejores resultados con imágenes en negro y tonalidades de gris.

> [!WARNING]
> `CToolBar` admite mapas de bits con un máximo de 16 colores. Al cargar una imagen en un editor de la barra de herramientas, Visual Studio convierte la imagen en un mapa de bits de 16 colores, si es necesario y muestra un mensaje de advertencia si la imagen se ha convertido. Si usa una imagen con más de 16 colores (mediante un editor externo para editar la imagen), la aplicación podría tener un comportamiento inesperado.

Botones de barra de herramientas imitan los botones de comando de forma predeterminada. Sin embargo, también pueden imitar los botones de barra de herramientas, botones de casilla de verificación o botones de radio. Botones de casilla tienen tres estados: activado, desactivado e indeterminado. Botones de radio tienen sólo dos estados: activada y desactivada.

Para establecer un botón individual o el estilo del separador sin que apunta a una matriz, llame a [GetButtonStyle](#getbuttonstyle) para recuperar el estilo y, a continuación, llame a [SetButtonStyle](#setbuttonstyle) en lugar de `SetButtons`. `SetButtonStyle` es muy útil cuando desea cambiar el estilo de un botón en tiempo de ejecución.

Para asignar el texto que aparezca en un botón, llame al [GetButtonText](#getbuttontext) para recuperar el texto para que aparezcan en el botón y, a continuación, llame a [SetButtonText](#setbuttontext) para establecer el texto.

Para crear un botón de casilla de verificación, asigna el estilo TBBS_CHECKBOX o use un `CCmdUI` del objeto `SetCheck` función miembro en un controlador ON_UPDATE_COMMAND_UI. Una llamada a `SetCheck` un botón de comando se convierte en un botón de casilla de verificación. Pasar `SetCheck` un argumento de 0 para no está activada, 1 para activado o 2 para indeterminado.

Para crear un botón de radio, llame a un [CCmdUI](../../mfc/reference/ccmdui-class.md) del objeto [SetRadio](../../mfc/reference/ccmdui-class.md#setradio) la función miembro desde un controlador ON_UPDATE_COMMAND_UI. Pasar `SetRadio` un argumento de 0 para distinto de cero para activada o desactivada. Con el fin de proporcionar un comportamiento mutuamente excluyente de un grupo de radio, debe tener controladores ON_UPDATE_COMMAND_UI para todos los botones del grupo.

Para obtener más información sobre el uso de `CToolBar`, consulte el artículo [implementación de la barra de herramientas de MFC](../../mfc/mfc-toolbar-implementation.md) y [Nota técnica 31: Barras de control](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext.h

##  <a name="commandtoindex"></a>  CToolBar::CommandToIndex

Esta función miembro devuelve el índice del botón de la primera barra, empezando en la posición 0, cuyo identificador de comando coincide con `nIDFind`.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parámetros

*nIDFind*<br/>
Identificador de comando de un botón de barra de herramientas.

### <a name="return-value"></a>Valor devuelto

El índice del botón, o -1 si no hay ningún botón tiene el identificador de comando especificado.

##  <a name="create"></a>  CToolBar::Create

Esta función miembro crea una barra de herramientas de Windows (una ventana secundaria) y lo asocia a la `CToolBar` objeto.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Puntero a la ventana que es primario de la barra de herramientas.

*dwStyle*<br/>
El estilo de barra de herramientas. Estilos de barra de herramientas adicionales compatibles son:

- Barra de Control de CBRS_TOP está en la parte superior de la ventana de marco.

- Barra de Control CBRS_BOTTOM es en parte inferior de la ventana de marco.

- Barra de Control CBRS_NOALIGN no se cambia de posición cuando se cambia el tamaño del elemento primario.

- Barra de Control CBRS_TOOLTIPS muestra información sobre herramientas.

- Barra de Control CBRS_SIZE_DYNAMIC es dinámico.

- Barra de Control CBRS_SIZE_FIXED es fijo.

- Barra de Control CBRS_FLOATING está flotando.

- Barra de estado CBRS_FLYBY muestra información sobre el botón.

- Barra de Control CBRS_HIDE_INPLACE no se muestra al usuario.

*nID*<br/>
Identificador de ventana secundaria de. la barra de herramientas

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

También se establece el alto de la barra de herramientas en un valor predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

##  <a name="createex"></a>  CToolBar::CreateEx

Llame a esta función para crear una barra de herramientas de Windows (una ventana secundaria) y asócielo con el `CToolBar` objeto.

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
Puntero a la ventana que es primario de la barra de herramientas.

*dwCtrlStyle*<br/>
Estilos adicionales para la creación de los datos incrustados [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) objeto. De forma predeterminada, este valor se establece en TBSTYLE_FLAT. Para obtener una lista completa de los estilos de barra de herramientas, consulte *dwStyle*.

*dwStyle*<br/>
El estilo de barra de herramientas. Consulte [Control de barra de herramientas y los estilos de botón](/windows/desktop/Controls/toolbar-control-and-button-styles) en el SDK de Windows para obtener una lista de estilos apropiados.

*rcBorders*<br/>
Un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que define el ancho de los bordes de ventana de la barra de herramientas. Estos límites se establecen en 0,0,0,0 de forma predeterminada, lo que resulta en una ventana de la barra de herramientas sin bordes.

*nID*<br/>
Identificador de ventana secundaria de. la barra de herramientas

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

También se establece el alto de la barra de herramientas en un valor predeterminado.

Use `CreateEx`, en lugar de [crear](#create), cuando necesitan estar presente durante la creación del control de barra de herramientas incrustada determinados estilos. Por ejemplo, establecer *dwCtrlStyle* a TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT para crear una barra de herramientas que se parece a las barras de herramientas de Internet Explorer 4.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

##  <a name="ctoolbar"></a>  CToolBar::CToolBar

Esta función miembro construye un `CToolBar` objeto y establece los tamaños predeterminados.

```
CToolBar();
```

### <a name="remarks"></a>Comentarios

Llame a la [crear](#create) función miembro para crear la ventana de la barra de herramientas.

##  <a name="getbuttoninfo"></a>  CToolBar::GetButtonInfo

Esta función miembro recupera el Id. de control, el estilo y el índice de imagen del botón de barra de herramientas o del separador en la ubicación especificada por *nIndex.*

```
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del botón de barra de herramientas o separador es cuya información va a recuperar.

*nID*<br/>
Referencia a un tipo UINT que se establece en el identificador de comando del botón.

*nStyle*<br/>
Referencia a un tipo UINT que se establece en el estilo del botón.

*iImage*<br/>
Referencia a un entero que se establece en el índice de la imagen del botón en el mapa de bits.

### <a name="remarks"></a>Comentarios

Esos valores se asignan a las variables que se hace referencia a *nID*, *nStyle*, y *iImage*. El índice de imagen es la posición de la imagen del mapa de bits que contiene imágenes para todos los botones de barra de herramientas. Es la primera imagen en la posición 0.

Si *nIndex* especifica un separador, *iImage* se establece en el ancho del separador en píxeles.

##  <a name="getbuttonstyle"></a>  CToolBar::GetButtonStyle

Llame a esta función miembro para recuperar el estilo de un botón o un separador en la barra de herramientas.

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice del estilo de botón o el separador de barra de herramientas van a recuperar.

### <a name="return-value"></a>Valor devuelto

El estilo del botón o el separador especificado por *nIndex*.

### <a name="remarks"></a>Comentarios

Estilo de un botón determina cómo aparece el botón y cómo responde a la entrada del usuario. Consulte [SetButtonStyle](#setbuttonstyle) para obtener ejemplos de estilos de botón.

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
Índice de texto va a recuperar.

*rString*<br/>
Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el texto que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

Un `CString` objeto que contiene el texto del botón.

### <a name="remarks"></a>Comentarios

La segunda forma de este miembro de función se llena un `CString` objeto con el texto de cadena.

##  <a name="getitemid"></a>  CToolBar::GetItemID

Esta función miembro devuelve el identificador de comando del botón o el separador especificado por *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del elemento cuyo identificador se va a recuperar.

### <a name="return-value"></a>Valor devuelto

El identificador de comando del botón o el separador especificado por *nIndex*.

### <a name="remarks"></a>Comentarios

Separadores devuelven ID_SEPARATOR.

##  <a name="getitemrect"></a>  CToolBar::GetItemRect

Esta función miembro se llena el `RECT` estructura cuya dirección se encuentra en *lpRect* con las coordenadas del botón o el separador especificado por *nIndex*.

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del producto (botón o el separador) cuyas coordenadas del rectángulo que se va a recuperar.

*lpRect*<br/>
Dirección de la [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estructura que contiene las coordenadas del elemento.

### <a name="remarks"></a>Comentarios

Las coordenadas están en píxeles con respecto a la esquina superior izquierda de la barra de herramientas.

Use `GetItemRect` para obtener las coordenadas de un separador que desee reemplazar por un cuadro combinado u otro control.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CToolBar::SetSizes](#setsizes).

##  <a name="gettoolbarctrl"></a>  CToolBar::GetToolBarCtrl

Esta función miembro permite el acceso directo al control subyacente común.

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

Referencia a un objeto `CToolBarCtrl`.

### <a name="remarks"></a>Comentarios

Use `GetToolBarCtrl` para aprovechar la funcionalidad del control común de barra de herramientas de Windows y para aprovechar la compatibilidad con [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) proporciona para la personalización de la barra de herramientas.

Para obtener más información sobre el uso de controles comunes, vea el artículo [controles](../../mfc/controls-mfc.md) y [controles comunes](/windows/desktop/Controls/common-controls-intro) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

##  <a name="loadbitmap"></a>  CToolBar::LoadBitmap

Llame a esta función miembro para cargar el mapa de bits especificado por `lpszResourceName` o `nIDResource`.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parámetros

*lpszResourceName*<br/>
Puntero al nombre del recurso del mapa de bits que se va a cargar.

*nIDResource*<br/>
Identificador de recurso del mapa de bits que se va a cargar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El mapa de bits debe contener una imagen para cada botón de barra de herramientas. Si las imágenes no son del tamaño estándar (16 píxeles de ancho y 15 píxeles de alto), llamada [SetSizes](#setsizes) para establecer el tamaño de botón y sus imágenes.

> [!WARNING]
> `CToolBar` admite mapas de bits con un máximo de 16 colores. Al cargar una imagen en un editor de la barra de herramientas, Visual Studio convierte la imagen en un mapa de bits de 16 colores, si es necesario y muestra un mensaje de advertencia si la imagen se ha convertido. Si usa una imagen con más de 16 colores (mediante un editor externo para editar la imagen), la aplicación podría tener un comportamiento inesperado.

##  <a name="loadtoolbar"></a>  CToolBar::LoadToolBar

Llame a esta función miembro para cargar la barra de herramientas especificado por *lpszResourceName* o *nIDResource*.

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>Parámetros

*lpszResourceName*<br/>
Puntero al nombre del recurso de la barra de herramientas que se cargue.

*nIDResource*<br/>
Identificador de recurso de la barra de herramientas que se cargue.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Consulte [editor de la barra de herramientas](../../windows/toolbar-editor.md) en para obtener más información acerca de cómo crear un recurso de barra de herramientas.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CToolBar:: CreateEx](#createex).

##  <a name="setbitmap"></a>  CToolBar::SetBitmap

Llame a esta función miembro para establecer la imagen de mapa de bits de la barra de herramientas.

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>Parámetros

*hbmImageWell*<br/>
Identificador de una imagen de mapa de bits que está asociada con una barra de herramientas.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Por ejemplo, llamar a `SetBitmap` para cambiar la imagen de mapa de bits después de que el usuario realiza una acción en un documento que cambia la acción de un botón.

##  <a name="setbuttoninfo"></a>  CToolBar::SetButtonInfo

Llame a esta función miembro para establecer el identificador de comando, estilo y número de la imagen del botón.

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
El valor al que se establece el identificador de comando del botón.

*nStyle*<br/>
El nuevo estilo de botón. Se admiten los siguientes estilos de botón:

- Pushbutton TBBS_BUTTON estándar (valor predeterminado)

- Separador TBBS_SEPARATOR

- Botón de casilla de verificación TBBS_CHECKBOX automática

- TBBS_GROUP marca el inicio de un grupo de botones

- TBBS_CHECKGROUP marca el inicio de un grupo de botones de casilla de verificación

- TBBS_DROPDOWN crea un botón de lista desplegable.

- TBBS_AUTOSIZE ancho del botón se calculará según el texto del botón, no en el tamaño de la imagen.

- TBBS_NOPREFIX el texto del botón no tendrá un prefijo de acelerador asociado con él.

*iImage*<br/>
Nuevo índice de la imagen del botón en el mapa de bits.

### <a name="remarks"></a>Comentarios

Para los separadores, que tienen el estilo TBBS_SEPARATOR, esta función establece el ancho del separador en píxeles, para el valor almacenado en *iImage*.

> [!NOTE]
>  También puede establecer los Estados del botón con el *nStyle* parámetro; sin embargo, porque los Estados del botón se controlan mediante el [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) controlador, cualquier estado se establece utilizando `SetButtonInfo` se perderán durante el siguiente procesamiento en inactividad. Consulte [cómo actualizar los objetos de interfaz de usuario](../../mfc/how-to-update-user-interface-objects.md) y [TN031: Barras de control](../../mfc/tn031-control-bars.md) para obtener más información.

Para obtener información sobre las imágenes de mapa de bits y botones, consulte el [CToolBar](../../mfc/reference/ctoolbar-class.md) información general y [CToolBar::LoadBitmap](#loadbitmap).

##  <a name="setbuttons"></a>  CToolBar::SetButtons

Esta función miembro establece el identificador de comando de cada botón de barra de herramientas en el valor especificado por el elemento correspondiente de la matriz *lpIDArray*.

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parámetros

*lpIDArray*<br/>
Puntero a una matriz de identificadores de comando. Puede ser NULL para asignar botones vacíos.

*nIDCount*<br/>
Número de elementos de la matriz señalada por *lpIDArray*.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Si un elemento de la matriz tiene el valor ID_SEPARATOR, se crea un separador en la posición correspondiente de la barra de herramientas. Esta función también establece el estilo de cada botón TBBS_BUTTON y estilo de cada separador TBBS_SEPARATOR y asigna un índice de imagen para cada botón. El índice de imagen especifica la posición de la imagen del botón en el mapa de bits.

No es necesario tener en cuenta para los separadores del mapa de bits porque esta función no asigna los índices de la imagen para los separadores. Si la barra de herramientas tiene botones en posiciones 0, 1 y 3 y un separador en la posición 2, las imágenes en las posiciones 0, 1 y 2 en el mapa de bits se asignan a los botones situados en posiciones 0, 1 y 3, respectivamente.

Si *lpIDArray* es NULL, esta función asigna espacio para el número de elementos especificado por *nIDCount*. Use [SetButtonInfo](#setbuttoninfo) para establecer atributos de cada elemento.

##  <a name="setbuttonstyle"></a>  CToolBar::SetButtonStyle

Llame a esta función miembro para establecer el estilo de un botón o un separador o para agrupar los botones.

```
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del botón o separador cuya información se va a establecer.

*nStyle*<br/>
El estilo de botón. Se admiten los siguientes estilos de botón:

- Pushbutton TBBS_BUTTON estándar (valor predeterminado)

- Separador TBBS_SEPARATOR

- Botón de casilla de verificación TBBS_CHECKBOX automática

- TBBS_GROUP marca el inicio de un grupo de botones

- TBBS_CHECKGROUP marca el inicio de un grupo de botones de casilla de verificación

- TBBS_DROPDOWN crea un botón de lista desplegable

- TBBS_AUTOSIZE ancho del botón se calculará según el texto del botón, no en el tamaño de la imagen

- TBBS_NOPREFIX el texto del botón no tendrá asociado un prefijo de Acelerador

### <a name="remarks"></a>Comentarios

Estilo de un botón determina cómo aparece el botón y cómo responde a la entrada del usuario.

Antes de llamar a `SetButtonStyle`, llame a la [GetButtonStyle](#getbuttonstyle) función miembro para recuperar el estilo de botón o el separador.

> [!NOTE]
>  También puede establecer los Estados del botón con el *nStyle* parámetro; sin embargo, porque los Estados del botón se controlan mediante el [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) controlador, cualquier estado se establece utilizando `SetButtonStyle` se perderán durante el siguiente procesamiento en inactividad. Consulte [cómo actualizar los objetos de interfaz de usuario](../../mfc/how-to-update-user-interface-objects.md) y [TN031: Barras de control](../../mfc/tn031-control-bars.md) para obtener más información.

##  <a name="setbuttontext"></a>  CToolBar::SetButtonText

Llame a esta función para establecer el texto en un botón.

```
BOOL SetButtonText(
    int nIndex,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice del botón cuyo texto se va a establecer.

*lpszText*<br/>
Señala el texto que se establecerá en un botón.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CToolBar:: GetToolBarCtrl](#gettoolbarctrl).

##  <a name="setheight"></a>  CToolBar::SetHeight

Esta función miembro establece el alto de la barra de herramientas en el valor, en píxeles, especificado en *cyHeight*.

```
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>Parámetros

*cyHeight*<br/>
El alto en píxeles de la barra de herramientas.

### <a name="remarks"></a>Comentarios

Después de llamar a [SetSizes](#setsizes), usar esta función miembro para invalidar el alto de la barra de herramientas estándar. Si el alto es demasiado pequeño, los botones se recortará en la parte inferior.

Si no se llama a esta función, el marco de trabajo usa el tamaño del botón para determinar el alto de la barra de herramientas.

##  <a name="setsizes"></a>  CToolBar::SetSizes

Llame a esta función miembro para establecer los botones de la barra de herramientas hasta el tamaño, en píxeles, especificado en *sizeButton*.

```
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>Parámetros

*sizeButton*<br/>
El tamaño en píxeles de cada botón.

*sizeImage*<br/>
El tamaño en píxeles de cada imagen.

### <a name="remarks"></a>Comentarios

El *sizeImage* parámetro debe contener el tamaño, en píxeles, de las imágenes de mapa de bits de la barra de herramientas. Las dimensiones en *sizeButton* debe ser suficiente para contener la imagen más 7 píxeles adicionales en el ancho y 6 adicional en el alto. Esta función también establece el alto de la barra de herramientas para ajustarse a los botones.

Llamar a esta función miembro solo para las barras de herramientas que no siguen *directrices de interfaz de Windows para el diseño de Software* recomendaciones para tamaños de imagen y el botón.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>Vea también

[CTRLBARS de ejemplo](../../visual-cpp-samples.md)<br/>
[DLGCBR32 de ejemplo MFC](../../visual-cpp-samples.md)<br/>
[Ejemplo MFC DOCKTOOL](../../visual-cpp-samples.md)<br/>
[CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl (clase)](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)
