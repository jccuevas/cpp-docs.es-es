---
title: Clase CMFCToolBarDateTimeCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e4f7bdc964da8df8d8a402ae70b38eec1dbbf436
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctoolbardatetimectrl-class"></a>Clase CMFCToolBarDateTimeCtrl
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
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|Especifica si un usuario puede ajustar el botón durante la personalización. (Invalida [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|  
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|Copia las propiedades de otro botón de barra de herramientas a la actual. (Invalida [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|  
|`CMFCToolBarDateTimeCtrl::DuplicateData`|Reservado para un uso futuro.|  
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|Copia el texto en el botón de barra de herramientas a un menú.|  
|`CMFCToolBarDateTimeCtrl::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|Recupera el primer `CMFCToolBarDateTimeCtrl` objeto de la aplicación con el identificador de comando especificado.|  
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|Devuelve un puntero para el control de selector de fecha y hora.|  
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|Recupera el identificador de ventana que está asociado con el botón de barra de herramientas. (Invalida [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|  
|`CMFCToolBarDateTimeCtrl::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|Obtiene el tiempo seleccionado de un control de selector de fecha y hora y lo coloca en un determinado [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura.|  
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|Devuelve la hora seleccionada en el botón de control de selector de tiempo que tiene un identificador de comando especificado.|  
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|Determina si un borde del botón se muestra cuando un usuario selecciona el botón. (Invalida [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|  
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|Especifica si el botón procesa el [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) mensaje. (Invalida [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|  
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|Lo llama el marco cuando el botón se agrega a un **personalizar** cuadro de diálogo. (Invalida [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|  
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|Lo llama el marco de trabajo para calcular el tamaño del botón para el contexto de dispositivo especificado y el estado de acoplamiento. (Invalida [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|  
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|Lo llama el marco cuando el botón se inserta en una nueva barra de herramientas. (Invalida [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|  
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|Lo llama el marco cuando el usuario hace clic en el control. (Invalida [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|  
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|Lo llama el marco cuando la barra de herramientas primario controla un `WM_CTLCOLOR` mensaje. (Invalida [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|  
|`CMFCToolBarDateTimeCtrl::OnDraw`|Lo llama el marco de trabajo para dibujar el botón con los estilos especificados y las opciones. (Invalida [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|  
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|Lo llama el marco para dibujar el botón el **comandos** panel de la **personalizar** cuadro de diálogo. (Invalida [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|  
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|Lo llama el marco de trabajo cuando ha cambiado la fuente global. (Invalida [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|  
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|Llamado por el marco de trabajo cuando se mueve la barra de herramientas primario. (Invalida [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|  
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|Lo llama el marco de trabajo cuando el botón se convierte en visible o invisible. (Invalida [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|  
|`CMFCToolBarDateTimeCtrl::OnSize`|Lo llama el marco de trabajo cuando la barra de herramientas primario cambia su tamaño o posición y este cambio hace que el botón Cambiar el tamaño. (Invalida [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|  
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|Llamado por el marco de trabajo cuando la barra de herramientas principal actualiza el texto de información sobre herramientas. (Invalida [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|  
|`CMFCToolBarDateTimeCtrl::Serialize`|Lee este objeto desde un archivo o lo escribe en un archivo (reemplaza a [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|  
|`CMFCToolBarDateTimeCtrl::SetStyle`|Establece el estilo del botón de barra de herramientas. (Invalida [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|  
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|Establece la fecha y hora en el control de selector de tiempo.|  
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|Establece la fecha y hora en todas las instancias del control de selector de tiempo que tienen un identificador de comando especificado.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener un ejemplo de cómo usar un control de selector de fecha y hora, vea el proyecto de ejemplo ToolbarDateTimePicker. Para obtener información acerca de cómo agregar botones de control a las barras de herramientas, consulte [Tutorial: poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtoolbardatetimectrl.h  
  
##  <a name="canbestretched"></a>CMFCToolBarDateTimeCtrl::CanBeStretched  
 Especifica si un usuario puede ajustar el botón durante la personalización.  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Este método devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el marco de trabajo no permite al usuario ajustar un botón de barra de herramientas durante la personalización. Este método extiende la implementación de la clase base ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) al permitir que el usuario ajustar un botón de barra de herramientas de fecha y hora durante la personalización.  
  
##  <a name="cmfctoolbardatetimectrl"></a>CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl  
 Crea e inicializa un [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md) objeto.  
  
```  
CMFCToolBarDateTimeCtrl(
    UINT uiID,  
    int iImage,  
    DWORD dwStyle=0,  
    int iWidth=0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiID`  
 El identificador del control.  
  
 [in] `iImage`  
 El índice de la imagen en la barra de herramientas `CMFCToolBarImages` objeto.  
  
 [in] `dwStyle`  
 El estilo de la `CMFCToolBarDateTimeCtrlImpl` ventana que se crea cuando un usuario hace clic en el botón.  
  
 [in] `iWidth`  
 Ancho del control, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Este objeto se inicializa en la fecha del sistema y la hora. El estilo de ventana de interno `CMFCToolBarDateTimeCtrlImpl` objeto incluye el `dwStyle` parámetro y el `WS_CHILD` y `WS_VISIBLE` estilos. No se puede cambiar estos estilos mediante `CMFCToolBarDateTimeCtrl::SetStyle`. Use `SetStyle` para cambiar el estilo de la `CMFCToolBarDateTimeCtrl` control.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCToolBarDateTimeCtrl` clase. Este fragmento de código forma parte de la [ejemplo de barra de herramientas Date Time Picker](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]  
  
##  <a name="copyfrom"></a>CMFCToolBarDateTimeCtrl::CopyFrom  
 Copia las propiedades de otro botón de barra de herramientas a la actual.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `src`  
 Una referencia al botón de origen desde el que se va a copiar.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para copiar otro botón de barra de herramientas en este botón de barra de herramientas. `src`debe ser del tipo `CMFCToolBarDateTimeCtrl`.  
  
##  <a name="exporttomenubutton"></a>CMFCToolBarDateTimeCtrl::ExportToMenuButton  
 Copia el texto en el botón de barra de herramientas a un menú.  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `menuButton`  
 Una referencia al botón de menú de destino.  
  
### <a name="return-value"></a>Valor devuelto  
 Este método devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método invalida la implementación de la clase base ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) al cargar el recurso de cadena que está asociado con el identificador de comando del control. Para obtener más información acerca de los recursos de cadena, vea [CStringT::LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring).  
  
##  <a name="getbycmd"></a>CMFCToolBarDateTimeCtrl::GetByCmd  
 Recupera el primer `CMFCToolBarDateTimeCtrl` objeto de la aplicación con el identificador de comando especificado.  
  
```  
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 El identificador de comando del botón para recuperar.  
  
### <a name="return-value"></a>Valor devuelto  
 La primera `CMFCToolBarDateTimeCtrl` objeto de la aplicación que tiene el identificador de comando especificado, o `NULL` si no hay ningún `CMFCToolBarDateTimeCtrl` objetos tienen el identificador del comando especificado.  
  
### <a name="remarks"></a>Comentarios  
 Este método de utilidad compartida se utiliza por métodos como [CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall) y [CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall) establecer u obtener la fecha y hora de todas las instancias de la hora control de selector que tienen un identificador de comando especificado.  
  
##  <a name="getdatetimectrl"></a>CMFCToolBarDateTimeCtrl::GetDateTimeCtrl  
 Devuelve un puntero para el control de selector de fecha y hora.  
  
```  
CDateTimeCtrl* GetDateTimeCtrl() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al control de selector de fecha y hora; o `NULL` si el control no existe.  
  
### <a name="remarks"></a>Comentarios  
 El `CMFCToolBarDateTimeCtrl` clase inicializa el `m_pWndDateTime` miembro de datos al insertar un `CMFCToolBarDateTimeCtrl` objeto en una barra de herramientas.  
  
##  <a name="gethwnd"></a>CMFCToolBarDateTimeCtrl::GetHwnd  
 Recupera el identificador de ventana que está asociado con el botón de barra de herramientas.  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de ventana que está asociado con el botón de barra de herramientas de fecha y hora.  
  
### <a name="remarks"></a>Comentarios  
 Este método invalida el [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) método.  
  
##  <a name="gettime"></a>CMFCToolBarDateTimeCtrl::GetTime  
 Obtiene la hora seleccionada de la fecha asociado y el control de selector de tiempo y lo coloca en un determinado [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura  
  
```  
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `[out] timeDest`  
 En la primera sobrecarga, un [clase COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que va a recibir la información de hora del sistema. En la segunda sobrecarga, un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que va a recibir la información de hora del sistema.  
  
 `[out] pTimeDest`  
 Un puntero a la [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura para recibir la información de hora del sistema. No debe ser `NULL`.  
  
### <a name="return-value"></a>Valor devuelto  
 En la primera sobrecarga, distinto de cero si la hora se escribe correctamente en el [clase COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto; de lo contrario devuelve 0. En las sobrecargas de segunda y terceros, el valor devuelto es un `DWORD` que es igual que el miembro dwFlag que estableció en el [NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730) estructura.  
  
### <a name="remarks"></a>Comentarios  
 El método establece la [NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730) dwFlags de miembro para indicar si el selector de fecha y hora se establece en una fecha y hora de la estructura. Si el valor es igual a GDT_NONE, el control se establece en `no date` estado y utiliza el estilo DTS_SHOWNONE. Si el valor devuelto es igual a GDT_VALID, la hora del sistema se almacena correctamente en la ubicación de destino.  
  
##  <a name="gettimeall"></a>CMFCToolBarDateTimeCtrl::GetTimeAll  
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
 `[in] uiCmd`  
 Especifica el identificador del comando. del botón de barra de herramientas  
  
 `[out] timeDest`  
 En la primera sobrecarga, un [clase COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que va a recibir la información de hora del sistema. En la segunda sobrecarga, un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que va a recibir la información de hora del sistema.  
  
 `[out] pTimeDest`  
 Un puntero a la [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura para recibir la información de hora del sistema. No debe ser `NULL`.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el marco de trabajo no puede encontrar un botón de barra de herramientas que coincida con el identificador de comando `uiCmd`, el valor devuelto es cero en la primera sobrecarga y GDT_NONE en las otras sobrecargas. Si se encuentra el botón de barra de herramientas, el valor devuelto es el mismo que el valor devuelto de una llamada a [CMFCToolBarDateTimeCtrl::GetTime](#gettime) en ese botón. A devolver el valor de cero o GDT_NONE puede producirse cuando se encuentra el botón, lo que indica que la llamada a `GetTime` no devolvió una fecha válida por algún otro motivo.  
  
### <a name="remarks"></a>Comentarios  
 Este método busca un botón de barra de herramientas que tiene el identificador de comando especificado y llama [CMFCToolBarDateTimeCtrl::GetTime](#gettime) método en ese botón.  
  
##  <a name="havehotborder"></a>CMFCToolBarDateTimeCtrl::HaveHotBorder  
 Determina si un borde del botón se muestra cuando un usuario selecciona el botón.  
  
```  
virtual BOOL HaveHotBorder() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si un botón muestra su borde cuando selecciona; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve un valor distinto de cero si el control es visible.  
  
##  <a name="notifycommand"></a>CMFCToolBarDateTimeCtrl::NotifyCommand  
 Especifica si el botón procesa el [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) mensaje.  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iNotifyCode`  
 El mensaje de notificación que está asociado con el comando.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el botón se procesa la `WM_COMMAND` mensaje, o `FALSE` para indicar que el mensaje debe controlarse con la barra de herramientas primario.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando está a punto de enviar un [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) mensaje a la ventana primaria.  
  
 Este método extiende la implementación de la clase base ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) mediante el procesamiento de la [DTN_DATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761737) notificación. Actualiza el estado de tiempo interno y actualiza la propiedad de tiempo de todos los `CMFCToolBarDateTimeCtrl` objetos con el mismo identificador de comando.  
  
##  <a name="onaddtocustomizepage"></a>CMFCToolBarDateTimeCtrl::OnAddToCustomizePage  
 Lo llama el marco cuando el botón se agrega a un **personalizar** cuadro de diálogo.  
  
```  
virtual void OnAddToCustomizePage();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método extiende la implementación de la clase base, [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage), por copiar las propiedades de la primera fecha y la hora de control en cualquier barra de herramientas que tiene el mismo identificador de comando como este objeto. Este método no hace nada si ninguna barra de herramientas tiene un control de fecha y hora en que tiene el mismo identificador de comando como este objeto.  
  
 Para obtener más información sobre la **personalizar** cuadro de diálogo, vea [CMFCToolBarsCustomizeDialog clase](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).  
  
##  <a name="onchangeparentwnd"></a>CMFCToolBarDateTimeCtrl::OnChangeParentWnd  
 Lo llama el marco cuando el botón se inserta en una nueva barra de herramientas.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndParent`  
 La nueva ventana primaria.  
  
### <a name="remarks"></a>Comentarios  
 Este método invalida la implementación de la clase base ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) al volver a crear interno `CMFCToolBarDateTimeCtrlImpl` objeto.  
  
##  <a name="onclick"></a>CMFCToolBarDateTimeCtrl::OnClick  
 Lo llama el marco cuando el usuario hace clic en el control.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Sin usar.  
  
 [in] `bDelay`  
 Sin usar.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el botón procesa el mensaje haga clic en; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método invalida la implementación de la clase base, [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), devolviendo un valor distinto de cero si el fax interno `CMFCToolBarDateTimeCtrlImpl` objeto está visible.  
  
##  <a name="onctlcolor"></a>CMFCToolBarDateTimeCtrl::OnCtlColor  
 Lo llama el marco cuando la barra de herramientas primario controla un `WM_CTLCOLOR` mensaje.  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 El contexto de dispositivo que muestra el botón.  
  
 [in] `nCtlColor`  
 Sin usar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el pincel global que el marco de trabajo que se usa para pintar el fondo del botón.  
  
### <a name="remarks"></a>Comentarios  
 Este método invalida la implementación de la clase base, [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor), por establecimiento del texto y fondo colores del contexto de dispositivo proporcionado en el texto global y colores de fondo, respectivamente.  
  
 Para obtener más información acerca de las opciones globales que están disponibles para su aplicación, consulte [AFX_GLOBAL_DATA (estructura)](../../mfc/reference/afx-global-data-structure.md).  
  
##  <a name="onglobalfontschanged"></a>CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged  
 Lo llama el marco de trabajo cuando ha cambiado la fuente global.  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)), cambie la fuente del control para que la fuente global.  
  
 Para obtener más información acerca de las opciones globales que están disponibles para su aplicación, consulte [AFX_GLOBAL_DATA (estructura)](../../mfc/reference/afx-global-data-structure.md).  
  
##  <a name="onmove"></a>CMFCToolBarDateTimeCtrl::OnMove  
 Llamado por el marco de trabajo cuando se mueve la barra de herramientas primario.  
  
```  
virtual void OnMove();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método invalida la implementación de la clase predeterminada ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) mediante la actualización de la posición de los internos `CMFCToolBarDateTimeCtrlImpl` objeto.  
  
##  <a name="onshow"></a>CMFCToolBarDateTimeCtrl::OnShow  
 Lo llama el marco de trabajo cuando el botón se convierte en visible o invisible.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bShow`  
 Especifica si el botón está visible. Si este parámetro es `TRUE`, el botón está visible. En caso contrario, el botón no está visible.  
  
### <a name="remarks"></a>Comentarios  
 Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) que muestre el botón si `bShow` es `TRUE`. En caso contrario, este método oculta el botón.  
  
##  <a name="onsize"></a>CMFCToolBarDateTimeCtrl::OnSize  
 Lo llama el marco de trabajo cuando la barra de herramientas primario cambia su tamaño o posición y este cambio hace que el botón Cambiar el tamaño.  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iSize`  
 El nuevo ancho del botón, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Este método invalida la implementación de la clase predeterminada ( [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)) al actualizar el tamaño y la posición de interno `CMFCToolBarDateTimeCtrlImpl` objeto.  
  
##  <a name="onupdatetooltip"></a>CMFCToolBarDateTimeCtrl::OnUpdateToolTip  
 Llamado por el marco de trabajo cuando la barra de herramientas principal actualiza el texto de información sobre herramientas.  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndParent`  
 La ventana primaria.  
  
 [in] `iButtonIndex`  
 Índice de base cero del botón en la colección de botón primario.  
  
 [in] `wndToolTip`  
 El control que muestra el texto de información sobre herramientas.  
  
 [out] `str`  
 Un `CString` objeto que recibe el texto actualizado.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el método actualiza el texto de información sobre herramientas; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método extiende la implementación de la clase base ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) al mostrar el texto de información sobre herramientas que está asociado con el botón. Si el botón no está acoplado horizontalmente, este método no hace nada y devuelve `FALSE`.  
  
##  <a name="settime"></a>CMFCToolBarDateTimeCtrl::SetTime  
 Establece la fecha y hora en el control de selector de tiempo.  
  
```  
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `[in] timeNew`  
 En la primera versión, una referencia a un [clase COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la hora a la que se establecerá el control. En la segunda versión, un puntero a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la hora a la que se establecerá el control.  
  
 `[in] pTimeNew`  
 Un puntero a la [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la hora a la que se establecerá el control.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Establece el tiempo en un control de selector de fecha y hora mediante una llamada a [CDateTimeCtrl::SetTime](../../mfc/reference/cdatetimectrl-class.md#settime).  
  
##  <a name="settimeall"></a>CMFCToolBarDateTimeCtrl::SetTimeAll  
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
 `[in] uiCmd`  
 Especifica el identificador del comando. del botón de barra de herramientas  
  
 `[in] timeNew`  
 En la primera versión, un [clase COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la hora a la que se establecerá el control. En la segunda versión, un puntero a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la hora a la que se establecerá el control.  
  
 `[in] pTimeNew`  
 Un puntero a la [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la hora a la que se establecerá el control.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Busca un botón de barra de herramientas con el identificador de comando especificado y establece el tiempo en un control de selector de fecha y hora mediante una llamada a [CMFCToolBarDateTimeCtrl::SetTime](#settime).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)



