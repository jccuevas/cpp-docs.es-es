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
ms.openlocfilehash: 0fd104e377300233ef1526f6c453346555dd27d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373787"
---
# <a name="cframewnd-class"></a>CFrameWnd (clase)

Proporciona la funcionalidad de una ventana de marco de interfaz de un único documento (SDI) de Windows superpuesta o emergente, junto con los miembros para administrar la ventana.

## <a name="syntax"></a>Sintaxis

```
class CFrameWnd : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFrameWnd::CFrameWnd](#cframewnd)|Construye un objeto `CFrameWnd`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFrameWnd::ActivateFrame](#activateframe)|Hace que el marco sea visible y esté disponible para el usuario.|
|[CFrameWnd::BeginModalState](#beginmodalstate)|Establece la ventana de marco en modal.|
|[CFrameWnd::Create](#create)|Llame para crear e inicializar la `CFrameWnd` ventana de marco de Windows asociada al objeto.|
|[CFrameWnd::CreateView](#createview)|Crea una vista dentro de un `CView`marco que no se deriva de .|
|[CFrameWnd::DockControlBar](#dockcontrolbar)|Acopla una barra de control.|
|[CFrameWnd::EnableDocking](#enabledocking)|Permite acoplar una barra de control.|
|[CFrameWnd::EndModalState](#endmodalstate)|Finaliza el estado modal de la ventana de marco. Habilita todas las ventanas deshabilitadas por `BeginModalState`.|
|[CFrameWnd::FloatControlBar](#floatcontrolbar)|Flota una barra de control.|
|[CFrameWnd::GetActiveDocument](#getactivedocument)|Devuelve el `CDocument` objeto activo.|
|[CFrameWnd::GetActiveFrame](#getactiveframe)|Devuelve el `CFrameWnd` objeto activo.|
|[CFrameWnd::GetActiveView](#getactiveview)|Devuelve el `CView` objeto activo.|
|[CFrameWnd::GetControlBar](#getcontrolbar)|Recupera la barra de control.|
|[CFrameWnd::GetDockState](#getdockstate)|Recupera el estado de acoplamiento de una ventana de marco.|
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|Recupera el estado de presentación del menú en la aplicación MFC actual.|
|[CFrameWnd::GetMenuBarVisibility](#getmenubarvisibility)|Indica si el comportamiento predeterminado del menú en la aplicación MFC actual está oculto o visible.|
|[CFrameWnd::GetMessageBar](#getmessagebar)|Devuelve un puntero a la barra de estado que pertenece a la ventana de marco.|
|[CFrameWnd::GetMessageString](#getmessagestring)|Recupera el mensaje correspondiente a un identificador de comando.|
|[CFrameWnd::GetTitle](#gettitle)|Recupera el título de la barra de control relacionada.|
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|Hace `OnInitialUpdate` que se llame a la función miembro que pertenece a todas las vistas de la ventana de marco.|
|[CFrameWnd::InModalState](#inmodalstate)|Devuelve un valor que indica si una ventana de marco está en un estado modal.|
|[CFrameWnd::IsTracking](#istracking)|Determina si la barra divisora se está moviendo actualmente.|
|[CFrameWnd::LoadAccelTable](#loadacceltable)|Llame para cargar una tabla de aceleradores.|
|[CFrameWnd::LoadBarState](#loadbarstate)|Llamada para restaurar la configuración de la barra de control.|
|[CFrameWnd::LoadFrame](#loadframe)|Llame para crear dinámicamente una ventana de marco a partir de la información de recursos.|
|[CFrameWnd::NegotiateBorderSpace](#negotiateborderspace)|Negocia el espacio de borde en la ventana de marco.|
|[CFrameWnd::OnBarCheck](#onbarcheck)|Se llama siempre que se realiza una acción en la barra de control especificada.|
|[CFrameWnd::OnContextHelp](#oncontexthelp)|Controla la Ayuda de SHIFT+F1 para los elementos in situ.|
|[CFrameWnd::OnSetPreviewMode](#onsetpreviewmode)|Establece la ventana de marco principal de la aplicación dentro y fuera del modo de vista previa de impresión.|
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|Llamado por el marco de trabajo cuando se actualiza el menú asociado.|
|[CFrameWnd::RecalcLayout](#recalclayout)|Cambia la posición de `CFrameWnd` las barras de control del objeto.|
|[CFrameWnd::SaveBarState](#savebarstate)|Llame para guardar la configuración de la barra de control.|
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|Designa la vista especificada para que sea la vista activa de Vista preliminar enriquecida.|
|[CFrameWnd::SetActiveView](#setactiveview)|Establece el `CView` objeto activo.|
|[CFrameWnd::SetDockState](#setdockstate)|Llame para acoplar la ventana de marco en la ventana principal.|
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|Establece el estado de visualización del menú en la aplicación MFC actual en oculto o mostrado.|
|[CFrameWnd::SetMenuBarVisibility](#setmenubarvisibility)|Establece el comportamiento predeterminado del menú en la aplicación MFC actual para que sea oculto o visible.|
|[CFrameWnd::SetMessageText](#setmessagetext)|Establece el texto de una barra de estado estándar.|
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|Establece la posición actual de la barra de progreso de Windows 7 que se muestra en la barra de tareas.|
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|Establece el rango de la barra de progreso de Windows 7 que se muestra en la barra de tareas.|
|[CFrameWnd::SetProgressBarState](#setprogressbarstate)|Establece el tipo y el estado del indicador de progreso que se muestra en un botón de la barra de tareas.|
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|Sobrecargado. Aplica una superposición a un botón de la barra de tareas para indicar el estado de la aplicación o una notificación al usuario.|
|[CFrameWnd::SetTitle](#settitle)|Establece el título de la barra de control relacionada.|
|[CFrameWnd::ShowControlBar](#showcontrolbar)|Llame para mostrar la barra de control.|
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|Muestra todas las ventanas `CFrameWnd` que son descendientes del objeto.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CFrameWnd::OnCreateClient](#oncreateclient)|Crea una ventana de cliente para el marco.|
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|Se llama antes de que se oculta el menú de la aplicación MFC actual.|
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|Se llama antes de que se muestre el menú de la aplicación MFC actual.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|Controla la funcionalidad de activación y desactivación automática para los elementos de menú.|
|[CFrameWnd::rectDefault](#rectdefault)|Pase esta `CRect` estática como parámetro `CFrameWnd` al crear un objeto para permitir que Windows elija el tamaño y la posición iniciales de la ventana.|

## <a name="remarks"></a>Observaciones

Para crear una ventana de marco útil `CFrameWnd`para la aplicación, derive una clase de . Agregue variables miembro a la clase derivada para almacenar datos específicos de la aplicación. Implemente funciones miembro de controlador de mensajes y un mapa de mensajes en la clase derivada para especificar qué ocurre cuando los mensajes se dirigen a la ventana.

Hay tres formas de construir una ventana de marco:

- Comabúlo directamente con [Create](#create).

- Comabúlo directamente con [LoadFrame](#loadframe).

- De forma indirecta, comportéalo con una plantilla de documento.

Antes de `Create` llamar `LoadFrame`a cualquiera o , debe construir el objeto de ventana de marco en el montón mediante el **operador new** C++. Antes `Create`de llamar a , también puede registrar una clase de ventana con la función global [AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass) para establecer los estilos de icono y clase para el marco.

Utilice `Create` la función miembro para pasar los parámetros de creación del marco como argumentos inmediatos.

`LoadFrame`requiere menos argumentos `Create`que , y en su lugar recupera la mayoría de sus valores predeterminados de los recursos, incluidos el título, el icono, la tabla de aceleradores y el menú del marco. Para que `LoadFrame`sea accesible por , todos estos recursos deben tener el mismo identificador de recurso (por ejemplo, IDR_MAINFRAME).

Cuando `CFrameWnd` un objeto contiene vistas y documentos, el marco de trabajo los crea indirectamente en lugar de directamente por el programador. El `CDocTemplate` objeto organiza la creación del marco, la creación de las vistas contenedoras y la conexión de las vistas al documento adecuado. Los parámetros `CDocTemplate` del `CRuntimeClass` constructor especifican las tres clases implicadas (documento, marco y vista). El `CRuntimeClass` marco de trabajo utiliza un objeto para crear dinámicamente nuevos marcos cuando lo especifica el usuario (por ejemplo, mediante el comando Nuevo archivo o el comando Ventana nueva de interfaz de documento múltiple (MDI).

Una clase de ventana `CFrameWnd` de trama derivada de debe declararse con DECLARE_DYNCREATE para que el mecanismo de RUNTIME_CLASS anterior funcione correctamente.

A `CFrameWnd` contiene implementaciones predeterminadas para realizar las siguientes funciones de una ventana principal en una aplicación típica para Windows:

- Una `CFrameWnd` ventana de marco realiza un seguimiento de una vista activa actualmente que es independiente de la ventana activa de Windows o del foco de entrada actual. Cuando se reactiva la trama, se notifica `CView::OnActivateView`la vista activa llamando a .

- Los mensajes de comando y muchos mensajes comunes `OnSetFocus`de `OnHScroll`notificación de fotogramas, incluidos los controlados por las funciones , , y `OnVScroll` de , se delegan mediante una `CWnd` `CFrameWnd` ventana de marco a la vista activa actualmente.

- La vista activa actualmente (o la ventana de marco secundario MDI activa actualmente en el caso de un marco MDI) puede determinar el título de la ventana de marco. Esta función se puede desactivar desactivando el bit de estilo FWS_ADDTOTITLE de la ventana de marco.

- Una `CFrameWnd` ventana de marco administra el posicionamiento de las barras de control, las vistas y otras ventanas secundarias dentro del área de cliente de la ventana de marco. Una ventana de marco también realiza la actualización en tiempo de inactividad de la barra de herramientas y otros botones de la barra de control. Una `CFrameWnd` ventana de marco también tiene implementaciones predeterminadas de comandos para activar y desactivar la barra de herramientas y la barra de estado.

- Una `CFrameWnd` ventana de marco administra la barra de menú principal. Cuando se muestra un menú emergente, la ventana de marco utiliza el mecanismo de UPDATE_COMMAND_UI para determinar qué elementos de menú deben habilitarse, deshabilitarse o comprobarse. Cuando el usuario selecciona un elemento de menú, la ventana de marco actualiza la barra de estado con la cadena de mensaje para ese comando.

- Una `CFrameWnd` ventana de marco tiene una tabla de aceleradores opcional que traduce automáticamente los aceleradores de teclado.

- Una `CFrameWnd` ventana de marco tiene `LoadFrame` un identificador de ayuda opcional establecido con que se utiliza para la ayuda contextual. Una ventana de marco es el orquestador principal de estados semimodales, como la ayuda contextual (SHIFT+F1) y los modos de vista previa de impresión.

- Una `CFrameWnd` ventana de marco abrirá un archivo arrastrado desde el Administrador de archivos y colocado en la ventana de marco. Si una extensión de archivo está registrada y asociada a la aplicación, la ventana de marco responde a la solicitud de apertura `ShellExecute` de intercambio de datos dinámicos (DDE) que se produce cuando el usuario abre un archivo de datos en el Administrador de archivos o cuando se llama a la función de Windows.

- Si la ventana de marco es la `CWinThread::m_pMainWnd`ventana principal de la aplicación (es decir, ), cuando el `OnClose` usuario `OnQueryEndSession`cierra la aplicación, la ventana de marco solicita al usuario que guarde los documentos modificados (para y ).

- Si la ventana de marco es la ventana principal de la aplicación, la ventana de marco es el contexto para ejecutar WinHelp. Al cerrar la ventana de marco se cerrará WINHELP. EXE si se inició para obtener ayuda para esta aplicación.

No utilice el operador **de eliminación** C++ para destruir una ventana de marco. En su lugar, use `CWnd::DestroyWindow`. La `CFrameWnd` implementación de `PostNcDestroy` eliminará el objeto C++ cuando se destruya la ventana. Cuando el usuario cierra la ventana `OnClose` de `DestroyWindow`marco, el controlador predeterminado llamará a .

Para obtener `CFrameWnd`más información sobre , consulte [Ventanas](../../mfc/frame-windows.md)de marco .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CFrameWnd`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cframewndactivateframe"></a><a name="activateframe"></a>CFrameWnd::ActivateFrame

