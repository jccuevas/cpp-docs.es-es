---
title: Compilador (nivel 4) de la advertencia C4463 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4463
dev_langs:
- C++
helpviewer_keywords:
- C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c13e0a79c667ecedbf3fd065338892d3af9c2ee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294445"
---
# <a name="compiler-warning-level-4-c4463"></a>Compilador (nivel 4) de la advertencia C4463  
  
> desbordamiento; asignar *valor* al campo de bits que solo puede contener valores de *low_value* a *high_value*  
  
Asignado *valor* está fuera del intervalo de valores que puede contener el campo de bits. Tipos de campo de bits con signo usan el orden de alta bit para el inicio de sesión, por lo que si *n* es el tamaño de un campo de bits, el intervalo de campos de bits con signo es -2<sup>n-1</sup> a 2<sup>n-1</sup>-1, mientras que sin signo campos de bits tienen un intervalo de 0 a 2<sup>n</sup>-1.  
  
## <a name="example"></a>Ejemplo  
  
Este ejemplo genera C4463 porque intenta asignar un valor de 3 a un campo de bits de tipo `int` con un tamaño de 2, que tiene un intervalo comprendido entre -2 y 1.  
  
Para corregir este problema, puede cambiar el valor asignado a algo en el intervalo permitido. Si el campo de bits está destinado a contener valores sin signo en el intervalo de 0 a 3, puede cambiar el tipo de declaración para `unsigned`. Si el campo está diseñado para almacenar los valores en el intervalo -4 a 3, puede cambiar el tamaño de un campo de bits a 3.  
  
```cpp  
// C4463_overflow.cpp
// compile with: cl /W4 /EHsc C4463_overflow.cpp
struct S { 
    int x : 2; // int type treats high-order bit as sign
}; 

int main() { 
    S s; 
    s.x = 3; // warning C4463: overflow; assigning 3 
    // to bit-field that can only hold values from -2 to 1 
    // To fix, change assigned value to fit in range,
    // increase size of bitfield, and/or change base type 
    // to unsigned.
} 
```  
