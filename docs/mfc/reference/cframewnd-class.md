---
title: CFrameWnd (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFrameWnd
dev_langs:
- C++
helpviewer_keywords:
- frame window classes, base class
- single document interface (SDI), frame windows
- frame windows, creating
- CFrameWnd class
ms.assetid: e2220aba-5bf4-4002-b960-fbcafcad01f1
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a8df28ed10208973832476b68140594c206bc22b
ms.lasthandoff: 02/24/2017

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
|[CFrameWnd::ActivateFrame](#activateframe)|Hace que el marco visibles y disponibles para el usuario.|  
|[CFrameWnd::BeginModalState](#beginmodalstate)|Establece la ventana de marco en modal.|  
|[CFrameWnd::Create](#create)|Llamada a crear e inicializar la ventana de marco de Windows asociada a la `CFrameWnd` objeto.|  
|[CFrameWnd::CreateView](#createview)|Crea una vista dentro de un marco que no se derive de `CView`.|  
|[CFrameWnd:: DockControlBar](#dockcontrolbar)|Acopla la barra de control.|  
|[CFrameWnd:: EnableDocking](#enabledocking)|Permite acoplar una barra de controles.|  
|[CFrameWnd::EndModalState](#endmodalstate)|Finaliza el estado de la ventana de marco modal. Habilita todas las ventanas que se deshabilitó `BeginModalState`.|  
|[CFrameWnd:: FloatControlBar](#floatcontrolbar)|Desplaza una barra de controles.|  
|[CFrameWnd::GetActiveDocument](#getactivedocument)|Devuelve el activo **CDocument** objeto.|  
|[CFrameWnd::GetActiveFrame](#getactiveframe)|Devuelve el activo `CFrameWnd` objeto.|  
|[CFrameWnd::GetActiveView](#getactiveview)|Devuelve el activo `CView` objeto.|  
|[CFrameWnd::GetControlBar](#getcontrolbar)|Recupera la barra de control.|  
|[CFrameWnd::GetDockState](#getdockstate)|Recupera el estado de acoplamiento de una ventana de marco.|  
|[CFrameWnd::GetMenuBarState](#getmenubarstate)|Recupera el estado de visualización del menú de la aplicación MFC actual.|  
|[CFrameWnd::GetMenuBarVisibility](#getmenubarvisibility)|Indica si el comportamiento predeterminado del menú de la aplicación MFC actual está oculto o visible.|  
|[CFrameWnd::GetMessageBar](#getmessagebar)|Devuelve un puntero a la que pertenece a la ventana de marco de la barra de estado.|  
|[CFrameWnd:: GetMessageString](#getmessagestring)|Recupera el mensaje correspondiente a un identificador de comando.|  
|[CFrameWnd::GetTitle](#gettitle)|Recupera el título de la barra de controles relacionados.|  
|[CFrameWnd::InitialUpdateFrame](#initialupdateframe)|Hace que el `OnInitialUpdate` función miembro que pertenecen a todas las vistas en la ventana de marco que se llame.|  
|[CFrameWnd::InModalState](#inmodalstate)|Devuelve un valor que indica si es o no una ventana de marco en un estado modal.|  
|[CFrameWnd::IsTracking](#istracking)|Determina si actualmente se está moviendo barra divisora.|  
|[CFrameWnd::LoadAccelTable](#loadacceltable)|Llamada para cargar una tabla de aceleradores.|  
|[CFrameWnd:: LoadBarState](#loadbarstate)|Llamada a restaurar la configuración de la barra de control.|  
|[CFrameWnd::LoadFrame](#loadframe)|Llamada a crear dinámicamente una ventana de marco de información de recursos.|  
|[CFrameWnd::NegotiateBorderSpace](#negotiateborderspace)|Negocia espacio del borde de la ventana de marco.|  
|[CFrameWnd::OnBarCheck](#onbarcheck)|Se llama siempre que se realiza una acción en la barra de control especificado.|  
|[CFrameWnd::OnContextHelp](#oncontexthelp)|Controla MAYÚS + F1 Ayuda para artículos en contexto.|  
|[CFrameWnd::OnSetPreviewMode](#onsetpreviewmode)|Establece la ventana de marco principal de la aplicación dentro y fuera del modo de vista previa de impresión.|  
|[CFrameWnd::OnUpdateControlBarMenu](#onupdatecontrolbarmenu)|Llamado por el marco de trabajo cuando se actualiza el menú asociado.|  
|[RecalcLayout](#recalclayout)|Cambia de posición de las barras de control de la `CFrameWnd` objeto.|  
|[CFrameWnd:: SaveBarState](#savebarstate)|Llaman para guardar la configuración de la barra de control.|  
|[CFrameWnd::SetActivePreviewView](#setactivepreviewview)|Designa la vista especificada sea la vista activa de la vista previa avanzada.|  
|[CFrameWnd::SetActiveView](#setactiveview)|Establece el activo `CView` objeto.|  
|[CFrameWnd::SetDockState](#setdockstate)|Llamada a acoplar la ventana de marco en la ventana principal.|  
|[CFrameWnd::SetMenuBarState](#setmenubarstate)|Establece el estado de visualización del menú de la aplicación MFC actual oculta o muestra.|  
|[CFrameWnd::SetMenuBarVisibility](#setmenubarvisibility)|Establece el comportamiento predeterminado del menú de la aplicación MFC actual para que esté visible u oculto.|  
|[CFrameWnd::SetMessageText](#setmessagetext)|Establece el texto de una barra de estado estándar.|  
|[CFrameWnd::SetProgressBarPosition](#setprogressbarposition)|Establece la posición actual de la barra de progreso de Windows 7 que se muestran en la barra de tareas.|  
|[CFrameWnd::SetProgressBarRange](#setprogressbarrange)|Establece el intervalo de muestra en la barra de tareas de la barra de progreso de Windows 7.|  
|[CFrameWnd::SetProgressBarState](#setprogressbarstate)|Establece el tipo y el estado del indicador de progreso mostrado en un botón de barra de tareas.|  
|[CFrameWnd::SetTaskbarOverlayIcon](#settaskbaroverlayicon)|Sobrecargado. Se aplica una superposición a un botón de barra de tareas para indicar el estado de la aplicación o una notificación al usuario.|  
|[CFrameWnd::SetTitle](#settitle)|Establece el título de la barra de controles relacionados.|  
|[CFrameWnd::ShowControlBar](#showcontrolbar)|La llamada para mostrar la barra de control.|  
|[CFrameWnd::ShowOwnedWindows](#showownedwindows)|Muestra todas las ventanas que son descendientes de los `CFrameWnd` objeto.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFrameWnd::OnCreateClient](#oncreateclient)|Crea una ventana de cliente para el marco.|  
|[CFrameWnd::OnHideMenuBar](#onhidemenubar)|Se llama antes de que el menú de la aplicación MFC actual está oculto.|  
|[CFrameWnd::OnShowMenuBar](#onshowmenubar)|Se llama antes de que se muestre el menú de la aplicación MFC actual.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFrameWnd::m_bAutoMenuEnable](#m_bautomenuenable)|Controles automática habilitar y deshabilitar la funcionalidad de los elementos de menú.|  
|[CFrameWnd::rectDefault](#rectdefault)|Pasar estático `CRect` como un parámetro al crear un `CFrameWnd` objeto para permitir que Windows elija el tamaño inicial y la posición de la ventana.|  
  
## <a name="remarks"></a>Comentarios  
 Para crear una ventana de marco útiles para su aplicación, derive una clase de `CFrameWnd`. Agregar variables miembro a la clase derivada para almacenar datos específicos de la aplicación. Implemente funciones miembro de controlador de mensajes y un mapa de mensajes en la clase derivada para especificar qué ocurre cuando los mensajes se dirigen a la ventana.  
  
 Hay tres formas de crear una ventana de marco:  
  
-   Crear directamente mediante [crear](#create).  
  
-   Crear directamente mediante [LoadFrame](#loadframe).  
  
-   Construir indirectamente mediante una plantilla de documento.  
  
 Antes de llamar a cualquiera **crear** o `LoadFrame`, debe crear el objeto de ventana de marco en el montón mediante C++ **nuevo** operador. Antes de llamar a **crear**, también puede registrar una clase de ventana con el [AfxRegisterWndClass](../../mfc/reference/application-information-and-management.md#afxregisterwndclass) función global para establecer los estilos de icono y de clase para el marco.  
  
 Utilice la **crear** función miembro para pasar los parámetros de creación del marco inmediatas como argumentos.  
  
 `LoadFrame`requiere menos argumentos que **crear**y en su lugar recupera la mayor parte de sus valores predeterminados de recursos, como el título del marco, icono, tabla de aceleradores y menús. Para tener acceso a `LoadFrame`, todos estos recursos deben tener el mismo identificador de recursos (por ejemplo, **IDR_MAINFRAME**).  
  
 Cuando un `CFrameWnd` objeto contiene documentos y vistas, que se crean indirectamente mediante el marco de trabajo en lugar de directamente por el programador. La `CDocTemplate` objeto organiza la creación del marco, la creación de las vistas que contienen y la conexión de las vistas para el documento adecuado. Los parámetros de la `CDocTemplate` constructor especifica la `CRuntimeClass` de las tres clases implicadas (documento, marco y ver). Un `CRuntimeClass` objeto se utiliza el marco de trabajo para crear dinámicamente nuevos marcos al especificado por el usuario (por ejemplo, mediante el comando nuevo archivo o el comando nueva ventana de varios documentos MDI (interfaz)).  
  
 Deriva una clase de ventana de marco `CFrameWnd` deben declararse con `DECLARE_DYNCREATE` en orden para los sistemas anteriores `RUNTIME_CLASS` mecanismo funcione correctamente.  
  
 Un `CFrameWnd` contiene implementaciones predeterminadas para realizar las siguientes funciones de la ventana principal en una aplicación típica de Windows:  
  
-   Un `CFrameWnd` ventana de marco hace un seguimiento de una vista activa es independiente de la ventana activa de Windows o el foco de entrada actual. Cuando se reactive el marco, la vista activa es una notificación mediante una llamada a `CView::OnActivateView`.  
  
-   Comando mensajes y muchos mensajes de notificación de marco comunes, incluidos los controlados por la `OnSetFocus`, `OnHScroll`, y `OnVScroll` funciones de `CWnd`, se delegan por un `CFrameWnd` ventana de marco en la vista activa.  
  
-   La vista activa (o la ventana de marco de secundario MDI activo actualmente en el caso de un marco de MDI) puede determinar el título de la ventana de marco. Esta característica se puede deshabilitar si se desactiva la **FWS_ADDTOTITLE** bit de estilo de la ventana de marco.  
  
-   Un `CFrameWnd` ventana de marco administra la posición de las barras de control, vistas y otras ventanas secundarias dentro del área de cliente de la ventana de marco. Una ventana de marco también realiza la actualización de tiempo de inactividad de la barra de herramientas y otros botones de barra de control. Un `CFrameWnd` ventana de marco también tiene implementaciones predeterminadas de los comandos para alternar activar y desactivar la barra de herramientas y barra de estado.  
  
-   Un `CFrameWnd` ventana de marco administra la barra de menús principal. Cuando se muestra un menú emergente, se utiliza la ventana de marco del **UPDATE_COMMAND_UI** mecanismo para determinar qué elementos de menú deben ser habilitados, deshabilitados o activadas. Cuando el usuario selecciona un elemento de menú, en la ventana de marco se actualiza la barra de estado con la cadena de mensaje para ese comando.  
  
-   Un `CFrameWnd` ventana de marco posee una tabla de aceleradores opcional que traduce automáticamente los aceleradores de teclado.  
  
-   Un `CFrameWnd` ventana de marco tiene un identificador de ayuda opcional establecida con `LoadFrame` que se usa para la Ayuda contextual. Una ventana de marco es el principal orchestrator de Estados semimodales, como ayuda contextual (MAYÚS + F1) y modos de vista previa de impresión.  
  
-   Un `CFrameWnd` ventana de marco abrirá un archivo desde el Administrador de archivos de arrastrar y colocar en la ventana de marco. Si una extensión de archivo registrada y asociada con la aplicación, la ventana de marco responde a la solicitud de apertura dinámico de datos (DDE) de exchange que se produce cuando el usuario abre un archivo de datos en el Administrador de archivos o el **ShellExecute** se llama la función de Windows.  
  
-   Si la ventana de marco es la ventana principal de la aplicación (es decir, `CWinThread::m_pMainWnd`), cuando el usuario cierra la aplicación, la ventana de marco pide al usuario que guarde los documentos modificados (para `OnClose` y `OnQueryEndSession`).  
  
-   Si la ventana de marco es la ventana principal de la aplicación, la ventana de marco es el contexto para la ejecución de WinHelp. Cierre la ventana de marco se apagará WINHELP. EXE si se ha iniciado para obtener ayuda para esta aplicación.  
  
 No use C++ **eliminar** operador para destruir una ventana de marco. Utilice `CWnd::DestroyWindow` en su lugar. El `CFrameWnd` implementación de `PostNcDestroy` eliminará el objeto de C++ cuando se destruye la ventana. Cuando el usuario cierra la ventana de marco, el valor predeterminado `OnClose` controlador llamará `DestroyWindow`.  
  
 Para obtener más información sobre `CFrameWnd`, consulte [ventanas de marco](../../mfc/frame-windows.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CFrameWnd`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="a-nameactivateframea--cframewndactivateframe"></a><a name="activateframe"></a>CFrameWnd::ActivateFrame  
 Llame a esta función miembro para activar y restaurar la ventana de marco para que sea visible y disponible para el usuario.  
  
```  
virtual void ActivateFrame(int nCmdShow = -1);
```  
  
### <a name="parameters"></a>Parámetros  
 `nCmdShow`  
 Especifica el parámetro que se pasa a [CWnd:: ShowWindow](../../mfc/reference/cwnd-class.md#showwindow). De forma predeterminada, el marco es que se muestra y restaurado correctamente.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente se llama a esta función miembro después de un evento de interfaz de usuario no como DDE, OLE u otro evento que se puede mostrar la ventana de marco o su contenido al usuario.  
  
 La implementación predeterminada activa el marco y pone en la parte superior del orden Z y, si es necesario, lleva a cabo los mismos pasos para la ventana de marco principal de la aplicación.  
  
 Reemplace esta función miembro para cambiar cómo se activa un marco. Por ejemplo, puede forzar ventanas secundarias MDI maximizarse. Agregar la funcionalidad adecuada, a continuación, llame a la versión de la clase base con un `nCmdShow`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[1 NVC_MFCWindowing](../../mfc/reference/codesnippet/cpp/cframewnd-class_1.cpp)]  
  
##  <a name="a-namebeginmodalstatea--cframewndbeginmodalstate"></a><a name="beginmodalstate"></a>CFrameWnd::BeginModalState  
 Llame a esta función miembro para convertir una ventana marco en modal.  
  
```  
virtual void BeginModalState();
```  
  
##  <a name="a-namecframewnda--cframewndcframewnd"></a><a name="cframewnd"></a>CFrameWnd::CFrameWnd  
 Construye un `CFrameWnd` el objeto, pero no crea la ventana de marco visibles.  
  
```  
CFrameWnd();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a **crear** para crear la ventana visible.  
  
##  <a name="a-namecreatea--cframewndcreate"></a><a name="create"></a>CFrameWnd::Create  
 Llamada a crear e inicializar la ventana de marco de Windows asociada a la `CFrameWnd` objeto.  
  
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
 `lpszClassName`  
 Apunta a una cadena de caracteres terminada en null que los nombres de la clase de Windows. El nombre de clase puede ser cualquier nombre registrado con el `AfxRegisterWndClass` función global o **RegisterClass** función de Windows. Si **NULL**, utiliza el valor predeterminado predefinido `CFrameWnd` atributos.  
  
 `lpszWindowName`  
 Apunta a una cadena de caracteres terminada en null que representa el nombre de la ventana. Se utiliza como texto de la barra de título.  
  
 `dwStyle`  
 Especifica el período de [estilo](../../mfc/reference/window-styles.md) atributos. Incluir el **FWS_ADDTOTITLE** si desea que la barra de título para mostrar automáticamente el nombre del documento representado en la ventana de estilo.  
  
 `rect`  
 Especifica el tamaño y la posición de la ventana. El `rectDefault` valor permite a Windows especificar el tamaño y la posición de la nueva ventana.  
  
 `pParentWnd`  
 Especifica la ventana primaria de esta ventana de marco. Este parámetro debe ser **NULL** para ventanas de marco de nivel superior.  
  
 *lpszMenuName*  
 Identifica el nombre del recurso de menú que se usará con la ventana. Utilice **MAKEINTRESOURCE** si el menú tiene un identificador entero en lugar de una cadena. Este parámetro puede ser **NULL**.  
  
 `dwExStyle`  
 Especifica el período extendido [estilo](../../mfc/reference/extended-window-styles.md) atributos.  
  
 `pContext`  
 Especifica un puntero a un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) estructura. Este parámetro puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la inicialización es correcta; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Construir un `CFrameWnd` objeto en dos pasos. En primer lugar, invocar el constructor, que construye la `CFrameWnd` de objetos y, a continuación, llame a **crear**, que crea la ventana de marco de Windows y lo adjunta a la `CFrameWnd` objeto. **Crear** inicializa el nombre de clase y el nombre de la ventana de la ventana y registra los valores predeterminados de su estilo, el primario y el menú asociado.  
  
 Utilice `LoadFrame` en lugar de **crear** para cargar la ventana de marco de un recurso en lugar de especificar sus argumentos.  
  
##  <a name="a-namecreateviewa--cframewndcreateview"></a><a name="createview"></a>CFrameWnd::CreateView  
 Llame a `CreateView` para crear una vista dentro de un marco.  
  
```  
CWnd* CreateView(
    CCreateContext* pContext,  
    UINT nID = AFX_IDW_PANE_FIRST);
```  
  
### <a name="parameters"></a>Parámetros  
 `pContext`  
 Especifica el tipo de documento y vista.  
  
 `nID`  
 El número de Id. de una vista.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un `CWnd` objeto si se realiza correctamente; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función miembro para crear "vistas" que no son `CView`-derivadas dentro de un marco. Después de llamar a `CreateView`, debe establecer la vista activa manualmente y establecer que sea visible; estas tareas no se realizan automáticamente por `CreateView`.  
  
##  <a name="a-namedockcontrolbara--cframewnddockcontrolbar"></a><a name="dockcontrolbar"></a>CFrameWnd:: DockControlBar  
 Hace que una barra de controles acoplada a la ventana de marco.  
  
```  
void DockControlBar(
    CControlBar* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pBar`  
 Apunta a acoplar la barra de control.  
  
 `nDockBarID`  
 Determina qué lados de la ventana de marco que considere la posibilidad de acoplamiento. Puede ser 0, o uno o varios de los siguientes:  
  
- `AFX_IDW_DOCKBAR_TOP`Acoplar en la parte superior de la ventana de marco.  
  
- **AFX_IDW_DOCKBAR_BOTTOM** acoplar en el lado inferior de la ventana de marco.  
  
- `AFX_IDW_DOCKBAR_LEFT`Acoplar en el lado izquierdo de la ventana de marco.  
  
- `AFX_IDW_DOCKBAR_RIGHT`Acoplar a la derecha de la ventana de marco.  
  
 Si es 0, la barra de control se puede acoplar a cualquier lado habilitado para el acoplamiento en la ventana de marco de destino.  
  
 `lpRect`  
 Determina, en coordenadas de pantalla, donde se acoplará la barra de control en el área no cliente de la ventana de marco de destino.  
  
### <a name="remarks"></a>Comentarios  
 La barra de control se acoplará a uno de los lados de la ventana de marco especificado en las llamadas a ambos [CControlBar:: EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking) y [CFrameWnd:: EnableDocking](#enabledocking). El lado elegido viene determinado por `nDockBarID`.  
  
##  <a name="a-nameenabledockinga--cframewndenabledocking"></a><a name="enabledocking"></a>CFrameWnd:: EnableDocking  
 Llame a esta función para habilitar las barras de control acoplable en una ventana de marco.  
  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDockStyle`  
 Especifica qué lados de la ventana de marco pueden servir como sitios de barras de control de acoplamiento. Puede ser uno o varios de los siguientes:  
  
- `CBRS_ALIGN_TOP`Permite acoplar en la parte superior del área cliente.  
  
- `CBRS_ALIGN_BOTTOM`Permite acoplar en la parte inferior del área de cliente.  
  
- `CBRS_ALIGN_LEFT`Permite acoplar en el lado izquierdo del área cliente.  
  
- `CBRS_ALIGN_RIGHT`Permite acoplar en el lado derecho del área de cliente.  
  
- `CBRS_ALIGN_ANY`Permite acoplar en cualquier lado del área de cliente.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, las barras de control estará acopladas a un lado de la ventana de marco en el siguiente orden: superior, inferior, izquierda, derecha.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CToolBar:: Create](../../mfc/reference/ctoolbar-class.md#create).  
  
##  <a name="a-nameendmodalstatea--cframewndendmodalstate"></a><a name="endmodalstate"></a>CFrameWnd::EndModalState  
 Llame a esta función miembro para cambiar una ventana marco de modal a no modal.  
  
```  
virtual void EndModalState();
```  
  
### <a name="remarks"></a>Comentarios  
 `EndModalState`habilita todas las ventanas que se deshabilitó [BeginModalState](#beginmodalstate).  
  
##  <a name="a-namefloatcontrolbara--cframewndfloatcontrolbar"></a><a name="floatcontrolbar"></a>CFrameWnd:: FloatControlBar  
 Llame a esta función para hacer que una barra de controles no se puede acoplar a la ventana de marco.  
  
```  
void FloatControlBar(
    CControlBar* pBar,  
    CPoint point,  
    DWORD dwStyle = CBRS_ALIGN_TOP);
```  
  
### <a name="parameters"></a>Parámetros  
 `pBar`  
 Puntos de la barra de controles flotar.  
  
 `point`  
 La ubicación, en coordenadas de pantalla, donde se colocará la esquina superior izquierda de la barra de control.  
  
 `dwStyle`  
 Especifica si se debe alinear la barra de control horizontal o verticalmente, dentro de su nueva ventana de marco. Puede ser cualquiera de las siguientes acciones:  
  
- `CBRS_ALIGN_TOP`Orienta verticalmente la barra de control.  
  
- `CBRS_ALIGN_BOTTOM`Orienta verticalmente la barra de control.  
  
- `CBRS_ALIGN_LEFT`Orienta horizontalmente la barra de control.  
  
- `CBRS_ALIGN_RIGHT`Orienta horizontalmente la barra de control.  
  
 Si se pasan estilos especificando la orientación horizontal y vertical, la barra de herramientas se va a orientar horizontalmente.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, esto se hace al iniciarse la aplicación cuando el programa es restaurar la configuración de la ejecución anterior.  
  
 El marco de trabajo llama a esta función cuando el usuario da lugar a una operación de colocar soltar el botón primario del mouse mientras arrastra el puntero sobre una ubicación que no está disponible para acoplar la barra de control.  
  
##  <a name="a-namegetactivedocumenta--cframewndgetactivedocument"></a><a name="getactivedocument"></a>CFrameWnd::GetActiveDocument  
 Llame a esta función miembro para obtener un puntero a la actual **CDocument** conectado a la vista activa actual.  
  
```  
virtual CDocument* GetActiveDocument();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la actual [CDocument](../../mfc/reference/cdocument-class.md). Si no hay ningún documento actual, devuelve **NULL**.  
  
##  <a name="a-namegetactiveframea--cframewndgetactiveframe"></a><a name="getactiveframe"></a>CFrameWnd::GetActiveFrame  
 Llame a esta función miembro para obtener un puntero al activo varios documentos ventana MDI (interfaz) secundario de una ventana de marco MDI.  
  
```  
virtual CFrameWnd* GetActiveFrame();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la ventana secundaria MDI activa. Si la aplicación es una aplicación SDI, o la ventana de marco MDI no tiene ningún documento activo, la parte implícita **esto** se devolverá el puntero.  
  
### <a name="remarks"></a>Comentarios  
 Si no hay ningún formulario secundario MDI activo o la aplicación es una interfaz de único documento (SDI), la parte implícita **esto** devuelve el puntero.  
  
##  <a name="a-namegetactiveviewa--cframewndgetactiveview"></a><a name="getactiveview"></a>CFrameWnd::GetActiveView  
 Llame a esta función miembro para obtener un puntero a la vista activa (si existe) asociado a una ventana de marco ( `CFrameWnd`).  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la actual [CView](../../mfc/reference/cview-class.md). Si no hay ninguna vista actual, devuelve **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función devuelve **NULL** cuando llama a una ventana de marco principal MDI ( `CMDIFrameWnd`). En una aplicación MDI, la ventana de marco principal MDI no tiene una vista asociada. En su lugar, cada ventana secundarios individuales ( `CMDIChildWnd`) tiene una o varias vistas asociadas. Primero debe encontrar la ventana secundaria MDI activa y, a continuación, buscando la vista activa para esa ventana secundaria se puede obtener la vista activa en una aplicación MDI. La ventana secundaria MDI activa puede encontrarse llamando a la función `MDIGetActive` o **GetActiveFrame** como se muestra en la siguiente:  
  
 [!code-cpp[NVC_MFCWindowing&#2;](../../mfc/reference/codesnippet/cpp/cframewnd-class_2.cpp)]  
  
##  <a name="a-namegetcontrolbara--cframewndgetcontrolbar"></a><a name="getcontrolbar"></a>CFrameWnd::GetControlBar  
 Llame a `GetControlBar` para obtener acceso a la barra de control que está asociado con el Id.  
  
```  
CControlBar* GetControlBar(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 El número de Id. de una barra de controles.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la barra de control que está asociado con el Id.  
  
### <a name="remarks"></a>Comentarios  
 El `nID` parámetro hace referencia al identificador exclusivo pasan a la **Create** método de la barra de control. Para obtener más información sobre las barras de control, consulte el tema dedicado a [barras de Control](../../mfc/control-bars.md).  
  
 `GetControlBar`Devuelve la barra de control aunque no es flotante y, por tanto, no es actualmente una ventana secundaria de la trama.  
  
##  <a name="a-namegetdockstatea--cframewndgetdockstate"></a><a name="getdockstate"></a>CFrameWnd::GetDockState  
 Llame a esta función miembro para almacenar la información de estado acerca de las barras de control de la ventana de marco en un `CDockState` objeto.  
  
```  
void GetDockState(CDockState& state) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `state`  
 Contiene el estado actual de barras de control de la ventana de marco tras la devolución.  
  
### <a name="remarks"></a>Comentarios  
 A continuación, puede escribir el contenido de `CDockState` al almacenamiento usando `CDockState::SaveState` o `Serialize`. Si más adelante desea restaurar las barras de control a un estado anterior, se carga el estado con `CDockState::LoadState` o `Serialize`, a continuación, llame a `SetDockState` para aplicar el estado anterior a barras de control de la ventana de marco.  
  
##  <a name="a-namegetmenubarstatea--cframewndgetmenubarstate"></a><a name="getmenubarstate"></a>CFrameWnd::GetMenuBarState  
 Recupera el estado de visualización del menú de la aplicación MFC actual.  
  
```  
virtual DWORD GetMenuBarState();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto puede tener los valores siguientes:  
  
-   AFX_MBS_VISIBLE (0 x&01;): el menú es visible.  
  
-   AFX_MBS_HIDDEN (0 x&02;): el menú esté oculto.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error en tiempo de ejecución, este método valida en modo de depuración y provoca una excepción derivada de la [CException](../../mfc/reference/cexception-class.md) clase.  
  
##  <a name="a-namegetmenubarvisibilitya--cframewndgetmenubarvisibility"></a><a name="getmenubarvisibility"></a>CFrameWnd::GetMenuBarVisibility  
 Indica si el estado predeterminado del menú de la aplicación MFC actual está oculto o visible.  
  
```  
virtual DWORD CFrameWnd::GetMenuBarVisibility();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Este método devuelve uno de los siguientes valores:  
  
-   AFX_MBV_KEEPVISIBLE (0 x&01;): se muestra el menú en todo momento y de forma predeterminada no tiene el foco.  
  
-   AFX_MBV_DISPLAYONFOCUS (0 x&02;): el menú está oculta de forma predeterminada. Si el menú está oculto, presione la tecla ALT para mostrar el menú y dar el foco. Si se muestra el menú, presione la tecla ALT o ESC para ocultarlo.  
  
-   AFX_MBV_ DISPLAYONFOCUS (0 X&02;) | AFX_MBV_DISPLAYONF10 (combinación bit a bit (OR)) - (0 x&04;) del menú está oculta de forma predeterminada. Si el menú está oculto, presione la tecla F10 para mostrar el menú y dar el foco. Si se muestra el menú, presione la tecla F10 para alternar el foco o desactivar el menú. Se muestra el menú hasta que presione la tecla ALT o ESC para ocultarlo.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error en tiempo de ejecución, este método valida en modo de depuración y provoca una excepción derivada de la [CException](../../mfc/reference/cexception-class.md) clase.  
  
##  <a name="a-namegetmessagebara--cframewndgetmessagebar"></a><a name="getmessagebar"></a>CFrameWnd::GetMessageBar  
 Llame a esta función miembro para obtener un puntero a la barra de estado.  
  
```  
virtual CWnd* GetMessageBar();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la ventana de la barra de estado.  
  
##  <a name="a-namegetmessagestringa--cframewndgetmessagestring"></a><a name="getmessagestring"></a>CFrameWnd:: GetMessageString  
 Reemplazar esta función para proporcionar cadenas personalizadas para los identificadores de comando.  
  
```  
virtual void GetMessageString(
    UINT nID,  
    CString& rMessage) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 Id. de recurso del mensaje deseado.  
  
 `rMessage`  
 `CString`objeto en el que se va a colocar el mensaje.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada simplemente carga la cadena especificada por `nID` del archivo de recursos. El marco de trabajo llama a esta función cuando la cadena de mensaje en la barra de estado debe actualizarse.  
  
##  <a name="a-namegettitlea--cframewndgettitle"></a><a name="gettitle"></a>CFrameWnd::GetTitle  
 Recupera el título del objeto window.  
  
```  
CString GetTitle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el título del objeto de ventana actual.  
  
##  <a name="a-nameinitialupdateframea--cframewndinitialupdateframe"></a><a name="initialupdateframe"></a>CFrameWnd::InitialUpdateFrame  
 Llame a **IntitialUpdateFrame** después de crear un nuevo marco con **crear**.  
  
```  
void InitialUpdateFrame(
    CDocument* pDoc,  
    BOOL bMakeVisible);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDoc`  
 Señala el documento al que está asociada la ventana de marco. Puede ser **NULL**.  
  
 `bMakeVisible`  
 Si **TRUE**, indica que el marco debe visible y activo. Si **FALSE**, no hay descendientes se hacen visibles.  
  
### <a name="remarks"></a>Comentarios  
 Esto hace que todas las vistas en esa ventana de marco para recibir sus `OnInitialUpdate` llamadas.  
  
 Además, si anteriormente no era una vista activa, se convierte la vista de la ventana de marco principal activa. El principal es una vista con un identificador secundario de **AFX_IDW_PANE_FIRST**. Por último, la ventana de marco se hace visible si `bMakeVisible` es distinto de cero. Si `bMakeVisible` es 0, no cambios el foco actual y el estado de visibilidad de la ventana de marco. No es necesario llamar a esta función cuando se utiliza la implementación del marco de trabajo de archivo nuevo y abrir archivo.  
  
##  <a name="a-nameinmodalstatea--cframewndinmodalstate"></a><a name="inmodalstate"></a>CFrameWnd::InModalState  
 Llame a esta función miembro para comprobar si una ventana de marco es modal o no modal.  
  
```  
BOOL InModalState() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero en caso afirmativo; en caso contrario, 0.  
  
##  <a name="a-nameistrackinga--cframewndistracking"></a><a name="istracking"></a>CFrameWnd::IsTracking  
 Llame a esta función miembro para determinar si la barra de división en la ventana se está moviendo actualmente.  
  
```  
BOOL IsTracking() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si una operación de divisor está en curso; en caso contrario, 0.  
  
##  <a name="a-nameloadacceltablea--cframewndloadacceltable"></a><a name="loadacceltable"></a>CFrameWnd::LoadAccelTable  
 Llamada para cargar la tabla de aceleradores especificado.  
  
```  
BOOL LoadAccelTable(LPCTSTR lpszResourceName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszResourceName`  
 Identifica el nombre del recurso del acelerador. Utilice **MAKEINTRESOURCE** si el recurso se identifica con un identificador entero.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la tabla de aceleradores se cargó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Solo una tabla se puede cargar a la vez.  
  
 Tablas de aceleradores cargadas desde recursos se liberan automáticamente cuando finaliza la aplicación.  
  
 Si se llama a `LoadFrame` para crear la ventana de marco, el marco de trabajo carga una tabla de aceleradores junto con los recursos de menú y el icono y, a continuación, es necesaria una llamada posterior a esta función miembro.  
  
##  <a name="a-nameloadbarstatea--cframewndloadbarstate"></a><a name="loadbarstate"></a>CFrameWnd:: LoadBarState  
 Llame a esta función para restaurar la configuración de cada barra de controles que pertenecen a la ventana de marco.  
  
```  
void LoadBarState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszProfileName`  
 Nombre de una sección en el archivo de inicialización (INI) o una clave del registro de Windows donde se almacena información de estado.  
  
### <a name="remarks"></a>Comentarios  
 Restaura la información incluye visibilidad, orientación horizontal o vertical, estado de acoplamiento y posición de la barra de control.  
  
 La configuración que desea restaurar debe escribirse en el registro antes de llamar a `LoadBarState`. Escribir la información en el registro mediante una llamada a [CWinApp::SetRegistryKey](../../mfc/reference/cwinapp-class.md#setregistrykey). Escribir la información en el archivo INI mediante una llamada a [SaveBarState](#savebarstate).  
  
##  <a name="a-nameloadframea--cframewndloadframe"></a><a name="loadframe"></a>CFrameWnd::LoadFrame  
 Llamada a crear dinámicamente una ventana de marco de información de recursos.  
  
```  
virtual BOOL LoadFrame(
    UINT nIDResource,  
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,  
    CWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDResource`  
 El identificador de recursos compartidos asociados con la ventana de marco.  
  
 *dwDefaultStyle*  
 El marco [estilo](../../mfc/reference/window-styles.md). Incluir el **FWS_ADDTOTITLE** si desea que la barra de título para mostrar automáticamente el nombre del documento representado en la ventana de estilo.  
  
 `pParentWnd`  
 Un puntero al elemento primario del marco.  
  
 `pContext`  
 Un puntero a un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) estructura. Este parámetro puede ser **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Construir un `CFrameWnd` objeto en dos pasos. En primer lugar, invocar el constructor, que construye la `CFrameWnd` de objetos y, a continuación, llame a `LoadFrame`, que carga la ventana de marco de Windows y los recursos asociados y se adjunta a la ventana de marco para el `CFrameWnd` objeto. El `nIDResource` parámetro especifica el menú, la tabla de aceleradores, el icono y el recurso de cadena del título de la ventana de marco.  
  
 Utilice la **crear** función miembro en lugar de `LoadFrame` cuando desee especificar todos los parámetros de creación de la ventana de marco.  
  
 El marco llama `LoadFrame` cuando crea una ventana de marco utilizando un objeto de plantilla de documento.  
  
 El marco de trabajo usa el `pContext` contenidos de argumento para especificar los objetos que se va a estar conectado a la ventana de marco, los incluidos objetos de vista. Puede establecer la `pContext` argumento **NULL** al llamar a `LoadFrame`.  
  
##  <a name="a-namembautomenuenablea--cframewndmbautomenuenable"></a><a name="m_bautomenuenable"></a>CFrameWnd::m_bAutoMenuEnable  
 Cuando este miembro de datos está habilitada (que es el valor predeterminado), elementos de menú que no tienen `ON_UPDATE_COMMAND_UI` o `ON_COMMAND` controladores se deshabilitará automáticamente cuando el usuario extrae un menú desplegable.  
  
```  
BOOL m_bAutoMenuEnable;  
```  
  
### <a name="remarks"></a>Comentarios  
 Elementos de menú que tienen un `ON_COMMAND` controlador pero no `ON_UPDATE_COMMAND_UI` se habilitará automáticamente el controlador.  
  
 Cuando se establece este miembro de datos, se habilitan automáticamente elementos de menú de la misma manera que estén habilitados los botones de barra de herramientas.  
  
> [!NOTE]
> `m_bAutoMenuEnable`no tiene ningún efecto en los elementos de menú de nivel superior.  
  
 Este miembro de datos simplifica la implementación de comandos opcionales, según la selección actual y reduce la necesidad de escribir `ON_UPDATE_COMMAND_UI` controladores para habilitar y deshabilitar elementos de menú.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&3;](../../mfc/reference/codesnippet/cpp/cframewnd-class_3.cpp)]  
  
##  <a name="a-namenegotiateborderspacea--cframewndnegotiateborderspace"></a><a name="negotiateborderspace"></a>CFrameWnd::NegotiateBorderSpace  
 Llame a esta función miembro para negociar el espacio del borde de una ventana de marco durante la activación de inplace OLE.  
  
```  
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,  
    LPRECT lpRectBorder);
```  
  
### <a name="parameters"></a>Parámetros  
 *nBorderCmd*  
 Contiene uno de los valores siguientes de la **enum BorderCmd**:  
  
- **borderGet** = 1  
  
- **borderRequest** = 2  
  
- **borderSet** = 3  
  
 `lpRectBorder`  
 Puntero a un [RECT](../../mfc/reference/rect-structure1.md) estructura o un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que especifica las coordenadas del borde.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro es el **CFrameWnd** implementación de negociación de espacio del borde OLE.  
  
##  <a name="a-nameonbarchecka--cframewndonbarcheck"></a><a name="onbarcheck"></a>CFrameWnd::OnBarCheck  
 Se llama siempre que se realiza una acción en la barra de control especificado.  
  
```  
afx_msg BOOL OnBarCheck(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `nID`  
 El identificador del control de la barra que se muestra.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la barra de control existentes; en caso contrario, 0.  
  
##  <a name="a-nameoncontexthelpa--cframewndoncontexthelp"></a><a name="oncontexthelp"></a>CFrameWnd::OnContextHelp  
 Controla MAYÚS + F1 Ayuda para artículos en contexto.  
  
```  
afx_msg void OnContextHelp();
```  
  
### <a name="remarks"></a>Comentarios  
 Para habilitar la Ayuda contextual, debe agregar un  
  
 [!code-cpp[NVC_MFCDocViewSDI Nº&16;](../../mfc/codesnippet/cpp/cframewnd-class_4.cpp)]  
  
 instrucción a su `CFrameWnd` clase mapa de mensajes y también agregar una entrada de tabla de aceleradores, normalmente MAYÚS+F1, para habilitar esta función miembro.  
  
 Si su aplicación es un contenedor OLE, `OnContextHelp` coloca todos los elementos en el lugar dentro del objeto de ventana de marco en modo de ayuda. El cursor cambia a una flecha y un signo de interrogación y el usuario puede mover el puntero del mouse y presione el botón primario del mouse para seleccionar un cuadro de diálogo, una ventana, un menú o un botón de comando. Esta función miembro llama a la función de Windows `WinHelp` con el contexto del objeto con el cursor.  
  
##  <a name="a-nameoncreateclienta--cframewndoncreateclient"></a><a name="oncreateclient"></a>CFrameWnd::OnCreateClient  
 Llamado por el marco de trabajo durante la ejecución de `OnCreate`.  
  
```  
virtual BOOL OnCreateClient(
    LPCREATESTRUCT lpcs,  
    CCreateContext* pContext);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpcs`  
 Un puntero a un Windows [CREATESTRUCT](../../mfc/reference/createstruct-structure.md) estructura *.*  
  
 `pContext`  
 Un puntero a un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) estructura *.*  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Nunca se llame a esta función.  
  
 La implementación predeterminada de esta función crea un `CView` objeto a partir de la información proporcionada en `pContext`, si es posible.  
  
 Reemplazar esta función para invalidar los valores pasados en el `CCreateContext` de objeto o para cambiar los controles de la manera en el área de cliente principal de la ventana de marco se crean. El `CCreateContext` se describen los miembros que se pueden invalidar en la [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) clase.  
  
> [!NOTE]
>  No reemplazar valores pasados en la `CREATESTRUCT` estructura. Son sólo con fines informativos. Si desea invalidar el rectángulo de la ventana inicial, por ejemplo, reemplazar el `CWnd` función miembro [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).  
  
##  <a name="a-nameonhidemenubara--cframewndonhidemenubar"></a><a name="onhidemenubar"></a>CFrameWnd::OnHideMenuBar  
 Esta función se invoca cuando el sistema está a punto de ocultar la barra de menús de la aplicación MFC actual.  
  
```  
virtual void OnHideMenuBar();
```  
  
### <a name="remarks"></a>Comentarios  
 Este controlador de eventos permite que la aplicación realizar acciones personalizadas cuando el sistema está a punto de ocultar el menú. No se puede impedir que el menú ocultas, pero, por ejemplo, puede llamar a otros métodos para recuperar el estilo de menú o el estado.  
  
##  <a name="a-nameonsetpreviewmodea--cframewndonsetpreviewmode"></a><a name="onsetpreviewmode"></a>CFrameWnd::OnSetPreviewMode  
 Llame a esta función miembro para establecer la ventana de marco principal de la aplicación dentro y fuera del modo de vista previa de impresión.  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>Parámetros  
 *bPreview*  
 Especifica si se debe o no colocar la aplicación en modo de vista previa de impresión. Establecer en **TRUE** para colocar en la vista preliminar, **FALSE** para cancelar el modo de vista previa.  
  
 `pState`  
 Un puntero a un **CPrintPreviewState** estructura.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada deshabilita todas las barras de herramientas estándar y oculta el menú principal y la ventana principal del cliente. Esto convierte ventanas de marco MDI en ventanas de marco SDI temporales.  
  
 Reemplace esta función miembro para personalizar el mostrar y ocultar las barras de control y otras partes de la ventana de marco durante la vista previa de impresión. Llame a la implementación de clase base desde la versión invalidada.  
  
##  <a name="a-nameonshowmenubara--cframewndonshowmenubar"></a><a name="onshowmenubar"></a>CFrameWnd::OnShowMenuBar  
 Esta función se invoca cuando el sistema está a punto de mostrar la barra de menús de la aplicación MFC actual.  
  
```  
virtual void OnShowMenuBar();
```  
  
### <a name="remarks"></a>Comentarios  
 Este controlador de eventos permite que la aplicación realizar acciones personalizadas cuando el menú está a punto de mostrarse. No se puede impedir que el menú aparezca, pero, por ejemplo, puede llamar a otros métodos para recuperar el estilo de menú o el estado.  
  
##  <a name="a-nameonupdatecontrolbarmenua--cframewndonupdatecontrolbarmenu"></a><a name="onupdatecontrolbarmenu"></a>CFrameWnd::OnUpdateControlBarMenu  
 Llamado por el marco de trabajo cuando se actualiza el menú asociado.  
  
```  
afx_msg void OnUpdateControlBarMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCmdUI`  
 Un puntero a un [CCmdUI](../../mfc/reference/ccmdui-class.md) objeto que representa el menú que generó el comando de actualización. Las llamadas del controlador de actualización de la [habilitar](../../mfc/reference/ccmdui-class.md#enable) función miembro de la `CCmdUI` a través del objeto `pCmdUI` para actualizar la interfaz de usuario.  
  
##  <a name="a-namerecalclayouta--cframewndrecalclayout"></a><a name="recalclayout"></a>RecalcLayout  
 Llamado por el marco de trabajo cuando las barras de controles estándar se activan o desactivan o cuando se cambia el tamaño de la ventana de marco.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bNotify`  
 Determina si el elemento en el contexto activo de la ventana de marco recibe la notificación de cambio de diseño. Si **TRUE**, el elemento es notificado; en caso contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función miembro llama el `CWnd` función miembro `RepositionBars` para cambiar la posición de las barras de control en el marco, así como en la ventana principal de cliente (normalmente un `CView` o **MDICLIENT**).  
  
 Reemplace esta función miembro para controlar la apariencia y el comportamiento de las barras de control después de cambia el diseño de la ventana de marco. Por ejemplo, llamar al activar o desactivar la barras de control o agregar otra barra de control.  
  
##  <a name="a-namerectdefaulta--cframewndrectdefault"></a><a name="rectdefault"></a>CFrameWnd::rectDefault  
 Pasar estático `CRect` como un parámetro al crear una ventana para permitir que Windows elija el tamaño inicial y la posición de la ventana.  
  
```  
static AFX_DATA const CRect rectDefault;  
```  
  
##  <a name="a-namesavebarstatea--cframewndsavebarstate"></a><a name="savebarstate"></a>CFrameWnd:: SaveBarState  
 Llame a esta función para almacenar información sobre cada propiedad de la ventana de marco de barra de control.  
  
```  
void SaveBarState(LPCTSTR lpszProfileName) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszProfileName`  
 Nombre de una sección en el archivo de inicialización o una clave del registro de Windows donde se almacena información de estado.  
  
### <a name="remarks"></a>Comentarios  
 Esta información se puede leer desde el archivo de inicialización con [LoadBarState](#loadbarstate). La información almacenada incluye visibilidad, orientación horizontal o vertical, estado y la posición de la barra de control de acoplamiento.  
  
##  <a name="a-namesetactivepreviewviewa--cframewndsetactivepreviewview"></a><a name="setactivepreviewview"></a>CFrameWnd::SetActivePreviewView  
 Designa la vista especificada sea la vista activa de la vista previa avanzada.  
  
```  
void SetActivePreviewView(CView* pViewNew);
```  
  
### <a name="parameters"></a>Parámetros  
 `pViewNew`  
 Un puntero a una vista para activarse.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetactiveviewa--cframewndsetactiveview"></a><a name="setactiveview"></a>CFrameWnd::SetActiveView  
 Llame a esta función miembro para establecer la vista activa.  
  
```  
void SetActiveView(
    CView* pViewNew,  
    BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *pViewNew*  
 Especifica un puntero a un [CView](../../mfc/reference/cview-class.md) objeto, o **NULL** para ninguna vista activa.  
  
 `bNotify`  
 Especifica si la vista es recibir una notificación de activación. Si **TRUE**, `OnActivateView` se llama para la nueva vista; si **FALSE**, no es así.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llamará a esta función automáticamente cuando el usuario cambia el foco a una vista de la ventana de marco. Se puede llamar explícitamente `SetActiveView` para cambiar el foco a la vista especificada.  
  
##  <a name="a-namesetdockstatea--cframewndsetdockstate"></a><a name="setdockstate"></a>CFrameWnd::SetDockState  
 Llame a esta función miembro para aplicar la información de estado almacenada en un `CDockState` objeto a barras de control de la ventana de marco.  
  
```  
void SetDockState(const CDockState& state);
```  
  
### <a name="parameters"></a>Parámetros  
 `state`  
 El estado almacenado se aplican a las barras de control de la ventana de marco.  
  
### <a name="remarks"></a>Comentarios  
 Para restaurar un estado anterior de las barras de control, puede cargar el estado almacenado con `CDockState::LoadState` o `Serialize`, a continuación, utilice `SetDockState` para aplicarlo a las barras de control de la ventana de marco. El estado anterior se almacena en el `CDockState` de objetos con`GetDockState`  
  
##  <a name="a-namesetmenubarstatea--cframewndsetmenubarstate"></a><a name="setmenubarstate"></a>CFrameWnd::SetMenuBarState  
 Establece el estado de visualización del menú de la aplicación MFC actual oculta o muestra.  
  
```  
virtual BOOL SetMenuBarState(DWORD nState);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `nState`|Especifica si se debe mostrar u ocultar el menú. El `nState` parámetro puede tener los valores siguientes:<br /><br /> -AFX_MBS_VISIBLE (0 x&01;): muestra el menú si está oculto, pero no tiene ningún efecto si está visible.<br />-AFX_MBS_HIDDEN (0 x&02;): oculta el menú si está visible, pero no tiene ningún efecto si está oculto.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método cambia correctamente el estado de menú. de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error en tiempo de ejecución, este método valida en modo de depuración y provoca una excepción derivada de la [CException](../../mfc/reference/cexception-class.md) clase.  
  
##  <a name="a-namesetmenubarvisibilitya--cframewndsetmenubarvisibility"></a><a name="setmenubarvisibility"></a>CFrameWnd::SetMenuBarVisibility  
 Establece el comportamiento predeterminado del menú de la aplicación MFC actual para que esté visible u oculto.  
  
```  
virtual void SetMenuBarVisibility(DWORD nStyle);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `nStyle`|Especifica si el menú está oculta, de manera predeterminada o está visible y tiene el foco. El `nStyle` parámetro puede tener los valores siguientes:<br /><br /> -AFX_MBV_KEEPVISIBLE (0 X&01;):<br />     El menú se muestra en todo momento y de forma predeterminada no tiene el foco.<br />-AFX_MBV_DISPLAYONFOCUS (0 X&02;):<br />     El menú se oculta de forma predeterminada. Si el menú está oculto, presione la tecla ALT para mostrar el menú y dar el foco. Si se muestra el menú, presione la tecla ALT o ESC para ocultar el menú.<br />-AFX_MBV_ DISPLAYONFOCUS (0 X&02;) | AFX_MBV_DISPLAYONF10 (0 X&04;)<br />     (combinación bit a bit (OR)): el menú está oculta de forma predeterminada. Si el menú está oculto, presione la tecla F10 para mostrar el menú y dar el foco. Si se muestra el menú, presione la tecla F10 para alternar el foco o desactivar el menú. Se muestra el menú hasta que presione la tecla ALT o ESC para ocultarlo.|  
  
### <a name="remarks"></a>Comentarios  
 Si el valor de la `nStyle` parámetro no es válido, este método valida en modo de depuración y genera [CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md) en modo de lanzamiento. Si hay otros errores en tiempo de ejecución, este método valida en modo de depuración y provoca una excepción derivada de la [CException](../../mfc/reference/cexception-class.md) clase.  
  
 Este método afecta al estado de menús en aplicaciones escritas para [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] y versiones posteriores.  
  
##  <a name="a-namesetmessagetexta--cframewndsetmessagetext"></a><a name="setmessagetext"></a>CFrameWnd::SetMessageText  
 Llame a esta función para colocar una cadena en el panel de la barra de estado que tiene un identificador de 0.  
  
```  
void SetMessageText(LPCTSTR lpszText);  
void SetMessageText(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszText`  
 Apunta a la cadena que se coloca en la barra de estado.  
  
 `nID`  
 Identificador de recurso de cadena de la cadena que se coloca en la barra de estado.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente es el panel de la izquierda y más largo, la barra de estado.  
  
##  <a name="a-namesetprogressbarpositiona--cframewndsetprogressbarposition"></a><a name="setprogressbarposition"></a>CFrameWnd::SetProgressBarPosition  
 Establece la posición actual de la barra de progreso de Windows 7 muestra la barra de tareas.  
  
```  
void SetProgressBarPosition(int nProgressPos);
```  
  
### <a name="parameters"></a>Parámetros  
 `nProgressPos`  
 Especifica la posición para establecer. Debe estar dentro del intervalo establecido por `SetProgressBarRange`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetprogressbarrangea--cframewndsetprogressbarrange"></a><a name="setprogressbarrange"></a>CFrameWnd::SetProgressBarRange  
 Establece el intervalo de la barra de progreso de Windows 7 muestra la barra de tareas.  
  
```  
void SetProgressBarRange(
    int nRangeMin,  
    int nRangeMax);
```  
  
### <a name="parameters"></a>Parámetros  
 `nRangeMin`  
 Valor mínimo.  
  
 `nRangeMax`  
 Valor máximo.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetprogressbarstatea--cframewndsetprogressbarstate"></a><a name="setprogressbarstate"></a>CFrameWnd::SetProgressBarState  
 Establece el tipo y el estado del indicador de progreso mostrado en un botón de barra de tareas.  
  
```  
void SetProgressBarState(TBPFLAG tbpFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 `tbpFlags`  
 Marcas que controlan el estado actual del botón del progreso. Especifique sólo uno de los siguientes indicadores porque todos los Estados son mutuamente excluyentes: TBPF_NOPROGRESS, TBPF_INDETERMINATE, TBPF_NORMAL, TBPF_ERROR, TBPF_PAUSED.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesettaskbaroverlayicona--cframewndsettaskbaroverlayicon"></a><a name="settaskbaroverlayicon"></a>CFrameWnd::SetTaskbarOverlayIcon  
 Sobrecargado. Se aplica una superposición a un botón de barra de tareas para indicar el estado de la aplicación o para notificar al usuario.  
  
```  
BOOL SetTaskbarOverlayIcon(
    UINT nIDResource,  
    LPCTSTR lpcszDescr);

 
BOOL SetTaskbarOverlayIcon(
    HICON hIcon,  
    LPCTSTR lpcszDescr);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDResource`  
 Especifica el identificador de recurso de un icono que se usará como la superposición. Consulte la descripción para `hIcon` para obtener más información.  
  
 `lpcszDescr`  
 Un puntero a una cadena que proporciona una versión de texto alternativo de la información transmitida por la superposición, por motivos de accesibilidad.  
  
 `hIcon`  
 El identificador de un icono que se va a utilizar como la superposición. Debe tratarse de un icono pequeño, medición de 16 x 16 píxeles a 96 puntos por pulgada (PPP). Si el botón de barra de tareas se ha aplicado un icono de superposición, se reemplaza ese superposición existente. Este valor puede ser `NULL`. Cómo un `NULL` trata valor depende de si el botón de barra de tareas representa una ventana o un grupo de windows. Es responsabilidad de la aplicación que realiza la llamada para liberar `hIcon` cuando ya no sea necesario.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si es correcto; `FALSE` si la versión del sistema operativo es menor que Windows 7, o si se produce un error al configurar el icono.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesettitlea--cframewndsettitle"></a><a name="settitle"></a>CFrameWnd::SetTitle  
 Establece el título del objeto window.  
  
```  
void SetTitle(LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszTitle`  
 Puntero a una cadena de caracteres que contiene el título del objeto window.  
  
##  <a name="a-nameshowcontrolbara--cframewndshowcontrolbar"></a><a name="showcontrolbar"></a>CFrameWnd::ShowControlBar  
 Llame a esta función miembro para mostrar u ocultar la barra de control.  
  
```  
void ShowControlBar(
    CControlBar* pBar,  
    BOOL bShow,  
    BOOL bDelay);
```  
  
### <a name="parameters"></a>Parámetros  
 `pBar`  
 Puntero a la barra de control para mostrar u ocultar.  
  
 `bShow`  
 Si **TRUE**, especifica que se mostrará la barra de control. Si **FALSE**, especifica que se oculta la barra de control.  
  
 *bDelay*  
 Si **TRUE**, retraso que muestra la barra de control. Si **FALSE**, mostrar el control de barra inmediatamente.  
  
##  <a name="a-nameshowownedwindowsa--cframewndshowownedwindows"></a><a name="showownedwindows"></a>CFrameWnd::ShowOwnedWindows  
 Llame a esta función miembro para mostrar todas las ventanas que son descendientes de los `CFrameWnd` objeto.  
  
```  
void ShowOwnedWindows(BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 `bShow`  
 Especifica si el propias windows deben mostrarse u ocultarse.  
  
## <a name="see-also"></a>Vea también  
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd (clase)](../../mfc/reference/cmdiframewnd-class.md)   
 [CMDIChildWnd (clase)](../../mfc/reference/cmdichildwnd-class.md)   
 [CView (clase)](../../mfc/reference/cview-class.md)   
 [CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)   
 [Estructura de CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)