Llame a esta función miembro para activar y restaurar la ventana de marco para que sea visible y disponible para el usuario.

```
virtual void ActivateFrame(int nCmdShow = -1);
```

### <a name="parameters"></a>Parámetros

*nCmdShow*<br/>
Especifica el parámetro que se va a pasar a [CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow). De forma predeterminada, el marco se muestra y se restaura correctamente.

### <a name="remarks"></a>Observaciones

Normalmente se llama a esta función miembro después de un evento de interfaz no de usuario como un DDE, OLE u otro evento que puede mostrar la ventana de marco o su contenido al usuario.

La implementación predeterminada activa el marco y lo lleva a la parte superior del orden Z y, si es necesario, lleva a cabo los mismos pasos para la ventana de marco principal de la aplicación.

Invalide esta función miembro para cambiar cómo se activa un fotograma. Por ejemplo, puede forzar que se maximicen las ventanas secundarias MDI. Agregue la funcionalidad adecuada y, a continuación, llame a la versión de la clase base con un *nCmdShow*explícito.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#1](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]

## <a name="cframewndbeginmodalstate"></a><a name="beginmodalstate"></a>CFrameWnd::BeginModalState

Llame a esta función miembro para convertir una ventana marco en modal.

```
virtual void BeginModalState();
```

