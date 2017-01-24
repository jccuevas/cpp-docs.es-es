---
title: "Inicializar y limpiar documentos y vistas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "objetos de documentos, ciclo de vida de"
  - "documentos, limpieza"
  - "documentos, inicializar"
  - "inicializar documentos"
  - "inicializar objetos, objetos de documentos"
  - "inicializar vistas"
  - "vistas, limpieza"
  - "vistas, inicializar"
ms.assetid: 95d6f09b-a047-4079-856a-ae7d0548e9d2
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Inicializar y limpiar documentos y vistas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilice las instrucciones siguientes para inicializar y limpiar después de documentos y vistas:  
  
-   El marco de trabajo de MFC inicializa documentos y vistas; puede inicializar los datos que agregue a ellos.  
  
-   El marco limpia como cierre documentos y vistas; debe desasignar cualquier memoria que se afectara asignado en el montón dentro de las funciones miembro de esos documentos y vistas.  
  
> [!NOTE]
>  Recuerde que la inicialización para toda la aplicación es mejor hecho en el reemplazo de la función miembro de [InitInstance](../Topic/CWinApp::InitInstance.md) de la clase `CWinApp`, y limpieza para toda la aplicación es mejor hecho en el reemplazo de la función [ExitInstance](../Topic/CWinApp::ExitInstance.md)miembro de `CWinApp` .  
  
 El ciclo de vida de un documento \(y la ventana de marco y vista u vistas\) en una aplicación MDI es la siguiente:  
  
1.  Durante la creación dinámica, se llama al constructor del documento.  
  
2.  Para cada nuevo, se llama [OnNewDocument](../Topic/CDocument::OnNewDocument.md) o [OnOpenDocument](../Topic/CDocument::OnOpenDocument.md) del documento.  
  
3.  El usuario interactúa con el documento en su duración.  Esto ocurre normalmente cuando el usuario trabaja en datos de documento con la vista, seleccionar y editar los datos.  La vista pasa cambios en el documento para el almacenamiento y actualizar otras vistas.  Durante este tiempo el documento y vista pueden controlar los comandos.  
  
4.  El marco de trabajo llama a [DeleteContents](../Topic/CDocument::DeleteContents.md) para eliminar datos específicos de un documento.  
  
5.  Se llama al destructor del documento.  
  
 En una aplicación SDI, el paso 1 se realiza una vez, cuando el documento se crea por primera vez.  A continuación los pasos 2 a 4 se realizan repetidamente cada vez que se abra un documento nuevo.  El nuevo documento reutiliza el objeto documento existente.  Finalmente, se realiza el paso 5 cuando se cierra la aplicación.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Documentos y vistas que se inicializan](../mfc/initializing-documents-and-views.md)  
  
-   [El limpiar documentos ni vistas](../mfc/cleaning-up-documents-and-views.md)  
  
## Vea también  
 [Arquitectura documento\/vista](../mfc/document-view-architecture.md)