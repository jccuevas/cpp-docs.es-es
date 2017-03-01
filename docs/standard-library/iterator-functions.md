---
title: Funciones de &lt;iterator&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a57c9a3-7e36-411f-8655-e0be2eec88e7
caps.latest.revision: 16
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 1fb4f0f27496db45c7bbb7b609e0f945eb007154
ms.lasthandoff: 02/24/2017

---
# <a name="ltiteratorgt-functions"></a>Funciones de &lt;iterator&gt;
||||  
|-|-|-|  
|[advance](#advance)|[back_inserter](#back_inserter)|[begin](#begin)|  
|[cbegin](#cbegin)|[cend](#cend)|[distance](#distance)|  
|[end](#end)|[front_inserter](#front_inserter)|[inserter](#inserter)|  
|[make_checked_array_iterator](#make_checked_array_iterator)|[make_move_iterator](#make_move_iterator)|[make_unchecked_array_iterator](#make_unchecked_array_iterator)|  
|[next](#next)|[prev](#prev)|  
  
##  <a name="a-nameadvancea--advance"></a><a name="advance"></a>  advance  
 Incrementa un iterador un número especificado de posiciones.  
  
```  
template <class InputIterator, class Distance>  
void advance(
    InputIterator& InIt,   
    Distance Off);
```  
  
### <a name="parameters"></a>Parámetros  
 `InIt`  
 Iterador que se va a incrementar y que debe satisfacer los requisitos de un iterador de entrada.  
  
 `Off`  
 Tipo entero convertible en el tipo de diferencia del iterador y que especifica el número de incrementos que la posición del iterador debe avanzar.  
  
### <a name="remarks"></a>Comentarios  
 El intervalo que se avanza debe ser no singular, donde los iteradores deben ser desreferenciables o pasar al final.  
  
 Si **InputIterator** cumple los requisitos de un tipo de iterador bidireccional, `Off` puede ser negativo. Si **InputIterator** es un tipo de iterador de entrada o hacia delante, `Off` no debe ser negativo.  
  
 La función advance tiene complejidad constante cuando **InputIterator** cumple los requisitos de un iterador de acceso aleatorio. En caso contrario, tiene complejidad lineal y, por tanto, es potencialmente costosa.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// iterator_advance.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   list<int> L;  
   for ( i = 1 ; i < 9 ; ++i )    
   {  
      L.push_back ( i );  
   }  
   list <int>::iterator L_Iter, LPOS = L.begin ( );  
  
   cout << "The list L is: ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
  
   cout << "The iterator LPOS initially points to the first element: "  
        << *LPOS << "." << endl;  
  
   advance ( LPOS , 4 );  
   cout << "LPOS is advanced 4 steps forward to point"  
        << " to the fifth element: "  
        << *LPOS << "." << endl;  
  
   advance ( LPOS , -3 );  
   cout << "LPOS is moved 3 steps back to point to the "  
        << "2nd element: " << *LPOS << "." << endl;  
}  
```  
  
```Output  
The list L is: ( 1 2 3 4 5 6 7 8 ).  
The iterator LPOS initially points to the first element: 1.  
LPOS is advanced 4 steps forward to point to the fifth element: 5.  
LPOS is moved 3 steps back to point to the 2nd element: 2.  
```  
  
##  <a name="a-namebackinsertera--backinserter"></a><a name="back_inserter"></a>  back_inserter  
 Crea un iterador que puede insertar elementos en la parte posterior de un contenedor especificado.  
  
```  
template <class Container>  
back_insert_iterator<Container> back_inserter(Container& _Cont);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Cont`  
 Contenedor en el que se va a ejecutar la inserción en el final.  
  
### <a name="return-value"></a>Valor devuelto  
 `back_insert_iterator` asociado con el objeto contenedor `_Cont`.  
  
### <a name="remarks"></a>Comentarios  
 Dentro de la biblioteca estándar de C++, el argumento debe hacer referencia a uno de los tres contenedores de secuencia que tienen la función miembro `push_back`: [clase deque](../standard-library/deque-class.md), [clase list](../standard-library/list-class.md) o [clase vector](../standard-library/vector-class.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// iterator_back_inserter.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for ( i = 0 ; i < 3 ; ++i )    
   {  
      vec.push_back ( i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   // Insertions can be done with template function  
   back_insert_iterator<vector<int> > backiter ( vec );  
 *backiter = 30;  
   backiter++;  
 *backiter = 40;  
  
   // Alternatively, insertions can be done with the  
   // back_insert_iterator member function  
   back_inserter ( vec ) = 500;  
   back_inserter ( vec ) = 600;  
  
   cout << "After the insertions, the vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 1 2 ).  
After the insertions, the vector vec is: ( 0 1 2 30 40 500 600 ).  
```  
  
##  <a name="a-namebegina--begin"></a><a name="begin"></a>  begin  
 Recupera un iterador en el primer elemento de un contenedor especificado.  
  
```  
template <class Container>  
auto begin(Container& cont)  `
   -> decltype(cont.begin());

template <class Container>  
auto begin(const Container& cont)   `
   -> decltype(cont.begin());

template <class Ty, class Size>  
Ty *begin(Ty (& array)[Size]);
```  
  
### <a name="parameters"></a>Parámetros  
 `cont`  
 Un contenedor.  
  
 `array`  
 Matriz de objetos de tipo `Ty`.  
  
### <a name="return-value"></a>Valor devuelto  
 Las dos primeras funciones de plantilla devuelven `cont.begin()`. La primera función no es constante; la segunda es constante.  
  
 La tercera función de plantilla devuelve `array`.  
  
### <a name="example"></a>Ejemplo  
  Se recomienda usar esta función de plantilla en lugar del miembro contenedor `begin()` cuando se precise un comportamiento más genérico.  
  
```cpp  
// cl.exe /EHsc /nologo /W4 /MTd   
#include <algorithm>  
#include <functional>  
#include <iostream>  
#include <iterator>  
#include <vector>  
  
template <typename C> void reverse_sort(C& c) {  
    using std::begin;  
    using std::end;  
  
    std::sort(begin(c), end(c), std::greater<>());  
}  
  
template <typename C> void print(const C& c) {  
    for (const auto& e : c) {  
        std::cout << e << " ";  
    }  
  
    std::cout << "\n";  
}  
  
int main() {  
    std::vector<int> v = { 11, 34, 17, 52, 26, 13, 40, 20, 10, 5, 16, 8, 4, 2, 1 };  
  
    print(v);  
    reverse_sort(v);  
    print(v);  
  
    std::cout << "--\n";  
  
    int arr[] = { 23, 70, 35, 106, 53, 160, 80, 40, 20, 10, 5, 16, 8, 4, 2, 1 };  
  
    print(arr);  
    reverse_sort(arr);  
    print(arr);  
}  
  
```  
  
```  
Output:  
11 34 17 52 26 13 40 20 10 5 16 8 4 2 1  
52 40 34 26 20 17 16 13 11 10 8 5 4 2 1  
--  
23 70 35 106 53 160 80 40 20 10 5 16 8 4 2 1  
160 106 80 70 53 40 35 23 20 16 10 8 5 4 2 1  
```  
  
  La función `reverse_sort` admite contenedores de cualquier clase, además de matrices regulares, porque llama a la versión que no es miembro de `begin()`. Si `reverse_sort` se codificó para usar el miembro contenedor `begin()`:  
  
```cpp  
template <typename C>  
void reverse_sort(C& c) {  
    using std::begin;  
    using std::end;  
 
    std::sort(c.begin(), c.end(), std::greater<>());

}  
```  
  
 Por tanto, enviarle una matriz podría provocar este error del compilador:  
  
```  
error C2228: left of '.begin' must have class/struct/union  
```  
  
##  <a name="a-namecbegina--cbegin"></a><a name="cbegin"></a>  cbegin  
 Recupera un iterador const en el primer elemento de un contenedor especificado.  
  
```  
template <class Container>  
auto cbegin(const Container& cont)   `
   -> decltype(cont.begin());
```  
  
### <a name="parameters"></a>Parámetros  
 `cont`  
 Un contenedor o initializer_list.  
  
### <a name="return-value"></a>Valor devuelto  
 Un objeto `cont.begin()` constante.  
  
### <a name="remarks"></a>Comentarios  
 Esta función funciona con todos los contenedores de la biblioteca estándar de C++ y con [initializer_list](../standard-library/initializer-list-class.md).  
  
 Puede utilizar esta función miembro en lugar de la función de plantilla `begin()` para garantizar que el valor devuelto sea `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, se considera que `Container` es un contenedor modificable (no `const`) o `initializer_list` de cualquier naturaleza que admite `begin()` y `cbegin()`.  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator  
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="a-namecenda--cend"></a><a name="cend"></a>  cend  
 Recupera un iterador const en el elemento que sigue al último elemento del contenedor especificado.  
  
```  
template <class Container>  
auto cend(const Container& cont)   `
   -> decltype(cont.end());
```  
  
### <a name="parameters"></a>Parámetros  
 `cont`  
 Un contenedor o initializer_list.  
  
### <a name="return-value"></a>Valor devuelto  
 Un objeto `cont.end()` constante.  
  
### <a name="remarks"></a>Comentarios  
 Esta función funciona con todos los contenedores de la biblioteca estándar de C++ y con [initializer_list](../standard-library/initializer-list-class.md).  
  
 Puede usar esta función miembro en lugar de la función de plantilla [end()](../standard-library/iterator-functions.md#end) para garantizar que el valor devuelto sea `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, se considera que `Container` es un contenedor modificable (no `const`) o `initializer_list` de cualquier naturaleza que admite `end()` y `cend()`.  
  
```cpp  
auto i1 = Container.end();
// i1 is Container<T>::iterator  
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="a-namedistancea--distance"></a><a name="distance"></a>  distance  
 Determina el número de incrementos entre las posiciones direccionadas por dos iteradores.  
  
```  
template <class InputIterator>  
typename iterator_traits<InputIterator>::difference_type distance(InputIterator first, InputIterator last);
```  
  
### <a name="parameters"></a>Parámetros  
 ` first`  
 Primer iterador cuya distancia del segundo debe determinarse.  
  
 ` last`  
 Segundo iterador cuya distancia del primero debe determinarse.  
  
### <a name="return-value"></a>Valor devuelto  
 Número de veces que se debe incrementar ` first` hasta que sea igual que ` last`.  
  
### <a name="remarks"></a>Comentarios  
 La función distance tiene complejidad constante cuando **InputIterator** cumple los requisitos de un iterador de acceso aleatorio. En caso contrario, tiene complejidad lineal y, por tanto, es potencialmente costosa.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// iterator_distance.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   list<int> L;  
   for ( i = -1 ; i < 9 ; ++i )   
   {  
      L.push_back ( 2 * i );  
   }  
   list <int>::iterator L_Iter, LPOS = L.begin ( );  
  
   cout << "The list L is: ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
  
   cout << "The iterator LPOS initially points to the first element: "  
        << *LPOS << "." << endl;  
  
   advance ( LPOS , 7 );  
   cout << "LPOS is advanced 7 steps forward to point "  
        << " to the eighth element: "  
        << *LPOS << "." << endl;  
  
   list<int>::difference_type Ldiff ;  
   Ldiff = distance ( L.begin ( ) , LPOS );  
   cout << "The distance from L.begin( ) to LPOS is: "  
        << Ldiff << "." << endl;  
}  
```  
  
```Output  
The list L is: ( -2 0 2 4 6 8 10 12 14 16 ).  
The iterator LPOS initially points to the first element: -2.  
LPOS is advanced 7 steps forward to point  to the eighth element: 12.  
The distance from L.begin( ) to LPOS is: 7.  
```  
  
##  <a name="a-nameenda--end"></a><a name="end"></a>  end  
 Recupera un iterador en el elemento que sigue al último elemento del contenedor especificado.  
  
```  
template <class Container>  
auto end(Container& cont)   `
   -> decltype(cont.end());

template <class Container>  
auto end(const Container& cont)   `
   -> decltype(cont.end());

template <class Ty, class Size>  
Ty *end(Ty (& array)[Size]);
```  
  
### <a name="parameters"></a>Parámetros  
 `cont`  
 Un contenedor.  
  
 `array`  
 Matriz de objetos de tipo `Ty`.  
  
### <a name="return-value"></a>Valor devuelto  
 Las dos primeras funciones devuelven `cont.end()` (la primeras es no-constante y la segunda es constante).  
  
 La tercera función de plantilla devuelve `array + Size`.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener un ejemplo de código, vea [begin](../standard-library/iterator-functions.md#begin).  
  
##  <a name="a-namefrontinsertera--frontinserter"></a><a name="front_inserter"></a>  front_inserter  
 Crea un iterador que puede insertar elementos en la parte delantera de un contenedor especificado.  
  
```  
template <class Container>  
front_insert_iterator<Container> front_inserter(Container& _Cont);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Cont`  
 Objeto contenedor en cuya parte frontal se va a insertar un elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 `front_insert_iterator` asociado con el objeto contenedor `_Cont`.  
  
### <a name="remarks"></a>Comentarios  
 También se puede usar la función miembro [front_insert_iterator](../standard-library/front-insert-iterator-class.md#front_insert_iterator__front_insert_iterator) de la clase front_insert_iterator.  
  
 Dentro de la biblioteca estándar de C++, el argumento debe hacer referencia a uno de los dos contenedores de secuencia que tienen la función miembro `push_back`: [clase deque](../standard-library/deque-class.md), o "clase list".  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// iterator_front_inserter.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   list <int>::iterator L_Iter;  
  
   list<int> L;  
   for ( i = -1 ; i < 9 ; ++i )  
   {  
      L.push_back ( i );  
   }  
  
   cout << "The list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
  
   // Using the template function to insert an element  
   front_insert_iterator< list < int> > Iter(L);  
 *Iter = 100;  
  
   // Alternatively, you may use the front_insert member function  
   front_inserter ( L ) = 200;  
  
   cout << "After the front insertions, the list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The list L is:  
 ( -1 0 1 2 3 4 5 6 7 8 ).  
After the front insertions, the list L is:  
 ( 200 100 -1 0 1 2 3 4 5 6 7 8 ).  
```  
  
##  <a name="a-nameinsertera--inserter"></a><a name="inserter"></a>  inserter  
 Función de plantilla auxiliar que le permite usar `inserter(``_Cont``,``_Where``)` en lugar de `insert_iterator<Container>(``_Cont`, `_Where``)`.  
  
```  
template <class Container>  
insert_iterator<Container>  
inserter(
    Container& _Cont,  
    typename Container::iterator _Where);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Cont`  
 Contenedor en el que se van a agregar nuevos elementos.  
  
 `_Where`  
 Iterador que localiza el punto de inserción.  
  
### <a name="remarks"></a>Comentarios  
 La función de plantilla devuelve [insert_iterator](../standard-library/insert-iterator-class.md#insert_iterator__insert_iterator)`<Container>(``_Cont``,` `_Where``)`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// iterator_inserter.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   list <int>::iterator L_Iter;  
  
   list<int> L;  
   for (i = 2 ; i < 5 ; ++i )    
   {  
      L.push_back ( 10 * i );  
   }  
  
   cout << "The list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
  
   // Using the template version to insert an element  
   insert_iterator<list <int> > Iter( L, L.begin ( ) );  
 *Iter = 1;  
  
   // Alternatively, using the member function to insert an element  
   inserter ( L, L.end ( ) ) = 500;  
  
   cout << "After the insertions, the list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The list L is:  
 ( 20 30 40 ).  
After the insertions, the list L is:  
 ( 1 20 30 40 500 ).  
```  
  
##  <a name="a-namemakecheckedarrayiteratora--makecheckedarrayiterator"></a><a name="make_checked_array_iterator"></a>  make_checked_array_iterator  
 Crea un [checked_array_iterator](../standard-library/checked-array-iterator-class.md) que pueden usar otros algoritmos.  
  
> [!NOTE]
>  Esta función es una extensión de Microsoft de la biblioteca estándar de C++. El código implementado mediante esta función no es portable a los entornos de compilación estándar de C++ que no admiten esta extensión de Microsoft.  
  
```  
template <class Iter>  
checked_array_iterator<Iter> 
    make_checked_array_iterator(
 Iter Ptr,  
    size_t Size,  
    size_t Index = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `Ptr`  
 Puntero a la matriz de destino.  
  
 `Size`  
 Tamaño de la matriz de destino.  
  
 `Index`  
 Índice opcional en la matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 Instancia de `checked_array_iterator`.  
  
### <a name="remarks"></a>Comentarios  
 La función `make_checked_array_iterator` se define en el espacio de nombres `stdext`.  
  
 Esta función toma un puntero sin formato (que normalmente causaría preocupación sobre la saturación de los límites) y lo encapsula en una clase [checked_array_iterator](../standard-library/checked-array-iterator-class.md) que hace la comprobación. Debido a que esa clase se marca como activada, la biblioteca estándar de C++ no advierte sobre ella. Para obtener más información y ejemplos de código, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Ejemplo  
  En el ejemplo siguiente, se crea un [vector](../standard-library/vector-class.md) y se rellena con 10 elementos. El contenido del vector se copia en una matriz utilizando el algoritmo de copia y, a continuación, se usa `make_checked_array_iterator` para especificar el destino. Esto va seguido de una infracción intencionada de la comprobación de límites de forma que se desencadena un error de aserción de depuración.  
  
```cpp  
// make_checked_array_iterator.cpp  
// compile with: /EHsc /W4 /MTd  
  
#include <algorithm>  
#include <iterator> // stdext::make_checked_array_iterator  
#include <memory> // std::make_unique  
#include <iostream>  
#include <vector>  
#include <string>  
  
using namespace std;  
  
template <typename C> void print(const string& s, const C& c) {  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    const size_t dest_size = 10;  
    // Old-school but not exception safe, favor make_unique<int[]>  
    // int* dest = new int[dest_size];  
    unique_ptr<int[]> updest = make_unique<int[]>(dest_size);  
    int* dest = updest.get(); // get a raw pointer for the demo  
  
    vector<int> v;  
  
    for (int i = 0; i < dest_size; ++i) {  
        v.push_back(i);  
    }  
    print("vector v: ", v);  
  
    copy(v.begin(), v.end(), stdext::make_checked_array_iterator(dest, dest_size));  
  
    cout << "int array dest: ";  
    for (int i = 0; i < dest_size; ++i) {  
        cout << dest[i] << " ";  
    }  
    cout << endl;  
  
    // Add another element to the vector to force an overrun.  
    v.push_back(10);  
    // The next line causes a debug assertion when it executes.  
    copy(v.begin(), v.end(), stdext::make_checked_array_iterator(dest, dest_size));  
}  
  
```  
  
##  <a name="a-namemakemoveiteratora--makemoveiterator"></a><a name="make_move_iterator"></a>  make_move_iterator  
 Crea un `move iterator` que contiene el iterador proporcionado como el iterador `stored`.  
  
```  
template <class Iterator>  
move_iterator<Iterator>  
make_move_iterator(const Iterator& _It);
```  
  
### <a name="parameters"></a>Parámetros  
 `_It`  
 Iterador almacenado en el nuevo iterador de movimiento.  
  
### <a name="remarks"></a>Comentarios  
 La función de plantilla devuelve `move_iterator``<Iterator>(``_It``)`.  
  
##  <a name="a-namemakeuncheckedarrayiteratora--makeuncheckedarrayiterator"></a><a name="make_unchecked_array_iterator"></a>  make_unchecked_array_iterator  
 Crea un [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md) que pueden usar otros algoritmos.  
  
> [!NOTE]
>  Esta función es una extensión de Microsoft de la biblioteca estándar de C++. El código implementado mediante esta función no es portable a los entornos de compilación estándar de C++ que no admiten esta extensión de Microsoft.  
  
```  
template <class Iter>  
unchecked_array_iterator<Iter> 
    make_unchecked_array_iterator(Iter Ptr);
```  
  
### <a name="parameters"></a>Parámetros  
 `Ptr`  
 Puntero a la matriz de destino.  
  
### <a name="return-value"></a>Valor devuelto  
 Instancia de `unchecked_array_iterator`.  
  
### <a name="remarks"></a>Comentarios  
 La función `make_unchecked_array_iterator` se define en el espacio de nombres `stdext`.  
  
 Esta función toma un puntero sin formato y lo encapsula en una clase que no realiza ninguna comprobación y por tanto no optimiza nada, pero también silencia las advertencias del compilador como [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Por tanto, es una manera dirigida de tratar las advertencias de puntero no comprobadas sin silenciarlas de forma global o incurrir en el costo de comprobación. Para obtener más información y ejemplos de código, vea [Iteradores comprobados](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Ejemplo  
  En el ejemplo siguiente, se crea un [vector](../standard-library/vector-class.md) y se rellena con 10 elementos. El contenido del vector se copia en una matriz utilizando el algoritmo de copia y, a continuación, se usa `make_unchecked_array_iterator` para especificar el destino.  
  
```cpp  
// make_unchecked_array_iterator.cpp  
// compile with: /EHsc /W4 /MTd  
  
#include <algorithm>  
#include <iterator> // stdext::make_unchecked_array_iterator  
#include <iostream>  
#include <vector>  
#include <string>  
  
using namespace std;  
  
template <typename C> void print(const string& s, const C& c) {  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    const size_t dest_size = 10;  
    int *dest = new int[dest_size];  
    vector<int> v;  
  
    for (int i = 0; i < dest_size; ++i) {  
        v.push_back(i);  
    }  
    print("vector v: ", v);  
  
    // COMPILER WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode  
    // (it performs no checking, so an overrun will trigger undefined behavior)  
    copy(v.begin(), v.end(), stdext::make_unchecked_array_iterator(dest));  
  
    cout << "int array dest: ";  
    for (int i = 0; i < dest_size; ++i) {  
        cout << dest[i] << " ";  
    }  
    cout << endl;  
  
    delete[] dest;  
}  
  
```  
  
##  <a name="a-namenexta--next"></a><a name="next"></a>  next  
 Procesa una iteración un número especificado de veces y devuelve la nueva posición del iterador.  
  
```  
template <class InputIterator>  
InputIterator next(
    InputIterator first,  
    typename iterator_traits<InputIterator>::difference_type _Off = 1);
```  
  
### <a name="parameters"></a>Parámetros  
 ` first`  
 Posición actual.  
  
 `_Off`  
 Número de veces que se va a iterar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la posición del nuevo iterador después de iterar `_Off` veces.  
  
### <a name="remarks"></a>Comentarios  
 La función de plantilla devuelve `next` incrementado `_Off` veces  
  
##  <a name="a-namepreva--prev"></a><a name="prev"></a>  prev  
 Procesa una iteración en dirección inversa un número especificado de veces y devuelve la nueva posición del iterador.  
  
```  
template <class BidirectionalIterator>  
BidirectionalIterator prev(
    BidirectionalIterator first,  
    typename iterator_traits<BidirectionalIterator>::difference_type _Off = 1);
```  
  
### <a name="parameters"></a>Parámetros  
 ` first`  
 Posición actual.  
  
 `_Off`  
 Número de veces que se va a iterar.  
  
### <a name="remarks"></a>Comentarios  
 La función de plantilla devuelve `next` reducido `off` veces.  
  
## <a name="see-also"></a>Vea también  
 [\<iterator>](../standard-library/iterator.md)


