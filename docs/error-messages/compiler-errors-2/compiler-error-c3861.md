---
title: "Error del compilador C3861 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3861"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3861"
ms.assetid: 0a1eee30-b3db-41b1-b1e5-35949c3924d7
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3861
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': no se encontró el identificador  
  
 El compilador no pudo resolver una referencia a un identificador, incluso con una búsqueda dependiente de argumentos.  
  
 Para corregir este error, compruebe el uso de mayúsculas y minúsculas y la ortografía en la declaración del identificador.  Compruebe que los [operadores de resolución de ámbito](../../cpp/scope-resolution-operator.md) y las [directivas using](../../misc/using-directive-cpp.md) del espacio de nombres se han usado correctamente.  Si el identificador se ha declarado en un archivo de encabezado, compruebe que el encabezado se haya incluido antes de la referencia.  Compruebe también que el identificador no haya sido excluido por las [directivas de compilación condicional](../../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3861:  
  
```  
// C3861.cpp  
void f2(){}  
int main() {  
   f();   // C3861  
   f2();   // OK  
}  
```  
  
## Ejemplo  
 Las clases de excepción de la biblioteca estándar de C\+\+ se encuentran ahora en el espacio de nombres de `std`.  
  
```  
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