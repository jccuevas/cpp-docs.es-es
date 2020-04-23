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
ms.openlocfilehash: cbb2d1bb797737a14e9728d339305bf9c371b543
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752206"
---
# <a name="ctoolbar-class"></a>CToolBar (clase)

Barras de control que tienen una fila de botones de mapas de bits y separadores opcionales.

## <a name="syntax"></a>Sintaxis

```
class CToolBar : public CControlBar
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CToolBar::CToolBar](#ctoolbar)|Construye un objeto `CToolBar`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CToolBar::CommandToIndex](#commandtoindex)|Devuelve el índice de un botón con el identificador de comando especificado.|
|[CToolBar::Crear](#create)|Crea la barra de herramientas `CToolBar` de Windows y la adjunta al objeto.|
|[CToolBar::CreateEx](#createex)|Crea `CToolBar` un objeto con estilos `CToolBarCtrl` adicionales para el objeto incrustado.|
|[CToolBar::GetButtonInfo](#getbuttoninfo)|Recupera el identificador, el estilo y el número de imagen de un botón.|
|[CToolBar::GetButtonStyle](#getbuttonstyle)|Recupera el estilo de un botón.|
|[CToolBar::GetButtonText](#getbuttontext)|Recupera el texto que aparecerá en un botón.|
|[CToolBar::GetItemID](#getitemid)|Devuelve el identificador de comando de un botón o separador en el índice especificado.|
|[CToolBar::GetItemRect](#getitemrect)|Recupera el rectángulo de visualización para el elemento en el índice especificado.|
|[CToolBar::GetToolBarCtrl](#gettoolbarctrl)|Permite el acceso directo al control común subyacente.|
|[CToolBar::LoadBitmap](#loadbitmap)|Carga el mapa de bits que contiene imágenes de botón de mapa de bits.|
|[CToolBar::LoadToolBar](#loadtoolbar)|Carga un recurso de barra de herramientas creado con el editor de recursos.|
|[CToolBar::SetBitmap](#setbitmap)|Establece una imagen de mapa de bits.|
|[CToolBar::SetButtonInfo](#setbuttoninfo)|Establece el ID, el estilo y el número de imagen de un botón.|
|[CToolBar::SetButtons](#setbuttons)|Establece estilos de botón y un índice de imágenes de botón dentro del mapa de bits.|
|[CToolBar::SetButtonStyle](#setbuttonstyle)|Establece el estilo de un botón.|
|[CToolBar::SetButtonText](#setbuttontext)|Establece el texto que aparecerá en un botón.|
|[CToolBar::SetHeight](#setheight)|Establece la altura de la barra de herramientas.|
|[CToolBar::SetSizes](#setsizes)|Establece los tamaños de los botones y sus mapas de bits.|

## <a name="remarks"></a>Observaciones

Los botones pueden actuar como pulsadores, botones de casilla de verificación o botones de opción. `CToolBar`los objetos suelen ser miembros incrustados de objetos de ventana de marco derivados de la clase [CFrameWnd](../../mfc/reference/cframewnd-class.md) o [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md).

[CToolBar::GetToolBarCtrl](#gettoolbarctrl), una función miembro nueva en MFC 4.0, le permite aprovechar la compatibilidad del control común de Windows para la personalización de la barra de herramientas y funcionalidad adicional. `CToolBar`Las funciones miembro proporcionan la mayor parte de la funcionalidad de los controles comunes de Windows; sin embargo, `GetToolBarCtrl`cuando se llama a , puede dar a sus barras de herramientas aún más de las características de las barras de herramientas de Windows 95/98. Cuando se `GetToolBarCtrl`llama a , se `CToolBarCtrl` devolverá una referencia a un objeto. Consulte [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) para obtener más información sobre el diseño de barras de herramientas mediante controles comunes de Windows. Para obtener más información general acerca de los controles comunes, vea [controles comunes](/windows/win32/Controls/common-controls-intro) en el Windows SDK.

Visual C++ proporciona dos métodos para crear una barra de herramientas. Para crear un recurso de barra de herramientas mediante el Editor de recursos, siga estos pasos:

1. Cree un recurso de barra de herramientas.

1. Construir `CToolBar` el objeto.

1. Llame a la función [Create](#create) (o [CreateEx](#createex)) `CToolBar` para crear la barra de herramientas de Windows y adjuntarla al objeto.

1. Llame a [LoadToolBar](#loadtoolbar) para cargar el recurso de barra de herramientas.

De lo contrario, siga estos pasos:

1. Construir `CToolBar` el objeto.

1. Llame a la función [Create](#create) (o [CreateEx](#createex)) `CToolBar` para crear la barra de herramientas de Windows y adjuntarla al objeto.

1. Llame a [LoadBitmap](#loadbitmap) para cargar el mapa de bits que contiene las imágenes del botón de barra de herramientas.

1. Llame a [SetButtons](#setbuttons) para establecer el estilo de botón y asociar cada botón con una imagen en el mapa de bits.

Todas las imágenes de botón de la barra de herramientas se toman de un mapa de bits, que debe contener una imagen para cada botón. Todas las imágenes deben tener el mismo tamaño; el valor predeterminado es 16 píxeles de ancho y 15 píxeles de alto. Las imágenes deben estar una al lado de la otra en el mapa de bits.

La `SetButtons` función toma un puntero a una matriz de controles iDs y un entero que especifica el número de elementos de la matriz. La función establece el identificador de cada botón en el valor del elemento correspondiente de la matriz y asigna a cada botón un índice de imagen, que especifica la posición de la imagen del botón en el mapa de bits. Si un elemento de matriz tiene el valor ID_SEPARATOR, no se asigna ningún índice de imagen.

El orden de las imágenes en el mapa de bits suele ser el orden en el que se dibujan en la pantalla, pero puede utilizar la función [SetButtonInfo](#setbuttoninfo) para cambiar la relación entre el orden de la imagen y el orden de dibujo.

Todos los botones de una barra de herramientas tienen el mismo tamaño. El valor predeterminado es 24 x 22 píxeles, de acuerdo con *las directrices*de interfaz de Windows para el diseño de software. Cualquier espacio adicional entre las dimensiones de la imagen y el botón se utiliza para formar un borde alrededor de la imagen.

Cada botón tiene una imagen. Los distintos estados y estilos de botón (presionados, arriba, abajo, deshabilitados, desactivados e indeterminados) se generan a partir de esa imagen. Aunque los mapas de bits pueden ser de cualquier color, puede lograr los mejores resultados con imágenes en negro y tonos de gris.

> [!WARNING]
> `CToolBar`admite mapas de bits con un máximo de 16 colores. Al cargar una imagen en un editor de barra de herramientas, Visual Studio convierte automáticamente la imagen en un mapa de bits de 16 colores, si es necesario, y muestra un mensaje de advertencia si la imagen se convirtió. Si utiliza una imagen con más de 16 colores (utilizando un editor externo para editar la imagen), la aplicación podría comportarse de forma inesperada.

Los botones de la barra de herramientas imitan los pulsadores de forma predeterminada. Sin embargo, los botones de la barra de herramientas también pueden imitar botones de casilla de verificación o botones de opción. Los botones de casilla de verificación tienen tres estados: marcado, desactivado e indeterminado. Los botones de radio solo tienen dos estados: marcado sin control ni borrado.

Para establecer un estilo de botón o separador individual sin apuntar a una matriz, `SetButtons`llame a [GetButtonStyle](#getbuttonstyle) para recuperar el estilo y, a continuación, llame a [SetButtonStyle](#setbuttonstyle) en lugar de . `SetButtonStyle`es más útil cuando desea cambiar el estilo de un botón en tiempo de ejecución.

Para asignar texto para que aparezca en un botón, llame a [GetButtonText](#getbuttontext) para recuperar el texto que aparece en el botón y, a continuación, llame a [SetButtonText](#setbuttontext) para establecer el texto.

Para crear un botón de casilla de verificación, `SetCheck` asígnele el estilo TBBS_CHECKBOX o use la función miembro de un `CCmdUI` objeto en un controlador de ON_UPDATE_COMMAND_UI. Llamar `SetCheck` convierte un pulsador en un botón de casilla de verificación. Pase `SetCheck` un argumento de 0 para unchecked, 1 para checked o 2 para indeterminado.

Para crear un botón de opción, llame a un [CCmdUI](../../mfc/reference/ccmdui-class.md) objeto [SetRadio](../../mfc/reference/ccmdui-class.md#setradio) función miembro desde un ON_UPDATE_COMMAND_UI controlador. Pase `SetRadio` un argumento de 0 para desmarcado o distinto de cero para checked. Para proporcionar el comportamiento mutuamente excluyente de un grupo de radio, debe tener controladores ON_UPDATE_COMMAND_UI para todos los botones del grupo.

Para obtener más `CToolBar`información sobre el uso , vea el artículo [Implementación](../../mfc/mfc-toolbar-implementation.md) de la barra de herramientas MFC y [Nota técnica 31: Barras](../../mfc/tn031-control-bars.md)de control .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext.h

## <a name="ctoolbarcommandtoindex"></a><a name="commandtoindex"></a>CToolBar::CommandToIndex

Esta función miembro devuelve el índice del primer botón de `nIDFind`barra de herramientas, comenzando en la posición 0, cuyo identificador de comando coincide con .

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parámetros

*nIDFind*<br/>
ID de comando de un botón de barra de herramientas.

### <a name="return-value"></a>Valor devuelto

El índice del botón, o -1 si ningún botón tiene el identificador de comando especificado.

## <a name="ctoolbarcreate"></a><a name="create"></a>CToolBar::Crear

Esta función miembro crea una barra de herramientas `CToolBar` de Windows (una ventana secundaria) y la asocia con el objeto.

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
El estilo de la barra de herramientas. Los estilos de barra de herramientas adicionales admitidos son:

- CBRS_TOP barra de control está en la parte superior de la ventana de marco.

- CBRS_BOTTOM barra de control se encuentra en la parte inferior de la ventana de marco.

- CBRS_NOALIGN barra de control no se cambia de posición cuando se cambia el tamaño del elemento primario.

- CBRS_TOOLTIPS barra control muestra las sugerencias de herramientas.

- CBRS_SIZE_DYNAMIC barra de control es dinámica.

- CBRS_SIZE_FIXED barra de control está fija.

- CBRS_FLOATING barra de control está flotante.

- CBRS_FLYBY barra Estado muestra información sobre el botón.

- CBRS_HIDE_INPLACE barra de control no se muestra al usuario.

*nID*<br/>
Id. de ventana secundaria de la barra de herramientas.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

También establece la altura de la barra de herramientas en un valor predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

## <a name="ctoolbarcreateex"></a><a name="createex"></a>CToolBar::CreateEx

Llame a esta función para crear una barra de `CToolBar` herramientas de Windows (una ventana secundaria) y asociarla al objeto.

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
Estilos adicionales para la creación del objeto [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) incrustado. De forma predeterminada, este valor se establece en TBSTYLE_FLAT. Para obtener una lista completa de estilos de barra de herramientas, vea *dwStyle*.

*dwStyle*<br/>
El estilo de la barra de herramientas. Consulte Control de barra de [herramientas y Estilos](/windows/win32/Controls/toolbar-control-and-button-styles) de botón en el Windows SDK para obtener una lista de estilos adecuados.

*rcBorders*<br/>
Un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que define los anchos de los bordes de la ventana de la barra de herramientas. Estos bordes se establecen en 0,0,0,0 de forma predeterminada, lo que da como resultado una ventana de barra de herramientas sin bordes.

*nID*<br/>
Id. de ventana secundaria de la barra de herramientas.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

También establece la altura de la barra de herramientas en un valor predeterminado.

Utilice `CreateEx`, en lugar de [Crear](#create), cuando determinados estilos deban estar presentes durante la creación del control de barra de herramientas incrustado. Por ejemplo, establezca *dwCtrlStyle* en TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT crear una barra de herramientas similar a las barras de herramientas de Internet Explorer 4.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

## <a name="ctoolbarctoolbar"></a><a name="ctoolbar"></a>CToolBar::CToolBar

Esta función miembro `CToolBar` construye un objeto y establece los tamaños predeterminados.

```
CToolBar();
```

### <a name="remarks"></a>Observaciones

Llame a la [crear](#create) función miembro para crear la ventana de la barra de herramientas.

## <a name="ctoolbargetbuttoninfo"></a><a name="getbuttoninfo"></a>CToolBar::GetButtonInfo

Esta función miembro recupera el identificador de control, el estilo y el índice de imagen del botón o separador de barra de herramientas en la ubicación especificada por *nIndex.*

```cpp
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Indice del botón o separador de la barra de herramientas cuya información se va a recuperar.

