---
title: "deque (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.deque"
  - "deque"
  - "std::deque"
  - "deque/std::deque"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "deque (clase), acerca de la clase deque"
  - "deque (clase)"
ms.assetid: 64842ee5-057a-4063-8c16-4267a0332584
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# deque (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Organiza los elementos de un tipo determinado en una organización lineal y, como un vector, permite un acceso aleatorio rápido a cualquier elemento y, una inserción y eliminación eficaces al final del contenedor. Sin embargo, a diferencia de un vector, la clase `deque` también admite la inserción y la eliminación eficaces al principio del contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```unstlib  
template <class Type,   
    class Allocator =allocator<Type>>  
class deque  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Type`  
 Tipo de datos de elementos que se va a almacenar en deque.  
  
 `Allocator`  
 Tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria de deque. Este argumento es opcional y el valor predeterminado es **allocator \< tipo>***.*  
  
## <a name="remarks"></a>Comentarios  
 En general, la elección del tipo de contenedor se debe tomar según el tipo de búsqueda y de inserción que necesite la aplicación. [Vectores](vector%20Class.md) debe ser el contenedor preferido para administrar una secuencia cuando el acceso aleatorio a cualquier elemento sea importante y las inserciones o eliminaciones de elementos sólo son necesarias al final de una secuencia. El rendimiento del contenedor de lista es superior al eficaz inserciones y eliminaciones (tiempo constante) en cualquier ubicación dentro de la secuencia es importante. Esas operaciones en medio de la secuencia requieren copias y asignaciones de elementos proporcionales al número de elementos de la secuencia (tiempo lineal).  
  
 La reasignación de deque se realiza cuando una función miembro debe insertar o borrar elementos de la secuencia:  
  
-   Si se inserta un elemento en una secuencia vacía, o si un elemento se borra para dejar una secuencia vacía, los iteradores anteriores devueltos por [comenzar](#deque__begin) y [final](#deque__end) dejan de ser válidos.  
  
-   Si se inserta un elemento en la primera posición del deque, todos los iteradores, pero ninguna referencia, que designan elementos existentes dejan de ser válidos.  
  
-   Si un elemento se inserta al final del deque, [end](#deque__end) todos los iteradores, pero ninguna referencia, que designa elementos existentes dejan de ser válidos.  
  
-   Si se borra un elemento al principio del deque, solo el iterador y las referencias al elemento borrado dejan de ser válidos.  
  
-   Si se borra el último elemento del final del deque, solo el iterador al elemento final y las referencias al elemento borrado dejan de ser válidos.  
  
 De lo contrario, al insertar o borrar un elemento se invalidan todos los iteradores y referencias.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[deque](#deque__deque)|Construye un `deque.` se proporcionan varios constructores para configurar el contenido del nuevo `deque` de maneras diferentes: vacío; cargado con un número especificado de elementos vacíos; contenido movido o copiado de otro `deque`; contenido copiado o movido mediante un iterador; y un elemento copiado en el `deque`` count` veces. Algunos de los constructores permiten usar un `allocator` personalizado para crear elementos.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#deque__allocator_type)|Tipo que representa la clase `allocator` para el objeto `deque`.|  
|[const_iterator](#deque__const_iterator)|Tipo que proporciona un iterador de acceso aleatorio que puede obtener acceso a elementos de `deque` como `const` y leerlos.|  
|[const_pointer](#deque__const_pointer)|Tipo que proporciona un puntero a un elemento de `deque` como `const.`|  
|[const_reference](#deque__const_reference)|Tipo que proporciona una referencia a un elemento de `deque` para operaciones de lectura y de otro tipo como `const.`|  
|[const_reverse_iterator](#deque__const_reverse_iterator)|Tipo que proporciona un iterador de acceso aleatorio que puede obtener acceso a elementos del `deque` como `const` y leerlos. El deque se ve en orden inverso. Para obtener más información, consulte [reverse_iterator (clase)](../standard-library/reverse-iterator-class.md)|  
|[difference_type](#deque__difference_type)|Tipo que proporciona la diferencia entre dos iteradores de acceso aleatorio que hacen referencia a elementos del mismo `deque`.|  
|[iterador](#deque__iterator)|Tipo que proporciona un iterador de acceso aleatorio que puede leer o modificar cualquier elemento de `deque`.|  
|[puntero](#deque__pointer)|Tipo que proporciona un puntero a un elemento de `deque`.|  
|[referencia](#deque__reference)|Tipo que proporciona una referencia a un elemento almacenado en un `deque`.|  
|[reverse_iterator](#deque__reverse_iterator)|Tipo que proporciona un iterador de acceso aleatorio que puede leer o modificar un elemento de `deque`. El deque se ve en orden inverso.|  
|[size_type](#deque__size_type)|Tipo que cuenta el número de elementos de un `deque`.|  
|[value_type](#deque__value_type)|Tipo que representa el tipo de datos almacenados en un `deque`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[asignar](#deque__assign)|Borra elementos de un `deque` y copia una nueva secuencia de elementos al `deque` de destino.|  
|[en](#deque__at)|Devuelve una referencia al elemento situado en una ubicación especificada del `deque`.|  
|[Atrás](#deque__back)|Devuelve una referencia al último elemento del `deque`.|  
|[comenzar](#deque__begin)|Devuelve un iterador de acceso aleatorio que direcciona el primer elemento del `deque`.|  
|[deque:: cbegin](#deque__cbegin)|Devuelve un iterador constante al primer elemento del `deque`.|  
|[deque:: cend](#deque__cend)|Devuelve un iterador `const` de acceso aleatorio que apunta justo después del final del `deque`.|  
|[Borrar](#deque__clear)|Borra todos los elementos de un `deque`.|  
|[deque:: crbegin](#deque__crbegin)|Devuelve un iterador constante de acceso aleatorio al primer elemento de `deque` que se ve en orden inverso.|  
|[deque:: crend](#deque__crend)|Devuelve un iterador constante de acceso aleatorio al primer elemento de `deque` que se ve en orden inverso.|  
|[deque:: emplace](#deque__emplace)|Inserta en una posición especificada del `deque` un elemento construido en contexto.|  
|[deque:: emplace_back](#deque__emplace_back)|Agrega un elemento construido en contexto al final del `deque`.|  
|[deque:: emplace_front](#deque__emplace_front)|Agrega un elemento construido en contexto al principio del `deque`.|  
|[vacía](#deque__empty)|Devuelve `true` si el `deque` contiene cero elementos y `false` si contiene uno o más elementos.|  
|[final](#deque__end)|Devuelve un iterador de acceso aleatorio que apunta justo después del final del `deque`.|  
|[Borrar](#deque__erase)|Quita un elemento o un intervalo de elementos de un `deque` de las posiciones especificadas.|  
|[parte frontal](#deque__front)|Devuelve una referencia al primer elemento de `deque`.|  
|[get_allocator](#deque__get_allocator)|Devuelve una copia del objeto `allocator` utilizado para construir el `deque`.|  
|[Insertar](#deque__insert)|Inserta un elemento, varios elementos o un intervalo de elementos en una posición especificada del `deque`.|  
|[max_size](#deque__max_size)|Devuelve la longitud máxima posible del `deque`.|  
|[pop_back](#deque__pop_back)|Borra el elemento situado al final del `deque`.|  
|[pop_front](#deque__pop_front)|Borra el elemento situado al principio del `deque`.|  
|[push_back](#deque__push_back)|Agrega un elemento al final del `deque`.|  
|[push_front](#deque__push_front)|Agrega un elemento al principio del `deque`.|  
|[rbegin](#deque__rbegin)|Devuelve un iterador de acceso aleatorio al primer elemento de `deque` invertido.|  
|[rend](#deque__rend)|Devuelve un iterador de acceso aleatorio que apunta justo detrás del último elemento de `deque` invertido.|  
|[cambiar el tamaño](#deque__resize)|Especifica un nuevo tamaño para un `deque`.|  
|[deque:: shrink_to_fit](#deque__shrink_to_fit)|Descarta el exceso de capacidad.|  
|[tamaño](#deque__size)|Devuelve el número de elementos de `deque`.|  
|[intercambio](#deque__swap)|Intercambia los elementos de dos `deque`.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operador &#91; &#93;](#deque__operator_at)|Devuelve una referencia al elemento del `deque` en una posición especificada.|  
|[deque:: operator =](#deque__operator_eq)|Reemplaza los elementos del `deque` con una copia de otro `deque`.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado**: \< deque>  
  
##  <a name="a-namedequeallocatortypea-dequeallocatortype"></a><a name="deque__allocator_type"></a>  deque:: allocator_type  
 Tipo que representa la clase de asignador del objeto deque.  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 **allocator_type** es un sinónimo del parámetro de plantilla **asignador**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [get_allocator](#deque__get_allocator).  
  
##  <a name="a-namedequeassigna-dequeassign"></a><a name="deque__assign"></a>  deque  
 Borra elementos de un deque y copia un nuevo conjunto de elementos en el deque de destino.  
  
```  
template <class InputIterator>  
void assign(
    InputIterator First,  
    InputIterator Last);

