---
title: Clase CMFCToolBarDateTimeCtrl
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CanBeStretched
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CopyFrom
- AFXTOOLBARDATETIMECTRL/CMFCToolBarButton::ExportToMenuButton
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetByCmd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetHwnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTimeAll
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::HaveHotBorder
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::NotifyCommand
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnAddToCustomizePage
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnChangeParentWnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnClick
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnCtlColor
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnMove
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnShow
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnUpdateToolTip
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTimeAll
helpviewer_keywords:
- CMFCToolBarDateTimeCtrl [MFC], CMFCToolBarDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], CanBeStretched
- CMFCToolBarDateTimeCtrl [MFC], CopyFrom
- CMFCToolBarButton [MFC], ExportToMenuButton
- CMFCToolBarDateTimeCtrl [MFC], GetByCmd
- CMFCToolBarDateTimeCtrl [MFC], GetDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], GetHwnd
- CMFCToolBarDateTimeCtrl [MFC], GetTime
- CMFCToolBarDateTimeCtrl [MFC], GetTimeAll
- CMFCToolBarDateTimeCtrl [MFC], HaveHotBorder
- CMFCToolBarDateTimeCtrl [MFC], NotifyCommand
- CMFCToolBarDateTimeCtrl [MFC], OnAddToCustomizePage
- CMFCToolBarDateTimeCtrl [MFC], OnChangeParentWnd
- CMFCToolBarDateTimeCtrl [MFC], OnClick
- CMFCToolBarDateTimeCtrl [MFC], OnCtlColor
- CMFCToolBarDateTimeCtrl [MFC], OnGlobalFontsChanged
- CMFCToolBarDateTimeCtrl [MFC], OnMove
- CMFCToolBarDateTimeCtrl [MFC], OnShow
- CMFCToolBarDateTimeCtrl [MFC], OnUpdateToolTip
- CMFCToolBarDateTimeCtrl [MFC], SetTime
- CMFCToolBarDateTimeCtrl [MFC], SetTimeAll
ms.assetid: a3853cb9-8ebc-444f-a1e4-9cf905e24c18
ms.openlocfilehash: 7ab6a240a403e70446ebc1860474f6cb9e1d71e3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504770"
---
# <a name="cmfctoolbardatetimectrl-class"></a>Clase CMFCToolBarDateTimeCtrl

Un botón de la barra de herramientas que contiene un control de selector de fecha y hora.

## <a name="syntax"></a>Sintaxis

