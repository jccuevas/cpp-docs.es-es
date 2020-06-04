---
title: accelerator (Clase)
ms.date: 11/04/2016
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
helpviewer_keywords:
- accelerator class
ms.assetid: 37eed593-cf87-4611-9cdc-e98df6c2377a
ms.openlocfilehash: 72a570ab28696730f835c42748a6ea12b865ca55
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427486"
---
# <a name="accelerator-class"></a>accelerator (Clase)

Un acelerador es una capacidad de hardware que está optimizada para la informática en paralelo de datos. Un acelerador puede ser un dispositivo conectado a un bus PCIe (como una GPU) o puede ser un conjunto de instrucciones extendidas en la CPU principal.

## <a name="syntax"></a>Sintaxis

```cpp
class accelerator;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor de acelerador](#ctor)|Inicializa una nueva instancia de la clase `accelerator`.|
|[~ (destructor de acelerador)](#ctor)|Destruye el objeto `accelerator`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[create_view](#create_view)|Crea y devuelve un objeto `accelerator_view` en este acelerador.|
|[get_all](#get_all)|Devuelve un vector de `accelerator` objetos que representan todos los aceleradores disponibles.|
|[get_auto_selection_view](#get_auto_selection_view)|Devuelve la `accelerator_view`de selección automática.|
|[get_dedicated_memory](#get_dedicated_memory)|Devuelve la memoria dedicada para el `accelerator`, en kilobytes.|
|[get_default_cpu_access_type](#get_default_cpu_access_type)|Devuelve el [access_type](concurrency-namespace-enums-amp.md#access_type) predeterminado para los búferes creados en este acelerador.|
|[get_default_view](#get_default_view)|Devuelve el objeto `accelerator_view` predeterminado que está asociado al `accelerator`.|
|[get_description](#get_description)|Devuelve una descripción breve del dispositivo `accelerator`.|
|[get_device_path](#get_device_path)|Devuelve la ruta de acceso del dispositivo.|
|[get_has_display](#get_has_display)|Determina si el `accelerator` se adjunta a una pantalla.|
|[get_is_debug](#get_is_debug)|Determina si el `accelerator` tiene habilitada la capa de depuración para informes de errores extensos.|
|[get_is_emulated](#get_is_emulated)|Determina si la `accelerator` está emulada.|
|[get_supports_cpu_shared_memory](#get_supports_cpu_shared_memory)|Determina si la `accelerator` admite la memoria compartida.|
|[get_supports_double_precision](#get_supports_double_precision)|Determina si el `accelerator` se adjunta a una pantalla.|
|[get_supports_limited_double_precision](#get_supports_limited_double_precision)|Determina si el `accelerator` tiene compatibilidad limitada con las matemáticas de precisión doble.|
|[get_version](#get_version)|Devuelve la versión de `accelerator`.|
|[set_default](#set_default)|Devuelve la ruta de acceso del acelerador predeterminado.|
|[set_default_cpu_access_type](#set_default_cpu_access_type)|Establece el [access_type](concurrency-namespace-enums-amp.md#access_type)de CPU predeterminado para matrices y asignaciones de memoria implícitas realizadas en esta `accelerator`.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator!=](#operator_neq)|Compara este objeto `accelerator` con otro y devuelve **false** si son iguales; de lo contrario, devuelve **true**.|
|[operator=](#operator_eq)|Copia el contenido del objeto `accelerator` especificado en este.|
|[operator==](#operator_eq_eq)|Compara este objeto `accelerator` con otro y devuelve **true** si son iguales; de lo contrario, devuelve **false**.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[cpu_accelerator](#cpu_accelerator)|Obtiene una constante de cadena para el `accelerator`de la CPU.|
|[dedicated_memory](#dedicated_memory)|Obtiene la memoria dedicada para el `accelerator`, en kilobytes.|
|[default_accelerator](#default_accelerator)|Obtiene una constante de cadena para el `accelerator`predeterminado.|
|[default_cpu_access_type](#default_cpu_access_type)|Obtiene o establece la [access_type](concurrency-namespace-enums-amp.md#access_type)de CPU predeterminada para las matrices y asignaciones de memoria implícitas realizadas en esta `accelerator`.|
|[default_view](#default_view)|Obtiene el objeto `accelerator_view` predeterminado que está asociado al `accelerator`.|
|[description](#description)|Obtiene una breve descripción del dispositivo `accelerator`.|
|[device_path](#device_path)|Obtiene la ruta de acceso del dispositivo.|
|[direct3d_ref](#direct3d_ref)|Obtiene una constante de cadena para una `accelerator`de referencia de Direct3D.|
|[direct3d_warp](#direct3d_warp)|Obtiene la constante de cadena para un objeto `accelerator` que puede usar para ejecutar código C++ de amp en CPU de varios núcleos que usan extensiones SIMD de streaming (SSE).|
|[has_display](#has_display)|Obtiene un valor booleano que indica si el `accelerator` está asociado a una pantalla.|
|[is_debug](#is_debug)|Indica si el `accelerator` tiene habilitada la capa de depuración para informes de errores extensos.|
|[is_emulated](#is_emulated)|Indica si la `accelerator` está emulada.|
|[supports_cpu_shared_memory](#supports_cpu_shared_memory)|Indica si la `accelerator` admite la memoria compartida.|
|[supports_double_precision](#supports_double_precision)|Indica si el acelerador admite matemáticas de precisión doble.|
|[supports_limited_double_precision](#supports_limited_double_precision)|Indica si el acelerador tiene compatibilidad limitada con las matemáticas de precisión doble.|
|[version](#version)|Obtiene la versión de `accelerator`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`accelerator`

## <a name="remarks"></a>Observaciones

Un acelerador es una capacidad de hardware que está optimizada para la informática en paralelo de datos. Un acelerador suele ser una GPU discreta, pero también puede ser una entidad del host virtual como un dispositivo de referencia de DirectX, una deformación (un dispositivo de la CPU que se acelera mediante instrucciones de SSE) o la propia CPU.

Puede construir un objeto de `accelerator` enumerando los dispositivos disponibles, o bien obteniendo el dispositivo predeterminado, el dispositivo de referencia o el dispositivo de ALABEo.

## <a name="requirements"></a>Requisitos

**Encabezado:** amprt. h

**Espacio de nombres:** Concurrency

## <a name="dtor"></a>Acelerador de </a> ~

Destruye el objeto `accelerator`.

```cpp
~accelerator();
```

### <a name="return-value"></a>Valor devuelto

## <a name="ctor"></a>métodos

Inicializa una nueva instancia de la [clase Accelerator](accelerator-class.md).

```cpp
accelerator();