void assign(
    size_type Count,  
    const Type& Val);

void assign(
    initializer_list<Type>  
IList);
```  
  
### <a name="parameters"></a>Parámetros  
 `First`  
 Posición del primer elemento en el intervalo de elementos que se va a copiar del argumento deque.  
  
 `Last`  
 Posición del primer elemento que se encuentra más allá del intervalo de elementos que se va a copiar del argumento deque.  
  
 `Count`  
 Número de copias de un elemento que se va a insertar en el deque.  
  
 `Val`  
 Valor del elemento que se va a insertar en el deque.  
  
 `IList`  
 initializer_list que se va a insertar en el deque.  
  
### <a name="remarks"></a>Comentarios  
 Después de borrar los elementos existentes en el deque de destino, `assign` inserta un intervalo especificado de elementos del deque original o de otro deque en el deque de destino, o inserta copias de un nuevo elemento de un valor especificado en el deque de destino.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_assign.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
#include <initializer_list>  
  
int main()  
{  
    using namespace std;  
    deque <int> c1, c2;  
    deque <int>::const_iterator cIter;  
  
    c1.push_back(10);  
    c1.push_back(20);  
    c1.push_back(30);  
    c2.push_back(40);  
    c2.push_back(50);  
    c2.push_back(60);  
  
    deque<int> d1{ 1, 2, 3, 4 };  
    initializer_list<int> iList{ 5, 6, 7, 8 };  
    d1.assign(iList);  
  
    cout << "d1 = ";  
    for (int i : d1)  
        cout << i;  
    cout << endl;  
  
    cout << "c1 =";  
    for (int i : c1)  
        cout << i;  
    cout << endl;  
  
    c1.assign(++c2.begin(), c2.end());  
    cout << "c1 =";  
    for (int i : c1)  
        cout << i;  
    cout << endl;  
  
    c1.assign(7, 4);  
    cout << "c1 =";  
    for (int i : c1)  
        cout << i;  
    cout << endl;  
  
}  
  
```  
  
```Output  
d1 = 5678c1 =102030c1 =5060c1 =4444444  
```  
  
##  <a name="a-namedequeata-dequeat"></a><a name="deque__at"></a>  deque:: AT  
 Devuelve una referencia al elemento en una ubicación especificada en el deque.  
  
```  
reference at(size_type _Pos);

const_reference at(size_type _Pos) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Pos`  
 El subíndice o número de posición del elemento hacer referencia en el deque.  
  
### <a name="return-value"></a>Valor devuelto  
 Si `_Pos` es mayor que el tamaño del deque, **en** produce una excepción.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el valor devuelto de **en** se asigna a un `const_reference`, no se puede modificar el objeto de deque. Si el valor devuelto de **en** se asigna a un **referencia**, el objeto deque se puede modificar.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_at.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
  
   const int& i = c1.at( 0 );  
   int& j = c1.at( 1 );  
   cout << "The first element is " << i << endl;  
   cout << "The second element is " << j << endl;  
}  
```  
  
```Output  
The first element is 10  
The second element is 20  
```  
  
##  <a name="a-namedequebacka-dequeback"></a><a name="deque__back"></a>  deque:: back  
 Devuelve una referencia al último elemento de deque.  
  
```  
reference back();

const_reference back() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El último elemento de deque. Si el deque está vacío, el valor devuelto es indefinido.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor devuelto de **volver** se asigna a un `const_reference`, no se puede modificar el objeto de deque. Si el valor devuelto de **volver** se asigna a un **referencia**, el objeto deque se puede modificar.  
  
 Al compilar con _SECURE_SCL 1, se producirá un error de tiempo de ejecución si se intenta tener acceso a un elemento de un deque vacío.  Vea [Checked Iterators](../standard-library/checked-iterators.md) para obtener más información.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_back.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 11 );  
  
   int& i = c1.back( );  
   const int& ii = c1.front( );  
  
   cout << "The last integer of c1 is " << i << endl;  
   i--;  
   cout << "The next-to-last integer of c1 is " << ii << endl;  
}  
```  
  
```Output  
The last integer of c1 is 11  
The next-to-last integer of c1 is 10  
```  
  
##  <a name="a-namedequebegina-dequebegin"></a><a name="deque__begin"></a>  deque:: begin  
 Devuelve un iterador que direcciona el primer elemento de deque.  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador de acceso aleatorio que direcciona el primer elemento del deque o a la ubicación que sigue un deque vacío.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor devuelto de **comenzar** se asigna a un `const_iterator`, no se puede modificar el objeto de deque. Si el valor devuelto de **comenzar** se asigna a un **iterador**, el objeto deque se puede modificar.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_begin.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::iterator c1_Iter;  
   deque <int>::const_iterator c1_cIter;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
  
   c1_Iter = c1.begin( );  
   cout << "The first element of c1 is " << *c1_Iter << endl;  
  
 *c1_Iter = 20;  
   c1_Iter = c1.begin( );  
   cout << "The first element of c1 is now " << *c1_Iter << endl;  
  
   // The following line would be an error because iterator is const  
   // *c1_cIter = 200;  
}  
```  
  
```Output  
The first element of c1 is 1  
The first element of c1 is now 20  
```  
  
##  <a name="a-namedequecbegina-dequecbegin"></a><a name="deque__cbegin"></a>  deque:: cbegin  
 Devuelve un iterador `const` que direcciona el primer elemento del intervalo.  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador `const` de acceso aleatorio que apunta al primer elemento del intervalo o la ubicación situada más allá del final de un intervalo vacío (para un intervalo vacío, `cbegin() == cend()`).  
  
