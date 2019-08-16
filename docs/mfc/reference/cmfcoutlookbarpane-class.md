---
title: Clase CMFCOutlookBarPane
ms.date: 11/04/2016
f1_keywords:
- CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::AddButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::CanBeAttached
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::ClearAll
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::Create
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnablePageScrollMode
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::GetRegularColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsBackgroundTexture
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsDrawShadedHighlight
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackImage
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetDefaultState
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetExtraSpace
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTextColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTransparentColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnableContextMenuItems
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveAllButtons
helpviewer_keywords:
- CMFCOutlookBarPane [MFC], AddButton
- CMFCOutlookBarPane [MFC], CanBeAttached
- CMFCOutlookBarPane [MFC], ClearAll
- CMFCOutlookBarPane [MFC], Create
- CMFCOutlookBarPane [MFC], EnablePageScrollMode
- CMFCOutlookBarPane [MFC], GetRegularColor
- CMFCOutlookBarPane [MFC], IsBackgroundTexture
- CMFCOutlookBarPane [MFC], IsDrawShadedHighlight
- CMFCOutlookBarPane [MFC], RemoveButton
- CMFCOutlookBarPane [MFC], SetBackColor
- CMFCOutlookBarPane [MFC], SetBackImage
- CMFCOutlookBarPane [MFC], SetDefaultState
- CMFCOutlookBarPane [MFC], SetExtraSpace
- CMFCOutlookBarPane [MFC], SetTextColor
- CMFCOutlookBarPane [MFC], SetTransparentColor
- CMFCOutlookBarPane [MFC], EnableContextMenuItems
- CMFCOutlookBarPane [MFC], RemoveAllButtons
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
ms.openlocfilehash: 9ef6a06a4889119e39e72a9e495e5d4f9e17cf56
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505159"
---
# <a name="cmfcoutlookbarpane-class"></a>Clase CMFCOutlookBarPane

Para obtener más información, consulte el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\MFC** de la instalación de Visual Studio.

