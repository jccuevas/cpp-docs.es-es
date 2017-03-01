---
title: "Clase array (Biblioteca estándar de C++)| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- array
- std::array
- array/std::array
- std::array::const_iterator
- array/std::array::const_iterator
- std::array::const_pointer
- array/std::array::const_pointer
- std::array::const_reference
- array/std::array::const_reference
- std::array::const_reverse_iterator
- array/std::array::const_reverse_iterator
- std::array::difference_type
- array/std::array::difference_type
- std::array::iterator
- array/std::array::iterator
- std::array::pointer
- array/std::array::pointer
- std::array::reference
- array/std::array::reference
- std::array::reverse_iterator
- array/std::array::reverse_iterator
- std::array::size_type
- array/std::array::size_type
- std::array::value_type
- array/std::array::value_type
- std::array::assign
- array/std::array::assign
- std::array::at
- array/std::array::at
- std::array::back
- array/std::array::back
- std::array::begin
- array/std::array::begin
- std::array::cbegin
- array/std::array::cbegin
- std::array::cend
- array/std::array::cend
- std::array::crbegin
- array/std::array::crbegin
- std::array::crend
- array/std::array::crend
- std::array::data
- array/std::array::data
- std::array::empty
- array/std::array::empty
- std::array::end
- array/std::array::end
- std::array::fill
- array/std::array::fill
- std::array::front
- array/std::array::front
- std::array::max_size
- array/std::array::max_size
- std::array::rbegin
- array/std::array::rbegin
- std::array::rend
- array/std::array::rend
- std::array::size
- array/std::array::size
- std::array::swap
- array/std::array::swap
- std::array::operator=
- array/std::array::operator=
- std::array::operator[]
- array/std::array::operator[]
dev_langs:
- C++
helpviewer_keywords:
- array class
ms.assetid: fdfd43a5-b2b5-4b9e-991f-93bf10fb4293
caps.latest.revision: 22
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
ms.openlocfilehash: 0e5e79e423d268da61ac9062edd099330f742b59
ms.lasthandoff: 02/24/2017

---
# <a name="array-class-c-standard-library"></a>Clase array (Biblioteca estándar de C++)
Describe un objeto que controla una secuencia de longitud `N` de elementos de tipo `Ty`. La secuencia se almacena como matriz de `Ty`, que se encuentra en el objeto `array<Ty, N>`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Ty, std::size_t N>  
class array;  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`Ty`|El tipo de un elemento.|  
|`N`|Número de elementos.|  
  
## <a name="members"></a>Miembros  
  