### <a name="remarks"></a>Comentarios  
 Con el valor devuelto de `cbegin`, los elementos del intervalo no se pueden modificar.  
  
 Se puede usar esta función miembro en lugar de la función miembro `begin()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se utiliza junto con la [automática](../cpp/auto-cpp.md) Escriba la palabra clave de deducción, tal como se muestra en el ejemplo siguiente. En el ejemplo, considere la posibilidad de `Container` sea un modificable (no - `const`) contenedor de cualquier naturaleza que admite `begin()` y `cbegin()`.  
  
```cpp  
 
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="a-namedequecenda-dequecend"></a><a name="deque__cend"></a>  deque:: cend  
 Devuelve un iterador `const` que direcciona la ubicación situada más allá del último elemento de un intervalo.  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador de acceso aleatorio que apunta justo después del final del intervalo.  
  
### <a name="remarks"></a>Comentarios  
 `cend` se usa para probar si un iterador ha sobrepasado el final de su intervalo.  
  
 Se puede usar esta función miembro en lugar de la función miembro `end()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se utiliza junto con la [automática](../cpp/auto-cpp.md) Escriba la palabra clave de deducción, tal como se muestra en el ejemplo siguiente. En el ejemplo, considere la posibilidad de `Container` sea un modificable (no - `const`) contenedor de cualquier naturaleza que admite `end()` y `cend()`.  
  
```cpp  
 
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
 El valor devuelto por `cend` no se debe desreferenciar.  
  
##  <a name="a-namedequecleara-dequeclear"></a><a name="deque__clear"></a>  deque:: Clear  
 Borra todos los elementos de un deque.  
  
