---
title: Usar objetos accelerator y accelerator_view | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 18f0dc66-8236-4420-9f46-1a14f2c3fba1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8cc676407a88979679a362b3d36f361614524432
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="using-accelerator-and-acceleratorview-objects"></a>Usar objetos accelerator y accelerator_view
Puede usar el [acelerador](../../parallel/amp/reference/accelerator-class.md) y [accelerator_view](../../parallel/amp/reference/accelerator-view-class.md) las clases para especificar el dispositivo o emulador para ejecutar el código de C++ AMP. Un sistema podría tener varios dispositivos o los emuladores que se distinguen por la cantidad de memoria, la compatibilidad de memoria compartida, la compatibilidad con la depuración ni la compatibilidad de doble precisión. C++ Accelerated Massive Parallelism (C++ AMP) proporciona las API que puede utilizar para examinar los aceleradores disponibles, establezca uno de ellos como el valor predeterminado, especifique varios objetos accelerator_views para varias llamadas a parallel_for_each y realizar tareas de depuración especiales.  
  
## <a name="using-the-default-accelerator"></a>Usar el Acelerador predeterminado  
 El tiempo de ejecución de C++ AMP recoge un acelerador predeterminado, a menos que escriba código para seleccionar una en concreto. El runtime elige el Acelerador predeterminado como sigue:  
  
1.  Si la aplicación se ejecuta en modo de depuración, un acelerador que admite la depuración.  
  
2.  En caso contrario, el acelerador especificado por la variable de entorno CPPAMP_DEFAULT_ACCELERATOR, si se establece.  
  
3.  En caso contrario, un dispositivo no emulados.  
  
4.  En caso contrario, el dispositivo que tiene la mayor cantidad de memoria disponible.  
  
5.  En caso contrario, un dispositivo que no esté conectado a la pantalla.  
  
 Además, el tiempo de ejecución especifica un `access_type` de `access_type_auto` para el Acelerador predeterminado. Esto significa que el Acelerador predeterminado utiliza memoria compartida si se admite y sus características de rendimiento (ancho de banda y latencia) suelen ser la misma que la memoria dedicada (no compartidos).  
  
 Puede determinar las propiedades del Acelerador predeterminado mediante la construcción el Acelerador predeterminado y examinar sus propiedades. En el ejemplo de código siguiente se imprime la ruta de acceso, la cantidad de memoria de acelerador, compatibilidad con memoria compartida, compatibilidad de doble precisión y una compatibilidad limitada con precisión doble del Acelerador predeterminado.  
  
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
  
### <a name="cppampdefaultaccelerator-environment-variable"></a>Variable de entorno CPPAMP_DEFAULT_ACCELERATOR  
 Puede establecer la variable de entorno CPPAMP_DEFAULT_ACCELERATOR para especificar el `accelerator::device_path` del Acelerador predeterminado. La ruta de acceso depende del hardware. El siguiente código utiliza el `accelerator::get_all` función para recuperar una lista de los aceleradores disponibles y, a continuación, muestra la ruta de acceso y las características de cada acelerador.  
  
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
  
