---
title: "Error del compilador C2712 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2712"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2712"
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# Error del compilador C2712
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No se puede usar \_\_try en funciones que requieran desenredo de objetos  
  
 El error C2712 puede producirse si se usa [\/EHsc](../../build/reference/eh-exception-handling-model.md) y una función con control de excepciones estructurado también tiene objetos que requieran desenredo \(destrucción\).  
  
 Soluciones posibles:  
  
-   Mueva el código que requiere SEH a otra función  
  
-   Vuelva a escribir las funciones que usan SEH para evitar el uso de variables locales y parámetros que tengan destructores.  No usar SEH en constructores o destructores  
  
-   Compilar sin \/EHsc  
  
 El error C2712 también se puede producir si llama a un método que se declara mediante la palabra clave [\_\_event](../../cpp/event.md).  Dado que el evento podría utilizarse en un entorno con subprocesamiento múltiple, el compilador genera código que impide la manipulación del objeto de evento subyacente y luego agrega el código generado en una SEH [try\-finally \(instrucción\)](../../cpp/try-finally-statement.md).  Por lo tanto, el error C2712 se producirá si llama al método de evento y pasa por valor un argumento cuyo tipo tiene un destructor.  En este caso, una solución es pasar el argumento como referencia constante.  
  
## Ejemplo  
 El error C2712 también se puede producir si se compila con **\/clr:pure** y declara una matriz estática de punteros a funciones en un bloque `__try`.  Un miembro estático exige al compilador que use la inicialización dinámica en **\/clr:pure**, que implica el control de excepciones de C\+\+.  Sin embargo, el control de excepciones de C\+\+ no se permite en un bloque `__try`.  
  
 En el ejemplo siguiente se genera el error C2712 y se muestra cómo corregirlo:  
  
```  
// C2712.cpp  
// compile with: /clr:pure /c  
struct S1 {  
   static int smf();  
   void fnc();  
};  
  
void S1::fnc() {  
   __try {  
      static int (*array_1[])() = {smf,};   // C2712  
  
      // OK  
      static int (*array_2[2])();  
      array_2[0] = smf;  
    }  
    __except(0) {}  
}  
```