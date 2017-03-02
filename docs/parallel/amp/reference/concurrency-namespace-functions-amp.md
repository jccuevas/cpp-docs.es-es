---
title: Funciones del espacio de nombres de simultaneidad (AMP) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2bef0985-cb90-4ece-90b9-66529aec73c9
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 22ba62ab8b3b4f9d14953dbab3edd8228ea85193
ms.openlocfilehash: a976cc06b49b10d5bb8dcecb10e114efdd89faa8
ms.lasthandoff: 02/24/2017

---
# <a name="concurrency-namespace-functions-amp"></a>Funciones del espacio de nombres de simultaneidad (AMP)
||||  
|-|-|-|  
|[all_memory_fence](#all_memory_fence)|[amp_uninitialize)](#amp_uninitialize)|[atomic_compare_exchange](#atomic_compare_exchange)|  
|[atomic_exchange (función) (C++ AMP)](#atomic_exchange)|[atomic_fetch_add (función) (C++ AMP)](#atomic_fetch_add)|[atomic_fetch_and (función) (C++ AMP)](#atomic_fetch_and)|  
|[atomic_fetch_dec](#atomic_fetch_dec)|[atomic_fetch_inc](#atomic_fetch_inc)|[atomic_fetch_max](#atomic_fetch_max)|  
|[atomic_fetch_min](#atomic_fetch_min)|[atomic_fetch_or (función) (C++ AMP)](#atomic_fetch_or)|[atomic_fetch_sub (función) (C++ AMP)](#atomic_fetch_sub)|  
|[atomic_fetch_xor (función) (C++ AMP)](#atomic_fetch_xor)|[copy](#copy)|[copy_async](#copy_async)|  
|[direct3d_abort](#direct3d_abort)|[direct3d_errorf](#direct3d_errorf)|[direct3d_printf](#direct3d_printf)|  
|[global_memory_fence](#global_memory_fence)|[parallel_for_each (función) (C++ AMP)](#parallel_for_each)|[tile_static_memory_fence](#tile_static_memory_fence)|  
  
##  <a name="a-nameallmemoryfencea--allmemoryfence"></a><a name="all_memory_fence"></a>all_memory_fence  
 Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos a memoria. Esto garantiza que todos los accesos de memoria son visibles para otros subprocesos del mosaico de subprocesos y se ejecutan en orden de programa.  
  
```  
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Barrier`  
 Objeto `tile_barrier`.  
  
##  <a name="a-nameampuninitializea--ampuninitialize"></a><a name="amp_uninitialize"></a>amp_uninitialize)  
 Anula la inicialización del runtime de C++ AMP. Es posible llamar a esta función varias veces durante un período de duración de las aplicaciones. Llamar a cualquier una vez de API de C++ AMP llamar a esta función se reinicialice el tiempo de ejecución de C++ AMP. Tenga en cuenta que no es válido para usar objetos de C++ AMP a través de llamadas a esta función, y esto conlleva un comportamiento indefinido. Además, al mismo tiempo una llamada a esta función y cualquier otro APIs AMP no es válida y daría como resultado un comportamiento indefinido.  
  
```  
void __cdecl amp_uninitialize();
```  
  
##  <a name="a-nameatomiccompareexchangea--atomiccompareexchange"></a><a name="atomic_compare_exchange"></a>atomic_compare_exchange  
 Atómicamente compara el valor almacenado en una ubicación de memoria especificados en el primer argumento de la igualdad con el valor del segundo argumento especificado y, si los valores son iguales, se cambia el valor en la ubicación de memoria para que del tercer argumento especificado.  
  
```  
inline bool atomic_compare_exchange(
    _Inout_ int* _Dest,  
    _Inout_ int* _Expected_value,  
    int value  
    ) restrict(amp)

 
inline bool atomic_compare_exchange(
    _Inout_ unsigned int* _Dest,  
    _Inout_ unsigned int* _Expected_value,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>Parámetros  
 `_Dest`  
 La ubicación desde la que uno de los valores que se va a comparar es de lectura y a la que el nuevo valor, si existe, es que se almacenará.  
  
 `_Expected_value`  
 La ubicación desde la que se lee el segundo valor que se va a comparar.  
  
 `value`  
 El valor que se almacenará en la ubicación de memoria especificada en `_Dest` si `_Dest` es igual a `_Expected_value`.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si la operación es correcta; de lo contrario, `false`.  
  

##  <a name="a-nameatomicexchangea--atomicexchange-function-c-amp"></a><a name="atomic_exchange"></a>atomic_exchange (función) (C++ AMP)  
 Establece el valor de ubicación de destino como una operación atómica.  
  
```  
inline int atomic_exchange(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_exchange(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)

 
inline float atomic_exchange(
    _Inout_ float* _Dest,  
    float value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>Parámetros  
 `_Dest`  
 Puntero a la ubicación de destino.  
  
 `value`  
 Nuevo valor.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor original de la ubicación de destino.  
  

##  <a name="a-nameatomicfetchadda--atomicfetchadd-function-c-amp"></a><a name="atomic_fetch_add"></a>atomic_fetch_add (función) (C++ AMP)  
 Agregar forma atómica un valor en el valor de una ubicación de memoria.  
  
```  
inline int atomic_fetch_add(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_add(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>Parámetros  
 `_Dest`  
 Puntero a la ubicación de memoria.  
  
 `value`  
 Valor que se va a agregar.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor original de la ubicación de memoria.  
  
##  <a name="a-nameatomicfetchanda--atomicfetchand-function-c-amp"></a><a name="atomic_fetch_and"></a>atomic_fetch_and (función) (C++ AMP)  
 Lleva a cabo una operación AND bit a bit de un valor y el valor de una ubicación de memoria de forma atómica.  
  
```  
inline int atomic_fetch_and(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_and(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>Parámetros  
 `_Dest`  
 Puntero a la ubicación de memoria.  
  
 `value`  
 Valor que se va a utilizar en el cálculo de AND bit a bit.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor original de la ubicación de memoria.  
  
##  <a name="a-nameatomicfetchdeca--atomicfetchdec"></a><a name="atomic_fetch_dec"></a>atomic_fetch_dec  
 Atómicamente disminuye el valor almacenado en la ubicación de memoria especificada.  
  
```  
inline int atomic_fetch_dec(_Inout_ int* _Dest  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Dest`  
 La ubicación en la memoria del valor que se va a reducir.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor original almacenado en la ubicación de memoria.  
  
##  <a name="a-nameatomicfetchinca--atomicfetchinc"></a><a name="atomic_fetch_inc"></a>atomic_fetch_inc  
 Atómicamente incrementa el valor almacenado en la ubicación de memoria especificada.  
  
```  
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

 
inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Dest`  
 La ubicación en la memoria del valor que se va a incrementar.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor original almacenado en la ubicación de memoria.  
  
##  <a name="a-nameatomicfetchmaxa--atomicfetchmax"></a><a name="atomic_fetch_max"></a>atomic_fetch_max  
 De forma atómica calcula el valor máximo entre el valor almacenado en la ubicación de memoria especificada en el primer argumento y el valor especificado en el segundo argumento y lo almacena en la misma ubicación de memoria.  
  
```  
inline int atomic_fetch_max(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_max(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>Parámetros  
 `_Dest`  
 La ubicación desde la que uno de los valores que se va a comparar es de lectura y a la que el máximo de los dos valores es almacenar.  
  
 `value`  
 El valor que se comparará con el valor en la ubicación especificada.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor original almacenado en la ubicación de la ubicación especificada.  
  
##  <a name="a-nameatomicfetchmina--atomicfetchmin"></a><a name="atomic_fetch_min"></a>atomic_fetch_min  
 De forma atómica calcula el valor mínimo entre el valor almacenado en la ubicación de memoria especificada en el primer argumento y el valor especificado en el segundo argumento y lo almacena en la misma ubicación de memoria.  
  
```  
inline int atomic_fetch_min(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_min(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>Parámetros  
 `_Dest`  
 La ubicación desde la que uno de los valores que se va a comparar es de lectura y a la que el mínimo de los dos valores es almacenar.  
  
 `value`  
 El valor que se comparará con el valor en la ubicación especificada.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor original almacenado en la ubicación de la ubicación especificada.  
  
##  <a name="a-nameatomicfetchora--atomicfetchor-function-c-amp"></a><a name="atomic_fetch_or"></a>atomic_fetch_or (función) (C++ AMP)  
 Lleva a cabo una operación OR bit a bit con un valor y el valor de una ubicación de memoria de forma atómica.  
  
```  
inline int atomic_fetch_or(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_or(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>Parámetros  
 `_Dest`  
 Puntero a la ubicación de memoria.  
  
 `value`  
 Valor que se va a utilizar en el cálculo de OR bit a bit.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor original de la ubicación de memoria.  
  
##  <a name="a-nameatomicfetchsuba--atomicfetchsub-function-c-amp"></a><a name="atomic_fetch_sub"></a>atomic_fetch_sub (función) (C++ AMP)  
 Resta de forma atómica un valor desde una ubicación de memoria.  
  
```  
inline int atomic_fetch_sub(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_sub(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>Parámetros  
 `_Dest`  
 Puntero a la ubicación de destino.  
  
 `value`  
 Valor que se va a restar.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor original de la ubicación de memoria.  
  
##  <a name="a-nameatomicfetchxora--atomicfetchxor-function-c-amp"></a><a name="atomic_fetch_xor"></a>atomic_fetch_xor (función) (C++ AMP)  
 Atómicamente realiza una operación XOR bit a bit de un valor y una ubicación de memoria.  
  
```  
inline int atomic_fetch_xor(
    _Inout_ int* _Dest,  
    int value  
    ) restrict(amp)

 
inline unsigned int atomic_fetch_xor(
    _Inout_ unsigned int* _Dest,  
    unsigned int value  
    ) restrict(amp)
```  
  
### <a name="parameters"></a>Parámetros  
 `_Dest`  
 Puntero a la ubicación de memoria.  
  
 `value`  
 Valor que se va a utilizar en el cálculo de XOR.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor original de la ubicación de memoria.  
  
##  <a name="a-namecopya--copy"></a><a name="copy"></a>  copy  
 Copia un objeto C++ AMP. Se cumplen todos los requisitos sincrónicos de transferencia de datos. No se puede copiar datos al ejecutar código en un acelerador. La forma general de esta función es `copy(src, dest)`.  
  
```  
template <typename value_type, int _Rank>  
void copy(
    const array<value_type, _Rank>& _Src,  
    array<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
void copy(
    InputIterator _SrcFirst,
    InputIterator _SrcLast,  
    array<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
void copy(
    InputIterator _SrcFirst,  
    array<value_type, _Rank>& _Dest);

 
template <typename OutputIterator, typename value_type, int _Rank>  
void copy(
    const array<value_type, _Rank>& _Src,
     OutputIterator _DestIter);

 
template <typename value_type, int _Rank>  
void copy(
    const array<value_type, _Rank>& _Src,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
void copy(
    const array_view<const value_type, _Rank>& _Src,  
    array<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
void copy(
    const array_view<value_type, _Rank>& _Src,  
    array<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
void copy(
    const array_view<const value_type, _Rank>& _Src,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
void copy(
    const array_view<value_type, _Rank>& _Src,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
void copy(
    InputIterator _SrcFirst, 
    InputIterator _SrcLast,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
void copy(
    InputIterator _SrcFirst,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename OutputIterator, typename value_type, int _Rank>  
void copy(
    const array_view<value_type, _Rank>& _Src,
    OutputIterator _DestIter);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Dest`  
 Objeto que se va a copiar a.  
  
 `_DestIter`  
 Un iterador de salida a la posición inicial en el destino.  
  
 `InputIterator`  
 El tipo de la entrada interator.  
  
 `OutputIterator`  
 El tipo de iterador de salida.  
  
 `_Rank`  
 El rango de objeto que se va a copiar de o el objeto que se va a copiar a.  
  
 `_Src`  
 Para el objeto a copiar.  
  
 `_SrcFirst`  
 Un iterador de comienzo en el contenedor de origen.  
  
 `_SrcLast`  
 Un iterador final en el contenedor de origen.  
  
 `value_type`  
 El tipo de datos de los elementos que se copian.  
  
##  <a name="a-namecopyasynca--copyasync"></a><a name="copy_async"></a>copy_async  
 Copia un objeto C++ AMP y devuelve un [completion_future](completion-future-class.md) objeto que se puede esperar. No se puede copiar datos al ejecutar código en un acelerador.  La forma general de esta función es `copy(src, dest)`.  
  
```  
template <typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src,  
    array<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
concurrency::completion_future copy_async(InputIterator _SrcFirst, InputIterator _SrcLast,  
    array<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
concurrency::completion_future copy_async(InputIterator _SrcFirst,  
    array<value_type, _Rank>& _Dest);

 
template <typename OutputIterator, typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src, OutputIterator _DestIter);

 
template <typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array_view<const value_type, _Rank>& _Src,  
    array<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src,  
    array<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array_view<const value_type, _Rank>& _Src,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
concurrency::completion_future copy_async(InputIterator _SrcFirst, InputIterator _SrcLast,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename InputIterator, typename value_type, int _Rank>  
concurrency::completion_future copy_async(InputIterator _SrcFirst,  
    array_view<value_type, _Rank>& _Dest);

 
template <typename OutputIterator, typename value_type, int _Rank>  
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src, OutputIterator _DestIter);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Dest`  
 Objeto que se va a copiar a.  
  
 `_DestIter`  
 Un iterador de salida a la posición inicial en el destino.  
  
 `InputIterator`  
 El tipo de la entrada interator.  
  
 `OutputIterator`  
 El tipo de iterador de salida.  
  
 `_Rank`  
 El rango de objeto que se va a copiar de o el objeto que se va a copiar a.  
  
 `_Src`  
 Para el objeto a copiar.  
  
 `_SrcFirst`  
 Un iterador de comienzo en el contenedor de origen.  
  
 `_SrcLast`  
 Un iterador final en el contenedor de origen.  
  
 `value_type`  
 El tipo de datos de los elementos que se copian.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `future<void>` que se puede esperar.  
  
##  <a name="a-namedirect3daborta--direct3dabort"></a><a name="direct3d_abort"></a>direct3d_abort  
 Anula la ejecución de una función con la cláusula de restricción `restrict(amp)` . Cuando el runtime de AMP detecta la llamada, provoca un [runtime_exception](runtime-exception-class.md) excepción con el mensaje de error "rasterizador de referencia: sombreador anular acierto de la instrucción".  
  
```  
void direct3d_abort() restrict(amp);
```  
  
##  <a name="a-namedirect3derrorfa--direct3derrorf"></a><a name="direct3d_errorf"></a>direct3d_errorf  
 Imprime una cadena con formato en la ventana de salida de Visual Studio. Se le llama desde una función con el `restrict(amp)` cláusula de restricción. Cuando el runtime de AMP detecta la llamada, provoca un [runtime_exception](runtime-exception-class.md) excepción con la misma cadena de formato.  
  
```  
void direct3d_errorf(
    const char *,  
 ...) restrict(amp);
```  
  
##  <a name="a-namedirect3dprintfa--direct3dprintf"></a><a name="direct3d_printf"></a>direct3d_printf  
 Imprime una cadena con formato en la ventana de salida de Visual Studio. Se le llama desde una función con el `restrict(amp)` cláusula de restricción.  
  
```  
void direct3d_printf(
    const char *,  
 ...) restrict(amp);
```  
  
##  <a name="a-nameglobalmemoryfencea--globalmemoryfence"></a><a name="global_memory_fence"></a>global_memory_fence  
 Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos a memoria globales. Esto garantiza que accesos a memoria globales son visibles para otros subprocesos del mosaico de subprocesos y se ejecutan en orden de programa.  
  
```  
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Barrier`  
 Un objeto tile_barrier  
  
##  <a name="a-nameparallelforeacha--parallelforeach-function-c-amp"></a><a name="parallel_for_each"></a>parallel_for_each (función) (C++ AMP)  
 Ejecuta una función en el dominio de cálculo. Para obtener más información, consulte [Introducción a C++ AMP](../../../parallel/amp/cpp-amp-overview.md).  
  
```  
template <int _Rank, typename _Kernel_type>  
void parallel_for_each(
    const extent<_Rank>& _Compute_domain,  
    const _Kernel_type& _Kernel);

 
template <int _Dim0, int _Dim1, int _Dim2, typename _Kernel_type>  
void parallel_for_each(
    const tiled_extent<_Dim0, _Dim1, _Dim2>& _Compute_domain,
     const _Kernel_type& _Kernel);

 
template <int _Dim0, int _Dim1, typename _Kernel_type>  
void parallel_for_each(
    const tiled_extent<_Dim0, _Dim1>& _Compute_domain,
    const _Kernel_type& _Kernel);

 
template <int _Dim0, typename _Kernel_type>  
void parallel_for_each(
    const tiled_extent<_Dim0>& _Compute_domain,  
    const _Kernel_type& _Kernel);

 
template <int _Rank, typename _Kernel_type>  
void parallel_for_each(
    const accelerator_view& _Accl_view,  
    const extent<_Rank>& _Compute_domain,  
    const _Kernel_type& _Kernel);

 
template <int _Dim0, int _Dim1, int _Dim2, typename _Kernel_type>  
void parallel_for_each(
    const accelerator_view& _Accl_view,  
    const tiled_extent<_Dim0, _Dim1, _Dim2>& _Compute_domain,  
    const _Kernel_type& _Kernel);

 
template <int _Dim0, int _Dim1, typename _Kernel_type>  
void parallel_for_each(
    const accelerator_view& _Accl_view,  
    const tiled_extent<_Dim0, _Dim1>& _Compute_domain,  
    const _Kernel_type& _Kernel);

 
template <int _Dim0, typename _Kernel_type>  
void parallel_for_each(
    const accelerator_view& _Accl_view,  
    const tiled_extent<_Dim0>& _Compute_domain,  
    const _Kernel_type& _Kernel);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Accl_view`  
 La `accelerator_view` objeto que se va a ejecutar el cálculo en paralelo en.  
  
 `_Compute_domain`  
 Un `extent` objeto que contiene los datos para el cálculo.  
  
 `_Dim0`  
 La dimensión de la `tiled_extent` objeto.  
  
 `_Dim1`  
 La dimensión de la `tiled_extent` objeto.  
  
 `_Dim2`  
 La dimensión de la `tiled_extent` objeto.  
  
 `_Kernel`  
 Un objeto de función o expresión lambda que toma un argumento de tipo "índice\<_Rank >" y realiza el cálculo en paralelo.  
  
 `_Kernel_type`  
 Una expresión lambda o un functor.  
  
 `_Rank`  
 El rango de la extensión.  
  
##  <a name="a-nametilestaticmemoryfencea--tilestaticmemoryfence"></a><a name="tile_static_memory_fence"></a>tile_static_memory_fence  
 Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los pendientes `tile_static` accesos a memoria se hayan completado. Esto garantiza que `tile_static` accesos a memoria son visibles para otros subprocesos del mosaico de subprocesos y accesos se ejecutan en orden de programa.  
  
```  
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Barrier`  
 Un objeto tile_barrier.  
  
## <a name="see-also"></a>Vea también  
 [Namespace de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)

