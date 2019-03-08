---
title: CMFCDropDownToolbarButton (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CopyFrom
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::DropDownToolbar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::ExportToMenuButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::GetDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsDropDown
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsExtraSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCalculateSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnChangeParentWnd
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClick
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClickUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnContextHelp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCustomizeMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDraw
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDrawOnCustomizeList
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::Serialize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::SetDefaultCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::m_uiShowBarDelay
helpviewer_keywords:
- CMFCDropDownToolbarButton [MFC], CMFCDropDownToolbarButton
- CMFCDropDownToolbarButton [MFC], CopyFrom
- CMFCDropDownToolbarButton [MFC], DropDownToolbar
- CMFCDropDownToolbarButton [MFC], ExportToMenuButton
- CMFCDropDownToolbarButton [MFC], GetDropDownToolBar
- CMFCDropDownToolbarButton [MFC], IsDropDown
- CMFCDropDownToolbarButton [MFC], IsExtraSize
- CMFCDropDownToolbarButton [MFC], OnCalculateSize
- CMFCDropDownToolbarButton [MFC], OnChangeParentWnd
- CMFCDropDownToolbarButton [MFC], OnClick
- CMFCDropDownToolbarButton [MFC], OnClickUp
- CMFCDropDownToolbarButton [MFC], OnContextHelp
- CMFCDropDownToolbarButton [MFC], OnCustomizeMenu
- CMFCDropDownToolbarButton [MFC], OnDraw
- CMFCDropDownToolbarButton [MFC], OnDrawOnCustomizeList
- CMFCDropDownToolbarButton [MFC], Serialize
- CMFCDropDownToolbarButton [MFC], SetDefaultCommand
- CMFCDropDownToolbarButton [MFC], m_uiShowBarDelay
ms.assetid: bc9d69e6-bd3e-4c15-9368-e80a504a0ba7
ms.openlocfilehash: b33e50328fd3c8997774515f248780edda6bcc75
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275498"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>CMFCDropDownToolbarButton (clase)

Un tipo de botón de la barra de herramientas que se comporta como un botón normal cuando se hace clic en él. Sin embargo, se abre una barra de herramientas desplegable ( [CMFCDropDownToolBar (clase)](../../mfc/reference/cmfcdropdowntoolbar-class.md) si el usuario presiona y mantiene el botón de la barra de herramientas.

## <a name="syntax"></a>Sintaxis

```
class CMFCDropDownToolbarButton : public CMFCToolBarButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|Construye un objeto `CMFCDropDownToolbarButton`.|
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|Copia las propiedades de otro botón de barra de herramientas a la actual. (Invalida [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCDropDownToolbarButton::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|Se abre una barra de herramientas desplegable.|
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|Copia el texto en el botón de barra de herramientas a un menú. (Invalida [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton).)|
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|Recupera la barra de herramientas de la lista desplegable que está asociado con el botón.|
|`CMFCDropDownToolbarButton::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|Determina si la barra de herramientas desplegable está abierto actualmente.|
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|Determina si se puede mostrar el botón con un borde extendido. (Invalida [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).)|
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|Lo llama el marco de trabajo para calcular el tamaño del botón para el contexto de dispositivo especificado y el estado de acoplamiento. (Invalida [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|`CMFCDropDownToolbarButton::OnCancelMode`|Lo llama el marco de trabajo para controlar la [WM_CANCELMODE](/windows/desktop/winmsg/wm-cancelmode) mensaje. (Invalida `CMCToolBarButton::OnCancelMode`).|
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|Lo llama el marco cuando el botón se inserta en una nueva barra de herramientas. (Invalida [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCDropDownToolbarButton::OnClick](#onclick)|Lo llama el marco cuando el usuario hace clic en el botón del mouse. (Invalida [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|Lo llama el marco cuando el usuario suelta el botón del mouse. (Invalida [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup).)|
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|Lo llama el marco de trabajo cuando la barra de herramientas primario controla un mensaje WM_HELPHITTEST. (Invalida [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|Cuando la aplicación muestra un menú contextual en la barra de herramientas primario se modifica el menú proporcionado. (Invalida [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu).)|
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|Lo llama el marco de trabajo para dibujar el botón mediante el uso de las opciones y estilos especificados. (Invalida [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Lo llama el marco de trabajo para dibujar el botón de la **comandos** panel de la **personalizar** cuadro de diálogo. (Invalida [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCDropDownToolbarButton::Serialize](#serialize)|Lee este objeto de un archivo o lo escribe en un archivo. (Invalida [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|Establece el comando predeterminado que usa el marco cuando un usuario hace clic en el botón.|

### <a name="data-members"></a>Miembros de datos

|nombre|Descripción|
|----------|-----------------|
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|Especifica el período de tiempo que un usuario debe mantenerse presionada el botón del mouse antes de que aparezca la barra de herramientas desplegable.|

## <a name="remarks"></a>Comentarios

Un `CMFCDropDownToolBarButton` difiere de un botón normal porque tiene una pequeña flecha en la esquina inferior derecha del botón. Después de que el usuario selecciona un botón de la barra de herramientas de la lista desplegable, el marco de trabajo muestra su icono en el botón de barra de herramientas de nivel superior (el botón con la flecha pequeña situada en la esquina inferior derecha).

Para obtener información sobre cómo implementar una barra de herramientas de la lista desplegable, vea [CMFCDropDownToolBar (clase)](../../mfc/reference/cmfcdropdowntoolbar-class.md).

El `CMFCDropDownToolBarButton` objeto puede exportarse a un [CMFCToolBarMenuButton (clase)](../../mfc/reference/cmfctoolbarmenubutton-class.md) de objeto y se muestra como un botón de menú con un menú emergente.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdropdowntoolbar.h

##  <a name="copyfrom"></a>  CMFCDropDownToolbarButton::CopyFrom

Copia las propiedades de otro botón de barra de herramientas a la actual.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
[in] Una referencia al botón de origen desde el que se va a copiar.

### <a name="remarks"></a>Comentarios

Llame a este método para copiar otro botón de barra de herramientas en este botón de barra de herramientas. *src* debe ser de tipo `CMFCDropDownToolbarButton`.

##  <a name="cmfcdropdowntoolbarbutton"></a>  CMFCDropDownToolbarButton::CMFCDropDownToolbarButton

Construye un objeto `CMFCDropDownToolbarButton`.

```
CMFCDropDownToolbarButton();

CMFCDropDownToolbarButton(
    LPCTSTR lpszName,
    CMFCDropDownToolBar* pToolBar);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
[in] El texto predeterminado del botón.

*pToolBar*<br/>
[in] Un puntero a la `CMFCDropDownToolBar` objeto que se muestra cuando el usuario presiona el botón.

### <a name="remarks"></a>Comentarios

La segunda sobrecarga del constructor de copia en el botón de lista desplegable el primer botón de la barra de herramientas que *pToolBar* especifica.

Normalmente, un botón de barra de herramientas desplegable usa el texto en el botón usado más recientemente en la barra de herramientas que *pToolBar* especifica. Utiliza el texto especificado por *lpszName* cuando el botón se convierte en un botón de menú o se muestra en el **comandos** pestaña de la **personalizar** cuadro de diálogo. Para obtener más información sobre la **personalizar** cuadro de diálogo, vea [CMFCToolBarsCustomizeDialog (clase)](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCDropDownToolbarButton` clase. Este fragmento de código forma parte de la [ejemplo de demostración de Visual Studio](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]

##  <a name="dropdowntoolbar"></a>  CMFCDropDownToolbarButton::DropDownToolbar

Se abre una barra de herramientas desplegable.

```
BOOL DropDownToolbar(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
[in] La ventana primaria del marco de la lista desplegable, o NULL para usar la ventana primaria del botón de barra de herramientas desplegable.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método es correcto; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

El [CMFCDropDownToolbarButton::OnClick](#onclick) método llama a este método para abrir la barra de herramientas desplegable cuando el usuario presiona y mantiene el botón de la barra de herramientas.

Este método crea la barra de herramientas desplegable utilizando el [CMFCDropDownFrame::Create](../../mfc/reference/cmfcdropdownframe-class.md#create) método. Si la barra de herramientas primario está acoplado vertical, este método coloca la barra de herramientas desplegable en el lado izquierdo o derecho de la barra de herramientas principal, según el ajuste. En caso contrario, este método coloca la barra de herramientas de la lista desplegable debajo de la barra de herramientas primario.

Este método produce un error si *conquistado* es NULL y el botón de barra de herramientas desplegable no tiene una ventana primaria.

##  <a name="exporttomenubutton"></a>  CMFCDropDownToolbarButton::ExportToMenuButton

Copia el texto en el botón de barra de herramientas a un menú.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parámetros

*menuButton*<br/>
[in] Una referencia al botón de menú de destino.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método es correcto; de lo contrario, 0.

### <a name="remarks"></a>Comentarios

Este método llama a la implementación de la clase base ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) y, a continuación, se anexa al botón de menú destino un menú emergente que contiene cada elemento de menú de la barra de herramientas en este botón. Este método no anexa submenús en el menú emergente.

Este método produce un error si la barra de herramientas principal, `m_pToolBar`, es NULL o la implementación de la clase base devuelve FALSE.

##  <a name="getdropdowntoolbar"></a>  CMFCDropDownToolbarButton::GetDropDownToolBar

Recupera la barra de herramientas de la lista desplegable que está asociado con el botón.

```
CMFCToolBar* GetDropDownToolBar() const;
```

### <a name="return-value"></a>Valor devuelto

La barra de herramientas de lista desplegable que está asociado con el botón.

### <a name="remarks"></a>Comentarios

Este método devuelve el `m_pToolBar` miembro de datos.

##  <a name="isdropdown"></a>  CMFCDropDownToolbarButton::IsDropDown

Determina si la barra de herramientas desplegable está abierto actualmente.

```
BOOL IsDropDown() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la barra de herramientas desplegable está abierto actualmente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

El marco de trabajo abre la barra de herramientas desplegable mediante el [CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar) método. El marco de trabajo cierra la barra de herramientas desplegable cuando el usuario presiona el botón izquierdo del ratón en el área no cliente de la barra de herramientas desplegable.

##  <a name="isextrasize"></a>  CMFCDropDownToolbarButton::IsExtraSize

Determina si se puede mostrar el botón con un borde extendido.

```
virtual BOOL IsExtraSize() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se puede mostrar el botón de barra de herramientas con un borde extendido; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de los bordes extendidos, vea [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).

##  <a name="m_uishowbardelay"></a>  CMFCDropDownToolbarButton::m_uiShowBarDelay

Especifica el período de tiempo que un usuario debe mantenerse presionada el botón del mouse antes de que aparezca la barra de herramientas desplegable.

```
static UINT m_uiShowBarDelay;
```

### <a name="remarks"></a>Comentarios

El tiempo de retraso se mide en milisegundos. El valor predeterminado es 500. Puede establecer otro retraso cambiando el valor de este miembro de datos compartido.

##  <a name="oncalculatesize"></a>  CMFCDropDownToolbarButton::OnCalculateSize

Lo llama el marco de trabajo para calcular el tamaño del botón para el contexto de dispositivo especificado y el estado de acoplamiento.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] El contexto de dispositivo que muestra el botón.

*sizeDefault*<br/>
[in] El tamaño predeterminado del botón.

*bHorz*<br/>
[in] El estado de acoplamiento de la barra de herramientas primario. Este parámetro es TRUE si la barra de herramientas está acoplado horizontalmente o está flotando, o FALSE si la barra de herramientas está acoplada verticalmente.

### <a name="return-value"></a>Valor devuelto

Un `SIZE` estructura que contiene las dimensiones del botón, en píxeles.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)) agregando el ancho de la flecha desplegable a la dimensión horizontal del tamaño del botón.

##  <a name="onchangeparentwnd"></a>  CMFCDropDownToolbarButton::OnChangeParentWnd

Lo llama el marco cuando el botón se inserta en una nueva barra de herramientas.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[in] La nueva ventana primaria.

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de la clase base ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) desactivando la etiqueta de texto ( [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) y estableciendo el [ CMFCToolBarButton::m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext) y [CMFCToolBarButton::m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton) los miembros de datos en FALSE.

##  <a name="onclick"></a>  CMFCDropDownToolbarButton::OnClick

Lo llama el marco cuando el usuario hace clic en el botón del mouse.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
[in] La ventana primaria del botón de barra de herramientas.

*bDelay*<br/>
[in] TRUE si el mensaje debe controlarse con un retraso.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón procesa el mensaje clic; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base, [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), actualizando el estado de la barra de herramientas desplegable.

Cuando un usuario hace clic en el botón de barra de herramientas, este método crea un temporizador que espera el período de tiempo especificado por el [CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay) miembro de datos y, a continuación, se abre la lista desplegable barra de herramientas mediante el uso de la [CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar) método. Este método cierra la barra de herramientas desplegable en la segunda vez que el usuario hace clic en el botón de barra de herramientas.

##  <a name="onclickup"></a>  CMFCDropDownToolbarButton::OnClickUp

Lo llama el marco cuando el usuario suelta el botón del mouse.

```
virtual BOOL OnClickUp();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón procesa el mensaje clic; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base, [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup), actualizando el estado de la barra de herramientas desplegable.

Este método detiene el temporizador de la barra de herramientas de lista desplegable si está activa. Cierra la barra de herramientas de la lista desplegable si está abierto.

Para obtener más información acerca de la barra de herramientas de lista desplegable y el temporizador de la barra de herramientas de lista desplegable, vea [CMFCDropDownToolbarButton::OnClick](#onclick).

##  <a name="oncontexthelp"></a>  CMFCDropDownToolbarButton::OnContextHelp

Lo llama el marco de trabajo cuando la barra de herramientas primario controla un mensaje WM_HELPHITTEST.

```
virtual BOOL OnContextHelp(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
[in] La ventana primaria del botón de barra de herramientas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón procesa el mensaje de ayuda; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)) mediante una llamada a la [CMFCDropDownToolbarButton::OnClick](#onclick) método con *bDelay*establecida en FALSE. Este método devuelve el valor devuelto por [CMFCDropDownToolbarButton::OnClick](#onclick).

Para obtener más información sobre el mensaje WM_HELPHITTEST, vea [TN028: Compatibilidad con la Ayuda contextual](../../mfc/tn028-context-sensitive-help-support.md).

##  <a name="oncustomizemenu"></a>  CMFCDropDownToolbarButton::OnCustomizeMenu

Cuando la aplicación muestra un menú contextual en la barra de herramientas primario se modifica el menú proporcionado.

```
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Parámetros

*pMenu*<br/>
[in] Para personalizar el menú.

### <a name="return-value"></a>Valor devuelto

Este método devuelve TRUE.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)) al deshabilitar los siguientes elementos:

- **Copiar imagen del botón**

- **Apariencia del botón**

- **Image**

- **Texto**

- **Imagen y texto**

Invalide este método para modificar el menú contextual que muestra el marco de trabajo en el modo de personalización.

##  <a name="ondraw"></a>  CMFCDropDownToolbarButton::OnDraw

Lo llama el marco de trabajo para dibujar el botón mediante el uso de las opciones y estilos especificados.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz = TRUE,
    BOOL bCustomizeMode = FALSE,
    BOOL bHighlight = FALSE,
    BOOL bDrawBorder = TRUE,
    BOOL bGrayDisabledButtons = TRUE);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] El contexto de dispositivo que muestra el botón.

*rect*<br/>
[in] El rectángulo delimitador del botón.

*pImages*<br/>
[in] La colección de imágenes de barra de herramientas que está asociada con el botón.

*bHorz*<br/>
[in] El estado de acoplamiento de la barra de herramientas primario. Este parámetro es TRUE cuando el botón está acoplado horizontalmente y FALSE cuando el botón está acoplado vertical.

*bCustomizeMode*<br/>
[in] Especifica si la barra de herramientas está en modo de personalización. Este parámetro es TRUE cuando la barra de herramientas está en modo de personalización y FALSE cuando la barra de herramientas no está en modo de personalización.

*bHighlight*<br/>
[in] Especifica si el botón está resaltado. Este parámetro es TRUE cuando el botón está resaltado y FALSE cuando no se resalta el botón.

*bDrawBorder*<br/>
[in] Especifica si el botón debe mostrar su borde. Este parámetro es TRUE cuando el botón debe mostrar su borde y FALSE cuando el botón no debe mostrar su borde.

*bGrayDisabledButtons*<br/>
[in] Especifica si se deben sombrear los botones deshabilitados o usar la colección de imágenes deshabilitado. Este parámetro es TRUE cuando los botones deshabilitados deberían ser sombreada y FALSE cuando este método debe usar la colección de imágenes deshabilitado.

### <a name="remarks"></a>Comentarios

Invalide este método para personalizar el dibujo del botón de barra de herramientas.

##  <a name="ondrawoncustomizelist"></a>  CMFCDropDownToolbarButton::OnDrawOnCustomizeList

Lo llama el marco de trabajo para dibujar el botón de la **comandos** panel de la **personalizar** cuadro de diálogo.

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] El contexto de dispositivo que muestra el botón.

*rect*<br/>
[in] El rectángulo delimitador del botón.

*bSelected*<br/>
[in] Si se selecciona el botón. Si este parámetro es TRUE, se selecciona el botón. Si este parámetro es FALSE, no se selecciona el botón.

### <a name="return-value"></a>Valor devuelto

El ancho, en píxeles, del botón en el contexto de dispositivo especificado.

### <a name="remarks"></a>Comentarios

Este método es invocado por el cuadro de diálogo de personalización ( **comandos** pestaña) cuando se requiere el botón para que se muestre en el cuadro de lista dibujado por el propietario.

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)) cambiando la etiqueta de texto del botón en el nombre del botón (es decir, en el valor de la *lpszName* parámetro que se pasó al constructor).

##  <a name="serialize"></a>  CMFCDropDownToolbarButton::Serialize

Lee este objeto de un archivo o lo escribe en un archivo.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

*ar*<br/>
[in] La `CArchive` objeto desde la que o que se va a serializar.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)) al serializar el identificador de recurso de la barra de herramientas primario. Cuando se está cargando el archivo ( [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) devuelve un valor distinto de cero), este método establece el `m_pToolBar` miembro de datos en la barra de herramientas que contiene el identificador de recurso serializado.

##  <a name="setdefaultcommand"></a>  CMFCDropDownToolbarButton::SetDefaultCommand

Establece el comando predeterminado que usa el marco cuando un usuario hace clic en el botón.

```
void SetDefaultCommand(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[in] El identificador del comando predeterminado.

### <a name="remarks"></a>Comentarios

Llame a este método para especificar un comando predeterminado que el marco de trabajo se ejecuta cuando el usuario hace clic en el botón. Un elemento con el identificador de comando especificado por *uiCmd* debe estar ubicado en la barra de herramientas de lista desplegable del elemento primario.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar (clase)](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarMenuButton (clase)](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[Tutorial: Insertar controles en barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)
