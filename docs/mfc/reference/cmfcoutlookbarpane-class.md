---
title: CMFCOutlookBarPane Clase
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
ms.openlocfilehash: 82d8f1da0640e5b487a06585c72279e7d7ffdf99
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369639"
---
# <a name="cmfcoutlookbarpane-class"></a>CMFCOutlookBarPane Clase

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

Control derivado de [CMFCToolBar (Clase)](../../mfc/reference/cmfctoolbar-class.md) que se puede insertar en una barra de Outlook ( [CMFCOutlookBar (Clase)](../../mfc/reference/cmfcoutlookbar-class.md)). El panel de barra de Outlook contiene una columna de botones grandes. El usuario puede subir y bajar la lista de botones si es mayor que el panel. Cuando el usuario desasocia un panel de barra de Outlook de la barra de Outlook, puede flotar o acoplarse en la ventana de marco principal.

## <a name="syntax"></a>Sintaxis

```
class CMFCOutlookBarPane : public CMFCToolBar
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|Constructor predeterminado.|
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCOutlookBarPane::AddButton](#addbutton)|Agrega un botón al panel de la barra de Outlook.|
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|Determina si el panel se puede acoplar a otro panel o ventana de marco. (Reemplaza [CBasePane::CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached).)|
|`CMFCOutlookBarPane::CanBeRestored`|Determina si el sistema puede restaurar una barra de herramientas a su estado original después de la personalización. (Reemplaza [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFCOutlookBarPane::ClearAll](#clearall)|Libera los recursos utilizados por las imágenes en el panel de la barra de Outlook.|
|[CMFCOutlookBarPane::Crear](#create)|Crea el panel de la barra de Outlook.|
|`CMFCOutlookBarPane::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CMFCOutlookBarPane::Dock`|Llamado por el marco de trabajo para acoplar el panel de la barra de Outlook. (Invalida `CPane::Dock`).|
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|Especifica si las flechas de desplazamiento en el panel de la barra de Outlook avanzan la lista de botones por página o por botón.|
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|Devuelve el color de texto normal (no seleccionado) del panel de la barra de Outlook.|
|`CMFCOutlookBarPane::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|Determina si hay una imagen de fondo cargada para el panel de la barra de Outlook.|
|`CMFCOutlookBarPane::IsChangeState`|Determina si se puede acoplar un panel flotante. (Invalida `CPane::IsChangeState`).|
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|Determina si el borde del botón está sombreado cuando se resalta un botón y se muestra una imagen de fondo.|
|`CMFCOutlookBarPane::OnBeforeFloat`|Llamado por el marco de trabajo cuando un panel está a punto de flotar. (Reemplaza [CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|Quita el botón que tiene un identificador de comando especificado.|
|`CMFCOutlookBarPane::RestoreOriginalstate`|Restaura el estado original de una barra de herramientas. (Reemplaza [CMFCToolBar::RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate).)|
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|Establece el color de fondo.|
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|Establece la imagen de fondo.|
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|Restablece el panel de la barra de Outlook al conjunto original de botones.|
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|Establece el número de píxeles de relleno utilizados alrededor de los botones en el panel de la barra de Outlook.|
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|Establece los colores del texto normal y resaltado en el panel de la barra de Outlook.|
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|Establece el color transparente para el panel de la barra de Outlook.|
|`CMFCOutlookBarPane::SmartUpdate`|Se utiliza internamente para actualizar la barra de Outlook. (Invalida `CMFCToolBar::SmartUpdate`).|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|Especifica qué elementos del menú contextual se muestran en modo de personalización.|
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|Quita todos los botones del panel de la barra de Outlook. (Reemplaza [CMFCToolBar::RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons).)|

## <a name="remarks"></a>Observaciones

Para obtener información acerca de cómo implementar una barra de Outlook, vea [CMFCOutlookBar (Clase)](../../mfc/reference/cmfcoutlookbar-class.md).

Para obtener un ejemplo de una barra de Outlook, vea el proyecto de ejemplo OutlookDemo.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCOutlookBarPane` cómo utilizar varios métodos de la clase. En el ejemplo se muestra cómo crear un panel de barra de Outlook, habilitar el modo de desplazamiento de página, habilitar el acoplamiento y establecer el color de fondo de la barra de Outlook. Este fragmento de código forma parte del [ejemplo de Outlook Multi Views.](../../overview/visual-cpp-samples.md)

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

**Encabezado:** afxoutlookbarpane.h

## <a name="cmfcoutlookbarpaneaddbutton"></a><a name="addbutton"></a>CMFCOutlookBarPane::AddButton

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
[en] Especifica el identificador de recursos de un mapa de bits.

*lpszLabel*<br/>
[en] Especifica el texto del botón.

*iIdCommand*<br/>
[en] Especifica el identificador del control de botón.

*iInsertAt*<br/>
[en] Especifica el índice de base cero en la página de la barra de outlook en la que se va a insertar el botón.

*uiLabel*<br/>
[en] Un identificador de recurso de cadena.

*szBmpFileName*<br/>
[en] Especifica el nombre del archivo de imagen de disco que se va a cargar.

*szLabel*<br/>
[en] Especifica el texto del botón.

*hBmp*<br/>
[en] Identificador del mapa de bits de un botón.

*hIcon*<br/>
[en] Un identificador del icono de un botón.

### <a name="return-value"></a>Valor devuelto

TRUESi un botón se ha agregado correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Utilice este método para insertar un nuevo botón en la página de una barra de Outlook. La imagen del botón se puede cargar desde los recursos de la aplicación o desde un archivo de disco.

Si el identificador de página especificado por *uiPageID* es -1, el botón se inserta en la primera página.

Si el índice especificado por *iInsertAt* es -1, el botón se agrega al final de la página.

## <a name="cmfcoutlookbarpanecanbeattached"></a><a name="canbeattached"></a>CMFCOutlookBarPane::CanBeAttached

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcoutlookbarpaneclearall"></a><a name="clearall"></a>CMFCOutlookBarPane::ClearAll

Libera los recursos utilizados por las imágenes en el panel de la barra de Outlook.

```
void ClearAll();
```

### <a name="remarks"></a>Observaciones

Este método llama directamente [a CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear), que se llama en las imágenes que usa el panel de la barra de Outlook.

## <a name="cmfcoutlookbarpanecreate"></a><a name="create"></a>CMFCOutlookBarPane::Crear

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
[en] Especifica la ventana primaria del control de panel de la barra de Outlook. No debe ser NULL.

*dwStyle*<br/>
[en] El estilo de ventana.  Para obtener una lista de estilos de ventana, consulte [Estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles)de ventana .

*uiID*<br/>
[en] El identificador de control. Debe ser único para habilitar el guardado del estado del control.

*dwControlBarStyle*<br/>
[en] Especifica estilos especiales que definen el comportamiento del control de panel de la barra de Outlook cuando se separa de la barra de Outlook.

### <a name="return-value"></a>Valor devuelto

TRUESi el método se realizó correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Para construir `CMFCOutlookBarPane` un objeto, primero llame `Create`al constructor y, a continuación, llame `CMFCOutlookBarPane` a , que crea el control de panel de barra de Outlook y lo adjunta al objeto.

Para obtener `dwControlBarStyle` más información sobre cómo vea [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).

## <a name="cmfcoutlookbarpaneenablecontextmenuitems"></a><a name="enablecontextmenuitems"></a>CMFCOutlookBarPane::EnableContextMenuItems

Especifica qué elementos del menú contextual se muestran en modo de personalización.

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>Parámetros

*pButton*<br/>
[en] Puntero a un botón de barra de herramientas en el que ha pulsado un usuario.

*pPopup*<br/>
[en] Un puntero al menú contextual.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se debe mostrar el menú contextual; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Invalide este método para modificar el menú contextual estándar del marco de trabajo que el marco de trabajo muestra en modo de personalización.

La implementación predeterminada comprueba el modo de personalización ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)) y, si se establece en TRUE, deshabilita todos los elementos del menú contextual excepto **Eliminar**. A continuación, sólo pasa los `CMFCToolBar::EnableContextMenuItems`parámetros de entrada a .

> [!NOTE]
> *El menú contextual* es un sinónimo de menú contextual.

## <a name="cmfcoutlookbarpaneenablepagescrollmode"></a><a name="enablepagescrollmode"></a>CMFCOutlookBarPane::EnablePageScrollMode

Especifica si las flechas de desplazamiento en el panel de la barra de Outlook avanzan la lista de botones página por página o botón por botón.

```
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>Parámetros

*bPageScroll*<br/>
[en] Si es TRUE, habilite el modo de desplazamiento de página. Si FALSE, deshabilite el modo de desplazamiento de página.

## <a name="cmfcoutlookbarpanegetregularcolor"></a><a name="getregularcolor"></a>CMFCOutlookBarPane::GetRegularColor

Devuelve el color de texto normal (es decir, no seleccionado) del panel de la barra de Outlook.

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>Valor devuelto

El color del texto actual como un valor de color RGB.

### <a name="remarks"></a>Observaciones

Utilice [CMFCOutlookBarPane::SetTextColor](#settextcolor) para establecer el color de texto actual (regular y seleccionado) de la barra de Outlook. Puede obtener el color de texto predeterminado llamando a la función [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) con el índice COLOR_WINDOW.

## <a name="cmfcoutlookbarpaneisbackgroundtexture"></a><a name="isbackgroundtexture"></a>CMFCOutlookBarPane::IsBackgroundTexture

Determina si hay una imagen de fondo cargada para el panel de la barra de Outlook.

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi hay una imagen de fondo para mostrar; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Puede agregar una imagen de fondo mediante una llamada a [CMFCOutlookBarPane::SetBackImage](#setbackimage) función.

Si no hay ninguna imagen de fondo, el fondo se pinta con un color especificado mediante [CMFCOutlookBarPane::SetBackColor](#setbackcolor).

## <a name="cmfcoutlookbarpaneisdrawshadedhighlight"></a><a name="isdrawshadedhighlight"></a>CMFCOutlookBarPane::IsDrawShadedHighlight

Determina si el borde del botón está sombreado cuando se resalta un botón y se muestra una imagen de fondo.

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi los bordes del botón están sombreados; de lo contrario FALSO.

## <a name="cmfcoutlookbarpaneremoveallbuttons"></a><a name="removeallbuttons"></a>CMFCOutlookBarPane::RemoveAllButtons

Quita todos los botones del panel de la barra de Outlook.

```
virtual void RemoveAllButtons();
```

## <a name="cmfcoutlookbarpaneremovebutton"></a><a name="removebutton"></a>CMFCOutlookBarPane::RemoveButton

Quita el botón que tiene un identificador de comando especificado.

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>Parámetros

*iIdCommand*<br/>
[en] Especifica el identificador de comando de un botón que se va a quitar.

### <a name="return-value"></a>Valor devuelto

TRUESi el botón se ha quitado correctamente; FALSE si el identificador de comando especificado no es válido.

## <a name="cmfcoutlookbarpanesetbackcolor"></a><a name="setbackcolor"></a>CMFCOutlookBarPane::SetBackColor

Establece el color de fondo de la barra de Outlook.

```
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
[en] Especifica el nuevo color de fondo.

### <a name="remarks"></a>Observaciones

Llame a esta función para establecer el color de fondo actual para la barra de Outlook. El color de fondo solo se utiliza si no hay ninguna imagen de fondo.

## <a name="cmfcoutlookbarpanesetbackimage"></a><a name="setbackimage"></a>CMFCOutlookBarPane::SetBackImage

Establece la imagen de fondo.

```
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>Parámetros

*uiImageID*<br/>
[en] Especifica el identificador del recurso de imagen.

### <a name="remarks"></a>Observaciones

Llame a este método para establecer la imagen de fondo de la barra de Outlook. La lista de imágenes de fondo se administra mediante el incrustado [CMFCToolBarImages clase](../../mfc/reference/cmfctoolbarimages-class.md) objeto.

## <a name="cmfcoutlookbarpanesetdefaultstate"></a><a name="setdefaultstate"></a>CMFCOutlookBarPane::SetDefaultState

Restablece el panel de la barra de Outlook al conjunto original de botones.

```
void SetDefaultState();
```

### <a name="remarks"></a>Observaciones

Este método restaura los botones de la barra de Outlook al conjunto original. Este método `CMFCOutlookBarPane::RestoreOriginalstate`es como , excepto que no desencadena un redibujo del panel de la barra de Outlook.

## <a name="cmfcoutlookbarpanesetextraspace"></a><a name="setextraspace"></a>CMFCOutlookBarPane::SetExtraSpace

Establece el número de píxeles de relleno utilizados alrededor de los botones en el panel de la barra de Outlook.

```
void SetExtraSpace()
```

## <a name="cmfcoutlookbarpanesettextcolor"></a><a name="settextcolor"></a>CMFCOutlookBarPane::SetTextColor

Establece los colores del texto normal y resaltado en el panel de la barra de Outlook.

```
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>Parámetros

*clrRegText*<br/>
[en] Especifica el nuevo color para el texto no seleccionado.

*clrSelText*<br/>
[en] Especifica el nuevo color para el texto seleccionado.

## <a name="cmfcoutlookbarpanesettransparentcolor"></a><a name="settransparentcolor"></a>CMFCOutlookBarPane::SetTransparentColor

Establece el color transparente para el panel de la barra de Outlook.

```
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
Especifica el nuevo color transparente.

### <a name="remarks"></a>Observaciones

El color transparente es necesario para mostrar imágenes transparentes. Cualquier aparición de este color en una imagen se pinta con el color de fondo en su lugar.  No hay mezcla de imágenes de fondo y de primer plano.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar (Clase)](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCOutlookBar Clase](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
