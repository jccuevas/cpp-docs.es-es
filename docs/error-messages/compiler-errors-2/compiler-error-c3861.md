---
title: Compilador Error C3861 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3861
dev_langs:
- C++
helpviewer_keywords:
- C3861
ms.assetid: 0a1eee30-b3db-41b1-b1e5-35949c3924d7
caps.latest.revision: 10
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
ms.sourcegitcommit: 65e7a7bd56096fbeec61b651ab494d82edef9c90
ms.openlocfilehash: 177890dcd3ff2abf07f5d9e282efd4a9fd7121a7
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3861"></a>Error del compilador C3861
'identifier': no se encontró el identificador  
  
El compilador no pudo resolver una referencia a un identificador, incluso con una búsqueda dependiente de argumentos.  
  
Para corregir este error, compruebe el uso de mayúsculas y minúsculas y la ortografía en la declaración del identificador. Compruebe que [operadores de resolución de ámbito](../../cpp/scope-resolution-operator.md) y espacio de nombres [directivas using](../../cpp/namespaces-cpp.md#using_directives) se usan correctamente. Si el identificador se ha declarado en un archivo de encabezado, compruebe que el encabezado se haya incluido antes de la referencia. Compruebe también que el identificador no es excluido por [directivas de compilación condicional](../../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).  
  
## <a name="example"></a>Ejemplo  
El ejemplo siguiente genera el error C3861:  
  
```cpp  
// C3861.cpp  
void f2(){}  
int main() {  
   f();   // C3861  
   f2();   // OK  
}  
```  
  
## <a name="example"></a>Ejemplo  
Las clases de excepción de la biblioteca estándar de C++ se encuentran ahora en el espacio de nombres de `std`.  
  
```cpp  
// C3861_b.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   try {  
      throw exception("Exception");   // C3861  
      // try the following line instead  
      // throw std::exception("Exception");  
   }  
   catch (...) {  
      std::cout << "caught an exception" << std::endl;  
   }  
}  
```