explicit accelerator(const std::wstring& _Device_path);

accelerator(const accelerator& _Other);
```

### <a name="parameters"></a>Parámetros

*_Device_path*<br/>
Ruta de acceso del dispositivo físico.

*_Other*<br/>
Acelerador que se va a copiar.

## <a name="cpu_accelerator"></a>cpu_accelerator

Obtiene una constante de cadena para el acelerador de CPU.

```cpp
static const wchar_t cpu_accelerator[];
```

## <a name="create_view"></a>create_view

Crea y devuelve un objeto `accelerator_view` en este acelerador usando el modo de cola especificado. Cuando no se especifica el modo de puesta en cola, el nuevo `accelerator_view` utiliza el modo de puesta en cola [queuing_mode:: inmediato](concurrency-namespace-enums-amp.md#queuing_mode) .

```cpp
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>Parámetros

*qmode*<br/>
Modo de puesta en cola.

### <a name="return-value"></a>Valor devuelto

Nuevo objeto `accelerator_view` en este acelerador, mediante el modo de puesta en cola especificado.

## <a name="dedicated_memory"></a>dedicated_memory

Obtiene la memoria dedicada para el `accelerator`, en kilobytes.

```cpp
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;
```

## <a name="default_accelerator"></a>default_accelerator

Obtiene una constante de cadena para el `accelerator`predeterminado.

```cpp
static const wchar_t default_accelerator[];
```

## <a name="default_cpu_access_type"></a>default_cpu_access_type