```  
void clear();
```  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_clear.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   cout << "The size of the deque is initially " << c1.size( ) << endl;  
   c1.clear( );  
   cout << "The size of the deque after clearing is " << c1.size( ) << endl;  
}  
```  
  
```Output  
The size of the deque is initially 3  
The size of the deque after clearing is 0  
```  
  
##  <a name="a-namedequeconstiteratora-dequeconstiterator"></a><a name="deque__const_iterator"></a>  deque:: const_iterator  
 Un tipo que proporciona un iterador de acceso aleatorio que puede obtener acceso y leer un **const** elemento de deque.  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `const_iterator` no se puede utilizar para modificar el valor de un elemento.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [volver](#deque__back).  
  
##  <a name="a-namedequeconstpointera-dequeconstpointer"></a><a name="deque__const_pointer"></a>  deque:: const_pointer  
 Proporciona un puntero a un elemento `const` de un deque.  
  
```unstlib  
typedef typename Allocator::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `const_pointer` no se puede utilizar para modificar el valor de un elemento. Un [iterador](#deque__iterator) se utiliza normalmente para tener acceso a un elemento de deque.  
  
##  <a name="a-namedequeconstreferencea-dequeconstreference"></a><a name="deque__const_reference"></a>  deque:: const_reference  
 Un tipo que proporciona una referencia a un **const** elemento almacenado en un deque para leer y realizar **const** operaciones.  
  
```  
typedef typename Allocator::const_reference const_reference;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `const_reference` no se puede utilizar para modificar el valor de un elemento.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_const_ref.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
  
   const deque <int> c2 = c1;  
   const int &i = c2.front( );  
   const int &j = c2.back( );  
   cout << "The first element is " << i << endl;  
   cout << "The second element is " << j << endl;  
  
   // The following line would cause an error as c2 is const  
   // c2.push_back( 30 );  
}  
```  
  
```Output  
The first element is 10  
The second element is 20  
```  
  
##  <a name="a-namedequeconstreverseiteratora-dequeconstreverseiterator"></a><a name="deque__const_reverse_iterator"></a>  deque:: const_reverse_iterator  
 Un tipo que proporciona un iterador de acceso aleatorio que puede lee cualquier **const** elemento de deque.  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo de `const_reverse_iterator` no se puede modificar el valor de un elemento y se utiliza para recorrer en iteración el deque en orden inverso.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [rbegin](#deque__rbegin) para obtener un ejemplo de cómo declarar y usar un iterador.  
  
##  <a name="a-namedequecrbegina-dequecrbegin"></a><a name="deque__crbegin"></a>  deque:: crbegin  
 Devuelve un iterador constante al primer elemento de un deque invertido.  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Const reverse de iterador de acceso aleatorio que direcciona el primer elemento en invertido [deque](../standard-library/deque-class.md) o direccionamiento lo que habría sido el último elemento de la irreversible `deque`.  
  
### <a name="remarks"></a>Comentarios  
 Con el valor devuelto de `crbegin`, el objeto `deque` no se puede modificar.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_crbegin.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
   deque <int>::iterator v1_Iter;  
   deque <int>::const_reverse_iterator v1_rIter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
  
   v1_Iter = v1.begin( );  
   cout << "The first element of deque is "  
        << *v1_Iter << "." << endl;  
  
   v1_rIter = v1.crbegin( );  
   cout << "The first element of the reversed deque is "  
        << *v1_rIter << "." << endl;  
}  
```  
  
```Output  
The first element of deque is 1.  
The first element of the reversed deque is 2.  
```  
  
##  <a name="a-namedequecrenda-dequecrend"></a><a name="deque__crend"></a>  deque:: crend  
 Devuelve un iterador const que direcciona la ubicación del último elemento de un deque invertido.  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Const reverse de iterador de acceso aleatorio que direcciona la ubicación del último elemento de invertido [deque](../standard-library/deque-class.md) (la ubicación que había precedido al primer elemento de deque sin invertir).  
  
### <a name="remarks"></a>Comentarios  
 `crend` se utiliza con invertido `deque` como [array::cend](../standard-library/array-class-stl.md#array__cend) se usa con un `deque`.  
  
 Con el valor devuelto de `crend` (convenientemente reduce) el `deque` no se puede modificar el objeto.  
  
 `crend` puede utilizarse para probar si un iterador inverso llegó al final de su deque.  
  
 El valor devuelto por `crend` no se debe desreferenciar.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_crend.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
   deque <int>::const_reverse_iterator v1_rIter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
  
   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )  
      cout << *v1_rIter << endl;  
}  
```  
  
```Output  
2  
1  
```  
  
##  <a name="a-namedequedequea-dequedeque"></a><a name="deque__deque"></a>  deque:: deque  
 Construye un deque de un tamaño específico, con elementos de un valor específico, con un asignador específico o como una copia de todo o de parte de otro deque.  
  
```  
deque();

explicit deque(
    const Allocator& Al);

explicit deque(
    size_type Count);

deque(
    size_type Count,  
    const Type& Val);

deque(
    size_type Count,  
    const Type& Val,  
    const Allocator& Al);

deque(
    const deque& Right);

template <class InputIterator>  
deque(
 InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
deque(
 InputIterator First,  
    InputIterator Last,  
    const Allocator& Al);

deque(
    initializer_list<value_type>  
IList,  
    const Allocator& Al);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`Al`|La clase de asignador que se usa con este objeto.|  
|`Count`|Número de elementos del deque construido.|  
|`Val`|Valor de los elementos del deque construido.|  
|`Right`|Deque del cual el deque construido va a ser una copia.|  
|`First`|Posición del primer elemento en el intervalo de elementos que se va a copiar.|  
|`Last`|Posición del primer elemento más allá del intervalo de elementos que se va a copiar.|  
|`IList`|initializer_list que se va a copiar.|  
  
### <a name="remarks"></a>Comentarios  
 Todos los constructores almacenan un objeto de asignador ( `Al`) e inicializan el deque.  
  
 Los dos primeros constructores especifican un deque inicial vacío; el segundo especifica también el tipo de asignador ( `_Al`) que se utilizará.  
  
 El tercer constructor especifica una repetición de un número especificado ( ` count`) de los elementos del valor predeterminado para la clase `Type`.  
  
 Los constructores cuarto y quinto especifican una repetición de ( `Count`) elementos de valor ` val`.  
  
 El sexto constructor especifica una copia del deque `Right`.  
  
 Los constructores séptimo y octavo copian el intervalo `[First, Last)` de un deque.  
  
 El séptimo constructor mueve el deque `Right`.  
  
 El octavo constructor copia el contenido de una initializer_list.  
  
 Ninguno de los constructores realiza ninguna reasignación provisional.  
  
### <a name="example"></a>Ejemplo  
  
```  
/ compile with: /EHsc  
#include <deque>  
#include <iostream>  
#include <forward_list>  
  
int main()  
{  
    using namespace std;  
  
    forward_list<int> f1{ 1, 2, 3, 4 };  
  
    f1.insert_after(f1.begin(), { 5, 6, 7, 8 });  
  
    deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;  
  
    // Create an empty deque c0  
    deque <int> c0;  
  
    // Create a deque c1 with 3 elements of default value 0  
    deque <int> c1(3);  
  
    // Create a deque c2 with 5 elements of value 2  
    deque <int> c2(5, 2);  
  
    // Create a deque c3 with 3 elements of value 1 and with the   
    // allocator of deque c2  
    deque <int> c3(3, 1, c2.get_allocator());  
  
    // Create a copy, deque c4, of deque c2  
    deque <int> c4(c2);  
  
    // Create a deque c5 by copying the range c4[ first,  last)  
    c4_Iter = c4.begin();  
    c4_Iter++;  
    c4_Iter++;  
    deque <int> c5(c4.begin(), c4_Iter);  
  
    // Create a deque c6 by copying the range c4[ first,  last) and   
    // c2 with the allocator of deque  
    c4_Iter = c4.begin();  
    c4_Iter++;  
    c4_Iter++;  
    c4_Iter++;  
    deque <int> c6(c4.begin(), c4_Iter, c2.get_allocator());  
  
    // Create a deque c8 by copying the contents of an initializer_list  
    // using brace initialization  
    deque<int> c8({ 1, 2, 3, 4 });  
  
    initializer_list<int> iList{ 5, 6, 7, 8 };  
    deque<int> c9( iList);  
  
    cout << "c1 = ";  
    for (int i : c1)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c2 = ";  
    for (int i : c2)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c3 = ";  
    for (int i : c3)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c4 = ";  
    for (int i : c4)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c5 = ";  
    for (int i : c5)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c6 = ";  
    for (int i : c6)  
        cout << i << " ";  
    cout << endl;  
  
    // Move deque c6 to deque c7  
    deque <int> c7(move(c6));  
    deque <int>::iterator c7_Iter;  
  
    cout << "c7 =";  
    for (int i : c7)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c8 = ";  
    for (int i : c8)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c9 = ";  
    for (int i : c9)  
        cout << i << " ";  
    cout << endl;  
  
    int x = 3;  
}  
// deque_deque.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
    using namespace std;  
   deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;  
  
    // Create an empty deque c0  
    deque <int> c0;  
  
    // Create a deque c1 with 3 elements of default value 0  
    deque <int> c1( 3 );  
  
    // Create a deque c2 with 5 elements of value 2  
    deque <int> c2( 5, 2 );  
  
    // Create a deque c3 with 3 elements of value 1 and with the   
    // allocator of deque c2  
    deque <int> c3( 3, 1, c2.get_allocator( ) );  
  
    // Create a copy, deque c4, of deque c2  
    deque <int> c4( c2 );  
  
    // Create a deque c5 by copying the range c4[ first,  last)  
    c4_Iter = c4.begin( );  
    c4_Iter++;  
    c4_Iter++;  
    deque <int> c5( c4.begin( ), c4_Iter );  
  
    // Create a deque c6 by copying the range c4[ first,  last) and   
    // c2 with the allocator of deque  
    c4_Iter = c4.begin( );  
   c4_Iter++;  
   c4_Iter++;  
   c4_Iter++;  
   deque <int> c6( c4.begin( ), c4_Iter, c2.get_allocator( ) );  
  
    // Create a deque c8 by copying the contents of an initializer_list  
    // using brace initialization  
    deque<int> c8({ 1, 2, 3, 4 });  
  
        initializer_list<int> iList{ 5, 6, 7, 8 };  
    deque<int> c9( iList);  
  
    cout << "c1 = ";  
    for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
        cout << *c1_Iter << " ";  
    cout << endl;  
  
    cout << "c2 = ";  
    for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )  
        cout << *c2_Iter << " ";  
    cout << endl;  
  
    cout << "c3 = ";  
    for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )  
        cout << *c3_Iter << " ";  
    cout << endl;  
  
    cout << "c4 = ";  
    for ( c4_Iter = c4.begin( ); c4_Iter != c4.end( ); c4_Iter++ )  
        cout << *c4_Iter << " ";  
    cout << endl;  
  
    cout << "c5 = ";  
    for ( c5_Iter = c5.begin( ); c5_Iter != c5.end( ); c5_Iter++ )  
        cout << *c5_Iter << " ";  
    cout << endl;  
  
    cout << "c6 = ";  
    for ( c6_Iter = c6.begin( ); c6_Iter != c6.end( ); c6_Iter++ )  
        cout << *c6_Iter << " ";  
    cout << endl;  
  
    // Move deque c6 to deque c7  
    deque <int> c7( move(c6) );  
    deque <int>::iterator c7_Iter;  
  
    cout << "c7 =" ;  
    for ( c7_Iter = c7.begin( ) ; c7_Iter != c7.end( ) ; c7_Iter++ )  
        cout << " " << *c7_Iter;  
    cout << endl;  
  
    cout << "c8 = ";  
    for (int i : c8)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c9 = ";  
    or (int i : c9)  
        cout << i << " ";  
    cout << endl;  
}  
```  
  
##  <a name="a-namedequedifferencetypea-dequedifferencetype"></a><a name="deque__difference_type"></a>  deque:: difference_type  
 Un tipo que proporciona la diferencia entre dos iteradores que hacen referencia a elementos dentro del mismo deque.  
  
```  
typedef typename Allocator::difference_type difference_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un `difference_type` también se puede describir como el número de elementos entre dos punteros.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <deque>  
#include <algorithm>  
  
