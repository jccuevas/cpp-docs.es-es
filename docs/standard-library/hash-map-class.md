---
title: hash_map (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- hash_map/stdext::hash_map
- hash_map/stdext::hash_map::allocator_type
- hash_map/stdext::hash_map::const_iterator
- hash_map/stdext::hash_map::const_pointer
- hash_map/stdext::hash_map::const_reference
- hash_map/stdext::hash_map::const_reverse_iterator
- hash_map/stdext::hash_map::difference_type
- hash_map/stdext::hash_map::iterator
- hash_map/stdext::hash_map::key_compare
- hash_map/stdext::hash_map::key_type
- hash_map/stdext::hash_map::mapped_type
- hash_map/stdext::hash_map::pointer
- hash_map/stdext::hash_map::reference
- hash_map/stdext::hash_map::reverse_iterator
- hash_map/stdext::hash_map::size_type
- hash_map/stdext::hash_map::value_type
- hash_map/stdext::hash_map::at
- hash_map/stdext::hash_map::begin
- hash_map/stdext::hash_map::cbegin
- hash_map/stdext::hash_map::cend
- hash_map/stdext::hash_map::clear
- hash_map/stdext::hash_map::count
- hash_map/stdext::hash_map::crbegin
- hash_map/stdext::hash_map::crend
- hash_map/stdext::hash_map::emplace
- hash_map/stdext::hash_map::emplace_hint
- hash_map/stdext::hash_map::empty
- hash_map/stdext::hash_map::end
- hash_map/stdext::hash_map::equal_range
- hash_map/stdext::hash_map::erase
- hash_map/stdext::hash_map::find
- hash_map/stdext::hash_map::get_allocator
- hash_map/stdext::hash_map::insert
- hash_map/stdext::hash_map::key_comp
- hash_map/stdext::hash_map::lower_bound
- hash_map/stdext::hash_map::max_size
- hash_map/stdext::hash_map::rbegin
- hash_map/stdext::hash_map::rend
- hash_map/stdext::hash_map::size
- hash_map/stdext::hash_map::swap
- hash_map/stdext::hash_map::upper_bound
- hash_map/stdext::hash_map::value_comp
dev_langs:
- C++
helpviewer_keywords:
- stdext::hash_map
- stdext::hash_map::allocator_type
- stdext::hash_map::const_iterator
- stdext::hash_map::const_pointer
- stdext::hash_map::const_reference
- stdext::hash_map::const_reverse_iterator
- stdext::hash_map::difference_type
- stdext::hash_map::iterator
- stdext::hash_map::key_compare
- stdext::hash_map::key_type
- stdext::hash_map::mapped_type
- stdext::hash_map::pointer
- stdext::hash_map::reference
- stdext::hash_map::reverse_iterator
- stdext::hash_map::size_type
- stdext::hash_map::value_type
- stdext::hash_map::at
- stdext::hash_map::begin
- stdext::hash_map::cbegin
- stdext::hash_map::cend
- stdext::hash_map::clear
- stdext::hash_map::count
- stdext::hash_map::crbegin
- stdext::hash_map::crend
- stdext::hash_map::emplace
- stdext::hash_map::emplace_hint
- stdext::hash_map::empty
- stdext::hash_map::end
- stdext::hash_map::equal_range
- stdext::hash_map::erase
- stdext::hash_map::find
- stdext::hash_map::get_allocator
- stdext::hash_map::insert
- stdext::hash_map::key_comp
- stdext::hash_map::lower_bound
- stdext::hash_map::max_size
- stdext::hash_map::rbegin
- stdext::hash_map::rend
- stdext::hash_map::size
- stdext::hash_map::swap
- stdext::hash_map::upper_bound
- stdext::hash_map::value_comp
ms.assetid: 40879dfc-51ba-4a59-9f9e-26208de568a8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dc280212a4d37147c8af9cd2921e12516c529d13
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2018
---
# <a name="hashmap-class"></a>hash_map (Clase)
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Almacena y recupera datos rápidamente de una colección en la que cada elemento es un par que tiene una clave de ordenación cuyo valor es único y un valor de datos asociado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Key,   
    class Type,   
    class Traits=hash_compare<Key, less<Key>>,   
    class Allocator=allocator<pair <const Key, Type>>>  
class hash_map  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Key`  
 Tipo de datos de clave que se almacenará en hash_map.  
  
 `Type`  
 Tipo de datos de elemento que se almacenará en hash_map.  
  
 `Traits`  
 Tipo que incluye dos objetos de función: uno de clase compare que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo y una función hash que es un predicado unario que asigna valores de clave de los elementos a enteros sin signo de tipo `size_t`. Este argumento es opcional, y hash_compare< `Key`, less< `Key`> > es el valor predeterminado.  
  
 `Allocator`  
 Tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria de hash_map. Este argumento es opcional y el valor predeterminado es allocator<pair <const `Key`, `Type`>>.  
  
## <a name="remarks"></a>Comentarios  
 hash_map es:  
  
-   Un contenedor asociativo de tamaño variable que admite la recuperación eficaz de valores de elemento según un valor de clave asociado.  
  
-   Reversible, porque proporciona un iterador bidireccional para tener acceso a sus elementos.  
  
-   Con algoritmo hash, ya que sus elementos se agrupan en depósitos en función del valor de una función hash aplicada a los valores de clave de los elementos.  
  
-   Único en el sentido de que cada uno de sus elementos debe tener una clave única.  
  
-   Un contenedor asociativo de pares, ya que los valores de datos de sus elementos son distintos de sus valores de clave.  
  
-   Una clase de plantilla, porque la funcionalidad que proporciona es genérica y por tanto independiente del tipo específico de datos contenido como elementos o claves. Los tipos de datos que se usarán para los elementos y las claves se especifican como parámetros en la plantilla de clase junto con la función de comparación y el asignador.  
  
 La ventaja principal de los algoritmos hash sobre la ordenación es su mayor eficacia; un algoritmo hash que se ejecuta correctamente realiza inserciones, eliminaciones y búsquedas en un tiempo promedio constante en comparación con un tiempo proporcional al logaritmo del número de elementos del contenedor en el caso de las técnicas de ordenación. El valor de un elemento de hash_map se puede cambiar directamente, pero no su valor de clave asociado. En su lugar, se deben eliminar los valores de clave asociados a los antiguos elementos e insertar los nuevos valores de clave asociados a los elementos nuevos.  
  
 En general, la elección del tipo de contenedor se debe tomar según el tipo de búsqueda y de inserción que necesite la aplicación. Los contenedores asociativos con algoritmo hash están optimizados para las operaciones de búsqueda, inserción y eliminación. Las funciones miembro que admiten explícitamente estas operaciones son eficaces cuando se usan con una función hash bien diseñada, las realizan en un tiempo que es una constante promedio y no dependen del número de elementos del contenedor. Una función hash bien diseñada genera una distribución uniforme de valores hash y minimiza el número de colisiones; se produce una colisión cuando se asignan valores de clave distintos al mismo valor hash. En el peor de los casos, con la peor función hash posible, el número de operaciones es proporcional al número de elementos de la secuencia (tiempo lineal).  
  
 El hash_map debe ser el contenedor asociativo preferido cuando la aplicación satisfaga las condiciones que asocian los valores a sus claves. Un modelo de este tipo de estructura es una lista ordenada de palabras clave únicas con valores de cadena asociados que proporcionan, por ejemplo, definiciones. Si por el contrario las palabras tienen más una definición correcta, de modo que las claves no son únicas, el contenedor más adecuado sería hash_multimap. Por otra parte, si solo se va a almacenar la lista de palabras, el contenedor correcto sería hash_set. Si se permiten varias repeticiones de las palabras, la estructura de contenedor adecuada sería hash_multiset.  
  
 El hash_map ordena la secuencia que controla al llamar a un objeto `Traits` hash almacenado de clase [value_compare](../standard-library/value-compare-class.md). Se puede obtener acceso a este objeto almacenado mediante una llamada a la función miembro [key_comp](#key_comp). Este tipo de objeto de función debe comportarse igual que un objeto de clase [hash_compare](../standard-library/hash-compare-class.md)<Key, less\<Key>>. En concreto, para todos los valores `Key` de tipo `Key`, la llamada a `Traits`( `Key`) produce una distribución de valores de tipo `size_t`.  
  
 En general, se debe poder comparar si los elementos son menores que otros para poder establecer este orden; de este modo, dados dos elementos cualesquiera, se puede determinar que son equivalentes (en el sentido de que ninguno es menor que el otro) o que uno es menor que el otro. Esto produce una ordenación entre los elementos no equivalentes. En un sentido más técnico, la función de comparación es un predicado binario que induce una ordenación débil estricta en el sentido matemático estándar. Un predicado binario f(x y) es un objeto de función que tiene dos objetos de argumento `x` e `y`, y un valor devuelto de `true` o `false`. Una ordenación impuesta en un hash_map es una ordenación débil estricta si el predicado binario es irreflexivo, antisimétrico y transitivo, y si la equivalencia es transitiva, donde dos objetos x e y se definen como equivalentes cuando tanto f(x, y) como f(y, x) son false. Si la condición más fuerte de igualdad entre las claves reemplaza la de equivalencia, la ordenación se convierte en total (en el sentido de que todos los elementos se ordenan entre sí) y las claves coincidentes serán indiscernibles unas de otras.  
  
 El orden real de los elementos de la secuencia controlada depende de la función hash, la función de ordenación y el tamaño actual de la tabla hash almacenada en el objeto contenedor. No se puede determinar el tamaño actual de la tabla hash, por lo que en general no se puede predecir el orden de los elementos de la secuencia controlada. La inserción de elementos no invalida ningún iterador y al quitar elementos solo se invalidan los iteradores que habían apuntado específicamente a los elementos quitados.  
  
 El iterador proporcionado por la clase hash_map es un iterador bidireccional, pero las funciones miembro de clase [insert](#insert) y [hash_map](#hash_map) tienen versiones que toman como parámetros de plantilla un iterador de entrada más débil, cuyos requisitos de funcionalidad son más mínimos que los garantizados por la clase de iteradores bidireccionales. Los distintos conceptos de iterador forman una familia relacionada por los refinamientos de su funcionalidad. Cada concepto de iterador tiene su propio conjunto de requisitos, y los algoritmos que funcionan con ellos deben limitar sus suposiciones a los requisitos proporcionados por ese tipo de iterador. Se puede suponer que se puede desreferenciar un iterador de entrada para hacer referencia a un objeto y que se puede incrementar hasta el iterador siguiente de la secuencia. Se trata de un conjunto mínimo de funcionalidad, pero es suficiente para poder comunicarse sobre un intervalo de iteradores `[First, Last)` en el contexto de las funciones miembro de clase.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[hash_map](#hash_map)|Construye un `hash_map` que está vacío o que es una copia de todo o de parte de otro `hash_map`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|Tipo que representa la clase `allocator` para el objeto `hash_map`.|  
|[const_iterator](#const_iterator)|Tipo que proporciona un iterador bidireccional que puede leer un elemento `const` en `hash_map`.|  
|[const_pointer](#const_pointer)|Tipo que proporciona un puntero a un elemento `const` en un `hash_map`.|  
|[const_reference](#const_reference)|Tipo que proporciona una referencia a un elemento `const` almacenado en un `hash_map` para leer y realizar operaciones `const`.|  
|[const_reverse_iterator](#const_reverse_iterator)|Tipo que proporciona un iterador bidireccional que puede leer cualquier elemento `const` en `hash_map`.|  
|[difference_type](#difference_type)|Tipo entero con signo que se puede usar para representar el número de elementos de un `hash_map` en un intervalo entre elementos a los que apuntan los iteradores.|  
|[iterator](#iterator)|Tipo que proporciona un iterador bidireccional que puede leer o modificar cualquier elemento de `hash_map`.|  
|[key_compare](#key_compare)|Tipo que proporciona un objeto de función que puede comparar dos claves de ordenación para determinar el orden relativo de dos elementos en el `hash_map`.|  
|[key_type](#key_type)|Tipo que describe el objeto de clave de ordenación que constituye cada elemento de `hash_map`.|  
|[mapped_type](#mapped_type)|Tipo que representa el tipo de datos almacenados en un `hash_map`.|  
|[pointer](#pointer)|Tipo que proporciona un puntero a un elemento de `hash_map`.|  
|[reference](#reference)|Tipo que proporciona una referencia a un elemento almacenado en un `hash_map`.|  
|[reverse_iterator](#reverse_iterator)|Tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento de `hash_map` invertido.|  
|[size_type](#size_type)|Tipo entero sin signo que puede representar el número de elementos de un `hash_map`.|  
|[value_type](#value_type)|Tipo que proporciona un objeto de función que puede comparar dos elementos como claves de ordenación para determinar su orden relativo en el `hash_map`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[at](#at)|Busca un elemento en un `hash_map` con un valor de clave especificado.|  
|[begin](#begin)|Devuelve un iterador que direcciona el primer elemento del `hash_map`.|  
|[cbegin](#cbegin)|Devuelve un iterador constante que direcciona el primer elemento del `hash_map`.|  
|[cend](#cend)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de `hash_map`.|  
|[clear](#clear)|Borra todos los elementos de un `hash_map`.|  
|[count](#count)|Devuelve el número de elementos de un `hash_map` cuya clave coincide con una clave especificada por un parámetro.|  
|[crbegin](#crbegin)|Devuelve un iterador constante que direcciona el primer elemento de `hash_map` invertido.|  
|[crend](#crend)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de `hash_map` invertido.|  
|[emplace](#emplace)|Inserta en un `hash_map` un elemento construido en contexto.|  
|[emplace_hint](#emplace_hint)|Inserta en un `hash_map` un elemento construido en contexto, con una sugerencia de colocación.|  
|[empty](#empty)|Comprueba si un `hash_map` está vacío.|  
|[end](#end)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de `hash_map`.|  
|[equal_range](#equal_range)|Devuelve un par de iteradores, respectivamente, al primer elemento de `hash_map` cuya clave mayor es que una clave especificada y al primer elemento del `hash_map` cuya clave es igual o mayor que la clave especificada.|  
|[erase](#erase)|Quita un elemento o un intervalo de elementos de un `hash_map` de las posiciones especificadas.|  
|[find](#find)|Devuelve un iterador que direcciona la ubicación de un elemento en un `hash_map` que tiene una clave equivalente a una clave especificada.|  
|[get_allocator](#get_allocator)|Devuelve una copia del objeto `allocator` utilizado para construir el `hash_map`.|  
|[insert](#insert)|Inserta un elemento o un intervalo de elementos en un `hash_map`.|  
|[key_comp](#key_comp)|Devuelve un iterador al primer elemento de `hash_map` cuyo valor de clave es igual o mayor que el de una clave especificada.|  
|[lower_bound](#lower_bound)|Devuelve un iterador al primer elemento de `hash_map` cuyo valor de clave es igual o mayor que el de una clave especificada.|  
|[max_size](#max_size)|Devuelve la longitud máxima del `hash_map`.|  
|[rbegin](#rbegin)|Devuelve un iterador que direcciona el primer elemento de `hash_map` invertido.|  
|[rend](#rend)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de `hash_map` invertido.|  
|[size](#size)|Devuelve el número de elementos de `hash_map`.|  
|[swap](#swap)|Intercambia los elementos de dos `hash_map`.|  
|[upper_bound](#upper_bound)|Devuelve un iterador al primer elemento de `hash_map` cuyo valor de clave es mayor que el de una clave especificada.|  
|[value_comp](#value_comp)|Recupera una copia del objeto de comparación utilizado para ordenar valores de elemento de `hash_map`.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator&#91;&#93;](#op_at)|Inserta un elemento en un `hash_map` con un valor de clave especificado.|  
|[hash_map::operator=](#op_eq)|Reemplaza los elementos de un `hash_map` con una copia de otro `hash_map`.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<hash_map>  
  
 **Espacio de nombres:** stdext  
  
##  <a name="allocator_type"></a>  hash_map::allocator_type  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Tipo que representa la clase de asignador para el objeto hash_map.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;  
```  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [get_allocator](#get_allocator) para obtener un ejemplo que usa `allocator_type`.  
  
##  <a name="at"></a>  hash_map::at  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Busca un elemento en un hash_map con un valor de clave especificado.  
  
```  
Type& at(const Key& key);

const Type& at(const Key& key) const;
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`key`|El valor de clave del elemento que se tiene que encontrar.|  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al valor de datos del elemento encontrado.  
  
### <a name="remarks"></a>Comentarios  
 Si no se encuentra el valor de clave de argumento, la función genera un objeto de clase [out_of_range](../standard-library/out-of-range-class.md).  
  

### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_at.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   typedef pair <const int, int> cInt2Int;  
   hash_map <int, int> hm1;  
  
   // Insert data values  
   hm1.insert ( cInt2Int ( 1, 10 ) );  
   hm1.insert ( cInt2Int ( 2, 20 ) );  
   hm1.insert ( cInt2Int ( 3, 30 ) );  
  
   cout  << "The values of the mapped elements are:";  
   for ( int i = 1 ; i <= hm1.size() ; i++ )  
      cout << " " << hm1.at(i);  
   cout << "." << endl;  
}  
```  
  
##  <a name="begin"></a>  hash_map::begin  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Devuelve un iterador que se dirige al primer elemento del objeto hash_map.  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador bidireccional que se dirige al primer elemento del objeto hash_map o la ubicación siguiente a un objeto hash_map vacío.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_begin.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
  
   hash_map <int, int> :: iterator hm1_Iter;  
   hash_map <int, int> :: const_iterator hm1_cIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 0, 0 ) );  
   hm1.insert ( Int_Pair ( 1, 1 ) );  
   hm1.insert ( Int_Pair ( 2, 4 ) );  
  
   hm1_cIter = hm1.begin ( );  
   cout << "The first element of hm1 is "   
        << hm1_cIter -> first << "." << endl;  
  
   hm1_Iter = hm1.begin ( );  
   hm1.erase ( hm1_Iter );  
  
   // The following 2 lines would err because the iterator is const  
   // hm1_cIter = hm1.begin ( );  
   // hm1.erase ( hm1_cIter );  
  
   hm1_cIter = hm1.begin( );  
   cout << "The first element of hm1 is now "   
        << hm1_cIter -> first << "." << endl;  
}  
```  
  
```Output  
The first element of hm1 is 0.  
The first element of hm1 is now 1.  
```  
  
##  <a name="cbegin"></a>  hash_map::cbegin  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Devuelve un iterador const que se dirige al primer elemento del objeto hash_map.  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador bidireccional const que se dirige al primer elemento del objeto [hash_map](../standard-library/hash-map-class.md) o la ubicación siguiente a un `hash_map` vacío.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_cbegin.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
  
   hash_map <int, int> :: const_iterator hm1_cIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 2, 4 ) );  
  
   hm1_cIter = hm1.cbegin ( );  
   cout << "The first element of hm1 is "   
        << hm1_cIter -> first << "." << endl;  
   }  
```  
  
