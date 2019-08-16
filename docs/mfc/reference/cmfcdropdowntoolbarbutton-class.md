---
title: Clase CMFCDropDownToolbarButton
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
ms.openlocfilehash: fcfb521e309463da81d0064451297b3b73610d2f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505331"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>Clase CMFCDropDownToolbarButton

Un tipo de botón de la barra de herramientas que se comporta como un botón normal cuando se hace clic en él. Sin embargo, abre una barra de herramientas desplegable ( [clase CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md) si el usuario presiona y mantiene presionado el botón de barra de herramientas.

## <a name="syntax"></a>Sintaxis

```
class CMFCDropDownToolbarButton : public CMFCToolBarButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|Construye un objeto `CMFCDropDownToolbarButton`.|
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|Copia las propiedades de otro botón de la barra de herramientas en el botón actual. (Invalida [CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)).|
|`CMFCDropDownToolbarButton::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|Abre una barra de herramientas desplegable.|
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|Copia texto del botón de la barra de herramientas en un menú. (Invalida [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)).|
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|Recupera la barra de herramientas desplegable que está asociada al botón.|
|`CMFCDropDownToolbarButton::GetThisClass`|Lo usa el marco de trabajo para obtener un puntero al objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|Determina si la barra de herramientas desplegable está abierta actualmente.|
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|Determina si el botón se puede mostrar con un borde extendido. (Invalida [CMFCToolBarButton:: IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize)).|
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|Lo llama el marco de trabajo para calcular el tamaño del botón para el contexto de dispositivo y el estado de acoplamiento especificados. (Invalida [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)).|
|`CMFCDropDownToolbarButton::OnCancelMode`|Lo llama el marco de trabajo para controlar el mensaje de [WM_CANCELMODE](/windows/win32/winmsg/wm-cancelmode) . (Invalida `CMCToolBarButton::OnCancelMode`).|
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|Lo llama el marco de trabajo cuando el botón se inserta en una nueva barra de herramientas. (Invalida [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)).|
|[CMFCDropDownToolbarButton::OnClick](#onclick)|Lo llama el marco de trabajo cuando el usuario hace clic con el botón del mouse. (Invalida [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)).|
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|Lo llama el marco de trabajo cuando el usuario suelta el botón del mouse. (Invalida [CMFCToolBarButton:: OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup)).|
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|Lo llama el marco de trabajo cuando la barra de herramientas primaria controla un mensaje WM_HELPHITTEST. (Invalida [CMFCToolBarButton:: OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)).|
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|Modifica el menú proporcionado cuando la aplicación muestra un menú contextual en la barra de herramientas primaria. (Invalida [CMFCToolBarButton:: OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)).|
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|Lo llama el marco de trabajo para dibujar el botón usando los estilos y las opciones especificados. (Invalida [CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)).|
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Lo llama el marco de trabajo para dibujar el botón en el panel **comandos** del cuadro de diálogo **personalizar** . (Invalida [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)).|
|[CMFCDropDownToolbarButton::Serialize](#serialize)|Lee este objeto de un archivo o lo escribe en un archivo. (Invalida [CMFCToolBarButton:: Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)).|
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|Establece el comando predeterminado que usa el marco cuando un usuario hace clic en el botón.|

### <a name="data-members"></a>Miembros de datos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|Especifica el período de tiempo que un usuario debe mantener presionado el botón del mouse antes de que aparezca la barra de herramientas desplegable.|

## <a name="remarks"></a>Comentarios

Un `CMFCDropDownToolBarButton` difiere de un botón normal en que tiene una flecha pequeña en la esquina inferior derecha del botón. Después de que el usuario selecciona un botón de la barra de herramientas desplegable, el marco de trabajo muestra su icono en el botón de la barra de herramientas de nivel superior (el botón con la flecha pequeña en la esquina inferior derecha).

Para obtener información sobre cómo implementar una barra de herramientas desplegable, vea [CMFCDropDownToolBar (clase](../../mfc/reference/cmfcdropdowntoolbar-class.md)).

El `CMFCDropDownToolBarButton` objeto se puede exportar a un objeto de la [clase CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) y se muestra como un botón de menú con un menú emergente.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdropdowntoolbar.h

##  <a name="copyfrom"></a>  CMFCDropDownToolbarButton::CopyFrom

Copia las propiedades de otro botón de la barra de herramientas en el botón actual.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
de Referencia al botón de origen desde el que se va a copiar.

### <a name="remarks"></a>Comentarios

Llame a este método para copiar otro botón de la barra de herramientas en este botón de la barra de herramientas. *src* debe ser de tipo `CMFCDropDownToolbarButton`.

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
de Texto predeterminado del botón.

*pToolBar*<br/>
de Puntero al `CMFCDropDownToolBar` objeto que se muestra cuando el usuario presiona el botón.

### <a name="remarks"></a>Comentarios

La segunda sobrecarga del constructor copia en el botón desplegable el primer botón de la barra de herramientas que especifica *pToolBar* .

Normalmente, un botón de la barra de herramientas desplegable usa el texto del botón usados más recientemente en la barra de herramientas que *pToolBar* especifica. Usa el texto especificado por *lpszName* cuando el botón se convierte en un botón de menú o se muestra en la pestaña **comandos** del cuadro de diálogo **personalizar** . Para obtener más información sobre el cuadro de diálogo **personalizar** , consulte [clase CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto de `CMFCDropDownToolbarButton` la clase. Este fragmento de código forma parte del [ejemplo de demostración de Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]

##  <a name="dropdowntoolbar"></a>  CMFCDropDownToolbarButton::DropDownToolbar

Abre una barra de herramientas desplegable.

```
BOOL DropDownToolbar(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
de La ventana primaria del marco desplegable o NULL para usar la ventana primaria del botón de la barra de herramientas desplegable.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método es correcto; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

El método [CMFCDropDownToolbarButton:: OnClick](#onclick) llama a este método para abrir la barra de herramientas desplegable cuando el usuario presiona y mantiene presionado el botón de barra de herramientas.

Estos métodos crean la barra de herramientas desplegable mediante el método [CMFCDropDownFrame:: Create](../../mfc/reference/cmfcdropdownframe-class.md#create) . Si la barra de herramientas primaria está acoplada verticalmente, este método coloca la barra de herramientas desplegable en la parte izquierda o derecha de la barra de herramientas primaria, en función del ajuste. De lo contrario, este método coloca la barra de herramientas desplegable debajo de la barra de herramientas primaria.

Este método produce un error si *PWND* es NULL y el botón de la barra de herramientas desplegable no tiene una ventana primaria.

##  <a name="exporttomenubutton"></a>  CMFCDropDownToolbarButton::ExportToMenuButton

Copia texto del botón de la barra de herramientas en un menú.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parámetros

*menuButton*<br/>
de Referencia al botón de menú de destino.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método es correcto; de lo contrario, 0.

### <a name="remarks"></a>Comentarios

Este método llama a la implementación de la clase base ( [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) y, a continuación, anexa al botón de menú de destino un menú emergente que contiene cada elemento de menú de la barra de herramientas de este botón. Este método no anexa menús secundarios al menú emergente.

Este método produce un error si la barra `m_pToolBar`de herramientas primaria,, es null o la implementación de la clase base devuelve false.

##  <a name="getdropdowntoolbar"></a>  CMFCDropDownToolbarButton::GetDropDownToolBar

Recupera la barra de herramientas desplegable que está asociada al botón.

```
CMFCToolBar* GetDropDownToolBar() const;
```

### <a name="return-value"></a>Valor devuelto

Barra de herramientas desplegable que está asociada al botón.

### <a name="remarks"></a>Comentarios

Este método devuelve el `m_pToolBar` miembro de datos.

##  <a name="isdropdown"></a>  CMFCDropDownToolbarButton::IsDropDown

Determina si la barra de herramientas desplegable está abierta actualmente.

```
BOOL IsDropDown() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la barra de herramientas desplegable está abierta actualmente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

El marco de trabajo abre la barra de herramientas desplegable con el método [CMFCDropDownToolbarButton::D ropdowntoolbar](#dropdowntoolbar) . El marco de trabajo cierra la barra de herramientas desplegable cuando el usuario presiona el botón primario del mouse en el área no cliente de la barra de herramientas desplegable.

##  <a name="isextrasize"></a>  CMFCDropDownToolbarButton::IsExtraSize

Determina si el botón se puede mostrar con un borde extendido.

```
virtual BOOL IsExtraSize() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón de la barra de herramientas se puede mostrar con un borde extendido; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre los bordes extendidos, vea [CMFCToolBarButton:: IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).

##  <a name="m_uishowbardelay"></a>  CMFCDropDownToolbarButton::m_uiShowBarDelay

Especifica el período de tiempo que un usuario debe mantener presionado el botón del mouse antes de que aparezca la barra de herramientas desplegable.

```
static UINT m_uiShowBarDelay;
```

### <a name="remarks"></a>Comentarios

El tiempo de retardo se mide en milisegundos. El valor predeterminado es 500. Puede establecer otro retraso cambiando el valor de este miembro de datos compartido.

##  <a name="oncalculatesize"></a>  CMFCDropDownToolbarButton::OnCalculateSize

Lo llama el marco de trabajo para calcular el tamaño del botón para el contexto de dispositivo y el estado de acoplamiento especificados.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Contexto de dispositivo que muestra el botón.

*sizeDefault*<br/>
de Tamaño predeterminado del botón.

*bHorz*<br/>
de Estado de acoplamiento de la barra de herramientas primaria. Este parámetro es TRUE si la barra de herramientas está acoplada horizontalmente o es flotante, o FALSE si la barra de herramientas está acoplada verticalmente.

### <a name="return-value"></a>Valor devuelto

`SIZE` Estructura que contiene las dimensiones del botón, en píxeles.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)) agregando el ancho de la flecha desplegable a la dimensión horizontal del tamaño del botón.

##  <a name="onchangeparentwnd"></a>  CMFCDropDownToolbarButton::OnChangeParentWnd

Lo llama el marco de trabajo cuando el botón se inserta en una nueva barra de herramientas.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
de Nueva ventana primaria.

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de la clase base ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) borrando la etiqueta de texto ( [CMFCToolBarButton:: m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) y estableciendo [CMFCToolBarButton:: m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext) y [CMFCToolBarButton :: m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton) los miembros de datos a false.

##  <a name="onclick"></a>  CMFCDropDownToolbarButton::OnClick

Lo llama el marco de trabajo cuando el usuario hace clic con el botón del mouse.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
de Ventana primaria del botón de la barra de herramientas.

*bDelay*<br/>
de TRUE si el mensaje se debe controlar con un retraso.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón procesa el mensaje de clic; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base, [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), actualizando el estado de la barra de herramientas desplegable.

Cuando un usuario hace clic en el botón de la barra de herramientas, este método crea un temporizador que espera el período de tiempo especificado por el miembro de datos [CMFCDropDownToolbarButton:: m_uiShowBarDelay](#m_uishowbardelay) y, a continuación, abre la barra de herramientas desplegable mediante [CMFCDropDownToolbarButton ::D método ropDownToolbar](#dropdowntoolbar) . Este método cierra la barra de herramientas desplegable la segunda vez que el usuario hace clic en el botón de la barra de herramientas.

##  <a name="onclickup"></a>  CMFCDropDownToolbarButton::OnClickUp

Lo llama el marco de trabajo cuando el usuario suelta el botón del mouse.

```
virtual BOOL OnClickUp();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón procesa el mensaje de clic; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base, [CMFCToolBarButton:: OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup), actualizando el estado de la barra de herramientas desplegable.

Este método detiene el temporizador de la barra de herramientas desplegable si está activo. Cierra la barra de herramientas desplegable si está abierta.

Para obtener más información sobre la barra de herramientas desplegable y el temporizador de la barra de herramientas desplegable, vea [CMFCDropDownToolbarButton:: OnClick](#onclick).

##  <a name="oncontexthelp"></a>  CMFCDropDownToolbarButton::OnContextHelp

Lo llama el marco de trabajo cuando la barra de herramientas primaria controla un mensaje WM_HELPHITTEST.

```
virtual BOOL OnContextHelp(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
de Ventana primaria del botón de la barra de herramientas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón procesa el mensaje de ayuda; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton:: OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)) llamando al método [CMFCDropDownToolbarButton:: OnClick](#onclick) con *bDelay* establecido en false. Este método devuelve el valor devuelto por [CMFCDropDownToolbarButton:: OnClick](#onclick).

Para obtener más información sobre el mensaje WM_HELPHITTEST, [consulte TN028: Compatibilidad con](../../mfc/tn028-context-sensitive-help-support.md)la ayuda contextual.

##  <a name="oncustomizemenu"></a>  CMFCDropDownToolbarButton::OnCustomizeMenu

Modifica el menú proporcionado cuando la aplicación muestra un menú contextual en la barra de herramientas primaria.

```
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Parámetros

*pMenu*<br/>
de Menú que se va a personalizar.

### <a name="return-value"></a>Valor devuelto

Este método devuelve TRUE.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton:: OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)) deshabilitando los siguientes elementos de menú:

- **Copiar imagen del botón**

- **Apariencia del botón**

- **Image**

- **Texto**

- **Imagen y texto**

Invalide este método para modificar el menú contextual que el marco de trabajo muestra en modo de personalización.

##  <a name="ondraw"></a>  CMFCDropDownToolbarButton::OnDraw

Lo llama el marco de trabajo para dibujar el botón usando los estilos y las opciones especificados.

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
de Contexto de dispositivo que muestra el botón.

*rect*<br/>
de Rectángulo delimitador del botón.

*pImages*<br/>
de Colección de imágenes de la barra de herramientas que está asociada al botón.

*bHorz*<br/>
de Estado de acoplamiento de la barra de herramientas primaria. Este parámetro es TRUE cuando el botón se acopla horizontalmente y FALSE cuando el botón está acoplado verticalmente.

*bCustomizeMode*<br/>
de Especifica si la barra de herramientas está en modo de personalización. Este parámetro es TRUE cuando la barra de herramientas está en modo de personalización y FALSE cuando la barra de herramientas no está en modo de personalización.

*bHighlight*<br/>
de Especifica si el botón está resaltado. Este parámetro es TRUE cuando el botón está resaltado y FALSE cuando el botón no está resaltado.

*bDrawBorder*<br/>
de Especifica si el botón debe mostrar su borde. Este parámetro es TRUE cuando el botón debe mostrar su borde y FALSE cuando el botón no debe mostrar su borde.

*bGrayDisabledButtons*<br/>
de Especifica si se deben sombrear los botones deshabilitados o usar la colección de imágenes deshabilitadas. Este parámetro es TRUE cuando los botones deshabilitados deben estar sombreados y FALSE cuando este método debe utilizar la colección de imágenes deshabilitadas.

### <a name="remarks"></a>Comentarios

Invalide este método para personalizar el dibujo del botón de la barra de herramientas.

##  <a name="ondrawoncustomizelist"></a>  CMFCDropDownToolbarButton::OnDrawOnCustomizeList

Lo llama el marco de trabajo para dibujar el botón en el panel **comandos** del cuadro de diálogo **personalizar** .

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Contexto de dispositivo que muestra el botón.

*rect*<br/>
de Rectángulo delimitador del botón.

*bSelected*<br/>
de Indica si el botón está seleccionado. Si este parámetro es TRUE, el botón está seleccionado. Si este parámetro es FALSE, el botón no está seleccionado.

### <a name="return-value"></a>Valor devuelto

Ancho, en píxeles, del botón en el contexto de dispositivo especificado.

### <a name="remarks"></a>Comentarios

Este método se llama mediante el cuadro de diálogo Personalización (pestaña **comandos** ) cuando el botón debe mostrarse en el cuadro de lista dibujado por el propietario.

Este método extiende la implementación de la clase base ( [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)) cambiando la etiqueta de texto del botón al nombre del botón (es decir, al valor del parámetro *lpszName* que pasó al constructor. ).

##  <a name="serialize"></a>  CMFCDropDownToolbarButton::Serialize

Lee este objeto de un archivo o lo escribe en un archivo.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

*ar*<br/>
de Objeto `CArchive` del que se va a serializar o en el que se va a serializar.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton:: Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)) serializando el identificador de recurso de la barra de herramientas primaria. Cuando se carga el archivo ( [CArchive:: IsLoading](../../mfc/reference/carchive-class.md#isloading) devuelve un valor distinto de cero), este método establece `m_pToolBar` el miembro de datos en la barra de herramientas que contiene el identificador de recurso serializado.

##  <a name="setdefaultcommand"></a>  CMFCDropDownToolbarButton::SetDefaultCommand

Establece el comando predeterminado que usa el marco cuando un usuario hace clic en el botón.

```
void SetDefaultCommand(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
de IDENTIFICADOR del comando predeterminado.

### <a name="remarks"></a>Comentarios

Llame a este método para especificar un comando predeterminado que el marco de trabajo ejecuta cuando el usuario hace clic en el botón. Un elemento con el identificador de comando especificado por *uiCmd* debe estar ubicado en la barra de herramientas desplegable primaria.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar (clase)](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarMenuButton (clase)](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)