int main( )   
{  
   using namespace std;  
  
   deque <int> c1;  
   deque <int>::iterator c1_Iter, c2_Iter;  
  
   c1.push_back( 30 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
   c1.push_back( 10 );  
   c1.push_back( 30 );  
   c1.push_back( 20 );  
  
   c1_Iter = c1.begin( );  
   c2_Iter = c1.end( );  
  
   deque <int>::difference_type df_typ1, df_typ2, df_typ3;  
  
   df_typ1 = count( c1_Iter, c2_Iter, 10 );  
   df_typ2 = count( c1_Iter, c2_Iter, 20 );  
   df_typ3 = count( c1_Iter, c2_Iter, 30 );  
   cout << "The number '10' is in c1 collection " << df_typ1 << " times.\n";  
   cout << "The number '20' is in c1 collection " << df_typ2 << " times.\n";  
   cout << "The number '30' is in c1 collection " << df_typ3 << " times.\n";  
}  
```  
  
```Output  
The number '10' is in c1 collection 1 times.  
The number '20' is in c1 collection 2 times.  
The number '30' is in c1 collection 3 times.  
```  
  
##  <a name="a-namedequeemplacea-dequeemplace"></a><a name="deque__emplace"></a>  deque:: emplace  
 Inserta un elemento construido en contexto en el deque en una posición especificada.  
  
```  
iterator emplace(
    const_iterator _Where,  
    Type&& val);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`_Where`|La posición en la [deque](../standard-library/deque-class.md) donde se inserta el primer elemento.|  
|` val`|Valor del elemento insertado en el `deque`.|  
  
### <a name="return-value"></a>Valor devuelto  
 La función devuelve un iterador que apunta a la posición donde se insertó el nuevo elemento en el deque.  
  
### <a name="remarks"></a>Comentarios  
 Las operaciones de inserción pueden ser costosas, consulte `deque` para obtener una explicación de `deque` rendimiento.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_emplace.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
   deque <int>::iterator Iter;  
  
   v1.push_back( 10 );  
   v1.push_back( 20 );  
   v1.push_back( 30 );  
  
   cout << "v1 =" ;  
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
  
// initialize a deque of deques by moving v1  
   deque < deque <int> > vv1;  
  
   vv1.emplace( vv1.begin(), move( v1 ) );  
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )  
      {  
      cout << "vv1[0] =";  
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )  
         cout << " " << *Iter;  
      cout << endl;  
      }  
}  
```  
  
```Output  
v1 = 10 20 30  
vv1[0] = 10 20 30  
```  
  
##  <a name="a-namedequeemplacebacka-dequeemplaceback"></a><a name="deque__emplace_back"></a>  deque:: emplace_back  
 Agrega un elemento construido en contexto al final del deque.  
  
```  
void emplace_back(Type&& val);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|` val`|El elemento que se agrega al final de la [deque](../standard-library/deque-class.md).|  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_emplace_back.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
  
   v1.push_back( 1 );  
   if ( v1.size( ) != 0 )  
      cout << "Last element: " << v1.back( ) << endl;  
  
   v1.push_back( 2 );  
   if ( v1.size( ) != 0 )  
      cout << "New last element: " << v1.back( ) << endl;  
  
// initialize a deque of deques by moving v1  
   deque < deque <int> > vv1;  
  
   vv1.emplace_back( move( v1 ) );  
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )  
      cout << "Moved last element: " << vv1[0].back( ) << endl;  
}  
```  
  
```Output  
Last element: 1  
New last element: 2  
Moved last element: 2  
```  
  
##  <a name="a-namedequeemplacefronta-dequeemplacefront"></a><a name="deque__emplace_front"></a>  deque:: emplace_front  
 Agrega un elemento construido en contexto al final del deque.  
  
```  
void emplace_front(Type&& val);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|` val`|El elemento que se agrega al principio de la [deque](../standard-library/deque-class.md).|  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_emplace_front.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
  
   v1.push_back( 1 );  
   if ( v1.size( ) != 0 )  
      cout << "Last element: " << v1.back( ) << endl;  
  
   v1.push_back( 2 );  
   if ( v1.size( ) != 0 )  
      cout << "New last element: " << v1.back( ) << endl;  
  
// initialize a deque of deques by moving v1  
   deque < deque <int> > vv1;  
  
   vv1.emplace_front( move( v1 ) );  
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )  
      cout << "Moved last element: " << vv1[0].back( ) << endl;  
}  
```  
  
```Output  
Last element: 1  
New last element: 2  
Moved last element: 2  
```  
  
##  <a name="a-namedequeemptya-dequeempty"></a><a name="deque__empty"></a>  deque:: Empty  
 Comprueba si un deque está vacío.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** Si está vacío; deque **false** Si deque no está vacío.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_empty.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   if ( c1.empty( ) )  
      cout << "The deque is empty." << endl;  
   else  
      cout << "The deque is not empty." << endl;  
}  
```  
  
```Output  
The deque is not empty.  
```  
  
##  <a name="a-namedequeenda-dequeend"></a><a name="deque__end"></a>  deque:: end  
 Devuelve un iterador que direcciona la ubicación del último elemento de un deque.  
  
```  
const_iterator end() const;

iterator end();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de acceso aleatorio que direcciona la ubicación del último elemento de un deque. Si el deque está vacío, deque:: end == deque.  
  
### <a name="remarks"></a>Comentarios  
 **end** se utiliza para probar si un iterador ha llegado al final de su deque.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_end.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::iterator c1_Iter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1_Iter = c1.end( );  
   c1_Iter--;  
   cout << "The last integer of c1 is " << *c1_Iter << endl;  
  
   c1_Iter--;  
 *c1_Iter = 400;  
   cout << "The new next-to-last integer of c1 is " << *c1_Iter << endl;  
  
   // If a const iterator had been declared instead with the line:  
   // deque <int>::const_iterator c1_Iter;  
   // an error would have resulted when inserting the 400  
  
   cout << "The deque is now:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
}  
```  
  
```Output  
The last integer of c1 is 30  
The new next-to-last integer of c1 is 400  
The deque is now: 10 400 30  
```  
  
##  <a name="a-namedequeerasea-dequeerase"></a><a name="deque__erase"></a>  deque  
 Quita un elemento o un intervalo de elementos de un deque de las posiciones especificadas.  
  
```  
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Where`  
 Posición del elemento que se va a quitar de deque.  
  
 ` first`  
 Posición del primer elemento se quitará del deque.  
  
 ` last`  
 Posición situada más allá del último elemento que se quitará el deque.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de acceso aleatorio que designa el primer elemento que permanece más allá de los elementos quitados, o un puntero al final del deque si no existe ese elemento.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre **Borrar**, consulte [deque y deque:: clear](../misc/deque-erase-and-deque-clear.md).  
  
 **Borrar** nunca inicia una excepción.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_erase.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::iterator Iter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
   c1.push_back( 40 );  
   c1.push_back( 50 );  
   cout << "The initial deque is: ";  
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )  
      cout << *Iter << " ";  
   cout << endl;  
   c1.erase( c1.begin( ) );  
   cout << "After erasing the first element, the deque becomes:  ";  
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )  
      cout << *Iter << " ";  
   cout << endl;  
   Iter = c1.begin( );  
   Iter++;  
   c1.erase( Iter, c1.end( ) );  
   cout << "After erasing all elements but the first, deque becomes: ";  
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )  
      cout << *Iter << " ";  
   cout << endl;  
}  
```  
  
```Output  
The initial deque is: 10 20 30 40 50   
After erasing the first element, the deque becomes:  20 30 40 50   
After erasing all elements but the first, deque becomes: 20   
```  
  
##  <a name="a-namedequefronta-dequefront"></a><a name="deque__front"></a>  deque  
 Devuelve una referencia al primer elemento de un deque.  
  
```  
reference front();

