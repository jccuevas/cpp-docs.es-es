---
title: Compilador Error C2712 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2712
dev_langs:
- C++
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 89b7d0ad3c7e175db1525c2f3fb8407240ce943c
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2712"></a>Compilador Error C2712
No se puede usar __try en funciones que requieran desenredo de objetos  
  
 Error C2712 puede aparecer si utiliza [/EHsc](../../build/reference/eh-exception-handling-model.md), y una función con control de excepciones estructurado también tiene objetos que requieran descarga (destrucción).  
  
 Soluciones posibles:  
  
-   Mueva el código que requiere SEH a otra función  
  
-   Vuelva a escribir las funciones que usan SEH para evitar el uso de variables locales y parámetros que tengan destructores. No usar SEH en constructores o destructores  
  
-   Compilar sin /EHsc  
  
 También puede producirse el error C2712 si llama a un método que se declara utilizando la [__event](../../cpp/event.md) (palabra clave). Dado que el evento se puede usar en un entorno multiproceso, el compilador genera código que impide la manipulación del objeto de evento subyacente y, a continuación, agrega el código generado en un SEH [instrucción try-finally](../../cpp/try-finally-statement.md). Por lo tanto, el error C2712 se producirá si llama al método de evento y pasa por valor un argumento cuyo tipo tiene un destructor. En este caso, una solución es pasar el argumento como referencia constante.  
  
## <a name="example"></a>Ejemplo  
 C2712 también puede producirse si se compila con **/CLR: pure** y declara una matriz estática de punteros a funciones en un `__try` bloque. Un miembro estático exige al compilador que utilice la inicialización dinámica en **/CLR: pure**, que implica el control de excepciones de C++. Sin embargo, el control de excepciones de C++ no se permite en un bloque `__try`.  
  
 El **/CLR: pure** y **/CLR: safe** opciones del compilador están desusadas en Visual Studio 2015.  
  
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