## <a name="selecting-an-accelerator"></a>Al seleccionar una tecla de aceleración  
 Para seleccionar un acelerador, use la `accelerator::get_all` método para recuperar una lista de los aceleradores disponibles y, a continuación, seleccione una en función de sus propiedades. Este ejemplo muestra cómo seleccionar el acelerador que tiene la mayor cantidad de memoria:  
  
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
>  Uno de los aceleradores que se devuelven por `accelerator::get_all` es el Acelerador de CPU. No se puede ejecutar código en el Acelerador de CPU. Para filtrar el Acelerador de CPU, compare el valor de la [device_path](reference/accelerator-class.md#device_path) propiedad del acelerador que es devuelto por `accelerator::get_all` con el valor de la [accelerator::cpu_accelerator](reference/accelerator-class.md#cpu_accelerator). Para obtener más información, vea la sección "Aceleradores especial" en este artículo.  
  
## <a name="shared-memory"></a>Memoria compartida  
 Memoria compartida es la memoria que puede tener acceso a la CPU y el acelerador. El uso de memoria compartida se elimina o reduce considerablemente la sobrecarga de copiar datos entre la CPU y el acelerador. Aunque la memoria se comparte, no se puede tener acceso simultáneamente a la CPU y el acelerador y, al hacerlo provoca un comportamiento indefinido. La propiedad de acelerador [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) devuelve `true` si el acelerador es compatible con memoria compartida y el [default_cpu_access_type](reference/accelerator-class.md#default_cpu_access_type) propiedad obtiene el valor predeterminado [access_type](reference/concurrency-namespace-enums-amp.md#access_type) para la memoria asignada en el `accelerator`: por ejemplo, `array`que están asociadas a la `accelerator`, o `array_view` objetos obtiene acceso en la `accelerator`. 
  
 El tiempo de ejecución de C++ AMP elige automáticamente el mejor valor predeterminado `access_type` para cada `accelerator`, pero las características de rendimiento (ancho de banda y latencia) de memoria compartida pueden ser peores que los de memoria dedicada acelerador (no compartidos) al leer de la CPU, escribir de la CPU, o ambos. Si realiza la memoria compartida, así como memoria dedicada para lectura y escritura de la CPU, el tiempo de ejecución predeterminado `access_type_read_write`; en caso contrario, el runtime elige el valor predeterminado es más conservador `access_type`y permite que la aplicación reemplazarlo si tener acceso la memoria patrones de los kernels de su cálculo beneficiarán de otro `access_type`.  
  
 En el ejemplo de código siguiente se muestra cómo determinar si el Acelerador predeterminado es compatible con memoria compartida y, a continuación, reemplaza el tipo de acceso predeterminado y crea un `accelerator_view` de él.  
  
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
  
 Un `accelerator_view` siempre refleja el `default_cpu_access_type` de la `accelerator` que está asociado, y no proporciona ninguna interfaz para invalidar o cambiar su `access_type`.  
  
## <a name="changing-the-default-accelerator"></a>Cambiar el Acelerador predeterminado  
 Puede cambiar el Acelerador predeterminado mediante una llamada a la `accelerator::set_default` método. Puede cambiar el Acelerador predeterminado de una sola vez por cada aplicación de ejecución y debe cambiarla antes de ejecutar cualquier código en la GPU. Devolverán las llamadas de función subsiguiente para cambiar el Acelerador `false`. Si desea usar un acelerador de diferentes en una llamada a `parallel_for_each`, lea la sección "Usar los aceleradores varios" en este artículo. En el ejemplo de código siguiente se establece el Acelerador predeterminado por uno que no se emula, no está conectado a una visualización y admite la precisión doble.  
  
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
 Hay dos maneras de utilizar varias aceleradores de la aplicación:  

-   Puede pasar `accelerator_view` objetos a las llamadas a la [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) método.  
  
-   Puede construir un `array` objeto con un determinado `accelerator_view` objeto. El tiempo de ejecución de C + AMP recogerá el `accelerator_view` objeto desde el capturada `array` objeto en la expresión lambda.  
  
## <a name="special-accelerators"></a>Aceleradores especiales  
 Las rutas de acceso de dispositivo de tres aceleradores especiales están disponibles como propiedades de la `accelerator` clase:  
  
- [Miembro de datos direct3d_ref](reference/accelerator-class.md#direct3d_ref): este acelerador de un único subproceso usa el software en la CPU para emular una tarjeta gráfica genérico. Se utiliza de forma predeterminada para la depuración, pero no es útil en producción porque es más lento que los aceleradores de hardware. Además, está disponible en el SDK de DirectX y el SDK de Windows, y es probable que estén instalados en equipos de sus clientes. Para obtener más información, consulte [depurar código de GPU](/visualstudio/debugger/debugging-gpu-code).  
  
- [Miembro de datos direct3d_warp](reference/accelerator-class.md#direct3d_warp): este acelerador proporciona una solución de reserva para la ejecución de código de C++ AMP en las CPU de varios núcleos que utilizan las extensiones SIMD de transmisión por secuencias (SSE).  
  
- [Miembro de datos Accelerator::cpu_accelerator](reference/accelerator-class.md#cpu_accelerator): puede usar este acelerador para la configuración de matrices de almacenamiento provisional. No puede ejecutar código de C++ AMP. Para obtener más información, consulte el [matrices de almacenamiento provisional en C++ AMP](http://go.microsoft.com/fwlink/p/?linkId=248485) post en la programación paralela en código nativo.  
  
## <a name="interoperability"></a>Interoperabilidad  
 El tiempo de ejecución de C++ AMP admite la interoperabilidad entre el `accelerator_view` clase y la Direct3D [ID3D11Device interfaz](http://go.microsoft.com/fwlink/p/?linkId=248488). El [create_accelerator_view](reference/concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view) método toma una `IUnknown` interfaz y devuelve un `accelerator_view` objeto. El [get_device](http://msdn.microsoft.com/en-us/8194125e-8396-4d62-aa8a-65831dea8439) método toma una `accelerator_view` objeto y devuelve una `IUknown` interfaz.  
  
## <a name="see-also"></a>Vea también  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Depurar código de GPU](/visualstudio/debugger/debugging-gpu-code)   
 [accelerator_view (clase)](../../parallel/amp/reference/accelerator-view-class.md)
