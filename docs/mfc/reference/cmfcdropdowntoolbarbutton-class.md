---
title: CMFCDropDownToolbarButton (Clase)
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
ms.openlocfilehash: d62d5ecb0962f74a5dac1658c207cfb08cf12588
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367606"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>CMFCDropDownToolbarButton (Clase)

Un tipo de botón de la barra de herramientas que se comporta como un botón normal cuando se hace clic en él. Sin embargo, abre una barra de herramientas desplegable ( [CMFCDropDownToolBar (Clase)](../../mfc/reference/cmfcdropdowntoolbar-class.md) si el usuario presiona y mantiene presionado el botón de la barra de herramientas hacia abajo.

## <a name="syntax"></a>Sintaxis

```
class CMFCDropDownToolbarButton : public CMFCToolBarButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|Construye un objeto `CMFCDropDownToolbarButton`.|
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|Copia las propiedades de otro botón de la barra de herramientas en el botón actual. (Reemplaza [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCDropDownToolbarButton::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|Abre una barra de herramientas desplegable.|
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|Copia texto del botón de la barra de herramientas en un menú. (Reemplaza [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton).)|
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|Recupera la barra de herramientas desplegable asociada al botón.|
|`CMFCDropDownToolbarButton::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|Determina si la barra de herramientas desplegable está abierta actualmente.|
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|Determina si el botón se puede mostrar con un borde extendido. (Reemplaza [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).)|
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|Llamado por el marco de trabajo para calcular el tamaño del botón para el contexto de dispositivo especificado y el estado de acoplamiento. (Reemplaza [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|`CMFCDropDownToolbarButton::OnCancelMode`|Llamado por el marco de trabajo para controlar el [mensaje de WM_CANCELMODE.](/windows/win32/winmsg/wm-cancelmode) (Invalida `CMCToolBarButton::OnCancelMode`).|
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|Llamado por el marco de trabajo cuando el botón se inserta en una nueva barra de herramientas. (Reemplaza [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCDropDownToolbarButton::OnClick](#onclick)|Llamado por el marco de trabajo cuando el usuario hace clic en el botón del mouse. (Reemplaza [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|Llamado por el marco de trabajo cuando el usuario suelta el botón del mouse. (Reemplaza [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup).)|
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|Llamado por el marco de trabajo cuando la barra de herramientas primaria controla un mensaje de WM_HELPHITTEST. (Reemplaza [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|Modifica el menú proporcionado cuando la aplicación muestra un menú contextual en la barra de herramientas principal. (Reemplaza [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu).)|
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|Llamado por el marco de trabajo para dibujar el botón mediante el uso de los estilos y opciones especificados. (Reemplaza [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Llamado por el marco de trabajo para dibujar el botón en el **comandos** panel de la **personalizar** cuadro de diálogo. (Reemplaza [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCDropDownToolbarButton::Serialize](#serialize)|Lee este objeto de un archivo o lo escribe en un archivo. (Reemplaza [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|Establece el comando predeterminado que utiliza el marco de trabajo cuando un usuario hace clic en el botón.|

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|Especifica el tiempo que un usuario debe mantener pulsado el botón del mouse antes de que aparezca la barra de herramientas desplegable.|

## <a name="remarks"></a>Observaciones

A `CMFCDropDownToolBarButton` difiere de un botón ordinario en que tiene una pequeña flecha en la esquina inferior derecha del botón. Después de que el usuario selecciona un botón de la barra de herramientas desplegable, el marco de trabajo muestra su icono en el botón de barra de herramientas de nivel superior (el botón con la flecha pequeña en la esquina inferior derecha).

Para obtener información sobre cómo implementar una barra de herramientas desplegable, vea [CMFCDropDownToolBar (Clase)](../../mfc/reference/cmfcdropdowntoolbar-class.md).

El `CMFCDropDownToolBarButton` objeto se puede exportar a un [CMFCToolBarMenuButton clase](../../mfc/reference/cmfctoolbarmenubutton-class.md) objeto y mostrarse como un botón de menú con un menú emergente.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdropdowntoolbar.h

## <a name="cmfcdropdowntoolbarbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCDropDownToolbarButton::CopyFrom

Copia las propiedades de otro botón de la barra de herramientas en el botón actual.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
[en] Una referencia al botón de origen desde el que se copia.

### <a name="remarks"></a>Observaciones

Llame a este método para copiar otro botón de la barra de herramientas en este botón de la barra de herramientas. *src* debe ser `CMFCDropDownToolbarButton`de tipo .

## <a name="cmfcdropdowntoolbarbuttoncmfcdropdowntoolbarbutton"></a><a name="cmfcdropdowntoolbarbutton"></a>CMFCDropDownToolbarButton::CMFCDropDownToolbarButton

Construye un objeto `CMFCDropDownToolbarButton`.

```
CMFCDropDownToolbarButton();

CMFCDropDownToolbarButton(
    LPCTSTR lpszName,
    CMFCDropDownToolBar* pToolBar);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
[en] El texto predeterminado del botón.

*pToolBar*<br/>
[en] Puntero al `CMFCDropDownToolBar` objeto que se muestra cuando el usuario presiona el botón.

### <a name="remarks"></a>Observaciones

La segunda sobrecarga del constructor copia en el botón desplegable el primer botón de la barra de herramientas que *pToolBar* especifica.

Normalmente, un botón de barra de herramientas desplegable utiliza el texto del botón utilizado más recientemente en la barra de herramientas que *pToolBar* especifica. Utiliza el texto especificado por *lpszName* cuando el botón se convierte en un botón de menú o se muestra en la ficha **Comandos** del cuadro de diálogo **Personalizar.** Para obtener más información sobre el cuadro de diálogo **Personalizar,** vea [CMFCToolBarsCustomizeDialog (Clase)](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCDropDownToolbarButton` cómo construir un objeto de la clase. Este fragmento de código forma parte del [ejemplo de demostración](../../overview/visual-cpp-samples.md)de Visual Studio.

[!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]

## <a name="cmfcdropdowntoolbarbuttondropdowntoolbar"></a><a name="dropdowntoolbar"></a>CMFCDropDownToolbarButton::DropDownToolbar

Abre una barra de herramientas desplegable.

```
BOOL DropDownToolbar(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
[en] La ventana primaria del marco desplegable o NULL para usar la ventana primaria del botón de barra de herramientas desplegable.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método es correcto; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El [CMFCDropDownToolbarButton::OnClick](#onclick) método llama a este método para abrir la barra de herramientas desplegable cuando el usuario presiona y mantiene presionado el botón de barra de herramientas hacia abajo.

Este método crea la barra de herramientas desplegable mediante el [CMFCDropDownFrame::Create](../../mfc/reference/cmfcdropdownframe-class.md#create) método. Si la barra de herramientas principal está acoplada verticalmente, este método coloca la barra de herramientas desplegable en el lado izquierdo o derecho de la barra de herramientas principal, dependiendo del ajuste. De lo contrario, este método coloca la barra de herramientas desplegable debajo de la barra de herramientas principal.

Este método produce un error si *pWnd* es NULL y el botón de barra de herramientas desplegable no tiene una ventana primaria.

## <a name="cmfcdropdowntoolbarbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCDropDownToolbarButton::ExportToMenuButton

Copia texto del botón de la barra de herramientas en un menú.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parámetros

*menuButton*<br/>
[en] Una referencia al botón de menú de destino.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método es correcto; de lo contrario, 0.

### <a name="remarks"></a>Observaciones

Este método llama a la implementación de la clase base ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) y, a continuación, anexa al botón de menú de destino un menú emergente que contiene cada elemento de menú de la barra de herramientas en este botón. Este método no anexa submenús al menú emergente.

Este método produce un `m_pToolBar`error si la barra de herramientas primaria, , es NULL o la implementación de la clase base devuelve FALSE.

## <a name="cmfcdropdowntoolbarbuttongetdropdowntoolbar"></a><a name="getdropdowntoolbar"></a>CMFCDropDownToolbarButton::GetDropDownToolBar

Recupera la barra de herramientas desplegable asociada al botón.

```
CMFCToolBar* GetDropDownToolBar() const;
```

### <a name="return-value"></a>Valor devuelto

La barra de herramientas desplegable que está asociada con el botón.

### <a name="remarks"></a>Observaciones

Este método `m_pToolBar` devuelve el miembro de datos.

## <a name="cmfcdropdowntoolbarbuttonisdropdown"></a><a name="isdropdown"></a>CMFCDropDownToolbarButton::IsDropDown

Determina si la barra de herramientas desplegable está abierta actualmente.

```
BOOL IsDropDown() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la barra de herramientas desplegable está abierta actualmente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El marco de trabajo abre la barra de herramientas desplegable mediante el [CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar) método. El marco de trabajo cierra la barra de herramientas desplegable cuando el usuario presiona el botón izquierdo del ratón en el área no cliente de la barra de herramientas desplegable.

## <a name="cmfcdropdowntoolbarbuttonisextrasize"></a><a name="isextrasize"></a>CMFCDropDownToolbarButton::IsExtraSize

Determina si el botón se puede mostrar con un borde extendido.

```
virtual BOOL IsExtraSize() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón de la barra de herramientas se puede mostrar con un borde extendido; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Para obtener más información acerca de los bordes extendidos, vea [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).

## <a name="cmfcdropdowntoolbarbuttonm_uishowbardelay"></a><a name="m_uishowbardelay"></a>CMFCDropDownToolbarButton::m_uiShowBarDelay

Especifica el tiempo que un usuario debe mantener pulsado el botón del mouse antes de que aparezca la barra de herramientas desplegable.

```
static UINT m_uiShowBarDelay;
```

### <a name="remarks"></a>Observaciones

El tiempo de retardo se mide en milisegundos. El valor predeterminado es 500. Puede establecer otro retraso cambiando el valor de este miembro de datos compartidos.

## <a name="cmfcdropdowntoolbarbuttononcalculatesize"></a><a name="oncalculatesize"></a>CMFCDropDownToolbarButton::OnCalculateSize

Llamado por el marco de trabajo para calcular el tamaño del botón para el contexto de dispositivo especificado y el estado de acoplamiento.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] El contexto del dispositivo que muestra el botón.

*sizeDefault*<br/>
[en] El tamaño predeterminado del botón.

*bHorz*<br/>
[en] El estado de acoplamiento de la barra de herramientas principal. Este parámetro es TRUE si la barra de herramientas está acoplada horizontalmente o está flotante, o FALSE si la barra de herramientas está acoplada verticalmente.

### <a name="return-value"></a>Valor devuelto

Estructura `SIZE` que contiene las dimensiones del botón, en píxeles.

### <a name="remarks"></a>Observaciones

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)) agregando el ancho de la flecha desplegable a la dimensión horizontal del tamaño del botón.

## <a name="cmfcdropdowntoolbarbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCDropDownToolbarButton::OnChangeParentWnd

Llamado por el marco de trabajo cuando el botón se inserta en una nueva barra de herramientas.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[en] La nueva ventana primaria.

### <a name="remarks"></a>Observaciones

Este método reemplaza la implementación de la clase base ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) borrando la etiqueta de texto ( [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) y estableciendo el [CMFCToolBarButton::m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext) y [CMFCToolBarButton::m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton) miembros de datos en FALSE.

## <a name="cmfcdropdowntoolbarbuttononclick"></a><a name="onclick"></a>CMFCDropDownToolbarButton::OnClick

Llamado por el marco de trabajo cuando el usuario hace clic en el botón del mouse.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
[en] La ventana principal del botón de la barra de herramientas.

*bDelay*<br/>
[en] TRUESi el mensaje debe controlarse con un retraso.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón procesa el mensaje de clic; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Este método extiende la implementación de la clase base, [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), actualizando el estado de la barra de herramientas desplegable.

Cuando un usuario hace clic en el botón de barra de herramientas, este método crea un temporizador que espera la longitud de tiempo especificada por el [CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay) miembro de datos y, a continuación, abre la barra de herramientas desplegable mediante el [CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar) método de datos. Este método cierra la barra de herramientas desplegable la segunda vez que el usuario hace clic en el botón de la barra de herramientas.

## <a name="cmfcdropdowntoolbarbuttononclickup"></a><a name="onclickup"></a>CMFCDropDownToolbarButton::OnClickUp

Llamado por el marco de trabajo cuando el usuario suelta el botón del mouse.

```
virtual BOOL OnClickUp();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón procesa el mensaje de clic; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Este método extiende la implementación de la clase base, [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup), actualizando el estado de la barra de herramientas desplegable.

Este método detiene el temporizador de la barra de herramientas desplegable si está activo. Cierra la barra de herramientas desplegable si está abierta.

Para obtener más información acerca de la barra de herramientas desplegable y el temporizador de la barra de herramientas desplegable, vea [CMFCDropDownToolbarButton::OnClick](#onclick).

## <a name="cmfcdropdowntoolbarbuttononcontexthelp"></a><a name="oncontexthelp"></a>CMFCDropDownToolbarButton::OnContextHelp

Llamado por el marco de trabajo cuando la barra de herramientas primaria controla un mensaje de WM_HELPHITTEST.

```
virtual BOOL OnContextHelp(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
[en] La ventana principal del botón de la barra de herramientas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón procesa el mensaje de ayuda; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)) mediante una llamada a la [CMFCDropDownToolbarButton::OnClick](#onclick) método con *bDelay* establecido en FALSE. Este método devuelve el valor devuelto por [CMFCDropDownToolbarButton::OnClick](#onclick).

Para obtener más información acerca del mensaje de WM_HELPHITTEST, vea [TN028: Compatibilidad](../../mfc/tn028-context-sensitive-help-support.md)con ayuda contextual .

## <a name="cmfcdropdowntoolbarbuttononcustomizemenu"></a><a name="oncustomizemenu"></a>CMFCDropDownToolbarButton::OnCustomizeMenu

Modifica el menú proporcionado cuando la aplicación muestra un menú contextual en la barra de herramientas principal.

```
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Parámetros

*pMenu*<br/>
[en] El menú para personalizar.

### <a name="return-value"></a>Valor devuelto

Este método devuelve TRUE.

### <a name="remarks"></a>Observaciones

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)) deshabilitando los siguientes elementos de menú:

- **Copiar imagen de botón**

- **Apariencia del botón**

- **Imagen**

- **Texto**

- **Imagen y texto**

Invalide este método para modificar el menú contextual que el marco de trabajo muestra en modo de personalización.

## <a name="cmfcdropdowntoolbarbuttonondraw"></a><a name="ondraw"></a>CMFCDropDownToolbarButton::OnDraw

Llamado por el marco de trabajo para dibujar el botón mediante el uso de los estilos y opciones especificados.

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
[en] El contexto del dispositivo que muestra el botón.

*Rect*<br/>
[en] El rectángulo delimitador del botón.

*pImages*<br/>
[en] La colección de imágenes de la barra de herramientas asociada al botón.

*bHorz*<br/>
[en] El estado de acoplamiento de la barra de herramientas principal. Este parámetro es TRUE cuando el botón se acopla horizontalmente y FALSE cuando el botón se acopla verticalmente.

*bCustomizeMode*<br/>
[en] Especifica si la barra de herramientas está en modo de personalización. Este parámetro es TRUE cuando la barra de herramientas está en modo de personalización y FALSE cuando la barra de herramientas no está en modo de personalización.

*bResaltar*<br/>
[en] Especifica si el botón está resaltado. Este parámetro es TRUE cuando se resalta el botón y FALSE cuando el botón no está resaltado.

*bDrawBorder*<br/>
[en] Especifica si el botón debe mostrar su borde. Este parámetro es TRUE cuando el botón debe mostrar su borde y FALSE cuando el botón no debe mostrar su borde.

*bGrayDisabledButtons*<br/>
[en] Especifica si se deben sombrear los botones deshabilitados o utilizar la colección de imágenes deshabilitadas. Este parámetro es TRUE cuando los botones deshabilitados deben estar sombreados y FALSE cuando este método debe usar la colección de imágenes deshabilitadas.

### <a name="remarks"></a>Observaciones

Invalide este método para personalizar el dibujo del botón de la barra de herramientas.

## <a name="cmfcdropdowntoolbarbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCDropDownToolbarButton::OnDrawOnCustomizeList

Llamado por el marco de trabajo para dibujar el botón en el **comandos** panel de la **personalizar** cuadro de diálogo.

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] El contexto del dispositivo que muestra el botón.

*Rect*<br/>
[en] El rectángulo delimitador del botón.

*bSeleccionado*<br/>
[en] Si el botón está seleccionado. Si este parámetro es TRUE, se selecciona el botón. Si este parámetro es FALSE, el botón no está seleccionado.

### <a name="return-value"></a>Valor devuelto

El ancho, en píxeles, del botón en el contexto del dispositivo especificado.

### <a name="remarks"></a>Observaciones

El cuadro de diálogo de personalización (ficha **Comandos)** llama a este método cuando se requiere que el botón se muestre en el cuadro de lista de dibujo del propietario.

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)) cambiando la etiqueta de texto del botón al nombre del botón (es decir, al valor del parámetro *lpszName* que pasó al constructor).

## <a name="cmfcdropdowntoolbarbuttonserialize"></a><a name="serialize"></a>CMFCDropDownToolbarButton::Serialize

Lee este objeto de un archivo o lo escribe en un archivo.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

*ar*<br/>
[en] Objeto `CArchive` desde el que se va a serializar o al que se va a serializar.

### <a name="remarks"></a>Observaciones

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)) serializando el identificador de recurso de la barra de herramientas primaria. Cuando el archivo se carga ( [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) devuelve un `m_pToolBar` valor distinto de cero), este método establece el miembro de datos en la barra de herramientas que contiene el identificador de recurso serializado.

## <a name="cmfcdropdowntoolbarbuttonsetdefaultcommand"></a><a name="setdefaultcommand"></a>CMFCDropDownToolbarButton::SetDefaultCommand

Establece el comando predeterminado que utiliza el marco de trabajo cuando un usuario hace clic en el botón.

```
void SetDefaultCommand(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[en] El ID del comando predeterminado.

### <a name="remarks"></a>Observaciones

Llame a este método para especificar un comando predeterminado que el marco de trabajo ejecuta cuando el usuario hace clic en el botón. Un elemento con el identificador de comando especificado por *uiCmd* debe estar ubicado en la barra de herramientas desplegable principal.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar (clase)](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCToolBar (Clase)](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarMenuButton (clase)](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)