```Output  
The first element of hm1 is 2.  
```  
  
##  <a name="cend"></a>  hash_map::cend  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Devuelve un iterador const que se dirige a la ubicación que sigue al último elemento de un objeto hash_map.  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador bidireccional const que se dirige a la ubicación que sigue al último elemento de un objeto [hash_map](../standard-library/hash-map-class.md). Si el `hash_map` está vacío, `hash_map::cend == hash_map::begin`.  
  
### <a name="remarks"></a>Comentarios  
 `cend` se usa para comprobar si un iterador ha llegado al final de su `hash_map`.  
  
 El valor devuelto por `cend` no se debe desreferenciar.  
  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_cend.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
  
   hash_map <int, int> :: const_iterator hm1_cIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_cIter = hm1.cend( );  
   hm1_cIter--;  
   cout << "The value of last element of hm1 is "   
        << hm1_cIter -> second << "." << endl;  
   }  
```  
  
```Output  
The value of last element of hm1 is 30.  
```  
  
##  <a name="clear"></a>  hash_map::clear  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Borra todos los elementos de una asignación hash_map.  
  
```  
void clear();
```  
  
### <a name="remarks"></a>Comentarios  
  
  
### <a name="example"></a>Ejemplo  
  En el ejemplo siguiente se muestra el uso de la función miembro hash_map::clear.  
  
```  
// hash_map_clear.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    using namespace stdext;  
    hash_map<int, int> hm1;  
    hash_map<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(1, 1));  
    hm1.insert(Int_Pair(2, 4));  
  
    i = hm1.size();  
    cout << "The size of the hash_map is initially "  
         << i << "." << endl;  
  
    hm1.clear();  
    i = hm1.size();  
    cout << "The size of the hash_map after clearing is "  
         << i << "." << endl;  
}  
```  
  
```Output  
The size of the hash_map is initially 2.  
The size of the hash_map after clearing is 0.  
```  
  
##  <a name="const_iterator"></a>  hash_map::const_iterator  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Tipo que proporciona un iterador bidireccional que puede leer un elemento **const** del objeto hash_map.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `const_iterator` no se puede utilizar para modificar el valor de un elemento.  
  
 El `const_iterator` definido por los puntos de hash_map a los elementos que son objetos de [value_type](#value_type), que es de tipo `pair`*\<***clave const, escriba***>*, cuyo primer miembro es la clave para el elemento y cuyo segundo miembro es el dato de referencia asignada mantenido por el elemento.  
  
 A fin de desreferenciar una `const_iterator` `cIter` apunta a un elemento de un objeto hash_map, use la  **->**  operador.  
  
 Para tener acceso al valor de clave del elemento, use `cIter` **-> first**, que es equivalente a (\* `cIter`) **.first**. Para tener acceso al valor de la referencia asignada del elemento, use `cIter` **-> second**, que es equivalente a (\* `cIter`) **.second**.  
  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [begin](#begin) para obtener un ejemplo que usa `const_iterator`.  
  
##  <a name="const_pointer"></a>  hash_map::const_pointer  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Tipo que proporciona un puntero a un elemento **const** en un objeto hash_map.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `const_pointer` no se puede utilizar para modificar el valor de un elemento.  
  
 En la mayoría de los casos, se debe usar [iterator](#iterator) para obtener acceso a los elementos de un objeto hash_map.  
  
  
##  <a name="const_reference"></a>  hash_map::const_reference  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Tipo que proporciona una referencia a un elemento **const** almacenado en un objeto hash_map para leer operaciones **const** y realizarlas.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;  
```  
  
