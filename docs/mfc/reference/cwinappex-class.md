---
title: "CWinAppEx Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWinAppEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinAppEx class"
ms.assetid: a3d3e053-3e22-463f-9444-c73abb1bb9d7
caps.latest.revision: 37
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 39
---
# CWinAppEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CWinAppEx` controla el estado de aplicación, guarda el estado al registro, carga el estado del registro, inicializa los administradores de la aplicación, y proporciona vínculos a esos mismos administradores de la aplicación.  
  
## Sintaxis  
  
```  
class CWinAppEx : public CWinApp  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinAppEx::CWinAppEx](../Topic/CWinAppEx::CWinAppEx.md)|Crea un objeto `CWinAppEx`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinAppEx::CleanState](../Topic/CWinAppEx::CleanState.md)|Quita la información sobre la aplicación del Registro de Windows.|  
|[CWinAppEx::EnableLoadWindowPlacement](../Topic/CWinAppEx::EnableLoadWindowPlacement.md)|Especifica si la aplicación cargará el tamaño inicial y la ubicación de la ventana de marco principal del registro.|  
|[CWinAppEx::EnableTearOffMenus](../Topic/CWinAppEx::EnableTearOffMenus.md)|Los permisos rasgan menús para la aplicación.|  
|[CWinAppEx::EnableUserTools](../Topic/CWinAppEx::EnableUserTools.md)|Permite al usuario crear comandos de menú personalizados en la aplicación.|  
|[CWinAppEx::ExitInstance](../Topic/CWinAppEx::ExitInstance.md)|Llamado por el marco dentro de la función miembro de `Run` para salir esta instancia de la aplicación.  \(Reemplaza [CWinApp::ExitInstance](../Topic/CWinApp::ExitInstance.md).\)|  
|[CWinAppEx::GetBinary](../Topic/CWinAppEx::GetBinary.md)|Lee los datos binarios que está asociado con el valor del Registro especificado.|  
|[CWinAppEx::GetContextMenuManager](../Topic/CWinAppEx::GetContextMenuManager.md)|Devuelve un puntero al objeto de [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) .|  
|[CWinAppEx::GetDataVersion](../Topic/CWinAppEx::GetDataVersion.md)||  
|[CWinAppEx::GetDataVersionMajor](../Topic/CWinAppEx::GetDataVersionMajor.md)|devuelve la versión principal de la aplicación guardada en el Registro de Windows.|  
|[CWinAppEx::GetDataVersionMinor](../Topic/CWinAppEx::GetDataVersionMinor.md)|Devuelve la versión secundaria de la aplicación guardada en el Registro de Windows.|  
|[CWinAppEx::GetInt](../Topic/CWinAppEx::GetInt.md)|Lee los datos numérico que está asociado con el valor especificado del registro.|  
|[CWinAppEx::GetKeyboardManager](../Topic/CWinAppEx::GetKeyboardManager.md)|Devuelve un puntero al objeto de [CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md) .|  
|[CWinAppEx::GetMouseManager](../Topic/CWinAppEx::GetMouseManager.md)|Devuelve un puntero al objeto de [CMouseManager](../../mfc/reference/cmousemanager-class.md) .|  
|[CWinAppEx::GetObject](../Topic/CWinAppEx::GetObject.md)|Lee `CObject`\- los datos derivado que está asociado con el valor especificado del registro.|  
|[CWinAppEx::GetRegSectionPath](../Topic/CWinAppEx::GetRegSectionPath.md)|Devuelve una cadena que es la ruta de una clave del Registro.  esta ruta concatena la ruta de acceso relativa proporcionada con la ruta de la aplicación.|  
|[CWinAppEx::GetRegistryBase](../Topic/CWinAppEx::GetRegistryBase.md)|Devuelve la ruta de acceso del registro de la aplicación.|  
|[CWinAppEx::GetSectionBinary](../Topic/CWinAppEx::GetSectionBinary.md)|Lee los datos binarios que está asociado a la clave y el valor especificados del registro.|  
|[CWinAppEx::GetSectionInt](../Topic/CWinAppEx::GetSectionInt.md)|Datos numéricos de las lecturas de registro asociado a la clave y el valor especificados.|  
|[CWinAppEx::GetSectionObject](../Topic/CWinAppEx::GetSectionObject.md)|Lee los datos de `CObject` que está asociado a la clave y el valor especificados del registro.|  
|[CWinAppEx::GetSectionString](../Topic/CWinAppEx::GetSectionString.md)|Lee los datos de cadena que está asociado a la clave y el valor especificados del registro.|  
|[CWinAppEx::GetShellManager](../Topic/CWinAppEx::GetShellManager.md)|Devuelve un puntero al objeto de [CShellManager](../../mfc/reference/cshellmanager-class.md) .|  
|[CWinAppEx::GetString](../Topic/CWinAppEx::GetString.md)|Lee los datos de cadena que está asociado con el valor especificado del registro.|  
|[CWinAppEx::GetTooltipManager](../Topic/CWinAppEx::GetTooltipManager.md)|Devuelve un puntero al objeto de [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) .|  
|[CWinAppEx::GetUserToolsManager](../Topic/CWinAppEx::GetUserToolsManager.md)|Devuelve un puntero al objeto de [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md) .|  
|[CWinAppEx::InitContextMenuManager](../Topic/CWinAppEx::InitContextMenuManager.md)|Inicializa el objeto `CContextMenuManager`.|  
|[CWinAppEx::InitKeyboardManager](../Topic/CWinAppEx::InitKeyboardManager.md)|Inicializa el objeto `CKeyboardManager`.|  
|[CWinAppEx::InitMouseManager](../Topic/CWinAppEx::InitMouseManager.md)|Inicializa el objeto `CMouseManager`.|  
|[CWinAppEx::InitShellManager](../Topic/CWinAppEx::InitShellManager.md)|Inicializa la clase de `CShellManager`|  
|[CWinAppEx::InitTooltipManager](../Topic/CWinAppEx::InitTooltipManager.md)|Inicializa la clase `CTooltipManager`.|  
|[CWinAppEx::IsResourceSmartUpdate](../Topic/CWinAppEx::IsResourceSmartUpdate.md)||  
|[CWinAppEx::IsStateExists](../Topic/CWinAppEx::IsStateExists.md)|Indica si la clave especificada está en el registro.|  
|[CWinAppEx::LoadState](../Topic/CWinAppEx::LoadState.md)|Carga el estado de la aplicación del registro.|  
|[CWinAppEx::OnAppContextHelp](../Topic/CWinAppEx::OnAppContextHelp.md)|Llamado por el marco cuando ayuda contextual de las solicitudes del usuario para el cuadro de diálogo de **personalización** .|  
|[CWinAppEx::OnViewDoubleClick](../Topic/CWinAppEx::OnViewDoubleClick.md)|Llama al comando definido por el usuario cuando el usuario hace doble clic en cualquier parte de la aplicación.|  
|[CWinAppEx::OnWorkspaceIdle](../Topic/CWinAppEx::OnWorkspaceIdle.md)||  
|[CWinAppEx::SaveState](../Topic/CWinAppEx::SaveState.md)|Escribe el estado de aplicación en el Registro de Windows.|  
|[CWinAppEx::SetRegistryBase](../Topic/CWinAppEx::SetRegistryBase.md)|Establece la ruta de acceso a la clave del Registro predeterminada.  Esta clave actúa como raíz para todas las llamadas subsiguientes del registro.|  
|[CWinAppEx::ShowPopupMenu](../Topic/CWinAppEx::ShowPopupMenu.md)|Muestra un menú emergente.|  
|[CWinAppEx::WriteBinary](../Topic/CWinAppEx::WriteBinary.md)|Escribe los datos binarios al valor del Registro especificado.|  
|[CWinAppEx::WriteInt](../Topic/CWinAppEx::WriteInt.md)|Escribe los datos numéricos del valor del Registro especificado.|  
|[CWinAppEx::WriteObject](../Topic/CWinAppEx::WriteObject.md)|Escribe los datos que se deriva de [CObject Class](../../mfc/reference/cobject-class.md) al valor del Registro especificado.|  
|[CWinAppEx::WriteSectionBinary](../Topic/CWinAppEx::WriteSectionBinary.md)|Escribe los datos binarios en un valor de la clave del Registro especificada.|  
|[CWinAppEx::WriteSectionInt](../Topic/CWinAppEx::WriteSectionInt.md)|Escribe los datos numéricos en un valor de la clave del Registro especificada.|  
|[CWinAppEx::WriteSectionObject](../Topic/CWinAppEx::WriteSectionObject.md)|Escribe los datos derivados de la clase de `CObject` a un valor de la clave del Registro especificada.|  
|[CWinAppEx::WriteSectionString](../Topic/CWinAppEx::WriteSectionString.md)|Escribe los datos de cadena en un valor de la clave del Registro especificada.|  
|[CWinAppEx::WriteString](../Topic/CWinAppEx::WriteString.md)|Escribe los datos de cadena al valor del Registro especificado.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinAppEx::LoadCustomState](../Topic/CWinAppEx::LoadCustomState.md)|Llamado por el marco cuando el estado de aplicación se ha cargado.|  
|[CWinAppEx::LoadWindowPlacement](../Topic/CWinAppEx::LoadWindowPlacement.md)|Llamado por el marco cuando carga el tamaño y la ubicación de la aplicación del registro.  Los datos carga incluye el tamaño y la ubicación del marco principal la última de se cierra la aplicación en el momento.|  
|[CWinAppEx::OnClosingMainFrame](../Topic/CWinAppEx::OnClosingMainFrame.md)|Llamado por el marco cuando una ventana de marco principal está procesando `WM_CLOSE`.|  
|[CWinAppEx::PreLoadState](../Topic/CWinAppEx::PreLoadState.md)|Llamado por el marco inmediatamente antes del estado de aplicación se carga.|  
|[CWinAppEx::PreSaveState](../Topic/CWinAppEx::PreSaveState.md)|Llamado por el marco inmediatamente antes del estado de aplicación se guarda.|  
|[CWinAppEx::ReloadWindowPlacement](../Topic/CWinAppEx::ReloadWindowPlacement.md)|Recarga el tamaño y la ubicación de la ventana proporcionada del registro|  
|[CWinAppEx::SaveCustomState](../Topic/CWinAppEx::SaveCustomState.md)|Llamado por el marco después de escribir el estado de la aplicación en el registro.|  
|[CWinAppEx::StoreWindowPlacement](../Topic/CWinAppEx::StoreWindowPlacement.md)|Llamado por el marco para escribir el tamaño y la ubicación del marco principal al registro.|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinAppEx::m\_bForceImageReset](../Topic/CWinAppEx::m_bForceImageReset.md)|Especifica si el marco restaure todas las imágenes de la barra de herramientas cuando la ventana de marco que contiene la barra de herramientas se carga.|  
  
## Comentarios  
 Gran parte de la funcionalidad proporcionada por el marco de trabajo de MFC dependerá del tipo de `CWinAppEx` .  Puede especificar la clase de `CWinAppEx` en la aplicación de dos maneras:  
  
-   Cree una clase de `CWinAppEx` en el subproceso principal.  
  
-   Derive la clase principal de la aplicación de `CWinAppEx`.  
  
 Después de escribir `CWinAppEx` en la aplicación, puede inicializar de los administradores de la aplicación.  Antes de utilizar un administrador de la aplicación, debe inicializarlo llamando a cuál es el método initialize.  Para obtener un puntero a un administrador concreto, llame al asociado obtienen método.  La clase de `CWinAppEx` administra los administradores de aplicaciones siguientes: [CMouseManager Class](../../mfc/reference/cmousemanager-class.md), [CContextMenuManager Class](../../mfc/reference/ccontextmenumanager-class.md), [CKeyboardManager Class](../../mfc/reference/ckeyboardmanager-class.md), [CUserToolsManager Class](../../mfc/reference/cusertoolsmanager-class.md), y [CMenuTearOffManager Class](../../mfc/reference/cmenutearoffmanager-class.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 [CWinApp](../../mfc/reference/cwinapp-class.md)  
  
 [CWinAppEx](../../mfc/reference/cwinappex-class.md)  
  
## Requisitos  
 **encabezado:** afxwinappex.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CWinApp Class](../../mfc/reference/cwinapp-class.md)   
 [CMouseManager Class](../../mfc/reference/cmousemanager-class.md)   
 [CContextMenuManager Class](../../mfc/reference/ccontextmenumanager-class.md)   
 [CKeyboardManager Class](../../mfc/reference/ckeyboardmanager-class.md)   
 [CUserToolsManager Class](../../mfc/reference/cusertoolsmanager-class.md)