---
title: "Usar objetos accelerator y accelerator_view | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 18f0dc66-8236-4420-9f46-1a14f2c3fba1
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# Usar objetos accelerator y accelerator_view
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Puede usar el [Acelerador](../../parallel/amp/reference/accelerator-class.md) y [accelerator_view](../../parallel/amp/reference/accelerator-view-class.md) especificar el dispositivo o emulador para ejecutar el código de C++ AMP que las clases. Un sistema podría tener varios dispositivos o emuladores que difieren en la cantidad de memoria, la compatibilidad de memoria compartida, la compatibilidad con la depuración o compatibilidad de doble precisión. C++ Accelerated Massive Parallelism (C++ AMP) proporciona API que puede utilizar para examinar los aceleradores disponibles, establecer uno como el valor predeterminado, especifique varios objetos accelerator_views para varias llamadas a parallel_for_each y realizar tareas de depuración especiales.  
  
## <a name="using-the-default-accelerator"></a>Con el Acelerador predeterminado  
 El tiempo de ejecución de C++ AMP recoge un acelerador predeterminado, a menos que escriba código para elegir una en concreto. El runtime elige el Acelerador predeterminado como sigue:  
  
1.  Si la aplicación se ejecuta en modo de depuración, un acelerador que admite la depuración.  
  
2.  De lo contrario, el acelerador especificado por la variable de entorno CPPAMP_DEFAULT_ACCELERATOR, si se establece.  
  
3.  De lo contrario, un dispositivo no emulados.  
  
4.  De lo contrario, el dispositivo que tiene la mayor cantidad de memoria disponible.  
  
5.  De lo contrario, un dispositivo que no esté conectado a la pantalla.  
  
 Además, el tiempo de ejecución especifica un `access_type` de `access_type_auto` para el Acelerador predeterminado. Esto significa que el Acelerador predeterminado utiliza memoria compartida si se admite y sus características de rendimiento (ancho de banda y latencia) suelen ser la misma que la memoria dedicada (no compartido).  
  
 Puede determinar las propiedades del Acelerador predeterminado creando el Acelerador predeterminado y examinar sus propiedades. En el ejemplo de código siguiente se imprime la ruta de acceso, la cantidad de memoria de acelerador, compatibilidad de memoria compartida, compatibilidad de doble precisión y compatibilidad de doble precisión limitada del Acelerador predeterminado.  
  
```cpp  
 
void default_properties() {  
    accelerator default_acc;  
    std::wcout <<default_acc.device_path <<"\n";  
    std::wcout <<default_acc.dedicated_memory <<"\n";  
    std::wcout <<(accs[i].supports_cpu_shared_memory    
 "CPU shared memory: true" : "CPU shared memory: false") <<"\n";  
    std::wcout <<(accs[i].supports_double_precision    
 "double precision: true" : "double precision: false") <<"\n";  
    std::wcout <<(accs[i].supports_limited_double_precision    
 "limited double precision: true" : "limited double precision: false") <<"\n";  
}  
 
```  
  
### <a name="cppampdefaultaccelerator-environment-variable"></a>Variable de entorno CPPAMP_DEFAULT_ACCELERATOR  
 Puede establecer la variable de entorno CPPAMP_DEFAULT_ACCELERATOR para especificar el `accelerator::device_path` del Acelerador predeterminado. La ruta de acceso depende del hardware. El siguiente código utiliza el `accelerator::get_all` función para recuperar una lista de los aceleradores disponibles y, a continuación, muestra la ruta de acceso y las características de cada acelerador.  
  
```cpp  
 
void list_all_accelerators()  
{  
    std::vector<accelerator> accs = accelerator::get_all();
for (int i = 0; i <accs.size();

i++) {  
    std::wcout <<accs[i].device_path <<"\n";  
    std::wcout <<accs[i].dedicated_memory <<"\n";  
    std::wcout <<(accs[i].supports_cpu_shared_memory    
 "CPU shared memory: true" : "CPU shared memory: false") <<"\n";  
    std::wcout <<(accs[i].supports_double_precision    
 "double precision: true" : "double precision: false") <<"\n";  
    std::wcout <<(accs[i].supports_limited_double_precision    
 "limited double precision: true" : "limited double precision: false") <<"\n";  
 }  
}  
 
```  
  
