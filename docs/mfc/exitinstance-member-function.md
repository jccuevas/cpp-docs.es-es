---
title: "ExitInstance Member (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CWinApp::ExitInstance"
  - "CWinApp.ExitInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinApp (clase), ExitInstance"
  - "ExitInstance (método)"
  - "programas [C++], terminar"
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ExitInstance Member (Funci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La función miembro de [ExitInstance](../Topic/CWinApp::ExitInstance.md) de la clase [CWinApp](../mfc/reference/cwinapp-class.md) se llama cada vez que una copia de la aplicación finaliza, normalmente como resultado del usuario que finaliza.  
  
 Reemplace `ExitInstance` si necesita el procesamiento especial de limpieza, como liberar los recursos de \(GDI\) de la interfaz de dispositivo gráfico o desasignar la memoria utilizada durante la ejecución del programa.  Limpieza de elementos como documentos y vistas, sin embargo, es proporcionada por el marco, otras funciones reemplazables para hacer concreto especial de limpieza a esos objetos.  
  
## Vea también  
 [CWinApp: The Application \(Clase\)](../mfc/cwinapp-the-application-class.md)