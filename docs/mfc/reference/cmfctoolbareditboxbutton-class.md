---
title: CMFCToolBarEditBoxButton Clase
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
ms.openlocfilehash: 064ebe1c8fe377064d410d09e5ef60ed628df2f3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753999"
---
# <a name="cmfctoolbareditboxbutton-class"></a>CMFCToolBarEditBoxButton Clase

Un botón de barra de herramientas que contiene un control de edición ( [CEdit Class](../../mfc/reference/cedit-class.md)).

## <a name="syntax"></a>Sintaxis

```
class CMFCToolBarEditBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](#cmfctoolbareditboxbutton)|Construye un objeto `CMFCToolBarEditBoxButton`.|
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CanBestretched](#canbestretched)|Especifica si un usuario puede estirar el botón durante la personalización. (Reemplaza [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarEditBoxButton::CopyFrom](#copyfrom)|Copia las propiedades de otro botón de la barra de herramientas en el botón actual. (Reemplaza [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::CreateEdit](#createedit)|Crea un nuevo control de edición en el botón.|
|`CMFCToolBarEditBoxButton::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|[CMFCToolBarEditBoxButton::GetByCmd](#getbycmd)|Recupera el `CMFCToolBarEditBoxButton` primer objeto de la aplicación que tiene el identificador de comando especificado.|
|[CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall)|Recupera el texto del primer control de barra de herramientas del cuadro de edición que tiene el identificador de comando especificado.|
|[CMFCToolBarEditBoxButton::GetContextMenuID](#getcontextmenuid)|Recupera el identificador de recurso del menú contextual asociado al botón.|
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|Recupera el rectángulo delimitador de la parte de edición del botón del cuadro de edición.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::GetEditBox](#geteditbox)|Devuelve un puntero al control de edición incrustado en el botón.|
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|Recupera el identificador de ventana asociado al botón de barra de herramientas. (Reemplaza [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|Recupera la región del área de cliente del botón que se debe volver a dibujar. (Reemplaza [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect).)|
|`CMFCToolBarEditBoxButton::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|[CMFCToolBarEditBoxButton::HaveHotBorder](#havehotborder)|Determina si se muestra un borde del botón cuando un usuario hace clic en el botón. (Reemplaza [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|Determina si los botones del cuadro de edición tienen un estilo plano.|
|[CMFCToolBarEditBoxButton::NotifyCommand](#notifycommand)|Especifica si el botón procesa el [mensaje de WM_COMMAND.](/windows/win32/menurc/wm-command) (Reemplaza [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarEditBoxButton::OnAddToCustomizePage](#onaddtocustomizepage)|Llamado por el marco de trabajo cuando el botón se agrega a un **personalizar** cuadro de diálogo. (Reemplaza [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarEditBoxButton::OnCalculateSize`|Llamado por el marco de trabajo para calcular el tamaño del botón para el contexto de dispositivo especificado y el estado de acoplamiento. (Reemplaza [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|Llamado por el marco de trabajo cuando el botón se inserta en una nueva barra de herramientas. (Reemplaza [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarEditBoxButton::OnClick](#onclick)|Llamado por el marco de trabajo cuando el usuario hace clic en el botón del mouse. (Reemplaza [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|Llamado por el marco de trabajo cuando la barra de herramientas primaria controla un mensaje de WM_CTLCOLOR. (Reemplaza [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarEditBoxButton::OnDraw`|Llamado por el marco de trabajo para dibujar el botón mediante el uso de los estilos y opciones especificados. (Reemplaza [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|Llamado por el marco de trabajo para dibujar el botón en el **comandos** panel de la **personalizar** cuadro de diálogo. (Reemplaza [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarEditBoxButton::OnGlobalFontsChanged](#onglobalfontschanged)|Llamado por el marco de trabajo cuando la fuente global ha cambiado. (Reemplaza [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|Llamado por el marco de trabajo cuando se mueve la barra de herramientas principal. (Reemplaza [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|
|[CMFCToolBarEditBoxButton::OnShow](#onshow)|Llamado por el marco de trabajo cuando el botón se vuelve visible o invisible. (Reemplaza [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|[CMFCToolBarEditBoxButton::OnSize](#onsize)|Llamado por el marco de trabajo cuando la barra de herramientas primaria cambia su tamaño o posición y este cambio hace que el botón cambie de tamaño. (Reemplaza [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarEditBoxButton::OnUpdateToolTip](#onupdatetooltip)|Llamado por el marco de trabajo cuando la barra de herramientas primaria actualiza su texto de información sobre herramientas. (Reemplaza [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarEditBoxButton::Serialize`|Lee este objeto de un archivo o lo escribe en un archivo. (Reemplaza [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|`CMFCToolBarEditBoxButton::SetACCData`|Rellena el `CAccessibilityData` objeto proporcionado con datos de accesibilidad desde el botón de la barra de herramientas. (Reemplaza [CMFCToolBarButton::SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).)|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetContents](#setcontents)|Establece el texto en el control de edición del botón.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall)|Busca el botón de control de edición que tiene un identificador de comando especificado y establece el texto en el control de edición de ese botón.|
|[CMFCToolBarEditBoxButton::SetContextMenuID](#setcontextmenuid)|Especifica el identificador de recurso del menú contextual asociado al botón.|
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|Especifica la apariencia de estilo plano de los botones del cuadro de edición en la aplicación.|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton::SetStyle](#setstyle)|Especifica el estilo del botón. (Reemplaza [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|

## <a name="remarks"></a>Observaciones

Para agregar un botón de cuadro de edición a una barra de herramientas, siga estos pasos:

1. Reserve un id. de recurso ficticio para el botón en el recurso primario de la barra de herramientas.

2. Construir `CMFCToolBarEditBoxButton` un objeto.

3. En el controlador de mensajes que procesa el mensaje de AFX_WM_RESETTOOLBAR, reemplace el botón ficticio con el nuevo botón de cuadro combinado mediante [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Para obtener más información, vea [Tutorial: Colocar controles en barras](../../mfc/walkthrough-putting-controls-on-toolbars.md)de herramientas .

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCToolBarEditBoxButton` . En el ejemplo se muestra cómo especificar que un usuario puede estirar el botón durante la personalización, especificar que se muestra un borde del botón cuando un usuario hace clic en el botón, establecer el texto en el control de cuadro de texto, especificar la apariencia de estilo plano de los botones del cuadro de edición en la aplicación y especificar el estilo de un control de cuadro de edición de barra de herramientas.

[!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

`CMFCToolBarEditBoxButton`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtoolbareditboxbutton.h

## <a name="cmfctoolbareditboxbuttoncanbestretched"></a><a name="canbestretched"></a>CMFCToolBarEditBoxButton::CanBestretched

Especifica si un usuario puede estirar el botón durante la personalización.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Valor devuelto

Este método devuelve TRUE.

### <a name="remarks"></a>Observaciones

De forma predeterminada, el marco de trabajo no permite al usuario estirar un botón de barra de herramientas durante la personalización. Este método extiende la implementación de la clase base ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) al permitir al usuario estirar un botón de barra de herramientas del cuadro de edición durante la personalización.

## <a name="cmfctoolbareditboxbuttoncmfctoolbareditboxbutton"></a><a name="cmfctoolbareditboxbutton"></a>CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton

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
[en] Especifica el identificador de control.

*iImage*<br/>
[en] Especifica el índice de base cero de una imagen de barra de herramientas. La imagen se encuentra en el [CMFCToolBarImages clase](../../mfc/reference/cmfctoolbarimages-class.md) objeto que [CMFCToolBar clase](../../mfc/reference/cmfctoolbar-class.md) mantiene.

*dwStyle*<br/>
[en] Especifica el estilo de control de edición.

*iWidth*<br/>
[en] Especifica el ancho en píxeles del control de edición.

### <a name="remarks"></a>Observaciones

El constructor predeterminado establece el estilo de control de edición en la siguiente combinación:

WS_CHILD de la casa de la casa de WS_VISIBLE ES_AUTOHSCROLL

El ancho predeterminado del control es de 150 píxeles.

## <a name="cmfctoolbareditboxbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCToolBarEditBoxButton::CopyFrom

Copia las propiedades de otro botón de la barra de herramientas en el botón actual.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
[en] Una referencia al botón de origen desde el que se copia.

### <a name="remarks"></a>Observaciones

Llame a este método para copiar otro botón de la barra de herramientas en este botón de la barra de herramientas. *src* debe ser `CMFCToolBarEditBoxButton`de tipo .

## <a name="cmfctoolbareditboxbuttoncreateedit"></a><a name="createedit"></a>CMFCToolBarEditBoxButton::CreateEdit

Crea un nuevo control de edición en el botón.

```
virtual CEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[en] Especifica la ventana primaria del control de edición. No debe ser NULL.

*Rect*<br/>
[en] Especifica el tamaño y la posición del control de edición.

### <a name="return-value"></a>Valor devuelto

Un puntero al control de edición recién creado; es NULL si se produce un error en la creación y los datos adjuntos del control.

### <a name="remarks"></a>Observaciones

Construir un `CMFCToolBarEditBoxButton` objeto en dos pasos. En primer lugar, llame `CreateEdit`al constructor y, a continuación, `CMFCToolBarEditBoxButton` llame a , que crea el control de edición de Windows y lo adjunta al objeto.

## <a name="cmfctoolbareditboxbuttongetbycmd"></a><a name="getbycmd"></a>CMFCToolBarEditBoxButton::GetByCmd

Recupera el `CMFCToolBarEditBoxButton` primer objeto de la aplicación que tiene el identificador de comando especificado.

```
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[en] El identificador de comando del botón que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

El `CMFCToolBarEditBoxButton` primer objeto de la aplicación que tiene el identificador de comando especificado, o NULL si no existe dicho objeto.

### <a name="remarks"></a>Observaciones

Este método de utilidad compartida lo utilizan métodos como [CMFCToolBarEditBoxButton::SetContentsAll](#setcontentsall) y [CMFCToolBarEditBoxButton::GetContentsAll](#getcontentsall) para establecer u obtener el texto del primer control de barra de herramientas del cuadro de edición que tiene el identificador de comando especificado.

## <a name="cmfctoolbareditboxbuttongetcontentsall"></a><a name="getcontentsall"></a>CMFCToolBarEditBoxButton::GetContentsAll

Recupera el texto del primer control de barra de herramientas del cuadro de edición que tiene el identificador de comando especificado.

```
static CString __stdcall GetContentsAll(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[en] El identificador de comando del botón desde el que se va a recuperar el contenido.

### <a name="return-value"></a>Valor devuelto

Objeto `CString` que contiene el texto del primer control de barra de herramientas del cuadro de edición que tiene el identificador de comando especificado.

### <a name="remarks"></a>Observaciones

Este método devuelve la `CMFCToolBarEditBoxButton` cadena vacía si ningún objeto tiene el identificador de comando especificado.

## <a name="cmfctoolbareditboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a>CMFCToolBarEditBoxButton::GetContextMenuID

Recupera el identificador de recurso del menú contextual asociado al botón.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Valor devuelto

El identificador de recurso del menú contextual asociado al botón o 0 si el botón no tiene ningún menú contextual asociado.

### <a name="remarks"></a>Observaciones

El marco de trabajo usa el identificador de recurso para crear el menú contextual cuando el usuario hace clic con el botón derecho en el botón.

## <a name="cmfctoolbareditboxbuttongeteditborder"></a><a name="geteditborder"></a>CMFCToolBarEditBoxButton::GetEditBorder

Recupera el rectángulo delimitador de la parte de edición del botón del cuadro de edición.

```
virtual void GetEditBorder(CRect& rectBorder);
```

### <a name="parameters"></a>Parámetros

*rectBorder*<br/>
[fuera] Una referencia `CRect` al objeto que recibe el rectángulo delimitador.

### <a name="remarks"></a>Observaciones

Este método recupera el rectángulo delimitador del control de edición en las coordenadas de cliente. Expande el tamaño del rectángulo en cada dirección en un píxel.

El [CMFCVisualManager::OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder) método llama a este método `CMFCToolBarEditBoxButton` cuando dibuja el borde alrededor de un objeto.

## <a name="cmfctoolbareditboxbuttongeteditbox"></a><a name="geteditbox"></a>CMFCToolBarEditBoxButton::GetEditBox

Devuelve un puntero a la [CEdit clase](../../mfc/reference/cedit-class.md) control que está incrustado en el botón.

```
CEdit* GetEditBox() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la [CEdit clase](../../mfc/reference/cedit-class.md) control que contiene el botón. Es NULL si `CEdit` el control aún no se ha creado.

### <a name="remarks"></a>Observaciones

Puede crear `CEdit` el control llamando a [CMFCToolBarEditBoxButton::CreateEdit](#createedit).

## <a name="cmfctoolbareditboxbuttongethwnd"></a><a name="gethwnd"></a>CMFCToolBarEditBoxButton::GetHwnd

Recupera el identificador de ventana asociado al botón de barra de herramientas.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Valor devuelto

El identificador de ventana que está asociado con el botón.

### <a name="remarks"></a>Observaciones

Este método reemplaza el [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) método devolviendo el identificador de ventana de la parte de control de edición del botón de cuadro de edición.

## <a name="cmfctoolbareditboxbuttongetinvalidaterect"></a><a name="getinvalidaterect"></a>CMFCToolBarEditBoxButton::GetInvalidateRect

Recupera la región del área de cliente del botón que se debe volver a dibujar.

```
virtual const CRect GetInvalidateRect() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto `CRect` que especifica la región que se debe volver a dibujar.

### <a name="remarks"></a>Observaciones

Este método extiende la implementación de la clase base, [CMFCToolBarButton::GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect), incluyendo en la región el área de la etiqueta de texto.

## <a name="cmfctoolbareditboxbuttonhavehotborder"></a><a name="havehotborder"></a>CMFCToolBarEditBoxButton::HaveHotBorder

Determina si se muestra un borde del botón cuando un usuario hace clic en el botón.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si un botón muestra su borde cuando está seleccionado; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Este método extiende la implementación de la clase base, [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder), devolviendo un valor distinto de cero si el control está visible.

## <a name="cmfctoolbareditboxbuttonisflatmode"></a><a name="isflatmode"></a>CMFCToolBarEditBoxButton::IsFlatMode

Determina si los botones del cuadro de edición tienen un estilo plano.

```
static BOOL __stdcall IsFlatMode();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los botones tienen un estilo plano; de lo contrario, 0.

### <a name="remarks"></a>Observaciones

De forma predeterminada, los botones del cuadro de edición tienen un estilo plano. Utilice el [CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode) método para cambiar la apariencia de estilo plano para la aplicación.

## <a name="cmfctoolbareditboxbuttonnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarEditBoxButton::NotifyCommand

Especifica si el botón procesa el [mensaje de WM_COMMAND.](/windows/win32/menurc/wm-command)

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parámetros

*iNotifyCode*<br/>
[en] El mensaje de notificación asociado al comando.

### <a name="return-value"></a>Valor devuelto

TRUESi el botón procesa el mensaje de WM_COMMAND o FALSE para indicar que la barra de herramientas primaria debe controlar el mensaje.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método cuando está a punto de enviar un [mensaje de WM_COMMAND](/windows/win32/menurc/wm-command) a la ventana primaria.

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) procesando la [notificación EN_UPDATE.](/windows/win32/Controls/en-update) Para cada cuadro de edición con el mismo identificador de comando que este objeto, establece su etiqueta de texto en la etiqueta de texto de este objeto.

## <a name="cmfctoolbareditboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolBarEditBoxButton::OnAddToCustomizePage

Llamado por el marco de trabajo cuando el botón se agrega a un **personalizar** cuadro de diálogo.

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Observaciones

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)) copiando las propiedades del control de cuadro de edición en cualquier barra de herramientas que tenga el mismo identificador de comando que este objeto. Este método no hace nada si ninguna barra de herramientas tiene un control de cuadro de edición que tiene el mismo identificador de comando que este objeto.

Para obtener más información sobre el cuadro de diálogo **Personalizar,** vea [CMFCToolBarsCustomizeDialog (Clase)](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

## <a name="cmfctoolbareditboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarEditBoxButton::OnChangeParentWnd

Llamado por el marco de trabajo cuando el botón se inserta en una nueva barra de herramientas.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[en] Un puntero a la nueva ventana primaria.

### <a name="remarks"></a>Observaciones

Este método reemplaza la implementación de la clase base ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) volviendo a crear el objeto interno. `CEdit`

## <a name="cmfctoolbareditboxbuttononclick"></a><a name="onclick"></a>CMFCToolBarEditBoxButton::OnClick

Llamado por el marco de trabajo cuando el usuario hace clic en el botón del mouse.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
[in] Sin utilizar.

*bDelay*<br/>
[in] Sin utilizar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón procesa el mensaje de clic; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Este método reemplaza la implementación de la clase base ( [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)) devolviendo un valor distinto de cero si el objeto interno `CEdit` está visible.

## <a name="cmfctoolbareditboxbuttononctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarEditBoxButton::OnCtlColor

Llamado por el marco de trabajo cuando la barra de herramientas primaria controla un mensaje de WM_CTLCOLOR.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] El contexto del dispositivo que muestra el botón.

*nCtlColor*<br/>
[in] Sin utilizar.

### <a name="return-value"></a>Valor devuelto

Un identificador para el pincel de ventana global.

### <a name="remarks"></a>Observaciones

Este método reemplaza la implementación de la clase base ( [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)) estableciendo el texto y los colores de fondo del contexto de dispositivo proporcionado en el texto global y los colores de fondo, respectivamente.

Para obtener más información acerca de las opciones globales que están disponibles para la aplicación, vea [AFX_GLOBAL_DATA estructura](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbareditboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarEditBoxButton::OnGlobalFontsChanged

Llamado por el marco de trabajo cuando la fuente global ha cambiado.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Observaciones

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) cambiando la fuente del control a la de la fuente global.

Para obtener más información acerca de las opciones globales que están disponibles para la aplicación, vea [AFX_GLOBAL_DATA estructura](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbareditboxbuttononmove"></a><a name="onmove"></a>CMFCToolBarEditBoxButton::OnMove

Llamado por el marco de trabajo cuando se mueve la barra de herramientas principal.

```
virtual void OnMove();
```

### <a name="remarks"></a>Observaciones

Este método reemplaza la implementación de clase predeterminada ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) actualizando la posición del objeto interno `CEdit`

## <a name="cmfctoolbareditboxbuttononshow"></a><a name="onshow"></a>CMFCToolBarEditBoxButton::OnShow

Llamado por el marco de trabajo cuando el botón se vuelve visible o invisible.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bMostrar*<br/>
[en] Especifica si el botón está visible. Si este parámetro es TRUE, el botón es visible. De lo contrario, el botón no está visible.

### <a name="remarks"></a>Observaciones

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) mostrando el botón si *bShow* es TRUE. De lo contrario, este método oculta el botón.

## <a name="cmfctoolbareditboxbuttononsize"></a><a name="onsize"></a>CMFCToolBarEditBoxButton::OnSize

Llamado por el marco de trabajo cuando la barra de herramientas primaria cambia su tamaño o posición y este cambio hace que el botón cambie de tamaño.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parámetros

*iSize*<br/>
[en] El nuevo ancho del botón, en píxeles.

### <a name="remarks"></a>Observaciones

Este método reemplaza la implementación de clase predeterminada, [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize) `CEdit` , actualizando el tamaño y la posición del objeto interno.

## <a name="cmfctoolbareditboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolBarEditBoxButton::OnUpdateToolTip

Llamado por el marco de trabajo cuando la barra de herramientas primaria actualiza su texto de información sobre herramientas.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[in] Sin utilizar.

*iButtonIndex*<br/>
[in] Sin utilizar.

*wndToolTip*<br/>
[en] El control que muestra el texto de información sobre herramientas.

*Str*<br/>
[fuera] Objeto `CString` que recibe el texto de información sobre herramientas actualizado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método actualiza el texto de información sobre herramientas; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) mostrando el texto de información sobre herramientas que está asociado con la parte de edición del botón. Si el `CEdit` objeto interno es NULL `CEdit` o el identificador de ventana del objeto no identifica una ventana existente, este método no hace nada y devuelve FALSE.

## <a name="cmfctoolbareditboxbuttonsetcontents"></a><a name="setcontents"></a>CMFCToolBarEditBoxButton::SetContents

Establece el texto en el control de cuadro de texto.

```
virtual void SetContents(const CString& sContents);
```

### <a name="parameters"></a>Parámetros

*sContents*<br/>
[en] Especifica el nuevo texto que se va a establecer.

## <a name="cmfctoolbareditboxbuttonsetcontentsall"></a><a name="setcontentsall"></a>CMFCToolBarEditBoxButton::SetContentsAll

Busca un [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) objeto que tiene un identificador de comando especificado y establece el texto especificado dentro de su cuadro de texto.

```
static BOOL SetContentsAll(
    UINT uiCmd,
    const CString& strContents);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[en] Especifica el identificador de comando del control para el que se cambiará el texto.

*strContents*<br/>
[en] Especifica el nuevo texto que se va a establecer.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se estableció el texto; 0 si `CMFCToolBarEditBoxButton` el control con el id de comando especificado no existe.

## <a name="cmfctoolbareditboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a>CMFCToolBarEditBoxButton::SetContextMenuID

Especifica el identificador de recurso del menú contextual asociado al botón.

```cpp
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[en] El identificador de recurso del menú contextual.

### <a name="remarks"></a>Observaciones

El marco de trabajo usa el identificador de recurso para crear el menú contextual cuando el usuario hace clic con el botón derecho en el botón de la barra de herramientas.

## <a name="cmfctoolbareditboxbuttonsetflatmode"></a><a name="setflatmode"></a>CMFCToolBarEditBoxButton::SetFlatMode

Especifica la apariencia de estilo plano de los botones del cuadro de edición en la aplicación.

```
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```

### <a name="parameters"></a>Parámetros

*bFlat*<br/>
[en] El estilo plano para los botones del cuadro de edición. Si este parámetro es TRUE, se habilita la apariencia de estilo plano; de lo contrario, la apariencia de estilo plano está desactivada.

### <a name="remarks"></a>Observaciones

El estilo plano predeterminado para los botones del cuadro de edición es TRUE. Utilice el [CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode) método para recuperar la apariencia de estilo plano para la aplicación.

## <a name="cmfctoolbareditboxbuttonsetstyle"></a><a name="setstyle"></a>CMFCToolBarEditBoxButton::SetStyle

Especifica el estilo de un control de cuadro de edición de barra de herramientas.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Parámetros

*nStyle*<br/>
[en] Un nuevo estilo para establecer.

### <a name="remarks"></a>Observaciones

Este método establece [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle) en *nStyle* También deshabilita el cuadro de texto cuando la aplicación está en modo Personalizar y lo habilita cuando la aplicación no está en modo de personalización (consulte [CMFCToolBar::SetCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode) y [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)). Consulte [Estilos](../../mfc/reference/toolbar-control-styles.md) de control de Barra de herramientas para obtener una lista de indicadores de estilo válidos.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton (clase)](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)
