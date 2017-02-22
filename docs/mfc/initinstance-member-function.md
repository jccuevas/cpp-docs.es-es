---
title: "InitInstance Member (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InitInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aplicaciones [MFC], inicializar"
  - "inicializar aplicaciones de MFC"
  - "InitInstance (método)"
  - "MFC [C++], inicializar"
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# InitInstance Member (Funci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El sistema operativo Windows permite ejecutar más de una copia, o “instancia,” de la misma aplicación.  `WinMain` llama [InitInstance](../Topic/CWinApp::InitInstance.md) cada vez que una nueva instancia de la aplicación.  
  
 La implementación de `InitInstance` standard creada por el asistente para aplicaciones MFC realiza las tareas siguientes:  
  
-   Como su acción central, crea las plantillas de documento que a su vez crean documentos, las vistas, las ventanas de marco.  Para obtener una descripción de este proceso, vea [Creación de plantillas de documento](../mfc/document-template-creation.md).  
  
-   Opciones de archivo estándar de las cargas de un archivo .ini o el Registro de Windows, como los nombres de los archivos utilizados más recientemente.  
  
-   Registra una o más plantillas de documento.  
  
-   Para una aplicación MDI, crea una ventana de marco principal.  
  
-   Procesa la línea de comandos para abrir un documento especificado en la línea de comandos o abrir un nuevo, vacío documento.  
  
 Puede agregar dispone del código de inicialización o modificar el código escrito por el asistente.  
  
> [!NOTE]
>  Las aplicaciones MFC deben inicializarse como contenedor uniproceso \(STA\).  Si llama a [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) en la invalidación de `InitInstance`, especifique `COINIT_APARTMENTTHREADED` \(en lugar de `COINIT_MULTITHREADED`\).  Para obtener más información, vea el artículo PRB acerca de que la aplicación MFC deja de responder cuando la aplicación se inicializa como contenedor multiproceso \(828643\) en [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;828643](http://support.microsoft.com/default.aspx?scid=kb;en-us;828643).  
  
## Vea también  
 [CWinApp: The Application \(Clase\)](../mfc/cwinapp-the-application-class.md)