### <a name="remarks"></a>Comentarios  
  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_const_ref.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map<int, int> hm1;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the key of the first element  
   const int &Ref1 = ( hm1.begin( ) -> first );  
  
   // The following line would cause an error because the   
   // non-const_reference cannot be used to access the key  
   // int &Ref1 = ( hm1.begin( ) -> first );  
  
   cout << "The key of the first element in the hash_map is "  
        << Ref1 << "." << endl;  
  
   // Declare and initialize a reference &Ref2   
   // to the data value of the first element  
   int &Ref2 = ( hm1.begin( ) -> second );  
  
   cout << "The data value of the first element in the hash_map is "  
        << Ref2 << "." << endl;  
}  
```  
  
```Output  
The key of the first element in the hash_map is 1.  
The data value of the first element in the hash_map is 10.  
```  
  
##  <a name="const_reverse_iterator"></a>  hash_map::const_reverse_iterator  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Tipo que proporciona un iterador bidireccional que puede leer cualquier elemento **const** del objeto hash_map.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse)iterator const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `const_reverse_iterator` no puede modificar el valor de un elemento y se usa para iterar el objeto hash_map en orden inverso.  
  
 El `const_reverse_iterator` definido mediante el objeto hash_map apunta a elementos que son objetos de [value_type](#value_type), que son de tipo `pair`\< **const Key, Type**>, cuyo primer miembro es la clave para el elemento y cuyo segundo miembro es la referencia asignada que el elemento conserva.  
  
 A fin de desreferenciar una `const_reverse_iterator` `crIter` apunta a un elemento de un objeto hash_map, use la  **->**  operador.  
  
 Para tener acceso al valor de clave del elemento, use `crIter` -> **first**, que es equivalente a (\* `crIter`) **.first**. Para tener acceso al valor de la referencia asignada del elemento, use `crIter` -> **second**, que es equivalente a (\* `crIter`). **first**.  
  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [rend](#rend) para obtener un ejemplo de cómo declarar y usar `const_reverse_iterator`.  
  
##  <a name="count"></a>  hash_map::count  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Devuelve el número de elementos de un objeto hash_map cuya clave coincide con una clave especificada por un parámetro.  
  
```  
size_type count(const Key& key) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Valor clave de los elementos cuya coincidencia debe buscarse a partir del objeto hash_map.  
  
### <a name="return-value"></a>Valor devuelto  
 1 si el objeto hash_map contiene un elemento cuyo criterio de ordenación coincide con el criterio del parámetro; 0 si el objeto hash_map no contiene ningún elemento con el mismo criterio.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve el número de elementos *x* del intervalo  
  
 [ `lower_bound` (_ *Key* ), `upper_bound` (\_ *Key* ) )  
  
 que es 0 o 1 en el caso de hash_map, que es un contenedor asociativo único.  
  
  
### <a name="example"></a>Ejemplo  
  El ejemplo siguiente muestra el uso de la función miembro hash_map::count.  
  
```  
// hash_map_count.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_map<int, int> hm1;  
    hash_map<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair (1, 1));  
    hm1.insert(Int_Pair (2, 1));  
    hm1.insert(Int_Pair (1, 4));  
    hm1.insert(Int_Pair (2, 1));  
  
    // Keys must be unique in hash_map, so duplicates are ignored  
    i = hm1.count(1);  
    cout << "The number of elements in hm1 with a sort key of 1 is: "  
         << i << "." << endl;  
  
    i = hm1.count(2);  
    cout << "The number of elements in hm1 with a sort key of 2 is: "  
         << i << "." << endl;  
  
    i = hm1.count(3);  
    cout << "The number of elements in hm1 with a sort key of 3 is: "  
         << i << "." << endl;  
}  
```  
  
```Output  
The number of elements in hm1 with a sort key of 1 is: 1.  
The number of elements in hm1 with a sort key of 2 is: 1.  
The number of elements in hm1 with a sort key of 3 is: 0.  
```  
  
##  <a name="crbegin"></a>  hash_map::crbegin  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Devuelve un iterador const que se dirige al primer elemento de un objeto hash_map invertido.  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador bidireccional inverso const que se dirige al primer elemento de un objeto [hash_map](../standard-library/hash-map-class.md) invertido o lo que ha sido el último elemento del objeto `hash_map` sin invertir.  
  
### <a name="remarks"></a>Comentarios  
 `crbegin` se usa con un hash_map invertido igual que [begin](#begin) se usa con un `hash_map`.  
  
 Con el valor devuelto de `crbegin`, el objeto `hash_map` no se puede modificar.  
  
 `crbegin` puede usarse para iterar `hash_map` hacia atrás.  
  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_crbegin.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
  
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_crIter = hm1.crbegin( );  
   cout << "The first element of the reversed hash_map hm1 is "  
        << hm1_crIter -> first << "." << endl;  
}  
```  
  
```Output  
The first element of the reversed hash_map hm1 is 3.  
```  
  
##  <a name="crend"></a>  hash_map::crend  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Devuelve un iterador const que se dirige a la ubicación que sigue al último elemento de un objeto hash_map invertido.  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador bidireccional inverso const que se dirige a la ubicación siguiente al último elemento de un objeto [hash_map](../standard-library/hash-map-class.md) invertido (la ubicación que había precedido al primer elemento del objeto `hash_map` sin invertir).  
  
### <a name="remarks"></a>Comentarios  
 `crend` se usa con un `hash_map` invertido igual que [hash_map::end](#end) se usa con un `hash_map`.  
  
 Con el valor devuelto de `crend`, el objeto `hash_map` no se puede modificar.  
  
 Se puede utilizar `crend` para comprobar si un iterador inverso llegó al final de su `hash_map`.  
  
 El valor devuelto por `crend` no se debe desreferenciar.  
  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_crend.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
  
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_crIter = hm1.crend( );  
   hm1_crIter--;  
   cout << "The last element of the reversed hash_map hm1 is "  
        << hm1_crIter -> first << "." << endl;  
}  
```  
  
```Output  
The last element of the reversed hash_map hm1 is 3.  
```  
  
##  <a name="difference_type"></a>  hash_map::difference_type  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Tipo entero con signo que se puede usar para representar el número de elementos de un objeto hash_map en un intervalo entre elementos a los que apuntan los iteradores.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;  
```  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <hash_map>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 3, 20 ) );  
  
   // The following won't insert, because map keys are unique  
   hm1.insert ( Int_Pair ( 2, 30 ) );     
  
   hash_map <int, int>::iterator hm1_Iter, hm1_bIter, hm1_eIter;     
   hm1_bIter = hm1.begin( );  
   hm1_eIter = hm1.end( );  
  
   // Count the number of elements in a hash_map   
   hash_map <int, int>::difference_type  df_count = 0;  
   hm1_Iter = hm1.begin( );  
   while ( hm1_Iter != hm1_eIter)     
   {  
      df_count++;  
      hm1_Iter++;  
   }  
  
   cout << "The number of elements in the hash_map hm1 is: "   
        << df_count << "." << endl;  
  
   cout  << "The keys of the mapped elements are:";  
   for ( hm1_Iter= hm1.begin( ) ; hm1_Iter!= hm1.end( ) ;  
         hm1_Iter++)  
      cout << " " << hm1_Iter-> first;  
   cout << "." << endl;  
  
   cout  << "The values of the mapped elements are:";  
   for ( hm1_Iter= hm1.begin( ) ; hm1_Iter!= hm1.end( ) ;  
         hm1_Iter++)  
      cout << " " << hm1_Iter-> second;  
   cout << "." << endl;  
}  
```  
  
```Output  
The number of elements in the hash_map hm1 is: 3.  
The keys of the mapped elements are: 1 2 3.  
The values of the mapped elements are: 10 20 20.  
```  
  
##  <a name="emplace"></a>  hash_map::emplace  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Inserta un elemento construido en contexto dentro de un objeto hash_map.  
  
