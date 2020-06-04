---
title: Usar objetos accelerator y accelerator_view
ms.date: 11/04/2016
ms.assetid: 18f0dc66-8236-4420-9f46-1a14f2c3fba1
ms.openlocfilehash: 80d9c26f636cc736f90eacddea07a8fc31caff93
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512876"
---
# <a name="using-accelerator-and-accelerator_view-objects"></a>Usar objetos accelerator y accelerator_view

Puede usar las clases [Accelerator](../../parallel/amp/reference/accelerator-class.md) y [accelerator_view](../../parallel/amp/reference/accelerator-view-class.md) para especificar el dispositivo o emulador en el que C++ se ejecutará el código de amp. Un sistema puede tener varios dispositivos o emuladores que se diferencien por la cantidad de memoria, la compatibilidad de memoria compartida, la compatibilidad con la depuración o la compatibilidad de doble precisión. C++El paralelismo masivo aceleradoC++ (amp) proporciona las API que puede usar para examinar los aceleradores disponibles, establecer uno como valor predeterminado, especificar varios accelerator_views para varias llamadas a parallel_for_each y realizar tareas de depuración especiales.

## <a name="using-the-default-accelerator"></a>Usar el acelerador predeterminado

El C++ tiempo de ejecución del amp selecciona un acelerador predeterminado, a menos que escriba código para elegir uno específico. El motor en tiempo de ejecución elige el acelerador predeterminado de la siguiente manera:

1. Si la aplicación se ejecuta en modo de depuración, un acelerador que admita la depuración.

2. De lo contrario, el acelerador especificado por la variable de entorno CPPAMP_DEFAULT_ACCELERATOR, si está establecido.

3. De lo contrario, un dispositivo no emulado.

4. De lo contrario, el dispositivo tiene la mayor cantidad de memoria disponible.

5. De lo contrario, un dispositivo que no esté asociado a la pantalla.

Además, el tiempo de ejecución `access_type` especifica `access_type_auto` un de para el acelerador predeterminado. Esto significa que el acelerador predeterminado usa la memoria compartida si se admite y si se sabe que sus características de rendimiento (ancho de banda y latencia) son las mismas que la memoria dedicada (no compartida).

Puede determinar las propiedades del acelerador predeterminado construyendo el acelerador predeterminado y examinando sus propiedades. En el ejemplo de código siguiente se imprime la ruta de acceso, la cantidad de memoria del acelerador, la compatibilidad de memoria compartida, la compatibilidad de doble precisión y la compatibilidad de doble precisión limitada del acelerador predeterminado.

```cpp
void default_properties() {
    accelerator default_acc;
    std::wcout << default_acc.device_path << "\n";
    std::wcout << default_acc.dedicated_memory << "\n";
    std::wcout << (accs[i].supports_cpu_shared_memory ?
        "CPU shared memory: true" : "CPU shared memory: false") << "\n";
    std::wcout << (accs[i].supports_double_precision ?
        "double precision: true" : "double precision: false") << "\n";
    std::wcout << (accs[i].supports_limited_double_precision ?
        "limited double precision: true" : "limited double precision: false") << "\n";
}
```

### <a name="cppamp_default_accelerator-environment-variable"></a>Variable de entorno CPPAMP_DEFAULT_ACCELERATOR

Puede establecer la variable de entorno CPPAMP_DEFAULT_ACCELERATOR para especificar el `accelerator::device_path` valor del acelerador predeterminado. La ruta de acceso depende del hardware. En el código siguiente se `accelerator::get_all` usa la función para recuperar una lista de los aceleradores disponibles y, a continuación, se muestran la ruta de acceso y las características de cada acelerador.

```cpp
void list_all_accelerators()
{
    std::vector<accelerator> accs = accelerator::get_all();

    for (int i = 0; i <accs.size(); i++) {
        std::wcout << accs[i].device_path << "\n";
        std::wcout << accs[i].dedicated_memory << "\n";
        std::wcout << (accs[i].supports_cpu_shared_memory ?
            "CPU shared memory: true" : "CPU shared memory: false") << "\n";
        std::wcout << (accs[i].supports_double_precision ?
            "double precision: true" : "double precision: false") << "\n";
        std::wcout << (accs[i].supports_limited_double_precision ?
            "limited double precision: true" : "limited double precision: false") << "\n";
    }
}
```

