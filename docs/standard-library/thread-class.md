---
title: thread (Clase)
ms.date: 11/04/2016
f1_keywords:
- thread/std::thread
- thread/std::thread::id Class
- thread/std::thread::thread
- thread/std::thread::detach
- thread/std::thread::get_id
- thread/std::thread::hardware_concurrency
- thread/std::thread::join
- thread/std::thread::joinable
- thread/std::thread::native_handle
- thread/std::thread::swap
ms.assetid: df249bc7-ff81-4ff9-a6d6-5e3d9a8f56a1
helpviewer_keywords:
- std::thread [C++]
- std::thread [C++], thread
- std::thread [C++], detach
- std::thread [C++], get_id
- std::thread [C++], hardware_concurrency
- std::thread [C++], join
- std::thread [C++], joinable
- std::thread [C++], native_handle
- std::thread [C++], swap
ms.openlocfilehash: f663034cdc7985dd440a1cdfdd659358c4e250f4
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458586"
---
# <a name="thread-class"></a>thread (Clase)

Define un objeto que se utiliza para observar y administrar un subproceso de ejecución dentro de una aplicación.

## <a name="syntax"></a>Sintaxis

```cpp
class thread;
```

## <a name="remarks"></a>Comentarios

Puede usar un objeto  de subproceso para observar y administrar un subproceso de ejecución dentro de una aplicación. Un objeto thread creado con el constructor predeterminado no está asociado a ningún subproceso de ejecución. Un objeto thread construido mediante un objeto al que se puede llamar crea un nuevo subproceso de ejecución y llama al objeto al que se puede llamar en ese subproceso. Los objetos thread se pueden mover pero no copiar. Por tanto, un subproceso de ejecución solo se puede asociar a un objeto thread.

Cada subproceso de ejecución tiene un identificador único de tipo `thread::id`. La función `this_thread::get_id` devuelve el identificador del subproceso que realiza la llamada. La función miembro `thread::get_id` devuelve el identificador del subproceso administrado por un objeto thread. Para un objeto thread creado con el constructor predeterminado, el método `thread::get_id` devuelve un objeto cuyo valor es el mismo para todos los objetos thread creados con el constructor predeterminado y diferente del valor devuelto por `this_thread::get_id` para cualquier subproceso de ejecución que se pueda unir en el momento de la llamada.

## <a name="members"></a>Miembros

