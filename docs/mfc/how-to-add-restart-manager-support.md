---
title: "C&#243;mo: Agregar compatibilidad con el Administrador de reinicio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Administrador de reinicio"
  - "C++, compatibilidad con el bloqueo de aplicación"
ms.assetid: 7f3f5867-d4bc-4ba8-b3c9-dc1e7be93642
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Agregar compatibilidad con el Administrador de reinicio
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El Administrador de reinicio es una característica agregada a [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] para [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)]. El Administrador de reinicio agrega compatibilidad para la aplicación en caso de cierre o reinicio de forma inesperada. El comportamiento del Administrador de reinicio depende del tipo de aplicación. Si la aplicación es un editor de documentos, el Administrador de reinicio permite que la aplicación guarde automáticamente el estado y el contenido de cualquier documento abierto y reinicia la aplicación después de que se cierre de forma inesperada. Si la aplicación no es un editor de documentos, el Administrador de reinicio reinicia la aplicación, pero no puede guardar el estado de la aplicación de forma predeterminada.  
  
 Después del reinicio, la aplicación muestra un cuadro de diálogo de tarea si la aplicación es Unicode. Si se trata de una aplicación ANSI, muestra un cuadro de mensaje de Windows. En este punto, el usuario decide si se deben restaurar los documentos guardados automáticamente. Si el usuario no restaura los documentos guardados automáticamente, el Administrador de reinicio descarta los archivos temporales.  
  
> [!NOTE]
>  Puede reemplazar el comportamiento predeterminado del Administrador de reinicio para guardar los datos y reiniciar la aplicación.  
  
 De forma predeterminada, las aplicaciones de MFC creadas con el asistente para proyectos de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] admiten el Administrador de reinicio cuando se ejecutan en un equipo que tiene [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)]. Si no desea que la aplicación admita el Administrador de reinicio, puede deshabilitarlo en el asistente para nuevo proyecto.  
  
### Para agregar compatibilidad con el Administrador de reinicio a una aplicación existente  
  
1.  Abra una aplicación de MFC existente en [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
2.  Abra el archivo de código fuente de la aplicación principal. De forma predeterminada, es el archivo .cpp que tiene el mismo nombre que la aplicación. Por ejemplo, el archivo de código fuente de la aplicación principal para MyProject es MyProject.cpp.  
  
3.  Busque el constructor de la aplicación principal. Por ejemplo, si el proyecto es MyProject, el constructor es `CMyProjectApp::CMyProjectApp()`.  
  
4.  Agregue la siguiente línea de código al constructor:  
  
    ```  
    m_dwRestartManagerSupportFlags = AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS;  
    ```  
  
5.  Asegúrese de que el método `InitInstance` de la aplicación llama a su método principal `InitInstance`: [CWinApp::InitInstance](../Topic/CWinApp::InitInstance.md) o `CWinAppEx::InitInstance`. El método `InitInstance` es responsable de comprobar el parámetro `m_dwRestartManagerSupportFlags`.  
  
6.  Compile y ejecute la aplicación.  
  
## Vea también  
 [CDataRecoveryHandler Class](../mfc/reference/cdatarecoveryhandler-class.md)   
 [CWinApp::m\_dwRestartManagerSupportFlags](../Topic/CWinApp::m_dwRestartManagerSupportFlags.md)   
 [CWinApp Class](../mfc/reference/cwinapp-class.md)   
 [CWinApp::m\_nAutosaveInterval](../Topic/CWinApp::m_nAutosaveInterval.md)   
 [CDocument::OnDocumentEvent](../Topic/CDocument::OnDocumentEvent.md)