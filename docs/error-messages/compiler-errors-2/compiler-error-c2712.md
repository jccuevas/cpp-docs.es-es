---
title: Error del compilador C2712 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2712
dev_langs: C++
helpviewer_keywords: C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ee098890bac40c0c376c7623578c4e95e551a75b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2712"></a>Error del compilador C2712
No se puede usar __try en funciones que requieran desenredo de objetos  
  
 Error C2712 puede producirse si usa [/EHsc](../../build/reference/eh-exception-handling-model.md), y una función con control de excepciones estructurado también tiene objetos que requieran desenredo (destrucción).  
  
 Soluciones posibles:  
  
-   Mueva el código que requiere SEH a otra función  
  
-   Vuelva a escribir las funciones que usan SEH para evitar el uso de variables locales y parámetros que tengan destructores. No usar SEH en constructores o destructores  
  
-   Compilar sin /EHsc  
  
 También puede producirse el error C2712 si llama a un método que se declara mediante la [__event](../../cpp/event.md) palabra clave. Dado que el evento podría utilizarse en un entorno multiproceso, el compilador genera código que impide la manipulación del objeto de evento subyacente y, a continuación, agrega el código generado en una SEH [try-finally (instrucción)](../../cpp/try-finally-statement.md). Por lo tanto, el error C2712 se producirá si llama al método de evento y pasa por valor un argumento cuyo tipo tiene un destructor. En este caso, una solución es pasar el argumento como referencia constante.  
  
## <a name="example"></a>Ejemplo  
 C2712 puede producirse también si se compila con **/CLR: pure** y declara una matriz estática de punteros a funciones en un `__try` bloque. Un miembro estático exige al compilador que use la inicialización dinámica en **/CLR: pure**, lo cual implica el control de excepciones de C++. Sin embargo, el control de excepciones de C++ no se permite en un bloque `__try`.  
  
 Las opciones del compilador **/clr:pure** y **/clr:safe** están en desuso en Visual Studio 2015.  
  
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