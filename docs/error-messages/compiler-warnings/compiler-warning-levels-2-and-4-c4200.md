---
title: Compilador (niveles 2 y 4) de la advertencia C4200 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4200
dev_langs:
- C++
helpviewer_keywords:
- C4200
ms.assetid: e44d6073-937f-42b7-acc1-65e802b475c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ffc789c3c4da5caf50f0657e17ddabe40a5773c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294955"
---
# <a name="compiler-warning-levels-2-and-4-c4200"></a>Advertencia del compilador (niveles 2 y 4) C4200
se ha utilizado una extensión no estándar: matriz de tamaño cero en struct/union  
  
 Indica que una estructura o unión contiene una matriz de tamaño cero.  
  
 La declaración de una matriz de tamaño cero es una extensión de Microsoft. Esto genera una advertencia de nivel 2 al compilar un archivo de C++ y una advertencia de nivel 4 al compilar un archivo de C. La compilación de C++ también genera esta advertencia: "No se puede generar el constructor de copias o el operador de asignación de copias cuando el tipo definido por el usuario contiene una matriz de tamaño cero". Este ejemplo genera la advertencia C4200:  
  
```cpp  
// C4200.cpp  
// compile by using: cl /W4 c4200.cpp  
struct A {  
    int a[0];  // C4200  
};  
int main() {  
}  
```  
  
 Esta extensión no estándar se utiliza a menudo para conectar el código con las estructuras de datos externos que tienen una longitud variable. Si esta situación se aplica a su código, puede deshabilitar la advertencia:  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// C4200b.cpp  
// compile by using: cl /W4 c4200a.cpp  
#pragma warning(disable : 4200)  
struct A {  
    int a[0];  
};  
int main() {  
}  
```