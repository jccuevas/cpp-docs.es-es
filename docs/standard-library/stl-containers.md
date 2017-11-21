---
title: "Contenedores de la biblioteca estándar de C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- C++ Standard Library, template class containers
- containers, C++ Standard Library
ms.assetid: 8e915ca1-19ba-4f0d-93c8-e2c3bfd638eb
caps.latest.revision: "29"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 86e856a47baa9df0da78e4db926ef64cd47284f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="c-standard-library-containers"></a>Contenedores de la biblioteca estándar de C++
La biblioteca estándar proporciona contenedores con seguridad de tipos para almacenar colecciones de objetos relacionados. Los contenedores son plantillas de clase; al declarar una variable de contenedor, debe especificar el tipo de los elementos que se incluirán en el contenedor. Los contenedores se pueden construir con las listas de inicializadores. Tienen funciones miembro para agregar y quitar elementos, así como para realizar otras operaciones.  
  
 Itere sobre los elementos de un contenedor y obtenga acceso a los elementos individuales mediante [iteradores](../standard-library/iterators.md). Puede usar iteradores de forma explícita mediante el uso de sus funciones de miembro y los operadores, así como las funciones globales. También puede usarlos de forma implícita, por ejemplo, mediante el uso de bucles de tipo range-for. Los iteradores para todos los contenedores de la biblioteca estándar de C++ tienen una interfaz común, pero cada contenedor define sus propios iteradores especializados.  
  
 Los contenedores se pueden dividir en tres categorías: contenedores de secuencias, contenedores asociativos y adaptadores de contenedor.  
  
##  <a name="sequence_containers"></a> Contenedores de secuencias  
 Los contenedores de secuencias mantienen el orden de los elementos insertados que especifique.  
  
 Un contenedor de `vector` se comporta como una matriz, pero puede crecer automáticamente según sea necesario. Su acceso es aleatorio y se almacena de forma contigua, y su longitud es muy flexible. Por estas y otras razones, `vector` es el contenedor preferido de secuencias para la mayoría de las aplicaciones. Si no sabe con seguridad qué tipo de contenedor de secuencias debe utilizar, empiece usando un vector. Para más información, vea [vector (Clase)](../standard-library/vector-class.md).  
  
 Un contenedor de `array` tiene algunas de las ventajas de `vector`, pero la longitud no es tan flexible. Para más información, vea [array (Clase)](../standard-library/array-class-stl.md).  
  
 Un contenedor de `deque` (cola de dos extremos) permite inserciones y eliminaciones rápidas al principio y al final del contenedor. Comparte las ventajas de acceso aleatorio y longitud flexible de `vector`, pero no es contiguo. Para más información, vea [deque (Clase)](../standard-library/deque-class.md).  
  
 Un contenedor de `list` es una lista doblemente vinculada que permite el acceso bidireccional e inserciones y eliminaciones rápidas en cualquier parte del contenedor, pero no permite tener acceso de forma aleatoria a un elemento en el contenedor. Para más información, vea [list (Clase)](../standard-library/list-class.md).  
  
 Un contenedor de `forward_list` es una lista vinculada única (la versión de acceso de avance de `list`). Para más información, vea [forward_list (Clase)](../standard-library/forward-list-class.md).  
  
## <a name="associative-containers"></a>Contenedores asociativos  
 En los contenedores asociativos, los elementos se insertan en un orden predefinido; por ejemplo, por orden ascendente. Los contenedores asociativos sin ordenar también están disponibles. Los contenedores asociativos se pueden agrupar en dos subconjuntos: asignaciones y conjuntos.  
  
 Una `map`, a la que a veces se hace referencia como un diccionario, consta de un par de clave/valor. La clave se utiliza para ordenar la secuencia, y el valor está asociado a esa clave. Por ejemplo, una `map` podría contener claves que representan cada palabra única en un texto y valores correspondientes que representan el número de veces que aparece cada palabra en el texto. La versión no ordenada de `map` es `unordered_map`. Para más información, vea [map (Clase)](../standard-library/map-class.md) y [unordered_map (Clase)](../standard-library/unordered-map-class.md).  
  
 Un `set` es simplemente es un contenedor ascendente de elementos únicos (el valor también es la clave). La versión no ordenada de `set` es `unordered_set`. Para más información, vea [set (Clase)](../standard-library/set-class.md) y [unordered_set (Clase)](../standard-library/unordered-set-class.md).  
  
 Tanto `map` como `set` permiten solo una instancia de una clave o elemento en el contenedor. Si se requieren varias instancias de elementos, utilice `multimap` o `multiset`. Las versiones no ordenadas son `unordered_multimap` y `unordered_multiset`. Para más información, vea los temas [multimap (Clase)](../standard-library/multimap-class.md), [unordered_multimap (Clase)](../standard-library/unordered-multimap-class.md), [multiset (Clase)](../standard-library/multiset-class.md) y [unordered_multiset (Clase)](../standard-library/unordered-multiset-class.md).  
  
 Las asignaciones y los conjuntos no ordenados admiten iteradores bidireccionales, y los homólogos no ordenados admiten los iteradores hacia delante. Para más información, vea [Iteradores](../standard-library/iterators.md).  
  