## <a name="cframewndcframewnd"></a><a name="cframewnd"></a>CFrameWnd::CFrameWnd

Construye un `CFrameWnd` objeto, pero no crea la ventana de marco visible.

```
CFrameWnd();
```

### <a name="remarks"></a>Observaciones

Llame `Create` para crear la ventana visible.

## <a name="cframewndcreate"></a><a name="create"></a>CFrameWnd::Create

Llame para crear e inicializar la `CFrameWnd` ventana de marco de Windows asociada al objeto.

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
Apunta a una cadena de caracteres terminada en null que nombra la clase Windows. El nombre de clase puede `AfxRegisterWndClass` ser cualquier `RegisterClass` nombre registrado con la función global o la función de Windows. Si NULL, utiliza los `CFrameWnd` atributos predeterminados predefinidos.

*lpszWindowName*<br/>
Apunta a una cadena de caracteres terminada en null que representa el nombre de la ventana. Se utiliza como texto para la barra de título.

*dwStyle*<br/>
Especifica los atributos de [estilo](../../mfc/reference/styles-used-by-mfc.md#window-styles) de ventana. Incluya el estilo FWS_ADDTOTITLE si desea que la barra de título muestre automáticamente el nombre del documento representado en la ventana.

*Rect*<br/>
Especifica el tamaño y la posición de la ventana. El valor *rectDefault* permite a Windows especificar el tamaño y la posición de la nueva ventana.

*pParentWnd*<br/>
Especifica la ventana primaria de esta ventana de marco. Este parámetro debe ser NULL para las ventanas de marco de nivel superior.

*lpszMenuName*<br/>
Identifica el nombre del recurso de menú que se utilizará con la ventana. Utilice MAKEINTRESOURCE si el menú tiene un identificador entero en lugar de una cadena. Este parámetro puede ser NULL.

*dwExStyle*<br/>
Especifica los atributos de [estilo](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) extendido de ventana.

*pContext*<br/>
Especifica un puntero a un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) estructura. Este parámetro puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización se realiza correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Construir `CFrameWnd` un objeto en dos pasos. En primer lugar, invoque `CFrameWnd` el constructor, `Create`que construye el objeto y, a `CFrameWnd` continuación, llame a , que crea la ventana de marco de Windows y lo adjunta al objeto. `Create`inicializa el nombre de clase y el nombre de ventana de la ventana y registra los valores predeterminados para su estilo, elemento primario y menú asociado.

Usar `LoadFrame` en `Create` lugar de cargar la ventana de marco desde un recurso en lugar de especificar sus argumentos.

## <a name="cframewndcreateview"></a><a name="createview"></a>CFrameWnd::CreateView

Llame `CreateView` para crear una vista dentro de un marco.

```
CWnd* CreateView(
    CCreateContext* pContext,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Parámetros

*pContext*<br/>
Especifica el tipo de vista y documento.

*nID*<br/>
El número de ID de una vista.

### <a name="return-value"></a>Valor devuelto

Puntero a `CWnd` un objeto si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Utilice esta función miembro para crear `CView`"vistas" que no se derivan dentro de un marco. Después `CreateView`de llamar , debe establecer manualmente la vista en activa y establecerla para que sea visible; estas tareas no se `CreateView`realizan automáticamente por .

## <a name="cframewnddockcontrolbar"></a><a name="dockcontrolbar"></a>CFrameWnd::DockControlBar

Hace que una barra de control se acopla a la ventana de marco.

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
Determina qué lados de la ventana de marco se deben tener en cuenta para el acoplamiento. Puede ser 0, o uno o más de los siguientes:

- AFX_IDW_DOCKBAR_TOP Acoplar en la parte superior de la ventana de marco.

- AFX_IDW_DOCKBAR_BOTTOM Acoplar en la parte inferior de la ventana de marco.

- AFX_IDW_DOCKBAR_LEFT Acoplar a la izquierda de la ventana de marco.

- AFX_IDW_DOCKBAR_RIGHT Acoplar a la derecha de la ventana de marco.

Si es 0, la barra de control se puede acoplar a cualquier lado habilitado para el acoplamiento en la ventana de marco de destino.

*lpRect*<br/>
Determina, en coordenadas de pantalla, dónde se acoplará la barra de control en el área no cliente de la ventana de marco de destino.

### <a name="remarks"></a>Observaciones

La barra de control se acoplará a uno de los lados de la ventana de marco especificada en las llamadas a [CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking) y [CFrameWnd::EnableDocking](#enabledocking). El lado elegido viene determinado por *nDockBarID*.

## <a name="cframewndenabledocking"></a><a name="enabledocking"></a>CFrameWnd::EnableDocking

Llame a esta función para habilitar las barras de control acoplables en una ventana de marco.

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parámetros

*dwDockStyle*<br/>
Especifica qué lados de la ventana de marco pueden servir como sitios de acoplamiento para las barras de control. Puede ser uno o más de los siguientes:

- CBRS_ALIGN_TOP Permite el acoplamiento en la parte superior del área de cliente.

- CBRS_ALIGN_BOTTOM Permite el acoplamiento en la parte inferior del área de cliente.

- CBRS_ALIGN_LEFT Permite el acoplamiento en el lado izquierdo del área de cliente.

- CBRS_ALIGN_RIGHT Permite el acoplamiento en el lado derecho del área de cliente.

- CBRS_ALIGN_ANY Permite el acoplamiento en cualquier lado del área de cliente.

### <a name="remarks"></a>Observaciones

De forma predeterminada, las barras de control se acoplarán a un lado de la ventana de marco en el siguiente orden: superior, inferior, izquierda, derecha.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CToolBar::Create](../../mfc/reference/ctoolbar-class.md#create).

## <a name="cframewndendmodalstate"></a><a name="endmodalstate"></a>CFrameWnd::EndModalState

Llame a esta función miembro para cambiar una ventana marco de modal a no modal.

```
virtual void EndModalState();
```

### <a name="remarks"></a>Observaciones

`EndModalState`habilita todas las ventanas deshabilitadas por [BeginModalState](#beginmodalstate).

## <a name="cframewndfloatcontrolbar"></a><a name="floatcontrolbar"></a>CFrameWnd::FloatControlBar

Llame a esta función para hacer que una barra de control no se acopla a la ventana de marco.

```
void FloatControlBar(
    CControlBar* pBar,
    CPoint point,
    DWORD dwStyle = CBRS_ALIGN_TOP);
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
Apunta a la barra de control que se va a flotar.

