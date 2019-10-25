---
title: CFrameWnd (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: d2e043c8c9f4ad86636cd0e9ea7d695826b6c8fb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506962"
---
# <a name="cframewnd-class"></a>CFrameWnd (clase)

Proporciona la funcionalidad de una ventana de marco de interfaz de un único documento (SDI) de Windows superpuesta o emergente, junto con los miembros para administrar la ventana.

## <a name="syntax"></a>Sintaxis

```
class CFrameWnd : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFrameWnd::CFrameWnd](#cframewnd)|Construye un objeto `CFrameWnd`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFrameWnd::ActivateFrame](#activateframe)|Hace que el marco esté visible y disponible para el usuario.|
|[CFrameWnd::BeginModalState](#beginmodalstate)|Establece la ventana de marco en modal.|
|[CFrameWnd::Create](#create)|Llame a para crear e inicializar la ventana de marco de `CFrameWnd` Windows asociada al objeto.|
|[CFrameWnd::CreateView](#createview)|Crea una vista dentro de un marco que no se deriva `CView`de.|
|[CFrameWnd::DockControlBar](#dockcontrolbar)|Acopla una barra de control.|
|[CFrameWnd::EnableDocking](#enabledocking)|Permite acoplar una barra de controles.|
|[CFrameWnd::EndModalState](#endmodalstate)|Finaliza el estado modal de la ventana de marco. Habilita todas las ventanas deshabilitadas `BeginModalState`por.|
|[CFrameWnd::FloatControlBar](#floatcontrolbar)|Flota una barra de controles.|
|[CFrameWnd::GetActiveDocument](#getactivedocument)|Devuelve el objeto `CDocument` activo.|
|[CFrameWnd::GetActiveFrame](#getactiveframe)|Devuelve el objeto `CFrameWnd` activo.|
|[CFrameWnd::GetActiveView](#getactiveview)|Devuelve el objeto `CView` activo.|
|[CFrameWnd::GetControlBar](#getcontrolbar)|Recupera la barra de controles.|
|[CFrameWnd::GetDockState](#getdockstate)|Recupera el estado de acoplamiento de una ventana de marco.|
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|Recupera el estado de visualización del menú en la aplicación MFC actual.|
|[CFrameWnd::GetMenuBarVisibility](#getmenubarvisibility)|Indica si el comportamiento predeterminado del menú en la aplicación MFC actual está oculto o visible.|
|[CFrameWnd::GetMessageBar](#getmessagebar)|Devuelve un puntero a la barra de estado que pertenece a la ventana de marco.|
|[CFrameWnd::GetMessageString](#getmessagestring)|Recupera el mensaje correspondiente a un identificador de comando.|
|[CFrameWnd::GetTitle](#gettitle)|Recupera el título de la barra de control relacionada.|
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|Hace que `OnInitialUpdate` se llame a la función miembro que pertenece a todas las vistas de la ventana de marco.|
|[CFrameWnd::InModalState](#inmodalstate)|Devuelve un valor que indica si una ventana de marco está en un estado modal.|
|[CFrameWnd::IsTracking](#istracking)|Determina si la barra de división se está moviendo actualmente.|
|[CFrameWnd::LoadAccelTable](#loadacceltable)|Llame a para cargar una tabla de aceleradores.|
|[CFrameWnd::LoadBarState](#loadbarstate)|Llame a para restaurar la configuración de la barra de control.|
|[CFrameWnd::LoadFrame](#loadframe)|Llame a para crear dinámicamente una ventana de marco a partir de la información de recursos.|
|[CFrameWnd::NegotiateBorderSpace](#negotiateborderspace)|Negocia el espacio de borde en la ventana de marco.|
|[CFrameWnd::OnBarCheck](#onbarcheck)|Se llama siempre que se realiza una acción en la barra de control especificada.|
|[CFrameWnd::OnContextHelp](#oncontexthelp)|Controla la ayuda Mayús + F1 para los elementos en contexto.|
|[CFrameWnd::OnSetPreviewMode](#onsetpreviewmode)|Establece la ventana de marco principal de la aplicación dentro y fuera del modo de vista previa de impresión.|
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|Lo llama el marco de trabajo cuando se actualiza el menú asociado.|
|[CFrameWnd::RecalcLayout](#recalclayout)|Cambia la posición de las barras de control `CFrameWnd` del objeto.|
|[CFrameWnd::SaveBarState](#savebarstate)|Llame a para guardar la configuración de la barra de control.|
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|Designa la vista especificada para que sea la vista activa para la vista previa enriquecida.|
|[CFrameWnd::SetActiveView](#setactiveview)|Establece el objeto `CView` activo.|
|[CFrameWnd::SetDockState](#setdockstate)|Llame a para acoplar la ventana de marco en la ventana principal.|
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|Establece el estado de visualización del menú en la aplicación MFC actual en oculto o mostrado.|
|[CFrameWnd::SetMenuBarVisibility](#setmenubarvisibility)|Establece el comportamiento predeterminado del menú en la aplicación MFC actual para que esté oculto o visible.|
|[CFrameWnd::SetMessageText](#setmessagetext)|Establece el texto de una barra de estado estándar.|
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|Establece la posición actual de la barra de progreso de Windows 7 mostrada en la barra de tareas.|
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|Establece el intervalo de la barra de progreso de Windows 7 en la barra de tareas.|
|[CFrameWnd::SetProgressBarState](#setprogressbarstate)|Establece el tipo y el estado del indicador de progreso mostrado en un botón de la barra de tareas.|
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|Sobrecargado. Aplica una superposición a un botón de la barra de tareas para indicar el estado de la aplicación o una notificación al usuario.|
|[CFrameWnd::SetTitle](#settitle)|Establece el título de la barra de control relacionada.|
|[CFrameWnd::ShowControlBar](#showcontrolbar)|Llame a para mostrar la barra de control.|
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|Muestra todas las ventanas que son descendientes del `CFrameWnd` objeto.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFrameWnd::OnCreateClient](#oncreateclient)|Crea una ventana de cliente para el marco.|
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|Se llama antes de que se oculte el menú de la aplicación MFC actual.|
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|Se llama antes de que se muestre el menú de la aplicación MFC actual.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|Controla la funcionalidad de habilitar y deshabilitar automática para los elementos de menú.|
|[CFrameWnd::rectDefault](#rectdefault)|Pase este estático `CRect` como parámetro al crear un `CFrameWnd` objeto para permitir que Windows elija el tamaño inicial y la posición de la ventana.|

## <a name="remarks"></a>Comentarios

Para crear una ventana de marco útil para la aplicación, derive una clase `CFrameWnd`de. Agregue variables de miembro a la clase derivada para almacenar datos específicos de la aplicación. Implemente funciones miembro de controlador de mensajes y un mapa de mensajes en la clase derivada para especificar qué ocurre cuando los mensajes se dirigen a la ventana.

Hay tres formas de crear una ventana de marco:

- Construya directamente mediante [Create](#create).

- Construya directamente mediante [LoadFrame](#loadframe).

- Construya indirectamente mediante una plantilla de documento.

Antes de llamar a `Create` o `LoadFrame`, debe construir el objeto de ventana de marco en el montón mediante el C++ operador **New** . Antes de `Create`llamar a, también puede registrar una clase de ventana con la función global [AfxRegisterWndClass (](../../mfc/reference/application-information-and-management.md#afxregisterwndclass) para establecer el icono y los estilos de clase para el marco.

Utilice la `Create` función miembro para pasar los parámetros de creación del marco como argumentos inmediatos.

`LoadFrame`requiere menos argumentos que `Create`y, en su lugar, recupera la mayoría de los valores predeterminados de los recursos, incluidos el título, el icono, la tabla de aceleradores y el menú del marco. Para que sea accesible `LoadFrame`para, todos estos recursos deben tener el mismo identificador de recurso (por ejemplo, IDR_MAINFRAME).

Cuando un `CFrameWnd` objeto contiene vistas y documentos, el marco de trabajo los crea indirectamente en lugar de hacerlo directamente por el programador. El `CDocTemplate` objeto orquesta la creación del marco, la creación de las vistas contenedoras y la conexión de las vistas al documento adecuado. Los parámetros del `CDocTemplate` constructor especifican el `CRuntimeClass` de las tres clases implicadas (documento, marco y vista). El `CRuntimeClass` marco de trabajo usa un objeto para crear dinámicamente nuevos marcos cuando lo especifica el usuario (por ejemplo, con el comando archivo nuevo o la ventana de interfaz de múltiples documentos (MDI) nuevo comando).

Una clase de ventana de marco derivada `CFrameWnd` de se debe declarar con DECLARE_DYNCREATE para que el mecanismo de RUNTIME_CLASS anterior funcione correctamente.

`CFrameWnd` Contiene implementaciones predeterminadas para realizar las siguientes funciones de una ventana principal en una aplicación típica de Windows:

- Una `CFrameWnd` ventana de marco realiza un seguimiento de una vista activa que es independiente de la ventana activa de Windows o del foco de entrada actual. Cuando se reactiva el marco, se notifica a la vista activa mediante una `CView::OnActivateView`llamada a.

- Los mensajes de comandos y muchos mensajes comunes de notificación de fotogramas, `OnSetFocus`incluidos `OnHScroll`los administrados por `CWnd`las funciones, y `OnVScroll` de, `CFrameWnd` se delegan mediante una ventana de marco en la vista activa.

- La vista activa (o la ventana de marco MDI secundario actualmente activa en el caso de un marco MDI) puede determinar el título de la ventana de marco. Esta característica se puede deshabilitar desactivando el bit de estilo FWS_ADDTOTITLE de la ventana de marco.

- Una `CFrameWnd` ventana de marco administra la posición de las barras de control, las vistas y otras ventanas secundarias dentro del área de cliente de la ventana de marco. Una ventana de marco también realiza la actualización en tiempo de inactividad de la barra de herramientas y otros botones de barra de control. Una `CFrameWnd` ventana de marco también tiene implementaciones predeterminadas de comandos para activar o desactivar la barra de herramientas y la barra de estado.

- Una `CFrameWnd` ventana de marco administra la barra de menús principal. Cuando se muestra un menú emergente, la ventana marco utiliza el mecanismo UPDATE_COMMAND_UI para determinar qué elementos de menú deben habilitarse, deshabilitarse o comprobarse. Cuando el usuario selecciona un elemento de menú, la ventana de marco actualiza la barra de estado con la cadena de mensaje de ese comando.

- Una `CFrameWnd` ventana de marco tiene una tabla de aceleradores opcional que traduce automáticamente los aceleradores de teclado.

- Una `CFrameWnd` ventana de marco tiene un conjunto de identificadores `LoadFrame` de ayuda opcional con que se utiliza para la ayuda contextual. Una ventana de marco es el orquestador principal de Estados semimodales, como la ayuda contextual (Mayús + F1) y los modos de vista previa de impresión.

- Una `CFrameWnd` ventana de marco abrirá un archivo arrastrado desde el administrador de archivos y se colocará en la ventana de marco. Si una extensión de archivo está registrada y asociada a la aplicación, la ventana de marco responde a la solicitud Open de intercambio dinámico de datos (DDE) que se produce cuando el usuario abre un archivo de datos en el `ShellExecute` administrador de archivos o cuando se llama a la función de Windows.

- Si la ventana de marco es la ventana principal de la aplicación ( `CWinThread::m_pMainWnd`es decir,) cuando el usuario cierra la aplicación, la ventana marco solicita al usuario que guarde los documentos modificados ( `OnClose` para `OnQueryEndSession`y).

- Si la ventana de marco es la ventana principal de la aplicación, la ventana marco es el contexto para ejecutar WinHelp. Al cerrar la ventana de marco, se cerrará WINHELP. EXE si se inició para obtener ayuda para esta aplicación.

No use el C++ operador **Delete** para destruir una ventana de marco. Utilice `CWnd::DestroyWindow` en su lugar. La `CFrameWnd` implementación de `PostNcDestroy` eliminará el C++ objeto cuando se destruya la ventana. Cuando el usuario cierra la ventana de marco, el controlador `OnClose` predeterminado llamará `DestroyWindow`a.

Para obtener más información `CFrameWnd`sobre, consulte [ventanas de marco](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CFrameWnd`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="activateframe"></a>  CFrameWnd::ActivateFrame

Llame a esta función miembro para activar y restaurar la ventana de marco de modo que esté visible y disponible para el usuario.

```
virtual void ActivateFrame(int nCmdShow = -1);
```

### <a name="parameters"></a>Parámetros

*nCmdShow*<br/>
Especifica el parámetro que se va a pasar a [CWnd:: ShowWindow](../../mfc/reference/cwnd-class.md#showwindow). De forma predeterminada, el marco se muestra y se restaura correctamente.

### <a name="remarks"></a>Comentarios

Normalmente, se llama a esta función miembro después de un evento de interfaz que no es de usuario, como un DDE, OLE u otro evento que puede mostrar la ventana de marco o su contenido al usuario.

La implementación predeterminada activa el marco y lo coloca en la parte superior del orden Z y, si es necesario, realiza los mismos pasos para la ventana de marco principal de la aplicación.

Invalide esta función miembro para cambiar el modo en que se activa un marco. Por ejemplo, puede forzar la maximización de las ventanas secundarias de MDI. Agregue la funcionalidad adecuada y, a continuación, llame a la versión de la clase base con una *nCmdShow*explícita.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]

##  <a name="beginmodalstate"></a>  CFrameWnd::BeginModalState

Llame a esta función miembro para convertir una ventana marco en modal.

```
virtual void BeginModalState();
```

##  <a name="cframewnd"></a>  CFrameWnd::CFrameWnd

Construye un `CFrameWnd` objeto, pero no crea la ventana de marco visible.

```
CFrameWnd();
```

### <a name="remarks"></a>Comentarios

Llame `Create` a para crear la ventana visible.

##  <a name="create"></a>  CFrameWnd::Create

Llame a para crear e inicializar la ventana de marco de `CFrameWnd` Windows asociada al objeto.

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

*lpszClassName*<br/>
Apunta a una cadena de caracteres terminada en null que nombra la clase de Windows. El nombre de clase puede ser cualquier nombre registrado con `AfxRegisterWndClass` la función global o `RegisterClass` la función de Windows. Si es null, utiliza los atributos predeterminados `CFrameWnd` predefinidos.

*lpszWindowName*<br/>
Apunta a una cadena de caracteres terminada en null que representa el nombre de la ventana. Se usa como texto para la barra de título.

*dwStyle*<br/>
Especifica los atributos de [estilo](../../mfc/reference/styles-used-by-mfc.md#window-styles) de ventana. Incluya el estilo FWS_ADDTOTITLE si desea que la barra de título muestre automáticamente el nombre del documento representado en la ventana.

*rect*<br/>
Especifica el tamaño y la posición de la ventana. El valor *rectDefault* permite a Windows especificar el tamaño y la posición de la nueva ventana.

*pParentWnd*<br/>
Especifica la ventana primaria de esta ventana de marco. Este parámetro debe ser NULL para las ventanas de marco de nivel superior.

*lpszMenuName*<br/>
Identifica el nombre del recurso de menú que se va a usar con la ventana. Use MAKEINTRESOURCE si el menú tiene un identificador entero en lugar de una cadena. Este parámetro puede ser NULL.

*dwExStyle*<br/>
Especifica los atributos de [estilo](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) extendido de ventana.

*pContext*<br/>
Especifica un puntero a una estructura [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) . Este parámetro puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización es correcta; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Construya un `CFrameWnd` objeto en dos pasos. En primer lugar, invoque el constructor, que `CFrameWnd` construye el objeto y, `Create`a continuación, llame a, que crea la ventana de marco de `CFrameWnd` Windows y la adjunta al objeto. `Create`Inicializa el nombre de clase y el nombre de la ventana de la ventana y registra los valores predeterminados para su estilo, elemento primario y menú asociado.

`LoadFrame` Use`Create` en lugar de para cargar la ventana de marco desde un recurso en lugar de especificar sus argumentos.

##  <a name="createview"></a>  CFrameWnd::CreateView

Llame `CreateView` a para crear una vista dentro de un marco.

```
CWnd* CreateView(
    CCreateContext* pContext,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Parámetros

*pContext*<br/>
Especifica el tipo de vista y documento.

*nID*<br/>
El número de identificación de una vista.

### <a name="return-value"></a>Valor devuelto

Puntero a un `CWnd` objeto si es correcto; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Utilice esta función miembro para crear "vistas" que no `CView`se deriven de un marco. Después de `CreateView`llamar a, debe establecer manualmente la vista en Active y establecerla para que sea visible; estas tareas no las `CreateView`realiza automáticamente.

##  <a name="dockcontrolbar"></a>  CFrameWnd::DockControlBar

Hace que una barra de controles esté acoplada a la ventana de marco.

```
void DockControlBar(
    CControlBar* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
Apunta a la barra de control que se va a acoplar.

*nDockBarID*<br/>
Determina qué lados de la ventana de marco se deben tener en cuenta para el acoplamiento. Puede ser 0 o uno o varios de los siguientes:

- AFX_IDW_DOCKBAR_TOP acoplar en el lado superior de la ventana de marco.

- AFX_IDW_DOCKBAR_BOTTOM acoplar en el lado inferior de la ventana de marco.

- AFX_IDW_DOCKBAR_LEFT acoplar en el lado izquierdo de la ventana de marco.

- AFX_IDW_DOCKBAR_RIGHT acoplar en el lado derecho de la ventana de marco.

Si es 0, la barra de control se puede acoplar a cualquier lado habilitado para el acoplamiento en la ventana de marco de destino.

*lpRect*<br/>
Determina, en coordenadas de pantalla, dónde se acoplará la barra de control en el área no cliente de la ventana de marco de destino.

### <a name="remarks"></a>Comentarios

La barra de control se acoplará a uno de los lados de la ventana de marco especificada en las llamadas a [CControlBar:: EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking) y [CFrameWnd:: EnableDocking](#enabledocking). El lado elegido viene determinado por *nDockBarID*.

##  <a name="enabledocking"></a>  CFrameWnd::EnableDocking

Llame a esta función para habilitar las barras de control acoplables en una ventana de marco.

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parámetros

*dwDockStyle*<br/>
Especifica qué lados de la ventana de marco pueden servir como sitios de acoplamiento para las barras de control. Puede ser uno o varios de los siguientes:

- CBRS_ALIGN_TOP permite el acoplamiento en la parte superior del área cliente.

- CBRS_ALIGN_BOTTOM permite el acoplamiento en la parte inferior del área cliente.

- CBRS_ALIGN_LEFT permite el acoplamiento en el lado izquierdo del área cliente.

- CBRS_ALIGN_RIGHT permite el acoplamiento en el lado derecho del área de cliente.

- CBRS_ALIGN_ANY permite el acoplamiento en cualquier lado del área de cliente.

### <a name="remarks"></a>Comentarios

De forma predeterminada, las barras de control se acoplarán a un lado de la ventana de marco en el siguiente orden: superior, inferior, izquierda, derecha.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CToolBar:: Create](../../mfc/reference/ctoolbar-class.md#create).

##  <a name="endmodalstate"></a>  CFrameWnd::EndModalState

Llame a esta función miembro para cambiar una ventana marco de modal a no modal.

```
virtual void EndModalState();
```

### <a name="remarks"></a>Comentarios

`EndModalState`habilita todas las ventanas deshabilitadas por [BeginModalState](#beginmodalstate).

##  <a name="floatcontrolbar"></a>  CFrameWnd::FloatControlBar

Llame a esta función para que una barra de control no esté acoplada a la ventana de marco.

```
void FloatControlBar(
    CControlBar* pBar,
    CPoint point,
    DWORD dwStyle = CBRS_ALIGN_TOP);
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
Apunta a la barra de control que se va a flotar.

*point*<br/>
Ubicación, en coordenadas de la pantalla, donde se colocará la esquina superior izquierda de la barra de control.

*dwStyle*<br/>
Especifica si la barra de controles se va a alinear horizontal o verticalmente dentro de la nueva ventana de marco. Puede ser cualquiera de los siguientes:

- CBRS_ALIGN_TOP orienta verticalmente la barra de control.

- CBRS_ALIGN_BOTTOM orienta verticalmente la barra de control.

- CBRS_ALIGN_LEFT orienta horizontalmente la barra de controles.

- CBRS_ALIGN_RIGHT orienta horizontalmente la barra de controles.

Si se pasan estilos que especifican la orientación horizontal y vertical, la barra de herramientas se orientará horizontalmente.

### <a name="remarks"></a>Comentarios

Normalmente, esto se hace al inicio de la aplicación cuando el programa restaura la configuración de la ejecución anterior.

El marco de trabajo llama a esta función cuando el usuario produce una operación de colocar soltando el botón primario del mouse mientras arrastra la barra de control por una ubicación que no está disponible para el acoplamiento.

##  <a name="getactivedocument"></a>  CFrameWnd::GetActiveDocument

Llame a esta función miembro para obtener un puntero al actual `CDocument` asociado a la vista activa actual.

```
virtual CDocument* GetActiveDocument();
```

### <a name="return-value"></a>Valor devuelto

Puntero al [CDocument](../../mfc/reference/cdocument-class.md)actual. Si no hay ningún documento actual, devuelve NULL.

##  <a name="getactiveframe"></a>  CFrameWnd::GetActiveFrame

Llame a esta función miembro para obtener un puntero a la ventana secundaria de la interfaz de múltiples documentos (MDI) activa de una ventana de marco MDI.

```
virtual CFrameWnd* GetActiveFrame();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la ventana secundaria MDI activa. Si la aplicación es una aplicación SDI o la ventana de marco MDI no tiene ningún documento activo, se devolverá el puntero **this** implícito.

### <a name="remarks"></a>Comentarios

Si no hay ningún elemento secundario MDI activo o si la aplicación es una interfaz de un único documento (SDI), se devuelve el puntero **this** implícito.

##  <a name="getactiveview"></a>  CFrameWnd::GetActiveView

Llame a esta función miembro para obtener un puntero a la vista activa (si existe) adjunta a una ventana de `CFrameWnd`marco ().

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a la [CView](../../mfc/reference/cview-class.md)actual. Si no hay ninguna vista actual, devuelve NULL.

### <a name="remarks"></a>Comentarios

Esta función devuelve NULL cuando se llama para una ventana de marco principal `CMDIFrameWnd`MDI (). En una aplicación MDI, la ventana marco principal MDI no tiene una vista asociada. En su lugar, cada ventana secundaria individual `CMDIChildWnd`() tiene una o varias vistas asociadas. La vista activa en una aplicación MDI se puede obtener buscando primero la ventana secundaria MDI activa y después buscando la vista activa para esa ventana secundaria. La ventana secundaria MDI activa se puede encontrar mediante una llamada a `MDIGetActive` la `GetActiveFrame` función o como se muestra a continuación:

[!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]

##  <a name="getcontrolbar"></a>  CFrameWnd::GetControlBar

Llame `GetControlBar` a para obtener acceso a la barra de control que está asociada con el identificador.

```
CControlBar* GetControlBar(UINT nID);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
El número de identificación de una barra de control.

### <a name="return-value"></a>Valor devuelto

Puntero a la barra de control que está asociada con el identificador.

### <a name="remarks"></a>Comentarios

El parámetro *nID* hace referencia al identificador único que se pasa al `Create` método de la barra de control. Para obtener más información acerca de las barras de control, consulte el tema titulado [barras de control](../../mfc/control-bars.md).

`GetControlBar`devolverá la barra de control incluso si es flotante y, por lo tanto, no es actualmente una ventana secundaria del marco.

##  <a name="getdockstate"></a>  CFrameWnd::GetDockState

Llame a esta función miembro para almacenar información de estado sobre las barras de control de la `CDockState` ventana de marco en un objeto.

```
void GetDockState(CDockState& state) const;
```

### <a name="parameters"></a>Parámetros

*state*<br/>
Contiene el estado actual de las barras de control de la ventana de marco después de la devolución.

### <a name="remarks"></a>Comentarios

Después, puede escribir el contenido de `CDockState` en el almacenamiento `CDockState::SaveState` mediante `Serialize`o. Si más adelante desea restaurar las barras de control a un estado anterior, cargue el estado con `CDockState::LoadState` o `Serialize`y, a `SetDockState` continuación, llame a para aplicar el estado anterior a las barras de control de la ventana de marco.

##  <a name="getmenubarstate"></a>  CFrameWnd::GetMenuBarState

Recupera el estado de visualización del menú en la aplicación MFC actual.

```
virtual DWORD GetMenuBarState();
```

### <a name="return-value"></a>Valor devuelto

El valor devuelto puede tener los valores siguientes:

- AFX_MBS_VISIBLE (0x01): el menú está visible.

- AFX_MBS_HIDDEN (0x02): el menú está oculto.

### <a name="remarks"></a>Comentarios

Si se produce un error en tiempo de ejecución, este método se valida en modo de depuración y genera una excepción derivada de la clase [CException](../../mfc/reference/cexception-class.md) .

##  <a name="getmenubarvisibility"></a>  CFrameWnd::GetMenuBarVisibility

Indica si el estado predeterminado del menú en la aplicación MFC actual está oculto o visible.

```
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```

### <a name="return-value"></a>Valor devuelto

Este método devuelve uno de los siguientes valores:

- AFX_MBV_KEEPVISIBLE (0x01): el menú se muestra en todo momento y, de forma predeterminada, no tiene el foco.

- AFX_MBV_DISPLAYONFOCUS (0x02): el menú está oculto de forma predeterminada. Si el menú está oculto, presione la tecla ALT para mostrar el menú y asígnele el foco. Si se muestra el menú, presione la tecla ALT o ESC para ocultarlo.

- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04) (combinación bit a bit (o)): el menú está oculto de forma predeterminada. Si el menú está oculto, presione la tecla F10 para mostrar el menú y darle el foco. Si se muestra el menú, presione la tecla F10 para activar o desactivar el menú. El menú se mostrará hasta que presione la tecla ALT o ESC para ocultarlo.

### <a name="remarks"></a>Comentarios

Si se produce un error en tiempo de ejecución, este método se valida en modo de depuración y genera una excepción derivada de la clase [CException](../../mfc/reference/cexception-class.md) .

##  <a name="getmessagebar"></a>  CFrameWnd::GetMessageBar

Llame a esta función miembro para obtener un puntero a la barra de estado.

```
virtual CWnd* GetMessageBar();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la ventana de la barra de estado.

##  <a name="getmessagestring"></a>  CFrameWnd::GetMessageString

Invalide esta función para proporcionar cadenas personalizadas para los identificadores de comando.

```
virtual void GetMessageString(
    UINT nID,
    CString& rMessage) const;
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
IDENTIFICADOR de recurso del mensaje deseado.

*rMessage*<br/>
`CString`objeto en el que se va a colocar el mensaje.

### <a name="remarks"></a>Comentarios

La implementación predeterminada simplemente carga la cadena especificada por *nID* desde el archivo de recursos. El marco de trabajo llama a esta función cuando se necesita actualizar la cadena de mensaje en la barra de estado.

##  <a name="gettitle"></a>  CFrameWnd::GetTitle

Recupera el título del objeto Window.

```
CString GetTitle() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene el título actual del objeto Window.

##  <a name="initialupdateframe"></a>  CFrameWnd::InitialUpdateFrame

Llame `IntitialUpdateFrame` al método después de crear un `Create`nuevo marco con.

```
void InitialUpdateFrame(
    CDocument* pDoc,
    BOOL bMakeVisible);
```

### <a name="parameters"></a>Parámetros

*pDoc*<br/>
Apunta al documento al que está asociada la ventana de marco. Puede ser NULL.

*bMakeVisible*<br/>
Si es TRUE, indica que el marco debe ser visible y activo. Si es FALSE, no se hacen visibles los descendientes.

### <a name="remarks"></a>Comentarios

Esto hace que todas las vistas de la ventana de marco `OnInitialUpdate` reciban sus llamadas.

Además, si no había anteriormente una vista activa, la vista principal de la ventana de marco se activa. La vista principal es una vista con un identificador secundario de AFX_IDW_PANE_FIRST. Por último, la ventana de marco se hace visible si *bMakeVisible* es distinto de cero. Si *bMakeVisible* es 0, el foco actual y el estado visible de la ventana de marco permanecerán sin cambios. No es necesario llamar a esta función cuando se usa la implementación del archivo New y el archivo Open del marco de trabajo.

##  <a name="inmodalstate"></a>  CFrameWnd::InModalState

Llame a esta función miembro para comprobar si una ventana de marco es modal o no modal.

```
BOOL InModalState() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero en caso afirmativo; de lo contrario, es 0.

##  <a name="istracking"></a>  CFrameWnd::IsTracking

Llame a esta función miembro para determinar si la barra divisora de la ventana se está moviendo actualmente.

```
BOOL IsTracking() const;
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si hay una operación de divisor en curso; de lo contrario, es 0.

##  <a name="loadacceltable"></a>  CFrameWnd::LoadAccelTable

Llame a para cargar la tabla de aceleradores especificada.

```
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```

### <a name="parameters"></a>Parámetros

*lpszResourceName*<br/>
Identifica el nombre del recurso de acelerador. Use MAKEINTRESOURCE si el recurso se identifica con un identificador entero.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la tabla de aceleradores se cargó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Solo se puede cargar una tabla a la vez.

Las tablas de aceleradores cargados desde los recursos se liberan automáticamente cuando finaliza la aplicación.

Si llama `LoadFrame` a para crear la ventana de marco, el marco de trabajo carga una tabla de aceleradores junto con los recursos de menú y icono, y una llamada subsiguiente a esta función miembro es innecesaria.

##  <a name="loadbarstate"></a>  CFrameWnd::LoadBarState

Llame a esta función para restaurar los valores de cada barra de control propiedad de la ventana de marco.

```
void LoadBarState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
Nombre de una sección del archivo de inicialización (INI) o una clave en el registro de Windows donde se almacena la información de estado.

### <a name="remarks"></a>Comentarios

La información restaurada incluye visibilidad, orientación horizontal o vertical, estado de acoplamiento y posición de la barra de control.

La configuración que desea restaurar se debe escribir en el registro antes de llamar `LoadBarState`a. Escriba la información en el registro llamando a [CWinApp:: SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey). Escriba la información en el archivo INI mediante una llamada a [SaveBarState](#savebarstate).

##  <a name="loadframe"></a>  CFrameWnd::LoadFrame

Llame a para crear dinámicamente una ventana de marco a partir de la información de recursos.

```
virtual BOOL LoadFrame(
    UINT nIDResource,
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,
    CWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parámetros

*nIDResource*<br/>
IDENTIFICADOR de recursos compartidos asociados a la ventana de marco.

*dwDefaultStyle*<br/>
[Estilo](../../mfc/reference/styles-used-by-mfc.md#window-styles)del marco. Incluya el estilo FWS_ADDTOTITLE si desea que la barra de título muestre automáticamente el nombre del documento representado en la ventana.

*pParentWnd*<br/>
Puntero al elemento primario del marco.

*pContext*<br/>
Puntero a una estructura [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) . Este parámetro puede ser NULL.

### <a name="remarks"></a>Comentarios

Construya un `CFrameWnd` objeto en dos pasos. En primer lugar, invoque el constructor, que `CFrameWnd` construye el objeto y, `LoadFrame`a continuación, llame a, que carga la ventana de marco de Windows y los recursos asociados `CFrameWnd` y adjunta la ventana de marco al objeto. El parámetro *nIDResource* especifica el menú, la tabla de aceleradores, el icono y el recurso de cadena del título de la ventana de marco.

Utilice la `Create` función miembro en lugar `LoadFrame` de cuando desee especificar todos los parámetros de creación de la ventana de marco.

El marco de `LoadFrame` trabajo llama a cuando crea una ventana de marco mediante un objeto de plantilla de documento.

El marco de trabajo usa el argumento *pContext* para especificar los objetos que se van a conectar a la ventana de marco, incluidos los objetos de vista incluidos. Puede establecer el argumento *pContext* en NULL cuando llame `LoadFrame`a.

##  <a name="m_bautomenuenable"></a>  CFrameWnd::m_bAutoMenuEnable

Cuando este miembro de datos está habilitado (que es el valor predeterminado), los elementos de menú que no tienen controladores ON_UPDATE_COMMAND_UI o ON_COMMAND se deshabilitan automáticamente cuando el usuario extrae un menú.

```
BOOL m_bAutoMenuEnable;
```

### <a name="remarks"></a>Comentarios

Los elementos de menú que tienen un controlador ON_COMMAND pero ningún controlador ON_UPDATE_COMMAND_UI se habilitarán automáticamente.

Cuando se establece este miembro de datos, los elementos de menú se habilitan automáticamente de la misma manera que se habilitan los botones de la barra de herramientas.

> [!NOTE]
> `m_bAutoMenuEnable`no tiene ningún efecto en los elementos de menú de nivel superior.

Este miembro de datos simplifica la implementación de comandos opcionales basados en la selección actual y reduce la necesidad de escribir controladores ON_UPDATE_COMMAND_UI para habilitar y deshabilitar elementos de menú.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]

##  <a name="negotiateborderspace"></a>  CFrameWnd::NegotiateBorderSpace

Llame a esta función miembro para negociar el espacio de borde en una ventana de marco durante la activación de OLE en contexto.

```
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,
    LPRECT lpRectBorder);
```

### <a name="parameters"></a>Parámetros

*nBorderCmd*<br/>
Contiene uno de los siguientes valores de `enum BorderCmd`:

- `borderGet` = 1

- `borderRequest` = 2

- `borderSet` = 3

*lpRectBorder*<br/>
Puntero a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) o un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) que especifica las coordenadas del borde.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro es la `CFrameWnd` implementación de la negociación de espacio del borde OLE.

##  <a name="onbarcheck"></a>  CFrameWnd::OnBarCheck

Se llama siempre que se realiza una acción en la barra de control especificada.

```
afx_msg BOOL OnBarCheck(UINT nID);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
IDENTIFICADOR de la barra de control que se va a mostrar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la barra de control existía; de lo contrario, es 0.

##  <a name="oncontexthelp"></a>  CFrameWnd::OnContextHelp

Controla la ayuda Mayús + F1 para los elementos en contexto.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>Comentarios

Para habilitar la ayuda contextual, debe agregar un

[!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]

en el `CFrameWnd` mapa de mensajes de clase y también agregue una entrada de tabla de aceleradores, normalmente Mayús + F1, para habilitar esta función miembro.

Si la aplicación es un contenedor OLE, `OnContextHelp` coloca todos los elementos en contexto contenidos en el objeto de ventana marco en el modo de ayuda. El cursor cambia a una flecha y un signo de interrogación, y el usuario puede desplace el puntero del mouse y presionar el botón primario del mouse para seleccionar un cuadro de diálogo, ventana, menú o botón de comando. Esta función miembro llama a la función `WinHelp` de Windows con el contexto de ayuda del objeto bajo el cursor.

##  <a name="oncreateclient"></a>  CFrameWnd::OnCreateClient

Lo llama el marco de trabajo durante la `OnCreate`ejecución de.

```
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parámetros

*lpcs*<br/>
Puntero a una estructura [CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw) de Windows.

*pContext*<br/>
Puntero a una estructura [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) .

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

No llame nunca a esta función.

La implementación predeterminada de esta función crea un `CView` objeto a partir de la información proporcionada en *pContext*, si es posible.

Invalide esta función para invalidar los `CCreateContext` valores pasados en el objeto o para cambiar la manera en que se crean los controles del área cliente principal de la ventana de marco. Los `CCreateContext` miembros que se pueden invalidar se describen en la clase [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) .

> [!NOTE]
>  No reemplace los valores pasados en la `CREATESTRUCT` estructura. Solo son para uso informativo. Si desea invalidar el rectángulo inicial de la ventana, por ejemplo, reemplace `CWnd` la función miembro [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).

##  <a name="onhidemenubar"></a>  CFrameWnd::OnHideMenuBar

Se llama a esta función cuando el sistema está a punto de ocultar la barra de menús de la aplicación MFC actual.

```
virtual void OnHideMenuBar();
```

### <a name="remarks"></a>Comentarios

Este controlador de eventos permite a la aplicación realizar acciones personalizadas cuando el sistema está a punto de ocultar el menú. No puede evitar que el menú se oculte, pero puede, por ejemplo, llamar a otros métodos para recuperar el estilo de menú o el estado.

##  <a name="onsetpreviewmode"></a>  CFrameWnd::OnSetPreviewMode

Llame a esta función miembro para establecer la ventana de marco principal de la aplicación dentro y fuera del modo de vista previa de impresión.

```
virtual void OnSetPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>Parámetros

*bPreview*<br/>
Especifica si se va a colocar la aplicación en modo de vista previa de impresión. Establézcalo en TRUE para colocar en la vista previa de impresión, FALSE para cancelar el modo de vista previa.

*pState*<br/>
Puntero a una `CPrintPreviewState` estructura.

### <a name="remarks"></a>Comentarios

La implementación predeterminada deshabilita todas las barras de herramientas estándar y oculta el menú principal y la ventana de cliente principal. Esto convierte las ventanas de marco MDI en ventanas de marco SDI temporales.

Invalide esta función miembro para personalizar la ocultación y visualización de las barras de control y otras partes de la ventana de marco durante la vista previa de impresión. Llame a la implementación de la clase base desde la versión invalidada.

##  <a name="onshowmenubar"></a>  CFrameWnd::OnShowMenuBar

Se llama a esta función cuando el sistema está a punto de mostrar la barra de menús en la aplicación MFC actual.

```
virtual void OnShowMenuBar();
```

### <a name="remarks"></a>Comentarios

Este controlador de eventos permite que la aplicación realice acciones personalizadas cuando el menú está a punto de mostrarse. No puede evitar que se muestre el menú, pero puede, por ejemplo, llamar a otros métodos para recuperar el estilo o el estado del menú.

##  <a name="onupdatecontrolbarmenu"></a>  CFrameWnd::OnUpdateControlBarMenu

Lo llama el marco de trabajo cuando se actualiza el menú asociado.

```
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Un puntero a un objeto [CCmdUI](../../mfc/reference/ccmdui-class.md) que representa el menú que generó el comando UPDATE. El controlador de actualización llama a la función miembro [enable](../../mfc/reference/ccmdui-class.md#enable) del `CCmdUI` objeto a través de *pCmdUI* para actualizar la interfaz de usuario.

##  <a name="recalclayout"></a>  CFrameWnd::RecalcLayout

Lo llama el marco de trabajo cuando se activan o desactivan las barras de control estándar o cuando se cambia el tamaño de la ventana de marco.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parámetros

*bNotify*<br/>
Determina si el elemento activo en contexto de la ventana de marco recibe una notificación del cambio de diseño. Si es TRUE, se notifica al elemento; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de esta función miembro llama a `CWnd` la función `RepositionBars` miembro para cambiar la posición de todas las barras de control en el marco, así como en la ventana de `CView` cliente principal (normalmente, o MdiClient).

Invalide esta función miembro para controlar la apariencia y el comportamiento de las barras de control después de que haya cambiado el diseño de la ventana de marco. Por ejemplo, llámelo al activar o desactivar las barras de control o agregar otra barra de control.

##  <a name="rectdefault"></a>  CFrameWnd::rectDefault

Pase este estático `CRect` como parámetro al crear una ventana para permitir que Windows elija el tamaño inicial y la posición de la ventana.

```
static AFX_DATA const CRect rectDefault;
```

##  <a name="savebarstate"></a>  CFrameWnd::SaveBarState

Llame a esta función para almacenar información sobre cada barra de control propiedad de la ventana de marco.

```
void SaveBarState(LPCTSTR lpszProfileName) const;
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
Nombre de una sección del archivo de inicialización o una clave en el registro de Windows donde se almacena la información de estado.

### <a name="remarks"></a>Comentarios

Esta información se puede leer desde el archivo de inicialización mediante [LoadBarState](#loadbarstate). La información almacenada incluye visibilidad, orientación horizontal o vertical, estado de acoplamiento y posición de la barra de control.

##  <a name="setactivepreviewview"></a>  CFrameWnd::SetActivePreviewView

Designa la vista especificada para que sea la vista activa para la vista previa enriquecida.

```
void SetActivePreviewView(CView* pViewNew);
```

### <a name="parameters"></a>Parámetros

*pViewNew*<br/>
Puntero a una vista que se va a activar.

### <a name="remarks"></a>Comentarios

##  <a name="setactiveview"></a>  CFrameWnd::SetActiveView

Llame a esta función miembro para establecer la vista activa.

```
void SetActiveView(
    CView* pViewNew,
    BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parámetros

*pViewNew*<br/>
Especifica un puntero a un objeto [CView](../../mfc/reference/cview-class.md) o null para ninguna vista activa.

*bNotify*<br/>
Especifica si se va a notificar la activación de la vista. Si es true `OnActivateView` , se llama a para la nueva vista; si es false, no lo es.

### <a name="remarks"></a>Comentarios

El marco de trabajo llamará automáticamente a esta función cuando el usuario cambie el foco a una vista dentro de la ventana de marco. Puede llamar `SetActiveView` explícitamente a para cambiar el foco a la vista especificada.

##  <a name="setdockstate"></a>  CFrameWnd::SetDockState

Llame a esta función miembro para aplicar la información de estado `CDockState` almacenada en un objeto a las barras de control de la ventana de marco.

```
void SetDockState(const CDockState& state);
```

### <a name="parameters"></a>Parámetros

*state*<br/>
Aplique el estado almacenado a las barras de control de la ventana de marco.

### <a name="remarks"></a>Comentarios

Para restaurar un estado anterior de las barras de control, puede cargar el estado almacenado con `CDockState::LoadState` o `Serialize`y, a `SetDockState` continuación, usar para aplicarlo a las barras de control de la ventana de marco. El estado anterior se almacena en el `CDockState` objeto con`GetDockState`

##  <a name="setmenubarstate"></a>  CFrameWnd::SetMenuBarState

Establece el estado de visualización del menú en la aplicación MFC actual en oculto o mostrado.

```
virtual BOOL SetMenuBarState(DWORD nState);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*nState*|de Especifica si se debe mostrar u ocultar el menú. El parámetro *nState* puede tener los siguientes valores:<br /><br />-AFX_MBS_VISIBLE (0x01): muestra el menú si está oculto, pero no tiene ningún efecto si está visible.<br />-AFX_MBS_HIDDEN (0x02): oculta el menú si está visible, pero no tiene ningún efecto si está oculto.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método cambia correctamente el estado del menú; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Si se produce un error en tiempo de ejecución, este método se valida en modo de depuración y genera una excepción derivada de la clase [CException](../../mfc/reference/cexception-class.md) .

##  <a name="setmenubarvisibility"></a>  CFrameWnd::SetMenuBarVisibility

Establece el comportamiento predeterminado del menú en la aplicación MFC actual para que esté oculto o visible.

```
virtual void SetMenuBarVisibility(DWORD nStyle);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*nStyle*|de Especifica si el menú está oculto de forma predeterminada o está visible y tiene el foco. El parámetro *nStyle* puede tener los siguientes valores:<br /><br />-AFX_MBV_KEEPVISIBLE (0x01)-<br />     El menú se muestra en todo momento y, de forma predeterminada, no tiene el foco.<br />-AFX_MBV_DISPLAYONFOCUS (0x02)-<br />     El menú está oculto de forma predeterminada. Si el menú está oculto, presione la tecla ALT para mostrar el menú y asígnele el foco. Si se muestra el menú, presione la tecla ALT o ESC para ocultar el menú.<br />-AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04)<br />     (combinación bit a bit (o)): el menú está oculto de forma predeterminada. Si el menú está oculto, presione la tecla F10 para mostrar el menú y darle el foco. Si se muestra el menú, presione la tecla F10 para activar o desactivar el menú. El menú se mostrará hasta que presione la tecla ALT o ESC para ocultarlo.|

### <a name="remarks"></a>Comentarios

Si el valor del parámetro *nStyle* no es válido, este método se valida en modo de depuración y genera [CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md) en modo de versión. En el caso de otros errores en tiempo de ejecución, este método se valida en modo de depuración y genera una excepción derivada de la clase [CException](../../mfc/reference/cexception-class.md) .

Este método afecta al estado de los menús de las aplicaciones escritas para Windows Vista y versiones posteriores.

##  <a name="setmessagetext"></a>  CFrameWnd::SetMessageText

Llame a esta función para colocar una cadena en el panel de la barra de Estado cuyo identificador sea 0.

```
void SetMessageText(LPCTSTR lpszText);
void SetMessageText(UINT nID);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
Apunta a la cadena que se va a colocar en la barra de estado.

*nID*<br/>
IDENTIFICADOR de recurso de cadena de la cadena que se va a colocar en la barra de estado.

### <a name="remarks"></a>Comentarios

Suele ser el panel de la izquierda y el más largo de la barra de estado.

##  <a name="setprogressbarposition"></a>  CFrameWnd::SetProgressBarPosition

Establece la posición actual de la barra de progreso de Windows 7 mostrada en la barra de tareas.

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Parámetros

*nProgressPos*<br/>
Especifica la posición que se va a establecer. Debe estar dentro del intervalo establecido por `SetProgressBarRange`.

### <a name="remarks"></a>Comentarios

##  <a name="setprogressbarrange"></a>  CFrameWnd::SetProgressBarRange

Establece el intervalo de la barra de progreso de Windows 7 que se muestra en la barra de tareas.

```
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Parámetros

*nRangeMin*<br/>
Valor mínimo.

*nRangeMax*<br/>
Valor máximo.

### <a name="remarks"></a>Comentarios

##  <a name="setprogressbarstate"></a>  CFrameWnd::SetProgressBarState

Establece el tipo y el estado del indicador de progreso mostrado en un botón de la barra de tareas.

```
void SetProgressBarState(TBPFLAG tbpFlags);
```

### <a name="parameters"></a>Parámetros

*tbpFlags*<br/>
Marcas que controlan el estado actual del botón de progreso. Especifique solo una de las marcas siguientes porque todos los Estados son mutuamente excluyentes: TBPF_NOPROGRESS, TBPF_INDETERMINATE, TBPF_NORMAL, TBPF_ERROR, TBPF_PAUSED.

### <a name="remarks"></a>Comentarios

##  <a name="settaskbaroverlayicon"></a>  CFrameWnd::SetTaskbarOverlayIcon

Sobrecargado. Aplica una superposición a un botón de la barra de tareas para indicar el estado de la aplicación o para notificar al usuario.

```
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,
    LPCTSTR lpcszDescr);

BOOL SetTaskbarOverlayIcon(
    HICON hIcon,
    LPCTSTR lpcszDescr);
```

### <a name="parameters"></a>Parámetros

*nIDResource*<br/>
Especifica el identificador de recurso de un icono que se va a usar como superposición. Vea la descripción de *hIcon* para obtener más información.

*lpcszDescr*<br/>
Puntero a una cadena que proporciona una versión de texto alternativo de la información transmitida por la superposición, con fines de accesibilidad.

*hIcon*<br/>
Identificador de un icono que se va a usar como superposición. Debe ser un icono pequeño, que mida 16x16 píxeles a 96 puntos por pulgada (PPP). Si ya hay un icono de superposición aplicado al botón de la barra de tareas, se reemplaza la superposición existente. Este valor puede ser NULL. La forma en que se controla un valor NULL depende de si el botón de la barra de tareas representa una única ventana o un grupo de ventanas. Es responsabilidad de la aplicación que realiza la llamada liberar *hIcon* cuando ya no se necesita.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; FALSE si la versión del sistema operativo es anterior a Windows 7 o si se produce un error al establecer el icono.

### <a name="remarks"></a>Comentarios

##  <a name="settitle"></a>  CFrameWnd::SetTitle

Establece el título del objeto de ventana.

```
void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Parámetros

*lpszTitle*<br/>
Puntero a una cadena de caracteres que contiene el título del objeto de ventana.

##  <a name="showcontrolbar"></a>  CFrameWnd::ShowControlBar

Llame a esta función miembro para mostrar u ocultar la barra de controles.

```
void ShowControlBar(
    CControlBar* pBar,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
Puntero a la barra de control que se va a mostrar u ocultar.

*bShow*<br/>
Si es TRUE, especifica que se va a mostrar la barra de control. Si es FALSE, especifica que la barra de control se va a ocultar.

*bDelay*<br/>
Si es TRUE, retrasar la visualización de la barra de control. Si es FALSE, Mostrar la barra de control inmediatamente.

##  <a name="showownedwindows"></a>  CFrameWnd::ShowOwnedWindows

Llame a esta función miembro para mostrar todas las ventanas que son descendientes `CFrameWnd` del objeto.

```
void ShowOwnedWindows(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bShow*<br/>
Especifica si las ventanas de propiedad se van a mostrar u ocultar.

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd (clase)](../../mfc/reference/cmdiframewnd-class.md)<br/>
[CMDIChildWnd (clase)](../../mfc/reference/cmdichildwnd-class.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)<br/>
[CRuntimeClass (estructura)](../../mfc/reference/cruntimeclass-structure.md)