|||  
|-|-|  
|Definición de tipo|Descripción|  
|[array::const_iterator](#array__const_iterator)|El tipo de un iterador constante para la secuencia controlada.|  
|[array::const_pointer](#array__const_pointer)|El tipo de un puntero constante a un elemento.|  
|[array::const_reference](#array__const_reference)|El tipo de una referencia constante a un elemento.|  
|[array::const_reverse_iterator](#array__const_reverse_iterator)|El tipo de un iterador invertido constante para la secuencia controlada.|  
|[array::difference_type](#array__difference_type)|El tipo de una distancia con signo entre dos elementos.|  
|[array::iterator](#array__iterator)|El tipo de un iterador para la secuencia controlada.|  
|[array::pointer](#array__pointer)|El tipo de un puntero a un elemento.|  
|[array::reference](#array__reference)|El tipo de una referencia a un elemento.|  
|[array::reverse_iterator](#array__reverse_iterator)|El tipo de un iterador invertido para la secuencia controlada.|  
|[array::size_type](#array__size_type)|El tipo de una distancia sin signo entre dos elementos.|  
|[array::value_type](#array__value_type)|El tipo de un elemento.|  
  
|||  
|-|-|  
|Función miembro|Descripción|  
|[array::array](#array__array)|Construye un objeto de matriz.|  
|[array::assign](#array__assign)|Reemplaza todos los elementos.|  
|[array::at](#array__at)|Obtiene acceso a un elemento en una posición especificada.|  
|[array::back](#array__back)|Obtiene acceso al último elemento.|  
|[array::begin](#array__begin)|Designa el principio de la secuencia controlada.|  
|[array::cbegin](#array__cbegin)|Devuelve un iterador const de acceso aleatorio al primer elemento de la matriz.|  
|[array::cend](#array__cend)|Devuelve un iterador const de acceso aleatorio que apunta justo después del final de la matriz.|  
|[array::crbegin](#array__crbegin)|Devuelve un iterador constante al primer elemento de una matriz inversa.|  
|[array::crend](#array__crend)|Devuelve un iterador constante al final de una matriz invertida.|  
|[array::data](#array__data)|Obtiene la dirección del primer elemento.|  
|[array::empty](#array__empty)|Comprueba si hay algún elemento presente.|  
|[array::end](#array__end)|Designa el final de la secuencia controlada.|  
|[array::fill](#array__fill)|Reemplaza todos los elementos por un valor especificado.|  
|[array::front](#array__front)|Obtiene acceso al primer elemento.|  
|[array::max_size](#array__max_size)|Cuenta el número de elementos.|  
|[array::rbegin](#array__rbegin)|Designa el principio de la secuencia controlada inversa.|  
|[array::rend](#array__rend)|Designa el final de la secuencia controlada inversa.|  
|[array::size](#array__size)|Cuenta el número de elementos.|  
|[array::swap](#array__swap)|Intercambia el contenido de dos contenedores.|  
  
|||  
|-|-|  
|Operador|Descripción|  
|[array::operator=](#array__operator_eq)|Reemplaza la secuencia controlada.|  
|[array::operator[]](#array__operator_at)|Obtiene acceso a un elemento en una posición especificada.|  
  
## <a name="remarks"></a>Comentarios  
 El tipo tiene un constructor predeterminado `array()` y un operador de asignación predeterminado `operator=`, y cumple los requisitos de un `aggregate`. Por lo tanto, los objetos de tipo `array<Ty, N>` se pueden inicializar con un inicializador agregado. Por ejemplo,  
  
```  
array<int, 4> ai = { 1, 2, 3 };  
```  
  
 crea el objeto `ai` que contiene cuatro valores enteros, inicializa los tres primeros elementos a los valores 1, 2 y 3, respectivamente, e inicializa el cuarto a 0.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<array>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namearrayarraya--arrayarray"></a><a name="array__array"></a>  array::array  
 Construye un objeto de matriz.  
  
```  
array();

array(const array& right);
```  
  
### <a name="parameters"></a>Parámetros  
*right*  
 Objeto o intervalo que se va a insertar.  
  
### <a name="remarks"></a>Comentarios  
El constructor predeterminado `array()` deja la secuencia controlada sin inicializar (o inicializada de forma predeterminada). Se usa para especificar una secuencia controlada sin inicializar.  
  
El constructor de copias `array(const array& right)` inicializa la secuencia controlada con la secuencia [*right*`.begin()`, *right*`.end()`). Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de matriz *right*.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_array.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    Myarray c1(c0);   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
```  
  
##  <a name="a-namearrayassigna--arrayassign"></a><a name="array__assign"></a>  array::assign  
Obsoleto en C++11, se ha sustituido por [fill](#array__fill). Reemplaza todos los elementos.  
  
```  
void assign(const Ty& val);
```  
  
### <a name="parameters"></a>Parámetros  
 `val`  
 Valor que se va a asignar.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro reemplaza la secuencia controlada por `*this` por una repetición de `N` elementos de valor `val`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_assign.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    Myarray c1;   
    c1.assign(4);   
  
// display contents " 4 4 4 4"   
    for (Myarray::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
4 4 4 4  
```  
  
##  <a name="a-namearrayata--arrayat"></a><a name="array__at"></a>  array::at  
 Obtiene acceso a un elemento en una posición especificada.  
  
```  
reference at(size_type off);

constexpr const_reference at(size_type off) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `off`  
 Posición del elemento al que se accederá.  
  
### <a name="remarks"></a>Comentarios  
 Las funciones miembro devuelven una referencia al elemento de la secuencia controlada en la posición `off`. Si esa posición no es válida, la función produce un objeto de clase `out_of_range`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_at.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display odd elements " 1 3"   
    std::cout << " " << c0.at(1);   
    std::cout << " " << c0.at(3);   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
##  <a name="a-namearraybacka--arrayback"></a><a name="array__back"></a>  array::back  
 Obtiene acceso al último elemento.  
  
```  
reference back();

constexpr const_reference back() const;
```  
  
### <a name="remarks"></a>Comentarios  
 Las funciones miembro devuelven una referencia al último elemento de la secuencia controlada, que no debe estar vacío.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_back.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display last element " 3"   
    std::cout << " " << c0.back();   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
3  
```  
  
##  <a name="a-namearraybegina--arraybegin"></a><a name="array__begin"></a>  array::begin  
 Designa el principio de la secuencia controlada.  
  
```  
iterator begin() noexcept;  
const_iterator begin() const noexcept;  
```  
  
### <a name="remarks"></a>Comentarios  
 Las funciones miembro devuelven un iterador de acceso aleatorio que apunta al primer elemento de la secuencia (o más allá del final de una secuencia vacía).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_begin.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display first element " 0"   
    Myarray::iterator it2 = c0.begin();   
    std::cout << " " << *it2;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0  
```  
  
##  <a name="a-namearraycbegina--arraycbegin"></a><a name="array__cbegin"></a>  array::cbegin  
 Devuelve un iterador `const` que direcciona el primer elemento del intervalo.  
  
```  
const_iterator cbegin() const noexcept;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador `const` de acceso aleatorio que apunta al primer elemento del intervalo o la ubicación situada más allá del final de un intervalo vacío (para un intervalo vacío, `cbegin() == cend()`).  
  
### <a name="remarks"></a>Comentarios  
 Con el valor devuelto de `cbegin`, los elementos del intervalo no se pueden modificar.  
  
 Se puede usar esta función miembro en lugar de la función miembro `begin()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, se considera que `Container` es un contenedor modificable (distinto de `const`) de cualquier naturaleza que admite `begin()` y `cbegin()`.  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="a-namearraycenda--arraycend"></a><a name="array__cend"></a>  array::cend  
 Devuelve un iterador `const` que direcciona la ubicación situada más allá del último elemento de un intervalo.  
  
```  
const_iterator cend() const noexcept;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador de acceso aleatorio que apunta justo después del final del intervalo.  
  
### <a name="remarks"></a>Comentarios  
 `cend` se usa para probar si un iterador ha sobrepasado el final de su intervalo.  
  
 Se puede usar esta función miembro en lugar de la función miembro `end()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, se considera que `Container` es un contenedor modificable (distinto de `const`) de cualquier naturaleza que admite `end()` y `cend()`.  
  
```cpp  
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
 El valor devuelto por `cend` no se debe desreferenciar.  
  
##  <a name="a-namearrayconstiteratora--arrayconstiterator"></a><a name="array__const_iterator"></a>  array::const_iterator  
 El tipo de un iterador constante para la secuencia controlada.  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto que puede actuar como un iterador de acceso aleatorio constante para la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_const_iterator.cpp  
// compile with: /EHsc /W4  
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> MyArray;   
  
int main()   
{   
    MyArray c0 = {0, 1, 2, 3};   
  
    // display contents " 0 1 2 3"   
    std::cout << "it1:";  
    for ( MyArray::const_iterator it1 = c0.begin();   
          it1 != c0.end();   
          ++it1 ) {  
       std::cout << " " << *it1;   
    }  
    std::cout << std::endl;   
  
    // display first element " 0"   
    MyArray::const_iterator it2 = c0.begin();   
    std::cout << "it2:";  
    std::cout << " " << *it2;   
    std::cout << std::endl;   
  
    return (0);   
}  
  
```  
  
```Output  
it1: 0 1 2 3                                  
  
it2: 0  
  
```  
  
##  <a name="a-namearrayconstpointera--arrayconstpointer"></a><a name="array__const_pointer"></a>  array::const_pointer  
 El tipo de un puntero constante a un elemento.  
  
```  
typedef const Ty *const_pointer;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto que puede actuar como un puntero constante a elementos de la secuencia.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_const_pointer.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display first element " 0"   
    Myarray::const_pointer ptr = &*c0.begin();   
    std::cout << " " << *ptr;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0  
```  
  
##  <a name="a-namearrayconstreferencea--arrayconstreference"></a><a name="array__const_reference"></a>  array::const_reference  
 El tipo de una referencia constante a un elemento.  
  
```  
typedef const Ty& const_reference;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto que puede actuar como referencia constante a un elemento de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_const_reference.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display first element " 0"   
    Myarray::const_reference ref = *c0.begin();   
    std::cout << " " << ref;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0  
```  
  
##  <a name="a-namearrayconstreverseiteratora--arrayconstreverseiterator"></a><a name="array__const_reverse_iterator"></a>  array::const_reverse_iterator  
 El tipo de un iterador invertido constante para la secuencia controlada.  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto que puede actuar como un iterador inverso constante para la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_const_reverse_iterator.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display last element " 3"   
    Myarray::const_reverse_iterator it2 = c0.rbegin();   
    std::cout << " " << *it2;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
3  
```  
  
##  <a name="a-namearraycrbegina--arraycrbegin"></a><a name="array__crbegin"></a>  array::crbegin  
 Devuelve un iterador constante al primer elemento de una matriz inversa.  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador inverso constante de acceso aleatorio que dirige al primer elemento de una matriz inversa o al que fue el último elemento de la matriz sin invertir.  
  
### <a name="remarks"></a>Comentarios  
 Con el valor devuelto de `crbegin`, el objeto de matriz no se puede modificar.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// array_crbegin.cpp  
// compile with: /EHsc  
#include <array>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   array<int, 2> v1 = {1, 2};  
   array<int, 2>::iterator v1_Iter;  
   array<int, 2>::const_reverse_iterator v1_rIter;  
  
   v1_Iter = v1.begin( );  
   cout << "The first element of array is "  
        << *v1_Iter << "." << endl;  
  
   v1_rIter = v1.crbegin( );  
   cout << "The first element of the reversed array is "  
        << *v1_rIter << "." << endl;  
}  
```  
  
```Output  
The first element of array is 1.  
The first element of the reversed array is 2.  
```  
  
##  <a name="a-namearraycrenda--arraycrend"></a><a name="array__crend"></a>  array::crend  
 Devuelve un iterador constante que dirige a la ubicación siguiente al último elemento de una matriz invertida.  
  
```  
const_reverse_iterator crend() const noexcept;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador constante de acceso aleatorio inverso que dirige a la ubicación siguiente al último elemento de una matriz invertida (la ubicación que había precedido al primer elemento de la matriz sin invertir).  
  
### <a name="remarks"></a>Comentarios  
 `crend` se usa con una matriz invertida igual que [array::cend](#array__cend) se emplea con una matriz.  
  
 Con el valor devuelto de `crend` (adecuadamente reducido), el objeto de matriz no se puede modificar.  
  
 Se puede utilizar `crend` para comprobar si un iterador inverso ha llegado al final de su matriz.  
  
 El valor devuelto por `crend` no se debe desreferenciar.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// array_crend.cpp  
// compile with: /EHsc  
#include <array>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   array<int, 2> v1 = {1, 2};  
   array<int, 2>::const_reverse_iterator v1_rIter;  
  
   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )  
      cout << *v1_rIter << endl;  
}  
```  
  
```Output  
2  
1  
```  
  
##  <a name="a-namearraydataa--arraydata"></a><a name="array__data"></a>  array::data  
 Obtiene la dirección del primer elemento.  
  
```  
Ty *data();

const Ty *data() const;
```  
  
### <a name="remarks"></a>Comentarios  
 Las funciones miembro devuelven la dirección del primer elemento de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_data.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display first element " 0"   
    Myarray::pointer ptr = c0.data();   
    std::cout << " " << *ptr;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0  
```  
  
##  <a name="a-namearraydifferencetypea--arraydifferencetype"></a><a name="array__difference_type"></a>  array::difference_type  
 El tipo de una distancia con signo entre dos elementos.  
  
```  
typedef std::ptrdiff_t difference_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo de entero con signo describe un objeto que puede representar la diferencia entre las direcciones de dos elementos cualesquiera de la secuencia controlada. Es un sinónimo del tipo `std::ptrdiff_t`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_difference_type.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display distance first-last " -4"   
    Myarray::difference_type diff = c0.begin() - c0.end();   
    std::cout << " " << diff;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
-4  
```  
  
##  <a name="a-namearrayemptya--arrayempty"></a><a name="array__empty"></a>  array::empty  
 Comprueba si no hay ningún elemento presente.  
  
```  
constexpr bool empty() const;
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve true solo si `N == 0`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_empty.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display whether c0 is empty " false"   
    std::cout << std::boolalpha << " " << c0.empty();   
    std::cout << std::endl;   
  
    std::array<int, 0> c1;   
  
// display whether c1 is empty " true"   
    std::cout << std::boolalpha << " " << c1.empty();   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
false  
true  
```  
  
##  <a name="a-namearrayenda--arrayend"></a><a name="array__end"></a>  array::end  
 Designa el final de la secuencia controlada.  
  
```  
reference end();

const_reference end() const;
```  
  
### <a name="remarks"></a>Comentarios  
 Las funciones miembro devuelven un iterador de acceso aleatorio que apunta inmediatamente después del final de la secuencia.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_end.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display last element " 3"   
    Myarray::iterator it2 = c0.end();   
    std::cout << " " << *--it2;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
3  
```  
  
##  <a name="a-namearrayfilla--arrayfill"></a><a name="array__fill"></a>  array::fill  
 Borra una matriz y copia los elementos especificados en la matriz vacía.  
  
```  
void fill(const Type& val);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|` val`|Valor del elemento que se va a insertar en la matriz.|  
  
### <a name="remarks"></a>Comentarios  
 `fill` reemplaza cada elemento de la matriz por el valor especificado.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// array_fill.cpp  
// compile with: /EHsc  
#include <array>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   array<int, 2> v1 = {1, 2};  
   array<int, 2>::iterator iter;  
  
   cout << "v1 = " ;  
   for (iter = v1.begin(); iter != v1.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
  
   v1.fill(3);  
   cout << "v1 = " ;  
   for (iter = v1.begin(); iter != v1.end(); iter++)  
      cout << *iter << " ";  
   cout << endl;  
}  
```  
  
##  <a name="a-namearrayfronta--arrayfront"></a><a name="array__front"></a>  array::front  
 Obtiene acceso al primer elemento.  
  
```  
reference front();

constexpr const_reference front() const;
```  
  
### <a name="remarks"></a>Comentarios  
 Las funciones miembro devuelven una referencia al primer elemento de la secuencia controlada, que no debe estar vacío.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_front.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display first element " 0"   
    std::cout << " " << c0.front();   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0  
```  
  
##  <a name="a-namearrayiteratora--arrayiterator"></a><a name="array__iterator"></a>  array::iterator  
 El tipo de un iterador para la secuencia controlada.  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto que puede actuar como un iterador de acceso aleatorio de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_iterator.cpp   
// compile with: /EHsc /W4  
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> MyArray;   
  
int main()   
{   
    MyArray c0 = {0, 1, 2, 3};   
  
    // display contents " 0 1 2 3"   
    std::cout << "it1:";  
    for ( MyArray::iterator it1 = c0.begin();   
          it1 != c0.end();   
          ++it1 ) {  
       std::cout << " " << *it1;   
    }  
    std::cout << std::endl;   
  
    // display first element " 0"   
    MyArray::iterator it2 = c0.begin();   
    std::cout << "it2:";  
    std::cout << " " << *it2;   
    std::cout << std::endl;   
  
    return (0);   
}  
  
```  
  
```Output  
it1: 0 1 2 3                                  
  
it2: 0  
  
```  
  
##  <a name="a-namearraymaxsizea--arraymaxsize"></a><a name="array__max_size"></a>  array::max_size  
 Cuenta el número de elementos.  
  
```  
constexpr size_type max_size() const;
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve `N`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_max_size.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display (maximum) size " 4"   
    std::cout << " " << c0.max_size();   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
4  
```  
  
##  <a name="a-namearrayoperatorata--arrayoperator"></a><a name="array__operator_at"></a>  array::operator[]  
 Obtiene acceso a un elemento en una posición especificada.  
  
```  
reference operator[](size_type off);

constexpr const_reference operator[](size_type off) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `off`  
 Posición del elemento al que se accederá.  
  
### <a name="remarks"></a>Comentarios  
 Las funciones miembro devuelven una referencia al elemento de la secuencia controlada en la posición `off`. Si esa posición no es válida, el comportamiento es indefinido.  
  
También hay una función no miembro [get](array-functions.md#get_function) disponible para obtener una referencia a un elemento de `array`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_operator_sub.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display odd elements " 1 3"   
    std::cout << " " << c0[1];   
    std::cout << " " << c0[3];   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
1 3  
```  
  
##  <a name="a-namearrayoperatoreqa--arrayoperator"></a><a name="array__operator_eq"></a>  array::operator=  
 Reemplaza la secuencia controlada.  
  
```  
array <Value>%  operator=(array <Value>% right);
```  
  
### <a name="parameters"></a>Parámetros  
 right  
 Contenedor que se va a copiar.  
  
### <a name="remarks"></a>Comentarios  
 El operador miembro asigna cada elemento de `right` al elemento correspondiente de la secuencia controlada y luego devuelve `*this`. Se usa para reemplazar la secuencia controlada por una copia de la secuencia controlada de `right`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_operator_as.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    Myarray c1;   
    c1 = c0;   
  
// display copied contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
```  
  
##  <a name="a-namearraypointera--arraypointer"></a><a name="array__pointer"></a>  array::pointer  
 El tipo de un puntero a un elemento.  
  
```  
typedef Ty *pointer;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto que puede actuar como un puntero a elementos de la secuencia.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_pointer.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display first element " 0"   
    Myarray::pointer ptr = &*c0.begin();   
    std::cout << " " << *ptr;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0  
```  
  
##  <a name="a-namearrayrbegina--arrayrbegin"></a><a name="array__rbegin"></a>  array::rbegin  
 Designa el principio de la secuencia controlada inversa.  
  
```  
reverse_iterator rbegin()noexcept;  
const_reverse_iterator rbegin() const noexcept;  
```  
  
### <a name="remarks"></a>Comentarios  
 Las funciones miembro devuelven un iterador inverso que apunta inmediatamente después del final de la secuencia controlada. Por tanto, designa el principio de la secuencia inversa.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_rbegin.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display last element " 3"   
    Myarray::const_reverse_iterator it2 = c0.rbegin();   
    std::cout << " " << *it2;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
3  
```  
  
##  <a name="a-namearrayreferencea--arrayreference"></a><a name="array__reference"></a>  array::reference  
 El tipo de una referencia a un elemento.  
  
```  
typedef Ty& reference;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto que puede actuar como referencia a un elemento de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_reference.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display first element " 0"   
    Myarray::reference ref = *c0.begin();   
    std::cout << " " << ref;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0  
```  
  
##  <a name="a-namearrayrenda--arrayrend"></a><a name="array__rend"></a>  array::rend  
 Designa el final de la secuencia controlada inversa.  
  
```  
reverse_iterator rend()noexcept;  
const_reverse_iterator rend() const noexcept;  
```  
  
### <a name="remarks"></a>Comentarios  
 Las funciones miembro devuelven un iterador inverso que apunta al primer elemento de la secuencia (o más allá del final de una secuencia vacía). Por tanto, designa el final de la secuencia inversa.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_rend.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display first element " 0"   
    Myarray::const_reverse_iterator it2 = c0.rend();   
    std::cout << " " << *--it2;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0  
```  
  
##  <a name="a-namearrayreverseiteratora--arrayreverseiterator"></a><a name="array__reverse_iterator"></a>  array::reverse_iterator  
 El tipo de un iterador invertido para la secuencia controlada.  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto que puede actuar como un iterador inverso para la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_reverse_iterator.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display last element " 3"   
    Myarray::reverse_iterator it2 = c0.rbegin();   
    std::cout << " " << *it2;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
3  
```  
  
##  <a name="a-namearraysizea--arraysize"></a><a name="array__size"></a>  array::size  
 Cuenta el número de elementos.  
  
```  
constexpr size_type size() const;
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve `N`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_size.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display size " 4"   
    std::cout << " " << c0.size();   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
4  
```  
  
##  <a name="a-namearraysizetypea--arraysizetype"></a><a name="array__size_type"></a>  array::size_type  
 Tipo de una distancia sin signo entre dos elementos.  
  
```  
typedef std::size_t size_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo de entero sin signo describe un objeto que puede representar la longitud de cualquier secuencia controlada. Es un sinónimo del tipo `std::size_t`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_size_type.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display distance last-first " 4"   
    Myarray::size_type diff = c0.end() - c0.begin();   
    std::cout << " " << diff;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
4  
```  
  
##  <a name="a-namearrayswapa--arrayswap"></a><a name="array__swap"></a>  array::swap  
Intercambia el contenido de esta matriz con otra matriz.  
  
```  
void swap(array& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 Matriz con la que se va a intercambiar el contenido.  
  
### <a name="remarks"></a>Comentarios  
La función miembro intercambia las secuencias controladas entre `*this` y `right`. Realiza una serie de asignaciones de elementos y llamadas de contructores proporcionales a `N`.  

También hay una función no miembro [swap](array-functions.md#swap_function) disponible para intercambiar dos instancias `array`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_swap.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    Myarray c1 = {4, 5, 6, 7};   
    c0.swap(c1);   
  
// display swapped contents " 4 5 6 7"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    swap(c0, c1);   
  
// display swapped contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
4 5 6 7  
0 1 2 3  
```  
  
##  <a name="a-namearrayvaluetypea--arrayvaluetype"></a><a name="array__value_type"></a>  array::value_type  
 El tipo de un elemento.  
  
```  
typedef Ty value_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla `Ty`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__array__array_value_type.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;   
int main()   
    {   
    Myarray c0 = {0, 1, 2, 3};   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        std::cout << " " << *it;   
    std::cout << std::endl;   
  
// display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();   
        it != c0.end(); ++it)   
        {   
        Myarray::value_type val = *it;   
        std::cout << " " << val;   
        }   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
```  
  
## <a name="see-also"></a>Vea también  
 [\<array>](../standard-library/array.md)