## <a name="selecting-an-accelerator"></a>Selección de un acelerador

Para seleccionar un acelerador, utilice `accelerator::get_all` el método para recuperar una lista de los aceleradores disponibles y, a continuación, seleccione uno basándose en sus propiedades. En este ejemplo se muestra cómo elegir el acelerador que tiene la mayor cantidad de memoria:

```cpp
void pick_with_most_memory()
{
    std::vector<accelerator> accs = accelerator::get_all();
    accelerator acc_chosen = accs[0];

    for (int i = 0; i <accs.size(); i++) {
        if (accs[i].dedicated_memory> acc_chosen.dedicated_memory) {
            acc_chosen = accs[i];
        }
    }

    std::wcout << "The accelerator with the most memory is "
        << acc_chosen.device_path << "\n"
        << acc_chosen.dedicated_memory << ".\n";
}
```

> [!NOTE]
> Uno de los aceleradores devueltos por `accelerator::get_all` es el acelerador de CPU. No se puede ejecutar código en el acelerador de CPU. Para filtrar el acelerador de la CPU, compare el valor de la propiedad [device_path](reference/accelerator-class.md#device_path) del acelerador devuelto por `accelerator::get_all` con el valor de [Accelerator:: cpu_accelerator](reference/accelerator-class.md#cpu_accelerator). Para obtener más información, consulte la sección "aceleradores especiales" de este artículo.

## <a name="shared-memory"></a>Memoria compartida

La memoria compartida es la memoria a la que puede tener acceso la CPU y el acelerador. El uso de memoria compartida elimina o reduce significativamente la sobrecarga de copiar datos entre la CPU y el acelerador. Aunque la memoria está compartida, no se puede tener acceso a ella simultáneamente por la CPU y el acelerador, y esto provoca un comportamiento indefinido. La propiedad Accelerator [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) devuelve **true** si el acelerador admite la memoria compartida y la propiedad [default_cpu_access_type](reference/accelerator-class.md#default_cpu_access_type) obtiene el valor predeterminado de [access_type](reference/concurrency-namespace-enums-amp.md#access_type) para la memoria asignada en el `accelerator`: por ejemplo, las **matrices**asociadas al objeto `accelerator`o `array_view` a los objetos a los que `accelerator`se obtiene acceso en.

El C++ tiempo de ejecución del amp elige automáticamente el `access_type` mejor valor `accelerator`predeterminado para cada uno de ellos, pero las características de rendimiento (ancho de banda y latencia) de la memoria compartida pueden ser peores que las de la memoria del acelerador dedicada (no compartida) cuando leer de la CPU, escribir desde la CPU o ambos. Si la memoria compartida se realiza así como la memoria dedicada para leer y escribir en la CPU, el tiempo de `access_type_read_write`ejecución tiene como valor predeterminado; de lo contrario, el `access_type`Runtime elige un valor predeterminado más conservador y permite que la aplicación lo invalide si el acceso a la memoria los patrones de sus kernels de cálculo se benefician `access_type`de un diferente.

En el ejemplo de código siguiente se muestra cómo determinar si el acelerador predeterminado admite la memoria compartida y, a continuación, se invalida su tipo `accelerator_view` de acceso predeterminado y se crea un a partir de él.

```cpp
#include <amp.h>
#include <iostream>

using namespace Concurrency;

int main()
{
    accelerator acc = accelerator(accelerator::default_accelerator);

    // Early out if the default accelerator doesn’t support shared memory.
    if (!acc.supports_cpu_shared_memory)
    {
        std::cout << "The default accelerator does not support shared memory" << std::endl;
        return 1;
    }

    // Override the default CPU access type.
    acc.set_default_cpu_access_type(access_type_read_write);

    // Create an accelerator_view from the default accelerator. The
    // accelerator_view reflects the default_cpu_access_type of the
    // accelerator it’s associated with.
    accelerator_view acc_v = acc.default_view;
}
```

Siempre refleja la `default_cpu_access_type` propiedad de la `accelerator` clase asociada a y no proporciona ninguna interfaz para invalidar o cambiar su `access_type`. `accelerator_view`

## <a name="changing-the-default-accelerator"></a>Cambiar el acelerador predeterminado

Puede cambiar el acelerador predeterminado llamando al `accelerator::set_default` método. Puede cambiar el acelerador predeterminado solo una vez por cada ejecución de la aplicación y debe cambiarlo antes de que se ejecute cualquier código en la GPU. Las llamadas de función subsiguientes para cambiar el acelerador devuelven **false**. Si desea usar un acelerador diferente en una llamada a `parallel_for_each`, lea la sección "uso de varios aceleradores" de este artículo. En el ejemplo de código siguiente se establece el acelerador predeterminado en uno que no está emulado, no está conectado a una pantalla y admite la precisión doble.

```cpp
bool pick_accelerator()
{
    std::vector<accelerator> accs = accelerator::get_all();
    accelerator chosen_one;

    auto result = std::find_if(accs.begin(), accs.end(),
        [] (const accelerator& acc) {
            return !acc.is_emulated &&
                acc.supports_double_precision &&
                !acc.has_display;
        });

    if (result != accs.end()) {
        chosen_one = *(result);
    }

    std::wcout <<chosen_one.description <<std::endl;
    bool success = accelerator::set_default(chosen_one.device_path);
    return success;
}
```

## <a name="using-multiple-accelerators"></a>Usar varios aceleradores

Hay dos maneras de usar varios aceleradores en la aplicación:

- Puede pasar `accelerator_view` objetos a las llamadas al método [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) .

- Puede construir un objeto de **matriz** mediante un objeto `accelerator_view` específico. El tiempo de ejecución de C + amp tomará el `accelerator_view` objeto del objeto de **matriz** capturado en la expresión lambda.

## <a name="special-accelerators"></a>Aceleradores especiales

Las rutas de acceso de los dispositivos de tres aceleradores especiales están disponibles `accelerator` como propiedades de la clase:

- [acelerador::D miembro de datos irect3d_ref](reference/accelerator-class.md#direct3d_ref): Este acelerador de un solo subproceso usa software de la CPU para emular una tarjeta de gráficos genérica. Se usa de forma predeterminada para la depuración, pero no es útil en producción porque es más lento que los aceleradores de hardware. Además, solo está disponible en el SDK de DirectX y en el Windows SDK, y no es probable que esté instalado en los equipos de los clientes. Para obtener más información, vea Depurar [código de GPU](/visualstudio/debugger/debugging-gpu-code).

- [acelerador::D miembro de datos irect3d_warp](reference/accelerator-class.md#direct3d_warp): Este acelerador proporciona una solución de reserva para C++ ejecutar código de amp en CPU de varios núcleos que usan extensiones SIMD de streaming (SSE).

- [miembro de datos Accelerator:: cpu_accelerator](reference/accelerator-class.md#cpu_accelerator): Puede usar este acelerador para configurar matrices de ensayo. No puede ejecutar C++ el código amp. Para obtener más información, consulte el blog sobre las [matrices C++ provisionales en amp](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/11/09/staging-arrays-in-c-amp/) en el blog de programación en paralelo en código nativo.

## <a name="interoperability"></a>Interoperabilidad

El C++ tiempo de ejecución del amp admite la `accelerator_view` interoperabilidad entre la clase y la [interfaz ID3D11Device](/windows/win32/api/d3d11/nn-d3d11-id3d11device)de Direct3D. El método [create_accelerator_view](reference/concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view) toma una `IUnknown` interfaz y devuelve un `accelerator_view` objeto. El método [get_device](reference/concurrency-direct3d-namespace-functions-amp.md#get_device) toma un `accelerator_view` objeto y devuelve una `IUnknown` interfaz.

## <a name="see-also"></a>Vea también

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Depurar código de GPU](/visualstudio/debugger/debugging-gpu-code)<br/>
[accelerator_view (clase)](../../parallel/amp/reference/accelerator-view-class.md)
