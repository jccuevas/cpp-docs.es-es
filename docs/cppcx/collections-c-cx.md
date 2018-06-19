---
title: Colecciones (C++ / CX) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 914da30b-aac5-4cd7-9da3-a5ac08cdd72c
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0296422ce0f9ef49b096d5ea8512530871fc733b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094262"
---
# <a name="collections-ccx"></a>Colecciones (C++/CX)
En C++ / programa CX, puedes hacer uso libre de contenedores de la biblioteca de plantillas estándar (STL), o cualquier otro tipo de colección definida por el usuario. Sin embargo, cuando pases colecciones y hacia atrás en la interfaz binaria de aplicación de Windows en tiempo de ejecución (ABI), por ejemplo, para un control XAML o a un cliente de JavaScript, debe usar los tipos de colección en tiempo de ejecución de Windows.  
  
 El tiempo de ejecución de Windows define las interfaces para colecciones y tipos relacionados y C++ / CX proporciona las implementaciones concretas de C++ en el archivo de encabezado collection.h. En esta ilustración se muestran las relaciones entre los tipos de colección:  
  
 ![C&#43;&#43;&#47;árbol de herencia de CX para tipos de colección](../cppcx/media/cppcxcollectionsinheritancetree.png "CPPCXCollectionsInheritanceTree")  
  
-   La [clase Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) es similar a la [clase std::vector](../standard-library/vector-class.md).  
  
-   La [clase Platform::Collections::Map](../cppcx/platform-collections-map-class.md) es similar a la [clase std::map](../standard-library/map-class.md).  
  
-   La[clase Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md) y la[clase Platform::Collections::MapView](../cppcx/platform-collections-mapview-class.md) son versiones de solo lectura de `Vector` y la `Map`.  
  
-   Los iteradores se definen en el [espacio de nombres Platform::Collections](../cppcx/platform-collections-namespace.md). Estos iteradores cumplen los requisitos de los iteradores de STL y permiten el uso de [std::find](../standard-library/algorithm-functions.md#find),  [std::count_if](../standard-library/algorithm-functions.md#count_if)y otros algoritmos de STL en cualquier tipo de interfaz [Windows::Foundation::Collections](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.aspx) o tipo de [Platform::Collections](../cppcx/platform-collections-namespace.md) concreto. Por ejemplo, esto significa que puede recorrer en iteración una colección en un componente en tiempo de ejecución de Windows que se crea en C# y aplicarle un algoritmo STL.  
  
    > [!IMPORTANT]
    >  Los iteradores de proxy `VectorIterator` y `VectorViewIterator` usan los objetos proxy `VectoryProxy<T>` y `ArrowProxy<T>` para permitir el uso de contenedores de STL. Para obtener más información, consulta “Elementos de VectorProxy” más adelante en este artículo.  
  
-   C++ / tipos de colecciones de CX admite la misma seguridad para subprocesos garantías de que los contenedores STL.  
  
-   [Windows::Foundation::Collections::IObservableVector](http://msdn.microsoft.com/library/windows/apps/br226052.aspx) y [Windows::Foundation::Collections::IObservableMap](http://msdn.microsoft.com/library/windows/apps/br226050.aspx) definen eventos que se desencadenan cuando la colección cambia de distintas maneras. Al implementar estas interfaces,  [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) y [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) permiten enlaces de datos con colecciones de XAML. Por ejemplo, si tienes un objeto `Vector` que está enlazado a datos a un objeto `Grid`, cuando agregues un elemento a una colección, el cambio se reflejará en la interfaz de usuario del objeto Grid.  
  
## <a name="vector-usage"></a>Uso de Vector  
 Cuando tu clase tenga que pasar un contenedor de secuencias a otro componente de Windows en tiempo de ejecución, utilice [Collections:: IVector\<T >](http://msdn.microsoft.com/library/windows/apps/br206631.aspx) como parámetro o tipo de valor devuelto, y [plataforma:: Collections::vector\<T >](../cppcx/platform-collections-vector-class.md) como la implementación concreta. Si intentas usar un tipo `Vector` en un valor devuelto o parámetro público, se producirá el error del compilador C3986. Puedes corregir el error cambiando el tipo `Vector` a `IVector`.  
  
> [!IMPORTANT]
>  Si pasas una secuencia dentro de tu propia programa, utiliza `Vector` o `std::vector` porque son más eficaces que `IVector`. Utiliza `IVector` solo cuando pases el contenedor a través de la interfaz binaria de aplicación (ABI).  
>   
>  El sistema de tipos en tiempo de ejecución de Windows no admite el concepto de matrices escalonadas y, por tanto, no se puede pasar un IVector < platform:: Array\<T >> como un parámetro de método o valor devuelto. Para pasar una matriz escalonada o un grupo de secuencias a través de la ABI, usa `IVector<IVector<T>^>`.  
  
 `Vector<T>` proporciona los métodos necesarios para agregar, quitar y tener acceso a los elementos de la colección, y se puede convertir implícitamente a `IVector<T>`. También puedes utilizar algoritmos de STL en instancias de `Vector<T>`. En el siguiente ejemplo se muestra algún uso básico. La [función begin](../cppcx/begin-function.md) y la [función end](../cppcx/end-function.md) proceden aquí del espacio de nombres `Platform::Collections` , no del espacio de nombres `std` .  
  
 [!code-cpp[cx_collections#01](../cppcx/codesnippet/CPP/collections/class1.cpp#01)]  
  
 Si tiene código existente que utiliza `std::vector` y desea volver a usarla en un componente en tiempo de ejecución de Windows, use uno de los `Vector` constructores que toma un `std::vector` o un par de iteradores para construir un `Vector` en el punto donde pasas la colección a través de ABI. En el ejemplo siguiente se muestra la forma de utilizar el constructor de movimiento `Vector` para la inicialización eficaz de un objeto `std::vector`. Después de la operación de movimiento, la variable `vec` original deja de ser válida.  
  
 [!code-cpp[cx_collections#02](../cppcx/codesnippet/CPP/collections/class1.cpp#02)]  
  
 Si tienes un vector de cadenas que debes pasar a través de ABI en algún momento futuro, debes decidir si creas las cadenas inicialmente como tipos de `std::wstring` o como tipos de `Platform::String^` . Si tienes que hacer una gran cantidad de procesamiento en las cadenas, utiliza `wstring`. Si no, crea las cadenas como tipos de `Platform::String^` y evita el costo de convertirlas más adelante. También debes decidir si estas cadenas se han de colocar en `std:vector` o `Platform::Collections::Vector` internamente. Como regla general, usa `std::vector` y crea después un objeto `Platform::Vector` desde él cuando pases el contenedor a través de ABI.  
  
## <a name="value-types-in-vector"></a>Tipos de valor de Vector  
 Cualquier elemento que se almacena en un objeto [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) debe admitir la comparación de igualdad, ya sea de forma implícita o mediante el comparador [std::equal_to](../standard-library/equal-to-struct.md) personalizado que proporciones. Todos los tipos de referencia y todos los tipos escalares admiten implícitamente comparaciones de igualdad. Para los tipos de valor no escalares como [Windows::Foundation::DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx)o para las comparaciones personalizadas (por ejemplo, `objA->UniqueID == objB->UniqueID`) debes proporcionar un objeto de función personalizado.  
   
  
## <a name="vectorproxy-elements"></a>Elementos de VectorProxy  
 [Vectoriterator](../cppcx/platform-collections-vectoriterator-class.md) y [vectorviewiterator](../cppcx/platform-collections-vectorviewiterator-class.md) habilitar el uso de `range for` bucles y algoritmos como [std:: Sort](../standard-library/algorithm-functions.md#sort) con un [ IVector\<T >](http://msdn.microsoft.com/en-us/library/windows/apps/br206631.aspx) contenedor. Sin embargo, no se puede acceder a los elementos de `IVector` mediante la desreferencia de un puntero de C++; solo se puede acceder a ellos con los métodos [GetAt](http://msdn.microsoft.com/library/windows/apps/br206634.aspx) y [SetAt](http://msdn.microsoft.com/library/windows/apps/br206642.aspx) . Por tanto, estos iteradores utilizan las clases de proxy `Platform::Details::VectorProxy<T>` y `Platform::Details::ArrowProxy<T>` para proporcionar acceso a los distintos elementos con los operadores `*`, `->`y `[]` , tal como STL requiere. En realidad, dado un `IVector<Person^> vec`, el tipo de `*begin(vec)` es `VectorProxy<Person^>`. Sin embargo, el objeto proxy casi siempre es transparente en el código. Estos objetos proxy no están documentados porque solo los usan internamente los operadores, pero es útil conocer cómo funciona el mecanismo.  
  
 Cuando usas un bucle `range for` en contenedores `IVector` , utilizas `auto&&` para permitir a la variable de iterador enlazar correctamente con los elementos de `VectorProxy` . Si usas `auto` o `auto&`, se genera la advertencia del compilador C4239 y `VectoryProxy` se menciona en el texto de la advertencia.  
  
 En la ilustración siguiente se muestra un bucle `range for` en un `IVector<Person^>`. Observa que la ejecución se detiene en el punto de interrupción de la línea 64. En la ventana **Inspección rápida** se muestra que la variable de iterador `p` es en realidad un `VectorProxy<Person^>` que tiene las variables miembro `m_v` y `m_i` . Sin embargo, cuando se llama a `GetType` en esta variable, se devuelve el tipo idéntico a la instancia `Person` de `p2`. La clave aquí es que aunque `VectorProxy` y `ArrowProxy` pueden aparecer en la ventana **Inspección rápida**, en algunos errores de compilación del depurador o en otros lugares, normalmente no es necesario escribir explícitamente código para ellos.  
  
 ![VectorProxy en intervalo&#45;en función de bucle](../cppcx/media/vectorproxy-1.png "VectorProxy_1")  
  
 Un escenario en el que tendrás código alrededor del objeto proxy es cuando tengas que aplicar `dynamic_cast` a los elementos (por ejemplo, cuando busques objetos XAML de un tipo determinado en una colección de elementos `UIElement` ). En este caso, primero debes convertir el elemento en [Platform::Object](../cppcx/platform-object-class.md)^ y después realizar la conversión dinámica:  
  
```  
  
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
 En este ejemplo se muestra cómo insertar elementos y buscarlos en un objeto [Platform::Collections::Map](../cppcx/platform-collections-map-class.md)y devolver después el objeto `Map` como un tipo [Windows::Foundation::Collections::IMapView](http://msdn.microsoft.com/library/windows/apps/br226037.aspx) de solo lectura.  
  
 [!code-cpp[cx_collections#04](../cppcx/codesnippet/CPP/collections/class1.cpp#04)]  
  
 Normalmente, para la funcionalidad interna de mapas, es preferible el tipo `std::map` por razones de rendimiento. Si tiene que pasar el contenedor a través de la ABI, crea un objeto [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) desde [std::map](../standard-library/map-class.md) y devuelve el objeto `Map` como un [Windows::Foundation::Collections::IMap](http://msdn.microsoft.com/library/windows/apps/br226042.aspx). Si intentas usar un tipo `Map` en un valor devuelto o parámetro público, se producirá el error del compilador C3986. Puedes corregir el error cambiando el tipo `Map` a `IMap`. En algunos casos (por ejemplo, si no estás realizando un gran número de búsquedas o inserciones y estás pasando la colección a través de ABI con frecuencia), puede ser menos oneroso utilizar `Platform::Collections::Map` desde el principio y evitar el costo de convertir el objeto `std::map`. En cualquier caso, conviene que evites operaciones de búsqueda e inserción en un objeto `IMap` ya que estas son las menos rentables en cuando a rendimiento de los tres tipos. Convierte a `IMap` solo en el momento de pasar el contenedor a través de ABI.  
  
## <a name="value-types-in-map"></a>Tipos de valor de Map  
 Los elementos de un objeto [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) están ordenados. Cualquier elemento que se almacena en `Map` debe admitir una comparación de tipo "menor que" con ordenación parcial estricta, ya sea de forma implícita o utilizando el comparador [stl::less](../standard-library/less-struct.md) que proporciones. Los tipos escalares son compatibles con la comparación de forma implícita. Para los tipos de valor no escalares como `Windows::Foundation::DateTime`, o para las comparaciones personalizadas (por ejemplo, `objA->UniqueID < objB->UniqueID`) debes proporcionar un comparador personalizado.  
  
## <a name="collection-types"></a>Tipos de colección  
 Las colecciones se dividen en cuatro categorías: versiones modificables y versiones de solo lectura de colecciones de secuencia y asociativas. Además, C++ / CX mejora las colecciones proporcionando tres clases de iterador que simplifican el acceso de las colecciones. 
  
 Los elementos de una colección modificable pueden cambiar, pero los elementos de una colección de solo lectura, que se denomina *vista*, solo se pueden leer. Elementos de un [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) o[vectorview](../cppcx/platform-collections-vectorview-class.md) puede tener acceso a la colección mediante un iterador o la colección [vector:: GetAt](../cppcx/platform-collections-vector-class.md#getat) y un índice. Pueden acceder a los elementos de una colección asociativa mediante el uso de la colección [Map:: Lookup](../cppcx/platform-collections-map-class.md#lookup) y una clave.  
  
 [clase Platform::Collections::Map](../cppcx/platform-collections-map-class.md)  
 Una colección asociativa modificable. Los elementos de mapa son pares clave-valor. Se admiten tanto la búsqueda de una clave para recuperar su valor asociado, como el recorrido en iteración de todos los pares clave-valor.  
  
 `Map` y `MapView` tienen plantillas en `<K, V, C = std::less<K>>`; por consiguiente, puedes personalizar el comparador.  Además, `Vector` y `VectorView` tienen plantillas en `<T, E = std::equal_to<T>>` , por lo que puedes personalizar el comportamiento de `IndexOf()`. Esto es importante principalmente para `Vector` y `VectorView` de los structs de valor. Por ejemplo, para crear un Vector\<Windows::Foundation::DateTime >, debe proporcionar un comparador personalizado porque DateTime no sobrecarga el operador ==.  
  
 [clase Platform::Collections::MapView](../cppcx/platform-collections-mapview-class.md)  
 Una versión de solo lectura de `Map`.  
  
 [Platform::Collections::Vector Class](../cppcx/platform-collections-vector-class.md)  
 Una colección de secuencias modificable. `Vector<T>` admite operaciones [Append](../cppcx/platform-collections-vector-class.md#append) de acceso aleatorio de tiempo constante y de tiempo constante amortizado.  
  
 [clase Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md)  
 Una versión de solo lectura de `Vector`.  
  
 [Platform::Collections::InputIterator (Clase)](../cppcx/platform-collections-inputiterator-class.md)  
 Un iterador de STL que satisface los requisitos de un iterador de entrada de STL.  
  
 [Platform::Collections::VectorIterator (Clase)](../cppcx/platform-collections-vectoriterator-class.md)  
 Un iterador de STL que satisface los requisitos de un iterador de acceso aleatorio mutable de STL.  
  
 [Platform::Collections::VectorViewIterator (Clase)](../cppcx/platform-collections-vectorviewiterator-class.md)  
 Un iterador de STL que satisface los requisitos de un iterador de acceso aleatorio  `const` de STL.  
  
### <a name="begin-and-end-functions"></a>Funciones begin() y end()  
 Para simplificar el uso de STL al procesar `Vector`, `VectorView`, `Map`, `MapView`y arbitrariamente `Windows::Foundation::Collections` objetos, C++ / CX admite las sobrecargas de la [begin (función)](../cppcx/begin-function.md) y [final Función](../cppcx/end-function.md) funciones no miembro.  
  
 En la tabla siguiente se enumeran los iteradores y las funciones disponibles.  
  
|Iterators|Funciones|  
|---------------|---------------|  
|[Vectoriterator\<T >](../cppcx/platform-collections-vectoriterator-class.md)<br /><br /> (Almacena internamente [Collections:: IVector\<T >](http://msdn.microsoft.com/library/windows/apps/br206631.aspx) e int.)|[comenzar](../cppcx/begin-function.md)/ [final](../cppcx/end-function.md)([Collections:: IVector\<T >](http://msdn.microsoft.com/library/windows/apps/br206631.aspx))|  
|[Vectorviewiterator\<T >](../cppcx/platform-collections-vectorviewiterator-class.md)<br /><br /> (Almacena internamente [IVectorView\<T >](http://msdn.microsoft.com/library/windows/apps/br226058.aspx)^ e int.)|[comenzar](../cppcx/begin-function.md)/ [final](../cppcx/end-function.md) ([IVectorView\<T >](http://msdn.microsoft.com/library/windows/apps/br226058.aspx)^)|  
|[Inputiterator\<T >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Almacena internamente [IIterator\<T >](http://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ y T.)|[comenzar](../cppcx/begin-function.md)/ [final](../cppcx/end-function.md) ([IIterable\<T >](http://msdn.microsoft.com/library/windows/apps/br226024.aspx))|  
|[Inputiterator < IKeyValuePair\<K, V > ^ >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Almacena internamente [IIterator\<T >](http://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ y T.)|[comenzar](../cppcx/begin-function.md)/ [final](../cppcx/end-function.md) ([IMap\<K, V >](http://msdn.microsoft.com/library/windows/apps/br226042.aspx).|  
|[Inputiterator < IKeyValuePair\<K, V > ^ >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Almacena internamente [IIterator\<T >](http://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ y T.)|[begin](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([Windows::Foundation::Collections::IMapView](http://msdn.microsoft.com/library/windows/apps/br226037.aspx))|  
  
### <a name="collection-change-events"></a>Eventos de cambios en colecciones  
 `Vector` y `Map` admiten el enlace de datos en colecciones de XAML mediante la implementación de eventos que se producen cuando se cambia o se restablece un objeto de colección, o cuando se inserta, se quita o se cambia cualquier elemento de una colección. Puedes escribir tus propios tipos que admitan enlace de datos, aunque no puedes heredar de `Map` o `Vector` porque esos tipos están sellados.  
  
 Los delegados [Windows::Foundation::Collections::VectorChangedEventHandler](http://msdn.microsoft.com/library/windows/apps/br206656.aspx) y [Windows::Foundation::Collections::MapChangedEventHandler](http://msdn.microsoft.com/library/windows/apps/br206644.aspx) especifican las firmas de los controladores de eventos para los eventos de cambio de la colección. La clase de enumeración pública [Windows::Foundation::Collections::CollectionChange](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx) y las clases ref `Platform::Collection::Details::MapChangedEventArgs` y `Platform::Collections::Details::VectorChangedEventArgs` almacenan los argumentos de eventos para determinar la causa del evento. Los tipos *`EventArgs` se definen en el espacio de nombres `Details` porque no tienes que crearlos ni usarlos de forma explícita cuando utilices `Map` o `Vector`.  
  
## <a name="see-also"></a>Vea también  
 [Sistema de tipos](../cppcx/type-system-c-cx.md)   
 [Tipos integrados](http://msdn.microsoft.com/en-us/acc196fd-09da-4882-b554-6c94685ec75f)   
 [Referencia del lenguaje de Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)