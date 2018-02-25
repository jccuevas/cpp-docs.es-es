---
title: Operadores de &lt;utility&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- utility/std::operator!=
- utility/std::operator&gt;
- utility/std::operator&gt;=
- utility/std::operator&lt;
- utility/std::operator&lt;=
- utility/std::operator==
dev_langs:
- C++
ms.assetid: a6617109-2cec-4a69-948f-6c87116eda5f
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::operator!= (utility)
- std::operator&gt; (utility)
- std::operator&gt;= (utility)
- std::operator&lt; (utility)
- std::operator&lt;= (utility)
- std::operator== (utility)
ms.openlocfilehash: 407e08934c4469776feb34d0f18b20b457d208d9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ltutilitygt-operators"></a>Operadores de &lt;utility&gt;
||||  
|-|-|-|  
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|  
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|  
  
##  <a name="op_neq"></a> operator!=  
 Comprueba si el objeto de par del lado izquierdo del operador no es igual que el objeto de par del lado derecho.  
  
```  
template <class Type>  
constexpr bool operator!=(const Type& left, const Type& right);

template <class T, class U>  
constexpr bool operator!=(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Un objeto de tipo **pair**.  
  
 `right`  
 Objeto de tipo `pair`.  
  
### <a name="return-value"></a>Valor devuelto  
 **true** si los pares no son iguales, **false** si los pares son iguales.  
  
### <a name="remarks"></a>Comentarios  
 Un par es igual a otro par si cada uno de sus respectivos elementos es igual. Dos pares no son iguales si el primer o el segundo elemento de uno de ellos no es igual al elemento correspondiente del otro par.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// utility_op_ne.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3;  
  
   p1 = make_pair ( 10, 1.11e-1 );  
   p2 = make_pair ( 1000, 1.11e-3 );  
   p3 = make_pair ( 10, 1.11e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl << endl;  
  
   if ( p1 != p2 )  
      cout << "The pairs p1 and p2 are not equal." << endl;  
   else  
      cout << "The pairs p1 and p2 are equal." << endl;  
  
   if ( p1 != p3 )  
      cout << "The pairs p1 and p3 are not equal." << endl;  
   else  
      cout << "The pairs p1 and p3 are equal." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.111 ).  
The pair p2 is: ( 1000, 0.00111 ).  
The pair p3 is: ( 10, 0.111 ).  
  
The pairs p1 and p2 are not equal.  
The pairs p1 and p3 are equal.  
```  
  
##  <a name="op_eq_eq"></a>  operator==  
 Comprueba si el objeto de par del lado izquierdo del operador es igual que el objeto de par del lado derecho.  
  
```  
template <class T, class U>  
constexpr bool operator==(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Un objeto de tipo **pair**.  
  
 `right`  
 Objeto de tipo `pair`.  
  
### <a name="return-value"></a>Valor devuelto  
 **true** si los pares son iguales, **false** si los `pair` no son iguales.  
  
### <a name="remarks"></a>Comentarios  
 Un par es igual a otro par si cada uno de sus respectivos elementos es igual. La función devuelve `left`. **first** == `right`. **first** && `left`. **second** == `right`. **second**. Dos pares no son iguales si el primer o el segundo elemento de uno de ellos no es igual al elemento correspondiente del otro par.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// utility_op_eq.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3;  
  
   p1 = make_pair ( 10, 1.11e-1 );  
   p2 = make_pair ( 1000, 1.11e-3 );  
   p3 = make_pair ( 10, 1.11e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl << endl;  
  
   if ( p1 == p2 )  
      cout << "The pairs p1 and p2 are equal." << endl;  
   else  
      cout << "The pairs p1 and p2 are not equal." << endl;  
  
   if ( p1 == p3 )  
      cout << "The pairs p1 and p3 are equal." << endl;  
   else  
      cout << "The pairs p1 and p3 are not equal." << endl;  
}  
```  
  
##  <a name="op_lt"></a> operator&lt;  
 Comprueba si el objeto de par del lado izquierdo del operador es menor que el objeto de par del lado derecho.  
  