```
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|Construye un objeto `CMFCToolBarDateTimeCtrl`.|
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|Especifica si un usuario puede ajustar el botón durante la personalización. (Invalida [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)).|
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|Copia las propiedades de otro botón de la barra de herramientas en el botón actual. (Invalida [CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)).|
|`CMFCToolBarDateTimeCtrl::DuplicateData`|Reservado para un uso futuro.|
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|Copia texto del botón de la barra de herramientas en un menú.|
|`CMFCToolBarDateTimeCtrl::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|Recupera el primer `CMFCToolBarDateTimeCtrl` objeto de la aplicación que tiene el identificador de comando especificado.|
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|Devuelve un puntero al control de selector de fecha y hora.|
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|Recupera el identificador de ventana asociado al botón de la barra de herramientas. (Invalida [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)).|
|`CMFCToolBarDateTimeCtrl::GetThisClass`|Lo usa el marco de trabajo para obtener un puntero al objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|Obtiene la hora seleccionada de un control selector de fecha y hora y la coloca en una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) especificada.|
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|Devuelve la hora seleccionada desde el botón de control selector de hora que tiene un identificador de comando especificado.|
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|Determina si se muestra un borde del botón cuando un usuario selecciona el botón. (Invalida [CMFCToolBarButton:: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)).|
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|Especifica si el botón procesa el mensaje [WM_COMMAND](/windows/win32/menurc/wm-command) . (Invalida [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)).|
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|Lo llama el marco de trabajo cuando el botón se agrega a un cuadro de diálogo de personalización. (Invalida [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)).|
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|Lo llama el marco de trabajo para calcular el tamaño del botón para el contexto de dispositivo y el estado de acoplamiento especificados. (Invalida [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)).|
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|Lo llama el marco de trabajo cuando el botón se inserta en una nueva barra de herramientas. (Invalida [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)).|
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|Lo llama el marco de trabajo cuando el usuario hace clic en el control. (Invalida [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)).|
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|Lo llama el marco de trabajo cuando la barra de herramientas primaria controla un mensaje WM_CTLCOLOR. (Invalida [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)).|
|`CMFCToolBarDateTimeCtrl::OnDraw`|Lo llama el marco de trabajo para dibujar el botón usando los estilos y las opciones especificados. (Invalida [CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)).|
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|Lo llama el marco de trabajo para dibujar el botón en el panel **comandos** del cuadro de diálogo **personalizar** . (Invalida [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)).|
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|Lo llama el marco de trabajo cuando ha cambiado la fuente global. (Invalida [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)).|
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|Lo llama el marco de trabajo cuando se mueve la barra de herramientas primaria. (Invalida [CMFCToolBarButton:: Move](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)).|
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|Lo llama el marco de trabajo cuando el botón se vuelve visible o invisible. (Invalida [CMFCToolBarButton:: show](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)).|
|`CMFCToolBarDateTimeCtrl::OnSize`|Lo llama el marco de trabajo cuando cambia el tamaño o la posición de la barra de herramientas primaria y este cambio hace que el botón cambie de tamaño. (Invalida [CMFCToolBarButton:: datasize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)).|
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|Lo llama el marco de trabajo cuando la barra de herramientas primaria actualiza el texto de información sobre herramientas. (Invalida [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)).|
|`CMFCToolBarDateTimeCtrl::Serialize`|Lee este objeto de un archivo o lo escribe en un archivo, (invalida [CMFCToolBarButton:: Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)).|
|`CMFCToolBarDateTimeCtrl::SetStyle`|Establece el estilo del botón de la barra de herramientas. (Invalida [CMFCToolBarButton:: setStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)).|
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|Establece la fecha y hora del control de selector de hora.|
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|Establece la fecha y hora en todas las instancias del control de selector de hora que tienen un identificador de comando especificado.|

## <a name="remarks"></a>Comentarios

Para obtener un ejemplo de cómo usar un control de selector de fecha y hora, vea el proyecto de ejemplo ToolbarDateTimePicker. Para obtener información sobre cómo agregar botones de control a las barras de [herramientas, vea Tutorial: Colocar controles en las barras](../../mfc/walkthrough-putting-controls-on-toolbars.md)de herramientas.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtoolbardatetimectrl. h

##  <a name="canbestretched"></a>  CMFCToolBarDateTimeCtrl::CanBeStretched

Especifica si un usuario puede ajustar el botón durante la personalización.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Valor devuelto

Este método devuelve TRUE.

### <a name="remarks"></a>Comentarios

