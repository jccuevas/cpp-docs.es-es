---
title: Compilador advertencia (nivel 1) C4838 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4838
dev_langs:
- C++
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 227af1840fe5aee63545e35456fe09749f00de1d
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4838"></a>Compilador advertencia (nivel 1) C4838
conversión de 'type_1' a 'type_2' requiere una conversión de restricción  
  
 Se encontró una conversión de restricción implícita cuando se usa la inicialización de agregado o lista.  
  
 Conversiones de restricción implícitas en las asignaciones y la inicialización permite que el lenguaje C y C++ sigue palo, aunque inesperado de la restricción es una causa de muchos errores de código. Para mejorar la seguridad de código, el estándar de C++ requiere un mensaje de diagnóstico cuando se produce una conversión de restricción en una lista de inicialización. En Visual C++, el diagnóstico es [C2397 de Error del compilador](../../error-messages/compiler-errors-1/compiler-error-c2397.md) cuando se utiliza la sintaxis de inicialización uniforme compatible a partir de Visual Studio 2015. El compilador genera la advertencia C4838 al utilizar la lista o la sintaxis de inicialización de agregado admitidas por Visual Studio 2013.  
  
 Una conversión de restricción puede ser aceptable cuando se sabe que puede satisfacer el intervalo posible de los valores convertidos en el destino. En este caso, sabrá que más de lo que hace el compilador. Si realiza una conversión de restricción intencionadamente, hacer que sus intenciones explícita utilizando una conversión de tipos estático. De lo contrario, este mensaje de advertencia casi siempre indica que hay un error en el código. Para solucionarlo, puede asegurarse de que los objetos que se inicialice con tipos que son lo suficientemente grandes como para controlar las entradas.  
  
 En el ejemplo siguiente genera C4838 y muestra una manera de corregir:  
  
```  
// C4838.cpp -- C++ narrowing conversion diagnostics  
// Compile by using: cl /EHsc C4838.cpp  
  
struct S1 {  
    int m1;  
    double m2, m3;  
};  
  
void function_C4838(double d1) {  
    double ad[] = { 1, d1 }; // OK  
    int ai[] = { 1, d1 };    // warning C4838  
    S1 s11 = { 1, 2, d1 };   // OK  
    S1 s12 { d1, 2, 3 };     // warning C4838  
    S1 s13 { static_cast<int>(d1), 2, 3 }; // possible fix for C4838  
}  
```
