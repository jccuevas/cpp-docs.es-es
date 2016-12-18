---
title: "Advertencia del compilador (nivel 4) C4837 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4837"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4837"
ms.assetid: 9a3c7b6b-ffe4-443d-96af-43deb80d85b4
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4837
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se detectó un trígrafo: '??%c' reemplazado por '%c'  
  
 El trígrafo indicado se reemplaza con el carácter indicado.  
  
 El compilador convierte los trígrafos antes de completar cualquier otro procesamiento.  Utilice la secuencia de escape de carácter, `\?`, para evitar la interpretación incorrecta de una secuencia de caracteres que se parece a un trígrafo.  Para obtener más información acerca de los trígrafos, vea [Trígrafos](../../c-language/trigraphs.md).  Para obtener más información acerca de las secuencias de escape, vea [Secuencias de escape](../../c-language/escape-sequences.md).  
  
 C4837 está desactivada de manera predeterminada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
### Para corregir este error  
  
1.  Utilice la secuencia de escape de carácter, `\?`, en lugar de uno de los caracteres '?' en el código fuente.  
  
## Vea también  
 [Trígrafos](../../c-language/trigraphs.md)   
 [Secuencias de escape](../../c-language/escape-sequences.md)   
 [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md)