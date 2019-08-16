---
title: Clase CMFCToolBarEditBoxButton
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
ms.openlocfilehash: 3e988d789ca6a038ce41bca829850f6509fd9df1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504728"
---
# <a name="cmfctoolbareditboxbutton-class"></a>Clase CMFCToolBarEditBoxButton

Un botón de la barra de herramientas que contiene un control de edición ( [clase CEDIT](../../mfc/reference/cedit-class.md)).

## <a name="syntax"></a>Sintaxis

```
class CMFCToolBarEditBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](#cmfctoolbareditboxbutton)|Construye un objeto `CMFCToolBarEditBoxButton`.|
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CanBeStretched](#canbestretched)|Especifica si un usuario puede ajustar el botón durante la personalización. (Invalida [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)).|
|[CMFCToolBarEditBoxButton::CopyFrom](#copyfrom)|Copia las propiedades de otro botón de la barra de herramientas en el botón actual. (Invalida [CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)).|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::CreateEdit](#createedit)|Crea un nuevo control de edición en el botón.|
|`CMFCToolBarEditBoxButton::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|Recupera el primer `CMFCToolBarEditBoxButton` objeto de la aplicación que tiene el identificador de comando especificado.|
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|Recupera el texto del primer control de barra de herramientas del cuadro de edición que tiene el identificador de comando especificado.|
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|Recupera el identificador de recurso del menú contextual asociado al botón.|
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|Recupera el rectángulo delimitador de la parte de edición del botón de cuadro de edición.|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::GetEditBox](#geteditbox)|Devuelve un puntero al control de edición que está incrustado en el botón.|
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|Recupera el identificador de ventana asociado al botón de la barra de herramientas. (Invalida [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)).|
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|Recupera la región del área cliente del botón que se debe volver a dibujar. (Invalida [CMFCToolBarButton:: GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect)).|
|`CMFCToolBarEditBoxButton::GetThisClass`|Lo usa el marco de trabajo para obtener un puntero al objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|Determina si se muestra un borde del botón cuando un usuario hace clic en el botón. (Invalida [CMFCToolBarButton:: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)).|
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|Determina si los botones del cuadro de edición tienen un estilo plano.|
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|Especifica si el botón procesa el mensaje [WM_COMMAND](/windows/win32/menurc/wm-command) . (Invalida [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)).|
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|Lo llama el marco de trabajo cuando el botón se agrega a un cuadro de diálogo de personalización. (Invalida [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)).|
|`CMFCToolBarEditBoxButton::OnCalculateSize`|Lo llama el marco de trabajo para calcular el tamaño del botón para el contexto de dispositivo y el estado de acoplamiento especificados. (Invalida [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)).|
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|Lo llama el marco de trabajo cuando el botón se inserta en una nueva barra de herramientas. (Invalida [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)).|
|[CMFCToolBarEditBoxButton::OnClick](#onclick)|Lo llama el marco de trabajo cuando el usuario hace clic con el botón del mouse. (Invalida [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)).|
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|Lo llama el marco de trabajo cuando la barra de herramientas primaria controla un mensaje WM_CTLCOLOR. (Invalida [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)).|
|`CMFCToolBarEditBoxButton::OnDraw`|Lo llama el marco de trabajo para dibujar el botón usando los estilos y las opciones especificados. (Invalida [CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)).|
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|Lo llama el marco de trabajo para dibujar el botón en el panel **comandos** del cuadro de diálogo **personalizar** . (Invalida [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)).|
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|Lo llama el marco de trabajo cuando ha cambiado la fuente global. (Invalida [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)).|
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|Lo llama el marco de trabajo cuando se mueve la barra de herramientas primaria. (Invalida [CMFCToolBarButton:: Move](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)).|
|[CMFCToolBarEditBoxButton::OnShow](#onshow)|Lo llama el marco de trabajo cuando el botón se vuelve visible o invisible. (Invalida [CMFCToolBarButton:: show](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)).|
|[CMFCToolBarEditBoxButton::OnSize](#onsize)|Lo llama el marco de trabajo cuando cambia el tamaño o la posición de la barra de herramientas primaria y este cambio hace que el botón cambie de tamaño. (Invalida [CMFCToolBarButton:: datasize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)).|
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|Lo llama el marco de trabajo cuando la barra de herramientas primaria actualiza el texto de información sobre herramientas. (Invalida [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)).|
|`CMFCToolBarEditBoxButton::Serialize`|Lee este objeto de un archivo o lo escribe en un archivo. (Invalida [CMFCToolBarButton:: Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)).|
|`CMFCToolBarEditBoxButton::SetACCData`|Rellena el objeto proporcionado `CAccessibilityData` con los datos de accesibilidad del botón de la barra de herramientas. (Invalida [CMFCToolBarButton:: SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata)).|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContents](#setcontents)|Establece el texto en el control de edición del botón.|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall)|Busca el botón de control de edición que tiene un identificador de comando especificado y establece el texto en el control de edición de ese botón.|
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|Especifica el identificador de recurso del menú contextual asociado al botón.|
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|Especifica la apariencia de estilo plano de los botones del cuadro de edición de la aplicación.|
|`CMFCToolBarEditBoxButton::` [CMFCToolBarEditBoxButton::SetStyle](#setstyle)|Especifica el estilo del botón. (Invalida [CMFCToolBarButton:: setStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)).|

## <a name="remarks"></a>Comentarios

Para agregar un botón de cuadro de edición a una barra de herramientas, siga estos pasos:

1. Reserve un id. de recurso ficticio para el botón en el recurso primario de la barra de herramientas.

2. Construya un `CMFCToolBarEditBoxButton` objeto.

3. En el controlador de mensajes que procesa el mensaje AFX_WM_RESETTOOLBAR, reemplace el botón ficticio por el botón nuevo cuadro combinado con [CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Para obtener más información, vea [Tutorial: Colocar controles en las barras](../../mfc/walkthrough-putting-controls-on-toolbars.md)de herramientas.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCToolBarEditBoxButton` . En el ejemplo se muestra cómo especificar que un usuario puede ajustar el botón durante la personalización, especificar que se muestre un borde del botón cuando un usuario haga clic en el botón, establecer el texto en el control de cuadro de texto, especificar la apariencia de estilo plano de los botones del cuadro de edición en la cation y especifican el estilo de un control de cuadro de edición de la barra de herramientas.

[!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

`CMFCToolBarEditBoxButton`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtoolbareditboxbutton. h

##  <a name="canbestretched"></a>  CMFCToolBarEditBoxButton::CanBeStretched

Especifica si un usuario puede ajustar el botón durante la personalización.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Valor devuelto

Este método devuelve TRUE.

### <a name="remarks"></a>Comentarios

De forma predeterminada, el marco de trabajo no permite al usuario ajustar un botón de la barra de herramientas durante la personalización. Este método extiende la implementación de la clase base ( [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) permitiendo al usuario ajustar un botón de la barra de herramientas del cuadro de edición durante la personalización.

##  <a name="cmfctoolbareditboxbutton"></a>  CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton

Construye un objeto [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) .

```
CMFCToolBarEditBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=ES_AUTOHSCROLL,
    int iWidth=0);
```

### <a name="parameters"></a>Parámetros

*uiID*<br/>
de Especifica el identificador del control.

*iImage*<br/>
de Especifica el índice de base cero de una imagen de la barra de herramientas. La imagen se encuentra en el objeto de la [clase CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) que mantiene la clase [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) .

*dwStyle*<br/>
de Especifica el estilo del control de edición.

*iWidth*<br/>
de Especifica el ancho en píxeles del control de edición.

### <a name="remarks"></a>Comentarios

El constructor predeterminado establece el estilo de control de edición en la combinación siguiente:

WS_CHILD | WS_VISIBLE | ES_AUTOHSCROLL

El ancho predeterminado del control es de 150 píxeles.

##  <a name="copyfrom"></a>CMFCToolBarEditBoxButton:: CopyFrom

Copia las propiedades de otro botón de la barra de herramientas en el botón actual.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
de Referencia al botón de origen desde el que se va a copiar.

### <a name="remarks"></a>Comentarios

Llame a este método para copiar otro botón de la barra de herramientas en este botón de la barra de herramientas. *src* debe ser de tipo `CMFCToolBarEditBoxButton`.

##  <a name="createedit"></a>  CMFCToolBarEditBoxButton::CreateEdit

Crea un nuevo control de edición en el botón.

```
virtual CEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
de Especifica la ventana primaria del control de edición. No debe ser NULL.

*rect*<br/>
de Especifica el tamaño y la posición del control de edición.

### <a name="return-value"></a>Valor devuelto

Puntero al control de edición que se acaba de crear; es NULL si se produce un error en la creación y el archivo adjunto del control.

### <a name="remarks"></a>Comentarios

Un `CMFCToolBarEditBoxButton` objeto se crea en dos pasos. En primer lugar, llame al constructor y `CreateEdit`, a continuación, llame `CMFCToolBarEditBoxButton` a, que crea el control de edición de Windows y lo adjunta al objeto.

##  <a name="getbycmd"></a>  CMFCToolBarEditBoxButton::GetByCmd

Recupera el primer `CMFCToolBarEditBoxButton` objeto de la aplicación que tiene el identificador de comando especificado.

```
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
de IDENTIFICADOR de comando del botón que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

El primer `CMFCToolBarEditBoxButton` objeto de la aplicación que tiene el identificador de comando especificado, o null si no existe dicho objeto.

### <a name="remarks"></a>Comentarios

Este método de utilidad compartida se usa en métodos como [CMFCToolBarEditBoxButton:: SetContentsAll](#setcontentsall) y [CMFCToolBarEditBoxButton:: GetContentsAll](#getcontentsall) para establecer u obtener el texto del primer control de barra de herramientas del cuadro de edición que tiene el identificador de comando especificado.

##  <a name="getcontentsall"></a>  CMFCToolBarEditBoxButton::GetContentsAll

Recupera el texto del primer control de barra de herramientas del cuadro de edición que tiene el identificador de comando especificado.

```
static CString __stdcall GetContentsAll(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
de IDENTIFICADOR de comando del botón del que se va a recuperar el contenido.

### <a name="return-value"></a>Valor devuelto

`CString` Objeto que contiene el texto del primer control de barra de herramientas del cuadro de edición que tiene el identificador de comando especificado.

### <a name="remarks"></a>Comentarios

Este método devuelve una cadena vacía si ningún `CMFCToolBarEditBoxButton` objeto tiene el identificador de comando especificado.

##  <a name="getcontextmenuid"></a>  CMFCToolBarEditBoxButton::GetContextMenuID

Recupera el identificador de recurso del menú contextual asociado al botón.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Valor devuelto

IDENTIFICADOR de recurso del menú contextual asociado al botón o 0 si el botón no tiene ningún menú contextual asociado.

### <a name="remarks"></a>Comentarios

El marco de trabajo usa el identificador de recurso para crear el menú contextual cuando el usuario hace clic con el botón secundario en el botón.

##  <a name="geteditborder"></a>  CMFCToolBarEditBoxButton::GetEditBorder

Recupera el rectángulo delimitador de la parte de edición del botón de cuadro de edición.

```
virtual void GetEditBorder(CRect& rectBorder);
```

### <a name="parameters"></a>Parámetros

*rectBorder*<br/>
enuncia Referencia al `CRect` objeto que recibe el rectángulo delimitador.

### <a name="remarks"></a>Comentarios

Este método recupera el rectángulo delimitador del control de edición en coordenadas de cliente. Expande el tamaño del rectángulo en cada dirección en un píxel.

El método [CMFCVisualManager:: OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder) llama a este método cuando dibuja el borde alrededor de `CMFCToolBarEditBoxButton` un objeto.

##  <a name="geteditbox"></a>  CMFCToolBarEditBoxButton::GetEditBox

Devuelve un puntero al control de [clase CEDIT](../../mfc/reference/cedit-class.md) que está incrustado en el botón.

```
CEdit* GetEditBox() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al control de la [clase CEDIT](../../mfc/reference/cedit-class.md) que contiene el botón. Es NULL si aún no `CEdit` se ha creado el control.

### <a name="remarks"></a>Comentarios

El `CEdit` control se crea llamando a [CMFCToolBarEditBoxButton:: CreateEdit](#createedit).

##  <a name="gethwnd"></a>  CMFCToolBarEditBoxButton::GetHwnd

Recupera el identificador de ventana asociado al botón de la barra de herramientas.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Valor devuelto

Identificador de ventana asociado al botón.

### <a name="remarks"></a>Comentarios

Este método invalida el método [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) devolviendo el identificador de ventana de la parte de control de edición del botón de cuadro de edición.

##  <a name="getinvalidaterect"></a>  CMFCToolBarEditBoxButton::GetInvalidateRect

Recupera la región del área cliente del botón que se debe volver a dibujar.

```
virtual const CRect GetInvalidateRect() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto `CRect` que especifica la región que se debe volver A dibujar.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base, [CMFCToolBarButton:: GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect), incluyendo en la región el área de la etiqueta de texto.

##  <a name="havehotborder"></a>  CMFCToolBarEditBoxButton::HaveHotBorder

Determina si se muestra un borde del botón cuando un usuario hace clic en el botón.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si un botón muestra su borde cuando está seleccionado; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base, [CMFCToolBarButton:: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder), devolviendo un valor distinto de cero si el control está visible.

##  <a name="isflatmode"></a>  CMFCToolBarEditBoxButton::IsFlatMode

Determina si los botones del cuadro de edición tienen un estilo plano.

```
static BOOL __stdcall IsFlatMode();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los botones tienen un estilo plano; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

De forma predeterminada, los botones del cuadro de edición tienen un estilo plano. Use el método [CMFCToolBarEditBoxButton:: SetFlatMode](#setflatmode) para cambiar la apariencia de estilo plano de la aplicación.

##  <a name="notifycommand"></a>  CMFCToolBarEditBoxButton::NotifyCommand

Especifica si el botón procesa el mensaje [WM_COMMAND](/windows/win32/menurc/wm-command) .

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parámetros

*iNotifyCode*<br/>
de Mensaje de notificación asociado al comando.

### <a name="return-value"></a>Valor devuelto

TRUE si el botón procesa el mensaje WM_COMMAND, o FALSE para indicar que el mensaje debe controlarse mediante la barra de herramientas primaria.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método cuando está a punto de enviar un mensaje [WM_COMMAND](/windows/win32/menurc/wm-command) a la ventana primaria.

Este método extiende la implementación de la clase base ( [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) procesando la notificación [EN_UPDATE](/windows/win32/Controls/en-update) . Para cada cuadro de edición con el mismo identificador de comando que este objeto, establece su etiqueta de texto en la etiqueta de texto de este objeto.

##  <a name="onaddtocustomizepage"></a>  CMFCToolBarEditBoxButton::OnAddToCustomizePage

Lo llama el marco de trabajo cuando el botón se agrega a un cuadro de diálogo de personalización.

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)) mediante la copia de las propiedades del control del cuadro de edición en cualquier barra de herramientas que tenga el mismo identificador de comando que este objeto. Este método no hace nada si ninguna barra de herramientas tiene un control de cuadro de edición que tiene el mismo identificador de comando que este objeto.

Para obtener más información sobre el cuadro de diálogo **personalizar** , consulte [clase CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

##  <a name="onchangeparentwnd"></a>  CMFCToolBarEditBoxButton::OnChangeParentWnd

Lo llama el marco de trabajo cuando el botón se inserta en una nueva barra de herramientas.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
de Puntero a la nueva ventana primaria.

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de la clase base ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) al volver a crear el `CEdit` objeto interno.

##  <a name="onclick"></a>  CMFCToolBarEditBoxButton::OnClick

Lo llama el marco de trabajo cuando el usuario hace clic con el botón del mouse.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
de Sin usar.

*bDelay*<br/>
de Sin usar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón procesa el mensaje de clic; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de la clase base ( [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)) devolviendo un valor distinto de cero si el `CEdit` objeto interno es visible.

##  <a name="onctlcolor"></a>  CMFCToolBarEditBoxButton::OnCtlColor

Lo llama el marco de trabajo cuando la barra de herramientas primaria controla un mensaje WM_CTLCOLOR.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Contexto de dispositivo que muestra el botón.

*nCtlColor*<br/>
de Sin usar.

### <a name="return-value"></a>Valor devuelto

Identificador del pincel de ventana global.

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de la clase base ( [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)) mediante el establecimiento de los colores de texto y de fondo del contexto de dispositivo proporcionado en los colores de fondo y de texto globales, respectivamente.

Para obtener más información sobre las opciones globales que están disponibles para la aplicación, consulte [estructura AFX_GLOBAL_DATA](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onglobalfontschanged"></a>  CMFCToolBarEditBoxButton::OnGlobalFontsChanged

Lo llama el marco de trabajo cuando ha cambiado la fuente global.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) cambiando la fuente del control por la fuente global.

Para obtener más información sobre las opciones globales que están disponibles para la aplicación, consulte [estructura AFX_GLOBAL_DATA](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onmove"></a>  CMFCToolBarEditBoxButton::OnMove

Lo llama el marco de trabajo cuando se mueve la barra de herramientas primaria.

```
virtual void OnMove();
```

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de clase predeterminada ( [CMFCToolBarButton:: Move](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) actualizando la posición del objeto interno `CEdit` .

##  <a name="onshow"></a>CMFCToolBarEditBoxButton:: show

Lo llama el marco de trabajo cuando el botón se vuelve visible o invisible.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bShow*<br/>
de Especifica si el botón está visible. Si este parámetro es TRUE, el botón está visible. De lo contrario, el botón no está visible.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton:: show](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) mostrando el botón si *bShow* es true. De lo contrario, este método oculta el botón.

##  <a name="onsize"></a>  CMFCToolBarEditBoxButton::OnSize

Lo llama el marco de trabajo cuando cambia el tamaño o la posición de la barra de herramientas primaria y este cambio hace que el botón cambie de tamaño.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parámetros

*iSize*<br/>
de Nuevo ancho del botón, en píxeles.

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de clase predeterminada, [CMFCToolBarButton:: datasize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize), actualizando el tamaño y la posición del objeto interno `CEdit` .

##  <a name="onupdatetooltip"></a>  CMFCToolBarEditBoxButton::OnUpdateToolTip

Lo llama el marco de trabajo cuando la barra de herramientas primaria actualiza el texto de información sobre herramientas.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
de Sin usar.

*iButtonIndex*<br/>
de Sin usar.

*wndToolTip*<br/>
de Control que muestra el texto de la información sobre herramientas.

*str*<br/>
enuncia `CString` Objeto que recibe el texto de información sobre herramientas actualizado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método actualiza el texto de información sobre herramientas; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) mostrando el texto de información sobre herramientas que está asociado a la parte de edición del botón. Si el objeto `CEdit` interno es null o el identificador `CEdit` de ventana del objeto no identifica una ventana existente, este método no hace nada y devuelve false.

##  <a name="setcontents"></a>  CMFCToolBarEditBoxButton::SetContents

Establece el texto del control de cuadro de texto.

```
virtual void SetContents(const CString& sContents);
```

### <a name="parameters"></a>Parámetros

*sContents*<br/>
de Especifica el nuevo texto que se va a establecer.

##  <a name="setcontentsall"></a>  CMFCToolBarEditBoxButton::SetContentsAll

Busca un objeto [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) que tiene un identificador de comando especificado y establece el texto especificado en el cuadro de texto.

```
static BOOL SetContentsAll(
    UINT uiCmd,
    const CString& strContents);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
de Especifica el identificador de comando del control para el que se cambiará el texto.

*strContents*<br/>
de Especifica el nuevo texto que se va a establecer.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se estableció el texto; 0 si el `CMFCToolBarEditBoxButton` control con el identificador de comando especificado no existe.

##  <a name="setcontextmenuid"></a>  CMFCToolBarEditBoxButton::SetContextMenuID

Especifica el identificador de recurso del menú contextual asociado al botón.

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
de IDENTIFICADOR de recurso del menú contextual.

### <a name="remarks"></a>Comentarios

El marco de trabajo usa el identificador de recurso para crear el menú contextual cuando el usuario hace clic con el botón secundario en el botón de la barra de herramientas.

##  <a name="setflatmode"></a>  CMFCToolBarEditBoxButton::SetFlatMode

Especifica la apariencia de estilo plano de los botones del cuadro de edición de la aplicación.

```
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```

### <a name="parameters"></a>Parámetros

*bFlat*<br/>
de Estilo plano de los botones del cuadro de edición. Si este parámetro es TRUE, la apariencia de estilo plano está habilitada; de lo contrario, la apariencia de estilo plano está deshabilitada.

### <a name="remarks"></a>Comentarios

El estilo plano predeterminado de los botones del cuadro de edición es TRUE. Use el método [CMFCToolBarEditBoxButton:: IsFlatMode](#isflatmode) para recuperar la apariencia de estilo plano de la aplicación.

##  <a name="setstyle"></a>  CMFCToolBarEditBoxButton::SetStyle

Especifica el estilo de un control de cuadro de edición de la barra de herramientas.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Parámetros

*nStyle*<br/>
de Nuevo estilo que se va a establecer.

### <a name="remarks"></a>Comentarios

Este método establece [CMFCToolBarButton:: m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle) en *nStyle* también deshabilita el cuadro de texto cuando la aplicación está en modo de personalización y la habilita cuando la aplicación no está en modo de personalización (vea [CMFCToolBar:: SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode) y [CMFCToolBar:: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)). Vea [estilos de control de barra de herramientas](../../mfc/reference/toolbar-control-styles.md) para obtener una lista de marcas de estilo válidas.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton (clase)](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CEdit (clase)](../../mfc/reference/cedit-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)