Un control derivado de la [clase CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) que se puede insertar en una barra de Outlook ( [clase cmfcoutlookbar (](../../mfc/reference/cmfcoutlookbar-class.md)). El panel de barra de Outlook contiene una columna de botones grandes. El usuario puede subir y bajar la lista de botones si es mayor que el panel. Cuando el usuario desasocia un panel de barra de Outlook de la barra de Outlook, puede flotar o acoplarse en la ventana de marco principal.

## <a name="syntax"></a>Sintaxis

```
class CMFCOutlookBarPane : public CMFCToolBar
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|Constructor predeterminado.|
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCOutlookBarPane::AddButton](#addbutton)|Agrega un botón al panel de la barra de Outlook.|
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|Determina si el panel se puede acoplar a otro panel o ventana de marco. (Invalida [a cbasepane:: CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached)).|
|`CMFCOutlookBarPane::CanBeRestored`|Determina si el sistema puede restaurar el estado original de una barra de herramientas después de la personalización. (Invalida [CMFCToolBar:: CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored)).|
|[CMFCOutlookBarPane::ClearAll](#clearall)|Libera los recursos utilizados por las imágenes en el panel de la barra de Outlook.|
|[CMFCOutlookBarPane::Create](#create)|Crea el panel de la barra de Outlook.|
|`CMFCOutlookBarPane::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CMFCOutlookBarPane::Dock`|Lo llama el marco de trabajo para acoplar el panel de la barra de Outlook. (Invalida `CPane::Dock`).|
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|Especifica si las flechas de desplazamiento del panel de la barra de Outlook avanzan en la lista de botones por página o por botón.|
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|Devuelve el color de texto normal (no seleccionado) del panel de la barra de Outlook.|
|`CMFCOutlookBarPane::GetThisClass`|Lo usa el marco de trabajo para obtener un puntero al objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|Determina si hay una imagen de fondo cargada para el panel de la barra de Outlook.|
|`CMFCOutlookBarPane::IsChangeState`|Determina si un panel flotante puede estar acoplado. (Invalida `CPane::IsChangeState`).|
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|Determina si el borde del botón está sombreado cuando se resalta un botón y se muestra una imagen de fondo.|
|`CMFCOutlookBarPane::OnBeforeFloat`|Lo llama el marco de trabajo cuando un panel está a punto de flotar. (Invalida [CPane:: OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat)).|
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|Quita el botón que tiene un identificador de comando especificado.|
|`CMFCOutlookBarPane::RestoreOriginalstate`|Restaura el estado original de una barra de herramientas. (Invalida [CMFCToolBar:: RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate)).|
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|Establece el color de fondo.|
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|Establece la imagen de fondo.|
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|Restablece el panel de la barra de Outlook al conjunto original de botones.|
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|Establece el número de píxeles de relleno usados alrededor de los botones del panel de la barra de Outlook.|
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|Establece los colores de texto normal y resaltado en el panel de la barra de Outlook.|
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|Establece el color transparente del panel de la barra de Outlook.|
|`CMFCOutlookBarPane::SmartUpdate`|Se usa internamente para actualizar la barra de Outlook. (Invalida `CMFCToolBar::SmartUpdate`).|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|Especifica los elementos de menú contextual que se muestran en el modo de personalización.|
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|Quita todos los botones del panel de la barra de Outlook. (Invalida [CMFCToolBar:: RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons)).|

## <a name="remarks"></a>Comentarios

Para obtener información sobre cómo implementar una barra de Outlook, consulte [clase cmfcoutlookbar (](../../mfc/reference/cmfcoutlookbar-class.md).

Para ver un ejemplo de una barra de Outlook, consulte el proyecto de ejemplo OutlookDemo.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar varios métodos de `CMFCOutlookBarPane` la clase. En el ejemplo se muestra cómo crear un panel de la barra de Outlook, habilitar el modo de desplazamiento de la página, habilitar el acoplamiento y establecer el color de fondo de la barra de Outlook. Este fragmento de código forma parte del [ejemplo de vistas múltiples de Outlook](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxoutlookbarpane. h

##  <a name="addbutton"></a>  CMFCOutlookBarPane::AddButton

Agrega un botón al panel de la barra de Outlook.

```
BOOL AddButton(
    UINT uiImage,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    UINT uiImage,
    UINT uiLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    LPCTSTR szBmpFileName,
    LPCTSTR szLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    HBITMAP hBmp,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    HICON hIcon,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1,
    BOOL bAlphaBlend=FALSE);
```

### <a name="parameters"></a>Parámetros

*uiImage*<br/>
de Especifica el identificador de recursos de un mapa de bits.

*lpszLabel*<br/>
de Especifica el texto del botón.

*iIdCommand*<br/>
de Especifica el identificador del control de botón.

*iInsertAt*<br/>
de Especifica el índice de base cero de la página de la barra de Outlook en el que se va a insertar el botón.

*uiLabel*<br/>
de IDENTIFICADOR de recurso de cadena.

*szBmpFileName*<br/>
de Especifica el nombre del archivo de imagen de disco que se va a cargar.

*szLabel*<br/>
de Especifica el texto del botón.

*hBmp*<br/>
de Identificador del mapa de bits de un botón.

*hIcon*<br/>
de Identificador del icono de un botón.

### <a name="return-value"></a>Valor devuelto

TRUE si se agregó correctamente un botón; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use este método para insertar un nuevo botón en la página de la barra de Outlook. La imagen del botón se puede cargar desde los recursos de la aplicación o desde un archivo de disco.

Si el ID. de página especificado por *uiPageID* es-1, el botón se inserta en la primera página.

Si el índice especificado por *iInsertAt* es-1, el botón se agrega al final de la página.

##  <a name="canbeattached"></a>  CMFCOutlookBarPane::CanBeAttached

Para obtener más información, consulte el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\MFC** de la instalación de Visual Studio.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="clearall"></a>  CMFCOutlookBarPane::ClearAll

Libera los recursos utilizados por las imágenes en el panel de la barra de Outlook.

```
void ClearAll();
```

### <a name="remarks"></a>Comentarios

Este método llama directamente a [CMFCToolBarImages:: Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear), al que se llama en las imágenes que se usan en el panel de la barra de Outlook.

##  <a name="create"></a>  CMFCOutlookBarPane::Create

Crea el panel de la barra de Outlook.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,
    UINT uiID=(UINT)-1,
    DWORD dwControlBarStyle=0);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
de Especifica la ventana primaria del control de panel de barra de Outlook. No debe ser NULL.

*dwStyle*<br/>
de Estilo de ventana.  Para obtener una lista de estilos de ventana, vea [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*uiID*<br/>
de IDENTIFICADOR del control. Debe ser único para habilitar el guardado del estado del control.

*dwControlBarStyle*<br/>
de Especifica estilos especiales que definen el comportamiento del control del panel de la barra de Outlook cuando se desasocia de la barra de Outlook.

### <a name="return-value"></a>Valor devuelto

TRUE si el método se realizó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Para construir un `CMFCOutlookBarPane` objeto, llame primero al constructor y, a continuación `Create`, llame a, que crea el control de panel de barra de Outlook `CMFCOutlookBarPane` y lo adjunta al objeto.

Para obtener más información `dwControlBarStyle` , vea [a cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex).

##  <a name="enablecontextmenuitems"></a>  CMFCOutlookBarPane::EnableContextMenuItems

Especifica los elementos de menú contextual que se muestran en el modo de personalización.

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>Parámetros

*pButton*<br/>
de Un puntero a un botón de la barra de herramientas en el que un usuario hizo clic.

*pPopup*<br/>
de Puntero al menú contextual.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si debe mostrarse el menú contextual; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Invalide este método para modificar el menú contextual estándar de Framework que el marco de trabajo muestra en el modo de personalización.

La implementación predeterminada comprueba el modo de personalización ( [CMFCToolBar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)) y, si se establece en true, deshabilita todos los elementos de menú contextual, excepto **Delete**. A continuación, simplemente pasa los parámetros de entrada `CMFCToolBar::EnableContextMenuItems`a.

> [!NOTE]
> El *menú contextual* es un sinónimo del menú contextual.

##  <a name="enablepagescrollmode"></a>  CMFCOutlookBarPane::EnablePageScrollMode

Especifica si las flechas de desplazamiento del panel de la barra de Outlook avanzan por la lista de botones página por página o por botón.

```
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>Parámetros

*bPageScroll*<br/>
de Si es TRUE, habilite el modo de desplazamiento de la página. Si es FALSE, deshabilite el modo de desplazamiento de página.

##  <a name="getregularcolor"></a>  CMFCOutlookBarPane::GetRegularColor

Devuelve el color del texto normal (es decir, no seleccionado) del panel de la barra de Outlook.

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>Valor devuelto

El color del texto actual como un valor de color RGB.

### <a name="remarks"></a>Comentarios

Use [CMFCOutlookBarPane:: SetTextColor](#settextcolor) para establecer el color de texto actual (normal y seleccionado) de la barra de Outlook. Puede obtener el color de texto predeterminado mediante una llamada a la función [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) con el índice COLOR_WINDOW.

##  <a name="isbackgroundtexture"></a>  CMFCOutlookBarPane::IsBackgroundTexture

Determina si hay una imagen de fondo cargada para el panel de la barra de Outlook.

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si se va a mostrar la imagen de fondo; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Puede Agregar una imagen de fondo mediante una llamada a la función [CMFCOutlookBarPane:: SetBackImage](#setbackimage) .

Si no hay ninguna imagen de fondo, el fondo se pinta con un color especificado mediante [CMFCOutlookBarPane:: SetBackColor](#setbackcolor).

##  <a name="isdrawshadedhighlight"></a>  CMFCOutlookBarPane::IsDrawShadedHighlight

Determina si el borde del botón está sombreado cuando se resalta un botón y se muestra una imagen de fondo.

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si los bordes del botón están sombreados; en caso contrario, FALSE.

##  <a name="removeallbuttons"></a>  CMFCOutlookBarPane::RemoveAllButtons

Quita todos los botones del panel de la barra de Outlook.

```
virtual void RemoveAllButtons();
```

##  <a name="removebutton"></a>  CMFCOutlookBarPane::RemoveButton

Quita el botón que tiene un identificador de comando especificado.

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>Parámetros

*iIdCommand*<br/>
de Especifica el identificador de comando de un botón que se va a quitar.

### <a name="return-value"></a>Valor devuelto

TRUE si el botón se quitó correctamente; FALSE si el identificador de comando especificado no es válido.

##  <a name="setbackcolor"></a>  CMFCOutlookBarPane::SetBackColor

Establece el color de fondo de la barra de Outlook.

```
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
de Especifica el nuevo color de fondo.

### <a name="remarks"></a>Comentarios

Llame a esta función para establecer el color de fondo actual de la barra de Outlook. El color de fondo solo se utiliza si no hay ninguna imagen de fondo.

##  <a name="setbackimage"></a>  CMFCOutlookBarPane::SetBackImage

Establece la imagen de fondo.

```
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>Parámetros

*uiImageID*<br/>
de Especifica el identificador de recurso de imagen.

### <a name="remarks"></a>Comentarios

Llame a este método para establecer la imagen de fondo de la barra de Outlook. El objeto de la [clase CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) incrustado administra la lista de imágenes de fondo.

##  <a name="setdefaultstate"></a>  CMFCOutlookBarPane::SetDefaultState

Restablece el panel de la barra de Outlook al conjunto original de botones.

```
void SetDefaultState();
```

### <a name="remarks"></a>Comentarios

Este método restaura los botones de la barra de Outlook en el conjunto original. Este método es como `CMFCOutlookBarPane::RestoreOriginalstate`, salvo que no desencadena un redibujo del panel de la barra de Outlook.

##  <a name="setextraspace"></a>  CMFCOutlookBarPane::SetExtraSpace

Establece el número de píxeles de relleno usados alrededor de los botones del panel de la barra de Outlook.

```
void SetExtraSpace()
```

##  <a name="settextcolor"></a>  CMFCOutlookBarPane::SetTextColor

Establece los colores de texto normal y resaltado en el panel de la barra de Outlook.

```
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>Parámetros

*clrRegText*<br/>
de Especifica el nuevo color para el texto no seleccionado.

*clrSelText*<br/>
de Especifica el nuevo color del texto seleccionado.

##  <a name="settransparentcolor"></a>  CMFCOutlookBarPane::SetTransparentColor

Establece el color transparente del panel de la barra de Outlook.

```
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
Especifica el nuevo color transparente.

### <a name="remarks"></a>Comentarios

El color transparente es necesario para mostrar imágenes transparentes. Cualquier aparición de este color en una imagen se pinta con el color de fondo en su lugar.  No hay ninguna combinación de imágenes de fondo y de primer plano.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCOutlookBar (clase)](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarTabCtrl (clase)](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