```  
template <class ValTy>  
pair <iterator, bool>  
emplace(
    ValTy&& val);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`val`|Valor usado para construir con movimiento un elemento que se va a insertar en el objeto [hash_map](../standard-library/hash-map-class.md) a menos que `hash_map` ya contenga ese elemento (o, de manera más general, un elemento cuya clave esté ordenada de manera equivalente).|  
  
### <a name="return-value"></a>Valor devuelto  
 La función miembro `emplace` devuelve un par cuyo componente bool devuelve True si se ha realizado una inserción y False si el `hash_map` ya contenía un elemento cuya clave tenía un valor equivalente en la ordenación y cuyo componente de iterador devuelve la dirección donde se ha insertado un nuevo elemento o donde ya estaba el elemento.  
  
 Para tener acceso al componente de iterador de un par `pr` devuelto por esta función miembro, utilice `pr.first` y, para desreferenciarlo, utilice `*(pr.first)`. Para tener acceso al componente `bool` de un par `pr` devuelto por esta función miembro, utilice `pr.second` y, para desreferenciarlo, utilice `*(pr.second)`.  
  
### <a name="remarks"></a>Comentarios  
 El [hash_map::value_type](#value_type) de un elemento es un par, de modo que el valor de un elemento será un par ordenado en el que el primer componente es igual que el valor de clave y el segundo componente es igual que el valor de datos del elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_emplace.cpp  
// compile with: /EHsc  
#include<hash_map>  
#include<iostream>  
#include <string>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_map<int, string> hm1;  
    typedef pair<int, string> is1(1, "a");  
  
    hm1.emplace(move(is1));  
    cout << "After the emplace insertion, hm1 contains:" << endl  
      << " " << hm1.begin()->first  
      << " => " << hm1.begin()->second  
      << endl;  
}  
```  
  
```Output  
After the emplace insertion, hm1 contains:  
 1 => a  
```  
  
##  <a name="emplace_hint"></a>  hash_map::emplace_hint  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Inserta un elemento construido en contexto dentro de un objeto hash_map, con una sugerencia de colocación.  
  
```  
template <class ValTy>  
iterator emplace_hint(
    const_iterator _Where,  
    ValTy&& val);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`val`|Valor usado para construir con movimiento un elemento que se va a insertar en el objeto [hash_map](../standard-library/hash-map-class.md) a menos que `hash_map` ya contenga ese elemento (o, de manera más general, un elemento cuya clave esté ordenada de manera equivalente).|  
|`_Where`|Sugerencia con respecto al lugar donde se va a empezar a buscar el punto correcto de inserción.|  
  
### <a name="return-value"></a>Valor devuelto  
 La función miembro [hash_multimap::emplace](../standard-library/hash-multimap-class.md#emplace) devuelve un iterador que apunta a la posición donde se ha insertado el nuevo elemento en el objeto `hash_map` o donde se encuentra el elemento existente con una ordenación equivalente.  
  
### <a name="remarks"></a>Comentarios  
 El [hash_map::value_type](#value_type) de un elemento es un par, de modo que el valor de un elemento será un par ordenado en el que el primer componente es igual que el valor de clave y el segundo componente es igual que el valor de datos del elemento.  
  
 La inserción se puede realizar en tiempo constante amortizado, en lugar de en tiempo logarítmico, si el punto de inserción sigue inmediatamente a `_Where`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_emplace_hint.cpp  
// compile with: /EHsc  
#include<hash_map>  
#include<iostream>  
#include <string>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_map<int, string> hm1;  
    typedef pair<int, string> is1(1, "a");  
  
    hm1.emplace(hm1.begin(), move(is1));  
    cout << "After the emplace, hm1 contains:" << endl  
      << " " << hm1.begin()->first  
      << " => " << hm1.begin()->second  
      << endl;  
}  
```  
  
```Output  
After the emplace insertion, hm1 contains:  
 1 => a  
```  
  
##  <a name="empty"></a>  hash_map::empty  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Comprueba si un objeto hash_map está vacío.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 **True** si el objeto hash_map está vacío; **False** si el objeto hash_map no lo está.  
  
### <a name="remarks"></a>Comentarios  
  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_empty.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1, hm2;  
  
   typedef pair <int, int> Int_Pair;  
   hm1.insert ( Int_Pair ( 1, 1 ) );  
  
   if ( hm1.empty( ) )  
      cout << "The hash_map hm1 is empty." << endl;  
   else  
      cout << "The hash_map hm1 is not empty." << endl;  
  
   if ( hm2.empty( ) )  
      cout << "The hash_map hm2 is empty." << endl;  
   else  
      cout << "The hash_map hm2 is not empty." << endl;  
}  
```  
  
```Output  
The hash_map hm1 is not empty.  
The hash_map hm2 is empty.  
```  
  
##  <a name="end"></a>  hash_map::end  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Devuelve un iterador que se dirige a la ubicación que sigue al último elemento de un objeto hash_map.  
  
```  
const_iterator end() const;

iterator end();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador bidireccional que se dirige a la ubicación que sigue al último elemento de un objeto hash_map. Si el objeto hash_map está vacío, hash_map::end == hash_map::begin.  
  
### <a name="remarks"></a>Comentarios  
 **end** se usa para comprobar si un iterador ha llegado al final de su objeto hash_map.  
  
 El valor devuelto por **end** no se debe desreferenciar.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_end.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
  
   hash_map <int, int> :: iterator hm1_Iter;  
   hash_map <int, int> :: const_iterator hm1_cIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_cIter = hm1.end( );  
   hm1_cIter--;  
   cout << "The value of last element of hm1 is "   
        << hm1_cIter -> second << "." << endl;  
  
   hm1_Iter = hm1.end( );  
   hm1_Iter--;  
   hm1.erase ( hm1_Iter );  
  
   // The following 2 lines would err because the iterator is const  
   // hm1_cIter = hm1.end ( );  
   // hm1_cIter--;  
   // hm1.erase ( hm1_cIter );  
  
   hm1_cIter = hm1.end( );  
   hm1_cIter--;  
   cout << "The value of last element of hm1 is now "  
        << hm1_cIter -> second << "." << endl;  
}  
```  
  
```Output  
The value of last element of hm1 is 30.  
The value of last element of hm1 is now 20.  
```  
  
##  <a name="equal_range"></a>  hash_map::equal_range  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Devuelve un par de iteradores, respectivamente, al primer elemento de un objeto hash_map cuya clave es mayor que una clave especificada y al primer elemento del objeto hash_map cuya clave es igual o mayor que la clave especificada.  
  
```  
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Valor de clave de argumento que se comparará con la clave de ordenación de un elemento del objeto hash_map que se está buscando.  
  
### <a name="return-value"></a>Valor devuelto  
 Un par de iteradores donde el primero es el elemento [lower_bound](#lower_bound) de la clave y el segundo es el elemento [upper_bound](#upper_bound) de la clave.  
  
 Para tener acceso al primer iterador de un par `pr` devuelto por la función miembro, use `pr`. **first** y para desreferenciar el iterador de límite inferior, use \*( `pr`. **first**). Para tener acceso al segundo iterador de un par `pr` devuelto por la función miembro, use `pr`. **second** y para desreferenciar el iterador de límite superior, use \*( `pr`. **second**).  
  
### <a name="remarks"></a>Comentarios  
  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_equal_range.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   typedef hash_map <int, int> IntMap;  
   IntMap hm1;  
   hash_map <int, int> :: const_iterator hm1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   pair <IntMap::const_iterator, IntMap::const_iterator> p1, p2;  
   p1 = hm1.equal_range( 2 );  
  
   cout << "The lower bound of the element with "  
        << "a key of 2 in the hash_map hm1 is: "  
        << p1.first -> second << "." << endl;  
  
   cout << "The upper bound of the element with "  
        << "a key of 2 in the hash_map hm1 is: "  
        << p1.second -> second << "." << endl;  
  
   // Compare the upper_bound called directly   
   hm1_RcIter = hm1.upper_bound( 2 );  
  
   cout << "A direct call of upper_bound( 2 ) gives "  
        << hm1_RcIter -> second << "," << endl  
        << " matching the 2nd element of the pair"  
        << " returned by equal_range( 2 )." << endl;  
  
   p2 = hm1.equal_range( 4 );  
  
   // If no match is found for the key,  
   // both elements of the pair return end( )  
   if ( ( p2.first == hm1.end( ) ) && ( p2.second == hm1.end( ) ) )  
      cout << "The hash_map hm1 doesn't have an element "  
             << "with a key less than 40." << endl;  
   else  
      cout << "The element of hash_map hm1 with a key >= 40 is: "  
           << p1.first -> first << "." << endl;  
}  
```  
  
```Output  
The lower bound of the element with a key of 2 in the hash_map hm1 is: 20.  
The upper bound of the element with a key of 2 in the hash_map hm1 is: 30.  
A direct call of upper_bound( 2 ) gives 30,  
 matching the 2nd element of the pair returned by equal_range( 2 ).  
The hash_map hm1 doesn't have an element with a key less than 40.  
```  
  
##  <a name="erase"></a>  hash_map::erase  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Quita un elemento o un intervalo de elementos de una asignación hash-map de las posiciones especificadas, o quita los elementos que coinciden con una clave especificada.  
  
```  
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Where`  
 Posición del elemento que se va a quitar de hash_map.  
  
 `first`  
 Posición del primer elemento que se ha quitado de hash_map.  
  
 `last`  
 Posición inmediatamente siguiente al último elemento que se ha quitado de hash_map.  
  
 `key`  
 El valor clave de los elementos que se van a quitar de hash_map.  
  
### <a name="return-value"></a>Valor devuelto  
 Para las dos primeras funciones miembro, un iterador bidireccional que designa el primer elemento que permanece más allá de los elementos quitados, o un puntero al final de hash_map si no existe ese elemento.  
  
 Para la tercera función miembro, devuelve el número de elementos que se han quitado de hash_map.  
  
### <a name="remarks"></a>Comentarios  
 Las funciones miembro nunca producen una excepción.  
  
  
### <a name="example"></a>Ejemplo  
  En el ejemplo siguiente se muestra el uso de la función miembro hash_map::erase.  
  
```  
// hash_map_erase.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_map<int, int> hm1, hm2, hm3;  
    hash_map<int, int> :: iterator pIter, Iter1, Iter2;  
    int i;  
    hash_map<int, int>::size_type n;  
    typedef pair<int, int> Int_Pair;  
  
    for (i = 1; i < 5; i++)  
    {  
        hm1.insert(Int_Pair (i, i));  
        hm2.insert(Int_Pair (i, i*i));  
        hm3.insert(Int_Pair (i, i-1));  
    }  
  
    // The 1st member function removes an element at a given position  
    Iter1 = ++hm1.begin();  
    hm1.erase(Iter1);  
  
    cout << "After the 2nd element is deleted, the hash_map hm1 is:";  
    for (pIter = hm1.begin(); pIter != hm1.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
  
    // The 2nd member function removes elements  
    // in the range [ first,  last)  
    Iter1 = ++hm2.begin();  
    Iter2 = --hm2.end();  
    hm2.erase(Iter1, Iter2);  
  
    cout << "After the middle two elements are deleted, "  
         << "the hash_map hm2 is:";  
    for (pIter = hm2.begin(); pIter != hm2.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
  
    // The 3rd member function removes elements with a given  key  
    n = hm3.erase(2);  
  
    cout << "After the element with a key of 2 is deleted,\n"  
         << "the hash_map hm3 is:";  
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
  
    // The 3rd member function returns the number of elements removed  
    cout << "The number of elements removed from hm3 is: "  
         << n << "." << endl;  
  
    // The dereferenced iterator can also be used to specify a key  
    Iter1 = ++hm3.begin();  
    hm3.erase(Iter1);  
  
    cout << "After another element with a key equal to that"  
         << endl;  
    cout  << "of the 2nd element is deleted, "  
          << "the hash_map hm3 is:";  
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)  
        cout << " " << pIter -> second;  
    cout << "." << endl;  
}  
```  
  
```Output  
After the 2nd element is deleted, the hash_map hm1 is: 1 3 4.  
After the middle two elements are deleted, the hash_map hm2 is: 1 16.  
After the element with a key of 2 is deleted,  
the hash_map hm3 is: 0 2 3.  
The number of elements removed from hm3 is: 1.  
After another element with a key equal to that  
of the 2nd element is deleted, the hash_map hm3 is: 0 3.  
```  
  
##  <a name="find"></a>  hash_map::find  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Devuelve un iterador que se dirige a la ubicación de un elemento en un objeto hash_map que tiene una clave equivalente a una clave especificada.  
  
```  
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 El valor de la clave con el que debe coincidir el criterio de ordenación de un elemento del objeto hash_map en el que se buscará.  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador que se dirige a la primera ubicación de un elemento con una clave especificada, o la ubicación siguiente al último elemento del objeto hash_map si no se encuentra ninguna coincidencia con la clave.  
  
