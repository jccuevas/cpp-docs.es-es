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
ms.openlocfilehash: 9aebd55f19a6687554d8d8378ef84ed5932025a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372175"
---
# <a name="cmfctoolbardatetimectrl-class"></a>CMFCToolBarDateTimeCtrl (clase)

Un botón de barra de herramientas que contiene un control de selector de fecha y hora.

## <a name="syntax"></a>Sintaxis

```
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|Construye un objeto `CMFCToolBarDateTimeCtrl`.|
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CanBestretched](#canbestretched)|Especifica si un usuario puede estirar el botón durante la personalización. (Reemplaza [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|Copia las propiedades de otro botón de la barra de herramientas en el botón actual. (Reemplaza [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarDateTimeCtrl::DuplicateData`|Reservado para uso futuro.|
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|Copia texto del botón de la barra de herramientas en un menú.|
|`CMFCToolBarDateTimeCtrl::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|Recupera el `CMFCToolBarDateTimeCtrl` primer objeto de la aplicación que tiene el identificador de comando especificado.|
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|Devuelve un puntero al control selector de fecha y hora.|
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|Recupera el identificador de ventana asociado al botón de barra de herramientas. (Reemplaza [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|`CMFCToolBarDateTimeCtrl::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|Obtiene la hora seleccionada de un control selector de fecha y hora y lo coloca en una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) especificada.|
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|Devuelve la hora seleccionada del botón de control del selector de tiempo que tiene un identificador de comando especificado.|
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|Determina si se muestra un borde del botón cuando un usuario selecciona el botón. (Reemplaza [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|Especifica si el botón procesa el [mensaje de WM_COMMAND.](/windows/win32/menurc/wm-command) (Reemplaza [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|Llamado por el marco de trabajo cuando el botón se agrega a un **personalizar** cuadro de diálogo. (Reemplaza [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|Llamado por el marco de trabajo para calcular el tamaño del botón para el contexto de dispositivo especificado y el estado de acoplamiento. (Reemplaza [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|Llamado por el marco de trabajo cuando el botón se inserta en una nueva barra de herramientas. (Reemplaza [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|Llamado por el marco de trabajo cuando el usuario hace clic en el control. (Reemplaza [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|Llamado por el marco de trabajo cuando la barra de herramientas primaria controla un mensaje de WM_CTLCOLOR. (Reemplaza [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarDateTimeCtrl::OnDraw`|Llamado por el marco de trabajo para dibujar el botón mediante el uso de los estilos y opciones especificados. (Reemplaza [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|Llamado por el marco de trabajo para dibujar el botón en el **comandos** panel de la **personalizar** cuadro de diálogo. (Reemplaza [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|Llamado por el marco de trabajo cuando la fuente global ha cambiado. (Reemplaza [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|Llamado por el marco de trabajo cuando se mueve la barra de herramientas principal. (Reemplaza [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|Llamado por el marco de trabajo cuando el botón se vuelve visible o invisible. (Reemplaza [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|`CMFCToolBarDateTimeCtrl::OnSize`|Llamado por el marco de trabajo cuando la barra de herramientas primaria cambia su tamaño o posición y este cambio hace que el botón cambie de tamaño. (Reemplaza [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|Llamado por el marco de trabajo cuando la barra de herramientas primaria actualiza su texto de información sobre herramientas. (Reemplaza [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarDateTimeCtrl::Serialize`|Lee este objeto de un archivo o lo escribe en un archivo (Reemplaza [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|`CMFCToolBarDateTimeCtrl::SetStyle`|Establece el estilo del botón de la barra de herramientas. (Reemplaza [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|Establece la hora y la fecha en el control de selector de hora.|
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|Establece la hora y la fecha en todas las instancias del control de selector de tiempo que tienen un identificador de comando especificado.|

## <a name="remarks"></a>Observaciones

Para obtener un ejemplo de cómo usar un control de selector de fecha y hora, vea el proyecto de ejemplo ToolbarDateTimePicker. Para obtener información sobre cómo agregar botones de control a las barras de herramientas, vea [Tutorial: Colocar controles en barras](../../mfc/walkthrough-putting-controls-on-toolbars.md)de herramientas .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtoolbardatetimectrl.h

## <a name="cmfctoolbardatetimectrlcanbestretched"></a><a name="canbestretched"></a>CMFCToolBarDateTimeCtrl::CanBestretched

Especifica si un usuario puede estirar el botón durante la personalización.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Valor devuelto

Este método devuelve TRUE.

### <a name="remarks"></a>Observaciones

De forma predeterminada, el marco de trabajo no permite al usuario estirar un botón de barra de herramientas durante la personalización. Este método extiende la implementación de la clase base ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) al permitir al usuario estirar un botón de barra de herramientas de fecha y hora durante la personalización.

## <a name="cmfctoolbardatetimectrlcmfctoolbardatetimectrl"></a><a name="cmfctoolbardatetimectrl"></a>CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl

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
[en] El identificador de control.

*iImage*<br/>
[en] El índice de la imagen `CMFCToolBarImages` en el objeto de la barra de herramientas.

*dwStyle*<br/>
[en] El estilo `CMFCToolBarDateTimeCtrlImpl` de la ventana que se crea cuando un usuario hace clic en el botón.

*iWidth*<br/>
[en] El ancho del control, en píxeles.

### <a name="remarks"></a>Observaciones

Este objeto se inicializa en la fecha y hora del sistema. El estilo de `CMFCToolBarDateTimeCtrlImpl` ventana del objeto interno incluye el parámetro *dwStyle* y los estilos WS_CHILD y WS_VISIBLE. No puede cambiar estos `CMFCToolBarDateTimeCtrl::SetStyle`estilos mediante . Se `SetStyle` utiliza para cambiar `CMFCToolBarDateTimeCtrl` el estilo del control.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCToolBarDateTimeCtrl` cómo construir un objeto de la clase. Este fragmento de código forma parte del ejemplo Selector de fecha y hora de la barra [de herramientas.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]

## <a name="cmfctoolbardatetimectrlcopyfrom"></a><a name="copyfrom"></a>CMFCToolBarDateTimeCtrl::CopyFrom

Copia las propiedades de otro botón de la barra de herramientas en el botón actual.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
[en] Una referencia al botón de origen desde el que se copia.

### <a name="remarks"></a>Observaciones

Llame a este método para copiar otro botón de la barra de herramientas en este botón de la barra de herramientas. *src* debe ser `CMFCToolBarDateTimeCtrl`de tipo .

## <a name="cmfctoolbardatetimectrlexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCToolBarDateTimeCtrl::ExportToMenuButton

Copia texto del botón de la barra de herramientas en un menú.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parámetros

*menuButton*<br/>
[en] Una referencia al botón de menú de destino.

### <a name="return-value"></a>Valor devuelto

Este método devuelve TRUE.

### <a name="remarks"></a>Observaciones

Este método reemplaza la implementación de la clase base ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) cargando el recurso de cadena que está asociado con el identificador de comando del control. Para obtener más información acerca de los recursos de cadena, vea [CStringT::LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring).

## <a name="cmfctoolbardatetimectrlgetbycmd"></a><a name="getbycmd"></a>CMFCToolBarDateTimeCtrl::GetByCmd

Recupera el `CMFCToolBarDateTimeCtrl` primer objeto de la aplicación que tiene el identificador de comando especificado.

```
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[en] El identificador de comando del botón que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

El `CMFCToolBarDateTimeCtrl` primer objeto de la aplicación que tiene el `CMFCToolBarDateTimeCtrl` identificador de comando especificado, o NULL si ningún objeto tiene el identificador de comando especificado.

### <a name="remarks"></a>Observaciones

Este método de utilidad compartida lo utilizan métodos como [CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall) y [CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall) para establecer u obtener la hora y la fecha de todas las instancias del control de selector de hora que tienen un identificador de comando especificado.

## <a name="cmfctoolbardatetimectrlgetdatetimectrl"></a><a name="getdatetimectrl"></a>CMFCToolBarDateTimeCtrl::GetDateTimeCtrl

Devuelve un puntero al control selector de fecha y hora.

```
CDateTimeCtrl* GetDateTimeCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al control selector de fecha y hora; o NULL si el control no existe.

### <a name="remarks"></a>Observaciones

La `CMFCToolBarDateTimeCtrl` clase inicializa `m_pWndDateTime` el miembro de `CMFCToolBarDateTimeCtrl` datos cuando se inserta un objeto en una barra de herramientas.

## <a name="cmfctoolbardatetimectrlgethwnd"></a><a name="gethwnd"></a>CMFCToolBarDateTimeCtrl::GetHwnd

Recupera el identificador de ventana asociado al botón de barra de herramientas.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Valor devuelto

El identificador de ventana asociado al botón de barra de herramientas de fecha y hora.

### <a name="remarks"></a>Observaciones

Este método reemplaza el [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) método.

## <a name="cmfctoolbardatetimectrlgettime"></a><a name="gettime"></a>CMFCToolBarDateTimeCtrl::GetTime

Obtiene la hora seleccionada del control de selector de fecha y hora asociado y lo coloca en una estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) especificada

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Parámetros

*timeDest*<br/>
[fuera] En la primera sobrecarga, un [COleDateTime clase](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que recibirá la información de hora del sistema. En la segunda sobrecarga, un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que recibirá la información de tiempo del sistema.

*pTimeDest*<br/>
[fuera] Puntero a la estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) para recibir la información de hora del sistema. No debe ser NULL.

### <a name="return-value"></a>Valor devuelto

En la primera sobrecarga, distinto de cero si la hora se escribe correctamente en el [COleDateTime clase](../../atl-mfc-shared/reference/coledatetime-class.md) objeto; de lo contrario 0. En la segunda y tercera sobrecarga, el valor devuelto es un DWORD que es igual al miembro dwFlag que se estableció en la estructura [NMDATETIMECHANGE.](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)

### <a name="remarks"></a>Observaciones

El método establece el miembro de estructura [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) dwFlags para indicar si el selector de fecha y hora se establece en una fecha y hora. Si el valor es igual a `no date` GDT_NONE, el control se establece en status y utiliza el estilo DTS_SHOWNONE. Si el valor devuelto es igual a GDT_VALID, la hora del sistema se almacena correctamente en la ubicación de destino.

## <a name="cmfctoolbardatetimectrlgettimeall"></a><a name="gettimeall"></a>CMFCToolBarDateTimeCtrl::GetTimeAll

Devuelve el tiempo seleccionado por el usuario desde el botón de control del selector de tiempo que tiene un identificador de comando especificado.

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
[en] Especifica el identificador de comando de un botón de barra de herramientas.

*timeDest*<br/>
[fuera] En la primera sobrecarga, un [COleDateTime clase](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que recibirá la información de hora del sistema. En la segunda sobrecarga, un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que recibirá la información de tiempo del sistema.

*pTimeDest*<br/>
[fuera] Puntero a la estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) para recibir la información de hora del sistema. No debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Si el marco de trabajo no puede encontrar un botón de barra de herramientas que coincida con el identificador de comando *uiCmd*, el valor devuelto es cero en la primera sobrecarga y GDT_NONE en las otras sobrecargas. Si se encuentra el botón de barra de herramientas, el valor devuelto es el mismo que el valor devuelto de una llamada a [CMFCToolBarDateTimeCtrl::GetTime](#gettime) en ese botón. Un valor devuelto de cero o GDT_NONE puede producirse cuando se `GetTime` encuentra el botón, lo que indica que la llamada a no devolvió una fecha válida por algún otro motivo.

### <a name="remarks"></a>Observaciones

Este método busca un botón de barra de herramientas que tiene el identificador de comando especificado y llama [a CMFCToolBarDateTimeCtrl::GetTime](#gettime) método en ese botón.

## <a name="cmfctoolbardatetimectrlhavehotborder"></a><a name="havehotborder"></a>CMFCToolBarDateTimeCtrl::HaveHotBorder

Determina si se muestra un borde del botón cuando un usuario selecciona el botón.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si un botón muestra su borde cuando está seleccionado; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Este método devuelve un valor distinto de cero si el control está visible.

## <a name="cmfctoolbardatetimectrlnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarDateTimeCtrl::NotifyCommand

Especifica si el botón procesa el [mensaje de WM_COMMAND.](/windows/win32/menurc/wm-command)

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parámetros

*iNotifyCode*<br/>
[en] El mensaje de notificación asociado al comando.

### <a name="return-value"></a>Valor devuelto

TRUESi el botón procesa el WM_COMMAND mensaje o FALSE para indicar que la barra de herramientas primaria debe controlar el mensaje.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método cuando está a punto de enviar un [mensaje de WM_COMMAND](/windows/win32/menurc/wm-command) a la ventana primaria.

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) procesando la notificación [DTN_DATETIMECHANGE.](/windows/win32/Controls/dtn-datetimechange) Actualiza el estado de hora interno y `CMFCToolBarDateTimeCtrl` actualiza la propiedad time de todos los objetos con el mismo identificador de comando.

## <a name="cmfctoolbardatetimectrlonaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolBarDateTimeCtrl::OnAddToCustomizePage

Llamado por el marco de trabajo cuando el botón se agrega a un **personalizar** cuadro de diálogo.

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Observaciones

Este método extiende la implementación de la clase base, [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage), copiando las propiedades del primer control de fecha y hora en cualquier barra de herramientas que tenga el mismo identificador de comando que este objeto. Este método no hace nada si ninguna barra de herramientas tiene un control de fecha y hora que tiene el mismo identificador de comando que este objeto.

Para obtener más información sobre el cuadro de diálogo **Personalizar,** vea [CMFCToolBarsCustomizeDialog (Clase)](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

## <a name="cmfctoolbardatetimectrlonchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarDateTimeCtrl::OnChangeParentWnd

Llamado por el marco de trabajo cuando el botón se inserta en una nueva barra de herramientas.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[en] La nueva ventana primaria.

### <a name="remarks"></a>Observaciones

Este método reemplaza la implementación de la clase base ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) volviendo a crear el objeto interno. `CMFCToolBarDateTimeCtrlImpl`

## <a name="cmfctoolbardatetimectrlonclick"></a><a name="onclick"></a>CMFCToolBarDateTimeCtrl::OnClick

Llamado por el marco de trabajo cuando el usuario hace clic en el control.

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

Este método reemplaza la implementación de la clase base, [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), devolviendo un valor distinto de cero si el objeto interno `CMFCToolBarDateTimeCtrlImpl` está visible.

## <a name="cmfctoolbardatetimectrlonctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarDateTimeCtrl::OnCtlColor

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

Identificador del pincel global que el marco de trabajo utiliza para pintar el fondo del botón.

### <a name="remarks"></a>Observaciones

Este método reemplaza la implementación de la clase base, [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor), estableciendo el texto y los colores de fondo del contexto de dispositivo proporcionado en el texto global y los colores de fondo, respectivamente.

Para obtener más información acerca de las opciones globales que están disponibles para la aplicación, vea [AFX_GLOBAL_DATA estructura](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbardatetimectrlonglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged

Llamado por el marco de trabajo cuando la fuente global ha cambiado.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Observaciones

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) cambiando la fuente del control a la de la fuente global.

Para obtener más información acerca de las opciones globales que están disponibles para la aplicación, vea [AFX_GLOBAL_DATA estructura](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbardatetimectrlonmove"></a><a name="onmove"></a>CMFCToolBarDateTimeCtrl::OnMove

Llamado por el marco de trabajo cuando se mueve la barra de herramientas principal.

```
virtual void OnMove();
```

### <a name="remarks"></a>Observaciones

Este método reemplaza la implementación de clase predeterminada ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) actualizando la posición del objeto interno. `CMFCToolBarDateTimeCtrlImpl`

## <a name="cmfctoolbardatetimectrlonshow"></a><a name="onshow"></a>CMFCToolBarDateTimeCtrl::OnShow

Llamado por el marco de trabajo cuando el botón se vuelve visible o invisible.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bMostrar*<br/>
[en] Especifica si el botón está visible. Si este parámetro es TRUE, el botón es visible. De lo contrario, el botón no está visible.

### <a name="remarks"></a>Observaciones

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) mostrando el botón si *bShow* es TRUE. De lo contrario, este método oculta el botón.

## <a name="cmfctoolbardatetimectrlonsize"></a><a name="onsize"></a>CMFCToolBarDateTimeCtrl::OnSize

Llamado por el marco de trabajo cuando la barra de herramientas primaria cambia su tamaño o posición y este cambio hace que el botón cambie de tamaño.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parámetros

*iSize*<br/>
[en] El nuevo ancho del botón, en píxeles.

### <a name="remarks"></a>Observaciones

Este método reemplaza la implementación de clase predeterminada ( [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)) actualizando el tamaño y la posición del objeto interno. `CMFCToolBarDateTimeCtrlImpl`

## <a name="cmfctoolbardatetimectrlonupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolBarDateTimeCtrl::OnUpdateToolTip

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
[en] La ventana principal.

*iButtonIndex*<br/>
[en] El índice de base cero del botón de la colección de botones primarios.

*wndToolTip*<br/>
[en] El control que muestra el texto de información sobre herramientas.

*Str*<br/>
[fuera] Objeto `CString` que recibe el texto de información sobre herramientas actualizado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método actualiza el texto de información sobre herramientas; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) mostrando el texto de información sobre herramientas que está asociado con el botón. Si el botón no está acoplado horizontalmente, este método no hace nada y devuelve FALSE.

## <a name="cmfctoolbardatetimectrlsettime"></a><a name="settime"></a>CMFCToolBarDateTimeCtrl::SetTime

Establece la hora y la fecha en el control de selector de hora.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>Parámetros

*timeNew*<br/>
[en] En la primera versión, una referencia a un [COleDateTime clase](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la hora a la que se establecerá el control. En la segunda versión, un puntero a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la hora a la que se establecerá el control.

*pTimeNew*<br/>
[en] Puntero a la estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que contiene la hora a la que se establecerá el control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Establece la hora en un control selector de fecha y hora llamando a [CDateTimeCtrl::SetTime](../../mfc/reference/cdatetimectrl-class.md#settime).

## <a name="cmfctoolbardatetimectrlsettimeall"></a><a name="settimeall"></a>CMFCToolBarDateTimeCtrl::SetTimeAll

Establece la hora y la fecha en todas las instancias del control de selector de tiempo que tienen un identificador de comando especificado.

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
[en] Especifica el identificador de comando de un botón de barra de herramientas.

*timeNew*<br/>
[en] En la primera versión, un [COleDateTime clase](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la hora a la que se establecerá el control. En la segunda versión, un puntero a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la hora a la que se establecerá el control.

*pTimeNew*<br/>
[en] Puntero a la estructura [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) que contiene la hora a la que se establecerá el control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Busca un botón de barra de herramientas con el identificador de comando especificado y establece la hora en un control de selector de fecha y hora llamando a [CMFCToolBarDateTimeCtrl::SetTime](#settime).

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton (clase)](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)
