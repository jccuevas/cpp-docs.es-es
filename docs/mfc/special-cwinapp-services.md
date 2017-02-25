---
title: "Servicios especiales de CWinApp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LoadStdProfileSettings"
  - "EnableShellOpen"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "objetos de aplicación [C++], servicios"
  - "CWinApp (clase), arrastrar y colocar el Administrador de archivos"
  - "CWinApp (clase), inicializar GDI+"
  - "CWinApp (clase), documentos usados recientemente"
  - "CWinApp (clase), servicios"
  - "CWinApp (clase), registro shell"
  - "arrastrar y colocar [C++], archivos"
  - "DragAcceptFiles (método)"
  - "EnableShellOpen (método)"
  - "archivos [C++], arrastrar y colocar"
  - "archivos [C++], usados más recientemente"
  - "GDI+, inicializar para MFC"
  - "GDI+, suprimir subproceso en segundo plano [MFC]"
  - "LoadStdProfileSettings (método)"
  - "MFC [C++], operaciones en archivo"
  - "MFC [C++], enumeración de los archivos usados más recientemente"
  - "MFC [C++], registro shell"
  - "listas de MRU"
  - "registrar tipos de archivos"
  - "RegisterShellFileTypes (método)"
  - "registro [C++], shell"
  - "registro [C++], archivos usados más recientemente"
  - "servicios, proporcionado por CWinApp"
  - "Shell, registrar tipos de archivos"
ms.assetid: 0480cd01-f629-4249-b221-93432d95b431
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Servicios especiales de CWinApp
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Además de ejecutar el bucle de mensajes y de que el usuario tenga la oportunidad de inicializar la aplicación y para limpiar después de ella, [CWinApp](../mfc/reference/cwinapp-class.md) proporciona varios otros servicios.  
  
##  <a name="_core_shell_registration"></a> Registro de shell  
 De forma predeterminada, el asistente para aplicaciones MFC permite al usuario a los archivos de datos abierto que la aplicación ha creado haciendo doble clic en el Explorador o administrador de archivo del archivo.  Si la aplicación es una aplicación MDI y especifica una extensión para los archivos que crea la aplicación, el asistente para aplicaciones MFC agregue llamadas a [RegisterShellFileTypes](../Topic/CWinApp::RegisterShellFileTypes.md) y las funciones miembro de [EnableShellOpen](../Topic/CWinApp::EnableShellOpen.md) de [CWinApp](../mfc/reference/cwinapp-class.md) a `InitInstance` reemplazan que escribe automáticamente.  
  
 `RegisterShellFileTypes` registra los tipos de documento de la aplicación con el Explorador o el administrador de archivos del archivo.  La función agrega entradas a la base de datos de registro que Windows mantiene.  Las entradas registrar cada tipo de documento, asociar una extensión de archivo al tipo de archivo, especifique una línea de comandos para abrir la aplicación, y especifique un comando de intercambio de datos dinámicos de \(DDE\) de abrir un documento de ese tipo.  
  
 `EnableShellOpen` completa el proceso permitiendo la aplicación para recibir los comandos DDE desde el archivo Explorador o administrador de archivos de abrir el archivo elegido por el usuario.  
  
 Esta compatibilidad automático del registro en `CWinApp` elimina la necesidad de enviar un archivo .reg con la aplicación o de realizar el trabajo de la instalación especial.  
  
 Si desea inicializar GDI\+ para la aplicación \(llamando a [GdiplusStartup](_gdiplus_FUNC_GdiplusStartup_token_input_output_) en función de [InitInstance](../Topic/CWinApp::InitInstance.md) \), tiene que suprimir el subproceso en segundo plano de GDI\+.  
  
 Puede hacer estableciendo el miembro de **SuppressBackgroundThread** de la estructura de [GdiplusStartupInput](_gdiplus_STRUC_GdiplusStartupInput) a **VERDADERO**.  Al suprimir el subproceso de fondo GDI\+, las llamadas de **NotificationHook** y de **NotificationUnhook** \(vea [GdiplusStartupOutput](_gdiplus_STRUC_GdiplusStartupOutput)\) se deben realizar justo antes de entrar y de salir del bucle de mensajes de la aplicación.  Por consiguiente, un buen lugar para llamar a **GdiplusStartup** y las funciones de notificación de enlace tendrían un reemplazo de la función virtual [CWinApp::Run](../Topic/CWinApp::Run.md), como se muestra a continuación:  
  
 [!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/CPP/special-cwinapp-services_1.cpp)]  
  
 Si no suprime el subproceso en segundo plano GDI\+, los comandos DDE pueden emitir prematuramente a la aplicación antes de crear la ventana principal.  Los comandos DDE emitidos por el shell pueden estar cancelado prematuramente, por lo que los mensajes de error.  
  
##  <a name="_core_file_manager_drag_and_drop"></a> Arrastrar y colocar del administrador de archivos  
 Los archivos se pueden arrastrar desde la ventana vista de archivo en el Explorador del administrador de archivos o a una ventana en la aplicación.  Se podría, por ejemplo, habilite uno o más archivos que se arrastrarán a la ventana principal de una aplicación MDI, donde la aplicación podría recuperar los nombres de archivo y abrir ventanas secundarias MDI para esos archivos.  
  
 Para habilitar arrastrar y colocar del archivo en la aplicación, el asistente para aplicaciones MFC escribe una llamada a la función [DragAcceptFiles](../Topic/CWnd::DragAcceptFiles.md) miembro de [CWnd](../mfc/reference/cwnd-class.md) para la ventana de marco principal en `InitInstance`.  Puede quitar esa llamada si no desea implementar la característica de arrastrar y colocar.  
  
> [!NOTE]
>  También puede implementar un arrastrar y colocar más general capacidad\- que arrastra datos entre o dentro documento\- con OLE.  Para obtener información, vea el artículo [Arrastrar y colocar \(OLE\)](../mfc/drag-and-drop-ole.md).  
  
##  <a name="_core_keeping_track_of_the_most_recently_used_documents"></a> Seguimiento de documentos utilizados Más Recientemente  
 Cuando el usuario abre y cierra los archivos, el objeto application realiza el seguimiento de los cuatro archivos usados recientemente.  Los nombres de estos archivos se agregan al menú archivo y se actualizan cuando cambian.  El marco almacena estos nombres de archivo en el registro o en el archivo .ini, con el mismo nombre que el proyecto y los lee del archivo cuando se inicia la aplicación.  La invalidación de `InitInstance` que el asistente para aplicaciones MFC crea automáticamente incluye una llamada a la función [LoadStdProfileSettings](../Topic/CWinApp::LoadStdProfileSettings.md)miembro de [CWinApp](../mfc/reference/cwinapp-class.md) , que carga la información del registro o del archivo .ini, incluidos los nombres de archivos usados recientemente.  
  
 Se almacenan estas entradas como sigue:  
  
-   En Windows NT, Windows 2000, y versiones posteriores, el valor se almacena en una clave del Registro.  
  
-   En Windows 3.x, el valor se almacena en el archivo Win.ini.  
  
-   En Windows 95 y versiones posteriores, el valor se almacena en una versión almacenada en memoria caché de WIN.INI.  
  
## Vea también  
 [CWinApp: The Application \(Clase\)](../mfc/cwinapp-the-application-class.md)