## <a name="selecting-an-accelerator"></a>Seleccionar una tecla de aceleración  
 Para seleccionar un acelerador, use la `accelerator::get_all` método para recuperar una lista de los aceleradores disponibles y, a continuación, seleccione una basada en sus propiedades. Este ejemplo muestra cómo seleccionar el acelerador que tiene la mayor cantidad de memoria:  
  
```cpp  
 
void pick_with_most_memory()  
{  
    std::vector<accelerator> accs = accelerator::get_all();
accelerator acc_chosen = accs[0];  
    for (int i = 0; i <accs.size();

i++) {  
    if (accs[i].dedicated_memory> acc_chosen.dedicated_memory) {  
    acc_chosen = accs[i];  
 }  
 }  
 
    std::wcout <<"The accelerator with the most memory is "    
 <<acc_chosen.device_path <<"\n"  
 <<acc_chosen.dedicated_memory <<".\n";  
}  
 
```  
  
> [!NOTE]
>  Uno de los aceleradores devueltos por `accelerator::get_all` es el Acelerador de CPU. No se puede ejecutar código en el Acelerador de CPU. Para filtrar el Acelerador de CPU, compare el valor de la [device_path](../Topic/accelerator::device_path%20Data%20Member.md) propiedad del acelerador que es devuelto por `accelerator::get_all` con el valor de la [accelerator::cpu_accelerator](../Topic/accelerator::cpu_accelerator%20Data%20Member.md). Para obtener más información, consulte la sección "Aceleradores especiales" de este artículo.  
  
## <a name="shared-memory"></a>Memoria compartida  
 Memoria compartida es que puede tener acceso por la CPU y el acelerador. El uso de memoria compartida se elimina o reduce la sobrecarga de copiar datos entre la CPU y el acelerador. Aunque la memoria se comparte, no se puede tener acceso simultáneamente a la CPU y el acelerador y al hacerlo provoca un comportamiento indefinido. La propiedad accelerator [supports_cpu_shared_memory](../Topic/accelerator::supports_cpu_shared_memory%20Data%20Member.md) devuelve `true` Si el acelerador es compatible con memoria compartida y el [default_cpu_access_type](../Topic/accelerator::default_cpu_access_type%20Data%20Member.md) propiedad obtiene el valor predeterminado [access_type ()](../Topic/access_type%20Enumeration.md) para la memoria asignada en el `accelerator`por ejemplo, `array`asociados con el `accelerator`, o `array_view` objetos obtiene acceso en la `accelerator`.  
  
 El tiempo de ejecución de C++ AMP elige automáticamente la mejor predeterminado `access_type` para cada `accelerator`, pero las características de rendimiento de memoria compartida (ancho de banda y latencia) pueden ser peores que los de memoria dedicada acelerador (no compartido) al leer de la CPU, la escritura de la CPU, o ambas. Si realiza la memoria compartida, así como la memoria dedicada para lectura y escritura de la CPU, el tiempo de ejecución predeterminado `access_type_read_write`; en caso contrario, el runtime elige el valor predeterminado es más conservador `access_type`, y permite a la aplicación invalidarlo si los patrones de acceso de la memoria del kernel de su cálculo beneficiarán de otra `access_type`.  
  
 En el ejemplo de código siguiente se muestra cómo determinar si el Acelerador predeterminado es compatible con memoria compartida y, a continuación, reemplaza su tipo de acceso predeterminado y crea un `accelerator_view` de él.  
  
