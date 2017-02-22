---
title: "Informaci&#243;n y administraci&#243;n de aplicaciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aplicaciones [MFC], administrar"
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# Informaci&#243;n y administraci&#243;n de aplicaciones
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Al escribir una aplicación, cree solo [CWinApp](../../mfc/reference/cwinapp-class.md)\- objeto derivado.  A veces, puede que desee recopilar la información sobre este objeto desde fuera de `CWinApp`\- objeto derivado.  
  
 La biblioteca Microsoft Foundation Class proporciona funciones globales siguientes para ayudarle a realizar estas tareas:  
  
### Información de la aplicación y funciones de administración  
  
|||  
|-|-|  
|[AfxBeginThread](../Topic/AfxBeginThread.md)|Crea un nuevo subproceso.|  
|[AfxEndThread](../Topic/AfxEndThread.md)|Finaliza el subproceso actual.|  
|[AfxFreeLibrary](../Topic/AfxFreeLibrary.md)|Disminuye el recuento de referencias del módulo cargado de \(DLL\) de biblioteca de vínculos dinámicos; cuando el recuento de referencias llega a cero, el módulo es no asignados.|  
|[AfxGetApp](../Topic/AfxGetApp.md)|Devuelve un puntero al mismo objeto de `CWinApp` de la aplicación.|  
|[AfxGetAppName](../Topic/AfxGetAppName.md)|Devuelve una cadena que contiene el nombre de aplicación.|  
|[AfxGetInstanceHandle](../Topic/AfxGetInstanceHandle.md)|Devuelve `HINSTANCE` que representa esta instancia de la aplicación.|  
|[AfxGetMainWnd](../Topic/AfxGetMainWnd.md)|Devuelve un puntero a la ventana “principal” actual de una aplicación de no OLE, o la ventana en el contexto del marco de una aplicación de servidor.|  
|[AfxGetPerUserRegistration](../Topic/AfxGetPerUserRegistration.md)|Utilice esta función para determinar si la aplicación redirige el acceso del registro en el nodo de **HKEY\_CURRENT\_USER** \(**HKCU**\).|  
|[AfxGetResourceHandle](../Topic/AfxGetResourceHandle.md)|Devuelve `HINSTANCE` al origen de los recursos predeterminados de la aplicación.  Utilice esto para tener acceso a los recursos de la aplicación directamente.|  
|[AfxGetThread](../Topic/AfxGetThread.md)|Recupera un puntero al objeto actual de [CWinThread](../../mfc/reference/cwinthread-class.md) .|  
|[AfxInitRichEdit](../Topic/AfxInitRichEdit.md)|Inicializa el control de edición amplio de la versión 1.0 para la aplicación.|  
|[AfxInitRichEdit2](../Topic/AfxInitRichEdit2.md)|Inicializa la versión 2.0 y el control rich edit posterior para la aplicación.|  
|[AfxLoadLibrary](../Topic/AfxLoadLibrary.md)|Asigna un módulo de DLL y devuelve un identificador que se puede utilizar para obtener la dirección de una función DLL.|  
|[AfxRegisterClass](../Topic/AfxRegisterClass.md)|Registra una clase de ventana en un archivo DLL que utiliza MFC.|  
|[Clase](../Topic/AfxRegisterWndClass.md)|Registra una clase de ventana de Windows para complementar los registrados automáticamente por MFC.|  
|[AfxSetPerUserRegistration](../Topic/AfxSetPerUserRegistration.md)|Establece si la aplicación redirige el acceso del registro en el nodo de **HKEY\_CURRENT\_USER** \(**HKCU**\).|  
|[AfxSetResourceHandle](../Topic/AfxSetResourceHandle.md)|Establece el identificador de `HINSTANCE` donde los recursos predeterminados de la aplicación se cargan.|  
|[AfxSocketInit](../Topic/AfxSocketInit.md)|Denominado en un reemplazo de `CWinApp::InitInstance` para inicializar Windows Sockets.|  
|[AfxWinInit](../Topic/AfxWinInit.md)|Llama a la función MFC\- proporcionada de `WinMain` , como parte de la inicialización de [CWinApp](../../mfc/reference/cwinapp-class.md) de una aplicación GUI\- basada, para inicializar MFC.  Se debe llamar directamente para aplicaciones de consola que utilizan MFC.|  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)   
 [CWinApp Class](../../mfc/reference/cwinapp-class.md)