---
title: Colecciones (C++/CX)
ms.date: 11/19/2018
ms.assetid: 914da30b-aac5-4cd7-9da3-a5ac08cdd72c
ms.openlocfilehash: 59e73b803a0878e88361c7fe75cff556b8eeedcd
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032322"
---
# <a name="collections-ccx"></a>Colecciones (C++/CX)

En un programa C++/CX, puede hacer uso gratuito de contenedores de biblioteca de plantillas estándar (STL) o cualquier otro tipo de colección definido por el usuario. Sin embargo, al pasar colecciones de ida y vuelta a través de la interfaz binaria de aplicación de Windows en tiempo de ejecución (ABI) (por ejemplo, a un control XAML o a un cliente JavaScript), debe usar tipos de colección de Windows runtime.

Windows Runtime define las interfaces para colecciones y tipos relacionados, y C++/CX proporciona las implementaciones concretas de C++ en el archivo de encabezado collection.h. En esta ilustración se muestran las relaciones entre los tipos de colección:

![C&#43;&#43;&#47;árbol de herencia CX para tipos de colección](../cppcx/media/cppcxcollectionsinheritancetree.png "C&#43;&#43;&#47;árbol de herencia CX para tipos de colección")

- La [clase Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) es similar a la [clase std::vector](../standard-library/vector-class.md).

- La [clase Platform::Collections::Map](../cppcx/platform-collections-map-class.md) es similar a la [clase std::map](../standard-library/map-class.md).

- La[clase Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md) y la[clase Platform::Collections::MapView](../cppcx/platform-collections-mapview-class.md) son versiones de solo lectura de `Vector` y la `Map`.

- Los iteradores se definen en el [espacio de nombres Platform::Collections](../cppcx/platform-collections-namespace.md). Estos iteradores cumplen los requisitos de los iteradores de STL y permiten el uso de [std::find](../standard-library/algorithm-functions.md#find),  [std::count_if](../standard-library/algorithm-functions.md#count_if)y otros algoritmos de STL en cualquier tipo de interfaz [Windows::Foundation::Collections](/uwp/api/windows.foundation.collections) o tipo de [Platform::Collections](../cppcx/platform-collections-namespace.md) concreto. Por ejemplo, esto significa que puede iterar una colección en un componente de Windows en tiempo de ejecución que se crea en C- y aplicarle un algoritmo STL.

   > [!IMPORTANT]
   > Los iteradores de proxy `VectorIterator` y `VectorViewIterator` usan los objetos proxy `VectoryProxy<T>` y `ArrowProxy<T>` para permitir el uso de contenedores de STL. Para obtener más información, consulta “Elementos de VectorProxy” más adelante en este artículo.

- Los tipos de colección C+/CX admiten la misma seguridad de subprocesos garantiza que los contenedores STL admiten.

- [Windows::Foundation::Collections::IObservableVector](/uwp/api/windows.foundation.collections.iobservablevector-1) y [Windows::Foundation::Collections::IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2) definen eventos que se desencadenan cuando la colección cambia de distintas maneras. Al implementar estas interfaces,  [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) y [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) permiten enlaces de datos con colecciones de XAML. Por ejemplo, si tienes un objeto `Vector` que está enlazado a datos a un objeto `Grid`, cuando agregues un elemento a una colección, el cambio se reflejará en la interfaz de usuario del objeto Grid.

## <a name="vector-usage"></a>Uso de Vector

Cuando la clase tiene que pasar un contenedor de secuencia a otro componente de Windows Runtime, use [Windows::Foundation::Collections:: IVector\<T>](/uwp/api/windows.foundation.collections.ivector-1) como parámetro o tipo de valor devuelto, y [Platform::Collections::Vector\<T>](../cppcx/platform-collections-vector-class.md) como la implementación concreta. Si intentas usar un tipo `Vector` en un valor devuelto o parámetro público, se producirá el error del compilador C3986. Puedes corregir el error cambiando el tipo `Vector` a `IVector`.

> [!IMPORTANT]
> Si pasas una secuencia dentro de tu propia programa, utiliza `Vector` o `std::vector` porque son más eficaces que `IVector`. Utiliza `IVector` solo cuando pases el contenedor a través de la interfaz binaria de aplicación (ABI).
>
> El sistema de tipos de Windows Runtime no admite el concepto de matrices irregulares y, por lo tanto, no se puede pasar un IVector<Platform::Array\<T>> como un valor devuelto o parámetro de método. Para pasar una matriz escalonada o un grupo de secuencias a través de la ABI, usa `IVector<IVector<T>^>`.

`Vector<T>` proporciona los métodos necesarios para agregar, quitar y tener acceso a los elementos de la colección, y se puede convertir implícitamente a `IVector<T>`. También puedes utilizar algoritmos de STL en instancias de `Vector<T>`. En el siguiente ejemplo se muestra algún uso básico. La [función begin](../cppcx/begin-function.md) y la [función end](../cppcx/end-function.md) proceden aquí del espacio de nombres `Platform::Collections` , no del espacio de nombres `std` .

[!code-cpp[cx_collections#01](../cppcx/codesnippet/CPP/collections/class1.cpp#01)]

Si tiene código existente `std::vector` que usa y desea reutilizarlo en un componente `Vector` de Windows `std::vector` Runtime, solo use uno `Vector` de los constructores que toma uno o un par de iteradores para construir un en el punto donde se pasa la colección a través de la ABI. En el ejemplo siguiente se muestra la forma de utilizar el constructor de movimiento `Vector` para la inicialización eficaz de un objeto `std::vector`. Después de la operación de movimiento, la variable `vec` original deja de ser válida.

[!code-cpp[cx_collections#02](../cppcx/codesnippet/CPP/collections/class1.cpp#02)]

Si tienes un vector de cadenas que debes pasar a través de ABI en algún momento futuro, debes decidir si creas las cadenas inicialmente como tipos de `std::wstring` o como tipos de `Platform::String^` . Si tienes que hacer una gran cantidad de procesamiento en las cadenas, utiliza `wstring`. Si no, crea las cadenas como tipos de `Platform::String^` y evita el costo de convertirlas más adelante. También debes decidir si estas cadenas se han de colocar en `std:vector` o `Platform::Collections::Vector` internamente. Como regla general, usa `std::vector` y crea después un objeto `Platform::Vector` desde él cuando pases el contenedor a través de ABI.

## <a name="value-types-in-vector"></a>Tipos de valor de Vector

Cualquier elemento que se almacena en un objeto [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) debe admitir la comparación de igualdad, ya sea de forma implícita o mediante el comparador [std::equal_to](../standard-library/equal-to-struct.md) personalizado que proporciones. Todos los tipos de referencia y todos los tipos escalares admiten implícitamente comparaciones de igualdad. Para los tipos de valor no escalares como [Windows::Foundation::DateTime](/uwp/api/windows.foundation.datetime)o para las comparaciones personalizadas (por ejemplo, `objA->UniqueID == objB->UniqueID`) debes proporcionar un objeto de función personalizado.

## <a name="vectorproxy-elements"></a>Elementos de VectorProxy

[Platform::Collections::VectorIterator](../cppcx/platform-collections-vectoriterator-class.md) y [Platform::Collections::VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md) permiten `range for` el uso de bucles y algoritmos como [std::sort](../standard-library/algorithm-functions.md#sort) con un contenedor [de>IVector\<T.](/uwp/api/windows.foundation.collections.ivector-1) Sin embargo, no se puede acceder a los elementos de `IVector` mediante la desreferencia de un puntero de C++; solo se puede acceder a ellos con los métodos [GetAt](/uwp/api/windows.foundation.collections.ivector-1.getat) y [SetAt](/uwp/api/windows.foundation.collections.ivector-1.setat) . Por lo tanto, estos `Platform::Details::VectorProxy<T>` iteradores utilizan las `Platform::Details::ArrowProxy<T>` clases de proxy y para proporcionar acceso a los elementos individuales a través __\*__ de , __->__, y __ \[]__ operadores, según lo requiera la biblioteca estándar. En realidad, dado un `IVector<Person^> vec`, el tipo de `*begin(vec)` es `VectorProxy<Person^>`. Sin embargo, el objeto proxy casi siempre es transparente en el código. Estos objetos proxy no están documentados porque solo los usan internamente los operadores, pero es útil conocer cómo funciona el mecanismo.

Cuando usas un bucle `range for` en contenedores `IVector` , utilizas `auto&&` para permitir a la variable de iterador enlazar correctamente con los elementos de `VectorProxy` . Si usas `auto` o `auto&`, se genera la advertencia del compilador C4239 y `VectoryProxy` se menciona en el texto de la advertencia.

En la ilustración siguiente se muestra un bucle `range for` en un `IVector<Person^>`. Observa que la ejecución se detiene en el punto de interrupción de la línea 64. En la ventana **Inspección rápida** se muestra que la variable de iterador `p` es en realidad un `VectorProxy<Person^>` que tiene las variables miembro `m_v` y `m_i` . Sin embargo, cuando se llama a `GetType` en esta variable, se devuelve el tipo idéntico a la instancia `Person` de `p2`. La clave aquí es que aunque `VectorProxy` y `ArrowProxy` pueden aparecer en la ventana **Inspección rápida**, en algunos errores de compilación del depurador o en otros lugares, normalmente no es necesario escribir explícitamente código para ellos.

![VectorProxy en el rango&#45;basado para bucle](../cppcx/media/vectorproxy-1.png "VectorProxy en el rango&#45;basado para bucle")

Un escenario en el que tendrás código alrededor del objeto proxy es cuando tengas que aplicar `dynamic_cast` a los elementos (por ejemplo, cuando busques objetos XAML de un tipo determinado en una colección de elementos `UIElement` ). En este caso, primero debes convertir el elemento en [Platform::Object](../cppcx/platform-object-class.md)^ y después realizar la conversión dinámica:

```cpp
void FindButton(UIElementCollection^ col)
{
    // Use auto&& to avoid warning C4239
    for (auto&& elem : col)
    {
        Button^ temp = dynamic_cast<Button^>(static_cast<Object^>(elem));
        if (nullptr != temp)
        {
            // Use temp...
        }
    }
}
```

## <a name="map-usage"></a>Uso de mapa

En este ejemplo se muestra cómo insertar elementos y buscarlos en un objeto [Platform::Collections::Map](../cppcx/platform-collections-map-class.md)y devolver después el objeto `Map` como un tipo [Windows::Foundation::Collections::IMapView](/uwp/api/windows.foundation.collections.imapview-2) de solo lectura.

[!code-cpp[cx_collections#04](../cppcx/codesnippet/CPP/collections/class1.cpp#04)]

Normalmente, para la funcionalidad interna de mapas, es preferible el tipo `std::map` por razones de rendimiento. Si tiene que pasar el contenedor a través de la ABI, crea un objeto [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) desde [std::map](../standard-library/map-class.md) y devuelve el objeto `Map` como un [Windows::Foundation::Collections::IMap](/uwp/api/windows.foundation.collections.imap-2). Si intentas usar un tipo `Map` en un valor devuelto o parámetro público, se producirá el error del compilador C3986. Puedes corregir el error cambiando el tipo `Map` a `IMap`. En algunos casos (por ejemplo, si no estás realizando un gran número de búsquedas o inserciones y estás pasando la colección a través de ABI con frecuencia), puede ser menos oneroso utilizar `Platform::Collections::Map` desde el principio y evitar el costo de convertir el objeto `std::map`. En cualquier caso, conviene que evites operaciones de búsqueda e inserción en un objeto `IMap` ya que estas son las menos rentables en cuando a rendimiento de los tres tipos. Convierte a `IMap` solo en el momento de pasar el contenedor a través de ABI.

## <a name="value-types-in-map"></a>Tipos de valor de Map

Los elementos de un objeto [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) están ordenados. Cualquier elemento que se almacena en `Map` debe admitir una comparación de tipo "menor que" con ordenación parcial estricta, ya sea de forma implícita o utilizando el comparador [stl::less](../standard-library/less-struct.md) que proporciones. Los tipos escalares son compatibles con la comparación de forma implícita. Para los tipos de valor no escalares como `Windows::Foundation::DateTime`, o para las comparaciones personalizadas (por ejemplo, `objA->UniqueID < objB->UniqueID`) debes proporcionar un comparador personalizado.

## <a name="collection-types"></a>Tipos de colección

Las colecciones se dividen en cuatro categorías: versiones modificables y versiones de solo lectura de colecciones de secuencia y asociativas. Además, C++/CX mejora las colecciones proporcionando tres clases de iterador que simplifican el acceso a las colecciones.

Los elementos de una colección modificable pueden cambiar, pero los elementos de una colección de solo lectura, que se denomina *vista*, solo se pueden leer. Se puede tener acceso a los elementos de una colección [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) o[Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md) mediante un iterador o [Vector::GetAt](../cppcx/platform-collections-vector-class.md#getat) de la colección y un índice. Se puede tener acceso a los elementos de una colección asociativa mediante [Map::Lookup](../cppcx/platform-collections-map-class.md#lookup) de la colección y una clave.

[clase Platform::Collections::Map](../cppcx/platform-collections-map-class.md)<br/>
Una colección asociativa modificable. Los elementos de mapa son pares clave-valor. Se admiten tanto la búsqueda de una clave para recuperar su valor asociado, como el recorrido en iteración de todos los pares clave-valor.

`Map` y `MapView` tienen plantillas en `<K, V, C = std::less<K>>`; por consiguiente, puedes personalizar el comparador.  Además, `Vector` y `VectorView` tienen plantillas en `<T, E = std::equal_to<T>>` , por lo que puedes personalizar el comportamiento de `IndexOf()`. Esto es importante principalmente para `Vector` y `VectorView` de los structs de valor. Por ejemplo, para\<crear un vector Windows::Foundation::DateTime>, debe proporcionar un comparador personalizado porque DateTime no sobrecarga el operador .

[Platform::Collections::MapView (Clase)](../cppcx/platform-collections-mapview-class.md)<br/>
Una versión de solo lectura de `Map`.

[Platform::Collections::Vector (Clase)](../cppcx/platform-collections-vector-class.md)<br/>
Una colección de secuencias modificable. `Vector<T>` admite operaciones [Append](../cppcx/platform-collections-vector-class.md#append) de acceso aleatorio de tiempo constante y de tiempo constante amortizado.

[clase Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md)<br/>
Una versión de solo lectura de `Vector`.

[Platform::Collections::InputIterator (Clase)](../cppcx/platform-collections-inputiterator-class.md)<br/>
Un iterador de STL que satisface los requisitos de un iterador de entrada de STL.

[Platform::Collections::VectorIterator (Clase)](../cppcx/platform-collections-vectoriterator-class.md)<br/>
Un iterador de STL que satisface los requisitos de un iterador de acceso aleatorio mutable de STL.

[Plataforma::Collections::VectorViewIterator (Clase)](../cppcx/platform-collections-vectorviewiterator-class.md)<br/>
Un iterador de STL que satisface los requisitos de un iterador de acceso aleatorio  `const` de STL.

### <a name="begin-and-end-functions"></a>Funciones begin() y end()

Para simplificar el uso de `Vector`los `VectorView` `Map`objetos STL para procesar , , `MapView`, , y objetos arbitrarios, `Windows::Foundation::Collections` C++/CX admite sobrecargas de las funciones no miembro sin miembro begin [Function](../cppcx/begin-function.md) y end [Function.](../cppcx/end-function.md)

En la tabla siguiente se enumeran los iteradores y las funciones disponibles.

|Iterators|Functions|
|---------------|---------------|
|[Platform::Collections::VectorIterator\<T>](../cppcx/platform-collections-vectoriterator-class.md)<br /><br /> (Almacene internamente [Windows::Foundation::Collections:: IVector\<T>](/uwp/api/windows.foundation.collections.ivector-1) e int.)|[begin](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md)([Windows::Foundation::Collections:: IVector\<T>](/uwp/api/windows.foundation.collections.ivector-1))|
|[Platform::Collections::VectorViewIterator\<T>](../cppcx/platform-collections-vectorviewiterator-class.md)<br /><br /> (Almacena internamente [IVectorView\<T>](/uwp/api/windows.foundation.collections.ivectorview-1)e int.)|[begin](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([\<IVectorView T>](/uwp/api/windows.foundation.collections.ivectorview-1))|
|[Plataforma::Colecciones::InputIterator\<T>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Almacena internamente [iIterator\<T>](/uwp/api/windows.foundation.collections.iiterator-1)y T.)|[comenzar](../cppcx/begin-function.md)/ [el final](../cppcx/end-function.md) (>T[\<iIterable ](/uwp/api/windows.foundation.collections.iiterable-1))|
|[Platform::Collections::InputIterator<IKeyValuePair\<K, V>->](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Almacena internamente [iIterator\<T>](/uwp/api/windows.foundation.collections.iiterator-1)y T.)|[begin](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([IMap\<K,V>](/uwp/api/windows.foundation.collections.imap-2).|
|[Platform::Collections::InputIterator<IKeyValuePair\<K, V>->](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Almacena internamente [iIterator\<T>](/uwp/api/windows.foundation.collections.iiterator-1)y T.)|[begin](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([Windows::Foundation::Collections::IMapView](/uwp/api/windows.foundation.collections.imapview-2))|

### <a name="collection-change-events"></a>Eventos de cambios en colecciones

`Vector` y `Map` admiten el enlace de datos en colecciones de XAML mediante la implementación de eventos que se producen cuando se cambia o se restablece un objeto de colección, o cuando se inserta, se quita o se cambia cualquier elemento de una colección. Puedes escribir tus propios tipos que admitan enlace de datos, aunque no puedes heredar de `Map` o `Vector` porque esos tipos están sellados.

Los delegados [Windows::Foundation::Collections::VectorChangedEventHandler](/uwp/api/windows.foundation.collections.vectorchangedeventhandler-1) y [Windows::Foundation::Collections::MapChangedEventHandler](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) especifican las firmas de los controladores de eventos para los eventos de cambio de la colección. La clase de enumeración pública [Windows::Foundation::Collections::CollectionChange](/uwp/api/windows.foundation.collections.collectionchange) y las clases ref `Platform::Collection::Details::MapChangedEventArgs` y `Platform::Collections::Details::VectorChangedEventArgs` almacenan los argumentos de eventos para determinar la causa del evento. Los `*EventArgs` tipos se `Details` definen en el espacio de nombres porque no `Map` es `Vector`que no tenga que construirlos o consumirlos explícitamente cuando se usa o .

## <a name="see-also"></a>Vea también

[Sistema de tipos](../cppcx/type-system-c-cx.md)<br/>
[Referencia del lenguaje C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)