*Punto*<br/>
La ubicación, en coordenadas de pantalla, donde se colocará la esquina superior izquierda de la barra de control.

*dwStyle*<br/>
Especifica si se debe alinear la barra de control horizontal o verticalmente dentro de su nueva ventana de marco. Puede ser cualquiera de los siguientes:

- CBRS_ALIGN_TOP Orienta la barra de control verticalmente.

- CBRS_ALIGN_BOTTOM Orienta la barra de control verticalmente.

- CBRS_ALIGN_LEFT Orienta la barra de control horizontalmente.

- CBRS_ALIGN_RIGHT Orienta la barra de control horizontalmente.

Si se pasan estilos especificando la orientación horizontal y vertical, la barra de herramientas se orientará horizontalmente.

### <a name="remarks"></a>Observaciones

Normalmente, esto se hace al iniciar la aplicación cuando el programa está restaurando la configuración de la ejecución anterior.

El marco de trabajo llama a esta función cuando el usuario provoca una operación de colocación soltando el botón izquierdo del ratón mientras arrastra la barra de control sobre una ubicación que no está disponible para el acoplamiento.

## <a name="cframewndgetactivedocument"></a><a name="getactivedocument"></a>CFrameWnd::GetActiveDocument

Llame a esta función miembro `CDocument` para obtener un puntero a la actual adjunta a la vista activa actual.

```
virtual CDocument* GetActiveDocument();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al [CDocument](../../mfc/reference/cdocument-class.md)actual. Si no hay ningún documento actual, devuelve NULL.

## <a name="cframewndgetactiveframe"></a><a name="getactiveframe"></a>CFrameWnd::GetActiveFrame

Llame a esta función miembro para obtener un puntero a la ventana secundaria de la interfaz de documento múltiple (MDI) activa de una ventana de marco MDI.

```
virtual CFrameWnd* GetActiveFrame();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la ventana secundaria MDI activa. Si la aplicación es una aplicación SDI o la ventana de marco MDI no tiene ningún documento activo, se devolverá el puntero **this** implícito.

### <a name="remarks"></a>Observaciones

Si no hay ningún elemento secundario MDI activo o la aplicación es una interfaz de documento único (SDI), se devuelve el puntero **this** implícito.

## <a name="cframewndgetactiveview"></a><a name="getactiveview"></a>CFrameWnd::GetActiveView

Llame a esta función miembro para obtener un puntero a la `CFrameWnd`vista activa (si existe) adjunta a una ventana de marco ( ).

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la [versión actual de CView](../../mfc/reference/cview-class.md). Si no hay ninguna vista actual, devuelve NULL.

### <a name="remarks"></a>Observaciones

Esta función devuelve NULL cuando se llama `CMDIFrameWnd`para una ventana de marco principal MDI ( ). En una aplicación MDI, la ventana de marco principal MDI no tiene una vista asociada. En su lugar, `CMDIChildWnd`cada ventana secundaria individual ( ) tiene una o más vistas asociadas. La vista activa en una aplicación MDI se puede obtener primero buscando la ventana secundaria MDI activa y, a continuación, buscando la vista activa para esa ventana secundaria. La ventana secundaria MDI activa se `MDIGetActive` puede `GetActiveFrame` encontrar llamando a la función o como se muestra en lo siguiente:

