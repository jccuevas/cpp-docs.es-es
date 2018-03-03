---
title: "Cómo: agregar compatibilidad con el Administrador de reinicio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Restart manager [MFC]
- C++, application crash support
ms.assetid: 7f3f5867-d4bc-4ba8-b3c9-dc1e7be93642
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a413f28909a52e3bc82e9d8f2694d559bf8a885c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-add-restart-manager-support"></a>Cómo: Agregar compatibilidad con el Administrador de reinicio
El Administrador de reinicio es una característica agregada a [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] para [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)]. El Administrador de reinicio agrega compatibilidad para la aplicación en caso de cierre o reinicio de forma inesperada. El comportamiento del Administrador de reinicio depende del tipo de aplicación. Si la aplicación es un editor de documentos, el Administrador de reinicio permite que la aplicación guarde automáticamente el estado y el contenido de cualquier documento abierto y reinicia la aplicación después de que se cierre de forma inesperada. Si la aplicación no es un editor de documentos, el Administrador de reinicio reinicia la aplicación, pero no puede guardar el estado de la aplicación de forma predeterminada.  
  
 Después del reinicio, la aplicación muestra un cuadro de diálogo de tarea si la aplicación es Unicode. Si se trata de una aplicación ANSI, muestra un cuadro de mensaje de Windows. En este punto, el usuario decide si se deben restaurar los documentos guardados automáticamente. Si el usuario no restaura los documentos guardados automáticamente, el Administrador de reinicio descarta los archivos temporales.  
  
> [!NOTE]
>  Puede reemplazar el comportamiento predeterminado del Administrador de reinicio para guardar los datos y reiniciar la aplicación.  
  
 De forma predeterminada, las aplicaciones de MFC creadas con el asistente para proyectos de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] admiten el Administrador de reinicio cuando se ejecutan en un equipo que tiene [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)]. Si no desea que la aplicación admita el Administrador de reinicio, puede deshabilitarlo en el asistente para nuevo proyecto.  
  
### <a name="to-add-support-for-the-restart-manager-to-an-existing-application"></a>Para agregar compatibilidad con el Administrador de reinicio a una aplicación existente  
  
1.  Abra una aplicación de MFC existente en [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
2.  Abra el archivo de código fuente de la aplicación principal. De forma predeterminada, es el archivo .cpp que tiene el mismo nombre que la aplicación. Por ejemplo, el archivo de código fuente de la aplicación principal para MyProject es MyProject.cpp.  
  
3.  Busque el constructor de la aplicación principal. Por ejemplo, si el proyecto es MyProject, el constructor es `CMyProjectApp::CMyProjectApp()`.  
  
4.  Agregue la siguiente línea de código al constructor:  
  
 ```  
    m_dwRestartManagerSupportFlags = AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS;  
 ```  
  
5.  Asegúrese de que el método `InitInstance` de la aplicación llama a su método principal `InitInstance` : [CWinApp::InitInstance](../mfc/reference/cwinapp-class.md#initinstance) o `CWinAppEx::InitInstance`. El método `InitInstance` es responsable de comprobar el parámetro `m_dwRestartManagerSupportFlags` .  
  
6.  Compile y ejecute la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Clase CDataRecoveryHandler](../mfc/reference/cdatarecoveryhandler-class.md)   
 [CWinApp::m_dwRestartManagerSupportFlags](../mfc/reference/cwinapp-class.md#m_dwrestartmanagersupportflags)   
 [CWinApp (clase)](../mfc/reference/cwinapp-class.md)   
 [CWinApp::m_nAutosaveInterval](../mfc/reference/cwinapp-class.md#m_nautosaveinterval)   
 [CDocument::OnDocumentEvent](../mfc/reference/cdocument-class.md#ondocumentevent)