### <a name="remarks"></a>Comentarios  
 **find** devuelve un iterador que se dirige a un elemento del objeto hash_map cuyo criterio de ordenación es equivalente a la clave de argumento de un predicado binario que induce a una ordenación basada en una relación de comparabilidad de menor que.  
  
 Si el valor devuelto de **find** se asigna a un [const_iterator](#const_iterator), el objeto hash_map no se puede modificar. Si el valor devuelto de **find** se asigna a un [iterator](#iterator), el objeto hash_map se puede modificar.  
  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_find.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_RcIter = hm1.find( 2 );  
   cout << "The element of hash_map hm1 with a key of 2 is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   // If no match is found for the key, end( ) is returned  
   hm1_RcIter = hm1.find( 4 );  
  
   if ( hm1_RcIter == hm1.end( ) )  
      cout << "The hash_map hm1 doesn't have an element "  
           << "with a key of 4." << endl;  
   else  
      cout << "The element of hash_map hm1 with a key of 4 is: "  
           << hm1_RcIter -> second << "." << endl;  
  
   // The element at a specific location in the hash_map can be found   
   // using a dereferenced iterator addressing the location  
   hm1_AcIter = hm1.end( );  
   hm1_AcIter--;  
   hm1_RcIter = hm1.find( hm1_AcIter -> first );  
   cout << "The element of hm1 with a key matching "  
        << "that of the last element is: "  
        << hm1_RcIter -> second << "." << endl;  
}  
```  
  
```Output  
The element of hash_map hm1 with a key of 2 is: 20.  
The hash_map hm1 doesn't have an element with a key of 4.  
The element of hm1 with a key matching that of the last element is: 30.  
```  
  
##  <a name="get_allocator"></a>  hash_map::get_allocator  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Devuelve una copia del objeto de asignador usado para construir el objeto hash_map.  
  
```  
Allocator get_allocator() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El asignador usado por el objeto hash_map.  
  
### <a name="remarks"></a>Comentarios  
 Los asignadores de la clase hash_map especifican cómo la clase administra el almacenamiento. Los asignadores predeterminados proporcionados con las clases contenedoras de la biblioteca estándar de C++ son suficientes para la mayoría de las necesidades de programación. La escritura y el uso de sus propias clases de asignador son temas avanzados de C++.  
  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_get_allocator.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int>::allocator_type hm1_Alloc;  
   hash_map <int, int>::allocator_type hm2_Alloc;  
   hash_map <int, double>::allocator_type hm3_Alloc;  
   hash_map <int, int>::allocator_type hm4_Alloc;  
  
   // The following lines declare objects  
   // that use the default allocator.  
   hash_map <int, int> hm1;  
   hash_map <int, int> hm2;  
   hash_map <int, double> hm3;  
  
   hm1_Alloc = hm1.get_allocator( );  
   hm2_Alloc = hm2.get_allocator( );  
   hm3_Alloc = hm3.get_allocator( );  
  
   cout << "The number of integers that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << hm2.max_size( ) << "." << endl;  
  
   cout << "The number of doubles that can be allocated"  
        << endl << "before free memory is exhausted: "  
        << hm3.max_size( ) <<  "." << endl;  
  
   // The following line creates a hash_map hm4  
   // with the allocator of hash_map hm1.  
   hash_map <int, int> hm4( less<int>( ), hm1_Alloc );  
  
   hm4_Alloc = hm4.get_allocator( );  
  
   // Two allocators are interchangeable if  
   // storage allocated from each can be  
   // deallocated with the other  
   if( hm1_Alloc == hm4_Alloc )  
   {  
      cout << "The allocators are interchangeable."  
           << endl;     
   }  
   else     
   {  
      cout << "The allocators are not interchangeable."  
           << endl;     
   }  
}  
```  
  
##  <a name="hash_map"></a>  hash_map::hash_map  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Construye un hash_map que está vacío o es una copia de todo o de parte de otro hash_map.  
  
```  
hash_map();

explicit hash_map(
    const Traits& Comp);

hash_map(
    const Traits& Comp,  
    const Allocator& Al);

hash_map(
    const hash_map& Right);

hash_map(
    hash_map&& Right);

hash_map(
    initializer_list<Type> IList);hash_map(initializer_list<Type> IList,  
    const key_compare& Comp);

hash_map(
    initializer_list<Type> IList,  
    const key_compare& Comp,   
    const allocator_type& Al);