*nID*<br/>
Referencia a un UINT que se establece en el identificador de comando del botón.

*nStyle*<br/>
Referencia a un UINT que se establece en el estilo del botón.

*iImage*<br/>
Referencia a un entero que se establece en el índice de la imagen del botón dentro del mapa de bits.

### <a name="remarks"></a>Observaciones

Estos valores se asignan a las variables a las que hace referencia *nID*, *nStyle*e *iImage*. El índice de imagen es la posición de la imagen dentro del mapa de bits que contiene imágenes para todos los botones de la barra de herramientas. La primera imagen está en la posición 0.

Si *nIndex* especifica un separador, *iImage* se establece en el ancho del separador en píxeles.

## <a name="ctoolbargetbuttonstyle"></a><a name="getbuttonstyle"></a>CToolBar::GetButtonStyle

Llame a esta función miembro para recuperar el estilo de un botón o separador en la barra de herramientas.

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice del botón de la barra de herramientas o el estilo de separador que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

El estilo del botón o separador especificado por *nIndex*.

### <a name="remarks"></a>Observaciones

El estilo de un botón determina cómo aparece el botón y cómo responde a la entrada del usuario. Consulte [SetButtonStyle](#setbuttonstyle) para ver ejemplos de estilos de botón.

## <a name="ctoolbargetbuttontext"></a><a name="getbuttontext"></a>CToolBar::GetButtonText

Llame a esta función miembro para recuperar el texto que aparece en un botón.

```
CString GetButtonText(int nIndex) const;

void GetButtonText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Indice del texto que se va a recuperar.

*rString*<br/>
Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contendrá el texto que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

Objeto `CString` que contiene el texto del botón.

### <a name="remarks"></a>Observaciones

La segunda forma de esta `CString` función miembro rellena un objeto con el texto de cadena.

## <a name="ctoolbargetitemid"></a><a name="getitemid"></a>CToolBar::GetItemID

Esta función miembro devuelve el identificador de comando del botón o separador especificado por *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Indice del elemento cuyo identificador se va a recuperar.

### <a name="return-value"></a>Valor devuelto

El identificador de comando del botón o separador especificado por *nIndex*.

### <a name="remarks"></a>Observaciones

Los separadores devuelven ID_SEPARATOR.

## <a name="ctoolbargetitemrect"></a><a name="getitemrect"></a>CToolBar::GetItemRect

Esta función miembro `RECT` rellena la estructura cuya dirección está contenida en *lpRect* con las coordenadas del botón o separador especificado por *nIndex*.

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Indice del elemento (botón o separador) cuyas coordenadas rectangulares se van a recuperar.

*lpRect*<br/>
Dirección de la estructura [RECT](/windows/win32/api/windef/ns-windef-rect) que contendrá las coordenadas del elemento.

### <a name="remarks"></a>Observaciones

Las coordenadas están en píxeles en relación con la esquina superior izquierda de la barra de herramientas.

Se `GetItemRect` utiliza para obtener las coordenadas de un separador que desea reemplazar con un cuadro combinado u otro control.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CToolBar::SetSizes](#setsizes).

## <a name="ctoolbargettoolbarctrl"></a><a name="gettoolbarctrl"></a>CToolBar::GetToolBarCtrl

Esta función miembro permite el acceso directo al control común subyacente.

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

Referencia a un objeto `CToolBarCtrl`.

### <a name="remarks"></a>Observaciones

Se `GetToolBarCtrl` usa para aprovechar la funcionalidad del control común de la barra de herramientas de Windows y para aprovechar la compatibilidad [que CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) proporciona para la personalización de la barra de herramientas.

Para obtener más información sobre el uso de controles comunes, vea el artículo [Controles](../../mfc/controls-mfc.md) y [controles comunes](/windows/win32/Controls/common-controls-intro) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

## <a name="ctoolbarloadbitmap"></a><a name="loadbitmap"></a>CToolBar::LoadBitmap

Llame a esta función miembro `lpszResourceName` para `nIDResource`cargar el mapa de bits especificado por o .

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parámetros

*lpszResourceName*<br/>
Puntero al nombre del recurso del mapa de bits que se va a cargar.

*nIDResource*<br/>
ID de recurso del mapa de bits que se va a cargar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El mapa de bits debe contener una imagen para cada botón de la barra de herramientas. Si las imágenes no tienen el tamaño estándar (16 píxeles de ancho y 15 píxeles de alto), llame a [SetSizes](#setsizes) para establecer los tamaños de botón y sus imágenes.

> [!WARNING]
> `CToolBar`admite mapas de bits con un máximo de 16 colores. Al cargar una imagen en un editor de barra de herramientas, Visual Studio convierte automáticamente la imagen en un mapa de bits de 16 colores, si es necesario, y muestra un mensaje de advertencia si la imagen se convirtió. Si utiliza una imagen con más de 16 colores (utilizando un editor externo para editar la imagen), la aplicación podría comportarse de forma inesperada.

## <a name="ctoolbarloadtoolbar"></a><a name="loadtoolbar"></a>CToolBar::LoadToolBar

Llame a esta función miembro para cargar la barra de herramientas especificada por *lpszResourceName* o *nIDResource*.

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>Parámetros

*lpszResourceName*<br/>
Puntero al nombre del recurso de la barra de herramientas que se va a cargar.

*nIDResource*<br/>
Identificador de recurso de la barra de herramientas que se va a cargar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Consulte el editor de [la barra](../../windows/toolbar-editor.md) de herramientas para obtener más información sobre cómo crear un recurso de barra de herramientas.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CToolBar::CreateEx](#createex).

## <a name="ctoolbarsetbitmap"></a><a name="setbitmap"></a>CToolBar::SetBitmap

Llame a esta función miembro para establecer la imagen de mapa de bits para la barra de herramientas.

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>Parámetros

*hbmImageWell*<br/>
Control de una imagen de mapa de bits asociada a una barra de herramientas.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Por ejemplo, `SetBitmap` llame para cambiar la imagen de mapa de bits después de que el usuario realiza una acción en un documento que cambia la acción de un botón.

## <a name="ctoolbarsetbuttoninfo"></a><a name="setbuttoninfo"></a>CToolBar::SetButtonInfo

Llame a esta función miembro para establecer el identificador de comando del botón, el estilo y el número de imagen.

```cpp
void SetButtonInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int iImage);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice de base cero del botón o separador para el que se va a establecer la información.

