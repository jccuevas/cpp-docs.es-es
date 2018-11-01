---
title: CMFCToolBarEditBoxButton (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CanBeStretched
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CopyFrom
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetByCmd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContentsAll
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetEditBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetHwnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetInvalidateRect
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::HaveHotBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::IsFlatMode
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::NotifyCommand
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnAddToCustomizePage
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnChangeParentWnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnClick
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnCtlColor
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnGlobalFontsChanged
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnMove
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnShow
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnSize
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnUpdateToolTip
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetFlatMode
helpviewer_keywords:
- CMFCToolBarEditBoxButton [MFC], CMFCToolBarEditBoxButton
- CMFCToolBarEditBoxButton [MFC], CanBeStretched
- CMFCToolBarEditBoxButton [MFC], CopyFrom
- CMFCToolBarEditBoxButton [MFC], GetByCmd
- CMFCToolBarEditBoxButton [MFC], GetContentsAll
- CMFCToolBarEditBoxButton [MFC], GetContextMenuID
- CMFCToolBarEditBoxButton [MFC], GetEditBorder
- CMFCToolBarEditBoxButton [MFC], GetHwnd
- CMFCToolBarEditBoxButton [MFC], GetInvalidateRect
- CMFCToolBarEditBoxButton [MFC], HaveHotBorder
- CMFCToolBarEditBoxButton [MFC], IsFlatMode
- CMFCToolBarEditBoxButton [MFC], NotifyCommand
- CMFCToolBarEditBoxButton [MFC], OnAddToCustomizePage
- CMFCToolBarEditBoxButton [MFC], OnChangeParentWnd
- CMFCToolBarEditBoxButton [MFC], OnClick
- CMFCToolBarEditBoxButton [MFC], OnCtlColor
- CMFCToolBarEditBoxButton [MFC], OnGlobalFontsChanged
- CMFCToolBarEditBoxButton [MFC], OnMove
- CMFCToolBarEditBoxButton [MFC], OnShow
- CMFCToolBarEditBoxButton [MFC], OnSize
- CMFCToolBarEditBoxButton [MFC], OnUpdateToolTip
- CMFCToolBarEditBoxButton [MFC], SetContextMenuID
- CMFCToolBarEditBoxButton [MFC], SetFlatMode
ms.assetid: b21d9b67-6bf7-4ca9-bd62-b237756e0ab3
ms.openlocfilehash: bf71bb508bf0327a7fdf34b128bdb825323cd3a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525728"
---
# <a name="cmfctoolbareditboxbutton-class"></a>CMFCToolBarEditBoxButton (clase)

Un botón de barra de herramientas que contiene un control de edición ( [clase CEdit](../../mfc/reference/cedit-class.md)).

## <a name="syntax"></a>Sintaxis

```
class CMFCToolBarEditBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](#cmfctoolbareditboxbutton)|Construye un objeto `CMFCToolBarEditBoxButton`.|
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CanBeStretched](#canbestretched)|Especifica si un usuario puede expandir el botón durante la personalización. (Invalida [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarEditBoxButton::CopyFrom](#copyfrom)|Copia las propiedades de otro botón de barra de herramientas a la actual. (Invalida [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::CreateEdit](#createedit)|Crea un nuevo control de edición en el botón.|
|`CMFCToolBarEditBoxButton::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|Recupera el primer `CMFCToolBarEditBoxButton` objeto en la aplicación que tiene el identificador de comando especificado.|
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|Recupera el texto del primer control de barra de herramientas de cuadro de edición que tiene el identificador de comando especificado.|
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|Recupera el identificador de recurso del menú contextual que está asociado con el botón.|
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|Recupera el rectángulo delimitador de la parte de edición del botón de cuadro de edición.|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::GetEditBox](#geteditbox)|Devuelve un puntero al control de edición que está incrustado en el botón.|
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|Recupera el identificador de ventana que está asociado con el botón de barra de herramientas. (Invalida [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|Recupera la región del área cliente del botón que se debe volver a dibujar. (Invalida [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect).)|
|`CMFCToolBarEditBoxButton::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|Determina si se muestra un borde del botón cuando un usuario hace clic en el botón. (Invalida [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|Determina si los botones del cuadro de edición tienen un estilo plano.|
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|Especifica si el botón procesa el [WM_COMMAND](/windows/desktop/menurc/wm-command) mensaje. (Invalida [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|Lo llama el marco cuando el botón se agrega a un **personalizar** cuadro de diálogo. (Invalida [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarEditBoxButton::OnCalculateSize`|Lo llama el marco de trabajo para calcular el tamaño del botón para el contexto de dispositivo especificado y el estado de acoplamiento. (Invalida [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|Lo llama el marco cuando el botón se inserta en una nueva barra de herramientas. (Invalida [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarEditBoxButton::OnClick](#onclick)|Lo llama el marco cuando el usuario hace clic en el botón del mouse. (Invalida [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|Lo llama el marco de trabajo cuando la barra de herramientas primario controla un WM_CTLCOLOR (mensaje). (Invalida [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarEditBoxButton::OnDraw`|Lo llama el marco de trabajo para dibujar el botón mediante el uso de las opciones y estilos especificados. (Invalida [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|Lo llama el marco de trabajo para dibujar el botón de la **comandos** panel de la **personalizar** cuadro de diálogo. (Invalida [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|Lo llama el marco de trabajo cuando ha cambiado la fuente global. (Invalida [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|Lo llama el marco de trabajo cuando se mueve la barra de herramientas primario. (Invalida [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|
|[CMFCToolBarEditBoxButton::OnShow](#onshow)|Lo llama el marco de trabajo cuando el botón se convierte en visible o invisible. (Invalida [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|[CMFCToolBarEditBoxButton::OnSize](#onsize)|Lo llama el marco de trabajo cuando la barra de herramientas del elemento primario cambia su tamaño o posición y este cambio hace que el botón Cambiar el tamaño. (Invalida [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|Lo llama el marco de trabajo cuando la barra de herramientas principal actualiza su texto de información sobre herramientas. (Invalida [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarEditBoxButton::Serialize`|Lee este objeto de un archivo o lo escribe en un archivo. (Invalida [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|`CMFCToolBarEditBoxButton::SetACCData`|Rellena proporcionado `CAccessibilityData` objeto con datos de accesibilidad en el botón de barra de herramientas. (Invalida [CMFCToolBarButton::SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).)|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContents](#setcontents)|Establece el texto del control de edición del botón.|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall)|Busca el botón de control de edición que tiene un identificador de comando especificado y establece el texto del control de edición de ese botón.|
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|Especifica el identificador de recurso del menú contextual que está asociado con el botón.|
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|Especifica la apariencia de estilo plano de los botones del cuadro de edición de la aplicación.|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetStyle](#setstyle)|Especifica el estilo del botón. (Invalida [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|

## <a name="remarks"></a>Comentarios

Para agregar un botón de cuadro de edición a una barra de herramientas, siga estos pasos:

1. Reserve un id. de recurso ficticio para el botón en el recurso primario de la barra de herramientas.

2. Construir un `CMFCToolBarEditBoxButton` objeto.

3. En el controlador de mensajes que procesa el mensaje AFX_WM_RESETTOOLBAR, reemplazar el botón ficticio con el nuevo botón de cuadro combinado mediante [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Para obtener más información, consulte [Tutorial: poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md).

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCToolBarEditBoxButton` . En el ejemplo se muestra cómo especificar que un usuario puede expandir el botón durante la personalización, especificar que se muestra un borde del botón cuando un usuario hace clic en el botón, establecer el texto en el control de cuadro de texto, especificar la apariencia de estilo plano de los botones del cuadro de edición en el receptor la aplicación y especifique el estilo de una barra de herramientas de control de cuadro de edición.

[!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

`CMFCToolBarEditBoxButton`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtoolbareditboxbutton.h

##  <a name="canbestretched"></a>  CMFCToolBarEditBoxButton::CanBeStretched

Especifica si un usuario puede expandir el botón durante la personalización.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Valor devuelto

Este método devuelve TRUE.

### <a name="remarks"></a>Comentarios

De forma predeterminada, el marco de trabajo no permite al usuario ajustar un botón de barra de herramientas durante la personalización. Este método extiende la implementación de la clase base ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)), ya que permite al usuario ajustar un botón de barra de herramientas del cuadro de edición durante la personalización.

##  <a name="cmfctoolbareditboxbutton"></a>  CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton

Construye un [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) objeto.

```
CMFCToolBarEditBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=ES_AUTOHSCROLL,
    int iWidth=0);
```

### <a name="parameters"></a>Parámetros

*uiID*<br/>
[in] Especifica el identificador de control.

*iImage*<br/>
[in] Especifica el índice de base cero de una imagen de la barra de herramientas. La imagen se encuentra en la [CMFCToolBarImages (clase)](../../mfc/reference/cmfctoolbarimages-class.md) objeto que [CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md) clase mantiene.

*dwStyle*<br/>
[in] Especifica el estilo del control de edición.

*iWidth*<br/>
[in] Especifica el ancho en píxeles del control de edición.

### <a name="remarks"></a>Comentarios

El constructor predeterminado establece el estilo del control de edición a la combinación siguiente:

WS_CHILD | WS_VISIBLE | ES_AUTOHSCROLL

El ancho predeterminado del control es 150 píxeles.

##  <a name="copyfrom"></a>  CMFCToolBarEditBoxButton::CopyFrom

Copia las propiedades de otro botón de barra de herramientas a la actual.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
[in] Una referencia al botón de origen desde el que se va a copiar.

### <a name="remarks"></a>Comentarios

Llame a este método para copiar otro botón de barra de herramientas en este botón de barra de herramientas. *src* debe ser de tipo `CMFCToolBarEditBoxButton`.

##  <a name="createedit"></a>  CMFCToolBarEditBoxButton::CreateEdit

Crea un nuevo control de edición en el botón.

```
virtual CEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[in] Especifica la ventana primaria del control de edición. No debe ser NULL.

*Rect*<br/>
[in] Especifica el tamaño y la posición del control de edición.

### <a name="return-value"></a>Valor devuelto

Un puntero para el control de edición recién creada; es NULL si no superan la creación y la inclusión del control.

### <a name="remarks"></a>Comentarios

Construir un `CMFCToolBarEditBoxButton` objeto en dos pasos. Llamar primero al constructor y, a continuación, llame a `CreateEdit`, que crea el control de edición de Windows y lo adjunta a la `CMFCToolBarEditBoxButton` objeto.

##  <a name="getbycmd"></a>  CMFCToolBarEditBoxButton::GetByCmd

Recupera el primer `CMFCToolBarEditBoxButton` objeto en la aplicación que tiene el identificador de comando especificado.

```
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[in] El identificador de comando del botón debe recuperar.

### <a name="return-value"></a>Valor devuelto

La primera `CMFCToolBarEditBoxButton` objeto en la aplicación que tiene el identificador de comando especificado o NULL si no existe el objeto existe.

### <a name="remarks"></a>Comentarios

Este método de utilidad compartida se usa como métodos [CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall) y [CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall) para establecer u obtener el texto de la primera barra de herramientas del cuadro de edición control que tiene el identificador de comando especificado.

##  <a name="getcontentsall"></a>  CMFCToolBarEditBoxButton::GetContentsAll

Recupera el texto del primer control de barra de herramientas de cuadro de edición que tiene el identificador de comando especificado.

```
static CString __stdcall GetContentsAll(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[in] El identificador de comando del botón desde la que se va a recuperar contenido.

### <a name="return-value"></a>Valor devuelto

Un `CString` objeto que contiene el texto del primer control de barra de herramientas de cuadro de edición que tiene el identificador de comando especificado.

### <a name="remarks"></a>Comentarios

Este método devuelve una cadena vacía si no hay ningún `CMFCToolBarEditBoxButton` objetos tienen el identificador de comando especificado.

##  <a name="getcontextmenuid"></a>  CMFCToolBarEditBoxButton::GetContextMenuID

Recupera el identificador de recurso del menú contextual que está asociado con el botón.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Valor devuelto

El identificador de recurso del menú contextual que está asociado con el botón o 0 si el botón no tiene ningún menú contextual asociado.

### <a name="remarks"></a>Comentarios

El marco de trabajo usa el identificador de recurso para crear el menú contextual cuando el usuario del botón secundario en el botón.

##  <a name="geteditborder"></a>  CMFCToolBarEditBoxButton::GetEditBorder

Recupera el rectángulo delimitador de la parte de edición del botón de cuadro de edición.

```
virtual void GetEditBorder(CRect& rectBorder);
```

### <a name="parameters"></a>Parámetros

*rectBorder*<br/>
[out] Una referencia a la `CRect` objeto que recibe el rectángulo delimitador.

### <a name="remarks"></a>Comentarios

Este método recupera el rectángulo delimitador del control de edición en coordenadas de cliente. Expande el tamaño del rectángulo en cada dirección de un píxel.

El [CMFCVisualManager::OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder) método llama a este método cuando dibuja el borde alrededor de un `CMFCToolBarEditBoxButton` objeto.

##  <a name="geteditbox"></a>  CMFCToolBarEditBoxButton::GetEditBox

Devuelve un puntero a la [clase CEdit](../../mfc/reference/cedit-class.md) control que está incrustado en el botón.

```
CEdit* GetEditBox() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la [clase CEdit](../../mfc/reference/cedit-class.md) control que contiene el botón. Es NULL si el `CEdit` control aún no se ha creado.

### <a name="remarks"></a>Comentarios

Crear el `CEdit` control mediante una llamada a [CMFCToolBarEditBoxButton::CreateEdit](#createedit).

##  <a name="gethwnd"></a>  CMFCToolBarEditBoxButton::GetHwnd

Recupera el identificador de ventana que está asociado con el botón de barra de herramientas.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Valor devuelto

El identificador de ventana que está asociado con el botón.

### <a name="remarks"></a>Comentarios

Este método invalida el [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) método devolviendo el identificador de ventana de la parte del control de edición del botón de cuadro de edición.

##  <a name="getinvalidaterect"></a>  CMFCToolBarEditBoxButton::GetInvalidateRect

Recupera la región del área cliente del botón que se debe volver a dibujar.

```
virtual const CRect GetInvalidateRect() const;
```

### <a name="return-value"></a>Valor devuelto

Un `CRect` objeto que especifica la región que se debe volver a dibujar.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base, [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect), mediante la inclusión en la región del área de la etiqueta de texto.

##  <a name="havehotborder"></a>  CMFCToolBarEditBoxButton::HaveHotBorder

Determina si se muestra un borde del botón cuando un usuario hace clic en el botón.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si un botón muestra su borde cuando se selecciona; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base, [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder), devolviendo un valor distinto de cero si el control está visible.

##  <a name="isflatmode"></a>  CMFCToolBarEditBoxButton::IsFlatMode

Determina si los botones del cuadro de edición tienen un estilo plano.

```
static BOOL __stdcall IsFlatMode();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los botones tienen un estilo plano; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

De forma predeterminada, los botones del cuadro de edición tienen un estilo plano. Use la [CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode) método para cambiar la apariencia de estilo plano de la aplicación.

##  <a name="notifycommand"></a>  CMFCToolBarEditBoxButton::NotifyCommand

Especifica si el botón procesa el [WM_COMMAND](/windows/desktop/menurc/wm-command) mensaje.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parámetros

*iNotifyCode*<br/>
[in] El mensaje de notificación que está asociado con el comando.

### <a name="return-value"></a>Valor devuelto

TRUE si el botón que procesa el mensaje WM_COMMAND, o FALSE para indicar que el mensaje debe controlarse mediante la barra de herramientas primario.

### <a name="remarks"></a>Comentarios

El marco llama a este método cuando está a punto de enviar un [WM_COMMAND](/windows/desktop/menurc/wm-command) mensaje a la ventana primaria.

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) mediante el procesamiento de la [EN_UPDATE](/windows/desktop/Controls/en-update) notificación. Para cada cuadro de edición con el mismo identificador de comando que este objeto, Establece la etiqueta de texto a la etiqueta de texto de este objeto.

##  <a name="onaddtocustomizepage"></a>  CMFCToolBarEditBoxButton::OnAddToCustomizePage

Lo llama el marco cuando el botón se agrega a un **personalizar** cuadro de diálogo.

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)) mediante la copia de las propiedades desde el control de cuadro de edición en cualquier barra de herramientas que tiene el mismo identificador de comando que este objeto. Este método no hace nada si no hay barra de herramientas tiene un control de cuadro de edición que tiene el mismo identificador de comando que este objeto.

Para obtener más información sobre la **personalizar** cuadro de diálogo, vea [CMFCToolBarsCustomizeDialog (clase)](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

##  <a name="onchangeparentwnd"></a>  CMFCToolBarEditBoxButton::OnChangeParentWnd

Lo llama el marco cuando el botón se inserta en una nueva barra de herramientas.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[in] Un puntero a la nueva ventana primaria.

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de la clase base ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) volviendo a interno `CEdit` objeto.

##  <a name="onclick"></a>  CMFCToolBarEditBoxButton::OnClick

Lo llama el marco cuando el usuario hace clic en el botón del mouse.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parámetros

*conquistado*<br/>
[in] Sin usar.

*bDelay*<br/>
[in] Sin usar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón procesa el mensaje clic; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de la clase base ( [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)) que devuelva un valor distinto de cero si interno `CEdit` objeto es visible.

##  <a name="onctlcolor"></a>  CMFCToolBarEditBoxButton::OnCtlColor

Lo llama el marco de trabajo cuando la barra de herramientas primario controla un WM_CTLCOLOR (mensaje).

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] El contexto de dispositivo que muestra el botón.

*nCtlColor*<br/>
[in] Sin usar.

### <a name="return-value"></a>Valor devuelto

Identificador del pincel de ventana global.

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de la clase base ( [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)) estableciendo el color de texto y fondo del contexto de dispositivo proporcionado al texto global y los colores de fondo, respectivamente.

Para obtener más información acerca de las opciones globales que están disponibles para su aplicación, consulte [AFX_GLOBAL_DATA (estructura)](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onglobalfontschanged"></a>  CMFCToolBarEditBoxButton::OnGlobalFontsChanged

Lo llama el marco de trabajo cuando ha cambiado la fuente global.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) cambiando la fuente del control a la de la fuente global.

Para obtener más información acerca de las opciones globales que están disponibles para su aplicación, consulte [AFX_GLOBAL_DATA (estructura)](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onmove"></a>  CMFCToolBarEditBoxButton::OnMove

Lo llama el marco de trabajo cuando se mueve la barra de herramientas primario.

```
virtual void OnMove();
```

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de la clase predeterminada ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) mediante la actualización de la posición de interno `CEdit` objeto

##  <a name="onshow"></a>  CMFCToolBarEditBoxButton::OnShow

Lo llama el marco de trabajo cuando el botón se convierte en visible o invisible.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bMostrar*<br/>
[in] Especifica si el botón está visible. Si este parámetro es TRUE, el botón está visible. En caso contrario, el botón no está visible.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) al mostrar el botón si *bMostrar* es TRUE. En caso contrario, este método oculta el botón.

##  <a name="onsize"></a>  CMFCToolBarEditBoxButton::OnSize

Lo llama el marco de trabajo cuando la barra de herramientas del elemento primario cambia su tamaño o posición y este cambio hace que el botón Cambiar el tamaño.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parámetros

*iSize*<br/>
[in] Nuevo ancho del botón, en píxeles.

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de la clase de forma predeterminada, [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize), actualizando el tamaño y posición de interno `CEdit` objeto.

##  <a name="onupdatetooltip"></a>  CMFCToolBarEditBoxButton::OnUpdateToolTip

Lo llama el marco de trabajo cuando la barra de herramientas principal actualiza su texto de información sobre herramientas.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[in] Sin usar.

*iButtonIndex*<br/>
[in] Sin usar.

*wndToolTip*<br/>
[in] El control que muestra el texto de información sobre herramientas.

*str*<br/>
[out] Un `CString` objeto que recibe el texto de información actualizada.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método actualiza el texto de información sobre herramientas; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) mostrando el texto de información sobre herramientas que está asociado a la parte de edición del botón. Si el texto interno `CEdit` objeto es NULL o el identificador de ventana de la `CEdit` objeto no identifica una ventana existente, este método no hace nada y devuelve FALSE.

##  <a name="setcontents"></a>  CMFCToolBarEditBoxButton::SetContents

Establece el texto en el control de cuadro de texto.

```
virtual void SetContents(const CString& sContents);
```

### <a name="parameters"></a>Parámetros

*sContents*<br/>
[in] Especifica el nuevo texto para establecer.

##  <a name="setcontentsall"></a>  CMFCToolBarEditBoxButton::SetContentsAll

Busca un [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) objeto que tiene un identificador de comando especificado y establece el texto especificado dentro de su cuadro de texto.

```
static BOOL SetContentsAll(
    UINT uiCmd,
    const CString& strContents);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[in] Especifica el identificador del control para el que se cambiará el texto de comando.

*strContents*<br/>
[in] Especifica el nuevo texto para establecer.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha establecido el texto; 0 si el `CMFCToolBarEditBoxButton` control con el identificador de comando especificado no existe.

##  <a name="setcontextmenuid"></a>  CMFCToolBarEditBoxButton::SetContextMenuID

Especifica el identificador de recurso del menú contextual que está asociado con el botón.

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[in] El identificador de recurso del menú contextual.

### <a name="remarks"></a>Comentarios

El marco de trabajo usa el identificador de recurso para crear el menú contextual cuando el usuario seleccione el botón de barra de herramientas.

##  <a name="setflatmode"></a>  CMFCToolBarEditBoxButton::SetFlatMode

Especifica la apariencia de estilo plano de los botones del cuadro de edición de la aplicación.

```
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```

### <a name="parameters"></a>Parámetros

*bFlat*<br/>
[in] El estilo plano de los botones del cuadro de edición. Si este parámetro es TRUE, la apariencia de estilo plano está habilitada; en caso contrario, se deshabilita la apariencia de estilo plano.

### <a name="remarks"></a>Comentarios

El estilo plano de forma predeterminada para los botones de cuadro de edición es TRUE. Use la [CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode) método para recuperar la apariencia de estilo plano de la aplicación.

##  <a name="setstyle"></a>  CMFCToolBarEditBoxButton::SetStyle

Especifica el estilo de una barra de herramientas de control de cuadro de edición.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Parámetros

*nStyle*<br/>
[in] Para establecer un nuevo estilo.

### <a name="remarks"></a>Comentarios

Este método establece [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle) a *nStyle* también deshabilita el cuadro de texto cuando la aplicación está en modo de personalización y habilita cuando la aplicación no está en modo de personalización (consulte [ CMFCToolBar::SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode) y [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)). Consulte [estilos de Control de barra de herramientas](../../mfc/reference/toolbar-control-styles.md) para obtener una lista de marcas de estilo válido.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton (clase)](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CEdit (clase)](../../mfc/reference/cedit-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)

