---
title: C2397 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2397
dev_langs:
- C++
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 31f2b548fd13bc7702d44ef4a6d5dc5c34a5eb3c
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2397"></a>C2397 de Error del compilador
conversión de 'type_1' a 'type_2' requiere una conversión de restricción  
  
 Se encontró una conversión de restricción implícita cuando se usa la inicialización uniforme.  
  
 Conversiones de restricción implícitas en las asignaciones y la inicialización permite que el lenguaje C y C++ sigue palo, aunque inesperado de la restricción es una causa de muchos errores de código. Para mejorar la seguridad de código, el estándar de C++ requiere un mensaje de diagnóstico cuando se produce una conversión de restricción en una lista de inicialización. En Visual C++, el diagnóstico es C2397 de Error del compilador cuando se usa el principio de la sintaxis compatible de inicialización uniforme en Visual Studio 2015. El compilador genera [C4838 de advertencia del compilador (nivel 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md) al usar la lista o la sintaxis de inicialización de agregado admitidas por Visual Studio 2013.  
  
 Una conversión de restricción puede ser aceptable cuando se sabe que puede satisfacer el intervalo posible de los valores convertidos en el destino. En este caso, sabrá que más de lo que hace el compilador. Si realiza una conversión de restricción intencionadamente, hacer que sus intenciones explícita utilizando una conversión de tipos estático. De lo contrario, este mensaje de error casi siempre indica que tiene un error en el código. Para solucionarlo, puede asegurarse de que los objetos que se inicialice con tipos que son lo suficientemente grandes como para controlar las entradas.  
  
 En el ejemplo siguiente genera C2397 y muestra una manera de corregir:  
  
```  
// C2397.cpp -- C++ narrowing conversion diagnostics  
// Compile by using: cl /EHsc C2397.cpp  
#include <vector>   
  
struct S1 {  
    int m1;  
    double m2, m3;  
};  
  
void function_C2397(double d1) {  
    char c1 { 127 };          // OK  
    char c2 { 513 };          // error C2397  
  
    std::vector<S1> vS1;  
    vS1.push_back({ d1, 2, 3 }); // error C2397  
  
    // Possible fix if you know d1 always fits in an int  
    vS1.push_back({ static_cast<int>(d1), 2, 3 });   
}  
```