[!code-cpp[NVC_MFCWindowing#2](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]

## <a name="cframewndgetcontrolbar"></a><a name="getcontrolbar"></a>CFrameWnd::GetControlBar

Llame `GetControlBar` para obtener acceso a la barra de control asociada al identificador.

```
CControlBar* GetControlBar(UINT nID);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
El número de ID de una barra de control.

### <a name="return-value"></a>Valor devuelto

Puntero a la barra de control asociada al identificador.

### <a name="remarks"></a>Observaciones

El *nID* parámetro hace referencia al `Create` identificador único pasado al método de la barra de control. Para obtener más información sobre las barras de control, consulte el tema titulado [Barras](../../mfc/control-bars.md)de control .

`GetControlBar`devolverá la barra de control incluso si está flotante y, por lo tanto, no es actualmente una ventana secundaria del marco.

## <a name="cframewndgetdockstate"></a><a name="getdockstate"></a>CFrameWnd::GetDockState

Llame a esta función miembro para almacenar información de `CDockState` estado sobre las barras de control de la ventana de marco en un objeto.

```
void GetDockState(CDockState& state) const;
```

### <a name="parameters"></a>Parámetros

*state*<br/>
Contiene el estado actual de las barras de control de la ventana de marco al devolver.

### <a name="remarks"></a>Observaciones

A continuación, puede `CDockState` escribir el `CDockState::SaveState` `Serialize`contenido del almacenamiento mediante o . Si más adelante desea restaurar las barras de control `CDockState::LoadState` a `Serialize`un `SetDockState` estado anterior, cargue el estado con o , a continuación, llame para aplicar el estado anterior a las barras de control de la ventana de marco.

## <a name="cframewndgetmenubarstate"></a><a name="getmenubarstate"></a>CFrameWnd::GetMenuBarState

Recupera el estado de presentación del menú en la aplicación MFC actual.

```
virtual DWORD GetMenuBarState();
```

### <a name="return-value"></a>Valor devuelto

El valor devuelto puede tener los siguientes valores:

- AFX_MBS_VISIBLE (0x01): el menú está visible.

- AFX_MBS_HIDDEN (0x02): el menú está oculto.

### <a name="remarks"></a>Observaciones

Si se produce un error en tiempo de ejecución, este método afirma en modo de depuración y genera una excepción derivada de la [CException](../../mfc/reference/cexception-class.md) clase.

## <a name="cframewndgetmenubarvisibility"></a><a name="getmenubarvisibility"></a>CFrameWnd::GetMenuBarVisibility

Indica si el estado predeterminado del menú en la aplicación MFC actual está oculto o visible.

```
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```

### <a name="return-value"></a>Valor devuelto

Este método devuelve uno de los siguientes valores:

- AFX_MBV_KEEPVISIBLE (0x01): el menú se muestra en todo momento y, de forma predeterminada, no tiene el foco.

- AFX_MBV_DISPLAYONFOCUS (0x02): el menú está oculto de forma predeterminada. Si el menú está oculto, presione la tecla ALT para mostrar el menú y darle el foco. Si se muestra el menú, pulse la tecla ALT o ESC para ocultarlo.

- AFX_MBV_ DISPLAYONFOCUS (0x02) &#124; AFX_MBV_DISPLAYONF10 (0x04) (combinación bit a bit (OR)) - El menú está oculto de forma predeterminada. Si el menú está oculto, presione la tecla F10 para mostrar el menú y darle el foco. Si se muestra el menú, pulse la tecla F10 para activar o desactivar el enfoque en el menú. El menú se muestra hasta que pulse la tecla ALT o ESC para ocultarlo.

### <a name="remarks"></a>Observaciones

Si se produce un error en tiempo de ejecución, este método afirma en modo de depuración y genera una excepción derivada de la [CException](../../mfc/reference/cexception-class.md) clase.

## <a name="cframewndgetmessagebar"></a><a name="getmessagebar"></a>CFrameWnd::GetMessageBar

Llame a esta función miembro para obtener un puntero a la barra de estado.

```
virtual CWnd* GetMessageBar();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la ventana de la barra de estado.

## <a name="cframewndgetmessagestring"></a><a name="getmessagestring"></a>CFrameWnd::GetMessageString

Invalide esta función para proporcionar cadenas personalizadas para los ideos de comando.

```
virtual void GetMessageString(
    UINT nID,
    CString& rMessage) const;
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
Id. de recurso del mensaje deseado.

*rMessage*<br/>
`CString`objeto en el que colocar el mensaje.

### <a name="remarks"></a>Observaciones

La implementación predeterminada simplemente carga la cadena especificada por *nID* desde el archivo de recursos. El marco de trabajo llama a esta función cuando la cadena de mensaje de la barra de estado necesita actualizarse.

## <a name="cframewndgettitle"></a><a name="gettitle"></a>CFrameWnd::GetTitle

Recupera el título del objeto de ventana.

```
CString GetTitle() const;
```

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el título actual del objeto de ventana.

## <a name="cframewndinitialupdateframe"></a><a name="initialupdateframe"></a>CFrameWnd::InitialUpdateFrame

Llame `IntitialUpdateFrame` después de `Create`crear un nuevo marco con .

```
void InitialUpdateFrame(
    CDocument* pDoc,
    BOOL bMakeVisible);
```

### <a name="parameters"></a>Parámetros

*pDoc*<br/>
Apunta al documento al que está asociada la ventana de marco. Puede ser NULL.

*bMakeVisible*<br/>
Si ES TRUE, indica que el marco debe ser visible y activo. Si FALSE, no se hace visible ningún descendiente.

### <a name="remarks"></a>Observaciones

Esto hace que todas las vistas `OnInitialUpdate` de esa ventana de marco reciban sus llamadas.

Además, si no había anteriormente una vista activa, la vista principal de la ventana de marco se activa. La vista principal es una vista con un identificador secundario de AFX_IDW_PANE_FIRST. Por último, la ventana de marco se hace visible si *bMakeVisible* es distinto de cero. Si *bMakeVisible* es 0, el foco actual y el estado visible de la ventana de marco permanecerán sin cambios. No es necesario llamar a esta función cuando se utiliza la implementación del marco de trabajo de archivo nuevo y archivo abierto.

## <a name="cframewndinmodalstate"></a><a name="inmodalstate"></a>CFrameWnd::InModalState

Llame a esta función miembro para comprobar si una ventana de marco es modal o no modal.

```
BOOL InModalState() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si sí; de lo contrario 0.

## <a name="cframewndistracking"></a><a name="istracking"></a>CFrameWnd::IsTracking

Llame a esta función miembro para determinar si la barra divisora en la ventana se está moviendo actualmente.

```
BOOL IsTracking() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si una operación de divisor está en curso; de lo contrario 0.

## <a name="cframewndloadacceltable"></a><a name="loadacceltable"></a>CFrameWnd::LoadAccelTable

Llame para cargar la tabla de aceleradores especificada.

```
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```

### <a name="parameters"></a>Parámetros

*lpszResourceName*<br/>
Identifica el nombre del recurso acelerador. Utilice MAKEINTRESOURCE si el recurso se identifica con un identificador entero.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la tabla de aceleradores se cargó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Solo se puede cargar una tabla a la vez.

Las tablas de aceleradores cargadas de recursos se liberan automáticamente cuando finaliza la aplicación.

Si llama `LoadFrame` para crear la ventana de marco, el marco de trabajo carga una tabla de aceleradores junto con los recursos de menú e icono, y una llamada posterior a esta función miembro es innecesaria.

## <a name="cframewndloadbarstate"></a><a name="loadbarstate"></a>CFrameWnd::LoadBarState

Llame a esta función para restaurar la configuración de cada barra de control propiedad de la ventana de marco.

```
void LoadBarState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
Nombre de una sección en el archivo de inicialización (INI) o una clave en el registro de Windows donde se almacena la información de estado.

### <a name="remarks"></a>Observaciones

La información restaurada incluye visibilidad, orientación horizontal/vertical, estado de acoplamiento y posición de la barra de control.

La configuración que desea restaurar debe escribirse `LoadBarState`en el registro antes de llamar a . Escriba la información en el registro llamando a [CWinApp::SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey). Escriba la información en el archivo INI llamando a [SaveBarState](#savebarstate).

## <a name="cframewndloadframe"></a><a name="loadframe"></a>CFrameWnd::LoadFrame

Llame para crear dinámicamente una ventana de marco a partir de la información de recursos.

```
virtual BOOL LoadFrame(
    UINT nIDResource,
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,
    CWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parámetros

*nIDResource*<br/>
El identificador de los recursos compartidos asociados a la ventana de marco.

*dwDefaultStyle*<br/>
El [estilo](../../mfc/reference/styles-used-by-mfc.md#window-styles)del marco . Incluya el estilo FWS_ADDTOTITLE si desea que la barra de título muestre automáticamente el nombre del documento representado en la ventana.

*pParentWnd*<br/>
Un puntero al elemento primario del marco.

*pContext*<br/>
Un puntero a un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) estructura. Este parámetro puede ser NULL.

### <a name="remarks"></a>Observaciones

Construir `CFrameWnd` un objeto en dos pasos. En primer lugar, invoque `CFrameWnd` el constructor, `LoadFrame`que construye el objeto y, a continuación, llame `CFrameWnd` a , que carga la ventana de marco de Windows y los recursos asociados y adjunta la ventana de marco al objeto. El parámetro *nIDResource* especifica el menú, la tabla aceleradora, el icono y el recurso de cadena del título de la ventana de marco.

Utilice `Create` la función `LoadFrame` miembro en lugar de cuando desee especificar todos los parámetros de creación de la ventana de marco.

El marco `LoadFrame` de trabajo llama cuando crea una ventana de marco mediante un objeto de plantilla de documento.

El marco de trabajo utiliza el argumento *pContext* para especificar los objetos que se van a conectar a la ventana de marco, incluidos los objetos de vista contenidos. Puede establecer el argumento *pContext* en `LoadFrame`NULL cuando se llama a .

## <a name="cframewndm_bautomenuenable"></a><a name="m_bautomenuenable"></a>CFrameWnd::m_bAutoMenuEnable

Cuando este miembro de datos está habilitado (que es el valor predeterminado), los elementos de menú que no tienen ON_UPDATE_COMMAND_UI o ON_COMMAND controladores se deshabilitarán automáticamente cuando el usuario tire hacia abajo de un menú.

```
BOOL m_bAutoMenuEnable;
```

### <a name="remarks"></a>Observaciones

Los elementos de menú que tienen un controlador de ON_COMMAND pero ningún controlador de ON_UPDATE_COMMAND_UI se habilitarán automáticamente.

Cuando se establece este miembro de datos, los elementos de menú se habilitan automáticamente de la misma manera que se habilitan los botones de la barra de herramientas.

> [!NOTE]
> `m_bAutoMenuEnable`no tiene ningún efecto en los elementos de menú de nivel superior.

Este miembro de datos simplifica la implementación de comandos opcionales en función de la selección actual y reduce la necesidad de escribir controladores de ON_UPDATE_COMMAND_UI para habilitar y deshabilitar elementos de menú.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#3](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]

## <a name="cframewndnegotiateborderspace"></a><a name="negotiateborderspace"></a>CFrameWnd::NegotiateBorderSpace

Llame a esta función miembro para negociar el espacio de borde en una ventana de marco durante la activación de OLE inplace.

```
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,
    LPRECT lpRectBorder);
```

### <a name="parameters"></a>Parámetros

*nBorderCmd*<br/>
Contiene uno de los `enum BorderCmd`siguientes valores de:

- `borderGet` = 1

- `borderRequest` = 2

- `borderSet` = 3

*lpRectBorder*<br/>
Puntero a una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) o un [objeto CRect](../../atl-mfc-shared/reference/crect-class.md) que especifica las coordenadas del borde.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función `CFrameWnd` miembro es la implementación de la negociación de espacio fronterizo OLE.

## <a name="cframewndonbarcheck"></a><a name="onbarcheck"></a>CFrameWnd::OnBarCheck

Se llama siempre que se realiza una acción en la barra de control especificada.

```
afx_msg BOOL OnBarCheck(UINT nID);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
El identificador de la barra de control que se muestra.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si existía la barra de control; de lo contrario 0.

## <a name="cframewndoncontexthelp"></a><a name="oncontexthelp"></a>CFrameWnd::OnContextHelp

Controla la Ayuda de SHIFT+F1 para los elementos in situ.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>Observaciones

Para habilitar la ayuda contextual, debe agregar un

[!code-cpp[NVC_MFCDocViewSDI#16](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]

instrucción `CFrameWnd` al mapa de mensajes de clase y también agregar una entrada de tabla de aceleradores, normalmente SHIFT+F1, para habilitar esta función miembro.

Si la aplicación es `OnContextHelp` un contenedor OLE, coloca todos los elementos en su lugar contenidos en el objeto de ventana de marco en modo de ayuda. El cursor cambia a una flecha y un signo de interrogación, y el usuario puede mover el puntero del ratón y presionar el botón izquierdo del ratón para seleccionar un cuadro de diálogo, ventana, menú o botón de comando. Esta función miembro `WinHelp` llama a la función de Windows con el contexto de Ayuda del objeto bajo el cursor.

## <a name="cframewndoncreateclient"></a><a name="oncreateclient"></a>CFrameWnd::OnCreateClient

Llamado por el marco `OnCreate`de trabajo durante la ejecución de .

```
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parámetros

*lpcs*<br/>
Puntero a una estructura [CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw) de Windows.

*pContext*<br/>
Un puntero a un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) estructura.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Nunca llame a esta función.

La implementación predeterminada de `CView` esta función crea un objeto a partir de la información proporcionada en *pContext*, si es posible.

Invalide esta función para `CCreateContext` invalidar los valores pasados en el objeto o para cambiar la forma en que se crean los controles en el área de cliente principal de la ventana de marco. Los `CCreateContext` miembros que puede invalidar se describen en la [clase CCreateContext.](../../mfc/reference/ccreatecontext-structure.md)

> [!NOTE]
> No reemplace los valores `CREATESTRUCT` pasados en la estructura. Son sólo para uso informativo. Si desea reemplazar el rectángulo de ventana inicial, por ejemplo, reemplace la `CWnd` función miembro [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).

## <a name="cframewndonhidemenubar"></a><a name="onhidemenubar"></a>CFrameWnd::OnHideMenuBar

Esta función se llama cuando el sistema está a punto de ocultar la barra de menús en la aplicación MFC actual.

```
virtual void OnHideMenuBar();
```

### <a name="remarks"></a>Observaciones

Este controlador de eventos permite a la aplicación realizar acciones personalizadas cuando el sistema está a punto de ocultar el menú. No puede evitar que el menú se ostique, pero puede, por ejemplo, llamar a otros métodos para recuperar el estilo o estado del menú.

## <a name="cframewndonsetpreviewmode"></a><a name="onsetpreviewmode"></a>CFrameWnd::OnSetPreviewMode

Llame a esta función miembro para establecer la ventana de marco principal de la aplicación dentro y fuera del modo de vista previa de impresión.

```
virtual void OnSetPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>Parámetros

*bVista previa*<br/>
Especifica si se debe colocar o no la aplicación en modo de vista previa de impresión. Establézcalo en TRUE para colocarlo en la vista previa de impresión, FALSE para cancelar el modo de vista previa.

*pState*<br/>
Un puntero `CPrintPreviewState` a una estructura.

### <a name="remarks"></a>Observaciones

La implementación predeterminada deshabilita todas las barras de herramientas estándar y oculta el menú principal y la ventana principal del cliente. Esto convierte las ventanas de marco MDI en ventanas de marco SDI temporales.

Invalide esta función miembro para personalizar la ocultación y la visualización de barras de control y otras partes de la ventana de marco durante la vista previa de impresión. Llame a la implementación de la clase base desde dentro de la versión reemplazada.

## <a name="cframewndonshowmenubar"></a><a name="onshowmenubar"></a>CFrameWnd::OnShowMenuBar

Esta función se llama cuando el sistema está a punto de mostrar la barra de menús en la aplicación MFC actual.

```
virtual void OnShowMenuBar();
```

### <a name="remarks"></a>Observaciones

Este controlador de eventos permite a la aplicación realizar acciones personalizadas cuando el menú está a punto de mostrarse. No puede impedir que se muestre el menú, pero puede, por ejemplo, llamar a otros métodos para recuperar el estilo o estado del menú.

## <a name="cframewndonupdatecontrolbarmenu"></a><a name="onupdatecontrolbarmenu"></a>CFrameWnd::OnUpdateControlBarMenu

Llamado por el marco de trabajo cuando se actualiza el menú asociado.

```
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Puntero a un objeto [CCmdUI](../../mfc/reference/ccmdui-class.md) que representa el menú que generó el comando update. El controlador de [Enable](../../mfc/reference/ccmdui-class.md#enable) actualización llama `CCmdUI` a la Enable función miembro del objeto a través de *pCmdUI* para actualizar la interfaz de usuario.

## <a name="cframewndrecalclayout"></a><a name="recalclayout"></a>CFrameWnd::RecalcLayout

Llamado por el marco de trabajo cuando las barras de control estándar están activadas o desactivadas o cuando se cambia el tamaño de la ventana de marco.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parámetros

*bNotificar*<br/>
Determina si el elemento activo en el lugar de la ventana de marco recibe una notificación del cambio de diseño. Si es TRUE, se notifica el elemento; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de `CWnd` esta `RepositionBars` función miembro llama a la función miembro para cambiar la `CView` posición de todas las barras de control en el marco, así como en la ventana de cliente principal (normalmente a o MDICLIENT).

Invalide esta función miembro para controlar la apariencia y el comportamiento de las barras de control después de que el diseño de la ventana de marco ha cambiado. Por ejemplo, llámelo cuando active o desactive las barras de control o agregue otra barra de control.

## <a name="cframewndrectdefault"></a><a name="rectdefault"></a>CFrameWnd::rectDefault

Pase esta `CRect` estática como parámetro al crear una ventana para permitir que Windows elija el tamaño y la posición iniciales de la ventana.

```
static AFX_DATA const CRect rectDefault;
```

## <a name="cframewndsavebarstate"></a><a name="savebarstate"></a>CFrameWnd::SaveBarState

Llame a esta función para almacenar información sobre cada barra de control propiedad de la ventana de marco.

```
void SaveBarState(LPCTSTR lpszProfileName) const;
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
Nombre de una sección en el archivo de inicialización o una clave en el registro de Windows donde se almacena la información de estado.

### <a name="remarks"></a>Observaciones

Esta información se puede leer desde el archivo de inicialización mediante [LoadBarState](#loadbarstate). La información almacenada incluye visibilidad, orientación horizontal/vertical, estado de acoplamiento y posición de la barra de control.

## <a name="cframewndsetactivepreviewview"></a><a name="setactivepreviewview"></a>CFrameWnd::SetActivePreviewView

Designa la vista especificada para que sea la vista activa de Vista preliminar enriquecida.

```
void SetActivePreviewView(CView* pViewNew);
```

### <a name="parameters"></a>Parámetros

*pViewNew*<br/>
Puntero a una vista que se va a activar.

### <a name="remarks"></a>Observaciones

## <a name="cframewndsetactiveview"></a><a name="setactiveview"></a>CFrameWnd::SetActiveView

Llame a esta función miembro para establecer la vista activa.

```
void SetActiveView(
    CView* pViewNew,
    BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parámetros

*pViewNew*<br/>
Especifica un puntero a un [CView](../../mfc/reference/cview-class.md) objeto o NULL para ninguna vista activa.

*bNotificar*<br/>
Especifica si se debe notificar la activación a la vista. Si TRUE, `OnActivateView` se llama para la nueva vista; si FALSE, no lo es.

### <a name="remarks"></a>Observaciones

El marco de trabajo llamará a esta función automáticamente a medida que el usuario cambia el foco a una vista dentro de la ventana de marco. Puede llamar `SetActiveView` explícitamente para cambiar el foco a la vista especificada.

## <a name="cframewndsetdockstate"></a><a name="setdockstate"></a>CFrameWnd::SetDockState

Llame a esta función miembro `CDockState` para aplicar información de estado almacenada en un objeto a las barras de control de la ventana de marco.

```
void SetDockState(const CDockState& state);
```

### <a name="parameters"></a>Parámetros

*state*<br/>
Aplique el estado almacenado a las barras de control de la ventana de marco.

### <a name="remarks"></a>Observaciones

Para restaurar un estado anterior de las barras de `CDockState::LoadState` `Serialize`control, `SetDockState` puede cargar el estado almacenado con o , a continuación, utilizar para aplicarlo a las barras de control de la ventana de marco. El estado anterior se `CDockState` almacena en el objeto con`GetDockState`

## <a name="cframewndsetmenubarstate"></a><a name="setmenubarstate"></a>CFrameWnd::SetMenuBarState

Establece el estado de visualización del menú en la aplicación MFC actual en oculto o mostrado.

```
virtual BOOL SetMenuBarState(DWORD nState);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*nEstado*|[en] Especifica si se debe mostrar u ocultar el menú. El parámetro *nState* puede tener los siguientes valores:<br /><br />- AFX_MBS_VISIBLE (0x01): muestra el menú si está oculto, pero no tiene ningún efecto si está visible.<br />- AFX_MBS_HIDDEN (0x02) - Oculta el menú si está visible, pero no tiene ningún efecto si está oculto.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método cambia correctamente el estado del menú; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Si se produce un error en tiempo de ejecución, este método afirma en modo de depuración y genera una excepción derivada de la [CException](../../mfc/reference/cexception-class.md) clase.

## <a name="cframewndsetmenubarvisibility"></a><a name="setmenubarvisibility"></a>CFrameWnd::SetMenuBarVisibility

Establece el comportamiento predeterminado del menú en la aplicación MFC actual para que sea oculto o visible.

```
virtual void SetMenuBarVisibility(DWORD nStyle);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*nStyle*|[en] Especifica si el menú está oculto de forma predeterminada o está visible y tiene el foco. El *nStyle* parámetro puede tener los siguientes valores:<br /><br />- AFX_MBV_KEEPVISIBLE (0x01) -<br />     El menú se muestra en todo momento y, de forma predeterminada, no tiene el foco.<br />- AFX_MBV_DISPLAYONFOCUS (0x02) -<br />     El menú está oculto de forma predeterminada. Si el menú está oculto, presione la tecla ALT para mostrar el menú y darle el foco. Si se muestra el menú, pulse la tecla ALT o ESC para ocultar el menú.<br />- AFX_MBV_ AFX_MBV_DISPLAYONF10 de &#124; DISPLAYONFOCUS (0x02) (0x04)<br />     (combinación bit a bit (OR)) - El menú está oculto por defecto. Si el menú está oculto, presione la tecla F10 para mostrar el menú y darle el foco. Si se muestra el menú, pulse la tecla F10 para activar o desactivar el enfoque en el menú. El menú se muestra hasta que pulse la tecla ALT o ESC para ocultarlo.|

### <a name="remarks"></a>Observaciones

Si el valor de la *nStyle* parámetro no es válido, este método afirma en modo de depuración y genera [CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md) en modo de versión. En caso de otros errores en tiempo de ejecución, este método afirma en modo de depuración y genera una excepción derivada de la [CException](../../mfc/reference/cexception-class.md) clase.

Este método afecta al estado de los menús de las aplicaciones escritas para Windows Vista y versiones posteriores.

## <a name="cframewndsetmessagetext"></a><a name="setmessagetext"></a>CFrameWnd::SetMessageText

Llame a esta función para colocar una cadena en el panel de barra de estado que tiene un identificador de 0.

```
void SetMessageText(LPCTSTR lpszText);
void SetMessageText(UINT nID);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
Apunta a la cadena que se va a colocar en la barra de estado.

*nID*<br/>
Identificador de recurso de cadena de la cadena que se va a colocar en la barra de estado.

### <a name="remarks"></a>Observaciones

Normalmente, este es el panel más a la izquierda y más largo de la barra de estado.

## <a name="cframewndsetprogressbarposition"></a><a name="setprogressbarposition"></a>CFrameWnd::SetProgressBarPosition

Establece la posición actual de la barra de progreso de Windows 7 que se muestra en la barra de tareas.

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Parámetros

*nProgressPos*<br/>
Especifica la posición que se va a establecer. Debe estar dentro del `SetProgressBarRange`rango establecido por .

### <a name="remarks"></a>Observaciones

## <a name="cframewndsetprogressbarrange"></a><a name="setprogressbarrange"></a>CFrameWnd::SetProgressBarRange

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

### <a name="remarks"></a>Observaciones

## <a name="cframewndsetprogressbarstate"></a><a name="setprogressbarstate"></a>CFrameWnd::SetProgressBarState

Establece el tipo y el estado del indicador de progreso que se muestra en un botón de la barra de tareas.

```
void SetProgressBarState(TBPFLAG tbpFlags);
```

### <a name="parameters"></a>Parámetros

*tbpFlags*<br/>
Indicadores que controlan el estado actual del botón de progreso. Especifique solo uno de los siguientes indicadores porque todos los estados son mutuamente excluyentes: TBPF_NOPROGRESS, TBPF_INDETERMINATE, TBPF_NORMAL, TBPF_ERROR TBPF_PAUSED.

### <a name="remarks"></a>Observaciones

## <a name="cframewndsettaskbaroverlayicon"></a><a name="settaskbaroverlayicon"></a>CFrameWnd::SetTaskbarOverlayIcon

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
Especifica el identificador de recurso de un icono que se usará como superposición. Consulte la descripción de *hIcon* para obtener más información.

*lpcszDescr*<br/>
Puntero a una cadena que proporciona una versión de texto alternativo de la información transmitida por la superposición, con fines de accesibilidad.

*hIcon*<br/>
El identificador de un icono que se va a utilizar como superposición. Debe ser un icono pequeño, que mide 16x16 píxeles a 96 puntos por pulgada (dpi). Si ya se aplica un icono de superposición al botón de la barra de tareas, se reemplazará esa superposición existente. Este valor puede ser NULL. La forma en que se controla un valor NULL depende de si el botón de la barra de tareas representa una sola ventana o un grupo de ventanas. Es responsabilidad de la aplicación de llamada liberar *hIcon* cuando ya no es necesario.

### <a name="return-value"></a>Valor devuelto

TRUESi se realiza correctamente; FALSE si la versión del sistema operativo es menor que Windows 7 o si se produce un error al establecer el icono.

### <a name="remarks"></a>Observaciones

## <a name="cframewndsettitle"></a><a name="settitle"></a>CFrameWnd::SetTitle

Establece el título del objeto de ventana.

```
void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Parámetros

*lpszTitle*<br/>
Puntero a una cadena de caracteres que contiene el título del objeto de ventana.

## <a name="cframewndshowcontrolbar"></a><a name="showcontrolbar"></a>CFrameWnd::ShowControlBar

Llame a esta función miembro para mostrar u ocultar la barra de control.

```
void ShowControlBar(
    CControlBar* pBar,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
Puntero a la barra de control que se mostrará u ocultará.

*bMostrar*<br/>
Si TRUE, especifica que se va a mostrar la barra de control. Si FALSE, especifica que la barra de control se va a ocultar.

*bDelay*<br/>
Si es TRUE, retrase la visualización de la barra de control. Si FALSE, muestre la barra de control inmediatamente.

## <a name="cframewndshowownedwindows"></a><a name="showownedwindows"></a>CFrameWnd::ShowOwnedWindows

Llame a esta función miembro para mostrar `CFrameWnd` todas las ventanas que son descendientes del objeto.

```
void ShowOwnedWindows(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bMostrar*<br/>
Especifica si las ventanas de propiedad deben mostrarse u ocultarse.

## <a name="see-also"></a>Consulte también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd (clase)](../../mfc/reference/cmdiframewnd-class.md)<br/>
[CMDIChildWnd (clase)](../../mfc/reference/cmdichildwnd-class.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)<br/>
[Estructura CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)
