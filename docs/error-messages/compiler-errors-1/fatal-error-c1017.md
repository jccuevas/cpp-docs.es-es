---
title: "Error irrecuperable C1017 | Microsoft Docs"
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
  - "C1017"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1017"
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1017
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

expresión constante de tipo entero no válida  
  
 Una directiva `#if` carece de expresión o ésta no ha sido evaluada como constante.  
  
 Si una directiva `#if`, `#elif`, o `#else` utiliza constantes definidas mediante `#define`, éstas deberán tener valores que se evalúen como constante entera.  
  
 El código siguiente genera el error C1017:  
  
```  
// C1017.cpp  
#define CONSTANT_NAME "YES"  
#if CONSTANT_NAME   // C1017  
#endif  
```  
  
 Posible solución:  
  
```  
// C1017b.cpp  
// compile with: /c  
#define CONSTANT_NAME 1  
#if CONSTANT_NAME  
#endif  
```  
  
 Debido a que `CONSTANT_NAME` se evalúa como cadena en vez de como número entero, la directiva `#if` generará el error irrecuperable C1017.  
  
 En otros casos, el preprocesador evalúa como cero las constantes no definidas.  Esto puede dar lugar a resultados imprevistos, como se muestra en el ejemplo siguiente.  `YES` no se ha definido, por lo que se evalúa como cero.  La expresión `#if` `CONSTANT_NAME` se evalúa como false y el preprocesador quita el código que se iba a usar en `YES`.  `NO` tampoco se ha definido \(cero\), de modo que `#elif` `CONSTANT_NAME==NO` se evalúa como true \(`0 == 0`\), lo que hace que el preprocesador mantenga el código de la parte `#elif` de la instrucción, justo lo contrario al comportamiento esperado.  
  
```  
// C1017c.cpp  
// compile with: /c  
#define CONSTANT_NAME YES  
#if CONSTANT_NAME  
   // Code to use on YES...  
#elif CONSTANT_NAME==NO  
   // Code to use on NO...  
#endif  
```  
  
 Para ver exactamente cómo controla el compilador las directivas de preprocesador, utilice [\/P](../../build/reference/p-preprocess-to-a-file.md), [\/E](../../build/reference/e-preprocess-to-stdout.md) o [\/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md).