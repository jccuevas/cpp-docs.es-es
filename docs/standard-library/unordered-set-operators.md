---
title: Operadores de &lt;unordered_set&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: []
ms.assetid: 8653eea6-12f2-4dd7-aa2f-db38a71599a0
caps.latest.revision: 7
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: da5fe91f5306080ce10c72d8cc1908b6952135c3
ms.lasthandoff: 02/24/2017

---
# <a name="ltunorderedsetgt-operators"></a>Operadores de &lt;unordered_set&gt;
|||||  
|-|-|-|-|  
|[operator!=](#operator_neq)|[operator==](#operator_eq_eq)|[operator!=](#operator_neq_unordered_multiset)|[operator==](#operator_eq_eq_unordered_multiset)|  
  
##  <a name="operator_neq"></a>  operator!=  
 Comprueba si el objeto [unordered_set](../standard-library/unordered-set-class.md) del lado izquierdo del operador no es igual que el objeto unordered_set del lado derecho.  
  
```
bool operator!=(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Objeto de tipo `unordered_set`.  
  
 `right`  
 Objeto de tipo `unordered_set`.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si los unordered_set no son iguales, `false` si son iguales.  
  
### <a name="remarks"></a>Comentarios  
 La comparación entre los objetos unordered_set no se ve afectada por el orden arbitrario en el que almacenan sus elementos. Dos unordered_set son iguales si tienen el mismo número de elementos y los elementos de un contenedor son una permutación de los elementos del otro contenedor. Si no se cumplen estas condiciones, significa que son distintas.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// unordered_set_ne.cpp   
// compile by using: cl.exe /EHsc /nologo /W4 /MTd   
#include <unordered_set>   
#include <iostream>   
#include <ios>  
  
int main()   
{   
    using namespace std;  
  
    unordered_set<char> c1, c2, c3;  
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
    c2.insert('c');   
    c2.insert('a');   
    c2.insert('d');   
  
    c3.insert('c');   
    c3.insert('a');   
    c3.insert('b');   
  
   cout << boolalpha;  
   cout << "c1 != c2: " << (c1 != c2) << endl;   
   cout << "c1 != c3: " << (c1 != c3) << endl;   
   cout << "c2 != c3: " << (c2 != c3) << endl;   
  
    return (0);   
}  
  
```  
  
 **Resultado:**  
  
 `c1 != c2: true`  
  
 `c1 != c3: false`  
  
 `c2 != c3: true`  
  
##  <a name="operator_eq_eq"></a>  operator==  
 Comprueba si el objeto [unordered_set](../standard-library/unordered-set-class.md) del lado izquierdo del operador es igual que el objeto unordered_set del lado derecho.  
  
```
bool operator==(const unordered_set <Key, Hash, Pred, Allocator>& left, const unordered_set <Key, Hash, Pred, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Objeto de tipo `unordered_set`.  
  
 `right`  
 Objeto de tipo `unordered_set`.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si los unordered_set son iguales, `false` si no son iguales.  
  
### <a name="remarks"></a>Comentarios  
 La comparación entre los objetos unordered_set no se ve afectada por el orden arbitrario en el que almacenan sus elementos. Dos unordered_set son iguales si tienen el mismo número de elementos y los elementos de un contenedor son una permutación de los elementos del otro contenedor. Si no se cumplen estas condiciones, significa que son distintas.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// unordered_set_eq.cpp   
// compile by using: cl.exe /EHsc /nologo /W4 /MTd   
#include <unordered_set>   
#include <iostream>   
#include <ios>  
  
int main()   
{   
    using namespace std;  
  
    unordered_set<char> c1, c2, c3;  
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
  
    c2.insert('c');   
    c2.insert('a');   
    c2.insert('d');   
  
    c3.insert('c');   
    c3.insert('a');   
    c3.insert('b');   
  
   cout << boolalpha;  
   cout << "c1 == c2: " << (c1 == c2) << endl;   
   cout << "c1 == c3: " << (c1 == c3) << endl;   
   cout << "c2 == c3: " << (c2 == c3) << endl;   
  
    return (0);   
}  
  
```  
  
 **Resultado:**  
  
 `c1 == c2: false`  
  
 `c1 == c3: true`  
  
 `c2 == c3: false`  
  
##  <a name="operator_neq_unordered_multiset"></a>  operator!=  
 Comprueba si el objeto [unordered_multiset](../standard-library/unordered-multiset-class.md) del lado izquierdo del operador no es igual que el objeto unordered_multiset del lado derecho.  
  
```
bool operator!=(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Objeto de tipo `unordered_multiset`.  
  
 `right`  
 Objeto de tipo `unordered_multiset`.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si los unordered_multiset no son iguales, `false` si son iguales.  
  
### <a name="remarks"></a>Comentarios  
 La comparación entre los objetos unordered_multiset no se ve afectada por el orden arbitrario en el que almacenan sus elementos. Dos unordered_multiset son iguales si tienen el mismo número de elementos y los elementos de un contenedor son una permutación de los elementos del otro contenedor. Si no se cumplen estas condiciones, significa que son distintas.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// unordered_multiset_ne.cpp   
// compile by using: cl.exe /EHsc /nologo /W4 /MTd   
#include <unordered_set>   
#include <iostream>   
#include <ios>  
  
int main()   
{   
    using namespace std;  
  
    unordered_multiset<char> c1, c2, c3;  
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
    c1.insert('c');   
  
    c2.insert('c');   
    c2.insert('c');   
    c2.insert('a');   
    c2.insert('d');   
  
    c3.insert('c');   
    c3.insert('c');   
    c3.insert('a');   
    c3.insert('b');   
  
   cout << boolalpha;  
   cout << "c1 != c2: " << (c1 != c2) << endl;   
   cout << "c1 != c3: " << (c1 != c3) << endl;   
   cout << "c2 != c3: " << (c2 != c3) << endl;   
  
    return (0);   
}  
  
```  
  
 **Resultado:**  
  
 `c1 != c2: true`  
  
 `c1 != c3: false`  
  
 `c2 != c3: true`  
  
##  <a name="operator_eq_eq_unordered_multiset"></a>  operator==  
 Comprueba si el objeto [unordered_multiset](../standard-library/unordered-multiset-class.md) del lado izquierdo del operador es igual que el objeto unordered_multiset del lado derecho.  
  
```
bool operator==(const unordered_multiset <Key, Hash, Pred, Allocator>& left, const unordered_multiset <Key, Hash, Pred, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Objeto de tipo `unordered_multiset`.  
  
 `right`  
 Objeto de tipo `unordered_multiset`.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si los unordered_multiset son iguales, `false` si no son iguales.  
  
### <a name="remarks"></a>Comentarios  
 La comparación entre los objetos unordered_multiset no se ve afectada por el orden arbitrario en el que almacenan sus elementos. Dos unordered_multiset son iguales si tienen el mismo número de elementos y los elementos de un contenedor son una permutación de los elementos del otro contenedor. Si no se cumplen estas condiciones, significa que son distintas.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// unordered_multiset_eq.cpp   
// compile by using: cl.exe /EHsc /nologo /W4 /MTd   
#include <unordered_set>   
#include <iostream>   
#include <ios>  
  
int main()   
{   
    using namespace std;  
  
    unordered_multiset<char> c1, c2, c3;  
  
    c1.insert('a');   
    c1.insert('b');   
    c1.insert('c');   
    c1.insert('c');   
  
    c2.insert('c');   
    c2.insert('c');   
    c2.insert('a');   
    c2.insert('d');   
  
    c3.insert('c');   
    c3.insert('c');   
    c3.insert('a');   
    c3.insert('b');   
  
   cout << boolalpha;  
   cout << "c1 == c2: " << (c1 == c2) << endl;   
   cout << "c1 == c3: " << (c1 == c3) << endl;   
   cout << "c2 == c3: " << (c2 == c3) << endl;   
  
    return (0);   
}  
  
```  
  
 **Resultado:**  
  
 `c1 == c2: false`  
  
 `c1 == c3: true`  
  
 `c2 == c3: false`  
  
## <a name="see-also"></a>Vea también  
 [<unordered_set>](../standard-library/unordered-set.md)




