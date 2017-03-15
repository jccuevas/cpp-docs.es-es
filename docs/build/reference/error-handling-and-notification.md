---
title: "Notificaci&#243;n y control de errores | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de errores, y notificación"
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Notificaci&#243;n y control de errores
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para obtener más información sobre la notificación y el control de errores, vea [Función auxiliar](http://msdn.microsoft.com/es-es/6279c12c-d908-4967-b0b3-cabfc3e91d3d).  
  
 Para obtener más información sobre las funciones de enlace, vea [Definiciones de estructura y de constante](../../build/reference/structure-and-constant-definitions.md).  
  
 Si el programa utiliza archivos DLL de carga retrasada, deberá controlar los errores con fiabilidad, ya que los que se produzcan durante su ejecución provocarán excepciones no controladas.  El control de errores se compone de dos partes:  
  
 Recuperación mediante un enlace.  
 Si es necesario recuperar un código o proporcionar una biblioteca y\/o rutina alternativas en caso de error, se puede proporcionar un *enlace* a la función auxiliar que permita solucionar la situación.  La rutina del enlace tiene que devolver un valor apropiado para que pueda continuar el procesamiento \(HINSTANCE o FARPROC\), o el valor 0 para indicar que debe producirse una excepción.  También podría producir su propia excepción o **longjmp**  desde el enlace.  Existen enlaces de notificación y enlaces de error.  
  
 Informe a través de una excepción.  
 Si todo lo necesario para controlar el error es anular el procedimiento, no se necesita un enlace mientras el código del usuario pueda controlar la excepción.  
  
 Los temas siguientes tratan el control y la notificación de errores.  
  
-   [Enlaces de notificación](../../build/reference/notification-hooks.md)  
  
-   [Enlaces de error](../../build/reference/failure-hooks.md)  
  
-   [Excepciones](../../build/reference/exceptions-c-cpp.md)  
  
## Vea también  
 [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)