const_reference front() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si el deque está vacío, el valor devuelto es indefinido.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor devuelto de `front` se asigna a un `const_reference`, no se puede modificar el objeto de deque. Si el valor devuelto de `front` se asigna a un **referencia**, el objeto deque se puede modificar.  
  
 Al compilar con _SECURE_SCL 1, se producirá un error de tiempo de ejecución si se intenta tener acceso a un elemento de un deque vacío.  Vea [Checked Iterators](../standard-library/checked-iterators.md) para obtener más información.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_front.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 11 );  
  
   int& i = c1.front( );  
   const int& ii = c1.front( );  
  
   cout << "The first integer of c1 is " << i << endl;  
   i++;  
   cout << "The second integer of c1 is " << ii << endl;  
}  
```  
  
```Output  
The first integer of c1 is 10  
The second integer of c1 is 11  
```  
  
##  <a name="a-namedequegetallocatora-dequegetallocator"></a><a name="deque__get_allocator"></a>  deque:: get_allocator  
 Devuelve una copia del objeto de asignador utilizado para construir el deque.  
  
```  
Allocator get_allocator() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El asignador utilizado por el deque.  
  
### <a name="remarks"></a>Comentarios  
 Los asignadores de la clase deque especifican cómo la clase administra el almacenamiento. Los asignadores predeterminados proporcionados con las clases de contenedor STL son suficientes para la mayoría de las necesidades de programación. La escritura y el uso de sus propias clases de asignador son temas avanzados de C++.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_get_allocator.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   // The following lines declare objects that use the default allocator.  
   deque <int> c1;  
   deque <int, allocator<int> > c2 = deque <int, allocator<int> >( allocator<int>( ) );  
  
   // c3 will use the same allocator class as c1  
   deque <int> c3( c1.get_allocator( ) );  
  
   deque <int>::allocator_type xlst = c1.get_allocator( );  
   // You can now call functions on the allocator class used by c1  
}  
```  
  
##  <a name="a-namedequeinserta-dequeinsert"></a><a name="deque__insert"></a>  deque:: Insert  
 Inserta un elemento, varios elementos o un intervalo de elementos en el deque en una posición especificada.  
  
```  
iterator insert(
    const_iterator Where,  
    const Type& Val);

iterator insert(
    const_iterator Where,  
    Type&& Val);

void insert(
    iterator Where,  
    size_type Count,  
    const Type& Val);

template <class InputIterator>  
void insert(
    iterator Where,  
    InputIterator First,  
    InputIterator Last);

iterator insert(
    iterator Where,initializer_list<Type>  
IList);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`Where`|Posición del deque de destino donde se inserta el primer elemento.|  
|`Val`|Valor del elemento que se va a insertar en el deque.|  
|`Count`|Número de elementos que se van a insertar en el deque.|  
|`First`|Posición del primer elemento en el intervalo de elementos del argumento deque que se va a copiar.|  
|`Last`|Posición del primer elemento más allá del intervalo de elementos del argumento deque que se va a copiar.|  
|`IList`|initializer_list de los elementos que se van a insertar.|  
  
### <a name="return-value"></a>Valor devuelto  
 Las dos primeras funciones insert devuelven un iterador que apunta a la posición donde se insertó el nuevo elemento en el deque.  
  
### <a name="remarks"></a>Comentarios  
 Las operaciones de inserción pueden ser muy costosas.  
  
##  <a name="a-namedequeiteratora-dequeiterator"></a><a name="deque__iterator"></a>  deque:: Iterator  
 Un tipo que proporciona un iterador de acceso aleatorio que puede leer o modificar cualquier elemento de un deque.  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo **iterador** puede utilizarse para modificar el valor de un elemento.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [comenzar](#deque__begin).  
  
##  <a name="a-namedequemaxsizea-dequemaxsize"></a><a name="deque__max_size"></a>  deque:: max_size  
 Devuelve la longitud máxima del deque.  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud máxima permitida de deque.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_max_size.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::size_type i;  
  
   i = c1.max_size( );  
   cout << "The maximum possible length of the deque is " << i << "." << endl;  
}  
```  
  
##  <a name="a-namedequeoperatorata-dequeoperator"></a><a name="deque__operator_at"></a>  [] deque:: operator  
 Devuelve una referencia al elemento de deque en una posición especificada.  
  
```  
reference operator[](size_type _Pos);

const_reference operator[](size_type _Pos) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Pos`  
 La posición del elemento de deque que se haga referencia.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al elemento cuya posición se especifica en el argumento. Si la posición especificada es mayor que el tamaño del deque, el resultado es indefinido.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor devuelto de `operator[]` se asigna a un `const_reference`, no se puede modificar el objeto de deque. Si el valor devuelto de `operator[]` se asigna a un **referencia**, el objeto deque se puede modificar.  
  
 Al compilar con _SECURE_SCL 1, se producirá un error de tiempo de ejecución si se intenta obtener acceso a un elemento fuera de los límites del deque.  Vea [Checked Iterators](../standard-library/checked-iterators.md) para obtener más información.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_op_ref.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   cout << "The first integer of c1 is " << c1[0] << endl;  
   int& i = c1[1];  
   cout << "The second integer of c1 is " << i << endl;  
  
}  
```  
  
```Output  
The first integer of c1 is 10  
The second integer of c1 is 20  
```  
  
##  <a name="a-namedequeoperatoreqa-dequeoperator"></a><a name="deque__operator_eq"></a>  deque:: operator =  
 Reemplaza los elementos de esta deque utilizando los elementos de otro deque.  
  
```  
deque& operator=(const deque& right);

deque& operator=(deque&& right);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|` right`|Deque que proporciona el nuevo contenido.|  
  
### <a name="remarks"></a>Comentarios  
 La invalidación de la primera copia elementos en esta deque de ` right`, el origen de la asignación. El segundo reemplazo mueve los elementos a este deque desde ` right`.  
  
 Se quitan los elementos contenidos en este deque antes de que se ejecuta el operador.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_operator_as.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
using namespace std;  
  
typedef deque<int> MyDeque;  
  
template<typename MyDeque> struct S;  
  
template<typename MyDeque> struct S<MyDeque&> {  
  static void show( MyDeque& d ) {  
    MyDeque::const_iterator iter;  
    for (iter = d.cbegin(); iter != d.cend(); iter++)  
       cout << *iter << " ";  
    cout << endl;  
  }  
};  
  
template<typename MyDeque> struct S<MyDeque&&> {  
  static void show( MyDeque&& d ) {  
    MyDeque::const_iterator iter;  
    for (iter = d.cbegin(); iter != d.cend(); iter++)  
       cout << *iter << " ";  
cout << " via unnamed rvalue reference " << endl;  
  }  
};  
  
int main( )  
{  
   MyDeque d1, d2;  
  
   d1.push_back(10);  
   d1.push_back(20);  
   d1.push_back(30);  
   d1.push_back(40);  
   d1.push_back(50);  
  
   cout << "d1 = " ;  
   S<MyDeque&>::show( d1 );  
  
   d2 = d1;  
   cout << "d2 = ";  
   S<MyDeque&>::show( d2 );  
  
   cout << "     ";  
   S<MyDeque&&>::show ( move< MyDeque& > (d1) );  
 }  
```  
  
