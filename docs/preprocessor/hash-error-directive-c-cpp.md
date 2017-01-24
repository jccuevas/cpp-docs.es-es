---
title: "#error (Directiva) (C/C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#error"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#error (directiva)"
  - "error (directiva) (#error)"
  - "preprocesador, directivas"
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #error (Directiva) (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La directiva `#error` emite un mensaje de error especificado por el usuario en tiempo de compilación y después finaliza la compilación.  
  
## Sintaxis  
  
```  
#error token-string  
```  
  
## Comentarios  
 El mensaje de error que esta directiva emite incluye el parámetro *token\-string*.  El parámetro `token-string` no está sujeto a la expansión de macro.  Esta directiva es más útil durante el preprocesamiento para notificar al desarrollador una incoherencia del programa o la infracción de una restricción.  En el ejemplo siguiente se muestra el procesamiento de errores durante el preprocesamiento:  
  
```  
#if !defined(__cplusplus)  
#error C++ compiler required.  
#endif  
```  
  
## Vea también  
 [Directivas de preprocesador](../preprocessor/preprocessor-directives.md)