### <a name="heterogeneous-lookup-in-associative-containers-c14"></a>Búsqueda heterogénea en contenedores asociativos (C++14)  
 Los contenedores asociativos ordenados (map, multimap, set y multiset) ahora admiten la búsqueda heterogénea, lo que significa que ya no es necesario pasar exactamente el mismo tipo de objeto que la clave o el elemento de las funciones miembro como `find()` y `lower_bound()`. En vez de eso, puede pasar cualquier tipo para el que haya definida una sobrecarga `operator<` que permita la comparación con el tipo de clave.  
  
 La búsqueda heterogénea se debe habilitar expresamente al especificar el comparador "functor rombo" `std::less<>` o `std::greater<>` cuando se declara la variable de contenedor, como se muestra aquí:  
  
```  
std::set<BigObject, std::less<>> myNewSet;  
```  
  
 Si usa el comparador predeterminado, el contenedor se comporta exactamente igual que en C++11 y versiones anteriores.  
  
 En el ejemplo siguiente se muestra cómo sobrecargar `operator<` para permitir a los usuarios de un `std::set` realizar búsquedas pasando simplemente una cadena pequeña que se puede comparar con el miembro `BigObject::id` de cada objeto.  
  
```cpp  
#include <set>  
#include <string>  
#include <iostream>  
#include <functional>  
  
using namespace std;  
  
class BigObject  
{  
public:  
    string id;  
    explicit BigObject(const string& s) : id(s) {}  
    bool operator< (const BigObject& other) const  
    {  
        return this->id < other.id;  
    }  
  
    // Other members....  
};  
  
inline bool operator<(const string& otherId, const BigObject& obj)  
{  
    return otherId < obj.id;  
}  
  
inline bool operator<(const BigObject& obj, const string& otherId)  
{  
    return obj.id < otherId;  
}  
  
int main()  
{  
    // Use C++14 brace-init syntax to invoke BigObject(string).  
    // The s suffix invokes string ctor. It is a C++14 user-defined  
    // literal defined in <string>  
    BigObject b1{ "42F"s };   
    BigObject b2{ "52F"s };  
    BigObject b3{ "62F"s };  
    set<BigObject, less<>> myNewSet; // C++14  
    myNewSet.insert(b1);  
    myNewSet.insert(b2);  
    myNewSet.insert(b3);  
    auto it = myNewSet.find(string("62F"));  
    if (it != myNewSet.end())  
        cout << "myNewSet element = " << it->id << endl;   
    else  
        cout << "element not found " << endl;  
  
    // Keep console open in debug mode:  
    cout << endl << "Press Enter to exit.";  
    string s;  
    getline(cin, s);  
    return 0;  
}  
  
//Output: myNewSet element = 62F  
  
```  
  
 Las siguientes funciones miembro de map, multimap, set y multiset se han sobrecargado para admitir búsquedas heterogéneas:  
  
1.  find  
  
2.  count  
  
3.  lower_bound  
  
4.  upper_bound  
  
5.  equal_range  
  