##  <a name="a-namedequepointera-dequepointer"></a><a name="deque__pointer"></a>  deque:: pointer  
 Proporciona un puntero a un elemento en un [deque](../standard-library/deque-class.md).  
  
```unstlib  
typedef typename Allocator::pointer pointer;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo **puntero** puede utilizarse para modificar el valor de un elemento. Un [iterador](#deque__iterator) se utiliza normalmente para tener acceso a un elemento de deque.  
  
##  <a name="a-namedequepopbacka-dequepopback"></a><a name="deque__pop_back"></a>  deque:: pop_back  
 Elimina el elemento al final del deque.  
  
```  
void pop_back();
```  
  
### <a name="remarks"></a>Comentarios  
 El último elemento no debe estar vacío. `pop_back` nunca inicia una excepción.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_pop_back.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   cout << "The first element is: " << c1.front( ) << endl;  
   cout << "The last element is: " << c1.back( ) << endl;  
  
   c1.pop_back( );  
   cout << "After deleting the element at the end of the deque, the "  
      "last element is: " << c1.back( ) << endl;  
}  
```  
  
```Output  
The first element is: 1  
The last element is: 2  
After deleting the element at the end of the deque, the last element is: 1  
```  
  
##  <a name="a-namedequepopfronta-dequepopfront"></a><a name="deque__pop_front"></a>  deque:: pop_front  
 Elimina el elemento situado al principio del deque.  
  
```  
void pop_front();
```  
  
### <a name="remarks"></a>Comentarios  
 El primer elemento no debe estar vacío. `pop_front` nunca inicia una excepción.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_pop_front.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   cout << "The first element is: " << c1.front( ) << endl;  
   cout << "The second element is: " << c1.back( ) << endl;  
  
   c1.pop_front( );  
   cout << "After deleting the element at the beginning of the "  
      "deque, the first element is: " << c1.front( ) << endl;  
}  
```  
  
```Output  
The first element is: 1  
The second element is: 2  
After deleting the element at the beginning of the deque, the first element is: 2  
```  
  
##  <a name="a-namedequepushbacka-dequepushback"></a><a name="deque__push_back"></a>  push_back  
 Agrega un elemento al final del deque.  
  
```  
void push_back(const Type& val);

void push_back(Type&& val);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|` val`|El elemento se agrega al final del deque.|  
  
### <a name="remarks"></a>Comentarios  
 Si se produce una excepción, el deque permanece inalterado y se vuelve a producir la excepción.  
  
##  <a name="a-namedequepushfronta-dequepushfront"></a><a name="deque__push_front"></a>  push_front  
 Agrega un elemento al principio del deque.  
  
```  
    void push_front(const Type& val);

void push_front(Type&& val);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|` val`|El elemento se agrega al principio del deque.|  
  
### <a name="remarks"></a>Comentarios  
 Si se produce una excepción, el deque permanece inalterado y se vuelve a producir la excepción.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_push_front.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
#include <string>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_front( 1 );  
   if ( c1.size( ) != 0 )  
      cout << "First element: " << c1.front( ) << endl;  
  
   c1.push_front( 2 );  
   if ( c1.size( ) != 0 )  
      cout << "New first element: " << c1.front( ) << endl;  
  
// move initialize a deque of strings  
   deque <string> c2;  
   string str("a");  
  
   c2.push_front( move( str ) );  
   cout << "Moved first element: " << c2.front( ) << endl;  
}  
```  
  
```Output  
First element: 1  
New first element: 2  
Moved first element: a  
```  
  
##  <a name="a-namedequerbegina-dequerbegin"></a><a name="deque__rbegin"></a>  rbegin  
 Devuelve un iterador al primer elemento de un deque invertido.  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de acceso aleatorio inverso dirige al primer elemento de un deque invertido o direccionamiento lo que habría sido el último elemento de deque irreversible.  
  
### <a name="remarks"></a>Comentarios  
 `rbegin` se utiliza con un deque invertido igual que [comenzar](#deque__begin) se usa con un deque.  
  
 Si el valor devuelto de `rbegin` se asigna a un `const_reverse_iterator`, no se puede modificar el objeto de deque. Si el valor devuelto de `rbegin` se asigna a un `reverse_iterator`, el objeto deque se puede modificar.  
  
 `rbegin` puede utilizarse para iterar a través de un deque hacia atrás.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_rbegin.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::iterator c1_Iter;  
   deque <int>::reverse_iterator c1_rIter;  
  
   // If the following line had replaced the line above, an error   
   // would have resulted in the line modifying an element   
   // (commented below) because the iterator would have been const  
   // deque <int>::const_reverse_iterator c1_rIter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1_rIter = c1.rbegin( );  
   cout << "Last element in the deque is " << *c1_rIter << "." << endl;  
  
   cout << "The deque contains the elements: ";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << *c1_Iter << " ";  
   cout << "in that order.";  
   cout << endl;  
  
   // rbegin can be used to iterate through a deque in reverse order  
   cout << "The reversed deque is: ";  
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )  
      cout << *c1_rIter << " ";  
   cout << endl;  
  
   c1_rIter = c1.rbegin( );  
 *c1_rIter = 40;  // This would have caused an error if a   
                    // const_reverse iterator had been declared as   
                    // noted above  
   cout << "Last element in deque is now " << *c1_rIter << "." << endl;  
}  
```  
  
```Output  
Last element in the deque is 30.  
The deque contains the elements: 10 20 30 in that order.  
The reversed deque is: 30 20 10   
Last element in deque is now 40.  
```  
  
##  <a name="a-namedequereferencea-dequereference"></a><a name="deque__reference"></a>  deque:: Reference  
 Un tipo que proporciona una referencia a un elemento almacenado en un deque.  
  
```  
typedef typename Allocator::reference reference;  
```  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_reference.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
  
   const int &i = c1.front( );  
   int &j = c1.back( );  
   cout << "The first element is " << i << endl;  
   cout << "The second element is " << j << endl;  
}  
```  
  
```Output  
The first element is 10  
The second element is 20  
```  
  
##  <a name="a-namedequerenda-dequerend"></a><a name="deque__rend"></a>  deque:: rend  
 Devuelve un iterador que direcciona la ubicación del último elemento de un deque invertido.  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de acceso aleatorio inverso que direcciona la ubicación del último elemento de un deque invertido (la ubicación que había precedido al primer elemento de deque sin invertir).  
  
