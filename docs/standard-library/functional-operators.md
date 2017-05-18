---
title: '&lt;functional&gt; (Operadores) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- functional/std::operator!=
- functional/std::operator==
dev_langs:
- C++
helpviewer_keywords:
- functional operators
ms.assetid: d4b3c760-f3e2-4b65-bdaa-d42e8dd6f5e1
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: f38d129aab8703b6077b2848d7b71bb0a07e0ea7
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="ltfunctionalgt-operators"></a>&lt;functional&gt; (Operadores)
|||  
|-|-|  
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|  
  
##  <a name="op_eq_eq"></a>  operator==  
 Comprueba si el objeto al que se puede llamar está vacío.  
  
```  
template <class Fty>  
bool operator==(const function<Fty>& f, null_ptr_type npc);

template <class Fty>  
bool operator==(null_ptr_type npc, const function<Fty>& f);
```  
  
### <a name="parameters"></a>Parámetros  
 `Fty`  
 Tipo de función que se va a contener.  
  
 `f`  
 Objeto de función  
  
 `npc`  
 Un puntero nulo.  
  
### <a name="remarks"></a>Comentarios  
 Los dos operadores toman un argumento que es una referencia a un objeto `function` y un argumento que es una constante de puntero nulo. Ambos devuelven true únicamente si el objeto `function` está vacío.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__functional__operator_eq.cpp
// compile with: /EHsc   
#include <functional>   
#include <iostream>   

int neg(int val)
{
    return (-val);
}

int main()
{
    std::function<int(int)> fn0;
    std::cout << std::boolalpha << "empty == "
        << (fn0 == 0) << std::endl;

    std::function<int(int)> fn1(neg);
    std::cout << std::boolalpha << "empty == "
        << (fn1 == 0) << std::endl;

    return (0);
}
  
```  
  
```Output  
empty == true  
empty == false  
```  
  
##  <a name="op_neq"></a>  operator!=  
 Comprueba si el objeto al que se puede llamar no está vacío.  
  
```  
template <class Fty>  
bool operator!=(const function<Fty>& f, null_ptr_type npc);

template <class Fty>  
bool operator!=(null_ptr_type npc, const function<Fty>& f);
```  
  
### <a name="parameters"></a>Parámetros  
 `Fty`  
 Tipo de función que se va a contener.  
  
 `f`  
 Objeto de función  
  
 `npc`  
 Un puntero nulo.  
  
### <a name="remarks"></a>Comentarios  
 Los dos operadores toman un argumento que es una referencia a un objeto `function` y un argumento que es una constante de puntero nulo. Ambos devuelven True solo si el objeto `function` no está vacío.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__functional__operator_ne.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val)   
    {   
    return (-val);   
    }   
  
int main()   
    {   
    std::function<int (int)> fn0;   
    std::cout << std::boolalpha << "not empty == "   
        << (fn0 != 0) << std::endl;   
  
    std::function<int (int)> fn1(neg);   
    std::cout << std::boolalpha << "not empty == "   
        << (fn1 != 0) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
not empty == false  
not empty == true  
```  
  
## <a name="see-also"></a>Vea también  
 [\<functional>](../standard-library/functional.md)