```cpp  
#include <amp.h>  
#include <iostream>  
  
using namespace Concurrency;  
  
int main()  
{  
  accelerator acc = accelerator(accelerator::default_accelerator);  
  
  // Early out if the default accelerator doesn’t support shared memory.  
  if(!acc.supports_cpu_shared_memory)  
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
  
 Un `accelerator_view` siempre refleja el `default_cpu_access_type` de la `accelerator` está asociado y no proporciona ninguna interfaz para reemplazar o cambiar su `access_type`.  
  
## <a name="changing-the-default-accelerator"></a>Cambiar el Acelerador predeterminado  
 Puede cambiar el Acelerador predeterminado llamando el `accelerator::set_default` método. Puede cambiar el Acelerador predeterminado de una sola vez por cada aplicación de ejecución y debe cambiarla antes de ejecutar cualquier código en la GPU. Devolverán las llamadas de función subsiguientes para cambiar el Acelerador de `false`. Si desea utilizar un acelerador de diferentes en una llamada a `parallel_for_each`, lea la sección "Usar los aceleradores varios" en este artículo. En el ejemplo de código siguiente se establece el Acelerador predeterminado por uno que no se emula, no está conectado a una pantalla y admite la precisión doble.  
  
```cpp  
 
    bool pick_accelerator()  
{  
    std::vector<accelerator> accs = accelerator::get_all();
accelerator chosen_one;  
 
    auto result = 
    std::find_if(accs.begin(), accs.end(), [] (const accelerator& acc)  
 {  
    return !acc.is_emulated&& 
    acc.supports_double_precision&& 
 !acc.has_display;  
 });

 
    if (result != accs.end())  
    chosen_one = *(result);

 
    std::wcout <<chosen_one.description <<std::endl;  
 
    bool success = accelerator::set_default(chosen_one.device_path);

    return success;  
}  
 
```  
  
## <a name="using-multiple-accelerators"></a>Usar varios aceleradores  
 Hay dos maneras de utilizar varias aceleradores en su aplicación:  
  
-   Puede pasar `accelerator_view` objetos a las llamadas a la [parallel_for_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) método.  
  
-   Puede construir un `array` un determinado de objeto `accelerator_view` objeto. El tiempo de ejecución de C + AMP recogerá la `accelerator_view` objeto desde el capturada `array` objeto en la expresión lambda.  
  
## <a name="special-accelerators"></a>Aceleradores especiales  
 Están disponibles como propiedades de las rutas de acceso de dispositivo de tres aceleradores especiales de la `accelerator` clase:  
  
- [Miembro de datos de direct3d_ref](../Topic/accelerator::direct3d_ref%20Data%20Member.md): este acelerador de un único subproceso utiliza el software de la CPU para emular una tarjeta gráfica genérico. Se utiliza de forma predeterminada para la depuración, pero no es útil en producción porque es más lento que los aceleradores de hardware. Además, está disponible sólo en el SDK de DirectX y el SDK de Windows y no es probable que estén instalados en los equipos de sus clientes. Para obtener más información, consulte [Depurar código de GPU](../Topic/Debugging%20GPU%20Code.md).  
  
- [Miembro de datos de direct3d_warp](../Topic/accelerator::direct3d_warp%20Data%20Member.md): este acelerador proporciona una solución de reserva para ejecutar código de C++ AMP en las CPU de varios núcleo que usan extensiones de SIMD de transmisión (SSE).  
  
- [Miembro de datos de Accelerator::cpu_accelerator](../Topic/accelerator::cpu_accelerator%20Data%20Member.md): puede utilizar este acelerador para la configuración de matrices de almacenamiento provisional. No puede ejecutar código de C++ AMP. Para obtener más información, consulte el [matrices de almacenamiento provisional en C++ AMP](http://go.microsoft.com/fwlink/p/LinkId=248485) registrar en la programación en paralelo en código nativo.  
  
## <a name="interoperability"></a>Interoperabilidad  
 El tiempo de ejecución de C++ AMP admite la interoperabilidad entre el `accelerator_view` clase y la Direct3D [interfaz ID3D11Device](http://go.microsoft.com/fwlink/p/LinkId=248488). El [create_accelerator_view](../Topic/create_accelerator_view%20Function.md) método toma un `IUnknown` interfaz y devuelve un `accelerator_view` objeto. El [get_device](http://msdn.microsoft.com/es-es/8194125e-8396-4d62-aa8a-65831dea8439) método toma un `accelerator_view` objeto y devuelve una `IUknown` interfaz.  
  
## <a name="see-also"></a>Vea también  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Depurar código de GPU](../Topic/Debugging%20GPU%20Code.md)   
 [accelerator_view (clase)](../../parallel/amp/reference/accelerator-view-class.md)
