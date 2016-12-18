---
title: "CWinApp: The Application (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CWinApp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clase de aplicación"
  - "CWinApp (clase), CWinThread"
  - "CWinApp (clase), multithreading"
  - "CWinApp (clase), WinMain"
  - "CWinThread (clase), y CWinApp"
  - "InitApplication (método)"
  - "MFC [C++], WinMain y"
  - "WinMain (método)"
  - "WinMain (método), en MFC"
ms.assetid: 935822bb-d463-481b-a5f6-9719d68ed1d5
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWinApp: The Application (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase principal de la aplicación en MFC encapsula la inicialización, ejecute, y la finalización de una aplicación para el sistema operativo Windows.  Una aplicación compilada en el marco debe tener un único objeto de una clase derivada de [CWinApp](../mfc/reference/cwinapp-class.md).  Se construye este objeto antes de que se creen las ventanas.  
  
 `CWinApp` se deriva de `CWinThread`, que representa el subproceso principal de la ejecución de la aplicación, que puede tener uno o más subprocesos.  En versiones recientes de MFC, `InitInstance`, **Ejecutar**, `ExitInstance`, y las funciones miembro de `OnIdle` están realmente en la clase `CWinThread`.  Estas funciones se tratan aquí como si fuesen miembros de `CWinApp` en su lugar, porque la descripción se conoce al rol de objeto como un objeto de la aplicación en lugar de como subproceso primario.  
  
> [!NOTE]
>  La clase app constituye el subproceso principal de la aplicación de la ejecución.  Mediante funciones de la API Win32, también puede crear subprocesos secundarios de la ejecución.  Estos subprocesos pueden utilizar la biblioteca MFC.  Para obtener más información, vea [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
 Como cualquier programa para el sistema operativo Windows, la aplicación de .NET framework tiene una función de `WinMain` .  En una aplicación de .NET framework, sin embargo, no se escribe `WinMain`.  Proporciona la biblioteca de clases y denominada cuando se inicia la aplicación.  `WinMain` contiene servicios estándar como registrar clases de ventana.  Llama a las funciones miembro del objeto application para inicializar y ejecutar la aplicación. \(Puede personalizar `WinMain` reemplazando el miembro de `CWinApp` funciona que las llamadas de `WinMain` .\)  
  
 Para inicializar la aplicación, las llamadas de `WinMain` el miembro de `InitApplication` y de `InitInstance` del objeto application funcionan.  Para ejecutar el bucle de mensajes de la aplicación, `WinMain` llama a la función miembro de **Ejecutar** .  En la finalización, `WinMain` llama a la función miembro de `ExitInstance` del objeto application.  
  
> [!NOTE]
>  Los nombres mostrados en **negrita** en esta documentación indican los elementos proporcionados por la biblioteca Microsoft Foundation Class\) y Visual C\+\+.  Los nombres mostrados en el tipo de `monospaced` indican los elementos que crea o invalida.  
  
## Vea también  
 [Temas generales de MFC](../mfc/general-mfc-topics.md)   
 [CWinApp y el Asistente para aplicaciones MFC](../mfc/cwinapp-and-the-mfc-application-wizard.md)   
 [Funciones miembro de CWinApp que se pueden sobrecargar](../mfc/overridable-cwinapp-member-functions.md)   
 [Servicios especiales de CWinApp](../mfc/special-cwinapp-services.md)