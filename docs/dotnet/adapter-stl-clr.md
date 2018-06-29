---
title: adaptador (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 06/15/2018
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/adapter>
- cliext::collection_adapter
- cliext::collection_adapter::base
- cliext::collection_adapter::begin
- cliext::collection_adapter
- cliext::collection_adapter::collection_adapter
- cliext::collection_adapter::difference_type
- cliext::collection_adapter::end
- cliext::collection_adapter::iterator
- cliext::collection_adapter::key_type
- cliext::collection_adapter::mapped_type
- cliext::collection_adapter::operator=
- cliext::collection_adapter::reference
- cliext::collection_adapter::size
- cliext::collection_adapter::size_type
- cliext::collection_adapter::swap
- cliext::collection_adapter::value_type
- cliext::make_collection
- cliext::range_adapter
- cliext::operator=
- cliext::range_adapter::operator=
- cliext::range_adapter::range_adapter
dev_langs:
- C++
helpviewer_keywords:
- <adapter> header [STL/CLR]
- adapter [STL/CLR]
- <cliext/adapter> header [STL/CLR]
- collection_adapter class [STL/CLR]
- base member [STL/CLR]
- begin member [STL/CLR]
- collection_adapter member [STL/CLR]
- difference_type member [STL/CLR]
- end member [STL/CLR]
- iterator member [STL/CLR]
- key_type member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- value_type member [STL/CLR]
- make_collection function [STL/CLR]
- range_adapter class [STL/CLR]
- operator= member [STL/CLR]
- range_adapter member [STL/CLR]
ms.assetid: 71ce7e51-42b6-4f70-9595-303791a97677
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a472284df67993a65de98df7db698ea533451ea3
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079441"
---
# <a name="adapter-stlclr"></a>adapter (STL/CLR)
El encabezado STL/CLR `<cliext/adapter>` especifica dos clases de plantilla (`collection_adapter` y `range_adapter`) y la función de plantilla `make_collection`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#include <cliext/adapter>  
```  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/adaptador >  
  
 **Namespace:** cliext 
  
## <a name="declarations"></a>Declaraciones  
  
|Clase|Descripción|  
|-----------|-----------------|  
|[collection_adapter (STL/CLR)](#collection_adapter)|Encapsula la colección de la biblioteca de clases Base (BCL) como un intervalo.|  
|[range_adapter (STL/CLR)](#range_adapter)|Ajusta el intervalo como una colección de BCL.|  

|Función|Descripción|  
|--------------|-----------------|  
|[make_collection (STL/CLR)](#make_collection)|Crea un adaptador de intervalo mediante un par de iteradores.|   
  
## <a name="members"></a>Miembros

## <a name="collection_adapter"></a> collection_adapter (STL/CLR)
Encapsula una colección de .NET para su uso como un contenedor STL/CLR. A `collection_adapter` es una clase de plantilla que describe un objeto de contenedor STL/CLR simple. Ajusta una interfaz de biblioteca de clases Base (BCL) y devuelve un par de iteradores que se utiliza para manipular la secuencia controlada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template<typename Coll>  
    ref class collection_adapter;  
  
template<>  
    ref class collection_adapter<  
        System::Collections::ICollection>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IEnumerable>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IList>;  
template<>  
    ref class collection_adapter<  
        System::Collections::IDictionary>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::ICollection<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IEnumerable<Value>>;  
template<typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IList<Value>>;  
template<typename Key,  
    typename Value>  
    ref class collection_adapter<  
        System::Collections::Generic::IDictionary<Key, Value>>;  
```  
  
##### <a name="parameters"></a>Parámetros  
 Coll  
 El tipo de la colección ajustada.  
  
### <a name="specializations"></a>Especializaciones  
  
|Especialización|Descripción|  
|--------------------|-----------------|  
|IEnumerable|Secuencias a través de los elementos.|  
|ICollection|Mantiene un grupo de elementos.|  
|IList|Mantiene un grupo ordenado de elementos.|  
|IDictionary|Mantener un conjunto de {clave, valor} pares.|  
|IEnumerable\<valor >|Secuencias a través de los elementos con tipo.|  
|ICollection\<valor >|Mantiene un grupo de elementos con tipo.|  
|IList\<valor >|Mantiene un grupo ordenado de elementos con tipo.|  
|IDictionary\<valor >|Mantiene un conjunto de tipo {clave, valor} pares.|  
  
### <a name="members"></a>Miembros  
  
|Definición de tipo|Descripción|  
|---------------------|-----------------|  
|[collection_adapter::difference_type (STL/CLR)](#difference_type)|El tipo de una distancia con signo entre dos elementos.|  
|[collection_adapter::iterator (STL/CLR)](#iterator)|El tipo de un iterador para la secuencia controlada.|  
|[collection_adapter::key_type (STL/CLR)](#key_type)|El tipo de una clave de diccionario.|  
|[collection_adapter::mapped_type (STL/CLR)](#mapped_type)|El tipo de un valor del diccionario.|  
|[collection_adapter::reference (STL/CLR)](#reference)|El tipo de una referencia a un elemento.|  
|[collection_adapter::size_type (STL/CLR)](#size_type)|El tipo de una distancia con signo entre dos elementos.|  
|[collection_adapter::value_type (STL/CLR)](#value_type)|El tipo de un elemento.|  
  
|Función miembro|Descripción|  
|---------------------|-----------------|  
|[collection_adapter::base (STL/CLR)](#base)|Designa la interfaz BCL ajustada.|  
|[collection_adapter::begin (STL/CLR)](#begin)|Designa el principio de la secuencia controlada.|  
|[collection_adapter::collection_adapter (STL/CLR)](#collection_adapter_collection_adapter)|Construye un objeto de adaptador.|  
|[collection_adapter::end (STL/CLR)](#end)|Designa el final de la secuencia controlada.|  
|[collection_adapter::size (STL/CLR)](#size)|Cuenta el número de elementos.|  
|[collection_adapter::swap (STL/CLR)](#swap)|Intercambia el contenido de dos contenedores.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[collection_adapter::operator= (STL/CLR)](#op_eq)|Reemplaza el identificador BCL almacenado.|  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta clase de plantilla para manipular un contenedor BCL como un contenedor STL/CLR. El `collection_adapter` almacena un identificador a una interfaz BCL, que a su vez controla una secuencia de elementos. A `collection_adapter` objeto `X` devuelve un par de iteradores de entrada `X.begin()` y `X.end()` que se utiliza para visitar los elementos en orden. Algunas de las especializaciones también permiten escribir `X.size()` para determinar la longitud de la secuencia controlada.  

## <a name="base"></a> collection_adapter::base (STL/CLR)
Designa la interfaz BCL ajustada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
Coll^ base();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve el identificador de interfaz BCL almacenado.  
  
### <a name="example"></a>Ejemplo  
  
```cpp
// cliext_collection_adapter_base.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
    Mycoll c1(%d6x);   
  
// display initial contents " x x x x x x"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("base() same = {0}", c1.base() == %c1);   
    return (0);   
    }  
  
```  
  
```Output  
 x x x x x x  
base() same = True  
```  

## <a name="begin"></a> collection_adapter::begin (STL/CLR)
Designa el principio de la secuencia controlada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
iterator begin();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un iterador de entrada que designa el primer elemento de la secuencia controlada o más allá del final de una secuencia vacía.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_collection_adapter_begin.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Mycoll::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*begin() = a  
*++begin() = b  
```  

## <a name="collection_adapter_collection_adapter"></a> collection_adapter::collection_adapter (STL/CLR)
Construye un objeto de adaptador.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
collection_adapter();  
collection_adapter(collection_adapter<Coll>% right);  
collection_adapter(collection_adapter<Coll>^ right);  
collection_adapter(Coll^ collection);  
```  
  
#### <a name="parameters"></a>Parámetros  
 colección  
 Identificador BCL que va a contener.  
  
 right  
 Objeto que se va a copiar.  
  
### <a name="remarks"></a>Comentarios  
 El constructor:  
  
 `collection_adapter();`  
  
 Inicializa el identificador almacenado con `nullptr`.  
  
 El constructor:  
  
 `collection_adapter(collection_adapter<Coll>% right);`  
  
 Inicializa el identificador almacenado con `right.` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`.  
  
 El constructor:  
  
 `collection_adapter(collection_adapter<Coll>^ right);`  
  
 Inicializa el identificador almacenado con `right->` [collection_adapter::base (STL/CLR)](../dotnet/collection-adapter-base-stl-clr.md)`()`.  
  
 El constructor:  
  
 `collection_adapter(Coll^ collection);`  
  
 Inicializa el identificador almacenado con `collection`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp 
// cliext_collection_adapter_construct.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
  
// construct an empty container   
    Mycoll c1;   
    System::Console::WriteLine("base() null = {0}", c1.base() == nullptr);   
  
// construct with a handle   
    Mycoll c2(%d6x);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mycoll c3(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mycoll c4(%c3);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
base() null = True  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  

## <a name="difference_type"></a> collection_adapter::difference_type (STL/CLR)
Los tipos de una distancia con signo entre dos elementos.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un recuento con signo del elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp 
// cliext_collection_adapter_difference_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Mycoll::difference_type diff = 0;   
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```  

## <a name="end"></a> collection_adapter::end (STL/CLR)
Designa el final de la secuencia controlada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
iterator end();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un iterador de entrada que apunta justo después del final de la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp 
// cliext_collection_adapter_end.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="iterator"></a> collection_adapter::Iterator (STL/CLR)
El tipo de un iterador para la secuencia controlada.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto de tipo no especificado `T1` que puede actuar como un iterador de entrada para la secuencia controlada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_collection_adapter_iterator.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="key_type"></a> collection_adapter::KEY_TYPE (STL/CLR)
El tipo de una clave de diccionario.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla `Key`, en una especialización para `IDictionary` o `IDictionary<Value>`; en caso contrario, no está definido.  
  
### <a name="example"></a>Ejemplo  
  
```cpp
// cliext_collection_adapter_key_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef cliext::collection_adapter<   
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;   
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;   
int main()   
    {   
    Mymap d1;   
    d1.insert(Mymap::make_value(L'a', 1));   
    d1.insert(Mymap::make_value(L'b', 2));   
    d1.insert(Mymap::make_value(L'c', 3));   
    Mycoll c1(%d1);   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mypair elem in c1)   
        {   
        Mycoll::key_type key = elem.Key;   
        Mycoll::mapped_type value = elem.Value;   
        System::Console::Write(" [{0} {1}]", key, value);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="mapped_type"></a> collection_adapter::mapped_type (STL/CLR)
El tipo de un valor del diccionario.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef Value mapped_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla `Value`, en una especialización para `IDictionary` o `IDictionary<Value>`; en caso contrario, no está definido.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_collection_adapter_mapped_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
typedef cliext::collection_adapter<   
    System::Collections::Generic::IDictionary<wchar_t, int>> Mycoll;   
typedef System::Collections::Generic::KeyValuePair<wchar_t,int> Mypair;   
int main()   
    {   
    Mymap d1;   
    d1.insert(Mymap::make_value(L'a', 1));   
    d1.insert(Mymap::make_value(L'b', 2));   
    d1.insert(Mymap::make_value(L'c', 3));   
    Mycoll c1(%d1);   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mypair elem in c1)   
        {   
        Mycoll::key_type key = elem.Key;   
        Mycoll::mapped_type value = elem.Value;   
        System::Console::Write(" [{0} {1}]", key, value);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="op_eq"></a> collection_adapter::operator = (STL/CLR)
Reemplaza el identificador BCL almacenado.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
collection_adapter<Coll>% operator=(collection_adapter<Coll>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 right  
 Adaptador para copiar.  
  
### <a name="remarks"></a>Comentarios  
 Las copias de operador de miembro `right` en el objeto, a continuación, devuelve `*this`. Úselo para reemplazar el identificador BCL almacenado con una copia del identificador BCL almacenado en `right`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp 
// cliext_collection_adapter_operator_as.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mycoll c2;   
    c2 = c1;   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="reference"></a> collection_adapter::Reference (STL/CLR)
El tipo de una referencia a un elemento.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una referencia a un elemento.  
  
### <a name="example"></a>Ejemplo  
  
```cpp 
// cliext_collection_adapter_reference.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        Mycoll::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="size"></a> collection_adapter::Size (STL/CLR)
Cuenta el número de elementos.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
size_type size();  
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve la longitud de la secuencia controlada. No está definido en una especialización para `IEnumerable` o `IEnumerable<Value>`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_collection_adapter_size.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
    Mycoll c1(%d6x);   
  
// display initial contents " x x x x x x"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 x x x x x x  
size() = 6  
```  

## <a name="size_type"></a> collection_adapter::size_type (STL/CLR)
El tipo de una distancia con signo entre dos elementos.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef int size_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un recuento de elemento no negativo.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_collection_adapter_size_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
    Mycoll c1(%d6x);   
  
// display initial contents " x x x x x x"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    Mycoll::size_type size = c1.size();   
    System::Console::WriteLine("size() = {0}", size);   
    return (0);   
    }  
  
```  
  
```Output  
 x x x x x x  
size() = 6  
```  

## <a name="swap"></a> collection_adapter::swap (STL/CLR)
Intercambia el contenido de dos contenedores.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void swap(collection_adapter<Coll>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 right  
 Contenedor con el que se va a intercambiar el contenido.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro intercambia los identificadores BCL almacenados entre `*this` y `right`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp
// cliext_collection_adapter_swap.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    cliext::deque<wchar_t> d2(5, L'x');   
    Mycoll c2(%d2);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
x x x x x  
x x x x x  
a b c  
```  

## <a name="value_type"></a> collection_adapter::value_type (STL/CLR)
El tipo de un elemento.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla `Value`, si está presente en la especialización; en caso contrario, es un sinónimo de `System::Object^`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_collection_adapter_value_type.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display contents " a b c" using value_type   
    for (Mycoll::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   // store element in value_type object   
        Mycoll::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="make_collection"></a> make_collection (STL/CLR)
Realizar una `range_adapter` de un par de iteradores.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template<typename Iter>  
    range_adapter<Iter> make_collection(Iter first, Iter last);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Iter`  
 El tipo de los iteradores ajustados.  
  
 `first`  
 Primer iterador que se va a ajustar.  
  
 `last`  
 Segundo iterador del que va a contener.  
  
### <a name="remarks"></a>Comentarios  
 La función de plantilla devuelve `gcnew range_adapter<Iter>(first, last)`. Utilícelo para construir un `range_adapter<Iter>` objeto a partir de un par de iteradores.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_make_collection.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::deque<wchar_t> Mycont;   
typedef cliext::range_adapter<Mycont::iterator> Myrange;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in d1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Collections::ICollection^ p1 =   
        cliext::make_collection(d1.begin(), d1.end());   
    System::Console::WriteLine("Count = {0}", p1->Count);   
    System::Console::WriteLine("IsSynchronized = {0}",   
        p1->IsSynchronized);   
    System::Console::WriteLine("SyncRoot not nullptr = {0}",   
        p1->SyncRoot != nullptr);   
  
// copy the sequence   
    cli::array<System::Object^>^ a1 = gcnew cli::array<System::Object^>(5);   
  
    a1[0] = L'|';   
    p1->CopyTo(a1, 1);   
    a1[4] = L'|';   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
Count = 3  
IsSynchronized = False  
SyncRoot not nullptr = True  
 | a b c |  
```  

## <a name="range_adapter"></a> range_adapter (STL/CLR)
Una clase de plantilla que contenga un par de iteradores que se usan para implementar varias interfaces de la biblioteca de clases Base (BCL). Utilice la range_adapter para manipular un intervalo STL/CLR como si fuera una colección de BCL.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
template<typename Iter>  
    ref class range_adapter  
        :   public  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<Value>,  
        System::Collections::Generic::ICollection<Value>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parámetros  
 ITER  
 El tipo asociado con los iteradores ajustados.  
  
### <a name="members"></a>Miembros  
  
|Función miembro|Descripción|  
|---------------------|-----------------|  
|[range_adapter::range_adapter (STL/CLR)](#range_adapter_range_adapter)|Construye un objeto de adaptador.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[range_adapter::operator= (STL/CLR)](#range_adapter_op_eq)|Reemplaza el par de iterador almacenado.|  
  
### <a name="interfaces"></a>Interfaces  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:System.Collections.IEnumerable>|Recorre en iteración los elementos de la colección.|  
|<xref:System.Collections.ICollection>|Mantiene un grupo de elementos.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Recorre en iteración los elementos con tipo en la colección...|  
|<xref:System.Collections.Generic.ICollection%601>|Mantiene un grupo de elementos con tipo.|  
  
### <a name="remarks"></a>Comentarios  
 El range_adapter almacena un par de iteradores, que a su vez delimitar una secuencia de elementos. El objeto implementa cuatro interfaces BCL que le permiten recorrer en iteración los elementos en orden. Utilice esta clase de plantilla para manipular los intervalos STL/CLR como contenedores BCL.  

## <a name="range_adapter_op_eq"></a> range_adapter::operator = (STL/CLR)
Reemplaza el par de iterador almacenado.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
range_adapter<Iter>% operator=(range_adapter<Iter>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 right  
 Adaptador para copiar.  
  
### <a name="remarks"></a>Comentarios  
 Las copias de operador de miembro `right` en el objeto, a continuación, devuelve `*this`. Úselo para reemplazar el par de iterador almacenado con una copia del par de iterador almacenado en `right`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_range_adapter_operator_as.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::deque<wchar_t> Mycont;   
typedef cliext::range_adapter<Mycont::iterator> Myrange;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Myrange c1(d1.begin(), d1.end());   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myrange c2;   
    c2 = c1;   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="range_adapter_range_adapter"></a> range_adapter::range_adapter (STL/CLR)
Construye un objeto de adaptador.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
range_adapter();  
range_adapter(range_adapter<Iter>% right);  
range_adapter(range_adapter<Iter>^ right);  
range_adapter(Iter first, Iter last);  
```  
  
#### <a name="parameters"></a>Parámetros  
 first  
 Primer iterador que se va a ajustar.  
  
 last  
 Segundo iterador del que va a contener.  
  
 right  
 Objeto que se va a copiar.  
  
### <a name="remarks"></a>Comentarios  
 El constructor:  
  
 `range_adapter();`  
  
 Inicializa el par de iterador almacenado con los iteradores construido de forma predeterminada.  
  
 El constructor:  
  
 `range_adapter(range_adapter<Iter>% right);`  
  
 Inicializa el par de iterador almacenado copiando el par almacenado en `right`.  
  
 El constructor:  
  
 `range_adapter(range_adapter<Iter>^ right);`  
  
 Inicializa el par de iterador almacenado copiando el par almacenado en `*right`.  
  
 El constructor:  
  
 `range_adapter(Iter^ first, last);`  
  
 Inicializa el par de iterador almacenado con `first` y `last`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_range_adapter_construct.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::deque<wchar_t> Mycont;   
typedef cliext::range_adapter<Mycont::iterator> Myrange;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
  
// construct an empty adapter   
    Myrange c1;   
  
// construct with an iterator pair   
    Myrange c2(d1.begin(), d1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another adapter   
    Myrange c3(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying an adapter handle   
    Myrange c4(%c3);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a b c  
```  