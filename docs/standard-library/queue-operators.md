---
title: Operadores &lt;queue&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c435b48-175c-45b0-88eb-24561044019c
caps.latest.revision: 13
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 3160c7fb3965bc05ceace5722a9c502e60f89442
ms.lasthandoff: 02/24/2017

---
# <a name="ltqueuegt-operators"></a>Operadores &lt;queue&gt;
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|[operator&gt;=](#operator_gt__eq)|  
|[operator&lt;](#operator_lt_)|[operator&lt;=](#operator_lt__eq)|[operator==](#operator_eq_eq)|  
  
##  <a name="operator_neq"></a> operator!=  
 Comprueba si el objeto queue en el lado izquierdo del operador no es igual al objeto queue del lado derecho.  
  
```  
bool operator!=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Un objeto de tipo **queue**.  
  
 `right`  
 Un objeto de tipo **queue**.  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si las colas no son iguales; **False** si lo son.  
  
### <a name="remarks"></a>Comentarios  
 La comparación entre los objetos queue se basa en una comparación en pares de sus elementos. Dos colas son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// queue_op_ne.cpp  
// compile with: /EHsc  
#include <queue>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares queues with list base containers  
   queue <int, list<int> > q1, q2, q3;  
  
   // The following line would have caused an error because vector   
   // does not support pop_front( ) and so cannot be adapted  
   // by queue as a base container  
   // queue <int, vector<int> > q1, q2, q3;  
  
   q1.push( 1 );  
   q2.push( 1 );  
   q2.push( 2 );  
   q3.push( 1 );  
  
   if ( q1 != q2 )  
      cout << "The queues q1 and q2 are not equal." << endl;  
   else  
      cout << "The queues q1 and q2 are equal." << endl;  
  
   if ( q1 != q3 )  
      cout << "The queues q1 and q3 are not equal." << endl;  
   else  
      cout << "The queues q1 and q3 are equal." << endl;  
}  
```  
  
```Output  
The queues q1 and q2 are not equal.  
The queues q1 and q3 are equal.  
```  
  
##  <a name="operator_lt_"></a> operator&lt;  
 Comprueba si el objeto queue en el lado izquierdo del operador es inferior al objeto queue del lado derecho.  
  
```  
bool operator<(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Un objeto de tipo **queue**.  
  
 `right`  
 Un objeto de tipo **queue**.  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si la cola del lado izquierdo del operador es menor y no igual que la cola del lado derecho del operador. Si no es así, **False**.  
  
### <a name="remarks"></a>Comentarios  
 La comparación entre los objetos queue se basa en una comparación en pares de sus elementos. La relación de menor que entre dos objetos queue se basa en una comparación del primer par de elementos diferentes.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// queue_op_lt.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares queues with default deque base container  
   queue <int> q1, q2, q3;  
  
   q1.push( 1 );  
   q1.push( 2 );  
   q2.push( 5 );  
   q2.push( 10 );  
   q3.push( 1 );  
   q3.push( 2 );  
  
   if ( q1 < q2 )  
      cout << "The queue q1 is less than the queue q2." << endl;  
   else  
      cout << "The queue q1 is not less than the queue q2." << endl;  
  
   if ( q1 < q3 )  
      cout << "The queue q1 is less than the queue q3." << endl;  
   else  
      cout << "The queue q1 is not less than the queue q3." << endl;  
}  
```  
  
```Output  
The queue q1 is less than the queue q2.  
The queue q1 is not less than the queue q3.  
```  
  
##  <a name="operator_lt__eq"></a> operator&lt;=  
 Comprueba si el objeto queue en el lado izquierdo del operador es inferior a o igual que el objeto queue del lado derecho.  
  
```  
bool operator<=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Un objeto de tipo **queue**.  
  
 `right`  
 Un objeto de tipo **queue**.  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si la cola del lado izquierdo del operador es estrictamente menor que la cola del lado derecho del operador. En caso contrario, es **False**.  
  
### <a name="remarks"></a>Comentarios  
 La comparación entre los objetos queue se basa en una comparación en pares de sus elementos. La relación de menor o igual entre dos objetos queue se basa en una comparación del primer par de elementos diferentes.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// queue_op_le.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   queue <int> q1, q2, q3;  
  
   q1.push( 5 );  
   q1.push( 10 );  
   q2.push( 1 );  
   q2.push( 2 );  
   q3.push( 5 );  
   q3.push( 10 );  
  
   if ( q1 <= q2 )  
      cout << "The queue q1 is less than or equal to "  
           << "the queue q2." << endl;  
   else  
      cout << "The queue q1 is greater than "  
           << "the queue q2." << endl;  
  
   if ( q1 <= q3 )  
      cout << "The queue q1 is less than or equal to "  
           << "the queue q3." << endl;  
   else  
      cout << "The queue q1 is greater than "  
           << "the queue q3." << endl;  
}  
```  
  
```Output  
The queue q1 is greater than the queue q2.  
The queue q1 is less than or equal to the queue q3.  
```  
  
##  <a name="operator_eq_eq"></a> operator==  
 Comprueba si el objeto queue en el lado izquierdo del operador es igual al objeto queue del lado derecho.  
  
```  
bool operator==(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Un objeto de tipo **queue**.  
  
 `right`  
 Un objeto de tipo **queue**.  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si las colas no son iguales; **False** si lo son.  
  
### <a name="remarks"></a>Comentarios  
 La comparación entre los objetos queue se basa en una comparación en pares de sus elementos. Dos colas son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// queue_op_eq.cpp  
// compile with: /EHsc  
#include <queue>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Declares queues with list base containers  
   queue <int, list<int> > q1, q2, q3;  
  
   // The following line would have caused an error because vector   
   // does not support pop_front( ) and so cannot be adapted  
   // by queue as a base container  
   // queue <int, vector<int> > q1, q2, q3;  
  
   q1.push( 1 );  
   q2.push( 2 );  
   q3.push( 1 );  
  
   if ( q1 != q2 )  
      cout << "The queues q1 and q2 are not equal." << endl;  
   else  
      cout << "The queues q1 and q2 are equal." << endl;  
  
   if ( q1 != q3 )  
      cout << "The queues q1 and q3 are not equal." << endl;  
   else  
      cout << "The queues q1 and q3 are equal." << endl;  
}  
```  
  
```Output  
The queues q1 and q2 are not equal.  
The queues q1 and q3 are equal.  
```  
  
##  <a name="operator_gt_"></a> operator&gt;  
 Comprueba si el objeto queue en el lado izquierdo del operador es mayor que el objeto queue del lado derecho.  
  
```  
bool operator>(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Un objeto de tipo **queue**.  
  
 `right`  
 Un objeto de tipo **queue**.  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si la cola del lado izquierdo del operador es estrictamente menor que la cola del lado derecho del operador. En caso contrario, es **False**.  
  
### <a name="remarks"></a>Comentarios  
 La comparación entre los objetos queue se basa en una comparación en pares de sus elementos. La relación de mayor que entre dos objetos queue se basa en una comparación del primer par de elementos diferentes.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// queue_op_gt.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   queue <int> q1, q2, q3;  
  
   q1.push( 1 );  
   q1.push( 2 );  
   q1.push( 3 );  
   q2.push( 5 );  
   q2.push( 10 );  
   q3.push( 1 );  
   q3.push( 2 );  
  
   if ( q1 > q2 )  
      cout << "The queue q1 is greater than "  
           << "the queue q2." << endl;  
   else  
      cout << "The queue q1 is not greater than "  
           << "the queue q2." << endl;  
  
   if ( q1> q3 )  
      cout << "The queue q1 is greater than "  
           << "the queue q3." << endl;  
   else  
      cout << "The queue q1 is not greater than "  
           << "the queue q3." << endl;  
}  
```  
  
```Output  
The queue q1 is not greater than the queue q2.  
The queue q1 is greater than the queue q3.  
```  
  
##  <a name="operator_gt__eq"></a> operator&gt;=  
 Comprueba si el objeto queue en el lado izquierdo del operador es mayor que o igual al objeto queue del lado derecho.  
  
```  
bool operator>=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Un objeto de tipo **queue**.  
  
 `right`  
 Un objeto de tipo **queue**.  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si la cola del lado izquierdo del operador es estrictamente menor que la cola del lado derecho del operador. En caso contrario, es **False**.  
  
### <a name="remarks"></a>Comentarios  
 La comparación entre los objetos queue se basa en una comparación en pares de sus elementos. Dos colas son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// queue_op_ge.cpp  
// compile with: /EHsc  
#include <queue>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   queue <int> q1, q2, q3;  
  
   q1.push( 1 );  
   q1.push( 2 );  
   q2.push( 5 );  
   q2.push( 10 );  
   q3.push( 1 );  
   q3.push( 2 );  
  
   if ( q1 >= q2 )  
      cout << "The queue q1 is greater than or equal to "  
           << "the queue q2." << endl;  
   else  
      cout << "The queue q1 is less than "  
           << "the queue q2." << endl;  
  
   if ( q1>= q3 )  
      cout << "The queue q1 is greater than or equal to "  
           << "the queue q3." << endl;  
   else  
      cout << "The queue q1 is less than "  
           << "the queue q3." << endl;  
}  
```  
  
```Output  
The queue q1 is less than the queue q2.  
The queue q1 is greater than or equal to the queue q3.  
```  
  
## <a name="see-also"></a>Vea también  
 [\<queue>](../standard-library/queue.md)


