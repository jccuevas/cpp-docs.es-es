---
title: Operadores de &lt;unordered_map&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- unordered_map/std::operator!=
- unordered_map/std::operator==
dev_langs:
- C++
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: d5ee8994367332e6e26d70e166bd0549d16fc965
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ltunorderedmapgt-operators"></a>Operadores de &lt;unordered_map&gt;
|||||  
|-|-|-|-|  
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|[operator!=](#op_neq_multimap)|[operator==](#op_eq_eq_multimap)|  
  
##  <a name="op_neq"></a> operator!=  
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
  
 **Salida:**  
  
 `um1 != um2: true`  
  
 `um1 != um3: false`  
  
 `um2 != um3: true`  
  
##  <a name="op_eq_eq"></a>  operator==  
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
  
##  <a name="op_neq_multimap"></a> operator!=  
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
  
 **Salida:**  
  
 `um1 != um2: true`  
  
 `um1 != um3: false`  
  
 `um2 != um3: true`  
  
##  <a name="op_eq_eq_multimap"></a>  operator==  
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
  
 **Salida:**  
  
 `um1 == um2: false`  
  
 `um1 == um3: true`  
  
 `um2 == um3: false`  
  
## <a name="see-also"></a>Vea también  
 [<unordered_map>](../standard-library/unordered-map.md)



