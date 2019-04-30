---
title: Gráficos (C++ AMP)
ms.date: 11/04/2016
ms.assetid: 190a98a4-5f7d-442e-866b-b374ca74c16f
ms.openlocfilehash: 4a40575d84c9a0efedcb3c7c9717fc310870b530
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405669"
---
# <a name="graphics-c-amp"></a>Gráficos (C++ AMP)

C++ AMP contiene varias API en el [Concurrency:: Graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md) espacio de nombres que puede usar para tener acceso a la compatibilidad con la textura en las GPU. Algunos escenarios comunes son los siguientes:

- Puede usar el [textura](../../parallel/amp/reference/texture-class.md) clase como contenedor de datos para el cálculo y aprovechar la *localidad espacial* de la memoria caché de textura y diseños de hardware GPU. La localidad espacial es la propiedad de los elementos de datos que están físicamente cerca unos de otros.

- El runtime proporciona interoperabilidad eficiente con los sombreadores que no son de cálculo. Los sombreadores de casco, píxeles, vértices y teselación consumen o generan con frecuencia texturas que se pueden utilizar en los cálculos de C++ AMP.

- Las API de gráficos de C++ AMP proporcionan maneras alternativas de tener acceso a los búferes empaquetados de palabras sub. Las texturas con formatos que representan *elementos de textura* (elementos de textura) que se componen de 8 bits o valores escalares de 16 bits permiten el acceso a dicho almacenamiento de datos empaquetados.

## <a name="the-norm-and-unorm-types"></a>Los tipos norm y unorm

El `norm` y `unorm` tipos son tipos escalares que limitan el intervalo de **float** valores; Esto se conoce como *fijación*. Estos tipos se pueden construir explícitamente a partir de otros tipos escalares. En las conversiones, el valor se convierte primero a **float** y, a continuación, se fija en la región correspondiente permitida por norm [-1.0, 1.0] o unorm [0.0, 1.0]. La conversión de +/- infinito devuelve +/-1. La conversión de NaN es indefinida. Norm se puede construir implícitamente a partir de unorm sin pérdida de datos. La conversión implícita del operador a float se define en los siguientes tipos. Los operadores binarios se definen entre estos tipos y otros tipos escalares integrados como **float** y **int**: +, -, \*, /, ==,! =, >, \<, > =, < =. También se admiten los operadores de asignación compuestos: +=, -=, \*=, / =. El operador unario de negación (-) se define para los tipos norm.

## <a name="short-vector-library"></a>Biblioteca de vectores cortos