### <a name="remarks"></a>Comentarios  
 `rend` se utiliza con un deque invertido igual que [final](#deque__end) se usa con un deque.  
  
 Si el valor devuelto de `rend` se asigna a un `const_reverse_iterator`, no se puede modificar el objeto de deque. Si el valor devuelto de `rend` se asigna a un `reverse_iterator`, el objeto deque se puede modificar.  
  
 `rend` puede utilizarse para probar si un iterador inverso ha llegado al final de su deque.  
  
 El valor devuelto por `rend` no se debe desreferenciar.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_rend.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   deque <int> c1;  
   deque <int>::iterator c1_Iter;  
   deque <int>::reverse_iterator c1_rIter;  
   // If the following line had replaced the line above, an error  
   // would have resulted in the line modifying an element  
   // (commented below) because the iterator would have been const  
   // deque <int>::const_reverse_iterator c1_rIter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1_rIter = c1.rend( );  
   c1_rIter --; // Decrementing a reverse iterator moves it forward   
                // in the deque (to point to the first element here)  
   cout << "The first element in the deque is: " << *c1_rIter << endl;  
  
   cout << "The deque is: ";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << *c1_Iter << " ";  
   cout << endl;  
  
   // rend can be used to test if an iteration is through all of   
   // the elements of a reversed deque  
   cout << "The reversed deque is: ";  
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )  
      cout << *c1_rIter << " ";  
   cout << endl;  
  
   c1_rIter = c1.rend( );  
   c1_rIter--; // Decrementing the reverse iterator moves it backward   
               // in the reversed deque (to the last element here)  
 *c1_rIter = 40; // This modification of the last element would   
                   // have caused an error if a const_reverse   
                   // iterator had been declared (as noted above)  
   cout << "The modified reversed deque is: ";  
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )  
      cout << *c1_rIter << " ";  
   cout << endl;  
}  
```  
  
```Output  
The first element in the deque is: 10  
The deque is: 10 20 30   
The reversed deque is: 30 20 10   
The modified reversed deque is: 30 20 40   
```  
  
##  <a name="a-namedequeresizea-dequeresize"></a><a name="deque__resize"></a>  deque:: Resize  
 Especifica un nuevo tamaño de un deque.  
  
```  
void resize(size_type _Newsize);

void resize(size_type _Newsize, Type val);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Newsize`  
 El nuevo tamaño del deque.  
  
 ` val`  
 El valor de los nuevos elementos que se agregarán a deque si el nuevo tamaño es mayor que el tamaño original. Si el valor se omite, a los nuevos elementos se les asigna el valor predeterminado para la clase.  
  
### <a name="remarks"></a>Comentarios  
 Si el tamaño del deque es menor que el tamaño solicitado, `_Newsize`, se agregan elementos a deque hasta que alcance el tamaño solicitado.  
  
 Si el tamaño del deque es mayor que el tamaño solicitado, los elementos más cercanos al final del deque se eliminan hasta que el deque alcanza el tamaño `_Newsize`.  
  
 Si el tamaño actual del deque es el mismo que el tamaño solicitado, se realiza ninguna acción.  
  
 [tamaño](#deque__size) refleja el tamaño actual del deque.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_resize.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{   
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1.resize( 4,40 );  
   cout << "The size of c1 is: " << c1.size( ) << endl;  
   cout << "The value of the last element is " << c1.back( ) << endl;  
  
   c1.resize( 5 );  
   cout << "The size of c1 is now: " << c1.size( ) << endl;  
   cout << "The value of the last element is now " << c1.back( ) << endl;  
  
   c1.resize( 2 );  
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;  
   cout << "The value of the last element is now " << c1.back( ) << endl;  
}  
```  
  
```Output  
The size of c1 is: 4  
The value of the last element is 40  
The size of c1 is now: 5  
The value of the last element is now 0  
The reduced size of c1 is: 2  
The value of the last element is now 20  
```  
  
##  <a name="a-namedequereverseiteratora-dequereverseiterator"></a><a name="deque__reverse_iterator"></a>  deque:: reverse_iterator  
 Un tipo que proporciona un iterador de acceso aleatorio que puede leer o modificar un elemento de un deque invertido.  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `reverse_iterator` se utiliza para recorrer en iteración el deque.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo rbegin.  
  
##  <a name="a-namedequeshrinktofita-dequeshrinktofit"></a><a name="deque__shrink_to_fit"></a>  deque:: shrink_to_fit  
 Descarta el exceso de capacidad.  
  
```  
void shrink_to_fit();
```  
  
### <a name="remarks"></a>Comentarios  
 No hay ninguna manera portátil para determinar si `shrink_to_fit` reduce el almacenamiento utilizado por un [deque](../standard-library/deque-class.md).  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_shrink_to_fit.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
   //deque <int>::iterator Iter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
   cout << "Current size of v1 = "   
      << v1.size( ) << endl;  
   v1.shrink_to_fit();  
   cout << "Current size of v1 = "   
      << v1.size( ) << endl;  
}  
```  
  
```Output  
Current size of v1 = 1  
Current size of v1 = 1  
```  
  
##  <a name="a-namedequesizea-dequesize"></a><a name="deque__size"></a>  deque  
 Devuelve el número de elementos del deque.  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud actual de deque.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_size.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::size_type i;  
  
   c1.push_back( 1 );  
   i = c1.size( );  
   cout << "The deque length is " << i << "." << endl;  
  
   c1.push_back( 2 );  
   i = c1.size( );  
   cout << "The deque length is now " << i << "." << endl;  
}  
```  
  
```Output  
The deque length is 1.  
The deque length is now 2.  
```  
  
##  <a name="a-namedequesizetypea-dequesizetype"></a><a name="deque__size_type"></a>  deque:: size_type  
 Un tipo que cuenta el número de elementos de un deque.  
  
```  
typedef typename Allocator::size_type size_type;  
```  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [tamaño](#deque__size).  
  
##  <a name="a-namedequeswapa-dequeswap"></a><a name="deque__swap"></a>  deque:: swap  
 Intercambia los elementos de dos deques.  
  
```  
void swap(deque<Type, Allocator>& right);

friend void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right) template <class Type, class Allocator>  
void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 El deque proporciona los elementos deben intercambiar o deque cuyos elementos son van a intercambiar con los del deque ` left`.  
  
 ` left`  
 Un deque cuyos elementos son van a intercambiar con los del deque ` right`.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_swap.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1, c2, c3;  
   deque <int>::iterator c1_Iter;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   c1.push_back( 3 );  
   c2.push_back( 10 );  
   c2.push_back( 20 );  
   c3.push_back( 100 );  
  
   cout << "The original deque c1 is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   c1.swap( c2 );  
  
   cout << "After swapping with c2, deque c1 is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   swap( c1,c3 );  
  
   cout << "After swapping with c3, deque c1 is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   swap<>(c1, c2);  
   cout << "After swapping with c2, deque c1 is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
}  
```  
  
```Output  
The original deque c1 is: 1 2 3  
After swapping with c2, deque c1 is: 10 20  
After swapping with c3, deque c1 is: 100  
After swapping with c2, deque c1 is: 1 2 3  
```  
  
##  <a name="a-namedequevaluetypea-dequevaluetype"></a><a name="deque__value_type"></a>  deque:: value_type  
 Tipo que representa el tipo de datos almacenados en un deque.  
  
```  
typedef typename Allocator::value_type value_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 `value_type` es un sinónimo del parámetro de plantilla **tipo**.  
  
### <a name="example"></a>Ejemplo  
  
```  
// deque_value_type.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
int main( )   
{  
   using namespace std;  
   deque<int>::value_type AnInt;  
   AnInt = 44;  
   cout << AnInt << endl;  
}  
```  
  
```Output  
44  
```  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)

