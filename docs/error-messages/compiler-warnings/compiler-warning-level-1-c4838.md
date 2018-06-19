---
title: Compilador advertencia (nivel 1) C4838 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- C4838
dev_langs:
- C++
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1327ed8869c17701c6aa0a6ce2e3479b6109b8cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283850"
---
# <a name="compiler-warning-level-1-c4838"></a>Compilador advertencia (nivel 1) C4838
la conversión de 'type_1' a 'type_2' requiere una conversión de restricción  
  
 Se encontró una conversión de restricción implícita cuando se usa la inicialización de agregado o una lista.  
  
 Conversiones de restricción implícitas en las asignaciones y la inicialización permite que el lenguaje C y C++ sigue palo, aunque inesperado de la restricción es una causa de muchos errores de código. Para que el código sea más seguro, el estándar de C++ requiere un mensaje de diagnóstico cuando se produce una conversión de restricción en una lista de inicialización. En Visual C++, el diagnóstico es [C2397 de Error del compilador](../../error-messages/compiler-errors-1/compiler-error-c2397.md) cuando se usa la sintaxis de inicialización uniforme compatible a partir de Visual Studio 2015. El compilador genera la advertencia C4838 cuando se usa la lista o la sintaxis de inicialización de agregado compatibles con Visual Studio 2013.  
  
 Una conversión de restricción puede ser correcta cuando se sabe que el intervalo posible de los valores convertidos puede caber en el destino. En este caso, sabrá que más de lo que hace el compilador. Si realiza una conversión de restricción de forma intencionada, asegúrese de sus intenciones explícita utilizando una conversión de tipos estático. En caso contrario, este mensaje de advertencia casi siempre indica que hay un error en el código. Se puede corregir asegurándose de que los objetos que inicializa tienen tipos que son lo suficientemente grandes como para controlar las entradas.  
  
 El ejemplo siguiente genera C4838 y muestra una forma de corregirlo:  
  
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