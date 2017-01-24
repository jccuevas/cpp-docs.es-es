---
title: "Advertencia del compilador (niveles 1 y 4) C4112 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4112"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4112"
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (niveles 1 y 4) C4112
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#line requiere un entero entre 1 y number  
  
 La directiva [\#line](../../preprocessor/hash-line-directive-c-cpp.md) especifica un parámetro entero que está fuera del intervalo permitido.  
  
 Si el parámetro especificado es menor que 1, el contador de línea se restablece en 1. Si el parámetro especificado es mayor que *número*, que es el límite definido por el compilador, el contador de línea no se modifica. Esta es una advertencia de nivel 1 con la compatibilidad con ANSI \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) y una advertencia de nivel 4 con las extensiones de Microsoft \([\/Ze](../../build/reference/za-ze-disable-language-extensions.md)\).  
  
 El ejemplo siguiente genera la advertencia C4112:  
  
```  
// C4112.cpp  
// compile with: /W4  
#line 0   // C4112, value must be between 1 and number  
  
int main() {  
}  
```