---
title: checked_array_iterator (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- iterator/checked_array_iterator
- checked_array_iterator
- iterator/stdext::checked_array_iterator::difference_type
- iterator/stdext::checked_array_iterator::pointer
- iterator/stdext::checked_array_iterator::reference
- iterator/stdext::checked_array_iterator::base
dev_langs:
- C++
helpviewer_keywords:
- checked_array_iterator, syntax
- checked_array_iterator class
- checked_array_iterator
ms.assetid: 7f07185e-d588-4ae3-9c4f-84ec4aa25a28
caps.latest.revision: 28
author: corob-msft
ms.author: corob
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 8494fc5f7f184505bf71712d41ac290f876c1311
ms.lasthandoff: 02/24/2017

---
# <a name="checkedarrayiterator-class"></a>checked_array_iterator (Clase)
La clase `checked_array_iterator` permite transformar una matriz o un puntero en un iterador comprobado. Use esta clase como contenedor (mediante la función [make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator)) para matrices o punteros sin formato como una manera dirigida de comprobar y administrar advertencias de puntero no comprobadas en lugar de silenciar de manera global estas advertencias. Si es necesario, puede usar la versión no comprobada de esta clase, [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md).  
  
> [!NOTE]
>  Esta clase es una extensión de Microsoft de la biblioteca estándar de C++. El código implementado mediante esta función no es portable a los entornos de compilación estándar de C++ que no admiten esta extensión de Microsoft. Para obtener un ejemplo en el que se muestra cómo escribir código que no requiere el uso de esta clase, vea el segundo ejemplo siguiente.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class _Iterator>  
class checked_array_iterator;
```  
  
## <a name="remarks"></a>Comentarios  
 Esta clase se define en el espacio de nombres [stdext](../standard-library/stdext-namespace.md).  
  
 Para obtener más información y código de ejemplo sobre la característica de iterador comprobado, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo definir y utilizar un iterador de matrices comprobado.  
  
 Si el destino no es suficientemente grande para contener todos los elementos que se van a copiar, como ocurriría si cambió la línea:  
  
```cpp  
copy(a, a + 5, checked_array_iterator<int*>(b, 5));
```  
  
 hasta  
  
```cpp  
copy(a, a + 5, checked_array_iterator<int*>(b, 4));
```  
  
 Se producirá un error en tiempo de ejecución.  
  
```cpp  
// compile with: /EHsc /W4 /MTd  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
using namespace stdext;  
  
int main() {  
   int a[]={0, 1, 2, 3, 4};  
   int b[5];  
   copy(a, a + 5, checked_array_iterator<int*>(b, 5));  
  
   cout << "(";  
   for (int i = 0 ; i < 5 ; i++)  
      cout << " " << b[i];  
   cout << " )" << endl;  
  
   // constructor example  
   checked_array_iterator<int*> checked_out_iter(b, 5);  
   copy(a, a + 5, checked_out_iter);  
  
   cout << "(";  
   for (int i = 0 ; i < 5 ; i++)  
      cout << " " << b[i];  
   cout << " )" << endl;  
}  
\* Output:   
( 0 1 2 3 4 )  
( 0 1 2 3 4 )  
*\  
```  
  
## <a name="example"></a>Ejemplo  
 Para evitar la necesidad de la clase `checked_array_iterator` cuando se usan algoritmos de la biblioteca estándar de C++, considere la posibilidad de usar `vector` en lugar de una matriz asignada de forma dinámica. En el ejemplo siguiente se muestra cómo hacerlo:  
  
```cpp  
// compile with: /EHsc /W4 /MTd  
  
#include <algorithm>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
int main()  
{  
    std::vector<int> v(10);  
    int *arr = new int[10];  
    for (int i = 0; i < 10; ++i)  
    {  
        v[i] = i;  
        arr[i] = i;  
    }  
  
    // std::copy(v.begin(), v.end(), arr); will result in  
    // warning C4996. To avoid this warning while using int *,  
    // use the Microsoft extension checked_array_iterator.  
    std::copy(v.begin(), v.end(),  
              stdext::checked_array_iterator<int *>(arr, 10));  
  
    // Instead of using stdext::checked_array_iterator and int *,  
    // consider using std::vector to encapsulate the array. This will  
    // result in no warnings, and the code will be portable.  
    std::vector<int> arr2(10);    // Similar to int *arr = new int[10];  
    std::copy(v.begin(), v.end(), arr2.begin());  
  
    for (int j = 0; j < arr2.size(); ++j)  
    {  
        cout << " " << arr2[j];  
    }  
    cout << endl;  
  
    return 0;  
}  
\* Output:   
 0 1 2 3 4 5 6 7 8 9  
*\  
```  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[checked_array_iterator](#checked_array_iterator__checked_array_iterator)|Construye un `checked_array_iterator` predeterminado o un `checked_array_iterator` a partir de un iterador subyacente.|  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[difference_type](#checked_array_iterator__difference_type)|Tipo que proporciona la diferencia entre dos `checked_array_iterator` que hacen referencia a elementos del mismo contenedor.|  
|[pointer](#checked_array_iterator__pointer)|Tipo que proporciona un puntero a un elemento direccionado por `checked_array_iterator`.|  
|[reference](#checked_array_iterator__reference)|Tipo que proporciona una referencia a un elemento direccionado por `checked_array_iterator`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[base](#checked_array_iterator__base)|Recupera el iterador subyacente de su `checked_array_iterator`.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator==](#checked_array_iterator__operator_eq_eq)|Comprueba dos `checked_array_iterator` para ver si son iguales.|  
|[operator!=](#checked_array_iterator__operator_neq)|Comprueba dos `checked_array_iterator` para ver si son distintos.|  
|[operator<](#checked_array_iterator__operator_lt_)|Comprueba si el `checked_array_iterator` a la izquierda del operador es menor que el `checked_array_iterator` de la derecha.|  
|[operator>](#checked_array_iterator__operator_gt_)|Comprueba si el `checked_array_iterator` a la izquierda del operador es mayor que el `checked_array_iterator` de la derecha.|  
|[operator<=](#checked_array_iterator__operator_lt__eq)|Comprueba si el `checked_array_iterator` a la izquierda del operador es menor o igual que el `checked_array_iterator` de la derecha.|  
|[operator>=](#checked_array_iterator__operator_gt__eq)|Comprueba si el `checked_array_iterator` a la izquierda del operador es mayor o igual que el `checked_array_iterator` de la derecha.|  
|[operator*](#checked_array_iterator__operator_star)|Devuelve el elemento que direcciona un `checked_array_iterator`.|  
|[operator->](#checked_array_iterator__operator-_gt_)|Devuelve un puntero al elemento direccionado por `checked_array_iterator`.|  
|[operator++](#checked_array_iterator__operator_add_add)|Incrementa el `checked_array_iterator` al elemento siguiente.|  
|[operator--](#checked_array_iterator__operator--)|Disminuye el `checked_array_iterator` al elemento anterior.|  
|[operator+=](#checked_array_iterator__operator_add_eq)|Agrega un desplazamiento especificado a un `checked_array_iterator`.|  
|[operator+](#checked_array_iterator__operator_add)|Agrega un desplazamiento a un iterador y devuelve el nuevo `checked_array_iterator` que direcciona el elemento insertado en la nueva posición de desplazamiento.|  
|[operator-=](#checked_array_iterator__operator-_eq)|Disminuye un desplazamiento especificado de un `checked_array_iterator`.|  
|[operator-](#checked_array_iterator__operator-)|Disminuye un desplazamiento de un iterador y devuelve el nuevo `checked_array_iterator` que direcciona el elemento insertado en la nueva posición de desplazamiento.|  
|[operator&#91;&#93;](#checked_array_iterator__operator_at)|Devuelve una referencia a un desplazamiento de elemento con respecto al elemento direccionado por `checked_array_iterator` un número especificado de posiciones.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<iterator>  
  
 **Espacio de nombres:** stdext  
  
##  <a name="checked_array_iterator__base"></a>  checked_array_iterator::base  
 Recupera el iterador subyacente de su `checked_array_iterator`.  
  
```
_Iterator base() const;
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// checked_array_iterators_base.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main() {  
   using namespace std;  
  
   int V1[10];  
  
   for (int i = 0; i < 10 ; i++)  
      V1[i] = i;  
  
   int* bpos;  
  
   stdext::checked_array_iterator<int*> rpos(V1, 10);  
   rpos++;  
  
   bpos = rpos.base ( );  
   cout << "The iterator underlying rpos is bpos & it points to: "   
        << *bpos << "." << endl;  
}  
\* Output:   
The iterator underlying rpos is bpos & it points to: 1.  
*\  
```  
  
##  <a name="checked_array_iterator__checked_array_iterator"></a>  checked_array_iterator::checked_array_iterator  
 Construye un `checked_array_iterator` predeterminado o un `checked_array _iterator` a partir de un iterador subyacente.  
  
```
checked_array_iterator();

