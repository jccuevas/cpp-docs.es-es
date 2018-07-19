---
title: CFrameWnd (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFrameWnd
- AFXWIN/CFrameWnd
- AFXWIN/CFrameWnd::CFrameWnd
- AFXWIN/CFrameWnd::ActivateFrame
- AFXWIN/CFrameWnd::BeginModalState
- AFXWIN/CFrameWnd::Create
- AFXWIN/CFrameWnd::CreateView
- AFXWIN/CFrameWnd::DockControlBar
- AFXWIN/CFrameWnd::EnableDocking
- AFXWIN/CFrameWnd::EndModalState
- AFXWIN/CFrameWnd::FloatControlBar
- AFXWIN/CFrameWnd::GetActiveDocument
- AFXWIN/CFrameWnd::GetActiveFrame
- AFXWIN/CFrameWnd::GetActiveView
- AFXWIN/CFrameWnd::GetControlBar
- AFXWIN/CFrameWnd::GetDockState
- AFXWIN/CFrameWnd::GetMenuBarState
- AFXWIN/CFrameWnd::GetMenuBarVisibility
- AFXWIN/CFrameWnd::GetMessageBar
- AFXWIN/CFrameWnd::GetMessageString
- AFXWIN/CFrameWnd::GetTitle
- AFXWIN/CFrameWnd::InitialUpdateFrame
- AFXWIN/CFrameWnd::InModalState
- AFXWIN/CFrameWnd::IsTracking
- AFXWIN/CFrameWnd::LoadAccelTable
- AFXWIN/CFrameWnd::LoadBarState
- AFXWIN/CFrameWnd::LoadFrame
- AFXWIN/CFrameWnd::NegotiateBorderSpace
- AFXWIN/CFrameWnd::OnBarCheck
- AFXWIN/CFrameWnd::OnContextHelp
- AFXWIN/CFrameWnd::OnSetPreviewMode
- AFXWIN/CFrameWnd::OnUpdateControlBarMenu
- AFXWIN/CFrameWnd::RecalcLayout
- AFXWIN/CFrameWnd::SaveBarState
- AFXWIN/CFrameWnd::SetActivePreviewView
- AFXWIN/CFrameWnd::SetActiveView
- AFXWIN/CFrameWnd::SetDockState
- AFXWIN/CFrameWnd::SetMenuBarState
- AFXWIN/CFrameWnd::SetMenuBarVisibility
- AFXWIN/CFrameWnd::SetMessageText
- AFXWIN/CFrameWnd::SetProgressBarPosition
- AFXWIN/CFrameWnd::SetProgressBarRange
- AFXWIN/CFrameWnd::SetProgressBarState
- AFXWIN/CFrameWnd::SetTaskbarOverlayIcon
- AFXWIN/CFrameWnd::SetTitle
- AFXWIN/CFrameWnd::ShowControlBar
- AFXWIN/CFrameWnd::ShowOwnedWindows
- AFXWIN/CFrameWnd::OnCreateClient
- AFXWIN/CFrameWnd::OnHideMenuBar
- AFXWIN/CFrameWnd::OnShowMenuBar
- AFXWIN/CFrameWnd::m_bAutoMenuEnable
- AFXWIN/CFrameWnd::rectDefault
dev_langs:
- C++
helpviewer_keywords:
- CFrameWnd [MFC], CFrameWnd
- CFrameWnd [MFC], ActivateFrame
- CFrameWnd [MFC], BeginModalState
- CFrameWnd [MFC], Create
- CFrameWnd [MFC], CreateView
- CFrameWnd [MFC], DockControlBar
- CFrameWnd [MFC], EnableDocking
- CFrameWnd [MFC], EndModalState
- CFrameWnd [MFC], FloatControlBar
- CFrameWnd [MFC], GetActiveDocument
- CFrameWnd [MFC], GetActiveFrame
- CFrameWnd [MFC], GetActiveView
- CFrameWnd [MFC], GetControlBar
- CFrameWnd [MFC], GetDockState
- CFrameWnd [MFC], GetMenuBarState
- CFrameWnd [MFC], GetMenuBarVisibility
- CFrameWnd [MFC], GetMessageBar
- CFrameWnd [MFC], GetMessageString
- CFrameWnd [MFC], GetTitle
- CFrameWnd [MFC], InitialUpdateFrame
- CFrameWnd [MFC], InModalState
- CFrameWnd [MFC], IsTracking
- CFrameWnd [MFC], LoadAccelTable
- CFrameWnd [MFC], LoadBarState
- CFrameWnd [MFC], LoadFrame
- CFrameWnd [MFC], NegotiateBorderSpace
- CFrameWnd [MFC], OnBarCheck
- CFrameWnd [MFC], OnContextHelp
- CFrameWnd [MFC], OnSetPreviewMode
- CFrameWnd [MFC], OnUpdateControlBarMenu
- CFrameWnd [MFC], RecalcLayout
- CFrameWnd [MFC], SaveBarState
- CFrameWnd [MFC], SetActivePreviewView
- CFrameWnd [MFC], SetActiveView
- CFrameWnd [MFC], SetDockState
- CFrameWnd [MFC], SetMenuBarState
- CFrameWnd [MFC], SetMenuBarVisibility
- CFrameWnd [MFC], SetMessageText
- CFrameWnd [MFC], SetProgressBarPosition
- CFrameWnd [MFC], SetProgressBarRange
- CFrameWnd [MFC], SetProgressBarState
- CFrameWnd [MFC], SetTaskbarOverlayIcon
- CFrameWnd [MFC], SetTitle
- CFrameWnd [MFC], ShowControlBar
- CFrameWnd [MFC], ShowOwnedWindows
- CFrameWnd [MFC], OnCreateClient
- CFrameWnd [MFC], OnHideMenuBar
- CFrameWnd [MFC], OnShowMenuBar
- CFrameWnd [MFC], m_bAutoMenuEnable
- CFrameWnd [MFC], rectDefault
ms.assetid: e2220aba-5bf4-4002-b960-fbcafcad01f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d2dee6c5157858fef2bd26101ac128ff3d53d23
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337387"
---
# <a name="cframewnd-class"></a>CFrameWnd (clase)
Proporciona la funcionalidad de una ventana de marco de interfaz de un único documento (SDI) de Windows superpuesta o emergente, junto con los miembros para administrar la ventana.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CFrameWnd : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFrameWnd::CFrameWnd](#cframewnd)|Construye un objeto `CFrameWnd`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFrameWnd::ActivateFrame](#activateframe)|Hace que el marco visibles y están disponibles para el usuario.|  
|[CFrameWnd::BeginModalState](#beginmodalstate)|Establece la ventana de marco en modal.|  
|[CFrameWnd::Create](#create)|Llamada a crear e inicializar la ventana de marco de Windows asociada con el `CFrameWnd` objeto.|  
|[CFrameWnd::CreateView](#createview)|Crea una vista dentro de un marco que no se deriva `CView`.|  
|[CFrameWnd:: DockControlBar](#dockcontrolbar)|Una barra de control se acopla.|  
|[CFrameWnd:: EnableDocking](#enabledocking)|Permite que una barra de control quede acoplado.|  
|[CFrameWnd::EndModalState](#endmodalstate)|Finaliza el estado de la ventana de marco modal. Habilita todas las ventanas deshabilitadas de forma `BeginModalState`.|  
|[CFrameWnd:: FloatControlBar](#floatcontrolbar)|Flota una barra de controles.|  
|[CFrameWnd::GetActiveDocument](#getactivedocument)|Devuelve el activo `CDocument` objeto.|  
|[CFrameWnd::GetActiveFrame](#getactiveframe)|Devuelve el activo `CFrameWnd` objeto.|  
|[CFrameWnd::GetActiveView](#getactiveview)|Devuelve el activo `CView` objeto.|  
|[CFrameWnd::GetControlBar](#getcontrolbar)|Recupera la barra de control.|  
|[CFrameWnd::GetDockState](#getdockstate)|Recupera el estado de acoplamiento de una ventana de marco.|  
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|Recupera el estado de vista del menú de la aplicación MFC actual.|  
|[CFrameWnd::GetMenuBarVisibility](#getmenubarvisibility)|Indica si el comportamiento predeterminado del menú de la aplicación MFC actual está oculto o visible.|  
|[CFrameWnd::GetMessageBar](#getmessagebar)|Devuelve un puntero a la que pertenecen a la ventana de marco de la barra de estado.|  
|[CFrameWnd:: GetMessageString](#getmessagestring)|Recupera el mensaje correspondiente a un identificador de comando.|  
|[CFrameWnd::GetTitle](#gettitle)|Recupera el título de la barra de controles relacionados.|  
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|Hace que el `OnInitialUpdate` función miembro que pertenecen a todas las vistas en la ventana de marco que se llame.|  
|[CFrameWnd::InModalState](#inmodalstate)|Devuelve un valor que indica si es o no una ventana de marco en un estado modal.|  
|[CFrameWnd::IsTracking](#istracking)|Determina si actualmente se está moviendo barra divisora.|  
|[CFrameWnd::LoadAccelTable](#loadacceltable)|Llamada a cargar una tabla de aceleradores.|  
|[CFrameWnd:: LoadBarState](#loadbarstate)|Llamada a restaurar la configuración de la barra de control.|  
|[CFrameWnd::LoadFrame](#loadframe)|Llamada a crear dinámicamente una ventana de marco de información de recursos.|  
|[CFrameWnd::NegotiateBorderSpace](#negotiateborderspace)|Negocia el espacio del borde de la ventana de marco.|  
|[CFrameWnd::OnBarCheck](#onbarcheck)|Se llama cada vez que se realice una acción en la barra de control especificado.|  
|[CFrameWnd::OnContextHelp](#oncontexthelp)|Controla MAYÚS + F1 Ayuda para los elementos en contexto.|  
|[CFrameWnd:: Onsetpreviewmode](#onsetpreviewmode)|Establece la ventana de marco principal de la aplicación dentro y fuera del modo de vista previa de impresión.|  
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|Lo llama el marco de trabajo cuando se actualiza el menú asociado.|  
|[RecalcLayout](#recalclayout)|Cambia de posición de las barras de control de la `CFrameWnd` objeto.|  
|[CFrameWnd:: SaveBarState](#savebarstate)|Llamada a guardar la configuración de la barra de control.|  
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|Designa la vista especificada sea la vista activa para vista previa avanzada.|  
|[CFrameWnd::SetActiveView](#setactiveview)|Establece el activo `CView` objeto.|  
|[CFrameWnd::SetDockState](#setdockstate)|Llamada a acoplar la ventana de marco en la ventana principal.|  
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|Establece el estado de vista del menú de la aplicación MFC actual a oculto o que se muestran.|  
|[CFrameWnd::SetMenuBarVisibility](#setmenubarvisibility)|Establece el comportamiento predeterminado del menú de la aplicación MFC actual esté oculto o visible.|  
|[CFrameWnd::SetMessageText](#setmessagetext)|Establece el texto de una barra de estado estándar.|  
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|Establece la posición actual de la barra de progreso de Windows 7 que se muestra en la barra de tareas.|  
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|Establece el intervalo de la barra de progreso de Windows 7 que se muestra en la barra de tareas.|  
|[CFrameWnd::SetProgressBarState](#setprogressbarstate)|Establece el tipo y el estado del indicador de progreso aparece en un botón de barra de tareas.|  
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|Sobrecargado. Se aplica a una superposición a un botón de barra de tareas para indicar el estado de la aplicación o una notificación al usuario.|  
|[CFrameWnd::SetTitle](#settitle)|Establece el título de la barra de controles relacionados.|  
|[CFrameWnd::ShowControlBar](#showcontrolbar)|Llamada a mostrar la barra de control.|  
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|Muestra todas las ventanas que son descendientes de los `CFrameWnd` objeto.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFrameWnd::OnCreateClient](#oncreateclient)|Crea una ventana de cliente para el marco.|  
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|Se llama antes de que el menú de la aplicación MFC actual está oculto.|  
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|Se llama antes de que aparezca el menú de la aplicación MFC actual.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|Controles automática habilitar y deshabilitar la funcionalidad de los elementos de menú.|  
|[CFrameWnd::rectDefault](#rectdefault)|Pase este estático `CRect` como un parámetro al crear un `CFrameWnd` objeto para permitir que Windows elegir el tamaño inicial y la posición de la ventana.|  
  
## <a name="remarks"></a>Comentarios  
 Para crear una ventana de marco útiles para su aplicación, derive una clase de `CFrameWnd`. Agregar variables miembro a la clase derivada para almacenar datos específicos de la aplicación. Implemente funciones miembro de controlador de mensajes y un mapa de mensajes en la clase derivada para especificar qué ocurre cuando los mensajes se dirigen a la ventana.  
  
 Hay tres formas de crear una ventana de marco:  
  
-   Crear directamente mediante [crear](#create).  
  
-   Crear directamente mediante [LoadFrame](#loadframe).  
  
-   Construir indirectamente mediante una plantilla de documento.  
  
 Antes de llamar a cualquiera `Create` o `LoadFrame`, debe construir el objeto de ventana de marco en el montón mediante C++ **nuevo** operador. Antes de llamar a `Create`, también puede registrar una clase de ventana con el [AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass) función global para establecer los estilos de icono y de clase para el marco.  
  
 Use el `Create` función miembro para pasar parámetros de creación del marco de inmediatos como argumentos.  
  
 `LoadFrame` requiere menos argumentos que `Create`y recupera en su lugar, la mayoría de sus valores predeterminados de recursos, incluidos el título del marco, icono, tabla de aceleradores y menús. Para tener acceso a `LoadFrame`, todos estos recursos deben tener el mismo identificador de recurso (por ejemplo, IDR_MAINFRAME).  
  
 Cuando un `CFrameWnd` objeto contiene documentos y vistas, crea indirectamente el marco de trabajo en lugar de directamente por el programador. La `CDocTemplate` objeto organiza la creación del marco, la creación de las vistas que contienen y la conexión de las vistas para el documento adecuado. Los parámetros de la `CDocTemplate` constructor especifica el `CRuntimeClass` de las tres clases implicadas (documento, marco y ver). Un `CRuntimeClass` objeto se usa el marco de trabajo para crear de forma dinámica nuevos marcos al especificado por el usuario (por ejemplo, mediante el comando nuevo archivo o el comando nueva ventana de varios documentos MDI (interfaz)).  
  
 Deriva una clase de ventana de marco `CFrameWnd` debe declararse con DECLARE_DYNCREATE para el mecanismo RUNTIME_CLASS anterior funcione correctamente.  
  
 Un `CFrameWnd` contiene implementaciones predeterminadas para llevar a cabo las siguientes funciones de ventana principal de una en una aplicación típica de Windows:  
  
-   Un `CFrameWnd` ventana de marco realiza un seguimiento de una vista activa que es independiente de la ventana activa de Windows o el foco de entrada actual. Cuando se reactiva el marco, la vista activa es una notificación mediante una llamada a `CView::OnActivateView`.  
  
-   Comando mensajes y muchos mensajes de notificación de marco común, las que controlan incluidas la `OnSetFocus`, `OnHScroll`, y `OnVScroll` funciones de `CWnd`, se delegan por un `CFrameWnd` ventana de marco en la vista activa actualmente.  
  
-   La vista activa actual (o la ventana de marco de secundario MDI activo actualmente en el caso de un marco de MDI) puede determinar el título de la ventana de marco. Esta característica puede deshabilitarse si se desactiva el bit de estilo FWS_ADDTOTITLE de la ventana de marco.  
  
-   Un `CFrameWnd` ventana de marco administra la posición de las barras de control, vistas y otras ventanas secundarias dentro del área de cliente de la ventana de marco. Una ventana de marco también realiza la actualización de tiempo de inactividad de la barra de herramientas y otros botones de barra de control. Un `CFrameWnd` ventana de marco también tiene implementaciones predeterminadas de los comandos para alternar activar y desactivar la barra de estado y la barra de herramientas.  
  
-   Un `CFrameWnd` ventana de marco administra la barra de menús principal. Cuando se muestra un menú emergente, la ventana de marco utiliza el mecanismo UPDATE_COMMAND_UI para determinar qué elementos de menú deben ser habilitados, deshabilitados o activados. Cuando el usuario selecciona un elemento de menú, en la ventana de marco se actualiza la barra de estado con la cadena de mensaje para ese comando.  
  
-   Un `CFrameWnd` ventana de marco tiene una tabla de aceleradores opcional que traduce automáticamente los aceleradores de teclado.  
  
-   Un `CFrameWnd` ventana de marco tiene un identificador de ayuda opcional establecido con `LoadFrame` que sirve de ayuda contextual. Una ventana de marco es el principal orchestrator de Estados semimodales, como los modos de vista previa de impresión y ayuda contextual (MAYÚS + F1).  
  
-   Un `CFrameWnd` ventana de marco abrirá un archivo desde el Administrador de archivos de arrastrar y colocar en la ventana de marco. Si una extensión de archivo está registrada y asociada a la aplicación, la ventana de marco responde a la solicitud de apertura dinámico de datos (DDE) de exchange que se produce cuando el usuario abre un archivo de datos en el Administrador de archivos o cuando el `ShellExecute` se llama a la función de Windows.  
  
-   Si la ventana de marco es la ventana principal de la aplicación (es decir, `CWinThread::m_pMainWnd`), cuando el usuario cierra la aplicación, la ventana de marco pide al usuario que guarde los documentos modificados (para `OnClose` y `OnQueryEndSession`).  
  
-   Si la ventana de marco es la ventana principal de la aplicación, la ventana de marco es el contexto para la ejecución de WinHelp. Cierre la ventana de marco se apagará WINHELP. EXE si se inició para obtener ayuda para esta aplicación.  
  
 No use C++ **eliminar** operador para destruir una ventana de marco. Utilice `CWnd::DestroyWindow` en su lugar. El `CFrameWnd` implementací `PostNcDestroy` eliminará el objeto de C++ cuando se destruye la ventana. Cuando el usuario cierra la ventana de marco, el valor predeterminado `OnClose` controlador llamará `DestroyWindow`.  
  
 Para obtener más información sobre `CFrameWnd`, consulte [marco Windows](../../mfc/frame-windows.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CFrameWnd`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="activateframe"></a>  CFrameWnd::ActivateFrame  
 Llame a esta función miembro para activar y restaurar la ventana de marco para que sea visible y disponible para el usuario.  
  
```  
virtual void ActivateFrame(int nCmdShow = -1);
```  
  
### <a name="parameters"></a>Parámetros  
 *nCmdShow*  
 Especifica el parámetro para pasarlo a [CWnd:: ShowWindow](../../mfc/reference/cwnd-class.md#showwindow). De forma predeterminada, el marco es que se muestran y se restauró correctamente.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, esta función miembro se llama después de un evento de interfaz de usuario que no son como DDE, OLE u otro evento que se puede mostrar la ventana de marco o su contenido al usuario.  
  
 La implementación predeterminada activa el marco y pone a la parte superior del orden Z y, si es necesario, lleva a cabo los mismos pasos para la ventana de marco principal de la aplicación.  
  
 Reemplace esta función miembro para cambiar cómo se activa un marco. Por ejemplo, puede forzar ventanas secundarias MDI maximizarse. Agregar la funcionalidad adecuada y, después, llame a la versión de la clase base con explícita *nCmdShow*.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]  
  
##  <a name="beginmodalstate"></a>  CFrameWnd::BeginModalState  
 Llame a esta función miembro para convertir una ventana marco en modal.  
  
```  
virtual void BeginModalState();
```  
  
##  <a name="cframewnd"></a>  CFrameWnd::CFrameWnd  
 Construye un `CFrameWnd` de objeto, pero no crea la ventana de marco visible.  
  
```  
CFrameWnd();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a `Create` para crear la ventana visible.  
  
##  <a name="create"></a>  CFrameWnd::Create  
 Llamada a crear e inicializar la ventana de marco de Windows asociada con el `CFrameWnd` objeto.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle = WS_OVERLAPPEDWINDOW,  
    const RECT& rect = rectDefault,  
    CWnd* pParentWnd = NULL,  
    LPCTSTR lpszMenuName = NULL,  
    DWORD dwExStyle = 0,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszClassName*  
 Apunta a una cadena de caracteres terminada en null que se nombra la clase de Windows. El nombre de clase puede ser cualquier nombre registrado con el `AfxRegisterWndClass` función global o `RegisterClass` función de Windows. Si es NULL, se usa el valor predeterminado predefinido `CFrameWnd` atributos.  
  
 *lpszWindowName*  
 Apunta a una cadena de caracteres terminada en null que representa el nombre de la ventana. Se utiliza como texto de la barra de título.  
  
 *dwStyle*  
 Especifica el período de [estilo](../../mfc/reference/styles-used-by-mfc.md#window-styles) atributos. Incluya el estilo FWS_ADDTOTITLE si desea que la barra de título para mostrar automáticamente el nombre del documento representado en la ventana.  
  
 *Rect*  
 Especifica el tamaño y posición de la ventana. El *rectDefault* valor permite que Windows especificar el tamaño y posición de la nueva ventana.  
  
 *pParentWnd*  
 Especifica la ventana primaria de esta ventana de marco. Este parámetro debe ser NULL para ventanas de marco de nivel superior.  
  
 *lpszMenuName*  
 Identifica el nombre del recurso de menú que se usará con la ventana. Use MAKEINTRESOURCE si el menú tiene un identificador entero en lugar de una cadena. Este parámetro puede ser NULL.  
  
 *dwExStyle*  
 Especifica el período extendido [estilo](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) atributos.  
  
 *pContext*  
 Especifica un puntero a un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) estructura. Este parámetro puede ser NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la inicialización es correcta; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Construir un `CFrameWnd` objeto en dos pasos. En primer lugar, invocar el constructor, que construye la `CFrameWnd` objeto y, a continuación, llame a `Create`, que crea la ventana de marco de Windows y lo adjunta a la `CFrameWnd` objeto. `Create` Inicializa el nombre de la ventana de la clase y nombre de la ventana y registra los valores predeterminados para su estilo, el elemento primario y menú asociado.  
  
 Use `LoadFrame` lugar `Create` para cargar la ventana de marco de un recurso en lugar de especificar sus argumentos.  
  
##  <a name="createview"></a>  CFrameWnd::CreateView  
 Llame a `CreateView` para crear una vista dentro de un marco.  
  
```  
CWnd* CreateView(
    CCreateContext* pContext,  
    UINT nID = AFX_IDW_PANE_FIRST);
```  
  
### <a name="parameters"></a>Parámetros  
 *pContext*  
 Especifica el tipo de documento y vista.  
  
 *nID*  
 El número de Id. de una vista.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un `CWnd` objeto si es correcto; de lo contrario, NULL.  
  
### <a name="remarks"></a>Comentarios  
 Use esta función miembro para crear "vistas" que no son `CView`-derivadas dentro de un marco. Después de llamar a `CreateView`, debe establecer la vista activa manualmente y establecer que sea visible; de estas tareas no se realizan automáticamente por `CreateView`.  
  
##  <a name="dockcontrolbar"></a>  CFrameWnd:: DockControlBar  
 Hace que una barra de control se acopla a la ventana de marco.  
  
```  
void DockControlBar(
    CControlBar* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *pBar*  
 Apunta a la barra de control quede acoplado.  
  
 *nDockBarID*  
 Determina qué lados de la ventana de marco que considere la posibilidad de acoplamiento. Puede ser 0, o uno o varios de los siguientes:  
  
- AFX_IDW_DOCKBAR_TOP acoplar en el lado superior de la ventana de marco.  
  
- AFX_IDW_DOCKBAR_BOTTOM acoplar en el lado inferior de la ventana de marco.  
  
- AFX_IDW_DOCKBAR_LEFT acoplar a la izquierda de la ventana de marco.  
  
- AFX_IDW_DOCKBAR_RIGHT acoplar a la derecha de la ventana de marco.  
  
 Si es 0, la barra de control se puede acoplar a cualquier lado habilitado para el acoplamiento en la ventana de marco de destino.  
  
 *lpRect*  
 Determina, en coordenadas de pantalla, donde se acoplará la barra de control en el área no cliente de la ventana de marco de destino.  
  
### <a name="remarks"></a>Comentarios  
 La barra de control se acoplará a uno de los lados de la ventana de marco especificado en las llamadas a ambos [CControlBar:: EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking) y [CFrameWnd:: EnableDocking](#enabledocking). Los elegidos lado viene determinada por *nDockBarID*.  
  
##  <a name="enabledocking"></a>  CFrameWnd:: EnableDocking  
 Llame a esta función para habilitar las barras de control acoplable en una ventana de marco.  
  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwDockStyle*  
 Especifica qué lados de la ventana de marco pueden actuar como sitios para barras de control de acoplamiento. Puede ser uno o varios de los siguientes:  
  
- CBRS_ALIGN_TOP permite acoplar en la parte superior del área cliente.  
  
- CBRS_ALIGN_BOTTOM permite acoplar en la parte inferior del área de cliente.  
  
- CBRS_ALIGN_LEFT permite acoplar en el lado izquierdo del área cliente.  
  
- CBRS_ALIGN_RIGHT permite acoplar en el lado derecho del área de cliente.  
  
- CBRS_ALIGN_ANY permite acoplar en cualquier lado del área de cliente.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, las barras de control estará acopladas a un lado de la ventana de marco en el siguiente orden: superior, inferior, izquierda, derecha.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CToolBar:: Create](../../mfc/reference/ctoolbar-class.md#create).  
  
##  <a name="endmodalstate"></a>  CFrameWnd::EndModalState  
 Llame a esta función miembro para cambiar una ventana marco de modal a no modal.  
  
```  
virtual void EndModalState();
```  
  
### <a name="remarks"></a>Comentarios  
 `EndModalState` habilita todas las ventanas deshabilitadas de forma [BeginModalState](#beginmodalstate).  
  
##  <a name="floatcontrolbar"></a>  CFrameWnd:: FloatControlBar  
 Llame a esta función para que una barra de control no se acopla a la ventana de marco.  
  
```  
void FloatControlBar(
    CControlBar* pBar,  
    CPoint point,  
    DWORD dwStyle = CBRS_ALIGN_TOP);
```  
  
### <a name="parameters"></a>Parámetros  
 *pBar*  
 Apunta a la barra de control a flotar.  
  
 *punto*  
 La ubicación, en coordenadas de pantalla, donde se colocará la esquina superior izquierda de la barra de control.  
  
 *dwStyle*  
 Especifica si se debe alinear la barra de control horizontal o verticalmente, dentro de su nueva ventana de marco. Puede ser cualquiera de las siguientes acciones:  
  
- CBRS_ALIGN_TOP orienta verticalmente la barra de control.  
  
- CBRS_ALIGN_BOTTOM orienta verticalmente la barra de control.  
  
- CBRS_ALIGN_LEFT orienta horizontalmente la barra de control.  
  
- CBRS_ALIGN_RIGHT orienta horizontalmente la barra de control.  
  
 Si se pasan los estilos especificando la orientación horizontal y vertical, la barra de herramientas estará orientado horizontalmente.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, esto se realiza al iniciar la aplicación cuando el programa es restaurar la configuración de la ejecución anterior.  
  
 El marco de trabajo llama a esta función cuando el usuario da lugar a una operación de colocar soltando el botón primario del mouse mientras arrastra el puntero sobre una ubicación que no está disponible para acoplar la barra de control.  
  
##  <a name="getactivedocument"></a>  CFrameWnd::GetActiveDocument  
 Llame a esta función miembro para obtener un puntero a la actual `CDocument` asociado a la vista activa actual.  
  
```  
virtual CDocument* GetActiveDocument();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la actual [CDocument](../../mfc/reference/cdocument-class.md). Si no hay ningún documento actual, devuelve NULL.  
  
##  <a name="getactiveframe"></a>  CFrameWnd::GetActiveFrame  
 Llame a esta función miembro para obtener un puntero a activo ventana MDI (interfaz) secundario de múltiples documentos de una ventana de marco MDI.  
  
```  
virtual CFrameWnd* GetActiveFrame();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la ventana secundaria MDI activa. Si la aplicación es una aplicación SDI o la ventana de marco MDI no tiene ningún documento activo, implícito **esto** se devolverá el puntero.  
  
### <a name="remarks"></a>Comentarios  
 Si no hay ningún formulario secundario MDI activo o la aplicación es una interfaz de único documento (SDI), implícita **esto** devuelve el puntero.  
  
##  <a name="getactiveview"></a>  CFrameWnd::GetActiveView  
 Llame a esta función miembro para obtener un puntero a la vista activa (si existe) asociado a una ventana de marco ( `CFrameWnd`).  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la actual [CView](../../mfc/reference/cview-class.md). Si no hay ninguna vista actual, devuelve NULL.  
  
### <a name="remarks"></a>Comentarios  
 Esta función devuelve NULL cuando se llama para una ventana de marco principal MDI ( `CMDIFrameWnd`). En una aplicación MDI, la ventana de marco principal MDI no tiene una vista asociada con él. En su lugar, cada ventana secundarios individuales ( `CMDIChildWnd`) tiene una o varias vistas asociadas. Primero debe encontrar la ventana secundaria MDI activa y, a continuación, buscando la vista activa para esa ventana secundaria, se puede obtener la vista activa en una aplicación MDI. Puede encontrar la ventana secundaria MDI activa mediante una llamada a la función `MDIGetActive` o `GetActiveFrame` como se muestra en la siguiente:  
  
 [!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]  
  
##  <a name="getcontrolbar"></a>  CFrameWnd::GetControlBar  
 Llame a `GetControlBar` para obtener acceso a la barra de control que está asociado con el identificador.  
  
```  
CControlBar* GetControlBar(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 *nID*  
 El número de Id. de una barra de controles.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la barra de control que está asociado con el identificador.  
  
### <a name="remarks"></a>Comentarios  
 El *nID* parámetro hace referencia al identificador exclusivo pasan a la `Create` método de la barra de control. Para obtener más información sobre las barras de control, consulte el tema titulado [barras de Control](../../mfc/control-bars.md).  
  
 `GetControlBar` devolverá la barra de control incluso si está flotando y, por tanto, no es actualmente una ventana secundaria del marco.  
  
##  <a name="getdockstate"></a>  CFrameWnd::GetDockState  
 Llame a esta función miembro para almacenar información de estado acerca de las barras de control de la ventana de marco en un `CDockState` objeto.  
  
```  
void GetDockState(CDockState& state) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *state*  
 Contiene el estado actual de las barras de control de la ventana de marco cuando se devuelve.  
  
### <a name="remarks"></a>Comentarios  
 A continuación, puede escribir el contenido de `CDockState` en storage mediante `CDockState::SaveState` o `Serialize`. Si posteriormente desea restaurar las barras de control a un estado anterior, cargar el estado con `CDockState::LoadState` o `Serialize`, a continuación, llame a `SetDockState` para aplicar el estado anterior a barras de control de la ventana de marco.  
  
##  <a name="getmenubarstate"></a>  CFrameWnd::GetMenuBarState  
 Recupera el estado de vista del menú de la aplicación MFC actual.  
  
```  
virtual DWORD GetMenuBarState();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto puede tener los siguientes valores:  
  
-   AFX_MBS_VISIBLE (0 x 01): el menú es visible.  
  
-   AFX_MBS_HIDDEN (0 x 02): el menú está oculto.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error en tiempo de ejecución, este método valida en modo de depuración y provoca una excepción derivada de la [CException](../../mfc/reference/cexception-class.md) clase.  
  
##  <a name="getmenubarvisibility"></a>  CFrameWnd::GetMenuBarVisibility  
 Indica si el estado predeterminado del menú de la aplicación MFC actual está oculto o visible.  
  
```  
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Este método devuelve uno de los siguientes valores:  
  
-   AFX_MBV_KEEPVISIBLE (0 x 01): se muestra el menú en todo momento y de forma predeterminada no tiene el foco.  
  
-   AFX_MBV_DISPLAYONFOCUS (0 x 02): el menú está oculta de forma predeterminada. Si se oculta el menú, presione la tecla ALT para mostrar el menú y asignarle el foco. Si se muestra el menú, presione la tecla ALT o ESC para ocultarlo.  
  
-   AFX_MBV_ DISPLAYONFOCUS (0 x 02) &#124; AFX_MBV_DISPLAYONF10 (combinación bit a bit (OR)): (0 x 04) del menú está oculta de forma predeterminada. Si se oculta el menú, presione la tecla F10 para mostrar el menú y asignarle el foco. Si se muestra el menú, presione la tecla F10 para alternar el foco o desactivar el menú. Se muestra el menú hasta que presione la tecla ALT o ESC para ocultarlo.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error en tiempo de ejecución, este método valida en modo de depuración y provoca una excepción derivada de la [CException](../../mfc/reference/cexception-class.md) clase.  
  
##  <a name="getmessagebar"></a>  CFrameWnd::GetMessageBar  
 Llame a esta función miembro para obtener un puntero a la barra de estado.  
  
```  
virtual CWnd* GetMessageBar();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la ventana de la barra de estado.  
  
##  <a name="getmessagestring"></a>  CFrameWnd:: GetMessageString  
 Reemplace esta función para proporcionar cadenas personalizadas para los identificadores de comando.  
  
```  
virtual void GetMessageString(
    UINT nID,  
    CString& rMessage) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *nID*  
 Identificador de recurso del mensaje deseado.  
  
 *rMessage*  
 `CString` objeto en el que se va a colocar el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada simplemente carga la cadena especificada por *nID* desde el archivo de recursos. Esta función se llama el marco de trabajo cuando la cadena de mensaje en la barra de estado debe actualizarse.  
  
##  <a name="gettitle"></a>  CFrameWnd::GetTitle  
 Recupera el título del objeto de ventana.  
  
```  
CString GetTitle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el título del objeto de ventana actual.  
  
##  <a name="initialupdateframe"></a>  CFrameWnd::InitialUpdateFrame  
 Llame a `IntitialUpdateFrame` después de crear un nuevo marco con `Create`.  
  
```  
void InitialUpdateFrame(
    CDocument* pDoc,  
    BOOL bMakeVisible);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDoc*  
 Apunta al documento al que está asociada la ventana de marco. Puede ser NULL.  
  
 *bMakeVisible*  
 Si es TRUE, indica que el marco debe convertirse en visible y activo. Si es FALSE, no hay descendientes se hacen visibles.  
  
### <a name="remarks"></a>Comentarios  
 Esto hace que todas las vistas en esa ventana de marco para recibir sus `OnInitialUpdate` llamadas.  
  
 Además, si anteriormente no era una vista activa, la vista de la ventana de marco principal estará activa. La vista primaria es una vista con un elemento secundario Id. de AFX_IDW_PANE_FIRST. Por último, la ventana de marco se hace visible si *bMakeVisible* es distinto de cero. Si *bMakeVisible* es 0, el foco actual y el estado de visibilidad de la ventana de marco permanecerá sin cambios. No es necesario llamar a esta función cuando se usa la implementación del marco de trabajo de archivo nuevo y abrir archivo.  
  
##  <a name="inmodalstate"></a>  CFrameWnd::InModalState  
 Llame a esta función miembro para comprobar si una ventana de marco es modal o no modal.  
  
```  
BOOL InModalState() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero en caso afirmativo; en caso contrario, es 0.  
  
##  <a name="istracking"></a>  CFrameWnd::IsTracking  
 Llame a esta función miembro para determinar si la barra de división en la ventana se está moviendo actualmente.  
  
```  
BOOL IsTracking() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si una operación de divisor está en curso; en caso contrario, es 0.  
  
##  <a name="loadacceltable"></a>  CFrameWnd::LoadAccelTable  
 Llamada a cargar la tabla de aceleradores especificado.  
  
```  
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszResourceName*  
 Identifica el nombre del recurso acelerador. Use MAKEINTRESOURCE si el recurso se identifica con un identificador entero.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la tabla de aceleradores se cargó correctamente; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Solo una tabla se puede cargar a la vez.  
  
 Tablas de aceleradores cargadas desde los recursos se liberan automáticamente cuando finaliza la aplicación.  
  
 Si se llama a `LoadFrame` para crear la ventana de marco, el marco de trabajo carga una tabla de aceleradores junto con los recursos de menú y el icono y, a continuación, es necesaria una llamada subsiguiente a esta función miembro.  
  
##  <a name="loadbarstate"></a>  CFrameWnd:: LoadBarState  
 Llame a esta función para restaurar la configuración de cada barra de controles que pertenecen a la ventana de marco.  
  
```  
void LoadBarState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszProfileName*  
 Nombre de una sección en el archivo de inicialización (INI) o una clave del registro de Windows donde se almacena la información de estado.  
  
### <a name="remarks"></a>Comentarios  
 Restaurar la información incluye orientación horizontal o vertical, visibilidad, estado de acoplamiento y posición de la barra de control.  
  
 La configuración que desea restaurar debe escribirse en el registro antes de llamar a `LoadBarState`. Escribir la información en el registro mediante una llamada a [CWinApp::SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey). Escribir la información en el archivo INI mediante una llamada a [SaveBarState](#savebarstate).  
  
##  <a name="loadframe"></a>  CFrameWnd::LoadFrame  
 Llamada a crear dinámicamente una ventana de marco de información de recursos.  
  
```  
virtual BOOL LoadFrame(
    UINT nIDResource,  
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,  
    CWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *nIDResource*  
 El identificador de recursos compartidos asociados con la ventana de marco.  
  
 *dwDefaultStyle*  
 El marco [estilo](../../mfc/reference/styles-used-by-mfc.md#window-styles). Incluya el estilo FWS_ADDTOTITLE si desea que la barra de título para mostrar automáticamente el nombre del documento representado en la ventana.  
  
 *pParentWnd*  
 Un puntero al elemento primario del marco.  
  
 *pContext*  
 Un puntero a un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) estructura. Este parámetro puede ser NULL.  
  
### <a name="remarks"></a>Comentarios  
 Construir un `CFrameWnd` objeto en dos pasos. En primer lugar, invocar el constructor, que construye la `CFrameWnd` objeto y, a continuación, llame a `LoadFrame`, que carga la ventana de marco de Windows y los recursos asociados y se adjunta a la ventana de marco para el `CFrameWnd` objeto. El *nIDResource* parámetro especifica el menú, la tabla de aceleradores, el icono y el recurso de cadena del título de la ventana de marco.  
  
 Use la `Create` función miembro en lugar de `LoadFrame` cuando desee especificar todos los parámetros de creación de la ventana de marco.  
  
 Las llamadas de framework `LoadFrame` cuando crea una ventana de marco utilizando un objeto de plantilla de documento.  
  
 El marco de trabajo usa el *pContext* argumento para especificar los objetos que se va a estar conectado a la ventana de marco, los incluidos contenidos de objetos de vista. Puede establecer el *pContext* argumento NULL cuando se llama a `LoadFrame`.  
  
##  <a name="m_bautomenuenable"></a>  CFrameWnd::m_bAutoMenuEnable  
 Cuando se habilita este miembro de datos (que es el valor predeterminado), los elementos de menú que no tienen controladores ON_UPDATE_COMMAND_UI o ON_COMMAND se deshabilitará automáticamente cuando el usuario extrae un menú desplegable.  
  
```  
BOOL m_bAutoMenuEnable;  
```  
  
### <a name="remarks"></a>Comentarios  
 Los elementos de menú que tienen un controlador ON_COMMAND pero no hay ningún controlador ON_UPDATE_COMMAND_UI se habilitará automáticamente.  
  
 Cuando se establece este miembro de datos, se habilitan automáticamente los elementos de menú de la misma manera que se habilitan los botones de barra de herramientas.  
  
> [!NOTE]
> `m_bAutoMenuEnable` no tiene ningún efecto en los elementos de menú de nivel superior.  
  
 Este miembro de datos simplifica la implementación de comandos opcionales, según la selección actual y reduce la necesidad de escribir controladores ON_UPDATE_COMMAND_UI para habilitar y deshabilitar los elementos de menú.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]  
  
##  <a name="negotiateborderspace"></a>  CFrameWnd::NegotiateBorderSpace  
 Llame a esta función miembro para negociar el espacio del borde de una ventana de marco durante la activación de inplace OLE.  
  
```  
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,  
    LPRECT lpRectBorder);
```  
  
### <a name="parameters"></a>Parámetros  
 *nBorderCmd*  
 Contiene uno de los siguientes valores de la `enum BorderCmd`:  
  
- `borderGet` = 1  
  
- `borderRequest` = 2  
  
- `borderSet` = 3  
  
 *lpRectBorder*  
 Puntero a un [RECT](../../mfc/reference/rect-structure1.md) estructura o un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que especifica las coordenadas del borde.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro es la `CFrameWnd` implementación de negociación de espacio del borde OLE.  
  
##  <a name="onbarcheck"></a>  CFrameWnd::OnBarCheck  
 Se llama cada vez que se realice una acción en la barra de control especificado.  
  
```  
afx_msg BOOL OnBarCheck(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 *nID*  
 El identificador del control de la barra se muestra.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si existiera la barra de control; en caso contrario, es 0.  
  
##  <a name="oncontexthelp"></a>  CFrameWnd::OnContextHelp  
 Controla MAYÚS + F1 Ayuda para los elementos en contexto.  
  
```  
afx_msg void OnContextHelp();
```  
  
### <a name="remarks"></a>Comentarios  
 Para habilitar la Ayuda contextual, debe agregar un  
  
 [!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]  
  
 instrucción a su `CFrameWnd` mapa de mensajes de la clase y también agregar una entrada de tabla de aceleradores, normalmente MAYÚS+F1, para habilitar esta función miembro.  
  
 Si la aplicación es un contenedor OLE, `OnContextHelp` coloca todos los elementos en contexto dentro del objeto de ventana de marco en modo de ayuda. El cursor cambia a una flecha y un signo de interrogación y el usuario, a continuación, puede mover el puntero del mouse y presione el botón primario del mouse para seleccionar un cuadro de diálogo, ventana, menú o botón de comando. Esta función miembro llama a la función de Windows `WinHelp` con el contexto de Ayuda del objeto bajo el cursor.  
  
##  <a name="oncreateclient"></a>  CFrameWnd::OnCreateClient  
 Lo llama el marco de trabajo durante la ejecución de `OnCreate`.  
  
```  
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,  
    CCreateContext* pContext);
```  
  
### <a name="parameters"></a>Parámetros  
 *LPC*  
 Un puntero a un Windows [CREATESTRUCT](../../mfc/reference/createstruct-structure.md) estructura.  
  
 *pContext*  
 Un puntero a un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Nunca se llame a esta función.  
  
 La implementación predeterminada de esta función crea un `CView` objeto a partir de la información proporcionada en *pContext*, si es posible.  
  
 Reemplace esta función para invalidar los valores pasados en el `CCreateContext` de objeto o para cambiar los controles de la manera en el área de cliente principal de la ventana de marco se crean. El `CCreateContext` se describen los miembros que se puede invalidar en el [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) clase.  
  
> [!NOTE]
>  No reemplazar los valores pasados en el `CREATESTRUCT` estructura. Son para uso meramente informativo. Si desea invalidar el rectángulo de ventana inicial, por ejemplo, reemplazar el `CWnd` función miembro [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).  
  
##  <a name="onhidemenubar"></a>  CFrameWnd::OnHideMenuBar  
 Esta función se invoca cuando el sistema está a punto de ocultar la barra de menús de la aplicación MFC actual.  
  
```  
virtual void OnHideMenuBar();
```  
  
### <a name="remarks"></a>Comentarios  
 Este controlador de eventos permite que la aplicación realizar acciones personalizadas cuando el sistema está a punto de ocultar el menú. No se puede impedir que el menú está oculto, pero puede, por ejemplo, llamar a otros métodos para recuperar el estilo de menú o el estado.  
  
##  <a name="onsetpreviewmode"></a>  CFrameWnd:: Onsetpreviewmode  
 Llame a esta función miembro para establecer la ventana de marco principal de la aplicación dentro y fuera del modo de vista previa de impresión.  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>Parámetros  
 *bPreview*  
 Especifica si se va a colocar la aplicación en modo de vista previa de impresión o no. Se establece en TRUE para colocar en la vista previa de impresión, FALSE para cancelar el modo de vista previa.  
  
 *pState*  
 Un puntero a un `CPrintPreviewState` estructura.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada deshabilita todas las barras de herramientas estándares y oculta el menú principal y la ventana principal de cliente. Esto convierte ventanas de marco MDI en ventanas de marco SDI temporales.  
  
 Reemplace esta función miembro para personalizar el mostrar y ocultar las barras de control y otras partes de la ventana de marco durante la vista previa de impresión. Llame a la implementación de clase base desde dentro de la versión invalidada.  
  
##  <a name="onshowmenubar"></a>  CFrameWnd::OnShowMenuBar  
 Esta función se invoca cuando el sistema está a punto de mostrar la barra de menús en la aplicación MFC actual.  
  
```  
virtual void OnShowMenuBar();
```  
  
### <a name="remarks"></a>Comentarios  
 Este controlador de eventos permite que la aplicación realizar acciones personalizadas cuando el menú se va a mostrar. No se puede impedir que el menú que se muestre, pero puede, por ejemplo, llamar a otros métodos para recuperar el estilo de menú o el estado.  
  
##  <a name="onupdatecontrolbarmenu"></a>  CFrameWnd::OnUpdateControlBarMenu  
 Lo llama el marco de trabajo cuando se actualiza el menú asociado.  
  
```  
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parámetros  
 *pCmdUI*  
 Un puntero a un [CCmdUI](../../mfc/reference/ccmdui-class.md) objeto que representa el menú que generó el comando de actualización. Las llamadas del controlador de actualización de la [habilitar](../../mfc/reference/ccmdui-class.md#enable) función miembro de la `CCmdUI` objeto a través de *pCmdUI* para actualizar la interfaz de usuario.  
  
##  <a name="recalclayout"></a>  RecalcLayout  
 Lo llama el marco de trabajo cuando las barras de control estándar se activan o desactivan, o cuando se cambia el tamaño de la ventana de marco.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *bNotify*  
 Determina si el elemento en contexto activo para la ventana de marco recibe la notificación del cambio de diseño. Si es TRUE, se notifica el elemento; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función miembro llama a la `CWnd` función miembro `RepositionBars` para volver a colocar todas las barras de control en el marco, así como en la ventana principal de cliente (normalmente un `CView` o MDICLIENT).  
  
 Reemplace esta función miembro para controlar la apariencia y comportamiento de las barras de control después de cambia el diseño de la ventana de marco. Por ejemplo, llamar al activar o desactivar la barras de control o agregar otra barra de control.  
  
##  <a name="rectdefault"></a>  CFrameWnd::rectDefault  
 Pase este estático `CRect` como un parámetro al crear una ventana para permitir que Windows elegir el tamaño inicial y la posición de la ventana.  
  
```  
static AFX_DATA const CRect rectDefault;  
```  
  
##  <a name="savebarstate"></a>  CFrameWnd:: SaveBarState  
 Llame a esta función para almacenar información sobre cada propiedad de la ventana de marco de la barra de control.  
  
```  
void SaveBarState(LPCTSTR lpszProfileName) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszProfileName*  
 Nombre de una sección en el archivo de inicialización o una clave del registro de Windows donde se almacena la información de estado.  
  
### <a name="remarks"></a>Comentarios  
 Esta información puede leerse desde el archivo de inicialización mediante [LoadBarState](#loadbarstate). La información almacenada incluye visibilidad, la orientación horizontal o vertical, estado y la posición de la barra de control de acoplamiento.  
  
##  <a name="setactivepreviewview"></a>  CFrameWnd::SetActivePreviewView  
 Designa la vista especificada sea la vista activa para vista previa avanzada.  
  
```  
void SetActivePreviewView(CView* pViewNew);
```  
  
### <a name="parameters"></a>Parámetros  
 *pViewNew*  
 Un puntero a una vista para activarse.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setactiveview"></a>  CFrameWnd::SetActiveView  
 Llame a esta función miembro para establecer la vista activa.  
  
```  
void SetActiveView(
    CView* pViewNew,  
    BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *pViewNew*  
 Especifica un puntero a un [CView](../../mfc/reference/cview-class.md) objeto, o NULL para ninguna vista activa.  
  
 *bNotify*  
 Especifica si la vista es recibir una notificación de activación. Si es TRUE, `OnActivateView` se llama para la nueva vista; si es FALSE, no es así.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llamará a esta función automáticamente cuando el usuario cambia el foco a una vista en la ventana de marco. Puede llamar explícitamente a `SetActiveView` para cambiar el foco a la vista especificada.  
  
##  <a name="setdockstate"></a>  CFrameWnd::SetDockState  
 Llame a esta función miembro para aplicar la información de estado almacenada en un `CDockState` objeto a las barras de control de la ventana de marco.  
  
```  
void SetDockState(const CDockState& state);
```  
  
### <a name="parameters"></a>Parámetros  
 *state*  
 El estado almacenado se aplican a las barras de control de la ventana de marco.  
  
### <a name="remarks"></a>Comentarios  
 Para restaurar un estado anterior de las barras de control, puede cargar el estado almacenado con `CDockState::LoadState` o `Serialize`, a continuación, usar `SetDockState` para aplicarlo a las barras de control de la ventana de marco. El estado anterior se almacena en el `CDockState` de objetos con `GetDockState`  
  
##  <a name="setmenubarstate"></a>  CFrameWnd::SetMenuBarState  
 Establece el estado de vista del menú de la aplicación MFC actual a oculto o que se muestran.  
  
```  
virtual BOOL SetMenuBarState(DWORD nState);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] *nState*|Especifica si se debe mostrar u ocultar el menú. El *nState* parámetro puede tener los siguientes valores:<br /><br /> -AFX_MBS_VISIBLE (0 x 01): muestra el menú si está oculto, pero no tiene ningún efecto si está visible.<br />-AFX_MBS_HIDDEN (0 x 02): oculta el control menu si está visible, pero no tiene ningún efecto si está oculto.|  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si este método cambia correctamente el estado de menú. en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error en tiempo de ejecución, este método valida en modo de depuración y provoca una excepción derivada de la [CException](../../mfc/reference/cexception-class.md) clase.  
  
##  <a name="setmenubarvisibility"></a>  CFrameWnd::SetMenuBarVisibility  
 Establece el comportamiento predeterminado del menú de la aplicación MFC actual esté oculto o visible.  
  
```  
virtual void SetMenuBarVisibility(DWORD nStyle);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] *nStyle*|Especifica si el menú está oculta, de manera predeterminada o es visible y tiene el foco. El *nStyle* parámetro puede tener los siguientes valores:<br /><br /> -AFX_MBV_KEEPVISIBLE (0 X 01):<br />     El menú se muestra en todo momento y, de forma predeterminada no tiene el foco.<br />-AFX_MBV_DISPLAYONFOCUS (0 X 02):<br />     El menú está oculta de forma predeterminada. Si se oculta el menú, presione la tecla ALT para mostrar el menú y asignarle el foco. Si se muestra el menú, presione la tecla ALT o ESC para ocultar el menú.<br />-AFX_MBV_ DISPLAYONFOCUS (0 x 02) &#124; AFX_MBV_DISPLAYONF10 (0 x 04)<br />     (combinación bit a bit (OR)): el menú está oculta de forma predeterminada. Si se oculta el menú, presione la tecla F10 para mostrar el menú y asignarle el foco. Si se muestra el menú, presione la tecla F10 para alternar el foco o desactivar el menú. Se muestra el menú hasta que presione la tecla ALT o ESC para ocultarlo.|  
  
### <a name="remarks"></a>Comentarios  
 Si el valor de la *nStyle* parámetro no es válido, este método valida en modo de depuración y provoca [CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md) en modo de lanzamiento. En el caso de otros errores en tiempo de ejecución, este método aserciones en modo de depuración y provoca una excepción derivada de la [CException](../../mfc/reference/cexception-class.md) clase.  
  
 Este método afecta al estado de menús de las aplicaciones escritas para [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] y versiones posteriores.  
  
##  <a name="setmessagetext"></a>  CFrameWnd::SetMessageText  
 Llame a esta función para colocar una cadena en el panel de barra de estado que tiene un identificador de 0.  
  
```  
void SetMessageText(LPCTSTR lpszText);  
void SetMessageText(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszText*  
 Apunta a la cadena que se colocará en la barra de estado.  
  
 *nID*  
 Identificador de recurso de cadena de la cadena que se colocará en la barra de estado.  
  
### <a name="remarks"></a>Comentarios  
 Esto suele ser el panel izquierdo y más largo, de la barra de estado.  
  
##  <a name="setprogressbarposition"></a>  CFrameWnd::SetProgressBarPosition  
 Establece la posición actual de la barra de progreso de Windows 7 que se muestra en la barra de tareas.  
  
```  
void SetProgressBarPosition(int nProgressPos);
```  
  
### <a name="parameters"></a>Parámetros  
 *nProgressPos*  
 Especifica la posición para establecer. Debe estar en el intervalo establecido por `SetProgressBarRange`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setprogressbarrange"></a>  CFrameWnd::SetProgressBarRange  
 Establece la duración de la barra de progreso de Windows 7 que se muestra en la barra de tareas.  
  
```  
void SetProgressBarRange(
    int nRangeMin,  
    int nRangeMax);
```  
  
### <a name="parameters"></a>Parámetros  
 *nRangeMin*  
 Valor mínimo.  
  
 *nRangeMax*  
 Valor máximo.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setprogressbarstate"></a>  CFrameWnd::SetProgressBarState  
 Establece el tipo y el estado del indicador de progreso aparece en un botón de barra de tareas.  
  
```  
void SetProgressBarState(TBPFLAG tbpFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 *tbpFlags*  
 Marcas que controlan el estado actual del botón del progreso. Especifique solo uno de los siguientes indicadores porque todos los Estados son mutuamente excluyentes: TBPF_NOPROGRESS, TBPF_INDETERMINATE, TBPF_NORMAL, TBPF_ERROR, TBPF_PAUSED.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="settaskbaroverlayicon"></a>  CFrameWnd::SetTaskbarOverlayIcon  
 Sobrecargado. Se aplica a una superposición a un botón de barra de tareas para indicar el estado de la aplicación o para notificar al usuario.  
  
```  
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,  
    LPCTSTR lpcszDescr);

 
BOOL SetTaskbarOverlayIcon(
    HICON hIcon,  
    LPCTSTR lpcszDescr);
```  
  
### <a name="parameters"></a>Parámetros  
 *nIDResource*  
 Especifica el identificador de recurso de un icono que se usará como la superposición. Consulte la descripción para *hIcon* para obtener más información.  
  
 *lpcszDescr*  
 Un puntero a una cadena que proporciona una versión de texto alternativo de la información transmitida por la superposición, por motivos de accesibilidad.  
  
 *hIcon*  
 El identificador de un icono que se usará como la superposición. Debe tratarse de un icono pequeño, medición de 16 x 16 píxeles a 96 puntos por pulgada (PPP). Si un icono de superposición se ha aplicado el botón de barra de tareas, se reemplazará ese superposición existente. Este valor puede ser NULL. Cómo trata un valor NULL depende de si el botón de barra de tareas representa una sola ventana o un grupo de windows. Es responsabilidad de la aplicación que realiza la llamada para liberar *hIcon* cuando ya no sea necesaria.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se realiza correctamente; FALSE si la versión del sistema operativo es menor que Windows 7 o si se produce un error al establecer el icono.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="settitle"></a>  CFrameWnd::SetTitle  
 Establece el título del objeto de ventana.  
  
```  
void SetTitle(LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszTitle*  
 Un puntero a una cadena de caracteres que contiene el título del objeto de ventana.  
  
##  <a name="showcontrolbar"></a>  CFrameWnd::ShowControlBar  
 Llame a esta función miembro para mostrar u ocultar la barra de control.  
  
```  
void ShowControlBar(
    CControlBar* pBar,  
    BOOL bShow,  
    BOOL bDelay);
```  
  
### <a name="parameters"></a>Parámetros  
 *pBar*  
 Puntero a la barra de control para mostrar u ocultar.  
  
 *bMostrar*  
 Si es TRUE, especifica que se mostrará la barra de control. Si es FALSE, especifica que la barra de control está a punto de ocultarse.  
  
 *bDelay*  
 Si es TRUE, retrasar el mostrar la barra de control. Si es FALSE, se muestra el control de barra inmediatamente.  
  
##  <a name="showownedwindows"></a>  CFrameWnd::ShowOwnedWindows  
 Llame a esta función miembro para mostrar todas las ventanas que son descendientes de los `CFrameWnd` objeto.  
  
```  
void ShowOwnedWindows(BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 *bMostrar*  
 Especifica si las ventanas de propiedad se puede mostrar u ocultar.  
  
## <a name="see-also"></a>Vea también  
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd (clase)](../../mfc/reference/cmdiframewnd-class.md)   
 [CMDIChildWnd (clase)](../../mfc/reference/cmdichildwnd-class.md)   
 [CView (clase)](../../mfc/reference/cview-class.md)   
 [CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)   
 [CRuntimeClass (estructura)](../../mfc/reference/cruntimeclass-structure.md)
