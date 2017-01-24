---
title: "Espacio de nombres de simultaneidad (C++ AMP) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp/Concurrency"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "espacio de nombres de simultaneidad"
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Espacio de nombres de simultaneidad (C++ AMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Proporciona clases y funciones que aceleran la ejecución de código C++ en el hardware de datos en paralelo. Para obtener más información, vea [Introducción a C++ AMP](../../../parallel/amp/cpp-amp-overview.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
namespace Concurrency;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="namespaces"></a>Espacios de nombres  
  
|Name|Descripción|  
|----------|-----------------|  
|[Espacio de nombres Concurrency::Direct3D](../../../parallel/amp/reference/concurrency-direct3d-namespace.md)|Proporciona funciones que admiten interoperabilidad de D3D. Habilita el uso sin problemas de los recursos D3D para el cálculo en el código AMP y el uso de los recursos creados con AMP en código D3D, sin crear copias intermedias redundantes. Puede usar C++ AMP para acelerar incrementalmente las secciones de cálculo intensivo de las aplicaciones DirectX y usar la API D3D en los datos producidos por los cálculos de AMP.|  
|[Espacio de nombres fast_math](../../../parallel/amp/reference/concurrency-fast-math-namespace.md)|Las funciones del espacio de nombres `fast_math` no cumplen el estándar C99. Solo se proporcionan versiones de precisión sencilla de cada función. Estas funciones usan las funciones intrínsecas de DirectX, que son más rápidas que las funciones correspondientes del espacio de nombres `precise_math` y no requieren la compatibilidad de doble precisión extendida en el acelerador, pero son menos precisas. Hay dos versiones de cada función para la compatibilidad de nivel de origen con el código C99; ambas toman y devuelven valores de precisión sencilla.|  
|[Espacio de nombres Concurrency:: Graphics](../../../parallel/amp/reference/concurrency-graphics-namespace.md)|Proporciona tipos y funciones que están diseñados para la programación de gráficos.|  
|[Espacio de nombres precise_math](../../../parallel/amp/reference/concurrency-precise-math-namespace.md)|Las funciones del espacio de nombres `precise_math` cumplen el estándar C99. Se incluyen las versiones de simple precisión y de doble precisión de cada función. Estas funciones, incluidas las funciones de precisión simple, requieren la compatibilidad de doble precisión extendida en el acelerador.|  
  
### <a name="classes"></a>Clases  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Accelerator (clase)](../../../parallel/amp/reference/accelerator-class.md)|Representa una abstracción de un nodo de cálculo físico optimizado para DP.|  
|[accelerator_view (clase)](../../../parallel/amp/reference/accelerator-view-class.md)|Representa una abstracción del dispositivo virtual en un acelerador C++ AMP de datos en paralelo.|  
|[accelerator_view_removed (clase)](../../../parallel/amp/reference/accelerator-view-removed-class.md)|La excepción que se produce cuando una llamada de DirectX subyacente produce un error debido al mecanismo de detección de tiempo de espera y recuperación de Windows.|  
|[Array (clase)](../../../parallel/amp/reference/array-class.md)|Un agregado de datos de una `accelerator_view` en el dominio de la cuadrícula. Es una colección de variables, una para cada elemento de un dominio de la cuadrícula. Cada variable contiene un valor correspondiente a algún tipo de C++.|  
|[array_view (clase)](../../../parallel/amp/reference/array-view-class.md)|Representa una vista de los datos en una matriz\<T,N>.|  
|[completion_future (clase)](../../../parallel/amp/reference/completion-future-class.md)|Representa un futuro que corresponde a la operación asincrónica de C++ AMP.|  
|[Extent (clase)](../../../parallel/amp/reference/extent-class-cpp-amp.md)|Representa un vector de valores enteros de n que especifican los límites de un espacio de n dimensiones que tiene un origen de 0. Los valores del vector de coordenadas se ordenan desde el más significativo al menos significativo. Por ejemplo, en el espacio cartesiano de 3 dimensiones, el vector de medida (7,5,3) representa un espacio en el cual la coordenada Z está comprendida entre 0 y 7, la coordenada Y está comprendida entre 0 y 5 y la coordenada x está comprendida entre 0 y 3.|  
|[Index (clase)](../../../parallel/amp/reference/index-class.md)|Define un punto de índice de n dimensiones.|  
|[invalid_compute_domain (clase)](../../../parallel/amp/reference/invalid-compute-domain-class.md)|La excepción que se produce cuando el runtime no puede iniciar un kernel mediante el dominio del cálculo especificado en el sitio de llamada `parallel_for_each`.|  
|[out_of_memory (clase)](../../../parallel/amp/reference/out-of-memory-class.md)|La excepción se produce cuando un método produce un error debido a la falta de memoria del sistema o del dispositivo.|  
|[runtime_exception (clase)](../../../parallel/amp/reference/runtime-exception-class.md)|El tipo base para las excepciones en la biblioteca de C++ AMP.|  
|[tile_barrier (clase)](../../../parallel/amp/reference/tile-barrier-class.md)|Una clase de capacidad que solo puede crear el sistema y que se pasa a una expresión lambda en mosaico `parallel_for_each` como parte del parámetro `tiled_index`. Proporciona un método, `wait()`, cuyo propósito es sincronizar la ejecución de subprocesos que se ejecutan en el grupo de subprocesos (mosaico).|  
|[tiled_extent (clase)](../../../parallel/amp/reference/tiled-extent-class.md)|Un objeto `tiled_extent` es un objeto `extent` de una a tres dimensiones que divide el espacio de la extensión en un mosaico de una, dos o tres dimensiones.|  
|[tiled_index (clase)](../../../parallel/amp/reference/tiled-index-class.md)|Proporciona un índice en un objeto `tiled_grid`. Esta clase tiene propiedades para tener acceso a elementos relacionados con el origen local del mosaico y con el origen global.|  
|[uninitialized_object (clase)](../../../parallel/amp/reference/uninitialized-object-class.md)|La excepción que se produce cuando se usa un objeto no inicializado.|  
|[unsupported_feature (clase)](../../../parallel/amp/reference/unsupported-feature-class.md)|La excepción que se produce cuando se usa una característica no compatible.|  
  
### <a name="enumerations"></a>Enumeraciones  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[access_type (enumeración)](../Topic/access_type%20Enumeration.md)|Especifica el tipo de acceso de los datos.|  
|[queuing_mode (enumeración)](../../../parallel/amp/reference/queuing-mode-enumeration.md)|Especifica los modos de la puesta en cola que se admiten en el acelerador.|  
  
### <a name="operators"></a>Operadores  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[Operator == (operador, C++ AMP)](../Topic/operator==%20Operator%20\(C++%20AMP\).md)|Determina si las estructuras de datos especificadas son iguales.|  
|[operador! = (operador) (C++ AMP)](../Topic/operator!=%20Operator%20\(C++%20AMP\).md)|Determina si las estructuras de datos especificadas no son iguales.|  
|[operador + (operador) (C++ AMP)](../Topic/operator+%20Operator%20\(C++%20AMP\).md)|Calcula la suma de todos los componentes de los argumentos especificados.|  
|[Operator-(operador) (C++ AMP)](../Topic/operator-%20Operator%20\(C++%20AMP\)1.md)|Calcula la diferencia de todos los componentes entre los argumentos especificados.|  
|[operador * (operador, C++ AMP)](../Topic/operator*%20Operator%20\(C++%20AMP\).md)|Calcula el producto de todos los componentes de los argumentos especificados.|  
|[operador / (operador, C++ AMP)](../Topic/operator-%20Operator%20\(C++%20AMP\)2.md)|Calcula el cociente de todos los componentes de los argumentos especificados.|  
|[operador % (operador, C++ AMP)](../Topic/operator%25%20Operator%20\(C++%20AMP\).md)|Calcula el módulo del primer argumento especificado dividido por el segundo argumento especificado.|  
  
### <a name="functions"></a>Funciones  
  
|Name|Descripción|  
|----------|-----------------|  
|[all_memory_fence (función)](../Topic/all_memory_fence%20Function.md)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos a memoria.|  
|[amp_uninitialize (función)](../Topic/amp_uninitialize%20Function.md)|Anula la inicialización del runtime de C++ AMP.|  
|[atomic_compare_exchange (función)](../Topic/atomic_compare_exchange%20Function.md)|Sobrecargado. Si el valor almacenado en la ubicación especificada es igual al primer valor especificado, el segundo valor especificado se almacena en la misma ubicación como una operación atómica.|  
|[atomic_exchange (función)](../Topic/atomic_exchange%20Function%20\(C++%20AMP\).md)|Sobrecargado. Establece el valor almacenado en la ubicación especificada en el valor especificado como una operación atómica.|  
|[atomic_fetch_add (función)](../Topic/atomic_fetch_add%20Function%20\(C++%20AMP\).md)|Sobrecargado. Establece el valor almacenado en la ubicación especificada en la suma de ese valor y un valor especificado como una operación atómica.|  
|[atomic_fetch_and (función)](../Topic/atomic_fetch_and%20Function%20\(C++%20AMP\).md)|Sobrecargado. Establece el valor almacenado en la ubicación especificada en el operador `and` bit a bit de ese valor y un valor especificado como una operación atómica.|  
|[atomic_fetch_dec (función)](../Topic/atomic_fetch_dec%20Function.md)|Sobrecargado. Disminuye el valor almacenado en la ubicación especificada y almacena el resultado en la misma ubicación como una operación atómica.|  
|[atomic_fetch_inc (función)](../Topic/atomic_fetch_inc%20Function.md)|Sobrecargado. Incrementa el valor almacenado en la ubicación especificada y almacena el resultado en la misma ubicación como una operación atómica.|  
|[atomic_fetch_max (función)](../Topic/atomic_fetch_max%20Function.md)|Sobrecargado. Establece el valor almacenado en la ubicación especificada en el mayor entre ese valor y un valor especificado como una operación atómica.|  
|[atomic_fetch_min (función)](../Topic/atomic_fetch_min%20Function.md)|Sobrecargado. Establece el valor almacenado en la ubicación especificada en el menor entre ese valor y un valor especificado como una operación atómica.|  
|[atomic_fetch_or (función)](../Topic/atomic_fetch_or%20Function%20\(C++%20AMP\).md)|Sobrecargado. Establece el valor almacenado en la ubicación especificada en el operador `or` bit a bit de ese valor y un valor especificado como una operación atómica.|  
|[atomic_fetch_sub (función)](../Topic/atomic_fetch_sub%20Function%20\(C++%20AMP\).md)|Sobrecargado. Establece el valor almacenado en la ubicación especificada en la diferencia entre ese valor y un valor especificado como una operación atómica.|  
|[atomic_fetch_xor (función)](../Topic/atomic_fetch_xor%20Function%20\(C++%20AMP\).md)|Sobrecargado. Establece el valor almacenado en la ubicación especificada en el operador `xor` bit a bit de ese valor y un valor especificado como una operación atómica.|  
|[Copy (función)](../Topic/copy%20Function.md)|Copia un objeto C++ AMP. Se cumplen todos los requisitos sincrónicos de transferencia de datos. Los datos no se pueden copiar cuando el código está ejecutando código en un acelerador. La forma general de esta función es `copy(src, dest)`.|  
|[copy_async (función)](../Topic/copy_async%20Function.md)|Copia un objeto C++ AMP y devuelve [completion_future](../../../parallel/amp/reference/completion-future-class.md) que se puede esperar. Los datos no se pueden copiar cuando el código se está ejecutando en un acelerador. La forma general de esta función es `copy(src, dest)`.|  
|[direct3d_abort (función)](../Topic/direct3d_abort%20Function.md)|Anula la ejecución de una función con la cláusula de restricción `restrict(amp)`.|  
|[direct3d_errorf (función)](../Topic/direct3d_errorf%20Function.md)|Imprime una cadena con formato en Visual Studio **salida** ventana y genera un [runtime_exception](../../../parallel/amp/reference/runtime-exception-class.md) excepción que tiene el mismo formato de cadena.|  
|[direct3d_printf (función)](../Topic/direct3d_printf%20Function.md)|Imprime una cadena con formato en Visual Studio **salida** ventana. Se le llama desde una función con la cláusula de restricción `restrict(amp)`.|  
|[global_memory_fence (función)](../Topic/global_memory_fence%20Function.md)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos a memoria globales.|  
|[parallel_for_each (función) (C++ AMP)](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md)|Ejecuta una función en el dominio de cálculo.|  
|[tile_static_memory_fence (función)](../Topic/tile_static_memory_fence%20Function.md)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos a memoria de `tile_static`.|  
  
## <a name="constants"></a>Constantes  
  
|Name|Descripción|  
|----------|-----------------|  
|[HLSL_MAX_NUM_BUFFERS (constante)](../Topic/HLSL_MAX_NUM_BUFFERS%20Constant.md)|El número máximo de búferes permitido por DirectX.|  
|[MODULENAME_MAX_LENGTH (constante)](../Topic/MODULENAME_MAX_LENGTH%20Constant.md)|Almacena la longitud máxima del nombre del módulo. Este valor debe ser el mismo en el compilador y en el runtime.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (C++ AMP)](../../../parallel/amp/reference/reference-cpp-amp.md)