checked_array_iterator(
    ITerator ptr,
    size_t size,
    size_t index = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `ptr`  
 Un puntero a la matriz.  
  
 `size`  
 Se refiere al tamaño de la matriz.  
  
 `index`  
 (Opcional) Un elemento de la matriz para inicializar el iterador.  De manera predeterminada, el iterador se inicializa en el primer elemento de la matriz.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// checked_array_iterators_ctor.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <iostream>   
  
using namespace std;  
using namespace stdext;  
  
int main() {  
   int a[] = {0, 1, 2, 3, 4};  
   int b[5];  
   copy(a, a + 5, checked_array_iterator<int*>(b,5));  
  
   for (int i = 0 ; i < 5 ; i++)  
      cout << b[i] << " ";  
   cout << endl;  
  
   checked_array_iterator<int*> checked_output_iterator(b,5);  
   copy (a, a + 5, checked_output_iterator);  
   for (int i = 0 ; i < 5 ; i++)  
      cout << b[i] << " ";  
   cout << endl;  
  
   checked_array_iterator<int*> checked_output_iterator2(b,5,3);  
   cout << *checked_output_iterator2 << endl;  
}  
\* Output:   
0 1 2 3 4   
0 1 2 3 4   
3  
*\  
```  
  
##  <a name="checked_array_iterator__difference_type"></a>  checked_array_iterator::difference_type  
 Tipo que proporciona la diferencia entre dos `checked_array_iterator` que hacen referencia a elementos del mismo contenedor.  
  
```
typedef typename iterator_traits<_Iterator>::difference_type difference_type;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo de diferencia `checked_array_iterator` es el mismo que el tipo de diferencia del iterador.  
  
 Vea [checked_array_iterator::operator[]](#checked_array_iterator__operator_at) para obtener un ejemplo de código.  
  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
##  <a name="checked_array_iterator__operator_eq_eq"></a>  checked_array_iterator::operator==  
 Comprueba dos `checked_array_iterator` para ver si son iguales.  
  
```
bool operator==(const checked_array_iterator<_Iterator>& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 El `checked_array_iterator` con el que se va a comprobar la igualdad.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// checked_array_iterators_opeq.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <iostream>   
  
using namespace std;  
using namespace stdext;  
  
int main() {  
   int a[] = {0, 1, 2, 3, 4};  
   int b[5];  
   copy(a, a + 5, checked_array_iterator<int*>(b,5));  
   copy(a, a + 5, checked_array_iterator<int*>(b,5));  
  
   checked_array_iterator<int*> checked_output_iterator(b,5);  
   checked_array_iterator<int*> checked_output_iterator2(b,5);  
  
   if (checked_output_iterator2 == checked_output_iterator)  
      cout << "checked_array_iterators are equal" << endl;  
   else  
      cout << "checked_array_iterators are not equal" << endl;  
  
   copy (a, a + 5, checked_output_iterator);  
   checked_output_iterator++;  
  
   if (checked_output_iterator2 == checked_output_iterator)  
      cout << "checked_array_iterators are equal" << endl;  
   else  
      cout << "checked_array_iterators are not equal" << endl;  
}  
\* Output:   
checked_array_iterators are equal  
checked_array_iterators are not equal  
*\  
```  
  
##  <a name="checked_array_iterator__operator_neq"></a>  checked_array_iterator::operator!=  
 Comprueba dos `checked_array_iterator` para ver si son distintos.  
  
```
bool operator!=(const checked_array_iterator<_Iterator>& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 El `checked_array_iterator` con el que se va a comprobar la desigualdad.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// checked_array_iterators_opneq.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <iostream>   
  
using namespace std;  
using namespace stdext;  
  
int main() {  
   int a[] = {0, 1, 2, 3, 4};  
   int b[5];  
   copy(a, a + 5, checked_array_iterator<int*>(b,5));  
   copy(a, a + 5, checked_array_iterator<int*>(b,5));  
  
   checked_array_iterator<int*> checked_output_iterator(b,5);  
   checked_array_iterator<int*> checked_output_iterator2(b,5);  
  
   if (checked_output_iterator2 != checked_output_iterator)  
      cout << "checked_array_iterators are not equal" << endl;  
   else  
      cout << "checked_array_iterators are equal" << endl;  
  
   copy (a, a + 5, checked_output_iterator);  
   checked_output_iterator++;  
  
   if (checked_output_iterator2 != checked_output_iterator)  
      cout << "checked_array_iterators are not equal" << endl;  
   else  
      cout << "checked_array_iterators are equal" << endl;  
}  
\* Output:   
checked_array_iterators are equal  
checked_array_iterators are not equal  
*\  
```  
  
##  <a name="checked_array_iterator__operator_lt_"></a>  checked_array_iterator::operator&lt;  
 Comprueba si el `checked_array_iterator` a la izquierda del operador es menor que el `checked_array_iterator` de la derecha.  
  
```
bool operator<(const checked_array_iterator<_Iterator>& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 El `checked_array_iterator` con el que se va a comprobar la desigualdad.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// checked_array_iterators_oplt.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <iostream>   
  
using namespace std;  
using namespace stdext;  
  
int main() {  
   int a[] = {0, 1, 2, 3, 4};  
   int b[5];  
   copy(a, a + 5, checked_array_iterator<int*>(b,5));  
   copy(a, a + 5, checked_array_iterator<int*>(b,5));  
  
   checked_array_iterator<int*> checked_output_iterator(b,5);  
   checked_array_iterator<int*> checked_output_iterator2(b,5);  
  
   if (checked_output_iterator2 < checked_output_iterator)  
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;  
   else  
      cout << "checked_output_iterator2 is not less than checked_output_iterator" << endl;  
  
   copy (a, a + 5, checked_output_iterator);  
   checked_output_iterator++;  
  
   if (checked_output_iterator2 < checked_output_iterator)  
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;  
   else  
      cout << "checked_output_iterator2 is not less than checked_output_iterator" << endl;  
}  
\* Output:   
checked_output_iterator2 is not less than checked_output_iterator  
checked_output_iterator2 is less than checked_output_iterator  
*\  
```  
  
##  <a name="checked_array_iterator__operator_gt_"></a>  checked_array_iterator::operator&gt;  
 Comprueba si el `checked_array_iterator` a la izquierda del operador es mayor que el `checked_array_iterator` de la derecha.  
  
```
bool operator>(const checked_array_iterator<_Iterator>& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 El `checked_array_iterator` con el que se va a comparar.  
  
### <a name="remarks"></a>Comentarios  
 Vea [checked_array_iterator::operator&lt;](#checked_array_iterator__operator_lt_) para obtener un ejemplo de código.  
  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
##  <a name="checked_array_iterator__operator_lt__eq"></a>  checked_array_iterator::operator&lt;=  
 Comprueba si el `checked_array_iterator` a la izquierda del operador es menor o igual que el `checked_array_iterator` de la derecha.  
  
```
bool operator<=(const checked_array_iterator<_Iterator>& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 El `checked_array_iterator` con el que se va a comparar.  
  
### <a name="remarks"></a>Comentarios  
 Vea [checked_array_iterator::operator&gt;=](#checked_array_iterator__operator_gt__eq) para obtener un ejemplo de código.  
  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
##  <a name="checked_array_iterator__operator_gt__eq"></a>  checked_array_iterator::operator&gt;=  
 Comprueba si el `checked_array_iterator` a la izquierda del operador es mayor o igual que el `checked_array_iterator` de la derecha.  
  
```
bool operator>=(const checked_array_iterator<_Iterator>& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 El `checked_array_iterator` con el que se va a comparar.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// checked_array_iterators_opgteq.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <iostream>   
  
using namespace std;  
using namespace stdext;  
  
int main() {  
   int a[] = {0, 1, 2, 3, 4};  
   int b[5];  
   copy(a, a + 5, checked_array_iterator<int*>(b,5));  
   copy(a, a + 5, checked_array_iterator<int*>(b,5));  
  
   checked_array_iterator<int*> checked_output_iterator(b,5);  
   checked_array_iterator<int*> checked_output_iterator2(b,5);  
  
   if (checked_output_iterator2 >= checked_output_iterator)  
      cout << "checked_output_iterator2 is greater than or equal to checked_output_iterator" << endl;  
   else  
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;  
  
   copy (a, a + 5, checked_output_iterator);  
   checked_output_iterator++;  
  
   if (checked_output_iterator2 >= checked_output_iterator)  
      cout << "checked_output_iterator2 is greater than or equal to checked_output_iterator" << endl;  
   else  
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;  
}  
\* Output:   
checked_output_iterator2 is greater than or equal to checked_output_iterator  
checked_output_iterator2 is less than checked_output_iterator  
*\  
```  
  
##  <a name="checked_array_iterator__operator_star"></a>  checked_array_iterator::operator*  
 Devuelve el elemento que direcciona un `checked_array_iterator`.  
  
```
reference operator*() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor del elemento al que se dirige el `checked_array_iterator`.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// checked_array_iterator_pointer.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <algorithm>  
#include <vector>  
#include <utility>  
#include <iostream>  
  
using namespace std;  
using namespace stdext;  
  
int main() {  
   int a[] = {0, 1, 2, 3, 4};  
   int b[5];  
   pair<int, int> c[1];  
   copy(a, a + 5, checked_array_iterator<int*>(b,5));  
  
   for (int i = 0 ; i < 5 ; i++)  
      cout << b[i] << endl;  
  
    c[0].first = 10;  
    c[0].second = 20;  
  
   checked_array_iterator<int*> checked_output_iterator(b,5);  
   checked_array_iterator<int*>::pointer p = &(*checked_output_iterator);  
   checked_array_iterator<pair<int, int>*> chk_c(c, 1);  
   checked_array_iterator<pair<int, int>*>::pointer p_c = &(*chk_c);  
  
   cout << "b[0] = " << *p << endl;  
   cout << "c[0].first = " << p_c->first << endl;  
}  
\* Output:   
0  
1  
2  
3  
4  
b[0] = 0  
c[0].first = 10  
*\  
```  
  
##  <a name="checked_array_iterator__operator-_gt_"></a>  checked_array_iterator::operator-&gt;  
 Devuelve un puntero al elemento direccionado por `checked_array_iterator`.  
  
```
pointer operator->() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al elemento al que se dirige el `checked_array_iterator`.  
  
### <a name="remarks"></a>Comentarios  
 Vea [checked_array_iterator::pointer](#checked_array_iterator__pointer) para obtener un ejemplo de código.  
  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
##  <a name="checked_array_iterator__operator_add_add"></a>  checked_array_iterator::operator++  
 Incrementa el `checked_array_iterator` al elemento siguiente.  
  
```
checked_array_iterator& operator++();

checked_array_iterator<_Iterator> operator++(int);
```  
  
### <a name="return-value"></a>Valor devuelto  
 El primer operador devuelve el `checked_array_iterator` preincrementado y el segundo, el operador de postincremento, devuelve una copia del `checked_array_iterator` incrementado.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// checked_array_iterators_op_plus_plus.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main() {  
   using namespace stdext;  
   using namespace std;  
   int a[] = {6, 3, 77, 199, 222};  
   int b[5];  
   copy(a, a + 5, checked_array_iterator<int*>(b,5));  
  
   checked_array_iterator<int*> checked_output_iterator(b,5);  
  
   cout << *checked_output_iterator << endl;  
   ++checked_output_iterator;  
   cout << *checked_output_iterator << endl;  
   checked_output_iterator++;  
   cout << *checked_output_iterator << endl;  
}  
\* Output:   
6  
3  
77  
*\  
```  
  
##  <a name="checked_array_iterator__operator--"></a>  checked_array_iterator::operator--  
 Disminuye el `checked_array_iterator` al elemento anterior.  
  
```
checked_array_iterator<_Iterator>& operator--();

checked_array_iterator<_Iterator> operator--(int);
```  
  
### <a name="return-value"></a>Valor devuelto  
 El primer operador devuelve el `checked_array_iterator` prereducido y el segundo, el operador de posdecremento, devuelve una copia del `checked_array_iterator` reducido.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// checked_array_iterators_op_minus_minus.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main() {  
   using namespace stdext;  
   using namespace std;  
   int a[] = {6, 3, 77, 199, 222};  
   int b[5];  
   copy(a, a + 5, checked_array_iterator<int*>(b,5));  
  
   checked_array_iterator<int*> checked_output_iterator(b,5);  
  
   cout << *checked_output_iterator << endl;  
   checked_output_iterator++;  
   cout << *checked_output_iterator << endl;  
   checked_output_iterator--;  
   cout << *checked_output_iterator << endl;  
}  
\* Output:   
6  
3  
6  
*\  
```  
  
##  <a name="checked_array_iterator__operator_add_eq"></a>  checked_array_iterator::operator+=  
 Agrega un desplazamiento especificado a un `checked_array_iterator`.  
  
```
checked_array_iterator<_Iterator>& operator+=(difference_type _Off);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Off`  
 El desplazamiento en el que se incrementa el iterador.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al elemento al que se dirige el `checked_array_iterator`.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// checked_array_iterators_op_plus_eq.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main() {  
   using namespace stdext;  
   using namespace std;  
   int a[] = {6, 3, 77, 199, 222};  
   int b[5];  
   copy(a, a + 5, checked_array_iterator<int*>(b,5));  
  
   checked_array_iterator<int*> checked_output_iterator(b,5);  
  
   cout << *checked_output_iterator << endl;  
   checked_output_iterator += 3;  
   cout << *checked_output_iterator << endl;  
}  
\* Output:   
6  
199  
*\  
```  
  
##  <a name="checked_array_iterator__operator_add"></a>  checked_array_iterator::operator+  
 Agrega un desplazamiento a un iterador y devuelve el nuevo `checked_array_iterator` que direcciona el elemento insertado en la nueva posición de desplazamiento.  
  
```
checked_array_iterator<_Iterator> operator+(difference_type _Off) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Off`  
 El desplazamiento que se va a agregar a `checked_array_iterator`.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `checked_array_iterator` que se dirige al elemento de desplazamiento.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// checked_array_iterators_op_plus.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main() {  
   using namespace stdext;  
   using namespace std;  
   int a[] = {6, 3, 77, 199, 222};  
   int b[5];  
   copy(a, a + 5, checked_array_iterator<int*>(b,5));  
  
   checked_array_iterator<int*> checked_output_iterator(b,5);  
  
   cout << *checked_output_iterator << endl;  
   checked_output_iterator = checked_output_iterator + 3;  
   cout << *checked_output_iterator << endl;  
}  
\* Output:   
6  
199  
*\  
```  
  
##  <a name="checked_array_iterator__operator-_eq"></a>  checked_array_iterator::operator-=  
 Disminuye un desplazamiento especificado de un `checked_array_iterator`.  
  
```
checked_array_iterator<_Iterator>& operator-=(difference_type _Off);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Off`  
 El desplazamiento en el que se incrementa el iterador.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al elemento al que se dirige el `checked_array_iterator`.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// checked_array_iterators_op_minus_eq.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main() {  
   using namespace stdext;  
   using namespace std;  
   int a[] = {6, 3, 77, 199, 222};  
   int b[5];  
   copy(a, a + 5, checked_array_iterator<int*>(b,5));  
  
   checked_array_iterator<int*> checked_output_iterator(b,5);  
  
   checked_output_iterator += 3;  
   cout << *checked_output_iterator << endl;  
   checked_output_iterator -= 2;  
   cout << *checked_output_iterator << endl;  
}  
\* Output:   
199  
3  
*\  
```  
  
##  <a name="checked_array_iterator__operator-"></a>  checked_array_iterator::operator-  
 Disminuye un desplazamiento de un iterador y devuelve el nuevo `checked_array_iterator` que direcciona el elemento insertado en la nueva posición de desplazamiento.  
  
```
checked_array_iterator<_Iterator> operator-(difference_type _Off) const;

difference_type operator-(const checked_array_iterator& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Off`  
 El desplazamiento que se restará del `checked_array_iterator`.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `checked_array_iterator` que se dirige al elemento de desplazamiento.  
  
### <a name="remarks"></a>Comentarios  
 Vea [checked_array_iterator::operator-](#checked_array_iterator__operator-) para obtener un ejemplo de código.  
  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
##  <a name="checked_array_iterator__operator_at"></a>  checked_array_iterator::operator[]  
 Devuelve una referencia a un desplazamiento de elemento con respecto al elemento direccionado por `checked_array_iterator` un número especificado de posiciones.  
  
```
reference operator[](difference_type _Off) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Off`  
 El desplazamiento desde la dirección del `checked_array_iterator`.  
  
### <a name="return-value"></a>Valor devuelto  
 La referencia al desplazamiento del elemento.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// checked_array_iterators_op_diff.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main() {  
   using namespace std;     
   int V1[10];  
  
   for (int i = 0; i < 10 ; i++)  
      V1[i] = i;  
  
   // Declare a difference type for a parameter  
   stdext::checked_array_iterator<int*>::difference_type diff = 2;  
  
   stdext::checked_array_iterator<int*> VChkIter(V1, 10);  
  
   stdext::checked_array_iterator<int*>::reference refrpos = VChkIter [diff];  
  
   cout << refrpos + 1 << endl;  
}  
\* Output:   
3  
*\  
```  
  
##  <a name="checked_array_iterator__pointer"></a>  checked_array_iterator::pointer  
 Tipo que proporciona un puntero a un elemento direccionado por `checked_array_iterator`.  
  
```
typedef typename iterator_traits<_Iterator>::pointer pointer;
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [checked_array_iterator::operator*](#checked_array_iterator__operator_star) para obtener un ejemplo de código.  
  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
##  <a name="checked_array_iterator__reference"></a>  checked_array_iterator::reference  
 Tipo que proporciona una referencia a un elemento direccionado por `checked_array_iterator`.  
  
```
typedef typename iterator_traits<_Iterator>::reference reference;
```  
  
### <a name="remarks"></a>Comentarios  
 Vea [checked_array_iterator::operator[]](#checked_array_iterator__operator_at) para obtener un ejemplo de código.  
  
 Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
## <a name="see-also"></a>Vea también  
 [\<iterator>](../standard-library/iterator.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)




