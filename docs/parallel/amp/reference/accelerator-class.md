---
title: Accelerator (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- AMPRT/accelerator
- AMPRT/Concurrency::accelerator::accelerator
- AMPRT/Concurrency::accelerator::create_view
- AMPRT/Concurrency::accelerator::get_all
- AMPRT/Concurrency::accelerator::get_auto_selection_view
- AMPRT/Concurrency::accelerator::get_dedicated_memory
- AMPRT/Concurrency::accelerator::get_default_cpu_access_type
- AMPRT/Concurrency::accelerator::get_default_view
- AMPRT/Concurrency::accelerator::get_description
- AMPRT/Concurrency::accelerator::get_device_path
- AMPRT/Concurrency::accelerator::get_has_display
- AMPRT/Concurrency::accelerator::get_is_debug
- AMPRT/Concurrency::accelerator::get_is_emulated
- AMPRT/Concurrency::accelerator::get_supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::get_supports_double_precision
- AMPRT/Concurrency::accelerator::get_supports_limited_double_precision
- AMPRT/Concurrency::accelerator::get_version
- AMPRT/Concurrency::accelerator::set_default
- AMPRT/Concurrency::accelerator::set_default_cpu_access_type
- AMPRT/Concurrency::accelerator::cpu_accelerator
- AMPRT/Concurrency::accelerator::dedicated_memory
- AMPRT/Concurrency::accelerator::default_accelerator
- AMPRT/Concurrency::accelerator::default_cpu_access_type
- AMPRT/Concurrency::accelerator::default_view
- AMPRT/Concurrency::accelerator::description
- AMPRT/Concurrency::accelerator::device_path
- AMPRT/Concurrency::accelerator::direct3d_ref
- AMPRT/Concurrency::accelerator::direct3d_warp
- AMPRT/Concurrency::accelerator::has_display
- AMPRT/Concurrency::accelerator::is_debug
- AMPRT/Concurrency::accelerator::is_emulated
- AMPRT/Concurrency::accelerator::supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::supports_double_precision
- AMPRT/Concurrency::accelerator::supports_limited_double_precision
- AMPRT/Concurrency::accelerator::version
dev_langs:
- C++
helpviewer_keywords:
- accelerator class
ms.assetid: 37eed593-cf87-4611-9cdc-e98df6c2377a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7748ae0f3993c1df97dcf97308fd6dfbfafdc8b6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375882"
---
# <a name="accelerator-class"></a>accelerator (Clase)

Un acelerador es una capacidad de hardware que está optimizada para computación paralela de datos. Un acelerador puede ser un dispositivo conectado a un bus PCIe (como una GPU), o podría ser una instrucción extendida establecida en la CPU principal.

## <a name="syntax"></a>Sintaxis

```
class accelerator;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[Acelerador de Constructor](#ctor)|Inicializa una nueva instancia de la clase `accelerator`.|
|[~ accelerator (destructor)](#ctor)|Destruye el objeto `accelerator`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CREATE_VIEW](#create_view)|Crea y devuelve un `accelerator_view` objeto en este acelerador.|
|[get_all](#get_all)|Devuelve un vector de `accelerator` objetos que representan todos los aceleradores disponibles.|
|[get_auto_selection_view](#get_auto_selection_view)|Devuelve la selección automática `accelerator_view`.|
|[get_dedicated_memory](#get_dedicated_memory)|Devuelve la memoria dedicada para el `accelerator`, en kilobytes.|
|[get_default_cpu_access_type](#get_default_cpu_access_type)|Devuelve el valor predeterminado [access_type](concurrency-namespace-enums-amp.md#access_type) para los búferes creados en este acelerador.|
|[get_default_view](#get_default_view)|Devuelve el valor predeterminado `accelerator_view` objeto que está asociado el `accelerator`.|
|[get_description](#get_description)|Devuelve una breve descripción de la `accelerator` dispositivo.|
|[get_device_path](#get_device_path)|Devuelve la ruta de acceso del dispositivo.|
|[get_has_display](#get_has_display)|Determina si el `accelerator` se asocia a una pantalla.|
|[get_is_debug](#get_is_debug)|Determina si el `accelerator` tiene la capa DEBUG habilitada para informar sobre errores.|
|[get_is_emulated](#get_is_emulated)|Determina si el `accelerator` se emula.|
|[get_supports_cpu_shared_memory](#get_supports_cpu_shared_memory)|Determina si el `accelerator` admite memoria compartida|
|[get_supports_double_precision](#get_supports_double_precision)|Determina si el `accelerator` se asocia a una pantalla.|
|[get_supports_limited_double_precision](#get_supports_limited_double_precision)|Determina si el `accelerator` tiene compatibilidad matemática de doble precisión limitada.|
|[get_version](#get_version)|Devuelve la versión de la `accelerator`.|
|[set_default](#set_default)|Devuelve la ruta de acceso del Acelerador predeterminado.|
|[set_default_cpu_access_type](#set_default_cpu_access_type)|Establece la CPU predeterminado [access_type](concurrency-namespace-enums-amp.md#access_type)para matrices y asignaciones de memoria implícitas creadas en este `accelerator`.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator!=](#operator_neq)|Compara este `accelerator` objeto con otro y devuelve `false` si son iguales; en caso contrario, devuelve `true`.|
|[operator=](#operator_eq)|Copia el contenido del elemento especificado `accelerator` objeto a ésta.|
|[operator==](#operator_eq_eq)|Compara este `accelerator` objeto con otro y devuelve `true` si son iguales; en caso contrario, devuelve `false`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[cpu_accelerator](#cpu_accelerator)|Obtiene una cadena constante para la CPU `accelerator`.|
|[dedicated_memory](#dedicated_memory)|Obtiene la memoria dedicada para el `accelerator`, en kilobytes.|
|[default_accelerator](#default_accelerator)|Obtiene una cadena constante para el valor predeterminado `accelerator`.|
|[default_cpu_access_type](#default_cpu_access_type)|Obtiene o establece la CPU predeterminado [access_type](concurrency-namespace-enums-amp.md#access_type)para matrices y asignaciones de memoria implícitas creadas en este `accelerator`.|
|[default_view](#default_view)|Obtiene el valor predeterminado `accelerator_view` objeto que está asociado el `accelerator`.|
|[description](#description)|Obtiene una breve descripción de la `accelerator` dispositivo.|
|[device_path](#device_path)|Obtiene la ruta de acceso del dispositivo.|
|[direct3d_ref](#direct3d_ref)|Obtiene una cadena constante para obtener una referencia de Direct3D `accelerator`.|
|[direct3d_warp](#direct3d_warp)|Obtiene la cadena de constante para un `accelerator` de objeto que puede usar para ejecutar el código de C++ AMP en CPUs de varios núcleos que usan las extensiones SIMD de transmisión por secuencias (SSE).|
|[has_display](#has_display)|Obtiene un valor booleano que indica si el `accelerator` se asocia a una pantalla.|
|[is_debug](#is_debug)|Indica si el `accelerator` tiene la capa DEBUG habilitada para informar sobre errores.|
|[is_emulated](#is_emulated)|Indica si el `accelerator` se emula.|
|[supports_cpu_shared_memory](#supports_cpu_shared_memory)|Indica si el `accelerator` admite memoria compartida.|
|[supports_double_precision](#supports_double_precision)|Indica si el Acelerador admite matemática de doble precisión.|
|[supports_limited_double_precision](#supports_limited_double_precision)|Indica si el acelerador tiene compatibilidad matemática de doble precisión limitada.|
|[version](#version)|Obtiene la versión de la `accelerator`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`accelerator`

## <a name="remarks"></a>Comentarios

Un acelerador es una capacidad de hardware que está optimizada para computación paralela de datos. Un acelerador de suele ser una GPU discreta, pero también puede ser una entidad del host virtual como un dispositivo de referencia del DirectX, una WARP (un dispositivo de lado de la CPU que se acelera por medio de instrucciones SSE) o la propia CPU.

Puede construir un `accelerator` objeto enumerando los dispositivos disponibles u obtener el dispositivo de forma predeterminada, el dispositivo de referencia o el dispositivo WARP.

## <a name="requirements"></a>Requisitos

**Encabezado:** amprt.h

**Espacio de nombres:** Concurrency

##  <a name="dtor"></a> </a> ~ accelerator

Destruye el objeto `accelerator`.

```
~accelerator();
```

### <a name="return-value"></a>Valor devuelto

##  <a name="ctor"></a> Acelerador

Inicializa una nueva instancia de la [accelerator (clase)](accelerator-class.md).

```
accelerator();

explicit accelerator(const std::wstring& _Device_path);

accelerator(const accelerator& _Other);
```

### <a name="parameters"></a>Parámetros

*_Device_path*<br/>
La ruta de acceso del dispositivo físico.

*_Otro*<br/>
El acelerador a copiar.

##  <a name="cpu_accelerator"></a> cpu_accelerator

Obtiene una cadena constante para el Acelerador de CPU.

```
static const wchar_t cpu_accelerator[];
```

##  <a name="create_view"></a> CREATE_VIEW

Crea y devuelve un `accelerator_view` objeto en este acelerador, utilizando el modo de puesta en cola especificado. Cuando no se especifica el modo de puesta en cola, el nuevo `accelerator_view` usa el [queuing_mode::immediate](concurrency-namespace-enums-amp.md#queuing_mode) modo de puesta en cola.

```
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>Parámetros

*qmode*<br/>
El modo de puesta en cola.

### <a name="return-value"></a>Valor devuelto

Un nuevo `accelerator_view` objeto en este acelerador, utilizando el modo de puesta en cola especificado.

##  <a name="dedicated_memory"></a> dedicated_memory

Obtiene la memoria dedicada para el `accelerator`, en kilobytes.

```
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;
```

##  <a name="default_accelerator"></a> default_accelerator

Obtiene una cadena constante para el valor predeterminado `accelerator`.

```
static const wchar_t default_accelerator[];
```

##  <a name="default_cpu_access_type"></a> default_cpu_access_type

El valor predeterminado cpu [access_type](concurrency-namespace-enums-amp.md#access_type)para matrices y asignaciones de memoria implícitas creadas en este `accelerator`.

```
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;
```

##  <a name="default_view"></a> default_view

Obtiene la vista de acelerador predeterminado que está asociada el `accelerator`.

```
__declspec(property(get= get_default_view)) accelerator_view default_view;
```

##  <a name="description"></a> Descripción

Obtiene una breve descripción de la `accelerator` dispositivo.

```
__declspec(property(get= get_description)) std::wstring description;
```

##  <a name="device_path"></a> device_path

Obtiene la ruta de acceso del acelerador. La ruta de acceso es único en el sistema.

```
__declspec(property(get= get_device_path)) std::wstring device_path;
```

##  <a name="direct3d_ref"></a> direct3d_ref

Obtiene una cadena constante para un acelerador de la referencia de Direct3D.

```
static const wchar_t direct3d_ref[];
```

##  <a name="direct3d_warp"></a> direct3d_warp

Obtiene la cadena de constante para un `accelerator` de objeto que puede usar para ejecutar el código de C++ AMP en CPUs de varios núcleos con extensiones SIMD de transmisión (SSE).

```
static const wchar_t direct3d_warp[];
```

##  <a name="get_all"></a> get_all

Devuelve un vector de `accelerator` objetos que representan todos los aceleradores disponibles.

```
static inline std::vector<accelerator> get_all();
```

### <a name="return-value"></a>Valor devuelto

El vector de aceleradores disponibles

##  <a name="get_auto_selection_view"></a> get_auto_selection_view

Devuelve el accelerator_view de selección automática, que, cuando especifica como el destino parallel_for_each da lugar al accelerator_view de destino para ejecutar el kernel parallel_for_each seleccionarse automáticamente el tiempo de ejecución. Para los demás casos, el accelerator_view devuelto por este método es el mismo que el accelerator_view predeterminado del Acelerador predeterminado

```
static accelerator_view __cdecl get_auto_selection_view();
```

### <a name="return-value"></a>Valor devuelto

El objeto accelerator_view de selección automática.

##  <a name="get_dedicated_memory"></a> get_dedicated_memory

Devuelve la memoria dedicada para el `accelerator`, en kilobytes.

```
size_t get_dedicated_memory() const;

```

### <a name="return-value"></a>Valor devuelto

La memoria dedicada para el `accelerator`, en kilobytes.

##  <a name="get_default_cpu_access_type"></a> get_default_cpu_access_type

Obtiene el access_type de cpu predeterminado para los búferes creados en este acelerador

```
access_type get_default_cpu_access_type() const;

```

### <a name="return-value"></a>Valor devuelto

El access_type de cpu predeterminado para los búferes creados en este acelerador.

##  <a name="get_default_view"></a> get_default_view

Devuelve el valor predeterminado `accelerator_view` objeto que está asociado el `accelerator`.

```
accelerator_view get_default_view() const;

```

### <a name="return-value"></a>Valor devuelto

El valor predeterminado `accelerator_view` objeto que está asociado el `accelerator`.

##  <a name="get_description"></a> get_description

Devuelve una breve descripción de la `accelerator` dispositivo.

```
std::wstring get_description() const;

```

### <a name="return-value"></a>Valor devuelto

Una breve descripción de la `accelerator` dispositivo.

##  <a name="get_device_path"></a> get_device_path

Devuelve la ruta de acceso del acelerador. La ruta de acceso es único en el sistema.

```
std::wstring get_device_path() const;

```

### <a name="return-value"></a>Valor devuelto

La ruta de acceso de la instancia de dispositivo único para todo el sistema.

##  <a name="get_has_display"></a> get_has_display

Devuelve un valor booleano que indica si el `accelerator` puede generar una pantalla.

```
bool get_has_display() const;

```

### <a name="return-value"></a>Valor devuelto

`true` Si el `accelerator` puede generar una pantalla; de lo contrario, `false`.

##  <a name="get_is_debug"></a> get_is_debug

Determina si el `accelerator` tiene la capa DEBUG habilitada para informar sobre errores.

```
bool get_is_debug() const;

```

### <a name="return-value"></a>Valor devuelto

`true` Si el `accelerator` tiene la capa DEBUG habilitada para informar sobre errores. En caso contrario, es `false`.

##  <a name="get_is_emulated"></a> get_is_emulated

Determina si el `accelerator` se emula.

```
bool get_is_emulated() const;

```

### <a name="return-value"></a>Valor devuelto

`true` Si el `accelerator` se emula. En caso contrario, es `false`.

##  <a name="get_supports_cpu_shared_memory"></a> get_supports_cpu_shared_memory

Devuelve un valor booleano que indica si el Acelerador admite memoria accesible tanto el acelerador como la CPU.

```
bool get_supports_cpu_shared_memory() const;

```

### <a name="return-value"></a>Valor devuelto

`true` Si el Acelerador admite memoria compartida de CPU; en caso contrario, `false`.

##  <a name="get_supports_double_precision"></a> get_supports_double_precision

Devuelve un valor booleano que indica si el Acelerador admite matemática de precisión doble, incluyendo fusionan multiplicar agrega (FMA), división, recíproca y conversión entre `int` y `double`.

```
bool get_supports_double_precision() const;

```

### <a name="return-value"></a>Valor devuelto

`true` Si el Acelerador admite matemática de precisión doble; en caso contrario, `false`.

##  <a name="get_supports_limited_double_precision"></a> get_supports_limited_double_precision

Devuelve un valor booleano que indica si el acelerador tiene compatibilidad matemática de precisión doble limitada. Si el acelerador tiene solamente una compatibilidad limitada, a continuación, se fusionan multiply agregar (FMA), división, recíproca y conversión entre `int` y `double` no se admiten.

```
bool get_supports_limited_double_precision() const;

```

### <a name="return-value"></a>Valor devuelto

`true` Si el acelerador tiene compatibilidad matemática de precisión doble; limitada en caso contrario, `false`.

##  <a name="get_version"></a> get_version

Devuelve la versión de la `accelerator`.

```
unsigned int get_version() const;

```

### <a name="return-value"></a>Valor devuelto

La versión de la `accelerator`.

##  <a name="has_display"></a> has_display

Obtiene un valor booleano que indica si el `accelerator` puede generar una pantalla.

```
__declspec(property(get= get_has_display)) bool has_display;
```

##  <a name="is_debug"></a> is_debug

Obtiene un valor booleano que indica si el `accelerator` tiene la capa DEBUG habilitada para informar sobre errores.

```
__declspec(property(get= get_is_debug)) bool is_debug;
```

##  <a name="is_emulated"></a> is_emulated

Obtiene un valor booleano que indica si el `accelerator` se emula.

```
__declspec(property(get= get_is_emulated)) bool is_emulated;
```

##  <a name="operator_neq"></a> operador! =

Compara este `accelerator` objeto con otro y devuelve `false` si son iguales; en caso contrario, devuelve `true`.

```
bool operator!= (const accelerator& _Other) const;

```

### <a name="parameters"></a>Parámetros

*_Otro*<br/>
La `accelerator` objeto que se va a comparar con éste.

### <a name="return-value"></a>Valor devuelto

`false` Si los dos `accelerator` objetos son iguales; en caso contrario, `true`.

##  <a name="operator_eq"></a> operator=

Copia el contenido del elemento especificado `accelerator` objeto a ésta.

```
accelerator& operator= (const accelerator& _Other);
```

### <a name="parameters"></a>Parámetros

*_Otro*<br/>
La `accelerator` objeto que se va a copiar desde.

### <a name="return-value"></a>Valor devuelto

Una referencia a este `accelerator` objeto.

##  <a name="operator_eq_eq"></a> operador ==

Compara este `accelerator` objeto con otro y devuelve `true` si son iguales; en caso contrario, devuelve `false`.

```
bool operator== (const accelerator& _Other) const;

```

### <a name="parameters"></a>Parámetros

*_Otro*<br/>
La `accelerator` objeto que se va a comparar con éste.

### <a name="return-value"></a>Valor devuelto

`true` Si el otro `accelerator` es igual que este objeto `accelerator` objeto; en caso contrario, `false`.

##  <a name="set_default"></a> set_default

Establece el Acelerador predeterminado que se usará para cualquier operación que utiliza implícitamente el Acelerador predeterminado. Este método solo se realiza correctamente si el Acelerador predeterminado seleccionado en tiempo de ejecución ya no se han usado en una operación que utiliza implícitamente el Acelerador predeterminado

```
static inline bool set_default(std::wstring _Path);
```

### <a name="parameters"></a>Parámetros

*_Ruta de acceso*<br/>
La ruta de acceso para el acelerador.

### <a name="return-value"></a>Valor devuelto

`true` Si la llamada establece correctamente el Acelerador predeterminado. En caso contrario, es `false`.

##  <a name="set_default_cpu_access_type"></a> set_default_cpu_access_type

Establezca el access_type de cpu predeterminado para las matrices creadas en este acelerador o para las asignaciones de memoria implícitas como parte de array_views al tener acceso en este acelerador. Este método solo se realiza correctamente si default_cpu_access_type para el Acelerador no ya ha sido reemplazada por una llamada anterior a este método y el default_cpu_access_type seleccionado en tiempo de ejecución para este acelerador aún no ha usado para asignar una matriz o para una asignación de memoria implícitas de seguridad de un array_view al tener acceso en este acelerador.

```
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```

### <a name="parameters"></a>Parámetros

*_Default_cpu_access_type*<br/>
El access_type de cpu predeterminado que se usará para las asignaciones de memoria de array/array_view en este acelerador.

### <a name="return-value"></a>Valor devuelto

Un valor booleano que indica si el access_type de cpu predeterminado para el Acelerador se estableció correctamente.

##  <a name="supports_cpu_shared_memory"></a> supports_cpu_shared_memory

Obtiene un valor booleano que indica si el `accelerator` admite memoria compartida.

```
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;
```

##  <a name="supports_double_precision"></a> supports_double_precision

Obtiene un valor booleano que indica si el Acelerador admite matemática de precisión doble.

```
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;
```

##  <a name="supports_limited_double_precision"></a> supports_limited_double_precision

Obtiene un valor booleano que indica si el acelerador tiene compatibilidad matemática de precisión doble limitada. Si el acelerador tiene solamente una compatibilidad limitada, a continuación, se fusionan multiply agregar (FMA), división, recíproca y conversión entre `int` y `double` no se admiten.

```
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;
```

##  <a name="version"></a> Versión

Obtiene la versión de la `accelerator`.

```
__declspec(property(get= get_version)) unsigned int version;
```

##  <a name="dtor"></a> </a> ~ accelerator_view

Destruye el [accelerator_view](accelerator-view-class.md) objeto.

```
~accelerator_view();
```

### <a name="return-value"></a>Valor devuelto

##  <a name="accelerator"></a> Acelerador

Obtiene el `accelerator` de objeto para el [accelerator_view](accelerator-view-class.md) objeto.

```
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

##  <a name="ctor"></a> accelerator_view

Inicializa una nueva instancia de la [accelerator_view](accelerator-view-class.md) clase copiando existente `accelerator_view` objeto.

```
accelerator_view(const accelerator_view& _Other);
```

### <a name="parameters"></a>Parámetros

*_Otro*<br/>
La `accelerator_view` objeto que se va a copiar.

##  <a name="create_marker"></a> create_marker

Devuelve un valor futuro para realizar un seguimiento de la finalización de todos los comandos presentados hasta ahora a este `accelerator_view` objeto.

```
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>Valor devuelto

Un futuro para realizar el seguimiento de la finalización de todos los comandos presentados hasta ahora a este `accelerator_view` objeto.

##  <a name="flush"></a> Vaciar

Envía todos los comandos pendientes en cola para el [accelerator_view](accelerator-view-class.md) objeto para el Acelerador para su ejecución.

```
void flush();
```

### <a name="return-value"></a>Valor devuelto

Devuelve `void`.

##  <a name="get_accelerator"></a> get_accelerator

Devuelve el `accelerator` de objeto para el [accelerator_view](accelerator-view-class.md) objeto.

```
accelerator get_accelerator() const;

```

### <a name="return-value"></a>Valor devuelto

El `accelerator` de objeto para el `accelerator_view` objeto.

##  <a name="get_is_auto_selection"></a> get_is_auto_selection

Devuelve un valor booleano que indica si el runtime seleccionará automáticamente un acelerador adecuado cuando accelerator_view se pase a un [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each).

```
bool get_is_auto_selection() const;

```

### <a name="return-value"></a>Valor devuelto

`true` Si el runtime seleccionará automáticamente un acelerador adecuado; en caso contrario, `false`.

##  <a name="get_is_debug"></a> get_is_debug

Devuelve un valor booleano que indica si el [accelerator_view](accelerator-view-class.md) objeto tiene el nivel DEBUG habilitado para informar sobre errores.

```
bool get_is_debug() const;

```

### <a name="return-value"></a>Valor devuelto

Un valor booleano que indica si el `accelerator_view` objeto tiene el nivel DEBUG habilitado para informar sobre errores.

##  <a name="get_queuing_mode"></a> get_queuing_mode

Devuelve el modo de puesta en cola para el [accelerator_view](accelerator-view-class.md) objeto.

```
queuing_mode get_queuing_mode() const;

```

### <a name="return-value"></a>Valor devuelto

El modo de puesta en cola para el `accelerator_view` objeto.

##  <a name="get_version"></a> get_version

Devuelve la versión de la [accelerator_view](accelerator-view-class.md).

```
unsigned int get_version() const;

```

### <a name="return-value"></a>Valor devuelto

La versión de la `accelerator_view`.

##  <a name="is_auto_selection"></a> is_auto_selection

Obtiene un valor booleano que indica si el runtime seleccionará automáticamente un acelerador adecuado cuando accelerator_view se pase a un [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each).

```
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

##  <a name="is_debug"></a> is_debug

Obtiene un valor booleano que indica si el [accelerator_view](accelerator-view-class.md) objeto tiene el nivel DEBUG habilitado para informar sobre errores.

```
__declspec(property(get= get_is_debug)) bool is_debug;
```

##  <a name="operator_neq"></a> operador! =

Compara este [accelerator_view](accelerator-view-class.md) objeto con otro y devuelve `false` si son iguales; en caso contrario, devuelve `true`.

```
bool operator!= (const accelerator_view& _Other) const;

```

### <a name="parameters"></a>Parámetros

*_Otro*<br/>
La `accelerator_view` objeto que se va a comparar con éste.

### <a name="return-value"></a>Valor devuelto

`false` si los dos objetos son iguales; de lo contrario, `true`.

##  <a name="operator_eq"></a> operator=

Copia el contenido del elemento especificado [accelerator_view](accelerator-view-class.md) objeto en este.

```
accelerator_view& operator= (const accelerator_view& _Other);
```

### <a name="parameters"></a>Parámetros

*_Otro*<br/>
La `accelerator_view` objeto que se va a copiar desde.

### <a name="return-value"></a>Valor devuelto

Una referencia a la modificación `accelerator_view` objeto.

##  <a name="operator_eq_eq"></a> operador ==

Compara este [accelerator_view](accelerator-view-class.md) objeto con otro y devuelve `true` si son iguales; en caso contrario, devuelve `false`.

```
bool operator== (const accelerator_view& _Other) const;

```

### <a name="parameters"></a>Parámetros

*_Otro*<br/>
La `accelerator_view` objeto que se va a comparar con éste.

### <a name="return-value"></a>Valor devuelto

`true` si los dos objetos son iguales; de lo contrario, `false`.

##  <a name="queuing_mode"></a> queuing_mode

Obtiene el modo de puesta en cola el [accelerator_view](accelerator-view-class.md) objeto.

```
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

##  <a name="version"></a> Versión

Obtiene la versión de la [accelerator_view](accelerator-view-class.md).

```
__declspec(property(get= get_version)) unsigned int version;
```

##  <a name="wait"></a> Espere

Espera a que todos los comandos enviados a la [accelerator_view](accelerator-view-class.md) objeto que se va a finalizar.

```
void wait();
```

### <a name="return-value"></a>Valor devuelto

Devuelve `void`.

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
