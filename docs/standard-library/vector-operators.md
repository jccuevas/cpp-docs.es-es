---
title: Operadores de &lt;vector&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d14f312-6f59-4ec7-88ae-95f89a558823
caps.latest.revision: 13
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 14308c0789851af423fd687f88acfe9177d89aff
ms.lasthandoff: 02/24/2017

---
# <a name="ltvectorgt-operators"></a>Operadores de &lt;vector&gt;
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|[operator&gt;=](#operator_gt__eq)|  
|[operator&lt;](#operator_lt_)|[operator&lt;=](#operator_lt__eq)|[operator==](#operator_eq_eq)|  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a>  operator!=  
 Comprueba si el objeto en el lado izquierdo del operador no es igual al objeto del lado derecho.  
  
```  
bool operator!=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` left`  
 Un objeto de tipo **vector**.  
  
 ` right`  
 Un objeto de tipo **vector**.  
  
### <a name="return-value"></a>Valor devuelto  
 **true** si los vectores no son iguales, **false** si los vectores son iguales.  
  
### <a name="remarks"></a>Comentarios  
 Dos vectores son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_op_ne.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
     v2.push_back( 2 );  
  
   if ( v1 != v2 )  
      cout << "Vectors not equal." << endl;  
   else  
      cout << "Vectors equal." << endl;  
}  
```  
  
```Output  
Vectors not equal.  
```  
  
##  <a name="a-nameoperatorlta--operatorlt"></a><a name="operator_lt_"></a>  operator&lt;  
 Comprueba si el objeto en el lado izquierdo del operador es menor que el objeto del lado derecho.  
  
```  
bool operator<(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` left`  
 Un objeto de tipo **vector**.  
  
 ` right`  
 Un objeto de tipo **vector**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es **true** si el vector del lado izquierdo del operador es menor que el vector del lado derecho del operador. De lo contrario, es **false**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_op_lt.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
   v1.push_back( 4 );  
  
   v2.push_back( 1 );  
   v2.push_back( 3 );  
  
   if ( v1 < v2 )  
      cout << "Vector v1 is less than vector v2." << endl;  
   else  
      cout << "Vector v1 is not less than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is less than vector v2.  
```  
  
##  <a name="a-nameoperatorlteqa--operatorlt"></a><a name="operator_lt__eq"></a>  operator&lt;=  
 Comprueba si el objeto en el lado izquierdo del operador es menor o igual que el objeto del lado derecho.  
  
```  
bool operator<=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` left`  
 Un objeto de tipo **vector**.  
  
 ` right`  
 Un objeto de tipo **vector**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es **true** si el vector del lado izquierdo del operador es menor o igual que el vector del lado derecho del operador. De lo contrario, es **false**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_op_le.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
   v1.push_back( 4 );  
  
   v2.push_back( 1 );  
   v2.push_back( 3 );  
  
   if ( v1 <= v2 )  
      cout << "Vector v1 is less than or equal to vector v2." << endl;  
   else  
      cout << "Vector v1 is greater than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is less than or equal to vector v2.  
```  
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a>  operator==  
 Comprueba si el objeto en el lado izquierdo del operador es igual al objeto del lado derecho.  
  
```  
bool operator==(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` left`  
 Un objeto de tipo **vector**.  
  
 ` right`  
 Un objeto de tipo **vector**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es **true** si el vector del lado izquierdo del operador es igual que el vector del lado derecho del operador. De lo contrario, es **false**.  
  
### <a name="remarks"></a>Comentarios  
 Dos vectores son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_op_eq.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v2.push_back( 1 );  
  
   if ( v1 == v2 )  
      cout << "Vectors equal." << endl;  
   else  
      cout << "Vectors not equal." << endl;  
}  
```  
  
```Output  
Vectors equal.  
```  
  
##  <a name="a-nameoperatorgta--operatorgt"></a><a name="operator_gt_"></a>  operator&gt;  
 Comprueba si el objeto en el lado izquierdo del operador es mayor que el objeto del lado derecho.  
  
```  
bool operator>(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` left`  
 Un objeto de tipo **vector**.  
  
 ` right`  
 Un objeto de tipo **vector**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es **true** si el vector del lado izquierdo del operador es mayor que el vector del lado derecho del operador. De lo contrario, es **false**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_op_gt.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 3 );  
   v1.push_back( 1 );  
  
   v2.push_back( 1 );  
   v2.push_back( 2 );  
   v2.push_back( 2 );  
  
   if ( v1 > v2 )  
      cout << "Vector v1 is greater than vector v2." << endl;  
   else  
      cout << "Vector v1 is not greater than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is greater than vector v2.  
```  
  
##  <a name="a-nameoperatorgteqa--operatorgt"></a><a name="operator_gt__eq"></a>  operator&gt;=  
 Comprueba si el objeto en el lado izquierdo del operador es mayor o igual que el objeto del lado derecho.  
  
```  
bool operator>=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` left`  
 Un objeto de tipo **vector**.  
  
 ` right`  
 Un objeto de tipo **vector**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es **true** si el vector del lado izquierdo del operador es mayor o igual que el vector del lado derecho del operador. De lo contrario, es **false**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// vector_op_ge.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 3 );  
   v1.push_back( 1 );  
  
     v2.push_back( 1 );  
   v2.push_back( 2 );  
   v2.push_back( 2 );  
  
   if ( v1 >= v2 )  
      cout << "Vector v1 is greater than or equal to vector v2." << endl;  
   else  
      cout << "Vector v1 is less than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is greater than or equal to vector v2.  
```  
  
## <a name="see-also"></a>Vea también  
 [\<vector>](../standard-library/vector.md)


