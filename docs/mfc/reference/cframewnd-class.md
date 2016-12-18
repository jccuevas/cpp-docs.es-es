---
title: "CFrameWnd Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFrameWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFrameWnd class"
  - "frame window classes, clase base"
  - "frame windows, crear"
  - "interfaz de único documento (SDI), frame windows"
ms.assetid: e2220aba-5bf4-4002-b960-fbcafcad01f1
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFrameWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad de una ventana superpuesta \(SDI\) móvil o de interfaz de un único documento de Windows en el cuadro, junto con los miembros para administrar la ventana.  
  
## Sintaxis  
  
```  
class CFrameWnd : public CWnd  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFrameWnd::CFrameWnd](../Topic/CFrameWnd::CFrameWnd.md)|Crea un objeto `CFrameWnd`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFrameWnd::ActivateFrame](../Topic/CFrameWnd::ActivateFrame.md)|Coloca el cuadro visible y a disposición del usuario.|  
|[CFrameWnd::BeginModalState](../Topic/CFrameWnd::BeginModalState.md)|Establece la ventana cuadro a modal.|  
|[CFrameWnd::Create](../Topic/CFrameWnd::Create.md)|Llame a para crear e inicializar la ventana cuadro de Windows asociado al objeto de `CFrameWnd` .|  
|[CFrameWnd::CreateView](../Topic/CFrameWnd::CreateView.md)|Crea una vista dentro de un marco que no es derivado de `CView`.|  
|[CFrameWnd::DockControlBar](../Topic/CFrameWnd::DockControlBar.md)|Acopla una barra de controles.|  
|[CFrameWnd::EnableDocking](../Topic/CFrameWnd::EnableDocking.md)|Permite que una barra de control es acoplada.|  
|[CFrameWnd::EndModalState](../Topic/CFrameWnd::EndModalState.md)|Finalizar el estado modal de la ventana de marco.  habilita todas las ventanas deshabilitadas por `BeginModalState`.|  
|[CFrameWnd::FloatControlBar](../Topic/CFrameWnd::FloatControlBar.md)|Flota una barra de controles.|  
|[CFrameWnd::GetActiveDocument](../Topic/CFrameWnd::GetActiveDocument.md)|devuelve el objeto activo de **CDocument** .|  
|[CFrameWnd::GetActiveFrame](../Topic/CFrameWnd::GetActiveFrame.md)|devuelve el objeto activo de `CFrameWnd` .|  
|[CFrameWnd::GetActiveView](../Topic/CFrameWnd::GetActiveView.md)|devuelve el objeto activo de `CView` .|  
|[CFrameWnd::GetControlBar](../Topic/CFrameWnd::GetControlBar.md)|recupera la barra de control.|  
|[CFrameWnd::GetDockState](../Topic/CFrameWnd::GetDockState.md)|Recupera el estado de vinculación de una ventana de marco.|  
|[CFrameWnd::GetMenuBarState](../Topic/CFrameWnd::GetMenuBarState.md)|Recupera el estado de la presentación del menú en la aplicación MFC actual.|  
|[CFrameWnd::GetMenuBarVisibility](../Topic/CFrameWnd::GetMenuBarVisibility.md)|Indica si el comportamiento predeterminado del menú en la aplicación MFC actual está oculto o visible.|  
|[CFrameWnd::GetMessageBar](../Topic/CFrameWnd::GetMessageBar.md)|Devuelve un puntero a la barra de estado correspondiente a la ventana de marco.|  
|[CFrameWnd::GetMessageString](../Topic/CFrameWnd::GetMessageString.md)|Recupera el mensaje correspondiente a un identificador de comando|  
|[CFrameWnd::GetTitle](../Topic/CFrameWnd::GetTitle.md)|Recupera el título de la barra de control relacionada.|  
|[CFrameWnd::InitialUpdateFrame](../Topic/CFrameWnd::InitialUpdateFrame.md)|Hace que la función miembro de `OnInitialUpdate` correspondiente a todas las vistas en la ventana de marco que se va a llamar.|  
|[CFrameWnd::InModalState](../Topic/CFrameWnd::InModalState.md)|Devuelve un valor que indica si una ventana de marco está en un estado modal.|  
|[CFrameWnd::IsTracking](../Topic/CFrameWnd::IsTracking.md)|Determina si la barra de división se mueve actualmente.|  
|[CFrameWnd::LoadAccelTable](../Topic/CFrameWnd::LoadAccelTable.md)|Llamada para cargar una tabla de aceleradores.|  
|[CFrameWnd::LoadBarState](../Topic/CFrameWnd::LoadBarState.md)|Llame a para restaurar valores de barra de control.|  
|[CFrameWnd::LoadFrame](../Topic/CFrameWnd::LoadFrame.md)|Llamada para crear dinámicamente una ventana cuadro de información de recursos.|  
|[CFrameWnd::NegotiateBorderSpace](../Topic/CFrameWnd::NegotiateBorderSpace.md)|Negocia el espacio del borde de la ventana de marco.|  
|[CFrameWnd::OnBarCheck](../Topic/CFrameWnd::OnBarCheck.md)|Denominado siempre que una acción se realice en la barra de control especificada.|  
|[CFrameWnd::OnContextHelp](../Topic/CFrameWnd::OnContextHelp.md)|Ayuda de identificadores MAYÚS\+F1 para los elementos de contexto.|  
|[CFrameWnd::OnSetPreviewMode](../Topic/CFrameWnd::OnSetPreviewMode.md)|Establece la ventana de marco principal de la aplicación en y fuera de modo vista previa de impresión.|  
|[CFrameWnd::OnUpdateControlBarMenu](../Topic/CFrameWnd::OnUpdateControlBarMenu.md)|Llamado por el marco cuando se actualiza el menú asociado.|  
|[CFrameWnd::RecalcLayout](../Topic/CFrameWnd::RecalcLayout.md)|Coloca las barras de control de nuevo del objeto de `CFrameWnd` .|  
|[CFrameWnd::SaveBarState](../Topic/CFrameWnd::SaveBarState.md)|Llamada para guardar valores de barra de control.|  
|[CFrameWnd::SetActivePreviewView](../Topic/CFrameWnd::SetActivePreviewView.md)|Seleccione la vista especificada sea la vista activa para la vista previa enriquecidas.|  
|[CFrameWnd::SetActiveView](../Topic/CFrameWnd::SetActiveView.md)|establece el objeto activo de `CView` .|  
|[CFrameWnd::SetDockState](../Topic/CFrameWnd::SetDockState.md)|Llamada para acoplar la ventana cuadro en la ventana principal.|  
|[CFrameWnd::SetMenuBarState](../Topic/CFrameWnd::SetMenuBarState.md)|Establece el estado de la presentación del menú en la aplicación MFC actual oculta o muestra.|  
|[CFrameWnd::SetMenuBarVisibility](../Topic/CFrameWnd::SetMenuBarVisibility.md)|Establece el comportamiento predeterminado del menú en la aplicación MFC actual para ocultar o visible.|  
|[CFrameWnd::SetMessageText](../Topic/CFrameWnd::SetMessageText.md)|establece el texto de una barra de estado estándar.|  
|[CFrameWnd::SetProgressBarPosition](../Topic/CFrameWnd::SetProgressBarPosition.md)|Establece la posición actual para la barra de progreso de Windows 7 mostrada respecto a la barra de tareas.|  
|[CFrameWnd::SetProgressBarRange](../Topic/CFrameWnd::SetProgressBarRange.md)|Los conjuntos se amplían para la barra de progreso de Windows 7 mostrada en la barra de tareas.|  
|[CFrameWnd::SetProgressBarState](../Topic/CFrameWnd::SetProgressBarState.md)|Establece el tipo y el estado del indicador de progreso mostrado en un botón de la barra de tareas.|  
|[CFrameWnd::SetTaskbarOverlayIcon](../Topic/CFrameWnd::SetTaskbarOverlayIcon.md)|Sobrecargado.  Aplica una superposición a un botón de la barra de tareas para indicar el estado de aplicación o una notificación al usuario.|  
|[CFrameWnd::SetTitle](../Topic/CFrameWnd::SetTitle.md)|Establece el título de la barra de control relacionada.|  
|[CFrameWnd::ShowControlBar](../Topic/CFrameWnd::ShowControlBar.md)|llamada para mostrar la barra de control.|  
|[CFrameWnd::ShowOwnedWindows](../Topic/CFrameWnd::ShowOwnedWindows.md)|Muestra todas las ventanas que son descendientes del objeto de `CFrameWnd` .|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFrameWnd::OnCreateClient](../Topic/CFrameWnd::OnCreateClient.md)|Crea una ventana del cliente para el cuadro.|  
|[CFrameWnd::OnHideMenuBar](../Topic/CFrameWnd::OnHideMenuBar.md)|Se llama antes de menú en la aplicación MFC actual se oculta.|  
|[CFrameWnd::OnShowMenuBar](../Topic/CFrameWnd::OnShowMenuBar.md)|Se llama antes de menú en la aplicación MFC actual se muestra.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFrameWnd::m\_bAutoMenuEnable](../Topic/CFrameWnd::m_bAutoMenuEnable.md)|Permiso automático de Controles y funcionalidad deshabilitada para elementos de menú.|  
|[CFrameWnd::rectDefault](../Topic/CFrameWnd::rectDefault.md)|Pase este `CRect` estático como parámetro al crear un objeto de `CFrameWnd` para permitir que Windows elija el tamaño inicial y la posición de la ventana.|  
  
## Comentarios  
 Para crear una ventana útil del cuadro para la aplicación, derive una clase de `CFrameWnd`.  Agregue las variables miembro a la clase derivada a concreto almacenado de datos a la aplicación.  El miembro del controlador de mensajes de implemente funciones y un mapa de mensajes en la clase derivada para especificar lo que ocurre cuando los mensajes se dirigen a la ventana.  
  
 Hay tres maneras de crear una ventana de marco:  
  
-   Construyalo directamente mediante [Crear](../Topic/CFrameWnd::Create.md).  
  
-   Construyalo directamente mediante [LoadFrame](../Topic/CFrameWnd::LoadFrame.md).  
  
-   Construyalo indirectamente mediante una plantilla de documento.  
  
 Antes de llamar a **Crear** o `LoadFrame`, debe crear el objeto de la ventana de marco en la pila mediante el operador de C\+\+ **nuevo** .  Antes de llamar a **Crear**, también puede registrar una clase de ventana con la función global de [Clase](../Topic/AfxRegisterWndClass.md) para establecer los estilos de icono y de clase del cuadro.  
  
 Utilice la función miembro de **Crear** para pasar los parámetros de creación de cuadro como argumentos inmediatos.  
  
 `LoadFrame` requiere menos argumentos que **Crear**y, en su lugar recupera la mayoría de los valores predeterminados de recursos, incluida la leyenda del cuadro, el icono, la tabla de aceleradores, y el menú.  para ser accesibles por `LoadFrame`, todos estos recursos deben tener el mismo Id. de recurso \(por ejemplo, **IDR\_MAINFRAME**\).  
  
 Cuando un objeto de `CFrameWnd` contiene vistas y documentos, se crean indirectamente el marco en lugar directamente por el programador.  El objeto de `CDocTemplate` orquestra la creación del marco, la creación de vistas que contienen, y la conexión de las vistas al documento adecuado.  Los parámetros de constructor de `CDocTemplate` especifican `CRuntimeClass` de las tres clases implicadas \(documento, cuadro, y vista\).  Un objeto de `CRuntimeClass` se utiliza el marco para crear dinámicamente los nuevos cuadros cuando es especificado por el usuario \(por ejemplo, utilizando el comando de Archivo Nuevo o el comando \(MDI\) New de la ventana de la interfaz de múltiples documentos\).  
  
 Una clase de la ventana de marco derivada de `CFrameWnd` se debe declarar con `DECLARE_DYNCREATE` para que el mecanismo anterior de `RUNTIME_CLASS` funcione correctamente.  
  
 `CFrameWnd` contiene implementaciones predeterminadas para realizar las siguientes funciones de una ventana principal en una aplicación típica para Windows:  
  
-   Una ventana de cuadro de `CFrameWnd` realiza un seguimiento de la vista activa de a actualmente que es independiente de la ventana activa de Windows o de foco actual.  Cuando se reactiva el cuadro, la vista activa es notificada llamando a `CView::OnActivateView`.  
  
-   Los mensajes de comando y muchos mensajes comunes de la cuadro\-notificación, incluidos los administrados por `OnSetFocus`, `OnHScroll`, y las funciones de `OnVScroll` de `CWnd`, son delegados en una ventana del cuadro de `CFrameWnd` actualmente a la vista activa.  
  
-   Actualmente la vista activa \(o actualmente la ventana secundaria activa de marco MDI en el caso de un marco MDI\) puede determinar la leyenda de la ventana de marco.  Esta característica puede deshabilitarse desactivando el bit de estilo de **FWS\_ADDTOTITLE** de la ventana de marco.  
  
-   Una ventana de cuadro de `CFrameWnd` administra la posición de las barras de controles, las vistas, y otras ventanas secundarias dentro del área de cliente de la ventana de marco.  Una ventana de marco también hace actualizar en tiempo de inactividad de la barra de herramientas y otros botones de barra de control.  Una ventana de cuadro de `CFrameWnd` también tiene implementaciones predeterminadas de los comandos para activar y desactivar la barra de herramientas y la barra de estado.  
  
-   Una ventana de cuadro de `CFrameWnd` administra la barra de menú principal.  Cuando se muestra un menú emergente, la ventana de marco utiliza el mecanismo de **UPDATE\_COMMAND\_UI** para determinar qué elementos de menú deben habilitar, deshabilitar, o comprobarse.  Cuando el usuario selecciona un elemento de menú, la ventana de marco actualiza la barra de estado con la cadena de mensaje para ese comando.  
  
-   Una ventana de cuadro de `CFrameWnd` tiene una tabla opcional de aceleradores que automáticamente de los aceleradores de teclado.  
  
-   Una ventana de cuadro de `CFrameWnd` tiene un identificador opcional de ayuda establecido con `LoadFrame` que se utiliza para ayuda contextual.  Una ventana de marco es el organizador principal de estados semimodal como modos de ayuda contextual \(MAYÚS\+F1\) y de la vista previa de impresión.  
  
-   Una ventana de cuadro de `CFrameWnd` abrirá un archivo arrastrando el administrador de programas y colocado en la ventana de marco.  Si una extensión es registrada y asociado a la aplicación, la ventana de marco responde al intercambio de datos dinámicos \(DDE\) abra la solicitud que aparece cuando el usuario abra un archivo de datos en el administrador de archivos o cuando se llama a la función de **ShellExecute** Windows.  
  
-   Si la ventana de marco es la ventana principal de la aplicación \(es decir, `CWinThread::m_pMainWnd`\), cuando el usuario cierra la aplicación, la ventana de marco pide al usuario guardar cualquier documento modificado \(para `OnClose` y `OnQueryEndSession`\).  
  
-   Si la ventana de marco es la ventana principal de la aplicación, la ventana de marco es el contexto para ejecutar WinHelp.  Cerrar la ventana de marco se cerrará WINHELP.EXE si se inició para obtener ayuda para esta aplicación.  
  
 No utilice el operador de C\+\+ **cancelación** destruir una ventana de marco.  Utilice `CWnd::DestroyWindow` en su lugar.  La implementación de `CFrameWnd` de `PostNcDestroy` eliminará el objeto C\+\+ cuando se destruye la ventana.  Cuando el usuario cierra la ventana de marco, el controlador predeterminado de `OnClose` llamará `DestroyWindow`.  
  
 Para obtener más información sobre `CFrameWnd`, vea [cuadro Windows](../../mfc/frame-windows.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CFrameWnd`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd Class](../../mfc/reference/cmdiframewnd-class.md)   
 [CMDIChildWnd Class](../../mfc/reference/cmdichildwnd-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [CRuntimeClass Structure](../../mfc/reference/cruntimeclass-structure.md)