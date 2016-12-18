---
title: "Evitar &#225;reas de riesgo en programas multiproceso | Microsoft Docs"
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
  - "errores [C++], programas multiproceso"
  - "subprocesamiento múltiple [C++], solucionar problemas"
  - "subprocesamiento [C++], solucionar problemas"
  - "solucionar problemas [C++], multithreading"
ms.assetid: 06cc231d-bb5a-409d-8bd3-676c9e2a8c5b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Evitar &#225;reas de riesgo en programas multiproceso
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al crear, vincular o ejecutar un programa multiproceso en C, pueden presentarse algunos problemas.  Algunos de los problemas más comunes se describen en la tabla siguiente. \(Encontrará una discusión similar desde el punto de vista de MFC en [Multithreading: sugerencias de programación](../parallel/multithreading-programming-tips.md).\)  
  
|Problema|Causa probable|  
|--------------|--------------------|  
|Aparece un cuadro de mensaje que indica que el programa produjo una infracción de la protección.|Muchos errores de programación de Win32 causan infracciones de protección.  Una causa habitual de las infracciones de protección es la asignación indirecta de datos a punteros null.  Esto último hace que el programa intente obtener acceso a memoria que no le pertenece, lo que produce una infracción de la protección.<br /><br /> Un método fácil para detectar la causa de una infracción de la protección consiste en compilar el programa con información de depuración y, a continuación, ejecutarlo por medio del depurador en el entorno de Visual C\+\+.  Cuando se produce el error de protección, Windows transfiere el control al depurador y coloca el cursor en la línea que causó el problema.|  
|El programa genera numerosos errores de compilación y vinculación.|Puede eliminar muchos posibles problemas si configura el nivel de advertencias del compilador con uno de sus valores más altos y tiene en cuenta los mensajes de advertencia.  Si utiliza los niveles de advertencia 3 ó 4, puede detectar conversiones de datos no intencionadas y prototipos de funciones que faltan, así como el uso de características no incluidas en el estándar ANSI.|  
  
## Vea también  
 [Subprocesamiento múltiple con C y Win32](../parallel/multithreading-with-c-and-win32.md)