*nID*<br/>
Valor en el que se establece el identificador de comando del botón.

*nStyle*<br/>
El nuevo estilo de botón. Se admiten los siguientes estilos de botón:

- TBBS_BUTTON Pulsador estándar (predeterminado)

- Separador de TBBS_SEPARATOR

- TBBS_CHECKBOX botón de casilla de verificación Automático

- TBBS_GROUP Marca el inicio de un grupo de botones

- TBBS_CHECKGROUP Marca el inicio de un grupo de botones de casilla de verificación

- TBBS_DROPDOWN Crea un botón de lista desplegable.

- TBBS_AUTOSIZE El ancho del botón se calculará en función del texto del botón, no del tamaño de la imagen.

- TBBS_NOPREFIX El texto del botón no tendrá un prefijo de acelerador asociado.

*iImage*<br/>
Nuevo índice para la imagen del botón dentro del mapa de bits.

### <a name="remarks"></a>Observaciones

Para los separadores, que tienen el estilo TBBS_SEPARATOR, esta función establece el ancho del separador en píxeles en el valor almacenado en *iImage*.

> [!NOTE]
> También puede establecer estados de botón mediante el *nStyle* parámetro; sin embargo, dado que los estados de botón `SetButtonInfo` están controlados por el [controlador ON_UPDATE_COMMAND_UI,](message-map-macros-mfc.md#on_update_command_ui) cualquier estado que establezca mediante se perderá durante el siguiente procesamiento inactivo. Consulte [Cómo actualizar objetos de interfaz de usuario](../../mfc/how-to-update-user-interface-objects.md) y [TN031: Barras](../../mfc/tn031-control-bars.md) de control para obtener más información.

Para obtener información sobre las imágenes y botones de mapa de bits, vea [CToolBar](../../mfc/reference/ctoolbar-class.md) Overview y [CToolBar::LoadBitmap](#loadbitmap).

## <a name="ctoolbarsetbuttons"></a><a name="setbuttons"></a>CToolBar::SetButtons

Esta función miembro establece el identificador de comando de cada botón de barra de herramientas en el valor especificado por el elemento correspondiente de la matriz *lpIDArray*.

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parámetros

*lpIDArray*<br/>
Puntero a una matriz de identificadores de comando. Puede ser NULL asignar botones vacíos.

*nIDCount*<br/>
Número de elementos de la matriz a los que apunta *lpIDArray*.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Si un elemento de la matriz tiene el valor ID_SEPARATOR, se crea un separador en la posición correspondiente de la barra de herramientas. Esta función también establece el estilo de cada botón en TBBS_BUTTON y el estilo de cada separador en TBBS_SEPARATOR y asigna un índice de imagen a cada botón. El índice de imagen especifica la posición de la imagen del botón dentro del mapa de bits.

No es necesario tener en cuenta los separadores en el mapa de bits porque esta función no asigna índices de imagen para los separadores. Si la barra de herramientas tiene botones en las posiciones 0, 1 y 3 y un separador en la posición 2, las imágenes en las posiciones 0, 1 y 2 del mapa de bits se asignan a los botones de las posiciones 0, 1 y 3, respectivamente.

Si *lpIDArray* es NULL, esta función asigna espacio para el número de elementos especificados por *nIDCount*. Use [SetButtonInfo](#setbuttoninfo) para establecer los atributos de cada elemento.

## <a name="ctoolbarsetbuttonstyle"></a><a name="setbuttonstyle"></a>CToolBar::SetButtonStyle

Llame a esta función miembro para establecer el estilo de un botón o separador, o para agrupar botones.

```cpp
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Indice del botón o separador cuya información se va a establecer.

*nStyle*<br/>
El estilo de botón. Se admiten los siguientes estilos de botón:

- TBBS_BUTTON Pulsador estándar (predeterminado)

- Separador de TBBS_SEPARATOR

- TBBS_CHECKBOX botón de casilla de verificación Automático

- TBBS_GROUP Marca el inicio de un grupo de botones

- TBBS_CHECKGROUP Marca el inicio de un grupo de botones de casilla de verificación

- TBBS_DROPDOWN Crea un botón de lista desplegable

- TBBS_AUTOSIZE El ancho del botón se calculará en función del texto del botón, no del tamaño de la imagen

- TBBS_NOPREFIX El texto del botón no tendrá un prefijo de acelerador asociado

### <a name="remarks"></a>Observaciones

El estilo de un botón determina cómo aparece el botón y cómo responde a la entrada del usuario.

Antes `SetButtonStyle`de llamar a , llame a la [GetButtonStyle](#getbuttonstyle) función miembro para recuperar el estilo de botón o separador.

> [!NOTE]
> También puede establecer estados de botón mediante el *nStyle* parámetro; sin embargo, dado que los estados de botón `SetButtonStyle` están controlados por el [controlador ON_UPDATE_COMMAND_UI,](message-map-macros-mfc.md#on_update_command_ui) cualquier estado que establezca mediante se perderá durante el siguiente procesamiento inactivo. Consulte [Cómo actualizar objetos de interfaz de usuario](../../mfc/how-to-update-user-interface-objects.md) y [TN031: Barras](../../mfc/tn031-control-bars.md) de control para obtener más información.

## <a name="ctoolbarsetbuttontext"></a><a name="setbuttontext"></a>CToolBar::SetButtonText

Llame a esta función para establecer el texto en un botón.

```
BOOL SetButtonText(
    int nIndex,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Indice del botón cuyo texto se va a establecer.

*lpszText*<br/>
Señala el texto que se va a establecer en un botón.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CToolBar::GetToolBarCtrl](#gettoolbarctrl).

## <a name="ctoolbarsetheight"></a><a name="setheight"></a>CToolBar::SetHeight

Esta función miembro establece el alto de la barra de herramientas en el valor, en píxeles, especificado en *cyHeight*.

```cpp
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>Parámetros

*cyHeight*<br/>
La altura en píxeles de la barra de herramientas.

### <a name="remarks"></a>Observaciones

Después de llamar a [SetSizes](#setsizes), utilice esta función miembro para invalidar la altura de la barra de herramientas estándar. Si la altura es demasiado pequeña, los botones se recortarán en la parte inferior.

Si no se llama a esta función, el marco de trabajo utiliza el tamaño del botón para determinar la altura de la barra de herramientas.

## <a name="ctoolbarsetsizes"></a><a name="setsizes"></a>CToolBar::SetSizes

Llame a esta función miembro para establecer los botones de la barra de herramientas en el tamaño, en píxeles, especificado en *sizeButton*.

```cpp
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>Parámetros

*sizeButton*<br/>
El tamaño en píxeles de cada botón.

*sizeImage*<br/>
El tamaño en píxeles de cada imagen.

### <a name="remarks"></a>Observaciones

El parámetro *sizeImage* debe contener el tamaño, en píxeles, de las imágenes del mapa de bits de la barra de herramientas. Las dimensiones de *sizeButton* deben ser suficientes para contener la imagen más 7 píxeles de ancho y 6 píxeles de altura adicionales. Esta función también establece la altura de la barra de herramientas para que se ajuste a los botones.

Llame a esta función miembro solo para las barras de herramientas que no siguen las recomendaciones de diseño de software de *las directrices* de interfaz de Windows para los tamaños de botón e imagen.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>Consulte también

[CTRLBARS de ejemplo de MFC](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[EJEMPLO DE MFC DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)