La [access_type](concurrency-namespace-enums-amp.md#access_type)de CPU predeterminada para matrices y asignaciones de memoria implícitas realizadas en esta `accelerator`.

```cpp
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;
```

## <a name="default_view"></a>default_view

Obtiene la vista de acelerador predeterminada que está asociada a la `accelerator`.

```cpp
__declspec(property(get= get_default_view)) accelerator_view default_view;
```

## <a name="description"></a>denominación

Obtiene una breve descripción del dispositivo `accelerator`.

```cpp
__declspec(property(get= get_description)) std::wstring description;
```

## <a name="device_path"></a>device_path

Obtiene la ruta de acceso del acelerador. La ruta de acceso es única en el sistema.

```cpp
__declspec(property(get= get_device_path)) std::wstring device_path;
```

## <a name="direct3d_ref"></a>direct3d_ref

Obtiene una constante de cadena para un acelerador de referencia de Direct3D.

```cpp
static const wchar_t direct3d_ref[];
```

## <a name="direct3d_warp"></a>direct3d_warp

Obtiene la constante de cadena para un objeto `accelerator` que puede usar para ejecutar el C++ código de amp en CPU de varios núcleos mediante extensiones SIMD de streaming (SSE).

```cpp
static const wchar_t direct3d_warp[];
```

## <a name="get_all"></a>get_all

Devuelve un vector de `accelerator` objetos que representan todos los aceleradores disponibles.

```cpp
static inline std::vector<accelerator> get_all();
```

### <a name="return-value"></a>Valor devuelto

Vector de los aceleradores disponibles

## <a name="get_auto_selection_view"></a>get_auto_selection_view

Devuelve la accelerator_view de selección automática, que cuando se especifica como el parallel_for_each destino produce el accelerator_view de destino para ejecutar el kernel parallel_for_each para que el motor en tiempo de ejecución lo seleccione automáticamente. Para el resto de propósitos, el accelerator_view devuelto por este método es el mismo que el accelerator_view predeterminado del acelerador predeterminado.

```cpp
static accelerator_view __cdecl get_auto_selection_view();
```

### <a name="return-value"></a>Valor devuelto

Accelerator_view de selección automática.

## <a name="get_dedicated_memory"></a>get_dedicated_memory

Devuelve la memoria dedicada para el `accelerator`, en kilobytes.

```cpp
size_t get_dedicated_memory() const;
```

### <a name="return-value"></a>Valor devuelto

Memoria dedicada para el `accelerator`, en kilobytes.

## <a name="get_default_cpu_access_type"></a>get_default_cpu_access_type

Obtiene el access_type de CPU predeterminado para los búferes creados en este acelerador.

```cpp
access_type get_default_cpu_access_type() const;
```

### <a name="return-value"></a>Valor devuelto

La access_type de CPU predeterminada para los búferes creados en este acelerador.

## <a name="get_default_view"></a>get_default_view

Devuelve el objeto `accelerator_view` predeterminado que está asociado al `accelerator`.

```cpp
accelerator_view get_default_view() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto `accelerator_view` predeterminado que está asociado al `accelerator`.

## <a name="get_description"></a>get_description

Devuelve una descripción breve del dispositivo `accelerator`.

```cpp
std::wstring get_description() const;
```

### <a name="return-value"></a>Valor devuelto

Breve descripción del dispositivo `accelerator`.

## <a name="get_device_path"></a>get_device_path

Devuelve la ruta de acceso del acelerador. La ruta de acceso es única en el sistema.

```cpp
std::wstring get_device_path() const;
```

### <a name="return-value"></a>Valor devuelto

La ruta de acceso de la instancia del dispositivo único en todo el sistema.

## <a name="get_has_display"></a>get_has_display

Devuelve un valor booleano que indica si el `accelerator` puede generar una presentación.

```cpp
bool get_has_display() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si el `accelerator` puede generar una presentación; en caso contrario, **false**.

## <a name="get_is_debug"></a>get_is_debug

Determina si el `accelerator` tiene habilitada la capa de depuración para informes de errores extensos.

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si el `accelerator` tiene habilitada la capa de depuración para informes de errores extensos. De lo contrario, se devuelve el valor **False**.

## <a name="get_is_emulated"></a>get_is_emulated

Determina si la `accelerator` está emulada.

```cpp
bool get_is_emulated() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si se emula el `accelerator`. De lo contrario, se devuelve el valor **False**.

## <a name="get_supports_cpu_shared_memory"></a>get_supports_cpu_shared_memory

Devuelve un valor booleano que indica si el acelerador admite la memoria a la que puede tener acceso el acelerador y la CPU.

```cpp
bool get_supports_cpu_shared_memory() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si el acelerador admite memoria compartida de CPU; en caso contrario, **false**.

## <a name="get_supports_double_precision"></a>get_supports_double_precision

Devuelve un valor booleano que indica si el acelerador admite cálculos matemáticos de precisión doble, incluidos los métodos de multiplicación fusionada (FMA), división, recíproco y conversión entre **int** y **Double** .

```cpp
bool get_supports_double_precision() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si el acelerador admite matemáticas de precisión doble; en caso contrario, **false**.

## <a name="get_supports_limited_double_precision"></a>get_supports_limited_double_precision

Devuelve un valor booleano que indica si el acelerador tiene compatibilidad limitada con las matemáticas de precisión doble. Si el acelerador solo tiene compatibilidad limitada, no se admiten los métodos de multiplicación de suma (FMA) combinados, división, recíproco y conversión entre **int** y **Double** .

```cpp
bool get_supports_limited_double_precision() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si el acelerador tiene compatibilidad limitada con las matemáticas de precisión doble; en caso contrario, **false**.

## <a name="get_version"></a>get_version

Devuelve la versión de `accelerator`.

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>Valor devuelto

La versión de `accelerator`.

## <a name="has_display"></a>has_display

Obtiene un valor booleano que indica si el `accelerator` puede generar una presentación.

```cpp
__declspec(property(get= get_has_display)) bool has_display;
```

## <a name="is_debug"></a>is_debug

Obtiene un valor booleano que indica si el `accelerator` tiene habilitada la capa de depuración para informes de errores extensos.

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="is_emulated"></a>is_emulated

Obtiene un valor booleano que indica si la `accelerator` está emulada.

```cpp
__declspec(property(get= get_is_emulated)) bool is_emulated;
```

## <a name="operator_neq"></a>operador! =

Compara este objeto `accelerator` con otro y devuelve **false** si son iguales; de lo contrario, devuelve **true**.

```cpp
bool operator!= (const accelerator& _Other) const;
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
Objeto `accelerator` que se va a comparar con este.

### <a name="return-value"></a>Valor devuelto

**false** si los dos objetos `accelerator` son iguales; en caso contrario, **true**.

## <a name="operator_eq"></a>operador =

Copia el contenido del objeto `accelerator` especificado en este.

```cpp
accelerator& operator= (const accelerator& _Other);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
Objeto de `accelerator` del que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Referencia a este objeto `accelerator`.

## <a name="operator_eq_eq"></a>operador = =

Compara este objeto `accelerator` con otro y devuelve **true** si son iguales; de lo contrario, devuelve **false**.

```cpp
bool operator== (const accelerator& _Other) const;
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
Objeto `accelerator` que se va a comparar con este.

### <a name="return-value"></a>Valor devuelto

**true** si el otro objeto `accelerator` es igual que este objeto `accelerator`; en caso contrario, **false**.

## <a name="set_default"></a>set_default

Establece el acelerador predeterminado que se usará para cualquier operación que use implícitamente el acelerador predeterminado. Este método solo se realiza correctamente si el acelerador predeterminado seleccionado en tiempo de ejecución aún no se ha usado en una operación que utiliza implícitamente el acelerador predeterminado.

```cpp
static inline bool set_default(std::wstring _Path);
```

### <a name="parameters"></a>Parámetros

*_Path*<br/>
La ruta de acceso al acelerador.

### <a name="return-value"></a>Valor devuelto

**true** si la llamada se realiza correctamente al establecer el acelerador predeterminado. De lo contrario, se devuelve el valor **False**.

## <a name="set_default_cpu_access_type"></a>set_default_cpu_access_type

Establezca la access_type de CPU predeterminada para las matrices creadas en este acelerador o para las asignaciones de memoria implícitas como parte de array_views a la que se tiene acceso en este acelerador. Este método solo se realiza correctamente si el default_cpu_access_type del acelerador aún no se ha reemplazado por una llamada anterior a este método y el tiempo de ejecución seleccionado default_cpu_access_type para este acelerador todavía no se ha usado para asignar una matriz o para asignación de memoria implícita que respalda una array_view a la que se tiene acceso en este acelerador.

```cpp
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```

### <a name="parameters"></a>Parámetros

*_Default_cpu_access_type*<br/>
La access_type de CPU predeterminada que se usará para las asignaciones de memoria de matriz/array_view en este acelerador.

### <a name="return-value"></a>Valor devuelto

Un valor booleano que indica si se estableció correctamente el access_type de la CPU predeterminada para el acelerador.

## <a name="supports_cpu_shared_memory"></a>supports_cpu_shared_memory

Obtiene un valor booleano que indica si la `accelerator` admite la memoria compartida.

```cpp
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;
```

## <a name="supports_double_precision"></a>supports_double_precision

Obtiene un valor booleano que indica si el acelerador admite matemáticas de precisión doble.

```cpp
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;
```

## <a name="supports_limited_double_precision"></a>supports_limited_double_precision

Obtiene un valor booleano que indica si el acelerador tiene compatibilidad limitada con las matemáticas de precisión doble. Si el acelerador solo tiene compatibilidad limitada, no se admiten los métodos de multiplicación de suma (FMA) combinados, división, recíproco y conversión entre `int` y `double`.

```cpp
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;
```

## <a name="version"></a>Versión

Obtiene la versión de `accelerator`.

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
