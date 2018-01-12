---
title: Compilador (niveles 2 y 4) de la advertencia C4200 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4200
dev_langs: C++
helpviewer_keywords: C4200
ms.assetid: e44d6073-937f-42b7-acc1-65e802b475c6
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f160476deb2ab3e4ad0ff00100305c934dfb14c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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