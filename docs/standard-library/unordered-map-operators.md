---
title: Operadores de &lt;unordered_map&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
caps.latest.revision: 7
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: c78d1dda2a61a85bde238167b75eace09af598b6
ms.lasthandoff: 02/24/2017

---
# <a name="ltunorderedmapgt-operators"></a>Operadores de &lt;unordered_map&gt;
|||||  
|-|-|-|-|  
|[operator!=](#operator_neq)|[operator==](#operator_eq_eq)|[operator!=](#operator_neq_multimap)|[operator==](#operator_eq_eq_multimap)|  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a>  operator!=  
 Comprueba si el objeto [unordered_map](../standard-library/unordered-map-class.md) del lado izquierdo del operador no es igual que el objeto unordered_map del lado derecho.  
  
```
bool operator!=(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Objeto de tipo `unordered_map`.  
  
 `right`  
 Objeto de tipo `unordered_map`.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si los unordered_map no son iguales, `false` si son iguales.  
  
### <a name="remarks"></a>Comentarios  
 La comparación entre los objetos unordered_map no se ve afectada por el orden arbitrario en el que almacenan sus elementos. Dos unordered_map son iguales si tienen el mismo número de elementos y los elementos de un contenedor son una permutación de los elementos del otro contenedor. Si no se cumplen estas condiciones, significa que son distintas.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// unordered_map_op_ne.cpp  
// compile by using: cl.exe /EHsc /nologo /W4 /MTd   
#include <unordered_map>  
#include <iostream>  
#include <ios>  
  
int main( )  
{  
   using namespace std;  
   unordered_map<int, int> um1, um2, um3;  
  
   for ( int i = 0 ; i < 3 ; ++i ) {  
      um1.insert( make_pair( i+1, i ) );  
      um1.insert( make_pair( i, i ) );  
  
      um2.insert( make_pair( i, i+1 ) );  
      um2.insert( make_pair( i, i ) );  
  
      um3.insert( make_pair( i, i ) );  
      um3.insert( make_pair( i+1, i ) );  
   }  
  
   cout << boolalpha;  
   cout << "um1 != um2: " << (um1 != um2) << endl;   
   cout << "um1 != um3: " << (um1 != um3) << endl;   
   cout << "um2 != um3: " << (um2 != um3) << endl;   
}  
  
```  
  
 **Resultado:**  
  
 `um1 != um2: true`  
  
 `um1 != um3: false`  
  
 `um2 != um3: true`  
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a>  operator==  
 Comprueba si el objeto [unordered_map](../standard-library/unordered-map-class.md) del lado izquierdo del operador es igual que el objeto unordered_map del lado derecho.  
  
```
bool operator==(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Objeto de tipo `unordered_map`.  
  
 `right`  
 Objeto de tipo `unordered_map`.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si los unordered_map son iguales, `false` si no son iguales.  
  
### <a name="remarks"></a>Comentarios  
 La comparación entre los objetos unordered_map no se ve afectada por el orden arbitrario en el que almacenan sus elementos. Dos unordered_map son iguales si tienen el mismo número de elementos y los elementos de un contenedor son una permutación de los elementos del otro contenedor. Si no se cumplen estas condiciones, significa que son distintas.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// unordered_map_op_eq.cpp  
// compile by using: cl.exe /EHsc /nologo /W4 /MTd   
#include <unordered_map>  
#include <iostream>  
#include <ios>  
  
int main( )  
{  
   using namespace std;  
   unordered_map<int, int> um1, um2, um3;  
  
   for ( int i = 0 ; i < 3 ; ++i ) {  
      um1.insert( make_pair( i+1, i ) );  
      um1.insert( make_pair( i, i ) );  
  
      um2.insert( make_pair( i, i+1 ) );  
      um2.insert( make_pair( i, i ) );  
  
      um3.insert( make_pair( i, i ) );  
      um3.insert( make_pair( i+1, i ) );  
   }  
  
   cout << boolalpha;  
   cout << "um1 == um2: " << (um1 == um2) << endl;   
   cout << "um1 == um3: " << (um1 == um3) << endl;   
   cout << "um2 == um3: " << (um2 == um3) << endl;   
}  
  
```  
  
 **Resultado:**  
  
 `um1 == um2: false`  
  
 `um1 == um3: true`  
  
 `um2 == um3: false`  
  
##  <a name="a-nameoperatorneqmultimapa--operator"></a><a name="operator_neq_multimap"></a>  operator!=  
 Comprueba si el objeto [unordered_multimap](../standard-library/unordered-multimap-class.md) del lado izquierdo del operador no es igual que el objeto unordered_multimap del lado derecho.  
  
```
bool operator!=(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Objeto de tipo `unordered_multimap`.  
  
 `right`  
 Objeto de tipo `unordered_multimap`.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si los unordered_multimap no son iguales, `false` si son iguales.  
  
### <a name="remarks"></a>Comentarios  
 La comparación entre los objetos unordered_multimap no se ve afectada por el orden arbitrario en el que almacenan sus elementos. Dos unordered_multimap son iguales si tienen el mismo número de elementos y los elementos de un contenedor son una permutación de los elementos del otro contenedor. De lo contrario, no son iguales.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// unordered_multimap_op_ne.cpp  
// compile by using: cl.exe /EHsc /nologo /W4 /MTd   
#include <unordered_map>  
#include <iostream>  
#include <ios>  
  
int main( )  
{  
   using namespace std;  
   unordered_multimap<int, int> um1, um2, um3;  
  
   for ( int i = 0 ; i < 3 ; ++i ) {  
      um1.insert( make_pair( i, i ) );  
      um1.insert( make_pair( i, i ) );  
  
      um2.insert( make_pair( i, i ) );  
      um2.insert( make_pair( i, i ) );  
      um2.insert( make_pair( i, i ) );  
  
      um3.insert( make_pair( i, i ) );  
      um3.insert( make_pair( i, i ) );  
   }  
  
   cout << boolalpha;  
   cout << "um1 != um2: " << (um1 != um2) << endl;   
   cout << "um1 != um3: " << (um1 != um3) << endl;   
   cout << "um2 != um3: " << (um2 != um3) << endl;   
}  
  
```  
  
 **Resultado:**  
  
 `um1 != um2: true`  
  
 `um1 != um3: false`  
  
 `um2 != um3: true`  
  
##  <a name="a-nameoperatoreqeqmultimapa--operator"></a><a name="operator_eq_eq_multimap"></a>  operator==  
 Comprueba si el objeto [unordered_multimap](../standard-library/unordered-multimap-class.md) del lado izquierdo del operador es igual que el objeto unordered_multimap del lado derecho.  
  
```
bool operator==(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Objeto de tipo `unordered_multimap`.  
  
 `right`  
 Objeto de tipo `unordered_multimap`.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si los unordered_multimap son iguales, `false` si no son iguales.  
  
### <a name="remarks"></a>Comentarios  
 La comparación entre los objetos unordered_multimap no se ve afectada por el orden arbitrario en el que almacenan sus elementos. Dos unordered_multimap son iguales si tienen el mismo número de elementos y los elementos de un contenedor son una permutación de los elementos del otro contenedor. Si no se cumplen estas condiciones, significa que son distintas.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// unordered_multimap_op_eq.cpp  
// compile by using: cl.exe /EHsc /nologo /W4 /MTd  
#include <unordered_map>  
#include <iostream>  
#include <ios>  
  
int main( )  
{  
   using namespace std;  
   unordered_multimap<int, int> um1, um2, um3;  
  
   for ( int i = 0 ; i < 3 ; ++i ) {  
      um1.insert( make_pair( i, i ) );  
      um1.insert( make_pair( i, i ) );  
  
      um2.insert( make_pair( i, i ) );  
      um2.insert( make_pair( i, i ) );  
      um2.insert( make_pair( i, i ) );  
  
      um3.insert( make_pair( i, i ) );  
      um3.insert( make_pair( i, i ) );  
   }  
  
   cout << boolalpha;  
   cout << "um1 == um2: " << (um1 == um2) << endl;   
   cout << "um1 == um3: " << (um1 == um3) << endl;   
   cout << "um2 == um3: " << (um2 == um3) << endl;   
}  
  
```  
  
 **Resultado:**  
  
 `um1 == um2: false`  
  
 `um1 == um3: true`  
  
 `um2 == um3: false`  
  
## <a name="see-also"></a>Vea también  
 [<unordered_map>](../standard-library/unordered-map.md)




