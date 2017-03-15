---
title: "ML Error Messages | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.errors.ml"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MASM (Microsoft Macro Assembler), ML error messages"
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# ML Error Messages
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Los mensajes de error generados por componentes de MASM se clasifican en tres categorías:  
  
-   **errores irrecuperables.** Estas líneas indican un problema grave que evita que la utilidad complete el proceso normal.  
  
-   **Errores no graves.** La utilidad puede completar el proceso.  Si lo hace, el resultado no es probable que el que desee.  
  
-   **advertencias.** Estos mensajes especifican las condiciones que pueden impedir que obtenga los resultados que desea.  
  
 Todos los mensajes de error adoptan la forma siguiente:  
  
```  
  
Utility: Filename (Line) : [Error_type} (Code): Message_text  
```  
  
 donde:  
  
 `Utility`  
 el programa que envió el mensaje de error.  
  
 *nombre de archivo*  
 el archivo que contiene la condición error\-que genera.  
  
 *Line*  
 la línea aproximada donde existe la condición de error.  
  
 *Error\_type*  
 Error irrecuperable, error, o warning.  
  
 *Código*  
 el único 5 \- o código de error de 6 dígitos.  
  
 `Message_text`  
 una descripción breve y general de la condición de error.  
  
## Vea también  
 [Microsoft Macro Assembler Reference](../../assembler/masm/microsoft-macro-assembler-reference.md)