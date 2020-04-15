---
title: Funciones del espacio de nombres de simultaneidad (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::all_memory_fence
- amp/Concurrency::atomic_compare_exchange
- amp/Concurrency::atomic_fetch_dec
- amp/Concurrency::atomic_fetch_max
- amp/Concurrency::atomic_fetch_min
- amp/Concurrency::copy
- amp/Concurrency::direct3d_abort
- amp/Concurrency::direct3d_printf
- amp/Concurrency::global_memory_fence
- amp/Concurrency::tile_static_memory_fence
ms.assetid: 2bef0985-cb90-4ece-90b9-66529aec73c9
ms.openlocfilehash: 1187b745a6d8c903c22958185be8d98a6e3d0204
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376345"
---
# <a name="concurrency-namespace-functions-amp"></a>Funciones del espacio de nombres de simultaneidad (AMP)

||||
|-|-|-|
|[all_memory_fence](#all_memory_fence)|[amp_uninitialize](#amp_uninitialize)|[atomic_compare_exchange](#atomic_compare_exchange)|
|[atomic_exchange (Función, C++ AMP)](#atomic_exchange)|[atomic_fetch_add (Función, C++ AMP)](#atomic_fetch_add)|[atomic_fetch_and (Función, C++ AMP)](#atomic_fetch_and)|
|[atomic_fetch_dec](#atomic_fetch_dec)|[atomic_fetch_inc](#atomic_fetch_inc)|[atomic_fetch_max](#atomic_fetch_max)|
|[atomic_fetch_min](#atomic_fetch_min)|[atomic_fetch_or (Función, C++ AMP)](#atomic_fetch_or)|[atomic_fetch_sub (Función, C++ AMP)](#atomic_fetch_sub)|
|[atomic_fetch_xor (Función, C++ AMP)](#atomic_fetch_xor)|[copy](#copy)|[copy_async](#copy_async)|
|[direct3d_abort](#direct3d_abort)|[direct3d_errorf](#direct3d_errorf)|[direct3d_printf](#direct3d_printf)|
|[global_memory_fence](#global_memory_fence)|[parallel_for_each (Función) (C++ AMP)](#parallel_for_each)|[tile_static_memory_fence](#tile_static_memory_fence)|

## <a name="all_memory_fence"></a><a name="all_memory_fence"></a>all_memory_fence

Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos a memoria. Esto garantiza que todos los accesos a la memoria sean visibles para otros subprocesos en el icono de subproceso y se ejecuten en orden de programa.

```cpp
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Barrier*<br/>
Objeto `tile_barrier` .

## <a name="amp_uninitialize"></a><a name="amp_uninitialize"></a>amp_uninitialize

Anula la inicialización del runtime de C++ AMP. Es legal llamar a esta función varias veces durante una duración de las aplicaciones. Llamar a cualquier API de C++ AMP después de llamar a esta función reinicializará el tiempo de ejecución de C++ AMP. Tenga en cuenta que es ilegal utilizar objetos C++ AMP a través de llamadas a esta función y hacerlo dará lugar a un comportamiento indefinido. Además, llamar simultáneamente a esta función y cualquier otra API de AMP es ilegal y daría lugar a un comportamiento indefinido.

```cpp
void __cdecl amp_uninitialize();
```

## <a name="atomic_compare_exchange"></a><a name="atomic_compare_exchange"></a>atomic_compare_exchange

Compara atómicamente el valor almacenado en una ubicación de memoria especificada en el primer argumento para la igualdad con el valor del segundo argumento especificado y, si los valores son los mismos, el valor de la ubicación de memoria se cambia al del tercer argumento especificado.

```cpp
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

*_Dest*<br/>
La ubicación desde la que se va a comparar uno de los valores que se va a comparar se lee y con la que se va a almacenar el nuevo valor, si existe.

*_Expected_value*<br/>
La ubicación desde la que se lee el segundo valor que se va a comparar.

*value*<br/>
El valor que se almacenará en la `_Dest` `_Dest` ubicación de `_Expected_value`memoria especificada por if es igual a .

### <a name="return-value"></a>Valor devuelto

**true** si la operación se realiza correctamente; de lo contrario, **false**.

## <a name="atomic_exchange-function-c-amp"></a><a name="atomic_exchange"></a>Función atomic_exchange (C++ AMP)

Establece el valor de la ubicación de destino como una operación atómica.

```cpp
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

*_Dest*<br/>
Puntero a la ubicación de destino.

*value*<br/>
Nuevo valor.

### <a name="return-value"></a>Valor devuelto

El valor original de la ubicación de destino.

## <a name="atomic_fetch_add-function-c-amp"></a><a name="atomic_fetch_add"></a>Función atomic_fetch_add (C++ AMP)

Agregue atómicamente un valor al valor de una ubicación de memoria.

```cpp
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

*_Dest*<br/>
Puntero a la ubicación de memoria.

*value*<br/>
Valor que se va a agregar.

### <a name="return-value"></a>Valor devuelto

El valor original de la ubicación de memoria.

## <a name="atomic_fetch_and-function-c-amp"></a><a name="atomic_fetch_and"></a>Función atomic_fetch_and (C++ AMP)

Atomicalmente realiza una operación AND bit a bit de un valor y el valor de una ubicación de memoria.

```cpp
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

*_Dest*<br/>
Puntero a la ubicación de memoria.

*value*<br/>
El valor que se va a utilizar en el cálculo AND bit a bit.

### <a name="return-value"></a>Valor devuelto

El valor original de la ubicación de memoria.

## <a name="atomic_fetch_dec"></a><a name="atomic_fetch_dec"></a>atomic_fetch_dec

Reduce atómicamente el valor almacenado en la ubicación de memoria especificada.

```cpp
inline int atomic_fetch_dec(_Inout_ int* _Dest
    ) restrict(amp)

inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Dest*<br/>
La ubicación en memoria del valor que se va a disminuir.

### <a name="return-value"></a>Valor devuelto

El valor original almacenado en la ubicación de memoria.

## <a name="atomic_fetch_inc"></a><a name="atomic_fetch_inc"></a>atomic_fetch_inc

Aumenta atómicamente el valor almacenado en la ubicación de memoria especificada.

```cpp
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Dest*<br/>
La ubicación en memoria del valor que se va a incrementar.

### <a name="return-value"></a>Valor devuelto

El valor original almacenado en la ubicación de memoria.

## <a name="atomic_fetch_max"></a><a name="atomic_fetch_max"></a>atomic_fetch_max

Calcula atómicamente el valor máximo entre el valor almacenado en la ubicación de memoria especificada en el primer argumento y el valor especificado en el segundo argumento y lo almacena en la misma ubicación de memoria.

```cpp
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

*_Dest*<br/>
La ubicación desde la que se lee uno de los valores que se van a comparar y a la que se va a almacenar el máximo de los dos valores.

*value*<br/>
El valor que se comparará con el valor en la ubicación especificada.

### <a name="return-value"></a>Valor devuelto

El valor original almacenado en la ubicación especificada.

## <a name="atomic_fetch_min"></a><a name="atomic_fetch_min"></a>atomic_fetch_min

Calcula atómicamente el valor mínimo entre el valor almacenado en la ubicación de memoria especificada en el primer argumento y el valor especificado en el segundo argumento y lo almacena en la misma ubicación de memoria.

```cpp
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

*_Dest*<br/>
La ubicación desde la que se lee uno de los valores que se van a comparar y a la que se va a almacenar el mínimo de los dos valores.

*value*<br/>
El valor que se comparará con el valor en la ubicación especificada.

### <a name="return-value"></a>Valor devuelto

El valor original almacenado en la ubicación especificada.

## <a name="atomic_fetch_or-function-c-amp"></a><a name="atomic_fetch_or"></a>Función atomic_fetch_or (C++ AMP)

Realiza atómicamente una operación OR bit a bit con un valor y el valor de una ubicación de memoria.

```cpp
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

*_Dest*<br/>
Puntero a la ubicación de memoria.

*value*<br/>
El valor que se va a utilizar en el cálculo OR bit a bit.

### <a name="return-value"></a>Valor devuelto

El valor original de la ubicación de memoria.

## <a name="atomic_fetch_sub-function-c-amp"></a><a name="atomic_fetch_sub"></a>Función atomic_fetch_sub (C++ AMP)

Resta atómicamente un valor de una ubicación de memoria.

```cpp
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

*_Dest*<br/>
Puntero a la ubicación de destino.

*value*<br/>
El valor que se va a restar.

### <a name="return-value"></a>Valor devuelto

El valor original de la ubicación de memoria.

## <a name="atomic_fetch_xor-function-c-amp"></a><a name="atomic_fetch_xor"></a>Función atomic_fetch_xor (C++ AMP)

Realiza atómicamente una operación XOR bit a bit de un valor y una ubicación de memoria.

```cpp
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

*_Dest*<br/>
Puntero a la ubicación de memoria.

*value*<br/>
El valor que se utilizará en el cálculo XOR.

### <a name="return-value"></a>Valor devuelto

El valor original de la ubicación de memoria.

## <a name="copy"></a><a name="copy"></a>Copia

Copia un objeto C++ AMP. Se cumplen todos los requisitos sincrónicos de transferencia de datos. No se pueden copiar datos al ejecutar código en un acelerador. La forma general de esta función es `copy(src, dest)`.

```cpp
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

*_Dest*<br/>
El objeto en el que se copia.

*_DestIter*<br/>
Iterador de salida a la posición inicial en el destino.

*InputIterator*<br/>
El tipo de iterador de entrada.

*OutputIterator*<br/>
El tipo del iterador de salida.

*_Rank*<br/>
El rango del objeto desde el que se va a copiar o el objeto al que se va a copiar.

*_Src*<br/>
Para objetar para copiar.

*_SrcFirst*<br/>
Iterador inicial en el contenedor de origen.

*_SrcLast*<br/>
Iterador final en el contenedor de origen.

*value_type*<br/>
El tipo de datos de los elementos que se copian.

## <a name="copy_async"></a><a name="copy_async"></a>copy_async

Copia un objeto AMP de C++ y devuelve un objeto [completion_future](completion-future-class.md) que se puede esperar. No se pueden copiar datos al ejecutar código en un acelerador.  La forma general de esta función es `copy(src, dest)`.

```cpp
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

*_Dest*<br/>
El objeto en el que se copia.

*_DestIter*<br/>
Iterador de salida a la posición inicial en el destino.

*InputIterator*<br/>
El tipo de iterador de entrada.

*OutputIterator*<br/>
El tipo del iterador de salida.

*_Rank*<br/>
El rango del objeto desde el que se va a copiar o el objeto al que se va a copiar.

*_Src*<br/>
Para objetar para copiar.

*_SrcFirst*<br/>
Iterador inicial en el contenedor de origen.

*_SrcLast*<br/>
Iterador final en el contenedor de origen.

*value_type*<br/>
El tipo de datos de los elementos que se copian.

### <a name="return-value"></a>Valor devuelto

A `future<void>` que se puede esperar.

## <a name="direct3d_abort"></a><a name="direct3d_abort"></a>direct3d_abort

Anula la ejecución de una función con la cláusula de restricción `restrict(amp)` . Cuando el tiempo de ejecución AMP detecta la llamada, provoca una excepción [runtime_exception](runtime-exception-class.md) con el mensaje de error "Reference Rasterizer: Shader abort instruction hit".

```cpp
void direct3d_abort() restrict(amp);
```

## <a name="direct3d_errorf"></a><a name="direct3d_errorf"></a>direct3d_errorf

Imprime una cadena con formato en la ventana de salida de Visual Studio. Se llama desde una `restrict(amp)` función con la cláusula de restricción. Cuando el tiempo de ejecución de AMP detecta la llamada, genera una [runtime_exception](runtime-exception-class.md) excepción con la misma cadena de formato.

```cpp
void direct3d_errorf(
    const char *,
...) restrict(amp);
```

## <a name="direct3d_printf"></a><a name="direct3d_printf"></a>direct3d_printf

Imprime una cadena con formato en la ventana de salida de Visual Studio. Se llama desde una `restrict(amp)` función con la cláusula de restricción.

```cpp
void direct3d_printf(
    const char *,
...) restrict(amp);
```

## <a name="global_memory_fence"></a><a name="global_memory_fence"></a>global_memory_fence

Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos a memoria globales. Esto garantiza que los accesos a la memoria global sean visibles para otros subprocesos en el icono de subproceso y se ejecuten en orden de programa.

```cpp
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Barrier*<br/>
Un objeto tile_barrier

## <a name="parallel_for_each-function-c-amp"></a><a name="parallel_for_each"></a>Función parallel_for_each (C++ AMP)

Ejecuta una función en el dominio de cálculo. Para obtener más información, consulte Información general de [C++ AMP](../../../parallel/amp/cpp-amp-overview.md).

```cpp
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

*_Accl_view*<br/>
Objeto `accelerator_view` en el que se va a ejecutar el cálculo paralelo.

*_Compute_domain*<br/>
Objeto `extent` que contiene los datos del cálculo.

*_Dim0*<br/>
La dimensión `tiled_extent` del objeto.

*_Dim1*<br/>
La dimensión `tiled_extent` del objeto.

*_Dim2*<br/>
La dimensión `tiled_extent` del objeto.

*_Kernel*<br/>
Un lambda o objeto de función\<que toma un argumento de tipo "index _Rank>" y realiza el cálculo paralelo.

*_Kernel_type*<br/>
Un lambda o functor.

*_Rank*<br/>
El rango de la extensión.

## <a name="tile_static_memory_fence"></a><a name="tile_static_memory_fence"></a>tile_static_memory_fence

Bloquea la ejecución de todos los `tile_static` subprocesos de un icono hasta que se hayan completado todos los accesos de memoria pendientes. Esto garantiza `tile_static` que los accesos a la memoria sean visibles para otros subprocesos en el icono de subproceso y que los accesos se ejecuten en orden de programa.

```cpp
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Barrier*<br/>
Un objeto tile_barrier.

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
