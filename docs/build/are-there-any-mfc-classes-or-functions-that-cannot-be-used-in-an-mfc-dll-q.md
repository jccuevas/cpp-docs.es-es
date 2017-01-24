---
title: "&#191;Hay clases o funciones MFC que no se puedan utilizar en un archivo DLL de MFC? | Microsoft Docs"
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
  - "DLL [C++], MFC"
  - "DLL [C++], restricciones"
  - "DLL de MFC [C++], restricciones"
ms.assetid: 18e2f1cb-4f72-4d3a-a951-3488208872c7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &#191;Hay clases o funciones MFC que no se puedan utilizar en un archivo DLL de MFC?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los archivos DLL de extensión deben utilizar la clase derivada de `CWinApp` de la aplicación de cliente.  No deben tener una clase derivada de `CWinApp` propia.  
  
 Los archivos DLL estándar deben contener una clase derivada de `CWinApp` y un solo objeto de dicha clase de aplicación, como sucede en una aplicación MFC.  A diferencia del objeto `CWinApp` de una aplicación, el objeto `CWinApp` del archivo DLL no tiene un suministro principal de mensajes.  
  
 Tenga en cuenta que, como el mecanismo `CWinApp::Run` no se aplica a un archivo DLL, la aplicación es propietaria del suministro principal de mensajes.  Si el archivo DLL abre cuadros de diálogo no modales o tiene una ventana de marco principal propia, el suministro principal de mensajes de la aplicación deberá llamar a una rutina exportada por el archivo DLL que, a su vez, llamará a la función miembro de `CWinApp::PreTranslateMessage` del objeto de aplicación del archivo DLL.  
  
## Vea también  
 [Preguntas más frecuentes sobre archivos DLL](../build/dll-frequently-asked-questions.md)