### <a name="public-classes"></a>Clases públicas

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[thread::id (Clase)](#id_class)|Identifica de forma única el subproceso asociado.|

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[thread](#thread)|Construye un objeto  de subproceso.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[detach](#detach)|Desasocia el subproceso asociado del  objeto de subproceso.|
|[get_id](#get_id)|Devuelve el identificador único del subproceso asociado.|
|[hardware_concurrency](#hardware_concurrency)|Estático. Devuelve una estimación del número de contextos de subprocesos de hardware.|
|[join](#join)|Se bloquea hasta que el subproceso asociado se completa.|
|[joinable](#joinable)|Especifica si se puede unir el subproceso asociado.|
|[native_handle](#native_handle)|Devuelve el tipo específico de la implementación que representa el identificador de subproceso.|
|[swap](#swap)|Intercambia el estado del objeto con un objeto  de subproceso especificado.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[thread::operator=](#op_eq)|Asocia un subproceso al objeto  de subproceso actual.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<subproceso >

**Espacio de nombres:** std

## <a name="detach"></a>  thread::detach

Desasocia el subproceso asociado. El sistema operativo pasa a ser responsable de liberar los recursos de subproceso al finalizar.

```cpp
void detach();
```

### <a name="remarks"></a>Comentarios

Después de llamar a `detach`, las siguientes llamadas a [get_id](#get_id) devuelven [id](#id_class).

Si el subproceso que está asociado con el objeto de llamada no se puede unir, la función produce un [system_error](../standard-library/system-error-class.md) que tiene un código de error de `invalid_argument`.

Si el subproceso que está asociado con el objeto de llamada no es válido, la función produce un `system_error` que tiene un código de error de `no_such_process`.

## <a name="get_id"></a>  thread::get_id

Devuelve un identificador único para el subproceso asociado.

```cpp
id get_id() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Un objeto [thread::id](#id_class) que identifica de forma única el subproceso asociado, o `thread::id()` si ningún subproceso está asociado con el objeto.

## <a name="hardware_concurrency"></a>  thread::hardware_concurrency

Un método estático que devuelve una estimación del número de contextos de subprocesos de hardware.

```cpp
static unsigned int hardware_concurrency() noexcept;
```

### <a name="return-value"></a>Valor devuelto

Una estimación del número de contextos de subprocesos de hardware. Si el valor no se puede calcular o no está bien definido, este método devuelve 0.

## <a name="id_class"></a>  thread::id (Clase)

Proporciona un identificador único para cada subproceso de ejecución en el proceso.

```cpp
class thread::id {
    id() noexcept;
};
```

### <a name="remarks"></a>Comentarios

El constructor predeterminado crea un objeto que no se compara como igual al objeto `thread::id` de cualquier subproceso existente.

Todos los objetos `thread::id` construidos de forma predeterminada son iguales.

## <a name="join"></a>  thread::join

Se bloquea hasta que finaliza el subproceso de ejecución que está asociado con el objeto de llamada.

```cpp
void join();
```

### <a name="remarks"></a>Comentarios

Si la llamada se realiza correctamente, las llamadas siguientes a [get_id](#get_id) para el objeto que realiza la llamada devuelven un [thread::id](#id_class) predeterminado que no es igual que el `thread::id` de cualquier subproceso existente. Si la llamada no se realiza correctamente, el valor devuelto por `get_id` no cambia.

## <a name="joinable"></a>  thread::joinable

Especifica si se puede *unir* el subproceso asociado.

```cpp
bool joinable() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

**true** si el subproceso asociado es combinable; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Un objeto de subproceso se puede *unir* si `get_id() != id()`.

## <a name="native_handle"></a>Thread:: native_handle

Devuelve el tipo específico de la implementación que representa el identificador de subproceso. El identificador de subproceso puede usarse en aspectos específicos de la implementación.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Valor devuelto

`native_handle_type` se define como un `HANDLE` de Win32 que se convierte en `void *`.

## <a name="op_eq"></a>  thread::operator=

El subproceso de un objeto especificado se asocia con el objeto actual.

```cpp
thread& operator=(thread&& Other) noexcept;
```

### <a name="parameters"></a>Parámetros

*Distinta*\
Objeto  de subproceso.

### <a name="return-value"></a>Valor devuelto

`*this`

### <a name="remarks"></a>Comentarios

Las llamadas de método se separan si el objeto que realiza la llamada se puede unir.

Una vez realizada la asociación, `Other` se establece en un estado construido de forma predeterminada.

## <a name="swap"></a>  thread::swap

Intercambia el estado del objeto con el de un objeto  de subproceso especificado.

```cpp
void swap(thread& Other) noexcept;
```

### <a name="parameters"></a>Parámetros

*Distinta*\
Objeto  de subproceso.

## <a name="thread"></a>  thread::thread (Constructor)

Construye un objeto  de subproceso.

```cpp
thread() noexcept;
template <class Fn, class... Args>
explicit thread(Fn&& F, Args&&... A);

thread(thread&& Other) noexcept;
```

### <a name="parameters"></a>Parámetros

*FORMATO*\
Una función definida por la aplicación que va a ejecutar el subproceso.

*UN*\
Lista de argumentos que se van a pasar a *F*.

*Distinta*\
Objeto de **subproceso** existente.

### <a name="remarks"></a>Comentarios

El primer constructor crea un objeto que no está asociado con un subproceso de ejecución. El valor devuelto por una llamada a `get_id` para el objeto construido es `thread::id()`.

El segundo constructor crea un objeto que está asociado a un nuevo subproceso de ejecución y ejecuta la pseudofunción `INVOKE` que se define en [\<functional>](../standard-library/functional.md). Si no hay suficientes recursos disponibles para iniciar un nuevo subproceso, la función produce un objeto [system_error](../standard-library/system-error-class.md) que tiene un código de error `resource_unavailable_try_again`. Si la llamada a *F* finaliza con una excepción no detectada, [](../standard-library/exception-functions.md#terminate) se llama a Terminate.

El tercer constructor crea un objeto que está asociado con el subproceso que está asociado a `Other`. Después, `Other` se establece en un estado construido de forma predeterminada.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<thread>](../standard-library/thread.md)
