---
title: hash (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- functional/std::hash
- bitset/std::hash
- memory/std::hash
- string/std::hash
- system_error/std::hash
- thread/std::hash
- typeindex/std::hash
- vector/std::hash
- XSTDDEF/std::hash
- xstring/std::hash
dev_langs: C++
helpviewer_keywords:
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
ms.assetid: e1b500c6-a5c8-4f6f-ad33-7ec52eb8e2e4
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3224ea06ecb74021d9e0971910a4ce974fa56b0a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="hash-class"></a>hash (Clase)
Calcula el código hash para un valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Ty>  
struct hash {  
    size_t operator()(Ty val) const; 
};  
```  
  
## <a name="remarks"></a>Comentarios  
El objeto de función define una función hash adecuada para asignar valores de tipo *Ty* a una distribución de valores de índice. El miembro `operator()` devuelve un código hash para *val*, adecuado para su uso con las clases de plantilla `unordered_map`, `unordered_multimap`, `unordered_set` y `unordered_multiset`. La biblioteca estándar proporciona especializaciones de tipos básicos: *Ty* puede ser cualquier tipo escalar, incluidos los tipos de puntero y los tipos de enumeración. Además, hay especializaciones para los tipos de biblioteca `string`, `wstring`, `u16string`, `u32string`, `string_view`, `wstring_view`, `u16string_view`, `u32string_view`, `bitset`, `error_code`, `error_condition`, `optional`, `shared_ptr`, `thread`, `type_index`, `unique_ptr`, `variant` y `vector<bool>`.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// std__functional__hash.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
#include <unordered_set>   
  
int main()   
    {   
    std::unordered_set<int, std::hash<int> > c0;   
    c0.insert(3);   
    std::cout << *c0.find(3) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
3  
```  
  
## <a name="requirements"></a>Requisitos  
**Encabezado:** \<functional>  
  
**Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<unordered_map>](../standard-library/unordered-map.md)   
 [unordered_multimap (Clase)](../standard-library/unordered-multimap-class.md)   
 [unordered_multiset (Clase)](../standard-library/unordered-multiset-class.md)   
 [<unordered_set>](../standard-library/unordered-set.md)