De forma predeterminada, el marco de trabajo no permite al usuario ajustar un botón de la barra de herramientas durante la personalización. Este método extiende la implementación de la clase base ( [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) permitiendo al usuario ajustar un botón de la barra de herramientas de fecha y hora durante la personalización.

##  <a name="cmfctoolbardatetimectrl"></a>  CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl

Crea e inicializa un objeto [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md) .

```
CMFCToolBarDateTimeCtrl(
    UINT uiID,
    int iImage,
    DWORD dwStyle=0,
    int iWidth=0);
```

### <a name="parameters"></a>Parámetros

*uiID*<br/>
de IDENTIFICADOR del control.

*iImage*<br/>
de Índice de la imagen en el `CMFCToolBarImages` objeto de la barra de herramientas.

*dwStyle*<br/>
de Estilo de la `CMFCToolBarDateTimeCtrlImpl` ventana que se crea cuando un usuario hace clic en el botón.

*iWidth*<br/>
de Ancho del control, en píxeles.

### <a name="remarks"></a>Comentarios

Este objeto se inicializa en la fecha y hora del sistema. El estilo de ventana del objeto `CMFCToolBarDateTimeCtrlImpl` interno incluye el parámetro *dwStyle* y los estilos WS_CHILD y WS_VISIBLE. Estos estilos no se pueden cambiar mediante `CMFCToolBarDateTimeCtrl::SetStyle`el uso de. Utilice `SetStyle` para cambiar el estilo `CMFCToolBarDateTimeCtrl` del control.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto de `CMFCToolBarDateTimeCtrl` la clase. Este fragmento de código forma parte del [ejemplo de selector de fecha y hora](../../overview/visual-cpp-samples.md)de la barra de herramientas.

[!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]

##  <a name="copyfrom"></a>  CMFCToolBarDateTimeCtrl::CopyFrom

Copia las propiedades de otro botón de la barra de herramientas en el botón actual.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
de Referencia al botón de origen desde el que se va a copiar.

### <a name="remarks"></a>Comentarios

Llame a este método para copiar otro botón de la barra de herramientas en este botón de la barra de herramientas. *src* debe ser de tipo `CMFCToolBarDateTimeCtrl`.

##  <a name="exporttomenubutton"></a>  CMFCToolBarDateTimeCtrl::ExportToMenuButton

Copia texto del botón de la barra de herramientas en un menú.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parámetros

*menuButton*<br/>
de Referencia al botón de menú de destino.

### <a name="return-value"></a>Valor devuelto

Este método devuelve TRUE.

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de la clase base ( [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) cargando el recurso de cadena que está asociado con el identificador de comando del control. Para obtener más información sobre los recursos de cadena, vea [CStringT:: LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring).

##  <a name="getbycmd"></a>  CMFCToolBarDateTimeCtrl::GetByCmd

Recupera el primer `CMFCToolBarDateTimeCtrl` objeto de la aplicación que tiene el identificador de comando especificado.

```
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
de IDENTIFICADOR de comando del botón que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

Primer `CMFCToolBarDateTimeCtrl` objeto de la aplicación que tiene el identificador de comando especificado, o null si no `CMFCToolBarDateTimeCtrl` hay ningún objeto con el identificador de comando especificado.

### <a name="remarks"></a>Comentarios

Este método de utilidad compartida se usa en métodos como [CMFCToolBarDateTimeCtrl:: SetTimeAll](#settimeall) y [CMFCToolBarDateTimeCtrl:: GetTimeAll](#gettimeall) para establecer u obtener la fecha y la hora de todas las instancias del control de selector de tiempo que tienen un identificador de comando especificado.

##  <a name="getdatetimectrl"></a>  CMFCToolBarDateTimeCtrl::GetDateTimeCtrl

Devuelve un puntero al control de selector de fecha y hora.

```
CDateTimeCtrl* GetDateTimeCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al control de selector de fecha y hora; o NULL si el control no existe.

### <a name="remarks"></a>Comentarios

La `CMFCToolBarDateTimeCtrl` clase inicializa el miembro `m_pWndDateTime` de datos cuando se inserta un `CMFCToolBarDateTimeCtrl` objeto en una barra de herramientas.

##  <a name="gethwnd"></a>  CMFCToolBarDateTimeCtrl::GetHwnd

Recupera el identificador de ventana asociado al botón de la barra de herramientas.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Valor devuelto

Identificador de ventana asociado al botón de la barra de herramientas de fecha y hora.

### <a name="remarks"></a>Comentarios

Este método invalida el método [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) .

##  <a name="gettime"></a>  CMFCToolBarDateTimeCtrl::GetTime

Obtiene la hora seleccionada desde el control de selector de fecha y hora asociado y la coloca en una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) especificada.

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Parámetros

*timeDest*<br/>
enuncia En la primera sobrecarga, un objeto de [clase COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) que recibirá la información de hora del sistema. En la segunda sobrecarga, un objeto [ctime](../../atl-mfc-shared/reference/ctime-class.md) que recibirá la información de hora del sistema.

*pTimeDest*<br/>
enuncia Puntero a la estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) para recibir la información de hora del sistema. No debe ser NULL.

### <a name="return-value"></a>Valor devuelto