```  
template <class T, class U>  
constexpr bool operator<(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Objeto de tipo `pair` en el lado izquierdo del operador.  
  
 `right`  
 Objeto de tipo `pair` en el lado derecho del operador.  
  
### <a name="return-value"></a>Valor devuelto  
 Es **true** si el `pair` del lado izquierdo del operador es estrictamente menor que el `pair` del lado derecho del operador. De lo contrario, es **false**.  
  
### <a name="remarks"></a>Comentarios  
 El `left` `pair` objeto se dice que es estrictamente menor que el `right` `pair` objeto si `left` es menor que y no es igual a `right`.  
  
 En una comparación de pares, los primeros elementos de los valores de los dos pares tienen la prioridad más alta. Si son diferentes, el resultado de la comparación se toma como resultado de la comparación del par. Si los valores de los primeros elementos no son diferentes, se comparan los valores de los elementos secundarios y se toma el resultado de la comparación como resultado de la comparación del par.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// utility_op_lt.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3;  
  
   p1 = make_pair ( 10, 2.22e-1 );  
   p2 = make_pair ( 100, 1.11e-1 );  
   p3 = make_pair ( 10, 1.11e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl << endl;  
  
   if ( p1 < p2 )  
      cout << "The pair p1 is less than the pair p2." << endl;  
   else  
      cout << "The pair p1 is not less than the pair p2." << endl;  
  
   if ( p1 < p3 )  
      cout << "The pair p1 is less than the pair p3." << endl;  
   else  
      cout << "The pair p1 is not less than the pair p3." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.222 ).  
The pair p2 is: ( 100, 0.111 ).  
The pair p3 is: ( 10, 0.111 ).  
  
The pair p1 is less than the pair p2.  
The pair p1 is not less than the pair p3.  
```  
  
##  <a name="op_lt_eq"></a> operator&lt;=  
 Comprueba si el objeto de par del lado izquierdo del operador es menor o igual que el objeto de par del lado derecho.  
  
```  
template <class Type>  
constexpr bool operator<=(const Type& left, const Type& right);

template <class T, class U>  
constexpr bool operator<=(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Objeto de tipo `pair` en el lado izquierdo del operador.  
  
 `right`  
 Objeto de tipo `pair` en el lado derecho del operador.  
  
### <a name="return-value"></a>Valor devuelto  
 Es **true** si el `pair` del lado izquierdo del operador es menor o igual que el `pair` del lado derecho del operador. De lo contrario, es **false**.  
  
### <a name="remarks"></a>Comentarios  
 En una comparación de pares, los primeros elementos de los valores de los dos pares tienen la prioridad más alta. Si son diferentes, el resultado de la comparación se toma como resultado de la comparación del par. Si los valores de los primeros elementos no son diferentes, se comparan los valores de los elementos secundarios y se toma el resultado de la comparación como resultado de la comparación del par.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// utility_op_le.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3, p4;  
  
   p1 = make_pair ( 10, 2.22e-1 );  
   p2 = make_pair ( 100, 1.11e-1 );  
   p3 = make_pair ( 10, 1.11e-1 );  
   p4 = make_pair ( 10, 2.22e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl;  
   cout << "The pair p4 is: ( " << p4.first << ", "   
        << p4.second << " )." << endl << endl;  
  
   if ( p1 <= p2 )  
      cout << "The pair p1 is less than or equal to the pair p2." << endl;  
   else  
      cout << "The pair p1 is greater than the pair p2." << endl;  
  
   if ( p1 <= p3 )  
      cout << "The pair p1 is less than or equal to the pair p3." << endl;  
   else  
      cout << "The pair p1 is greater than the pair p3." << endl;  
  
   if ( p1 <= p4 )  
      cout << "The pair p1 is less than or equal to the pair p4." << endl;  
   else  
      cout << "The pair p1 is greater than the pair p4." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.222 ).  
The pair p2 is: ( 100, 0.111 ).  
The pair p3 is: ( 10, 0.111 ).  
The pair p4 is: ( 10, 0.222 ).  
  
The pair p1 is less than or equal to the pair p2.  
The pair p1 is greater than the pair p3.  
The pair p1 is less than or equal to the pair p4.  
```  
  
##  <a name="op_gt"></a> operator&gt;  
 Comprueba si el objeto de par del lado izquierdo del operador es mayor que el objeto de par del lado derecho.  
  
