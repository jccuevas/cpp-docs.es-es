---
title: __alignof (operador) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- alignas_cpp
- __alignof_cpp
- alignof_cpp
dev_langs:
- C++
helpviewer_keywords:
- alignas
- alignment of structures
- __alignof keyword [C++]
- alignof
- types [C++], alignment requirements
ms.assetid: acb1eed7-6398-40bd-b0c5-684ceb64afbc
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 66ec7ff196a4f22aec043d8b76faf0189e05cd0f
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="alignof-operator"></a>__alignof (Operador)
C++11 incluye por primera vez el operador `alignof`, que devuelve la alineación del tipo especificado en bytes. Para la máxima portabilidad, use el operador alignof en lugar del operador __alignof específico de Microsoft.  
  
 **Específicos de Microsoft**  
  
 Devuelve un valor de tipo **size_t** que es el requisito de alineación del tipo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      __alignof(   
   type    
)  
```  
  
## <a name="remarks"></a>Comentarios  
 Por ejemplo:  
  
|Expresión|Valor|  
|----------------|-----------|  
|**__alignof (char)**|1|  
|**__alignof (corto)**|2|  
|**__alignof (int)**|4|  
|**__alignof ( \__int64)**|8|  
|**__alignof (float)**|4|  
|**__alignof (double)**|8|  
|**__alignof (char\* )**|4|  
  
 El valor de `__alignof` es igual que el valor de `sizeof` para los tipos básicos. Considere, no obstante, este ejemplo:  
  
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
  
 Un uso para `__alignof` sería como parámetro para una de sus propias rutinas de asignación de memoria. Por ejemplo, dada la siguiente estructura definida `S`, podría llamar a una rutina de asignación de memoria denominada `aligned_malloc` para asignar memoria en un límite de alineación determinado.  
  
```  
typedef __declspec(align(32)) struct { int a; double b; } S;  
int n = 50; // array size  
S* p = (S*)aligned_malloc(n * sizeof(S), __alignof(S));  
```  
  
 Para obtener más información sobre la modificación de la alineación, vea:  
  
-   [pack](../preprocessor/pack.md)  
  
-   [align](../cpp/align-cpp.md)  
  
-   [__unaligned](../cpp/unaligned.md)  
  
-   [/Zp (alineación de miembros de estructura)](../build/reference/zp-struct-member-alignment.md)  
  
-   [Ejemplos de alineación de estructuras](../build/examples-of-structure-alignment.md) (x64 específico)  
  
 Para obtener más información sobre las diferencias de la alineación en código para x86 y x64, vea:  
  
-   [Conflictos con el compilador de x86](../build/conflicts-with-the-x86-compiler.md)  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)   
 [Palabras clave](../cpp/keywords-cpp.md)
