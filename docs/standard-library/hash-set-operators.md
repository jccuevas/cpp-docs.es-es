---
title: Operadores de &lt;hash_set&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- hash_set/std::operator!=
- hash_set/std::operator==
dev_langs: C++
ms.assetid: 403d8e4e-0b3f-43fb-bc5a-8100c4f331c5
caps.latest.revision: "13"
manager: ghogen
ms.openlocfilehash: e5205240d4f0bbfbf41423ee73a737e7d2bd0667
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="lthashsetgt-operators"></a>Operadores de &lt;hash_set&gt;
||||  
|-|-|-|  
|[operator!=](#op_neq)|[operator!= (hash_multiset)](#op_neq_hash_multiset)|[operator==](#op_eq_eq)|  
|[operator== (hash_multiset)](#op_eq_eq_hash_multiset)|  
  
##  <a name="op_neq"></a>  operator!=  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).  
  
 Comprueba si el objeto hash_set del lado izquierdo del operador no es igual que el objeto hash_set del lado derecho.  
  
```  
bool operator!=(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Objeto de tipo `hash_set`.  
  
 `right`  
 Objeto de tipo `hash_set`.  
  
### <a name="return-value"></a>Valor devuelto  
 **true** si los objetos hash_set no son iguales; **false** si los objetos hash_set son iguales.  
  
### <a name="remarks"></a>Comentarios  
 La comparación entre los objetos hash_set se basa en una comparación en pares de sus elementos. Dos objetos hash_set son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.  
  
 Los miembros de la [< hash_map >](../standard-library/hash-map.md) y [< hash_set >](../standard-library/hash-set.md) archivos de encabezado que se encuentran en el [stdext Namespace](../standard-library/stdext-namespace.md).
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_set_op_ne.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> hs1, hs2, hs3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      hs1.insert ( i );  
      hs2.insert ( i * i );  
      hs3.insert ( i );  
   }  
  
   if ( hs1 != hs2 )  
      cout << "The hash_sets hs1 and hs2 are not equal." << endl;  
   else  
      cout << "The hash_sets hs1 and hs2 are equal." << endl;  
  
   if ( hs1 != hs3 )  
      cout << "The hash_sets hs1 and hs3 are not equal." << endl;  
   else  
      cout << "The hash_sets hs1 and hs3 are equal." << endl;  
}  
```  
  
```Output  
The hash_sets hs1 and hs2 are not equal.  
The hash_sets hs1 and hs3 are equal.  
```  
  
##  <a name="op_eq_eq"></a>  operator==  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).  
  
 Comprueba si el objeto hash_set del lado izquierdo del operador es igual que el objeto hash_set del lado derecho.  
  
```  
bool operator!==(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Objeto de tipo `hash_set`.  
  
 `right`  
 Objeto de tipo `hash_set`.  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el objeto hash_set del lado izquierdo del operador es igual que el objeto hash_set del lado derecho del operador. En caso contrario, **False**.  
  
### <a name="remarks"></a>Comentarios  
 La comparación entre los objetos hash_set se basa en una comparación en pares de sus elementos. Dos objetos hash_set son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.  
  
   
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_set_op_eq.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_set <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i );  
   }  
  
   if ( s1 == s2 )  
      cout << "The hash_sets s1 and s2 are equal." << endl;  
   else  
      cout << "The hash_sets s1 and s2 are not equal." << endl;  
  
   if ( s1 == s3 )  
      cout << "The hash_sets s1 and s3 are equal." << endl;  
   else  
      cout << "The hash_sets s1 and s3 are not equal." << endl;  
}  
```  
  
```Output  
The hash_sets s1 and s2 are not equal.  
The hash_sets s1 and s3 are equal.  
```  
  
##  <a name="neq_hash_multiset"></a>  operator!= (hash_multiset)  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).  
  
 Comprueba si el objeto hash_multiset del lado izquierdo del operador no es igual que el objeto hash_multiset del lado derecho.  
  
```  
bool operator!=(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Objeto de tipo `hash_multiset`.  
  
 `right`  
 Objeto de tipo `hash_multiset`.  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si los objetos hash_multiset no son iguales; **False** si los objetos hash_multiset son iguales.  
  
### <a name="remarks"></a>Comentarios  
 La comparación entre los objetos hash_multiset se basa en una comparación en pares de sus elementos. Dos objetos hash_multiset son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.  
  
   
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hashset_op_ne.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> hs1, hs2, hs3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      hs1.insert ( i );  
      hs2.insert ( i * i );  
      hs3.insert ( i );  
   }  
  
   if ( hs1 != hs2 )  
      cout << "The hash_multisets hs1 and hs2 are not equal." << endl;  
   else  
      cout << "The hash_multisets hs1 and hs2 are equal." << endl;  
  
   if ( hs1 != hs3 )  
      cout << "The hash_multisets hs1 and hs3 are not equal." << endl;  
   else  
      cout << "The hash_multisets hs1 and hs3 are equal." << endl;  
}  
```  
  
```Output  
The hash_multisets hs1 and hs2 are not equal.  
The hash_multisets hs1 and hs3 are equal.  
```  
  
##  <a name="eq_eq_hash_multiset"></a>  operator== (hash_multiset)  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).  
  
 Comprueba si el objeto hash_multiset del lado izquierdo del operador es igual que el objeto hash_multiset del lado derecho.  
  
```  
bool operator!==(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Objeto de tipo `hash_multiset`.  
  
 `right`  
 Objeto de tipo `hash_multiset`.  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el objeto hash_multiset del lado izquierdo del operador es igual que el objeto hash_multiset del lado derecho del operador. En caso contrario, **False**.  
  
### <a name="remarks"></a>Comentarios  
 La comparación entre los objetos hash_multiset se basa en una comparación en pares de sus elementos. Dos objetos hash_multiset son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_multiset_op_eq.cpp  
// compile with: /EHsc  
#include <hash_set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_multiset <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i );  
   }  
  
   if ( s1 == s2 )  
      cout << "The hash_multisets s1 and s2 are equal." << endl;  
   else  
      cout << "The hash_multisets s1 and s2 are not equal." << endl;  
  
   if ( s1 == s3 )  
      cout << "The hash_multisets s1 and s2 are equal." << endl;  
   else  
      cout << "The hash_multisets s1 and s2 are not equal." << endl;  
}  
```  
  
```Output  
The hash_multisets s1 and s2 are not equal.  
The hash_multisets s1 and s2 are equal.  
```  
  
## <a name="see-also"></a>Vea también  
 [<hash_set>](../standard-library/hash-set.md)

