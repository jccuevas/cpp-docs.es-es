---
title: "exit (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Exit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exit (función)"
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# exit (Funci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La función **exit**, declarada en el archivo de inclusión estándar STDLIB.H, finaliza un programa de C\+\+.  
  
 El valor proporcionado como argumento a **exit** se devuelve al sistema operativo como código de retorno o código de salida del programa.  Por convención, un código de retorno de cero significa que el programa se completó correctamente.  
  
> [!NOTE]
>  Puede utilizar las constantes `EXIT_FAILURE` y `EXIT_SUCCESS`, definidas en STDLIB.H, para indicar si el programa se ha completado correctamente o ha generado errores.  
  
 Emitir una instrucción `return` desde la función **main** equivale a llamar a la función **exit** con el valor devuelto como argumento.  
  
 Para obtener más información, vea [exit](../c-runtime-library/reference/exit-exit-exit.md) en la *Referencia de la biblioteca en tiempo de ejecución*.  
  
## Vea también  
 [Finalización del programa](../cpp/program-termination.md)