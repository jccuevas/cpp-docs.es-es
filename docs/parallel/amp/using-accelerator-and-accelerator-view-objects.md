---
title: Usar objetos accelerator y accelerator_view | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 18f0dc66-8236-4420-9f46-1a14f2c3fba1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58eb907841abf63d77817e106ee339ad6c49bd7b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681208"
---
# <a name="using-accelerator-and-acceleratorview-objects"></a>Usar objetos accelerator y accelerator_view
Puede usar el [acelerador](../../parallel/amp/reference/accelerator-class.md) y [accelerator_view](../../parallel/amp/reference/accelerator-view-class.md) clases para especificar el dispositivo o emulador para ejecutar el código de C++ AMP. Un sistema podría tener varios dispositivos o emuladores que difieren según la cantidad de memoria, la compatibilidad de memoria compartida, la compatibilidad con la depuración o compatibilidad de doble precisión. C++ Accelerated Massive Parallelism (C++ AMP) proporciona las API que puede usar para examinar los aceleradores disponibles, establecer uno como el valor predeterminado, especifique varios objetos accelerator_views para múltiples llamadas a y realizar tareas de depuración especiales.  
  
## <a name="using-the-default-accelerator"></a>Usar el Acelerador predeterminado  
 
El runtime de C++ AMP selecciona un acelerador predeterminado, a menos que escriba código para seleccionar uno. El runtime elige el Acelerador predeterminado como sigue:  
  
1. Si la aplicación se ejecuta en modo de depuración, un acelerador que admite la depuración.  
  
2. En caso contrario, el acelerador especificado por el entorno cppamp_default_accelerator, si se establece.  
  
3. En caso contrario, un dispositivo no emulado.  
  
4. En caso contrario, el dispositivo que tiene la mayor cantidad de memoria disponible.  
  
5. En caso contrario, un dispositivo que no se asocia a la pantalla.  
  
Además, especifica el tiempo de ejecución un `access_type` de `access_type_auto` para el Acelerador predeterminado. Esto significa que el Acelerador predeterminado utiliza memoria compartida si se admite y sus características de rendimiento (ancho de banda y latencia) se conocen a ser la misma que la memoria dedicada (no compartida).  
  
Puede determinar las propiedades del Acelerador predeterminado mediante la construcción del Acelerador predeterminado y examinar sus propiedades. El ejemplo de código siguiente imprime la ruta de acceso, la cantidad de memoria de Acelerador de la memoria compartida, compatibilidad de doble precisión y la compatibilidad con compatibilidad de doble precisión limitada del Acelerador predeterminado.  
  
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
  
### <a name="cppampdefaultaccelerator-environment-variable"></a>Entorno Cppamp_default_accelerator  
Puede establecer la opción de entorno cppamp_default_accelerator para especificar el `accelerator::device_path` del Acelerador predeterminado. La ruta de acceso depende del hardware. El siguiente código utiliza el `accelerator::get_all` de función para recuperar una lista de los aceleradores disponibles y, a continuación, muestra la ruta de acceso y las características de cada acelerador.  
  
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
 
