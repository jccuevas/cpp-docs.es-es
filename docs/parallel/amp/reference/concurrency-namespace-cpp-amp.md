---
title: Espacio de nombres de simultaneidad (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- AMP/Concurrency
helpviewer_keywords:
- Concurrency namespace
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
ms.openlocfilehash: 34c3c10fa6bec2737ba78a71c282f90f284a28c2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139366"
---
# <a name="concurrency-namespace-c-amp"></a>Espacio de nombres de simultaneidad (C++ AMP)

Proporciona clases y funciones que aceleran la ejecución de código C++ en el hardware de datos en paralelo. Para obtener más información, consulte [ C++ información general de amp.](../cpp-amp-overview.md)

## <a name="syntax"></a>Sintaxis

```cpp
namespace Concurrency;
```

## <a name="members"></a>Members

### <a name="namespaces"></a>Espacios de nombres

|Nombre|Descripción|
|----------|-----------------|
|[Concurrency::direct3d (espacio de nombres)](concurrency-direct3d-namespace.md)|Proporciona funciones que admiten interoperabilidad de D3D. Habilita el uso sin problemas de los recursos D3D para el cálculo en el código AMP y el uso de los recursos creados con AMP en código D3D, sin crear copias intermedias redundantes. Puede usar C++ AMP para acelerar incrementalmente las secciones de cálculo intensivo de las aplicaciones DirectX y usar la API D3D en los datos producidos por los cálculos de AMP.|
|[Concurrency::fast_math (espacio de nombres)](concurrency-fast-math-namespace.md)|Las funciones del espacio de nombres `fast_math` no cumplen el estándar C99. Solo se proporcionan versiones de precisión sencilla de cada función. Estas funciones usan las funciones intrínsecas de DirectX, que son más rápidas que las funciones correspondientes del espacio de nombres `precise_math` y no requieren la compatibilidad de doble precisión extendida en el acelerador, pero son menos precisas. Hay dos versiones de cada función para la compatibilidad de nivel de origen con el código C99; ambas toman y devuelven valores de precisión sencilla.|
|[Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)|Proporciona tipos y funciones que están diseñados para la programación de gráficos.|
|[Concurrency::precise_math (espacio de nombres)](concurrency-precise-math-namespace.md)|Las funciones del espacio de nombres `precise_math` cumplen el estándar C99. Se incluyen las versiones de simple precisión y de doble precisión de cada función. Estas funciones, incluidas las funciones de precisión simple, requieren la compatibilidad de doble precisión extendida en el acelerador.|

### <a name="classes"></a>Clases

|Nombre|Descripción|
|----------|-----------------|
|[accelerator (clase)](accelerator-class.md)|Representa una abstracción de un nodo de cálculo físico optimizado para DP.|
|[accelerator_view (clase)](accelerator-view-class.md)|Representa una abstracción del dispositivo virtual en un acelerador C++ AMP de datos en paralelo.|
|[accelerator_view_removed (clase)](accelerator-view-removed-class.md)|La excepción que se produce cuando una llamada de DirectX subyacente produce un error debido al mecanismo de detección de tiempo de espera y recuperación de Windows.|
|[array (clase)](array-class.md)|Un agregado de datos de una `accelerator_view` en el dominio de la cuadrícula. Es una colección de variables, una para cada elemento de un dominio de la cuadrícula. Cada variable contiene un valor correspondiente a algún tipo de C++.|
|[array_view (clase)](array-view-class.md)|Representa una vista de los datos de una matriz\<T, N >.|
|[completion_future (clase)](completion-future-class.md)|Representa un futuro que corresponde a la operación asincrónica de C++ AMP.|
|[extent (Clase)](extent-class.md)|Representa un vector de valores enteros de n que especifican los límites de un espacio de n dimensiones que tiene un origen de 0. Los valores del vector de coordenadas se ordenan desde el más significativo al menos significativo. Por ejemplo, en el espacio cartesiano de 3 dimensiones, el vector de medida (7,5,3) representa un espacio en el cual la coordenada Z está comprendida entre 0 y 7, la coordenada Y está comprendida entre 0 y 5 y la coordenada x está comprendida entre 0 y 3.|
|[index (clase)](index-class.md)|Define un punto de índice de n dimensiones.|
|[invalid_compute_domain (clase)](invalid-compute-domain-class.md)|La excepción que se produce cuando el runtime no puede iniciar un kernel mediante el dominio del cálculo especificado en el sitio de llamada `parallel_for_each`.|
|[out_of_memory (clase)](out-of-memory-class.md)|La excepción se produce cuando un método produce un error debido a la falta de memoria del sistema o del dispositivo.|
|[runtime_exception (clase)](runtime-exception-class.md)|El tipo base para las excepciones en la biblioteca de C++ AMP.|
|[tile_barrier (clase)](tile-barrier-class.md)|Una clase de capacidad que solo puede crear el sistema y que se pasa a una expresión lambda en mosaico `parallel_for_each` como parte del parámetro `tiled_index`. Proporciona un método, `wait()`, cuyo propósito es sincronizar la ejecución de subprocesos que se ejecutan en el grupo de subprocesos (mosaico).|
|[tiled_extent (clase)](tiled-extent-class.md)|Un objeto `tiled_extent` es un objeto `extent` de una a tres dimensiones que divide el espacio de la extensión en un mosaico de una, dos o tres dimensiones.|
|[tiled_index (clase)](tiled-index-class.md)|Proporciona un índice en un objeto `tiled_grid`. Esta clase tiene propiedades para tener acceso a elementos relacionados con el origen local del mosaico y con el origen global.|
|[uninitialized_object (clase)](uninitialized-object-class.md)|La excepción que se produce cuando se usa un objeto no inicializado.|
|[unsupported_feature (clase)](unsupported-feature-class.md)|La excepción que se produce cuando se usa una función no compatible.|

### <a name="enumerations"></a>Enumeraciones

|Nombre|Descripción|
|----------|-----------------|
|[Enumeración access_type](concurrency-namespace-enums-amp.md#access_type)|Especifica el tipo de acceso de los datos.|
|[Enumeración queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode)|Especifica los modos de la puesta en cola que se admiten en el acelerador.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|--------------|-----------------|
|[Operator = = (operadorC++ ) (amp)](concurrency-namespace-operators-amp.md#operator_eq_eq)|Determina si las estructuras de datos especificadas son iguales.|
|[Operator! = (operadorC++ ) (amp)](concurrency-namespace-operators-amp.md#operator_neq)|Determina si las estructuras de datos especificadas no son iguales.|
|[Operator + (operadorC++ ) (amp)](concurrency-namespace-operators-amp.md#operator_add)|Calcula la suma de todos los componentes de los argumentos especificados.|
|[Operator-(operadorC++ ) (amp)](concurrency-namespace-operators-amp.md#operator-)|Calcula la diferencia de todos los componentes entre los argumentos especificados.|
|[operador Operator * (C++ amp)](concurrency-namespace-operators-amp.md#operator_star)|Calcula el producto de todos los componentes de los argumentos especificados.|
|[operador/operador (C++ amp)](concurrency-namespace-operators-amp.md#operator_div)|Calcula el cociente de todos los componentes de los argumentos especificados.|
|[Operator% (operadorC++ ) (amp)](concurrency-namespace-operators-amp.md#operator_mod)|Calcula el módulo del primer argumento especificado dividido por el segundo argumento especificado.|

### <a name="functions"></a>Functions

|Nombre|Descripción|
|----------|-----------------|
|[all_memory_fence](concurrency-namespace-functions-amp.md#all_memory_fence)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos a memoria.|
|[amp_uninitialize](concurrency-namespace-functions-amp.md#amp_uninitialize)|Anula la inicialización del runtime de C++ AMP.|
|[atomic_compare_exchange](concurrency-namespace-functions-amp.md#atomic_compare_exchange)|Sobrecargado. Si el valor almacenado en la ubicación especificada es igual al primer valor especificado, el segundo valor especificado se almacena en la misma ubicación como una operación atómica.|
|[atomic_exchange](concurrency-namespace-functions-amp.md#atomic_exchange)|Sobrecargado. Establece el valor almacenado en la ubicación especificada en el valor especificado como una operación atómica.|
|[atomic_fetch_add](concurrency-namespace-functions-amp.md#atomic_fetch_add)|Sobrecargado. Establece el valor almacenado en la ubicación especificada en la suma de ese valor y un valor especificado como una operación atómica.|
|[atomic_fetch_and](concurrency-namespace-functions-amp.md#atomic_fetch_and)|Sobrecargado. Establece el valor almacenado en la ubicación especificada en el operador `and` bit a bit de ese valor y un valor especificado como una operación atómica.|
|[atomic_fetch_dec](concurrency-namespace-functions-amp.md#atomic_fetch_dec)|Sobrecargado. Disminuye el valor almacenado en la ubicación especificada y almacena el resultado en la misma ubicación como una operación atómica.|
|[atomic_fetch_inc](concurrency-namespace-functions-amp.md#atomic_fetch_inc)|Sobrecargado. Incrementa el valor almacenado en la ubicación especificada y almacena el resultado en la misma ubicación como una operación atómica.|
|[atomic_fetch_max](concurrency-namespace-functions-amp.md#atomic_fetch_max)|Sobrecargado. Establece el valor almacenado en la ubicación especificada en el mayor entre ese valor y un valor especificado como una operación atómica.|
|[atomic_fetch_min](concurrency-namespace-functions-amp.md#atomic_fetch_min)|Sobrecargado. Establece el valor almacenado en la ubicación especificada en el menor entre ese valor y un valor especificado como una operación atómica.|
|[atomic_fetch_or](concurrency-namespace-functions-amp.md#atomic_fetch_or)|Sobrecargado. Establece el valor almacenado en la ubicación especificada en el operador `or` bit a bit de ese valor y un valor especificado como una operación atómica.|
|[atomic_fetch_sub](concurrency-namespace-functions-amp.md#atomic_fetch_sub)|Sobrecargado. Establece el valor almacenado en la ubicación especificada en la diferencia entre ese valor y un valor especificado como una operación atómica.|
|[atomic_fetch_xor](concurrency-namespace-functions-amp.md#atomic_fetch_xor)|Sobrecargado. Establece el valor almacenado en la ubicación especificada en el operador `xor` bit a bit de ese valor y un valor especificado como una operación atómica.|
|[copy](concurrency-namespace-functions-amp.md#copy)|Copia un objeto C++ AMP. Se cumplen todos los requisitos sincrónicos de transferencia de datos. Los datos no se pueden copiar cuando el código está ejecutando código en un acelerador. La forma general de esta función es `copy(src, dest)`.|
|[copy_async](concurrency-namespace-functions-amp.md#copy_async)|Copia un C++ objeto amp y devuelve [completion_future](completion-future-class.md) que se pueden esperar. Los datos no se pueden copiar cuando el código se está ejecutando en un acelerador. La forma general de esta función es `copy(src, dest)`.|
|[direct3d_abort](concurrency-namespace-functions-amp.md#direct3d_abort)|Anula la ejecución de una función con la cláusula de restricción `restrict(amp)`.|
|[direct3d_errorf](concurrency-namespace-functions-amp.md#direct3d_errorf)|Imprime una cadena con formato en la ventana de **salida** de Visual Studio y genera una excepción [runtime_exception](runtime-exception-class.md) que tiene la misma cadena de formato.|
|[direct3d_printf](concurrency-namespace-functions-amp.md#direct3d_printf)|Imprime una cadena con formato en la ventana de **salida** de Visual Studio. Se le llama desde una función con la cláusula de restricción `restrict(amp)`.|
|[global_memory_fence](concurrency-namespace-functions-amp.md#global_memory_fence)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos a memoria globales.|
|[Función parallel_for_each (C++ amp)](concurrency-namespace-functions-amp.md#parallel_for_each)|Ejecuta una función en el dominio de cálculo.|
|[tile_static_memory_fence](concurrency-namespace-functions-amp.md#tile_static_memory_fence)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos a memoria de `tile_static`.|

## <a name="constants"></a>Constantes

|Nombre|Descripción|
|----------|-----------------|
|[HLSL_MAX_NUM_BUFFERS constante)](concurrency-namespace-constants-amp.md#hlsl_max_num_buffers)|El número máximo de búferes permitido por DirectX.|
|[MODULENAME_MAX_LENGTH constante)](concurrency-namespace-constants-amp.md#modulename_max_length)|Almacena la longitud máxima del nombre del módulo. Este valor debe ser el mismo en el compilador y en el runtime.|

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

## <a name="see-also"></a>Consulte también

[Referencia (C++ AMP)](reference-cpp-amp.md)
