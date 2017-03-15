---
title: "Advertencia del compilador (nivel 3) C4373 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4373"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4373"
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 3) C4373
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'%$S': la función virtual invalida '%$pS'; las versiones anteriores del compilador no se reemplazaron cuando los parámetros solo se diferenciaban en los calificadores const y volatile  
  
 La aplicación contiene un método en una clase derivada que reemplaza un método virtual en una clase base, y los parámetros en el método de reemplazo difieren solo en un calificador [const](../../cpp/const-cpp.md) o [volatile](../../cpp/volatile-cpp.md) de los parámetros del método virtual. Esto significa que el compilador debe enlazar una referencia a función con el método en la clase derivada o base.  
  
 Las versiones del compilador anteriores a [!INCLUDE[cpp_orcas_long](../../cpp/includes/cpp_orcas_long_md.md)] enlazan la función con el método de la clase base y luego emiten un mensaje de advertencia. Las versiones posteriores del compilador omiten el calificador `const` o `volatile`, enlazan la función con el método de la clase derivada y después emiten la advertencia `C4373`. Este último comportamiento cumple con el estándar de C\+\+.  
  
## Ejemplo  
 El siguiente código de ejemplo genera la advertencia C4373.  
  
```  
// c4373.cpp // compile with: /c /W3 #include <stdio.h> struct Base { virtual void f(int i) { printf("base\n"); } }; struct Derived : Base { void f(const int i) {  // C4373 printf("derived\n"); } }; void main() { Derived d; Base* p = &d; p->f(1); }  
```  
  
```Output  
derivadas  
```