Para seleccionar un acelerador, utilice el `accelerator::get_all` método para recuperar una lista de los aceleradores disponibles y, a continuación, seleccione una según sus propiedades. En este ejemplo se muestra cómo elegir el acelerador que tenga la mayor cantidad de memoria:  
  
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
> Uno de los aceleradores devueltos por `accelerator::get_all` es el Acelerador de CPU. No se puede ejecutar código en el Acelerador de CPU. Para filtrar el Acelerador de CPU, compare el valor de la [device_path](reference/accelerator-class.md#device_path) propiedad del Acelerador devuelto por `accelerator::get_all` con el valor de la [Accelerator:: cpu_accelerator](reference/accelerator-class.md#cpu_accelerator). Para obtener más información, consulte la sección «Aceleradores especiales» en este artículo.  
  
## <a name="shared-memory"></a>Memoria compartida  
 
Memoria compartida es memoria que se puede acceder por la CPU y el acelerador. El uso de memoria compartida elimina o reduce la sobrecarga de copiar datos entre la CPU y el acelerador. Aunque la memoria se comparte, no se puede acceder a él al mismo tiempo la CPU y el acelerador y, si lo hace un comportamiento indefinido. La propiedad de acelerador [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) devuelve **true** si el Acelerador admite memoria compartida y el [default_cpu_access_type](reference/accelerator-class.md#default_cpu_access_type) procedimientos property get el valor predeterminado [access_type](reference/concurrency-namespace-enums-amp.md#access_type) para la memoria asignada en el `accelerator`— por ejemplo, **matriz**asociada con el `accelerator`, o `array_view` objetos accedidos en el `accelerator`. 
  
El runtime de C++ AMP elige automáticamente el mejor valor predeterminado `access_type` para cada `accelerator`, pero las características de rendimiento (ancho de banda y latencia) de memoria compartida pueden ser peores que las de memoria de acelerador (no compartida) dedicada al leer de la CPU, escribir desde la CPU, o ambos. Si realiza la memoria compartida, así como la memoria dedicada para lectura y escritura de la CPU, el tiempo de ejecución predeterminado `access_type_read_write`; en caso contrario, el runtime elige un valor predeterminado más conservador `access_type`y permite que la aplicación invalidarlo si tener acceso la memoria patrones de los núcleos de cálculo se benefician de otro `access_type`.  
  
El ejemplo de código siguiente muestra cómo determinar si el Acelerador predeterminado admite memoria compartida y, a continuación, invalida su tipo de acceso predeterminada y crea un `accelerator_view` de él.  
  
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
  
Un `accelerator_view` siempre refleja el `default_cpu_access_type` de la `accelerator` está asociado, y no proporciona ninguna interfaz para reemplazar o cambiar su `access_type`.  
  
## <a name="changing-the-default-accelerator"></a>Cambio del Acelerador predeterminado  
 
Puede cambiar el Acelerador predeterminado mediante una llamada a la `accelerator::set_default` método. Puede cambiar el Acelerador predeterminado solo una vez por cada aplicación de ejecución y debe cambiarlo antes de ejecutar cualquier código en la GPU. Devolverán las llamadas de función subsiguientes para cambiar el Acelerador **false**. Si desea utilizar otro acelerador en una llamada a `parallel_for_each`, lea la sección "Uso de varios aceleradores" en este artículo. El ejemplo de código siguiente establece el Acelerador predeterminado en uno que no se emula, no está conectado a una pantalla y admite doble precisión.  
  
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
 
Hay dos maneras de utilizar varios aceleradores en la aplicación:  

- Puede pasar `accelerator_view` objetos a las llamadas a la [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) método.  
  
- Puede construir un **matriz** un determinado objeto `accelerator_view` objeto. El runtime de C+AMP recogerá el `accelerator_view` objeto capturado **matriz** objeto en la expresión lambda.  
  
## <a name="special-accelerators"></a>Aceleradores especiales  
 
Las rutas de acceso de dispositivo de tres aceleradores especiales están disponibles como propiedades de la `accelerator` clase:  
  
- [Miembro de datos direct3d_ref](reference/accelerator-class.md#direct3d_ref): este acelerador de un único subproceso utiliza el software de la CPU para emular una tarjeta de gráficos genérica. Se utiliza de forma predeterminada para la depuración, pero no es útil en producción porque es más lento que los aceleradores de hardware. Además, está disponible solo en el SDK de DirectX y el SDK de Windows y no es probable que esté instalado en los equipos de sus clientes. Para obtener más información, consulte [depurar código de GPU](/visualstudio/debugger/debugging-gpu-code).  
  
- [Miembro de datos direct3d_warp](reference/accelerator-class.md#direct3d_warp): este acelerador proporciona una solución de reserva para ejecutar código de C++ AMP en CPUs de varios núcleos que usan las extensiones SIMD de transmisión por secuencias (SSE).  
  
- [Miembro de datos Accelerator:: cpu_accelerator](reference/accelerator-class.md#cpu_accelerator): puede utilizar este acelerador para establecer las matrices provisionales. No puede ejecutar código C++ AMP. Para obtener más información, consulte el [matrices provisionales en C++ AMP](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/11/09/staging-arrays-in-c-amp/) publicar en la programación paralela en código nativo.  
  
## <a name="interoperability"></a>Interoperabilidad  
 
El runtime de C++ AMP admite la interoperabilidad entre el `accelerator_view` clase y la Direct3D [interfaz ID3D11Device](/windows/desktop/api/d3d11/nn-d3d11-id3d11device). El [create_accelerator_view](reference/concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view) método toma un `IUnknown` interfaz y devuelve un `accelerator_view` objeto. El [get_device](reference/concurrency-direct3d-namespace-functions-amp.md#get_device) método toma un `accelerator_view` objeto y devuelve un `IUnknown` interfaz.  
  
## <a name="see-also"></a>Vea también  
 
[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
[Depurar código de GPU](/visualstudio/debugger/debugging-gpu-code)   
[accelerator_view (clase)](../../parallel/amp/reference/accelerator-view-class.md)