La biblioteca de vectores cortos proporciona algunas de las funcionalidades de la [tipo Vector](http://go.microsoft.com/fwlink/p/?linkid=248500) que se define en HLSL y se utiliza normalmente para definir elementos de textura. Un vector corto es una estructura de datos que contiene de uno a cuatro valores del mismo tipo. Los tipos admitidos son **doble**, **float**, **int**, `norm`, `uint`, y `unorm`. Los nombres de tipo se muestran en la siguiente tabla. Para cada tipo, hay también un correspondiente **typedef** que no tiene un carácter de subrayado en el nombre. Los tipos que tienen los caracteres de subrayado están en el [Concurrency:: Graphics Namespace](../../parallel/amp/reference/concurrency-graphics-namespace.md). Los tipos que no tienen los caracteres de subrayado están en el [Concurrency::graphics::direct3d Namespace](../../parallel/amp/reference/concurrency-graphics-direct3d-namespace.md) para que están claramente separados de los tipos fundamentales con nombres similares, como **__int8** y **__int16**.

||Longitud 2|Longitud de 3|Longitud de 4|
|-|--------------|--------------|--------------|
|double|double_2<br /><br /> double2|double_3<br /><br /> double3|double_4<br /><br /> double4|
|float|float_2<br /><br /> float2|float_3<br /><br /> float3|float_4<br /><br /> float4|
|int|int_2<br /><br /> int2|int_3<br /><br /> int3|int_4<br /><br /> int4|
|norm|norm_2<br /><br /> norm2|norm_3<br /><br /> norm3|norm_4<br /><br /> norm4|
|uint|uint_2<br /><br /> uint2|uint_3<br /><br /> uint3|uint_4<br /><br /> uint4|
|unorm|unorm_2<br /><br /> unorm2|unorm_3<br /><br /> unorm3|unorm_4<br /><br /> unorm4|

### <a name="operators"></a>Operadores

Si se define un operador entre dos vectores cortos, se define también entre un vector corto y uno escalar. Además, uno de ellos debe ser true:

- El tipo escalar tiene que ser igual que el tipo de elemento del vector corto.

- El tipo escalar se puede convertir implícitamente en el tipo de elemento del vector utilizando únicamente una conversión definida por el usuario.

La operación se lleva a cabo entre cada componente del vector corto y el escalar. Los operadores válidos son:

|Tipo de operador|Tipos válidos|
|-------------------|-----------------|
|Operadores binarios|Válido en todos los tipos: +, -, \*, /,<br /><br /> Válido en tipos enteros: %, ^, &#124;&, <\<, >><br /><br /> Los dos vectores deben tener el mismo tamaño y el resultado es un vector del mismo tamaño.|
|Operadores relacionales|Válido en todos los tipos: == y !=|
|Operador de asignación compuesto|Válido en todos los tipos: +=, -=, \*=, / =<br /><br /> Válido en tipos enteros: % =, ^ =, &#124;= & =, <\<=, >> =|
|Operadores de incremento y decremento|Válido en todos los tipos: ++, --<br /><br /> Tanto el prefijo como el sufijo son válidos.|
|Operador NOT bit a bit (~)|Válido en tipos enteros.|
|Operador unario -|Válido en todos los tipos excepto `unorm` y `uint`.|

### <a name="swizzling-expressions"></a>Expresiones de permutación

La biblioteca de vectores cortos admite que el constructor del descriptor de acceso `vector_type.identifier` tenga acceso a los componentes de un vector corto. El `identifier`, que se conoce como un *expresión de permutación*, especifica los componentes del vector. La expresión puede ser un valor l o un valor r. Los caracteres individuales en el identificador pueden ser: x, y, z y w; o r, g, b y un. "x" y "r" significan el componente cero, "y" y significan el primer componente de "g" y así sucesivamente. (Observe que "x" y "r" no se pueden utilizar en el mismo identificador). Por consiguiente, "rgba" y "xyzw"devuelven el mismo resultado. Los descriptores de acceso de un único componente como "x" e "y" son tipos de valores escalares. Los descriptores de acceso de varios componentes son tipos de vector corto. Por ejemplo, si crea un vector `int_4` denominado `fourInts` que tiene los valores 2, 4, 6 y 8, entonces `fourInts.y` devuelve el entero 4 y `fourInts.rg` devuelve un objeto `int_2` con los valores 2 y 4.

## <a name="texture-classes"></a>Clases de texturas

Muchas GPU tienen hardware y cachés que se optimizan para capturar los píxeles y los elementos de textura y presentar imágenes y texturas. El [textura\<T, N >](../../parallel/amp/reference/texture-class.md) (clase), que es una clase de contenedor para objetos de textura, expone la funcionalidad de textura de estas GPU. Un elemento de textura puede ser:

- Un **int**, `uint`, **float**, **doble**, `norm`, o `unorm` escalares.

- Un vector corto que tiene dos o cuatro componentes. La única excepción es `double_4`, que no se permite.

El objeto `texture` puede tener un intervalo de 1, 2 o 3. El objeto `texture` se puede capturar solamente por referencia en la expresión lambda de una llamada a `parallel_for_each`. La textura se almacena en la GPU como objetos de textura Direct3D. Para obtener más información sobre las texturas y los elementos de textura en Direct3D, vea [Introducción a las texturas en Direct3D 11](http://go.microsoft.com/fwlink/p/?linkid=248502).

El tipo de elemento de textura que se usa puede ser uno de los muchos formatos de textura utilizados en la programación de gráficos. Por ejemplo, un formato RGBA podría utilizar 32 bits, con 8 bits para cada uno de los elementos escalares R, G, B y A. El hardware de textura de una tarjeta gráfica puede tener acceso a los elementos individuales según el formato. Por ejemplo, si se utiliza el formato RGBA, el hardware de textura puede convertir cada elemento de 8 bits en un formato de 32 bits. En C++ AMP, se pueden establecer los bits por elemento escalar del elemento de textura para poder tener acceso automáticamente a los elementos escalares individuales en el código sin utilizar el desplazamiento de bit.

### <a name="instantiating-texture-objects"></a>Crear instancias de objetos de textura

Se puede declarar un objeto de textura sin inicialización. El siguiente ejemplo de código declara varios objetos de textura.

```cpp
#include <amp.h>
#include <amp_graphics.h>
using namespace concurrency;
using namespace concurrency::graphics;

void declareTextures() {
    // Create a 16-texel texture of int.
    texture<int, 1> intTexture1(16);
    texture<int, 1> intTexture2(extent<1>(16));

    // Create a 16 x 32 texture of float_2.
    texture<float_2, 2> floatTexture1(16, 32);
    texture<float_2, 2> floatTexture2(extent<2>(16, 32));

    // Create a 2 x 4 x 8 texture of uint_4.
    texture<uint_4, 3> uintTexture1(2, 4, 8);
    texture<uint_4, 3> uintTexture2(extent<3>(2, 4, 8));
}
```

También se puede utilizar un constructor para declarar e inicializar un objeto `texture`. El siguiente ejemplo de código crea una instancia de un objeto `texture` a partir de un vector de objetos `float_4`. Los bits por elemento escalar se establecen en el valor predeterminado. Este constructor no se puede usar con `norm`, `unorm` ni con los vectores cortos de `norm` y `unorm`, porque no tienen bits predeterminados por cada elemento escalar.

```cpp
#include <amp.h>
#include <amp_graphics.h>
#include <vector>
using namespace concurrency;
using namespace concurrency::graphics;

void initializeTexture() {
    std::vector<int_4> texels;
    for (int i = 0; i < 768 * 1024; i++) {
        int_4 i4(i, i, i, i);
        texels.push_back(i4);
    }

    texture<int_4, 2> aTexture(768, 1024, texels.begin(), texels.end());
}
```

También se puede declarar e inicializar un objeto `texture` mediante una sobrecarga del constructor que tome un puntero a los datos de origen, el tamaño de los datos de origen en bytes y los bits por elemento escalar.

```cpp
void createTextureWithBPC() { // Create the source data.
    float source[1024* 2];
    for (int i = 0; i <1024* 2; i++) {
        source[i] = (float)i;
    }
    // Initialize the texture by using the size of source in bytes // and bits per scalar element.
    texture<float_2, 1> floatTexture(1024, source, (unsigned int)sizeof(source), 32U);
}
```

Las texturas de estos ejemplos se crean en la vista predeterminada del acelerador predeterminado. Se pueden utilizar otras sobrecargas del constructor si desea especificar un objeto `accelerator_view`. No se puede crear un objeto de textura en un acelerador de CPU.

Hay límites respecto al tamaño de cada dimensión del objeto `texture`, tal como se muestra en la tabla siguiente. Se genera un error en tiempo de ejecución si se superan los límites.

|Textura|Limitación de tamaño por dimensión|
|-------------|---------------------|
|textura\<T, 1 >|16384|
|textura\<T, 2 >|16384|
|textura\<T, 3 >|2048|

### <a name="reading-from-texture-objects"></a>Leer objetos de textura

Puede leer desde un `texture` objeto mediante el uso de [Texture:: operator\[\]](reference/texture-class.md#operator_at), [texture::operator() (operador)](reference/texture-class.md#operator_call), o [texture::get(método)](reference/texture-class.md#get). Los dos operadores devuelven un valor, no una referencia. Por consiguiente, no se puede escribir en un objeto `texture` mediante `texture::operator\[\]`.

```cpp
void readTexture() {
    std::vector<int_2> src;
    for (int i = 0; i <16 *32; i++) {
        int_2 i2(i, i);

        src.push_back(i2);
    }

    std::vector<int_2> dst(16* 32);

    array_view<int_2, 2> arr(16, 32, dst);

    arr.discard_data();

    const texture<int_2, 2> tex9(16, 32, src.begin(), src.end());

    parallel_for_each(tex9.extent, [=, &tex9] (index<2> idx) restrict(amp) { // Use the subscript operator.
        arr[idx].x += tex9[idx].x; // Use the function () operator.
        arr[idx].x += tex9(idx).x; // Use the get method.
        arr[idx].y += tex9.get(idx).y; // Use the function () operator.
        arr[idx].y += tex9(idx[0], idx[1]).y;
    });

    arr.synchronize();
}
```

El siguiente ejemplo de código muestra cómo almacenar los canales de textura en un vector corto y, después, tener acceso a los elementos escalares individuales como propiedades del vector corto.

```cpp
void UseBitsPerScalarElement() { // Create the image data. // Each unsigned int (32-bit) represents four 8-bit scalar elements(r,g,b,a values).
    const int image_height = 16;
    const int image_width = 16;
    std::vector<unsigned int> image(image_height* image_width);

    extent<2> image_extent(image_height, image_width);

    // By using uint_4 and 8 bits per channel, each 8-bit channel in the data source is // stored in one 32-bit component of a uint_4.
    texture<uint_4, 2> image_texture(image_extent, image.data(), image_extent.size()* 4U,  8U);

    // Use can access the RGBA values of the source data by using swizzling expressions of the uint_4.
    parallel_for_each(image_extent,
        [&image_texture](index<2> idx) restrict(amp)
        { // 4 bytes are automatically extracted when reading.
            uint_4 color = image_texture[idx];
            unsigned int r = color.r;
            unsigned int g = color.g;
            unsigned int b = color.b;
            unsigned int a = color.a;
        });
}
```

En la tabla siguiente se enumeran los bits válidos por canal para cada tipo de vector.

|Tipo de datos de textura|Bits válidos por elemento escalar|
|-----------------------|-----------------------------------|
|int, int_2, int_4<br /><br /> uint, uint_2, uint_4|8, 16, 32|
|int_3, uint_3|32|
|float, float_2, float_4|16, 32|
|float_3|32|
|double, double_2|64|
|norm, norm_2, norm_4<br /><br /> unorm, unorm_2, unorm, 4|8, 16|

### <a name="writing-to-texture-objects"></a>Escribir en objetos de textura

Use la [Texture:: Set](reference/texture-class.md#set) método para escribir en `texture` objetos. Un objeto de textura puede ser de solo lectura o de lectura y escritura. Para que un objeto de textura sea de lectura y escritura, deben cumplirse las condiciones siguientes:

- T tiene solo un componente escalar. (No se permiten los vectores cortos).

- T no es **doble**, `norm`, o `unorm`.

- La propiedad `texture::bits_per_scalar_element` es 32.

Si no se cumple ninguna de las tres condiciones, el objeto `texture` es de solo lectura. Las dos primeras condiciones se comprueban durante la compilación. Se genera un error de compilación si hay código que intenta escribir en un objeto de textura `readonly`. La condición para `texture::bits_per_scalar_element` se detecta en tiempo de ejecución y el tiempo de ejecución genera el [unsupported_feature](../../parallel/amp/reference/unsupported-feature-class.md) excepción si se intenta escribir en una variable readonly `texture` objeto.

El siguiente ejemplo de código escribe valores en un objeto de textura.

```cpp
void writeTexture() {
    texture<int, 1> tex1(16);

    parallel_for_each(tex1.extent, [&tex1] (index<1> idx) restrict(amp) {
        tex1.set(idx, 0);
    });
}
```

### <a name="copying-texture-objects"></a>Copiar objetos de textura

Puede copiar entre los objetos de textura utilizando la [copia](reference/concurrency-namespace-functions-amp.md#copy) función o el [copy_async](reference/concurrency-namespace-functions-amp.md#copy_async) funcione, como se muestra en el siguiente ejemplo de código.

```cpp
void copyHostArrayToTexture() { // Copy from source array to texture object by using the copy function.
    float floatSource[1024* 2];
    for (int i = 0; i <1024* 2; i++) {
        floatSource[i] = (float)i;
    }
    texture<float_2, 1> floatTexture(1024);

    copy(floatSource, (unsigned int)sizeof(floatSource), floatTexture);

    // Copy from source array to texture object by using the copy function.
    char charSource[16* 16];
    for (int i = 0; i <16* 16; i++) {
        charSource[i] = (char)i;
    }
    texture<int, 2> charTexture(16, 16, 8U);

    copy(charSource, (unsigned int)sizeof(charSource), charTexture);
    // Copy from texture object to source array by using the copy function.
    copy(charTexture, charSource, (unsigned int)sizeof(charSource));
}
```

También puede copiar de una textura a otra mediante el uso de la [Texture:: copy_to](reference/texture-class.md#copy_to) método. Las dos texturas pueden estar en diferentes objetos accelerator_views. Cuando se copia en un objeto `writeonly_texture_view`, los datos se copian en el objeto subyacente `texture`. Los bits por elemento escalar y la extensión deben ser iguales en los objetos `texture` de origen y destino. Si los requisitos no se cumplen, el runtime inicia una excepción.

## <a name="texture-view-classes"></a>Clases de vista de textura

C++AMP presenta la [texture_view (clase)](../../parallel/amp/reference/texture-view-class.md) en Visual Studio 2013. Las vistas de textura que admiten los mismos tipos de elemento de textura y rangos como el [texture (clase)](../../parallel/amp/reference/texture-class.md), pero a diferencia de las texturas, proporcionan acceso a las características de hardware adicionales como muestreo de textura y asignaciones MIP. Las vistas de textura admiten el acceso de solo lectura, de solo escritura y de lectura y escritura a los datos de textura subyacentes.

- El acceso de solo lectura lo proporciona la especialización de la plantilla `texture_view<const T, N>`, que admite los elementos con 1, 2 o 4 componentes, el muestreo de textura y el acceso dinámico a un intervalo de niveles de asignación MIP que se determinan al crear instancias de la vista.

- El acceso de solo escritura lo proporciona la clase de plantilla no especializada `texture_view<T, N>`, que admite los elementos con 2 o 4 componentes y tiene acceso a un nivel de asignación MIP que se determina al crear instancias de la vista. No admite el muestreo.

- El acceso de lectura y escritura lo proporciona la clase de plantilla no especializada `texture_view<T, N>`, que, de forma similar a las texturas, admite elementos con un solo componente; la vista puede tener acceso a un nivel de asignación MIP que se determina al crear instancias de la vista. No admite el muestreo.

Las vistas de textura son análogas a las vistas de matriz, pero no proporcionan la funcionalidad de administración y el movimiento de datos automática que la [array_view (clase)](../../parallel/amp/reference/array-view-class.md) proporciona a través de la [array (clase)](../../parallel/amp/reference/array-class.md). Solo se puede tener acceso a `texture_view` en la vista de aceleradores donde residen los datos de textura subyacentes.

### <a name="writeonlytextureview-deprecated"></a>writeonly_texture_view está en desuso

Para Visual Studio 2013, C++ AMP presenta mejor compatibilidad para las características de textura de hardware como muestreo y mapas MIP, que podría no ser compatible con la [writeonly_texture_view (clase)](../../parallel/amp/reference/writeonly-texture-view-class.md). La clase `texture_view` introducida recientemente admite un supraconjunto de la funcionalidad de `writeonly_texture_view`; como resultado, `writeonly_texture_view` está en desuso.

Se recomienda, al menos para nuevo código, utilizar `texture_view` para tener acceso a la funcionalidad proporcionada antes por `writeonly_texture_view`. Compare los dos ejemplos de código siguientes que escriben en un objeto de textura con dos componentes (int_2). Observe que en ambos casos, la vista, `wo_tv4`, debe capturarse por el valor de la expresión lambda. A continuación se muestra el ejemplo que usa la nueva clase `texture_view`:

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex4(16);

    texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        wo_tv4.set(idx, int_2(1, 1));
    });
}
```

Este es el ejemplo de la clase `writeonly_texture_view` desusada:

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex4(16);

    writeonly_texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        wo_tv4.set(idx, int_2(1, 1));
    });
}
```

Como puede ver, los dos ejemplos de código son casi idénticos cuando todo lo que se está haciendo es escribir en el nivel de asignación MIP primario. Si utilizó `writeonly_texture_view` en código existente y no tiene previsto mejorar ese código, no tiene que cambiarlo. Sin embargo, si piensa seguir usando ese código, sugerimos que vuelva a escribirlo para usar `texture_view`, porque las mejoras que incluye admiten nuevas características de textura de hardware. Siga leyendo para obtener más información sobre estas nuevas capacidades.

Para obtener más información sobre el desuso de `writeonly_texture_view`, consulte [general sobre el diseño de la vista de textura en C++ AMP](http://blogs.msdn.com/b/nativeconcurrency/archive/2013/07/25/overview-of-the-texture-view-design-in-c-amp.aspx) en la programación paralela en código nativo.

### <a name="instantiating-texture-view-objects"></a>Creación de instancias de objetos de vista de textura

Declarar un `texture_view` es similar a declarar una `array_view` que está asociado con un **matriz**. En el ejemplo de código siguiente se declaran varios objetos `texture` y los objetos `texture_view` asociados a ellos.

```cpp
#include <amp.h>
#include <amp_graphics.h>
using namespace concurrency;
using namespace concurrency::graphics;

void declareTextureViews()
{
    // Create a 16-texel texture of int, with associated texture_views.
    texture<int, 1> intTexture(16);
    texture_view<const int, 1> intTextureViewRO(intTexture);  // read-only
    texture_view<int, 1> intTextureViewRW(intTexture);        // read-write

    // Create a 16 x 32 texture of float_2, with associated texture_views.
    texture<float_2, 2> floatTexture(16, 32);
    texture_view<const float_2, 2> floatTextureViewRO(floatTexture);  // read-only
    texture_view<float_2, 2> floatTextureViewRO(floatTexture);        // write-only

    // Create a 2 x 4 x 8 texture of uint_4, with associated texture_views.
    texture<uint_4, 3> uintTexture(2, 4, 8);
    texture_view<const uint_4, 3> uintTextureViewRO(uintTexture);  // read-only
    texture_view<uint_4, 3> uintTextureViewWO(uintTexture);        // write-only
}
```

Observe que una vista de textura con un tipo de elemento distinto de const y un componente es de lectura y escritura, pero una vista de textura con un tipo de elemento distinto de const y varios componentes es de solo escritura. Las vistas de textura de los tipos de elemento const siempre son de solo lectura, pero si el tipo de elemento no es const, el número de componentes del elemento determina si es de lectura y escritura (un componente) o de solo escritura (varios componentes).

El tipo de elemento de `texture_view` (su declaración como constante y también el número de componentes que tiene) también desempeña un rol para determinar si la vista admite el muestreo de textura y cómo se puede tener acceso a los niveles de asignación MIP:

|Tipo|Componentes|Leer|Write|Muestreo|Acceso de asignación MIP|
|----------|----------------|----------|-----------|--------------|-------------------|
|texture_view\<const T, N>|1, 2, 4|Sí|No (1)|Sí|Sí, indizable. El intervalo se determina en la creación de instancias.|
|Texture_view\<T, N >|1<br /><br /> 2, 4|Sí<br /><br /> No (2)|Sí<br /><br /> Sí|No (1)<br /><br /> No (1)|Sí, un nivel. El nivel se determina en la creación de instancias.<br /><br /> Sí, un nivel. El nivel se determina en la creación de instancias.|

En esta tabla, puede ver que las vistas de textura de solo lectura admiten totalmente las nuevas capacidades a cambio de no poder escribir en la vista. Las vistas de textura de escritura están limitadas a tener acceso solo a un nivel de asignación MIP. Las vistas de textura de lectura y escritura son más especializadas que las de escritura, porque agregan el requisito de que el tipo de elemento de la vista de textura solo tiene un componente. Observe que el muestreo no se admite para las vistas de textura de escritura porque es una operación orientada a la lectura.

### <a name="reading-from-texture-view-objects"></a>Leer objetos de vista de textura

Leer datos de textura sin muestreo a través de una vista de textura es lo mismo que leerlos de la propia textura, salvo que las texturas se capturan por referencia, mientras que las vistas de textura se capturan por valor. Esto se demuestra en los dos ejemplos de código siguientes; primero, mediante `texture` solo:

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> text_data(16);

    parallel_for_each(extent<1>(16), [&] (index<1> idx) restrict(amp) {
        tex_data.set(idx, int_2(1, 1));
    });
}
```

Y a continuación se muestra el mismo ejemplo, ahora con la clase `texture_view`:

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex_data(16);

    texture_view<int_2, 1> tex_view(tex_data);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        tex_view.set(idx, int_2(1, 1));
    });
}
```

Las vistas de textura cuyos elementos se basan en tipos de punto flotante, por ejemplo, float, float_2 o float_4, también se pueden leer mediante el muestreo de textura para aprovechar la compatibilidad de hardware con los distintos modos de filtrado y modos de direccionamiento. C++ AMP admite los dos modos de filtrado que son más comunes en los escenarios de cálculo, como el filtrado de puntos (vecino más cercano) y el filtrado lineal (media ponderada), así como cuatro modos de direccionamiento: ajustado, reflejado, fijo y borde. Para obtener más información sobre los modos de direccionamiento, vea [address_mode (enumeración)](reference/concurrency-graphics-namespace-enums.md#address_mode).

Además de los modos que C++ AMP admite directamente, puede tener acceso a otros modos de filtrado y modos de direccionamiento de la plataforma subyacente mediante la API de interoperabilidad para adoptar una muestra de textura creada directamente con la API de la plataforma. Por ejemplo, Direct3D admite otros modos de filtrado, como el filtrado anisotrópico, y puede aplicar otro modo de direccionamiento a cada dimensión de una textura. Puede crear una muestra de textura cuyas coordenadas se ajusten verticalmente, se reflejen horizontalmente y se muestreen con el filtrado anisotrópico mediante las API de Direct3D, y después aprovechar la muestra en el código de C++ AMP mediante la API de interoperabilidad de `make_sampler`. Para obtener más información, consulte [muestreo de textura en C++ AMP](http://blogs.msdn.com/b/nativeconcurrency/archive/2013/07/18/texture-sampling-in-c-amp.aspx) en la programación paralela en código nativo.

Las vistas de textura también admiten la lectura de asignaciones MIP. Las vistas de textura de solo lectura (las que tienen un tipo de elemento const) proporcionan la máxima flexibilidad porque se puede muestrear dinámicamente un intervalo de niveles de asignación MIP que se determina en la creación de instancias y porque se admiten los elementos que tienen 1, 2 o 4 componentes. Las vistas de textura de lectura y escritura que tienen elementos con un componente también admiten las asignaciones MIP, pero solo de un nivel que se determine en la creación de instancias. Para obtener más información, consulte [textura con asignaciones MIP](http://blogs.msdn.com/b/nativeconcurrency/archive/2013/08/22/texture-with-mipmaps.aspx) en la programación paralela en código nativo.

### <a name="writing-to-texture-view-objects"></a>Escribir en objetos de vista de textura

Use la [texture_view::get método](reference/texture-view-class.md#get) escribir subyacente `texture` a través de la `texture_view` objeto. Una vista de textura puede ser de solo lectura, de lectura y escritura o de solo escritura. Para que una vista de textura sea de escritura, debe tener un tipo de elemento que no sea const; para que una vista de textura sea de lectura y escritura, su tipo de elemento también debe tener un solo componente. De lo contrario, la vista de textura es de solo lectura. Solo se puede tener acceso a un nivel de asignación MIP de una textura a la vez a través de una vista de textura, y el nivel se especifica al crear instancias de la vista.

Este ejemplo muestra cómo escribir en el segundo nivel de asignación MIP más detallado de una textura con cuatro niveles de asignación MIP. El nivel de asignación MIP más detallado es el nivel 0.

```cpp
// Create a texture that has 4 mipmap levels : 16x16, 8x8, 4x4, 2x2
texture<int, 2> tex(extent<2>(16, 16), 16U, 4);

// Create a writable texture view to the second mipmap level :4x4
texture_view<int, 2> w_view(tex, 1);

parallel_for_each(w_view.extent, [=](index<2> idx) restrict(amp)
{
    w_view.set(idx, 123);
});
```

## <a name="interoperability"></a>Interoperabilidad

El runtime de C++ AMP admite la interoperabilidad entre `texture<T,1>` y [interfaz ID3D11Texture1D](http://go.microsoft.com/fwlink/p/?linkId=248503), entre `texture<T,2>` y [interfaz ID3D11Texture2D](http://go.microsoft.com/fwlink/p/?linkId=255317)y entre `texture<T,3>`y [interfaz ID3D11Texture3D](http://go.microsoft.com/fwlink/p/?linkId=255377). El [get_texture](reference/concurrency-graphics-direct3d-namespace-functions.md#get_texture) método toma un `texture` objeto y devuelve un `IUnknown` interfaz. El [make_texture](reference/concurrency-graphics-direct3d-namespace-functions.md#make_texture) método toma un `IUnknown` interfaz y un `accelerator_view` objeto y devuelve un `texture` objeto.

## <a name="see-also"></a>Vea también

[double_2 (clase)](../../parallel/amp/reference/double-2-class.md)<br/>
[double_3 (clase)](../../parallel/amp/reference/double-3-class.md)<br/>
[double_4 (clase)](../../parallel/amp/reference/double-4-class.md)<br/>
[float_2 (clase)](../../parallel/amp/reference/float-2-class.md)<br/>
[float_3 (clase)](../../parallel/amp/reference/float-3-class.md)<br/>
[float_4 (clase)](../../parallel/amp/reference/float-4-class.md)<br/>
[int_2 (clase)](../../parallel/amp/reference/int-2-class.md)<br/>
[int_3 (clase)](../../parallel/amp/reference/int-3-class.md)<br/>
[int_4 (clase)](../../parallel/amp/reference/int-4-class.md)<br/>
[norm_2 (clase)](../../parallel/amp/reference/norm-2-class.md)<br/>
[norm_3 (clase)](../../parallel/amp/reference/norm-3-class.md)<br/>
[norm_4 (clase)](../../parallel/amp/reference/norm-4-class.md)<br/>
[short_vector (estructura)](../../parallel/amp/reference/short-vector-structure.md)<br/>
[short_vector_traits (estructura)](../../parallel/amp/reference/short-vector-traits-structure.md)<br/>
[uint_2 (clase)](../../parallel/amp/reference/uint-2-class.md)<br/>
[uint_3 (clase)](../../parallel/amp/reference/uint-3-class.md)<br/>
[uint_4 (clase)](../../parallel/amp/reference/uint-4-class.md)<br/>
[unorm_2 (clase)](../../parallel/amp/reference/unorm-2-class.md)<br/>
[unorm_3 (clase)](../../parallel/amp/reference/unorm-3-class.md)<br/>
[unorm_4 (clase)](../../parallel/amp/reference/unorm-4-class.md)