## <a name="container-adapters"></a>Adaptadores de contenedor  
 Un adaptador de contenedor es una variación de un contenedor de secuencia o asociativo que restringe la interfaz para una mayor simplicidad y claridad. Los adaptadores de contenedor no admiten iteradores.  
  
 Un contenedor de `queue` sigue la semántica de FIFO (primero en entrar, primero en salir). El primer elemento *insertado* (es decir, insertado en la cola) es el primero en *sacarse* (es decir, en eliminarse de la cola). Para más información, vea [queue (Clase)](../standard-library/queue-class.md).  
  
 Un contenedor de `priority_queue` se organiza de forma que el elemento que tiene el valor más alto siempre es el primero de la cola. Para más información, vea [priority_queue (Clase)](../standard-library/priority-queue-class.md).  
  
 Un contenedor de `stack` sigue la semántica de LIFO (último en entrar, primero en salir). El último elemento incrustado en la pila es el primer elemento sacado. Para más información, vea [stack (Clase)](../standard-library/stack-class.md).  
  
 Dado que los adaptadores de contenedor no admiten iteradores, no se pueden usar con los algoritmos de la biblioteca estándar de C++. Para más información, vea [Algoritmos](../standard-library/algorithms.md).  
  
## <a name="requirements-for-container-elements"></a>Requisitos para los elementos de contenedor  
 Normalmente los elementos insertados en un contenedor de la biblioteca estándar de C++ pueden ser simplemente de cualquier tipo de objeto si se pueden copiar. Móvil (solo elementos): por ejemplo, los `vector<unique_ptr<T>>` creados mediante `unique_ptr<>` funcionarán siempre que no llame a funciones de miembro que intenten copiarlos.  
  
 Los destructores no pueden producir excepciones.  
  
 Los contenedores asociativos ordenados (descritos anteriormente en este artículo) deben tener un operador de comparación público definido. (De forma predeterminada, el operador es `operator<`, pero se admiten incluso los que no funcionan con `operator<`).  
  
 Algunas operaciones en los contenedores también podrían requerir un constructor público predeterminado y un operador de equivalencia público. Por ejemplo, los contenedores asociativos sin ordenar requieren la compatibilidad de algoritmos hash y de igualdad.  
  
## <a name="accessing-container-elements"></a>Elementos contenedores de acceso  
 El acceso a los elementos de contenedores se realiza mediante iteradores. Para más información, vea [Iteradores](../standard-library/iterators.md).  
  
> [!NOTE]
>  También se pueden usar [bucles for basados en intervalos](../cpp/range-based-for-statement-cpp.md) para recorrer en iteración colecciones de la biblioteca estándar de C++.  
  
## <a name="comparing-containers"></a>Comparar contenedores  
 Todos los contenedores sobrecargan el operador == para comparar dos contenedores del mismo tipo que tienen el mismo tipo de elemento. Se puede usar == para comparar un vector\<string> con otro vector\<string>, pero no se puede usar para comparar un vector\<string> con una list\<string> o un vector\<string> con un vector\<char*>.  En C++98/03 se puede usar [std::equal](algorithm-functions.md#equal) o [std::mismatch](algorithm-functions.md#mismatch) para comparar tipos de contenedores o elementos diferentes. En C++11 también se puede usar [std::is_permutation](algorithm-functions.md#is_permutation). Pero en todos estos casos, las funciones asumen que los contenedores tienen la misma longitud. Si el segundo intervalo es menor que el primero, se producirá un comportamiento indefinido. Si el segundo intervalo es más largo, los resultados pueden ser incorrectos porque la comparación no continúa más allá del final del primer intervalo.  
  
### <a name="comparing-dissimilar-containers-c14"></a>Comparar contenedores diferentes (C++14)  
 En C++14 y versiones posteriores, se pueden comparar contenedores y tipos de elementos diferentes mediante una de las sobrecargas de funciones de **std::equal**, **std::mismatch** o **std::is_permutation** que toman dos intervalos completos. Estas sobrecargas le permiten comparar contenedores de distintas longitudes. Estas sobrecargas son mucho menos susceptibles a errores del usuario y están optimizadas para devolver false en tiempo constante cuando se comparan contenedores de longitudes diferentes. Por tanto, se recomienda usar estas sobrecargas a menos que (1) tenga un motivo muy claro para no hacerlo o (2) use un contenedor [std::list](../standard-library/list-class.md), que no se beneficia de las optimizaciones de doble intervalo.  
  
## <a name="see-also"></a>Vea también  
 [Contenedores](../cpp/containers-modern-cpp.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)   
 [\<contenedor de ejemplo>](../standard-library/sample-container.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

