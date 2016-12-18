---
title: "Referencias (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "declaraciones, referencias"
  - "objetos [C++], hacer referencia"
  - "referencias"
  - "referencias, declarar"
  - "referencias, a punteros"
  - "hacer referencia a objetos, sintaxis de declarador"
ms.assetid: 68156f7f-97a0-4b66-b26d-b25ade5e3bd8
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Referencias (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una referencia \(por ejemplo, un puntero\) almacena la dirección de un objeto que se encuentra en otra parte de la memoria.  A diferencia de un puntero, una referencia inicializada no puede hacer referencia a otro objeto ni establecerse en null.  Hay dos tipos de referencias: referencias lvalue, que hacen referencia a una variable con nombre y referencias rvalue, que hacen referencia a un [objeto temporal](../cpp/temporary-objects.md).  El operador & significa una referencia lvalue, mientras que el operador && significa una referencia rvalue o una referencia universal \(lvalue o rvalue\) según el contexto.  
  
 Las referencias se pueden declarar con la sintaxis siguiente:  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers   
[ms-modifier] declarator [= expression];  
```  
  
 Se puede usar cualquier declarador válido que especifique una referencia.  A menos que la referencia sea una referencia a un tipo de función o matriz, se aplica la siguiente sintaxis simplificada:  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers [& or &&]   
[cv-qualifiers] identifier [= expression];  
```  
  
 Las referencias se declaran mediante la siguiente secuencia:  
  
 1.  Los especificadores de la declaración:  
  
-   Un especificador de clase de almacenamiento opcional.  
  
-   Calificadores **const** y\/o `volatile` opcionales.  
  
-   El especificador de tipo: el nombre de un tipo.  
  
-   2.  El declarador:  
  
-   Un modificador opcional específico de Microsoft.  Para obtener más información, vea [Modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md).  
  
-   El operador & o el operador &&.  
  
-   Calificadores **const** y\/o `volatile` opcionales.  
  
-   El identificador.  
  
 3.  Un inicializador opcional.  
  
 Las formas de declarador más complejas para punteros a matrices y funciones también se aplican a las referencias a matrices y funciones. Vea [punteros](../cpp/pointers-cpp.md) y [declaradores](http://msdn.microsoft.com/es-es/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838).  
  
 Varios declaradores e inicializadores pueden aparecer en una lista separada por comas detrás de un único especificador de declaración.  Por ejemplo:  
  
```  
int &i;   
int &i, &j;   
```  
  
 Las referencias, punteros y objetos se pueden declarar juntos:  
  
```  
int &ref, *ptr, k;   
```  
  
 Una referencia contiene la dirección de un objeto, pero se comporta sintácticamente como un objeto.  
  
 Observe que, en el siguiente programa, el nombre del objeto `Today` y la referencia al objeto, `TodayRef`, se pueden usar de la misma forma:  
  
## Ejemplo  
  
```  
// references.cpp  
#include <stdio.h>  
struct S {  
   short i;  
};  
  
int main() {  
   S  s;   // Declare the object.  
   S& SRef = s;   // Declare the reference.  
   s.i = 3;  
  
   printf_s("%d\n", s.i);  
   printf_s("%d\n", SRef.i);  
  
   SRef.i = 4;  
   printf_s("%d\n", s.i);  
   printf_s("%d\n", SRef.i);  
}  
```  
  
  **3**  
**3**  
**4**  
**4**   
## Comentario  
 Temas de esta sección:  
  
-   [Argumentos de función de tipo de referencia](../cpp/reference-type-function-arguments.md)  
  
-   [Valores devueltos de función de tipo de referencia](../cpp/reference-type-function-returns.md)  
  
-   [Referencias a punteros](../cpp/references-to-pointers.md)  
  
## Vea también  
 [Inicializar referencias](../misc/initializing-references.md)