En la primera sobrecarga, es distinto de cero si la hora se escribe correctamente en el objeto de la [clase COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ; de lo contrario, es 0. En la segunda y tercera sobrecargas, el valor devuelto es un valor DWORD que es igual al miembro dwFlag establecido en la estructura [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) .

### <a name="remarks"></a>Comentarios

El método establece el miembro de la estructura [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) dwFlags para indicar si el selector de fecha y hora se establece en una fecha y hora. Si el valor es igual a GDT_NONE, el control se establece `no date` en status y se usa el estilo DTS_SHOWNONE. Si el valor devuelto es igual a GDT_VALID, la hora del sistema se almacena correctamente en la ubicación de destino.

##  <a name="gettimeall"></a>  CMFCToolBarDateTimeCtrl::GetTimeAll

Devuelve la hora seleccionada por el usuario desde el botón de control selector de hora que tiene un identificador de comando especificado.

```
static BOOL GetTimeAll(
    UINT uiCmd,
    COleDateTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,
    CTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,
    LPSYSTEMTIME pTimeDest);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
de Especifica el identificador de comando de un botón de la barra de herramientas.

*timeDest*<br/>
enuncia En la primera sobrecarga, un objeto de [clase COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) que recibirá la información de hora del sistema. En la segunda sobrecarga, un objeto [ctime](../../atl-mfc-shared/reference/ctime-class.md) que recibirá la información de hora del sistema.

*pTimeDest*<br/>
enuncia Puntero a la estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) para recibir la información de hora del sistema. No debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Si el marco no encuentra un botón de la barra de herramientas que coincida con el identificador de comando *uiCmd*, el valor devuelto es cero en la primera sobrecarga y GDT_NONE en las otras sobrecargas. Si se encuentra el botón de barra de herramientas, el valor devuelto es el mismo que el valor devuelto de una llamada a [CMFCToolBarDateTimeCtrl:: getTime](#gettime) en ese botón. Un valor devuelto de cero o GDT_NONE puede producirse cuando se encuentra el botón, lo que indica que `GetTime` la llamada a no devolvió una fecha válida por algún otro motivo.

### <a name="remarks"></a>Comentarios

Este método busca un botón de la barra de herramientas que tenga el identificador de comando especificado y llama al método [CMFCToolBarDateTimeCtrl:: getTime](#gettime) en ese botón.

##  <a name="havehotborder"></a>  CMFCToolBarDateTimeCtrl::HaveHotBorder

Determina si se muestra un borde del botón cuando un usuario selecciona el botón.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si un botón muestra su borde cuando está seleccionado; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método devuelve un valor distinto de cero si el control está visible.

##  <a name="notifycommand"></a>  CMFCToolBarDateTimeCtrl::NotifyCommand

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

Este método extiende la implementación de la clase base ( [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) procesando la notificación [DTN_DATETIMECHANGE](/windows/win32/Controls/dtn-datetimechange) . Actualiza el estado de hora interna y actualiza la propiedad de tiempo de `CMFCToolBarDateTimeCtrl` todos los objetos con el mismo identificador de comando.

##  <a name="onaddtocustomizepage"></a>  CMFCToolBarDateTimeCtrl::OnAddToCustomizePage

Lo llama el marco de trabajo cuando el botón se agrega a un cuadro de diálogo de personalización.

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base, [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage), mediante la copia de las propiedades del primer control de fecha y hora de cualquier barra de herramientas que tenga el mismo identificador de comando que este objeto. Este método no hace nada si ninguna barra de herramientas tiene un control de fecha y hora que tiene el mismo identificador de comando que este objeto.

Para obtener más información sobre el cuadro de diálogo **personalizar** , consulte [clase CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

##  <a name="onchangeparentwnd"></a>  CMFCToolBarDateTimeCtrl::OnChangeParentWnd

Lo llama el marco de trabajo cuando el botón se inserta en una nueva barra de herramientas.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
de Nueva ventana primaria.

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de la clase base ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) al volver a crear el `CMFCToolBarDateTimeCtrlImpl` objeto interno.

##  <a name="onclick"></a>  CMFCToolBarDateTimeCtrl::OnClick

Lo llama el marco de trabajo cuando el usuario hace clic en el control.

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

Este método invalida la implementación de la clase base, [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), devolviendo un valor distinto de cero si el `CMFCToolBarDateTimeCtrlImpl` objeto interno es visible.

##  <a name="onctlcolor"></a>  CMFCToolBarDateTimeCtrl::OnCtlColor

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

Identificador del pincel global que el marco de trabajo usa para pintar el fondo del botón.

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de la clase base, [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor), estableciendo los colores de texto y de fondo del contexto de dispositivo proporcionado en los colores de fondo y de texto globales, respectivamente.

Para obtener más información sobre las opciones globales que están disponibles para la aplicación, consulte [estructura AFX_GLOBAL_DATA](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onglobalfontschanged"></a>  CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged

Lo llama el marco de trabajo cuando ha cambiado la fuente global.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) cambiando la fuente del control por la fuente global.

Para obtener más información sobre las opciones globales que están disponibles para la aplicación, consulte [estructura AFX_GLOBAL_DATA](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onmove"></a>  CMFCToolBarDateTimeCtrl::OnMove

Lo llama el marco de trabajo cuando se mueve la barra de herramientas primaria.

```
virtual void OnMove();
```

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de clase predeterminada ( [CMFCToolBarButton:: Move](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) actualizando la posición del objeto interno `CMFCToolBarDateTimeCtrlImpl` .

##  <a name="onshow"></a>  CMFCToolBarDateTimeCtrl::OnShow

Lo llama el marco de trabajo cuando el botón se vuelve visible o invisible.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bShow*<br/>
de Especifica si el botón está visible. Si este parámetro es TRUE, el botón está visible. De lo contrario, el botón no está visible.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton:: show](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) mostrando el botón si *bShow* es true. De lo contrario, este método oculta el botón.

##  <a name="onsize"></a>  CMFCToolBarDateTimeCtrl::OnSize

Lo llama el marco de trabajo cuando cambia el tamaño o la posición de la barra de herramientas primaria y este cambio hace que el botón cambie de tamaño.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parámetros

*iSize*<br/>
de Nuevo ancho del botón, en píxeles.

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de clase predeterminada ( [CMFCToolBarButton:: datasize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)) actualizando el tamaño y la posición del objeto interno `CMFCToolBarDateTimeCtrlImpl` .

##  <a name="onupdatetooltip"></a>  CMFCToolBarDateTimeCtrl::OnUpdateToolTip

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
de La ventana primaria.

*iButtonIndex*<br/>
de Índice de base cero del botón de la colección de botones primario.

*wndToolTip*<br/>
de Control que muestra el texto de la información sobre herramientas.

*str*<br/>
enuncia `CString` Objeto que recibe el texto de información sobre herramientas actualizado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método actualiza el texto de información sobre herramientas; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) mostrando el texto de información sobre herramientas asociado al botón. Si el botón no está acoplado horizontalmente, este método no hace nada y devuelve FALSE.

##  <a name="settime"></a>  CMFCToolBarDateTimeCtrl::SetTime

Establece la fecha y hora del control de selector de hora.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>Parámetros

*timeNew*<br/>
de En la primera versión, se trata de una referencia a un objeto de la [clase COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) que contiene la hora a la que se establecerá el control. En la segunda versión, puntero a un objeto [ctime](../../atl-mfc-shared/reference/ctime-class.md) que contiene la hora a la que se establecerá el control.

*pTimeNew*<br/>
de Puntero a la estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que contiene la hora a la que se establecerá el control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Establece la hora de un control de selector de fecha y hora llamando a [CDateTimeCtrl:: setTime](../../mfc/reference/cdatetimectrl-class.md#settime).

##  <a name="settimeall"></a>  CMFCToolBarDateTimeCtrl::SetTimeAll

Establece la fecha y hora en todas las instancias del control de selector de hora que tienen un identificador de comando especificado.

```
static BOOL SetTimeAll(
    UINT uiCmd,
    const COleDateTime& timeNew);

static BOOL SetTimeAll(
    UINT uiCmd,
    const CTime* pTimeNew);

static BOOL SetTimeAll(
    UINT uiCmd,
    LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
de Especifica el identificador de comando de un botón de la barra de herramientas.

*timeNew*<br/>
de En la primera versión, un objeto de [clase COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) que contiene la hora a la que se establecerá el control. En la segunda versión, puntero a un objeto [ctime](../../atl-mfc-shared/reference/ctime-class.md) que contiene la hora a la que se establecerá el control.

*pTimeNew*<br/>
de Puntero a la estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que contiene la hora a la que se establecerá el control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Busca un botón de la barra de herramientas con el identificador de comando especificado y establece la hora en un control de selector de fecha y hora llamando a [CMFCToolBarDateTimeCtrl:: setTime](#settime).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton (clase)](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)
