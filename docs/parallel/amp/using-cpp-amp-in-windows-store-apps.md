---
title: Usar C++ AMP en aplicaciones UWP
ms.date: 11/04/2016
ms.assetid: 85577298-2c28-4209-9470-eb21048615db
ms.openlocfilehash: 9e17cb8691408d664f403b53e9cd8ad70fe6e5e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447764"
---
# <a name="using-c-amp-in-uwp-apps"></a>Usar C++ AMP en aplicaciones UWP

Puede utilizar C++ AMP (C++ Accelerated Massive Parallelism) en la aplicación de plataforma Universal de Windows (UWP) para realizar cálculos en la GPU (unidad de procesamiento de gráficos) o en otros aceleradores de cálculo. Sin embargo, C++ AMP no proporciona las API para trabajar directamente con los tipos de Windows Runtime y este no proporciona un contenedor para C++ AMP. Cuando use los tipos de Windows Runtime en el código, incluidos los que ha creado usted mismo, debe convertirlos en tipos compatibles con C++ AMP.

## <a name="performance-considerations"></a>Consideraciones sobre el rendimiento

Si usa extensiones de componentes de C++ de Visual C++ / c++ / CX para crear la aplicación de plataforma Universal de Windows (UWP), le recomendamos que use tipos de datos de antiguos sin formato (POD) junto con almacenamiento contiguo, por ejemplo, `std::vector` o matrices de estilo C, para los datos que serán Puede usar con C++ AMP. Esto puede ayudarle a conseguir un rendimiento mayor que el logrado mediante tipos o contenedores que no sean POD o Windows RT, ya que no se debe realizar ninguna serialización.

En un kernel de C++ AMP, para obtener acceso a los datos que se almacenan de esta manera, simplemente ajuste `std::vector` o el almacenamiento para la matriz en `concurrency::array_view` y use la vista de matriz en un bucle `concurrency::parallel_for_each`:

```cpp
// simple vector addition example
std::vector<int> data0(1024, 1);
std::vector<int> data1(1024, 2);
std::vector<int> data_out(data0.size(), 0);

concurrency::array_view<int, 1> av0(data0.size(), data0);
concurrency::array_view<int, 1> av1(data1.size(), data1);
concurrency::array_view<int, 1> av2(data_out.size(), data2);

av2.discard_data();

concurrency::parallel_for_each(av0.extent, [=](concurrency::index<1> idx) restrict(amp)
    {
        av2[idx] = av0[idx] + av1[idx];
    });
```

## <a name="marshaling-windows-runtime-types"></a>Serialización de tipos de Windows Runtime

Cuando se trabaja con Windows Runtime APIs, desea utilizar C++ AMP en los datos que se almacenan en un contenedor de Windows en tiempo de ejecución, como un `Platform::Array<T>^` o en tipos de datos complejos como clases o structs que se declaran mediante la **ref** palabra clave o el **valor** palabra clave. En estas situaciones, tiene que realizar alguna tarea adicional para que los datos estén disponibles para C++ AMP.

### <a name="platformarrayt-where-t-is-a-pod-type"></a>Platform:: Array\<T > ^, donde T es un tipo POD

Cuando encuentra un contenedor `Platform::Array<T>^` y T es un tipo POD, puede tener acceso al almacén subyacente simplemente usando la función miembro `get`:

```cpp
Platform::Array<float>^ arr; // Assume that this was returned by a Windows Runtime API
concurrency::array_view<float, 1> av(arr->Length, &arr->get(0));
```

Si T no es un tipo POD, use la técnica que se describe en la sección siguiente para utilizar los datos con C++ AMP.

### <a name="windows-runtime-types-ref-classes-and-value-classes"></a>Tipos de Windows en tiempo de ejecución: clases de referencia y clases de valor

C++ AMP no admite tipos de datos complejos. Esto incluye tipos que no sean POD y cualquier tipo que se declara mediante la **ref** palabra clave o el **valor** palabra clave. Si se usa un tipo no compatible en un contexto `restrict(amp)`, se genera un error en tiempo de compilación.

Si encuentra un tipo no compatible, puede copiar elementos interesantes de sus datos en un objeto `concurrency::array`. Además de conseguir que los datos estén disponibles para su uso por parte de C++ AMP, este enfoque de copia manual también puede mejorar el rendimiento maximizando la situación de los datos y garantizando que los datos que no se usen no se copiarán en el acelerador. Puede mejorar aún más el rendimiento mediante el uso de un *matriz provisional*, que es una forma especial de `concurrency::array` que proporciona una sugerencia al runtime de AMP que la matriz debe estar optimizada para las transferencias frecuentes entre ella y otras matrices en la Acelerador especificado.

```cpp
// pixel_color.h
ref class pixel_color sealed
{
public:
    pixel_color(Platform::String^ color_name, int red, int green, int blue)
    {
        name = color_name;
        r = red;
        g = green;
        b = blue;
    }

    property Platform::String^ name;
    property int r;
    property int g;
    property int b;
};

// Some other file

std::vector<pixel_color^> pixels (256);

for (pixel_color ^pixel : pixels)
{
    pixels.push_back(ref new pixel_color("blue", 0, 0, 255));
}

// Create the accelerators
auto cpuAccelerator = concurrency::accelerator(concurrency::accelerator::cpu_accelerator);
auto devAccelerator = concurrency::accelerator(concurrency::accelerator::default_accelerator);

// Create the staging arrays
concurrency::array<float, 1> red_vec(256, cpuAccelerator.default_view, devAccelerator.default_view);
concurrency::array<float, 1>  blue_vec(256, cpuAccelerator.default_view, devAccelerator.default_view);

// Extract data from the complex array of structs into staging arrays.
concurrency::parallel_for(0, 256, [&](int i)
    {
        red_vec[i] = pixels[i]->r;
        blue_vec[i] = pixels[i]->b;
    });

// Array views are still used to copy data to the accelerator
concurrency::array_view<float, 1> av_red(red_vec);
concurrency::array_view<float, 1> av_blue(blue_vec);

// Change all pixels from blue to red.
concurrency::parallel_for_each(av_red.extent, [=](index<1> idx) restrict(amp)
    {
        av_red[idx] = 255;
        av_blue[idx] = 0;
    });
```

## <a name="see-also"></a>Vea también

[Cree su primera aplicación UWP con C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)<br/>
[Crear componentes de Windows en tiempo de ejecución en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)