```  
template <class Type>  
constexpr bool operator>(const Type& left, const Type& right);

template <class T, class U>  
constexpr bool operator>(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Objeto de tipo `pair` en el lado izquierdo del operador.  
  
 `right`  
 Objeto de tipo `pair` en el lado derecho del operador.  
  
### <a name="return-value"></a>Valor devuelto  
 Es **true** si el `pair` del lado izquierdo del operador es estrictamente mayor que el `pair` del lado derecho del operador. De lo contrario, es **false**.  
  
### <a name="remarks"></a>Comentarios  
 El `left` `pair` objeto se dice que es estrictamente mayor que el `right` `pair` objeto si `left` es mayor que y no es igual a `right`.  
  
 En una comparación de pares, los primeros elementos de los valores de los dos pares tienen la prioridad más alta. Si son diferentes, el resultado de la comparación se toma como resultado de la comparación del par. Si los valores de los primeros elementos no son diferentes, se comparan los valores de los elementos secundarios y se toma el resultado de la comparación como resultado de la comparación del par.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// utility_op_gt.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3, p4;  
  
   p1 = make_pair ( 10, 2.22e-1 );  
   p2 = make_pair ( 100, 1.11e-1 );  
   p3 = make_pair ( 10, 1.11e-1 );  
   p4 = make_pair ( 10, 2.22e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl;  
   cout << "The pair p4 is: ( " << p4.first << ", "   
        << p4.second << " )." << endl << endl;  
  
   if ( p1 > p2 )  
      cout << "The pair p1 is greater than the pair p2." << endl;  
   else  
      cout << "The pair p1 is not greater than the pair p2." << endl;  
  
   if ( p1 > p3 )  
      cout << "The pair p1 is greater than the pair p3." << endl;  
   else  
      cout << "The pair p1 is not greater than the pair p3." << endl;  
  
   if ( p1 > p4 )  
      cout << "The pair p1 is greater than the pair p4." << endl;  
   else  
      cout << "The pair p1 is not greater than the pair p4." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.222 ).  
The pair p2 is: ( 100, 0.111 ).  
The pair p3 is: ( 10, 0.111 ).  
The pair p4 is: ( 10, 0.222 ).  
  
The pair p1 is not greater than the pair p2.  
The pair p1 is greater than the pair p3.  
The pair p1 is not greater than the pair p4.  
```  
  
##  <a name="op_gt_eq"></a> operator&gt;=  
 Comprueba si el objeto de par del lado izquierdo del operador es mayor o igual que el objeto de par del lado derecho.  
  
```  
template <class Type>  
constexpr bool operator>=(const Type& left, const Type& right);

template <class T, class U>  
constexpr bool operator>=(const pair<T, U>& left, const pair<T, U>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Objeto de tipo `pair` en el lado izquierdo del operador.  
  
 `right`  
 Objeto de tipo `pair` en el lado derecho del operador.  
  
### <a name="return-value"></a>Valor devuelto  
 **true** si el `pair` del lado izquierdo del operador es mayor o igual que el `pair` del lado derecho del operador. De lo contrario es **false**.  
  
### <a name="remarks"></a>Comentarios  
 En una comparación de pares, los primeros elementos de los valores de los dos pares tienen la prioridad más alta. Si son diferentes, el resultado de la comparación se toma como resultado de la comparación del par. Si los valores de los primeros elementos no son diferentes, se comparan los valores de los elementos secundarios y se toma el resultado de la comparación como resultado de la comparación del par.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// utility_op_ge.cpp  
// compile with: /EHsc  
#include <utility>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   pair <int, double> p1, p2, p3, p4;  
  
   p1 = make_pair ( 10, 2.22e-1 );  
   p2 = make_pair ( 100, 1.11e-1 );  
   p3 = make_pair ( 10, 1.11e-1 );  
   p4 = make_pair ( 10, 2.22e-1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl;  
   cout << "The pair p4 is: ( " << p4.first << ", "   
        << p4.second << " )." << endl << endl;  
  
   if ( p1 >= p2 )  
      cout << "Pair p1 is greater than or equal to pair p2." << endl;  
   else  
      cout << "The pair p1 is less than the pair p2." << endl;  
  
   if ( p1 >= p3 )  
      cout << "Pair p1 is greater than or equal to pair p3." << endl;  
   else  
      cout << "The pair p1 is less than the pair p3." << endl;  
  
   if ( p1 >= p4 )  
      cout << "Pair p1 is greater than or equal to pair p4." << endl;  
   else  
      cout << "The pair p1 is less than the pair p4." << endl;  
}  
```  
  
```Output  
The pair p1 is: ( 10, 0.222 ).  
The pair p2 is: ( 100, 0.111 ).  
The pair p3 is: ( 10, 0.111 ).  
The pair p4 is: ( 10, 0.222 ).  
  
The pair p1 is less than the pair p2.  
Pair p1 is greater than or equal to pair p3.  
Pair p1 is greater than or equal to pair p4.  
```  
  
## <a name="see-also"></a>Vea también  
 [\<utility>](../standard-library/utility.md)

