---
title: CMFCToolBarDateTimeCtrl (clase)
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
ms.openlocfilehash: dfe1d3dc058371dd13cc335968b9c3a89e057da2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218480"
---
# <a name="cmfctoolbardatetimectrl-class"></a>CMFCToolBarDateTimeCtrl (clase)

Un botón de barra de herramientas que contiene un control de selector de fecha y hora.

## <a name="syntax"></a>Sintaxis

```
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|Construye un objeto `CMFCToolBarDateTimeCtrl`.|
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|Especifica si un usuario puede expandir el botón durante la personalización. (Invalida [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|Copia las propiedades de otro botón de barra de herramientas a la actual. (Invalida [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarDateTimeCtrl::DuplicateData`|Reservado para un uso futuro.|
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|Copia el texto en el botón de barra de herramientas a un menú.|
|`CMFCToolBarDateTimeCtrl::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|Recupera el primer `CMFCToolBarDateTimeCtrl` objeto en la aplicación que tiene el identificador de comando especificado.|
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|Devuelve un puntero para el control de selector de fecha y hora.|
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|Recupera el identificador de ventana que está asociado con el botón de barra de herramientas. (Invalida [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|`CMFCToolBarDateTimeCtrl::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|Obtiene la hora seleccionada de un control de selector de fecha y hora y lo coloca en un determinado [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) estructura.|
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|Devuelve la hora seleccionada en el botón de control de selector de tiempo que tiene un identificador de comando especificado.|
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|Determina si se muestra un borde del botón cuando un usuario selecciona el botón. (Invalida [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|Especifica si el botón procesa el [WM_COMMAND](/windows/desktop/menurc/wm-command) mensaje. (Invalida [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|Lo llama el marco cuando el botón se agrega a un **personalizar** cuadro de diálogo. (Invalida [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|Lo llama el marco de trabajo para calcular el tamaño del botón para el contexto de dispositivo especificado y el estado de acoplamiento. (Invalida [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|Lo llama el marco cuando el botón se inserta en una nueva barra de herramientas. (Invalida [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|Lo llama el marco cuando el usuario hace clic en el control. (Invalida [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|Lo llama el marco de trabajo cuando la barra de herramientas primario controla un WM_CTLCOLOR (mensaje). (Invalida [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarDateTimeCtrl::OnDraw`|Lo llama el marco de trabajo para dibujar el botón mediante el uso de las opciones y estilos especificados. (Invalida [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|Lo llama el marco de trabajo para dibujar el botón de la **comandos** panel de la **personalizar** cuadro de diálogo. (Invalida [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|Lo llama el marco de trabajo cuando ha cambiado la fuente global. (Invalida [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|Lo llama el marco de trabajo cuando se mueve la barra de herramientas primario. (Invalida [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|Lo llama el marco de trabajo cuando el botón se convierte en visible o invisible. (Invalida [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|`CMFCToolBarDateTimeCtrl::OnSize`|Lo llama el marco de trabajo cuando la barra de herramientas del elemento primario cambia su tamaño o posición y este cambio hace que el botón Cambiar el tamaño. (Invalida [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|Lo llama el marco de trabajo cuando la barra de herramientas principal actualiza su texto de información sobre herramientas. (Invalida [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarDateTimeCtrl::Serialize`|Lee este objeto desde un archivo o lo escribe en un archivo (invalidaciones [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|`CMFCToolBarDateTimeCtrl::SetStyle`|Establece el estilo del botón de barra de herramientas. (Invalida [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|Establece la fecha y hora en el control de selector de hora.|
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|Establece la fecha y hora en todas las instancias del control de selector de tiempo que tienen un identificador de comando especificado.|

## <a name="remarks"></a>Comentarios

Para obtener un ejemplo de cómo usar un control de selector de fecha y hora, vea el proyecto de ejemplo ToolbarDateTimePicker. Para obtener información acerca de cómo agregar botones de control a las barras de herramientas, consulte [Tutorial: Insertar controles en barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtoolbardatetimectrl.h

##  <a name="canbestretched"></a>  CMFCToolBarDateTimeCtrl::CanBeStretched

Especifica si un usuario puede expandir el botón durante la personalización.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Valor devuelto

Este método devuelve TRUE.

### <a name="remarks"></a>Comentarios

De forma predeterminada, el marco de trabajo no permite al usuario ajustar un botón de barra de herramientas durante la personalización. Este método extiende la implementación de la clase base ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)), ya que permite al usuario ajustar un botón de barra de herramientas de fecha y hora durante la personalización.

##  <a name="cmfctoolbardatetimectrl"></a>  CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl

Crea e inicializa un [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md) objeto.

```
CMFCToolBarDateTimeCtrl(
    UINT uiID,
    int iImage,
    DWORD dwStyle=0,
    int iWidth=0);
```

### <a name="parameters"></a>Parámetros

*uiID*<br/>
[in] El identificador de control.

*iImage*<br/>
[in] El índice de la imagen en la barra de herramientas `CMFCToolBarImages` objeto.

*dwStyle*<br/>
[in] El estilo de la `CMFCToolBarDateTimeCtrlImpl` ventana que se crea cuando un usuario hace clic en el botón.

*iWidth*<br/>
[in] El ancho del control, en píxeles.

### <a name="remarks"></a>Comentarios

Este objeto se inicializa en la fecha del sistema y la hora. El estilo de ventana de interno `CMFCToolBarDateTimeCtrlImpl` objeto incluye el *dwStyle* parámetro y los estilos WS_CHILD y WS_VISIBLE. No se puede cambiar estos estilos mediante `CMFCToolBarDateTimeCtrl::SetStyle`. Use `SetStyle` para cambiar el estilo de la `CMFCToolBarDateTimeCtrl` control.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCToolBarDateTimeCtrl` clase. Este fragmento de código forma parte de la [ejemplo de la barra de herramientas Date Time Picker](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]

##  <a name="copyfrom"></a>  CMFCToolBarDateTimeCtrl::CopyFrom

Copia las propiedades de otro botón de barra de herramientas a la actual.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
[in] Una referencia al botón de origen desde el que se va a copiar.

### <a name="remarks"></a>Comentarios

Llame a este método para copiar otro botón de barra de herramientas en este botón de barra de herramientas. *src* debe ser de tipo `CMFCToolBarDateTimeCtrl`.

##  <a name="exporttomenubutton"></a>  CMFCToolBarDateTimeCtrl::ExportToMenuButton

Copia el texto en el botón de barra de herramientas a un menú.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parámetros

*menuButton*<br/>
[in] Una referencia al botón de menú de destino.

### <a name="return-value"></a>Valor devuelto

Este método devuelve TRUE.

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de la clase base ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) al cargar el recurso de cadena que está asociado con el identificador de comando del control. Para obtener más información acerca de los recursos de cadena, vea [CStringT::LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring).

##  <a name="getbycmd"></a>  CMFCToolBarDateTimeCtrl::GetByCmd

Recupera el primer `CMFCToolBarDateTimeCtrl` objeto en la aplicación que tiene el identificador de comando especificado.

```
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[in] El identificador de comando del botón debe recuperar.

### <a name="return-value"></a>Valor devuelto

La primera `CMFCToolBarDateTimeCtrl` objeto en la aplicación que tiene el identificador de comando especificado o NULL si no hay ningún `CMFCToolBarDateTimeCtrl` objetos tienen el identificador de comando especificado.

### <a name="remarks"></a>Comentarios

Este método de utilidad compartida se usa como métodos [CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall) y [CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall) para establecer u obtener la fecha y hora de todas las instancias del tiempo control de selector que tiene un identificador de comando especificado.

##  <a name="getdatetimectrl"></a>  CMFCToolBarDateTimeCtrl::GetDateTimeCtrl

Devuelve un puntero para el control de selector de fecha y hora.

```
CDateTimeCtrl* GetDateTimeCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al control de selector de fecha y hora; o NULL si el control no existe.

### <a name="remarks"></a>Comentarios

El `CMFCToolBarDateTimeCtrl` clase inicializa el `m_pWndDateTime` miembro de datos al insertar un `CMFCToolBarDateTimeCtrl` objeto en una barra de herramientas.

##  <a name="gethwnd"></a>  CMFCToolBarDateTimeCtrl::GetHwnd

Recupera el identificador de ventana que está asociado con el botón de barra de herramientas.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Valor devuelto

El identificador de ventana que está asociado con el botón de barra de herramientas de fecha y hora.

### <a name="remarks"></a>Comentarios

Este método invalida el [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) método.

##  <a name="gettime"></a>  CMFCToolBarDateTimeCtrl::GetTime

Obtiene la hora seleccionada del control selector de hora y fecha asociada y lo coloca en un determinado [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) estructura

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Parámetros

*timeDest*<br/>
[out] En la primera sobrecarga, una [COleDateTime (clase)](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que recibirá la información de hora del sistema. En la segunda sobrecarga, una [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que recibirá la información de hora del sistema.

*pTimeDest*<br/>
[out] Un puntero a la [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) estructura para recibir la información de hora del sistema. No debe ser NULL.

### <a name="return-value"></a>Valor devuelto

En la primera sobrecarga, distinto de cero si se ha escrito correctamente la hora a la [COleDateTime (clase)](../../atl-mfc-shared/reference/coledatetime-class.md) objeto; en caso contrario, 0. En las sobrecargas de segunda y terceros, el valor devuelto es un valor DWORD que es igual que el miembro dwFlag que se estableció en el [NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange) estructura.

### <a name="remarks"></a>Comentarios

El método establece el [NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange) estructura miembro dwFlags para indicar si el selector de fecha y hora se establece en una fecha y hora. Si el valor es igual a GDT_NONE, el control se establece en `no date` estado y usa el estilo DTS_SHOWNONE. Si el valor devuelto es igual a GDT_VALID, la hora del sistema esté almacenada correctamente en la ubicación de destino.

##  <a name="gettimeall"></a>  CMFCToolBarDateTimeCtrl::GetTimeAll

Devuelve la hora seleccionada por el usuario en el botón de control de selector de tiempo que tiene un identificador de comando especificado.

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
[in] Especifica el identificador de comando. de un botón de barra de herramientas

*timeDest*<br/>
[out] En la primera sobrecarga, una [COleDateTime (clase)](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que recibirá la información de hora del sistema. En la segunda sobrecarga, una [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que recibirá la información de hora del sistema.

*pTimeDest*<br/>
[out] Un puntero a la [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) estructura para recibir la información de hora del sistema. No debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Si el marco de trabajo no puede encontrar un botón de barra de herramientas que coincida con el identificador de comando *uiCmd*, el valor devuelto es cero en la primera sobrecarga y GDT_NONE en las otras sobrecargas. Si se encuentra el botón de barra de herramientas, el valor devuelto es el mismo que el valor devuelto de una llamada a [CMFCToolBarDateTimeCtrl::GetTime](#gettime) en ese botón. Devolver de un valor de cero o GDT_NONE puede producirse cuando se encuentra el botón, lo que indica que la llamada a `GetTime` no devolvió una fecha válida por algún otro motivo.

### <a name="remarks"></a>Comentarios

Este método busca un botón de barra de herramientas que tiene el identificador de comando especificado y llama [CMFCToolBarDateTimeCtrl::GetTime](#gettime) método en ese botón.

##  <a name="havehotborder"></a>  CMFCToolBarDateTimeCtrl::HaveHotBorder

Determina si se muestra un borde del botón cuando un usuario selecciona el botón.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si un botón muestra su borde cuando se selecciona; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método devuelve un valor distinto de cero si el control está visible.

##  <a name="notifycommand"></a>  CMFCToolBarDateTimeCtrl::NotifyCommand

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

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) mediante el procesamiento de la [DTN_DATETIMECHANGE](/windows/desktop/Controls/dtn-datetimechange) notificación. Actualiza el estado interno del tiempo y actualiza la propiedad de tiempo de todos los `CMFCToolBarDateTimeCtrl` objetos con el mismo identificador de comando.

##  <a name="onaddtocustomizepage"></a>  CMFCToolBarDateTimeCtrl::OnAddToCustomizePage

Lo llama el marco cuando el botón se agrega a un **personalizar** cuadro de diálogo.

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base, [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage), por copiar las propiedades de la primera fecha y la hora de control en cualquier barra de herramientas que tiene el mismo identificador de comando que este objeto. Este método no hace nada si ninguna barra de herramientas tiene un control de fecha y hora en que tiene el mismo identificador de comando que este objeto.

Para obtener más información sobre la **personalizar** cuadro de diálogo, vea [CMFCToolBarsCustomizeDialog (clase)](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

##  <a name="onchangeparentwnd"></a>  CMFCToolBarDateTimeCtrl::OnChangeParentWnd

Lo llama el marco cuando el botón se inserta en una nueva barra de herramientas.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[in] La nueva ventana primaria.

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de la clase base ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) volviendo a interno `CMFCToolBarDateTimeCtrlImpl` objeto.

##  <a name="onclick"></a>  CMFCToolBarDateTimeCtrl::OnClick

Lo llama el marco cuando el usuario hace clic en el control.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
[in] Sin usar.

*bDelay*<br/>
[in] Sin usar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el botón procesa el mensaje clic; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de la clase base, [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), devolviendo un valor distinto de cero si interno `CMFCToolBarDateTimeCtrlImpl` objeto es visible.

##  <a name="onctlcolor"></a>  CMFCToolBarDateTimeCtrl::OnCtlColor

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

Un identificador del pincel global que el marco de trabajo que se usa para pintar el fondo del botón.

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de la clase base, [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor), por establecer el texto y en segundo plano los colores del contexto de dispositivo proporcionado al texto global y los colores de fondo, respectivamente.

Para obtener más información acerca de las opciones globales que están disponibles para su aplicación, consulte [AFX_GLOBAL_DATA (estructura)](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onglobalfontschanged"></a>  CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged

Lo llama el marco de trabajo cuando ha cambiado la fuente global.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) cambiando la fuente del control a la de la fuente global.

Para obtener más información acerca de las opciones globales que están disponibles para su aplicación, consulte [AFX_GLOBAL_DATA (estructura)](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onmove"></a>  CMFCToolBarDateTimeCtrl::OnMove

Lo llama el marco de trabajo cuando se mueve la barra de herramientas primario.

```
virtual void OnMove();
```

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de la clase predeterminada ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) mediante la actualización de la posición de interno `CMFCToolBarDateTimeCtrlImpl` objeto.

##  <a name="onshow"></a>  CMFCToolBarDateTimeCtrl::OnShow

Lo llama el marco de trabajo cuando el botón se convierte en visible o invisible.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bShow*<br/>
[in] Especifica si el botón está visible. Si este parámetro es TRUE, el botón está visible. En caso contrario, el botón no está visible.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) al mostrar el botón si *bMostrar* es TRUE. En caso contrario, este método oculta el botón.

##  <a name="onsize"></a>  CMFCToolBarDateTimeCtrl::OnSize

Lo llama el marco de trabajo cuando la barra de herramientas del elemento primario cambia su tamaño o posición y este cambio hace que el botón Cambiar el tamaño.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parámetros

*iSize*<br/>
[in] Nuevo ancho del botón, en píxeles.

### <a name="remarks"></a>Comentarios

Este método invalida la implementación de la clase predeterminada ( [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)) mediante la actualización de tamaño y posición de interno `CMFCToolBarDateTimeCtrlImpl` objeto.

##  <a name="onupdatetooltip"></a>  CMFCToolBarDateTimeCtrl::OnUpdateToolTip

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
[in] La ventana primaria.

*iButtonIndex*<br/>
[in] Índice de base cero del botón en la colección de botones primario.

*wndToolTip*<br/>
[in] El control que muestra el texto de información sobre herramientas.

*str*<br/>
[out] Un `CString` objeto que recibe el texto de información actualizada.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método actualiza el texto de información sobre herramientas; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) mostrando el texto de información sobre herramientas que está asociado con el botón. Si el botón no está acoplado horizontalmente, este método no hace nada y devuelve FALSE.

##  <a name="settime"></a>  CMFCToolBarDateTimeCtrl::SetTime

Establece la fecha y hora en el control de selector de hora.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>Parámetros

*timeNew*<br/>
[in] En la primera versión, una referencia a un [COleDateTime (clase)](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la hora a la que se establecerá el control. En la segunda versión, un puntero a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la hora a la que se establecerá el control.

*pTimeNew*<br/>
[in] Un puntero a la [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) estructura que contiene la hora a la que se establecerá el control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Establece el tiempo en un control de selector de fecha y hora mediante una llamada a [CDateTimeCtrl::SetTime](../../mfc/reference/cdatetimectrl-class.md#settime).

##  <a name="settimeall"></a>  CMFCToolBarDateTimeCtrl::SetTimeAll

Establece la fecha y hora en todas las instancias del control de selector de tiempo que tienen un identificador de comando especificado.

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
[in] Especifica el identificador de comando. de un botón de barra de herramientas

*timeNew*<br/>
[in] En la primera versión, un [COleDateTime (clase)](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la hora a la que se establecerá el control. En la segunda versión, un puntero a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la hora a la que se establecerá el control.

*pTimeNew*<br/>
[in] Un puntero a la [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) estructura que contiene la hora a la que se establecerá el control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Busca un botón de barra de herramientas con el identificador de comando especificado y establece el tiempo en un control de selector de fecha y hora mediante una llamada a [CMFCToolBarDateTimeCtrl::SetTime](#settime).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton (clase)](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)