template <class InputIterator>  
hash_map(
 InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
hash_map(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp);

template <class InputIterator>  
hash_map(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp,  
    const Allocator& Al  
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`Al`|Clase de asignador de almacenamiento que se usará para este objeto hash_map, que de manera predeterminada es **Allocator**.|  
|`Comp`|Función de comparación de tipo const `Traits` utilizada para ordenar los elementos del hash_map, que de forma predeterminada es `hash_compare`.|  
|`Right`|hash_map del que el mapa construido va a ser una copia.|  
|`First`|Posición del primer elemento en el intervalo de elementos que se va a copiar.|  
|`Last`|Posición del primer elemento más allá del intervalo de elementos que se va a copiar.|  
|`IList`|initializer_list|  
  
### <a name="remarks"></a>Comentarios  
 Todos los constructores almacenan un tipo de objeto de asignador que administra el almacenamiento en memoria del objeto hash_map y que se puede devolver más adelante al llamar a [get_allocator](#get_allocator). El parámetro de asignador se suele omitir en las declaraciones de clase y las macros de preprocesamiento que se utilizan para sustituir asignadores alternativos.  
  
 Todos los constructores inicializan sus hash_map.  
  
 Todos los constructores almacenan un objeto de función de tipo `Traits` que se usa para establecer un orden entre las claves del objeto hash_map y que se puede devolver más adelante al llamar a [key_comp](#key_comp).  
  
 Los tres primeros constructores especifican un objeto hash_map inicial vacío, además, el segundo especifica el tipo de función de comparación (`Comp`) que se usará para establecer el orden de los elementos y el tercero especifica de forma explícita el tipo de asignador (`Al`) que se va a usar. La palabra clave `explicit` suprime ciertas clases de conversión automática de tipos.  
  
 El cuarto constructor especifica una copia del hash_map `Right`.  
  
 Los tres constructores siguientes copian el intervalo `[First, Last)` de un hash_map especificando de forma cada vez más explícita el tipo de función de comparación de clase `Traits` y el asignador.  
  
 El último constructor mueve el hash_map `Right`.  
  
##  <a name="insert"></a>  hash_map::insert  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Inserta un elemento o un intervalo de elementos en un objeto hash_map.  
  
```  
pair <iterator, bool> insert(
    const value_type& val);

iterator insert(
    const_iterator _Where,  
    const value_type& val);

template <class InputIterator>  
void insert(
    InputIterator first,  
    InputIterator last);

template <class ValTy>  
pair <iterator, bool>  
insert(
    ValTy&& val);

template <class ValTy>  
iterator insert(
    const_iterator _Where,  
    ValTy&& val);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`val`|Valor de un elemento que se va a insertar en el objeto hash_map a menos que este ya contenga ese elemento (o, de manera más general, un elemento cuya clave esté ordenada de manera equivalente).|  
|`_Where`|Sugerencia con respecto al lugar donde se va a empezar a buscar el punto correcto de inserción.|  
|`first`|Posición del primer elemento que se va a copiar de un objeto hash_map.|  
|`last`|Posición situada más allá del último elemento que se va a copiar de un objeto hash_map.|  
  
### <a name="return-value"></a>Valor devuelto  
 La primera función miembro **insert** devuelve un par cuyo componente bool devuelve True si se ha realizado una inserción y False si el objeto hash_map ya contenía un elemento cuya clave tenía un valor equivalente en la ordenación y cuyo componente de iterador devuelve la dirección donde se ha insertado un nuevo elemento o donde ya estaba el elemento.  
  
 Para tener acceso al componente de iterador de un par `pr` devuelto por esta función miembro, use `pr`. **first** y para desreferenciarla, use \*( `pr`. **first**). Para tener acceso al componente `bool` de un par `pr` devuelto por esta función miembro, utilice `pr`. **second** y para desreferenciarla, use \*( `pr`. **second**).  
  
 La segunda función miembro **insert**, la versión de sugerencia, devuelve un iterador que apunta a la posición donde se ha insertado el nuevo elemento en el objeto hash_map.  
  
 Las dos últimas funciones miembro **insert** se comportan igual que las dos primeras, salvo que construyen con movimiento el valor insertado.  
  
### <a name="remarks"></a>Comentarios  
 El [value_type](../standard-library/map-class.md#value_type) de un elemento es un par, de modo que el valor de un elemento será un par ordenado en el que el primer componente es igual que el valor de clave y el segundo componente es igual que el valor de datos del elemento.  
  
 La inserción se puede realizar en tiempo constante amortizado para la versión de sugerencia de insert, en lugar de en tiempo logarítmico, si el punto de inserción sigue inmediatamente a `_Where`.  
  
 La tercera función miembro inserta la secuencia de valores de elemento en un objeto hash_map correspondiente a cada elemento al que se dirige por un iterador en el intervalo *[First, Last)* de un conjunto especificado.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_insert.cpp  
// compile with: /EHsc  
#include<hash_map>  
#include<iostream>  
#include <string>  
  
int main()  
{  
    using namespace std;  
    using namespace stdext;  
    hash_map<int, int>::iterator hm1_pIter, hm2_pIter;  
  
    hash_map<int, int> hm1, hm2;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(1, 10));  
    hm1.insert(Int_Pair(2, 20));  
    hm1.insert(Int_Pair(3, 30));  
    hm1.insert(Int_Pair(4, 40));  
  
    cout<< "The original elements (Key => Value) of hm1 are:";  
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)  
        cout << endl << " " << hm1_pIter -> first << " => "  
             << hm1_pIter->second;  
    cout << endl;  
  
    pair< hash_map<int,int>::iterator, bool > pr;  
    pr = hm1.insert(Int_Pair(1, 10));  
  
    if (pr.second == true)  
    {  
        cout<< "The element 10 was inserted in hm1 successfully."  
            << endl;  
    }  
    else  
    {  
        cout<< "The element 10 already exists in hm1\n with a key value of"  
            << "((pr.first) -> first)= "<<(pr.first)-> first  
            << "."<< endl;  
    }  
  
    // The hint version of insert  
    hm1.insert(--hm1.end(), Int_Pair(5, 50));  
  
    cout<< "After the insertions, the elements of hm1 are:";  
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)  
        cout << endl << " " << hm1_pIter -> first << " => "  
             << hm1_pIter->second;  
    cout << endl;  
  
    hm2.insert(Int_Pair(10, 100));  
  
    // The templatized version inserting a range  
    hm2.insert( ++hm1.begin(), --hm1.end() );  
  
    cout<< "After the insertions, the elements of hm2 are:";  
    for (hm2_pIter = hm2.begin(); hm2_pIter != hm2.end(); hm2_pIter++)  
        cout << endl << " " << hm2_pIter -> first << " => "  
             << hm2_pIter->second;  
    cout << endl;  
  
    // The templatized versions move constructing elements  
    hash_map<int, string> hm3, hm4;  
    pair<int, string> is1(1, "a"), is2(2, "b");  
  
    hm3.insert(move(is1));  
    cout << "After the move insertion, hm3 contains:" << endl  
      << " " << hm3.begin()->first  
      << " => " << hm3.begin()->second  
      << endl;  
  
    hm4.insert(hm4.begin(), move(is2));  
    cout << "After the move insertion, hm4 contains:" << endl  
      << " " << hm4.begin()->first  
      << " => " << hm4.begin()->second  
      << endl;  
}  
```  
  
```Output  
The original elements (Key => Value) of hm1 are:  
 1 => 10  
 2 => 20  
 3 => 30  
 4 => 40  
The element 10 already exists in hm1  
 with a key value of((pr.first) -> first)= 1.  
After the insertions, the elements of hm1 are:  
 1 => 10  
 2 => 20  
 3 => 30  
 4 => 40  
 5 => 50  
After the insertions, the elements of hm2 are:  
 2 => 20  
 10 => 100  
 3 => 30  
 4 => 40  
After the move insertion, hm3 contains:  
 1 => a  
After the move insertion, hm4 contains:  
 2 => b  
```  
  
##  <a name="iterator"></a>  hash_map::iterator  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Tipo que proporciona un iterador bidireccional que puede leer o modificar cualquier elemento de un objeto hash_map.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El **iterator** definido mediante el objeto hash_map apunta a elementos que son objetos de [value_type](#value_type), que son de tipo **pair\<const Key, Type>,** cuyo primer miembro es la clave para el elemento y cuyo segundo miembro es la referencia asignada que el elemento conserva.  
  
 Para desreferenciar un elemento **iterator**`Iter` que señala a un elemento de un mapa múltiple, use el operador **->**.  
  
 Para tener acceso al valor de clave del elemento, use `Iter` -> **first**, que es equivalente a (\* `Iter`). **first**. Para tener acceso al valor de la referencia asignada del elemento, use `Iter` -> **second**, que es equivalente a (\* `Iter`). **second**.  
  
 Se puede usar un tipo **iterator** para modificar el valor de un elemento.  
  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [begin](#begin) para obtener un ejemplo de cómo declarar y usar el **iterator**.  
  
##  <a name="key_comp"></a>  hash_map::key_comp  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Recupera una copia del objeto de comparación usado para ordenar claves de un objeto hash_map.  
  
```  
key_compare key_comp() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el objeto de función que usa un objeto hash_map para ordenar sus elementos.  
  
### <a name="remarks"></a>Comentarios  
 El objeto almacenado define la función miembro  
  
 **bool operator**( **const Key&** `left`**, const Key&** `right`);  
  
 que devuelve **True** si `left` precede y no es igual a `right` en el criterio de ordenación.  
  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_key_comp.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_map <int, int, hash_compare<int, less<int> > > hm1;  
   hash_map <int, int, hash_compare<int, less<int> > >::key_compare   
      kc1 = hm1.key_comp( ) ;  
  
   // Operator stored in kc1 tests order & returns bool value  
   bool result1 = kc1( 2, 3 ) ;     
   if( result1 == true )     
   {  
      cout << "kc1( 2,3 ) returns value of true,"  
           << "\n where kc1 is the function object of hm1"  
           << " of type key_compare." << endl;  
   }  
   else     
   {  
      cout << "kc1( 2,3 ) returns value of false"  
           << "\n where kc1 is the function object of hm1"  
           << " of type key_compare." << endl;  
   }  
  
   hash_map <int, int, hash_compare<int, greater<int> > > hm2;  
   hash_map <int, int, hash_compare<int, greater<int> > >  
      ::key_compare kc2 = hm2.key_comp( );  
  
   // Operator stored in kc2 tests order & returns bool value  
   bool result2 = kc2( 2, 3 ) ;  
   if( result2 == true )  
   {  
      cout << "kc2( 2,3 ) returns value of true,"  
           << "\n where kc2 is the function object of hm2"  
           << " of type key_compare." << endl;  
   }  
   else     
   {  
      cout << "kc2( 2,3 ) returns value of false,"  
           << "\n where kc2 is the function object of hm2"  
           << " of type key_compare." << endl;  
   }  
}  
```  
  
##  <a name="key_compare"></a>  hash_map::key_compare  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Tipo que proporciona un objeto de función que puede comparar dos criterios de ordenación para determinar el orden relativo de dos elementos del mapa.  
  
```  
typedef Traits key_compare;  
```  
  
### <a name="remarks"></a>Comentarios  
 `key_compare` es un sinónimo del parámetro de plantilla `Traits`.  
  
 Para obtener más información sobre `Traits`, vea el tema [hash_map (Clase)](../standard-library/hash-map-class.md).  
  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [key_comp](#key_comp) para obtener un ejemplo de cómo declarar y usar `key_compare`.  
  
##  <a name="key_type"></a>  hash_map::key_type  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Tipo que describe el objeto de clave de ordenación que constituye cada elemento del objeto hash_map.  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 `key_type` es un sinónimo del parámetro de plantilla `Key`.  
  
 Para obtener más información sobre `Key`, vea la sección Comentarios del tema [hash_map (Clase)](../standard-library/hash-map-class.md).  
  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [value_type](#value_type) para obtener un ejemplo de cómo declarar y usar `key_type`.  
  
##  <a name="lower_bound"></a>  hash_map::lower_bound  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Devuelve un iterador al primer elemento de un objeto hash_map cuyo valor de clave es igual o mayor que el de una clave especificada.  
  
```  
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Valor de clave de argumento que se comparará con la clave de ordenación de un elemento del objeto hash_map que se está buscando.  
  
### <a name="return-value"></a>Valor devuelto  
 [Iterator](#iterator) o [const_iterator](#const_iterator) que se dirige a la ubicación de un elemento en un objeto hash_map que tiene un valor de clave igual o mayor que la clave de argumento, o que se dirige a la ubicación siguiente al último elemento del objeto hash_map si no se encuentra ninguna coincidencia con la clave.  
  
 Si el valor devuelto de `lower_bound` se asigna a un `const_iterator`, no se puede modificar el objeto hash_map. Si el valor devuelto de `lower_bound` se asigna a un **iterator**, se puede modificar el objeto hash_map.  
  
### <a name="remarks"></a>Comentarios  
  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_lower_bound.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_RcIter = hm1.lower_bound( 2 );  
   cout << "The first element of hash_map hm1 with a key of 2 is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   // If no match is found for the key, end( ) is returned  
   hm1_RcIter = hm1. lower_bound ( 4 );  
  
   if ( hm1_RcIter == hm1.end( ) )  
      cout << "The hash_map hm1 doesn't have an element "  
           << "with a key of 4." << endl;  
   else  
      cout << "The element of hash_map hm1 with a key of 4 is: "  
           << hm1_RcIter -> second << "." << endl;  
  
   // An element at a specific location in the hash_map can be   
   // found using a dereferenced iterator addressing the location  
   hm1_AcIter = hm1.end( );  
   hm1_AcIter--;  
   hm1_RcIter = hm1. lower_bound ( hm1_AcIter -> first );  
   cout << "The element of hm1 with a key matching "  
        << "that of the last element is: "  
        << hm1_RcIter -> second << "." << endl;  
}  
```  
  
```Output  
The first element of hash_map hm1 with a key of 2 is: 20.  
The hash_map hm1 doesn't have an element with a key of 4.  
The element of hm1 with a key matching that of the last element is: 30.  
```  
  
##  <a name="mapped_type"></a>  hash_map::mapped_type  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Tipo que representa el tipo de datos almacenado en un objeto hash_map.  
  
```  
typedef Type mapped_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo `mapped_type` es un sinónimo del parámetro de plantilla `Type`.  
  
 Para obtener más información sobre `Type`, vea el tema [hash_map (Clase)](../standard-library/hash-map-class.md).  
  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [value_type](#value_type) para obtener un ejemplo de cómo declarar y usar `key_type`.  
  
##  <a name="max_size"></a>  hash_map::max_size  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Devuelve la longitud máxima del objeto hash_map.  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Longitud máxima posible del objeto hash_map.  
  
### <a name="remarks"></a>Comentarios  
  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_max_size.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
   hash_map <int, int> :: size_type i;  
  
   i = hm1.max_size( );     
   cout << "The maximum possible length "  
        << "of the hash_map is " << i << "."  
        << endl << "(Magnitude is machine specific.)";  
}  
```  
  
##  <a name="op_at"></a>  hash_map::operator[]  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Inserta un elemento en un `hash_map` con un valor de clave especificado.  
  
```  
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`key`|El valor de clave del elemento que se tiene que insertar.|  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al valor de datos del elemento insertado.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor de clave de argumento no se encuentra, se inserta junto con el valor predeterminado del tipo de datos.  
  
 `operator[]` puede usarse para insertar elementos en un `hash_map m` con  
  
 `m[ key] = DataValue`;  
  
 donde DataValue es el valor del `mapped_type` del elemento con un valor de clave de `key`.  
  
 Cuando se usa `operator[]` para insertar elementos, la referencia devuelta no indica si una inserción cambia un elemento ya existente o crea uno nuevo. Se pueden usar las funciones miembro [find](../standard-library/map-class.md#find) e [insert](../standard-library/map-class.md#insert) para determinar si ya existe un elemento con una clave especificada antes de una inserción.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_op_ref.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
#include <string>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   typedef pair <const int, int> cInt2Int;  
   hash_map <int, int> hm1;  
   hash_map <int, int> :: iterator pIter;  
  
   // Insert a data value of 10 with a key of 1  
   // into a hash_map using the operator[] member function  
   hm1[ 1 ] = 10;  
  
   // Compare other ways to insert objects into a hash_map  
   hm1.insert ( hash_map <int, int> :: value_type ( 2, 20 ) );  
   hm1.insert ( cInt2Int ( 3, 30 ) );  
  
   cout  << "The keys of the mapped elements are:";  
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )  
      cout << " " << pIter -> first;  
   cout << "." << endl;  
  
   cout  << "The values of the mapped elements are:";  
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )  
      cout << " " << pIter -> second;  
   cout << "." << endl;  
  
   // If the key already exists, operator[]  
   // changes the value of the datum in the element  
   hm1[ 2 ] = 40;  
  
   // operator[] will also insert the value of the data  
   // type's default constructor if the value is unspecified  
   hm1[5];  
  
   cout  << "The keys of the mapped elements are now:";  
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )  
      cout << " " << pIter -> first;  
   cout << "." << endl;  
  
   cout  << "The values of the mapped elements are now:";  
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )  
      cout << " " << pIter -> second;  
   cout << "." << endl;  
  
   // opperator[] will also insert by moving a key  
   hash_map <string, int> hm2;  
   string str("a");  
   hm2[move(str)] = 1;  
   cout << "The moved key is " << hm2.begin()->first  
      << ", with value " << hm2.begin()->second << endl;  
}  
```  
  
##  <a name="op_eq"></a>  hash_map::operator=  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Reemplaza los elementos del objeto hash_map por una copia de otro objeto hash_map.  
  
```  
hash_map& operator=(const hash_map& right);

hash_map& operator=(hash_map&& right);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`right`|Objeto [hash_map (Clase)](../standard-library/hash-map-class.md) que se copia a `hash_map`.|  
  
### <a name="remarks"></a>Comentarios  
 Después de borrar todos los elementos existentes en un `hash_map`, `operator=` copia o mueve el contenido de `right` al `hash_map`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_operator_as.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map<int, int> v1, v2, v3;  
   hash_map<int, int>::iterator iter;  
  
   v1.insert(pair<int, int>(1, 10));  
  
   cout << "v1 = " ;  
   for (iter = v1.begin(); iter != v1.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
  
   v2 = v1;  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
  
// move v1 into v2  
   v2.clear();  
   v2 = move(v1);  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
}  
```  
  
##  <a name="pointer"></a>  hash_map::pointer  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Tipo que proporciona un puntero a un elemento de un objeto hash_map.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;  
```  
  
### <a name="remarks"></a>Comentarios  
 Se puede usar un tipo **pointer** para modificar el valor de un elemento.  
  
 En la mayoría de los casos, se debe usar [iterator](#iterator) para obtener acceso a los elementos de un objeto hash_map.  
  
  
##  <a name="rbegin"></a>  hash_map::rbegin  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Devuelve un iterador que se dirige al primer elemento en un objeto hash_map invertido.  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador bidireccional inverso que se dirige al primer elemento de un objeto hash_map invertido o lo que ha sido el último elemento del objeto hash_map sin invertir.  
  
### <a name="remarks"></a>Comentarios  
 `rbegin` se usa con un hash_map invertido igual que [begin](#begin) se usa con un hash_map.  
  
 Si el valor devuelto de `rbegin` se asigna a [const_reverse_iterator](#const_reverse_iterator), no se puede modificar el objeto hash_map. Si el valor devuelto de `rbegin` se asigna a [reverse_iterator](#reverse_iterator), se puede modificar el objeto hash_map.  
  
 `rbegin` puede usarse para iterar un objeto hash_map hacia atrás.  
  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_rbegin.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
  
   hash_map <int, int> :: iterator hm1_Iter;  
   hash_map <int, int> :: reverse_iterator hm1_rIter;  
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_rIter = hm1.rbegin( );  
   cout << "The first element of the reversed hash_map hm1 is "  
        << hm1_rIter -> first << "." << endl;  
  
   // begin can be used to start an iteration   
   // through a hash_map in a forward order  
   cout << "The hash_map is: ";  
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)  
      cout << hm1_Iter -> first << " ";  
      cout << "." << endl;  
  
   // rbegin can be used to start an iteration   
   // through a hash_map in a reverse order  
   cout << "The reversed hash_map is: ";  
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)  
      cout << hm1_rIter -> first << " ";  
      cout << "." << endl;  
  
   // A hash_map element can be erased by dereferencing to its key   
   hm1_rIter = hm1.rbegin( );  
   hm1.erase ( hm1_rIter -> first );  
  
   hm1_rIter = hm1.rbegin( );  
   cout << "After the erasure, the first element "  
        << "in the reversed hash_map is "  
        << hm1_rIter -> first << "." << endl;  
}  
```  
  
```Output  
The first element of the reversed hash_map hm1 is 3.  
The hash_map is: 1 2 3 .  
The reversed hash_map is: 3 2 1 .  
After the erasure, the first element in the reversed hash_map is 2.  
```  
  
##  <a name="reference"></a>  hash_map::reference  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Tipo que proporciona una referencia a un elemento almacenado en un objeto hash_map.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;  
```  
  
### <a name="remarks"></a>Comentarios  
  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_reference.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the key of the first element  
   const int &Ref1 = ( hm1.begin( ) -> first );  
  
   // The following line would cause an error as the   
   // non-const_reference cannot be used to access the key  
   // int &Ref1 = ( hm1.begin( ) -> first );  
  
   cout << "The key of first element in the hash_map is "  
        << Ref1 << "." << endl;  
  
   // Declare and initialize a reference &Ref2   
   // to the data value of the first element  
   int &Ref2 = ( hm1.begin( ) -> second );  
  
   cout << "The data value of first element in the hash_map is "  
        << Ref2 << "." << endl;  
  
   // The non-const_reference can be used to modify the   
   // data value of the first element  
   Ref2 = Ref2 + 5;  
   cout << "The modified data value of first element is "  
        << Ref2 << "." << endl;  
}  
```  
  
```Output  
The key of first element in the hash_map is 1.  
The data value of first element in the hash_map is 10.  
The modified data value of first element is 15.  
```  
  
##  <a name="rend"></a>  hash_map::rend  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Devuelve un iterador que se dirige a la ubicación que sigue al último elemento en un objeto hash_map invertido.  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador bidireccional inverso que se dirige a la ubicación siguiente al último elemento de un objeto hash_map invertido (la ubicación que había precedido al primer elemento del objeto hash_map sin invertir).  
  
### <a name="remarks"></a>Comentarios  
 `rend` se usa con un hash_map invertido igual que [end](#end) se usa con un hash_map.  
  
 Si el valor devuelto de `rend` se asigna a [const_reverse_iterator](#const_reverse_iterator), no se puede modificar el objeto hash_map. Si el valor devuelto de `rend` se asigna a [reverse_iterator](#reverse_iterator), se puede modificar el objeto hash_map.  
  
 Se puede usar `rend` para comprobar si un iterador inverso ha llegado al final de su objeto hash_map.  
  
 El valor devuelto por `rend` no se debe desreferenciar.  
  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_rend.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
  
   hash_map <int, int> :: iterator hm1_Iter;  
   hash_map <int, int> :: reverse_iterator hm1_rIter;  
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_rIter = hm1.rend( );  
   hm1_rIter--;  
   cout << "The last element of the reversed hash_map hm1 is "  
        << hm1_rIter -> first << "." << endl;  
  
   // begin can be used to start an iteration   
   // through a hash_map in a forward order  
   cout << "The hash_map is: ";  
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( );  
   hm1_Iter++)  
      cout << hm1_Iter -> first << " ";  
      cout << "." << endl;  
  
   // rbegin can be used to start an iteration   
   // through a hash_map in a reverse order  
   cout << "The reversed hash_map is: ";  
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( );  
      hm1_rIter++)  
      cout << hm1_rIter -> first << " ";  
      cout << "." << endl;  
  
   // A hash_map element can be erased by dereferencing to its key   
   hm1_rIter = --hm1.rend( );  
   hm1.erase ( hm1_rIter -> first );  
  
   hm1_rIter = hm1.rend( );  
   hm1_rIter--;  
   cout << "After the erasure, the last element "  
        << "in the reversed hash_map is "  
        << hm1_rIter -> first << "." << endl;  
}  
```  
  
```Output  
The last element of the reversed hash_map hm1 is 1.  
The hash_map is: 1 2 3 .  
The reversed hash_map is: 3 2 1 .  
After the erasure, the last element in the reversed hash_map is 2.  
```  
  
##  <a name="reverse_iterator"></a>  hash_map::reverse_iterator  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento en un objeto hash_map invertido.  
  
```  
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 Un tipo `reverse_iterator` no puede modificar el valor de un elemento y se usa para iterar el objeto hash_map en orden inverso.  
  
 El `reverse_iterator` definido mediante el objeto hash_map apunta a elementos que son objetos de [value_type](#value_type), que son de tipo **pair\<const Key, Type>**, cuyo primer miembro es la clave para el elemento y cuyo segundo miembro es la referencia asignada que el elemento conserva.  
  
 A fin de desreferenciar una `reverse_iterator` `rIter` apunta a un elemento de un objeto hash_map, use el operador ->.  
  
 Para tener acceso al valor de clave del elemento, use `rIter` -> **first**, que es equivalente a (\* `rIter`). **first**. Para tener acceso al valor de la referencia asignada del elemento, use `rIter` -> **second**, que es equivalente a (\* `rIter`). **first**.  
  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [rbegin](#rbegin) para obtener un ejemplo de cómo declarar y usar `reverse_iterator`.  
  
##  <a name="size"></a>  hash_map::size  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Devuelve el número de elementos en hash_map.  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud actual de hash_map.  
  
### <a name="remarks"></a>Comentarios  
  
  
### <a name="example"></a>Ejemplo  
  En el ejemplo siguiente se muestra el uso de la función de miembro hash_map::size.  
  
```  
// hash_map_size.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    using namespace stdext;  
    hash_map<int, int> hm1, hm2;  
    hash_map<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    hm1.insert(Int_Pair(1, 1));  
    i = hm1.size();  
    cout << "The hash_map length is " << i << "." << endl;  
  
    hm1.insert(Int_Pair(2, 4));  
    i = hm1.size();  
    cout << "The hash_map length is now " << i << "." << endl;  
}  
```  
  
```Output  
The hash_map length is 1.  
The hash_map length is now 2.  
```  
  
##  <a name="size_type"></a>  hash_map::size_type  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Tipo entero sin signo que puede representar el número de elementos de un objeto hash_map.  
  
```  
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;  
```  
  
### <a name="remarks"></a>Comentarios  
  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [size](#size) para obtener un ejemplo de cómo declarar y usar `size_type`.  
  
##  <a name="swap"></a>  hash_map::swap  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Intercambia los elementos de dos objetos hash_map.  
  
```  
void swap(hash_map& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 Objeto hash_map de argumentos que proporciona los elementos que se van a intercambiar con el objeto hash_map de destino.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro no invalida ninguna referencia, puntero o iterador que designen los elementos de los dos objetos hash_map cuyos elementos se intercambian.  
  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_swap.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1, hm2, hm3;  
   hash_map <int, int>::iterator hm1_Iter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
   hm2.insert ( Int_Pair ( 10, 100 ) );  
   hm2.insert ( Int_Pair ( 20, 200 ) );  
   hm3.insert ( Int_Pair ( 30, 300 ) );  
  
   cout << "The original hash_map hm1 is:";  
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )  
      cout << " " << hm1_Iter -> second;  
   cout   << "." << endl;  
  
   // This is the member function version of swap  
   // hm2 is said to be the argument hash_map;   
   // hm1 is said to be the target hash_map  
   hm1.swap( hm2 );  
  
   cout << "After swapping with hm2, hash_map hm1 is:";  
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )  
      cout << " " << hm1_Iter -> second;  
   cout  << "." << endl;  
  
   // This is the specialized template version of swap  
   swap( hm1, hm3 );  
  
   cout << "After swapping with hm3, hash_map hm1 is:";  
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )  
      cout << " " << hm1_Iter -> second;  
   cout   << "." << endl;  
}  
```  
  
```Output  
The original hash_map hm1 is: 10 20 30.  
After swapping with hm2, hash_map hm1 is: 100 200.  
After swapping with hm3, hash_map hm1 is: 300.  
```  
  
##  <a name="upper_bound"></a>  hash_map::upper_bound  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Devuelve un iterador al primer elemento de un objeto hash_map cuyo valor de clave es mayor que el de una clave especificada.  
  
```  
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Valor de clave de argumento que se comparará con el valor de clave de ordenación de un elemento del objeto hash_map que se está buscando.  
  
### <a name="return-value"></a>Valor devuelto  
 [Iterator](#iterator) o [const_iterator](#const_iterator) que se dirige a la ubicación de un elemento en un objeto hash_map que tiene un valor de clave mayor que la clave de argumento, o que se dirige a la ubicación siguiente al último elemento del objeto hash_map si no se encuentra ninguna coincidencia con la clave.  
  
 Si el valor devuelto se asigna a un `const_iterator`, no se puede modificar el objeto hash_map. Si el valor devuelto se asigna a un **iterator**, se puede modificar el objeto hash_map.  
  
### <a name="remarks"></a>Comentarios  
  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_upper_bound.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
   hash_map <int, int> hm1;  
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   hm1.insert ( Int_Pair ( 1, 10 ) );  
   hm1.insert ( Int_Pair ( 2, 20 ) );  
   hm1.insert ( Int_Pair ( 3, 30 ) );  
  
   hm1_RcIter = hm1.upper_bound( 2 );  
   cout << "The first element of hash_map hm1 with a key "  
        << "greater than 2 is: "  
        << hm1_RcIter -> second << "." << endl;  
  
   // If no match is found for the key, end is returned  
   hm1_RcIter = hm1. upper_bound ( 4 );  
  
   if ( hm1_RcIter == hm1.end( ) )  
      cout << "The hash_map hm1 doesn't have an element "  
           << "with a key greater than 4." << endl;  
   else  
      cout << "The element of hash_map hm1 with a key > 4 is: "  
           << hm1_RcIter -> second << "." << endl;  
  
   // The element at a specific location in the hash_map can be found   
   // using a dereferenced iterator addressing the location  
   hm1_AcIter = hm1.begin( );  
   hm1_RcIter = hm1. upper_bound ( hm1_AcIter -> first );  
   cout << "The 1st element of hm1 with a key greater than "  
        << "that\n of the initial element of hm1 is: "  
        << hm1_RcIter -> second << "." << endl;  
}  
```  
  
```Output  
The first element of hash_map hm1 with a key greater than 2 is: 30.  
The hash_map hm1 doesn't have an element with a key greater than 4.  
The 1st element of hm1 with a key greater than that  
 of the initial element of hm1 is: 20.  
```  
  
##  <a name="value_comp"></a>  hash_map::value_comp  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Devuelve un objeto de función que determina el orden de los elementos de un objeto hash_map mediante la comparación de sus valores de clave.  
  
```  
value_compare value_comp() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el objeto de función de comparación que un objeto hash_map usa para ordenar sus elementos.  
  
### <a name="remarks"></a>Comentarios  
 Para un objeto hash_map *m*, si dos elementos *e*1 *(k*1 *, d*1 *)* y *e*2 *(k*2 *, d*2 *)* son objetos de tipo [value_type](#value_type), donde *k*1 y *k*2 son sus claves de tipo [key_type](#key_type) y `d`1 y `d`2 son sus datos de tipo [mapped_type](#mapped_type), entonces *m.*`value_comp`*( )(e*1 *, e*2 *)* es equivalente a *m.*`key_comp`*( ) (k*1 *, k*2 *)*. Un objeto almacenado define la función miembro  
  
 **bool operator**( **value_type&** `left`, **value_type&** `right`) **;**  
  
 que devuelve **True** si el valor de clave de `left` precede y no es igual al valor de clave de `right` en el criterio de ordenación.  
  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_value_comp.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   using namespace stdext;  
  
   hash_map <int, int, hash_compare<int, less<int> > > hm1;  
   hash_map <int, int, hash_compare<int, less<int> > >  
   ::value_compare vc1 = hm1.value_comp( );  
   pair< hash_map<int,int>::iterator, bool > pr1, pr2;  
  
   pr1= hm1.insert ( hash_map <int, int> :: value_type ( 1, 10 ) );  
   pr2= hm1.insert ( hash_map <int, int> :: value_type ( 2, 5 ) );  
  
   if( vc1( *pr1.first, *pr2.first ) == true )     
   {  
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."  
           << endl;  
   }  
   else     
   {  
      cout << "The element ( 1,10 ) does not precede the element ( 2,5 )."  
           << endl;  
   }  
  
   if( vc1 ( *pr2.first, *pr1.first ) == true )  
   {  
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."  
           << endl;  
   }  
   else     
   {  
      cout << "The element ( 2,5 ) does not precede the element ( 1,10 )."  
           << endl;  
   }  
}  
```  
  
##  <a name="value_type"></a>  hash_map::value_type  
  
> [!NOTE]
>  Esta API está obsoleta. La alternativa es la [clase unordered_map](../standard-library/unordered-map-class.md).  
  
 Tipo que representa el tipo de objeto almacenado en un objeto hash_map.  
  
```  
typedef pair<const Key, Type> value_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 `value_type` se declara como `pair` *\<***const**[key_type](#key_type), [mapped_type](#mapped_type)*>* y no `pair`**\<key_type, mapped_type>** porque las claves de un contenedor asociativo no pueden cambiarse mediante un iterador no constante o una referencia.  
  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// hash_map_value_type.cpp  
// compile with: /EHsc  
#include <hash_map>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   using namespace stdext;  
   typedef pair <const int, int> cInt2Int;  
   hash_map <int, int> hm1;  
   hash_map <int, int> :: key_type key1;  
   hash_map <int, int> :: mapped_type mapped1;  
   hash_map <int, int> :: value_type value1;  
   hash_map <int, int> :: iterator pIter;  
  
   // value_type can be used to pass the correct type  
   // explicitely to avoid implicit type conversion  
   hm1.insert ( hash_map <int, int> :: value_type ( 1, 10 ) );  
  
   // Compare other ways to insert objects into a hash_map  
   hm1.insert ( cInt2Int ( 2, 20 ) );  
   hm1[ 3 ] = 30;  
  
   // Initializing key1 and mapped1  
   key1 = ( hm1.begin( ) -> first );  
   mapped1 = ( hm1.begin( ) -> second );  
  
   cout << "The key of first element in the hash_map is "  
        << key1 << "." << endl;  
  
   cout << "The data value of first element in the hash_map is "  
        << mapped1 << "." << endl;  
  
   // The following line would cause an error because  
   // the value_type is not assignable  
   // value1 = cInt2Int ( 4, 40 );  
  
   cout  << "The keys of the mapped elements are:";  
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )  
      cout << " " << pIter -> first;  
   cout << "." << endl;  
  
   cout  << "The values of the mapped elements are:";  
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )  
      cout << " " << pIter -> second;  
   cout << "." << endl;  
}  
```  
  
```Output  
The key of first element in the hash_map is 1.  
The data value of first element in the hash_map is 10.  
The keys of the mapped elements are: 1 2 3.  
The values of the mapped elements are: 10 20 30.  
```  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)

