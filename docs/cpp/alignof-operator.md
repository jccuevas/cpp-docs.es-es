---
title: "__alignof (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__alignof"
  - "alignof"
  - "alignas"
  - "__alignof_cpp"
  - "alignof_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__alignof (palabra clave) [C++]"
  - "alignas"
  - "alineación de estructuras"
  - "alignof"
  - "tipos [C++], requisitos de alineación"
ms.assetid: acb1eed7-6398-40bd-b0c5-684ceb64afbc
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# __alignof (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+11 incluye por primera vez el operador `alignof`, que devuelve la alineación del tipo especificado en bytes.  Para la máxima portabilidad, use el operador alignof en lugar del operador \_\_alignof específico de Microsoft.  
  
 **Específicos de Microsoft**  
  
 Devuelve un valor de tipo **size\_t**, que es el requisito de alineación del tipo.  
  
## Sintaxis  
  
```  
  
        __alignof(   
   type    
)  
```  
  
## Comentarios  
 Por ejemplo:  
  
|Expresión|Valor|  
|---------------|-----------|  
|**\_\_alignof\( char \)**|1|  
|**\_\_alignof\( short \)**|2|  
|**\_\_alignof\( int \)**|4|  
|**\_\_alignof\( \_\_int64 \)**|8|  
|**\_\_alignof\( float \)**|4|  
|**\_\_alignof\( double \)**|8|  
|**\_\_alignof\( char\* \)**|4|  
  
 El valor de `__alignof` es igual que el valor de `sizeof` para los tipos básicos.  Considere, no obstante, este ejemplo:  
  
```  
typedef struct { int a; double b; } S;  
// __alignof(S) == 8  
```  
  
 En este caso, el valor de `__alignof` es el requisito de alineación del elemento más grande de la estructura.  
  
 De igual forma, para  
  
```  
typedef __declspec(align(32)) struct { int a; } S;  
```  
  
 `__alignof(S)` es igual a `32`.  
  
 Un uso para `__alignof` sería como parámetro para una de sus propias rutinas de asignación de memoria.  Por ejemplo, dada la siguiente estructura definida `S`, podría llamar a una rutina de asignación de memoria denominada `aligned_malloc` para asignar memoria en un límite de alineación determinado.  
  
```  
typedef __declspec(align(32)) struct { int a; double b; } S;  
int n = 50; // array size  
S* p = (S*)aligned_malloc(n * sizeof(S), __alignof(S));  
```  
  
 Para obtener más información sobre la modificación de la alineación, vea:  
  
-   [pack](../preprocessor/pack.md)  
  
-   [align](../cpp/align-cpp.md)  
  
-   [\_\_unaligned](../cpp/unaligned.md)  
  
-   [\/Zp \(Alineación de miembros de estructura\)](../build/reference/zp-struct-member-alignment.md)  
  
-   [Ejemplos de alineación de estructuras](../build/examples-of-structure-alignment.md) \(específico de x64\)  
  
 Para obtener más información sobre las diferencias de la alineación en código para x86 y x64, vea:  
  
-   [Conflictos con el compilador de x86](../build/conflicts-with-the-x86-compiler.md)  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)