---
title: "Marco (MFC) | Microsoft Docs"
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
  - "API [C++], encapsulación por Win32 MFC"
  - "marco de trabajo de la aplicación [C++], acerca del marco de trabajo de la aplicación MFC"
  - "API Win32 encapsulada"
  - "encapsulación [C++]"
  - "encapsulación [C++], API Win32"
  - "MFC [C++], marco de trabajo de la aplicación"
  - "Win32 [C++], encapsulación API por MFC"
  - "API de Windows [C++], encapsulación por MFC"
  - "clases contenedoras, explicadas"
ms.assetid: 3be0fec8-9843-4119-ae42-ece993ef500b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Marco (MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El trabajo con el marco de la biblioteca de \(MFC\) de la clase de la Microsoft foundation class se basa en gran medida en algunas clases importantes y varias herramientas de Visual C\+\+.  Algunas clases encapsulan a una gran parte de la interfaz de programación \(API\) de aplicaciones de Win32.  Otras clases encapsulan los conceptos de la aplicación como documentos, vistas, y la propia aplicación.  Quedan otros encapsulan la funcionalidad de las características de OLE y acceso a datos de ODBC y DAO.  
  
 Por ejemplo, el concepto de Win32 de ventana se encapsula en la clase MFC `CWnd`.  Es decir, el c\+\+. `CWnd` denominado clase encapsula o “ajusta” el identificador de `HWND` que representa una ventana de Windows.  Igualmente, la clase `CDialog` encapsula los cuadros de diálogo de Win32.  
  
 La encapsulación significa que la clase `CWnd`de C\+\+, por ejemplo, contiene una variable miembro de `HWND`con tipo, y las funciones miembro de clases encapsulan llamadas a funciones de Win32 que toman `HWND` como parámetro.  Las funciones miembro de clase normalmente tienen el mismo nombre que la función de Win32 que encapsula.  
  
## En esta sección  
 [SDI y MDI](../mfc/sdi-and-mdi.md)  
  
 [Documentos, vistas, y el marco](../mfc/documents-views-and-the-framework.md)  
  
 [Asistentes y editores de recursos](../mfc/wizards-and-the-resource-editors.md)  
  
## En secciones relacionadas  
 [La compilación en el marco](../mfc/building-on-the-framework.md)  
  
 [Cómo el marco de trabajo llama al código se](../mfc/how-the-framework-calls-your-code.md)  
  
 [CWinApp: La clase de aplicación](../mfc/cwinapp-the-application-class.md)  
  
 [Plantillas de documento y el proceso de Creación de documentos y vistas](../mfc/document-templates-and-the-document-view-creation-process.md)  
  
 [Control de mensajes y asignación](../mfc/message-handling-and-mapping.md)  
  
 [Objetos de la ventana](../mfc/window-objects.md)  
  
## Vea también  
 [Usar las clases para escribir aplicaciones para Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)