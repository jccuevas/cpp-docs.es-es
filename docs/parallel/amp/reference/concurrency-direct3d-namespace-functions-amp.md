---
title: Concurrency::direct3d (Funciones del espacio de nombres) (AMP)
ms.date: 08/31/2018
f1_keywords:
- amp/Concurrency::direct3d::abs
- amp/Concurrency::direct3d::countbits
- amp/Concurrency::direct3d::create_accelerator_view
- amp/Concurrency::direct3d::d3d_access_lock
- amp/Concurrency::direct3d::d3d_access_unlock
- amp/Concurrency::direct3d::firstbithigh
- amp/Concurrency::direct3d::get_buffer
- amp/Concurrency::direct3d::get_device
- amp/Concurrency::direct3d::imax
- amp/Concurrency::direct3d::is_timeout_disabled
- amp/Concurrency::direct3d::mad
- amp/Concurrency::direct3d::noise
- amp/Concurrency::direct3d::radians
- amp/Concurrency::direct3d::reversebits
- amp/Concurrency::direct3d::saturate
- amp/Concurrency::direct3d::smoothstep
- amp/Concurrency::direct3d::step
- amp/Concurrency::direct3d::umin
ms.assetid: 28943b62-52c9-42dc-baf1-ca7b095c1a19
ms.openlocfilehash: e21b1f2869ab81973b341abc5371714fbf8580e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375926"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Concurrency::direct3d (Funciones del espacio de nombres) (AMP)

||||
|-|-|-|
|[Abs](#abs)|[Abrazadera](#clamp)|[countbits](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|[d3d_access_lock](#d3d_access_lock)||
|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|[firstbithigh](#firstbithigh)|
|[firstbitlow](#firstbitlow)|[get_buffer](#get_buffer)|[get_device](#get_device)|
|[Imax](#imax)|[Imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|
|[Enojado](#mad)|[make_array](#make_array)|[Ruido](#noise)|
|[Radianes](#radians)|[rcp](#rcp)|[reversebits](#reversebits)|
|[Saturar](#saturate)|[sign](#sign)|[smoothstep](#smoothstep)|
|[Paso](#step)|[Umax](#umax)|[umin](#umin)|

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h **Espacio de nombres:** Simultaneidad

## <a name="abs"></a><a name="abs"></a>Abs

Devuelve el valor absoluto del argumento

```cpp
inline int abs(int _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

Devuelve el valor absoluto del argumento.

## <a name="clamp"></a><a name="clamp"></a>Abrazadera

Calcula el valor del primer argumento especificado sujeto a un intervalo definido por el segundo y tercer argumento especificado.

```cpp
inline float clamp(
    float _X,
    float _Min,
    float _Max) restrict(amp);

inline int clamp(
    int _X,
    int _Min,
    int _Max) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
El valor a sujetar

*_Min*<br/>
El límite inferior del rango de sujeción.

*_Max*<br/>
El límite superior del rango de sujeción.

### <a name="return-value"></a>Valor devuelto

El valor de `_X`sujeción de .

## <a name="countbits"></a><a name="countbits"></a>countbits

Cuenta el número de bits establecidos en _X

```cpp
inline unsigned int countbits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero sin signo

### <a name="return-value"></a>Valor devuelto

Devuelve el número de bits establecidos en _X

## <a name="create_accelerator_view"></a><a name="create_accelerator_view"></a>create_accelerator_view

Crea un [objeto accelerator_view](accelerator-view-class.md) a partir de un puntero a una interfaz de dispositivo Direct3D.

## <a name="syntax"></a>Sintaxis

```cpp
accelerator_view create_accelerator_view(
    IUnknown * _D3D_device
    queuing_mode _Qmode = queuing_mode_automatic);

accelerator_view create_accelerator_view(
    accelerator& _Accelerator,
    bool _Disable_timeout
    queuing_mode _Qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>Parámetros

*_Accelerator*<br/>
El acelerador en el que se va a crear el nuevo accelerator_view.

*_D3D_device*<br/>
El puntero a la interfaz del dispositivo Direct3D.

*_Disable_timeout*<br/>
Un parámetro booleano que especifica si se debe deshabilitar el tiempo de espera para el accelerator_view recién creado. Esto corresponde a la marca D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT para la creación de dispositivos Direct3D y se utiliza para indicar si el sistema operativo debe permitir que se ejecuten cargas de trabajo que tardan más de 2 segundos sin restablecer el dispositivo según el mecanismo de detección y recuperación de tiempo de espera de Windows. Se recomienda el uso de esta marca si necesita realizar tareas que consumen mucho tiempo en el accelerator_view.

*_Qmode*<br/>
El [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) que se utilizará para el accelerator_view recién creado. Este parámetro tiene un `queuing_mode_automatic`valor predeterminado de .

## <a name="return-value"></a>Valor devuelto

Objeto `accelerator_view` creado a partir de la interfaz de dispositivo Direct3D pasada.

## <a name="remarks"></a>Observaciones

Esta función `accelerator_view` crea un nuevo objeto a partir de un puntero existente a una interfaz de dispositivo Direct3D. Si la llamada de función se realiza correctamente, el `AddRef` recuento de referencias del parámetro se incrementa mediante una llamada a la interfaz. Puede liberar el objeto de forma segura cuando ya no sea necesario en el código DirectX. Si se produce un error en la llamada al método, se produce un [runtime_exception.](runtime-exception-class.md)

El `accelerator_view` objeto que se crea mediante esta función es seguro para subprocesos. Debe sincronizar el uso `accelerator_view` simultáneo del objeto. El uso simultáneo no `accelerator_view` sincronizado del objeto y la interfaz ID3D11Device sin formato provoca un comportamiento indefinido.

El tiempo de ejecución de C++ AMP proporciona información de error detallada `D3D11_CREATE_DEVICE_DEBUG` en modo de depuración mediante la capa D3D Debug si utiliza la marca.

## <a name="d3d_access_lock"></a><a name="d3d_access_lock"></a>d3d_access_lock

Adquiera un bloqueo en un accelerator_view con el fin de realizar de forma segura operaciones D3D en recursos compartidos con el accelerator_view. El accelerator_view y todos los recursos de C++ AMP asociados a este accelerator_view toman internamente este bloqueo al realizar operaciones y se bloquearán mientras otro subproceso contiene el bloqueo de acceso D3D. Este bloqueo no es recursivo: es un comportamiento indefinido llamar a esta función desde un subproceso que ya contiene el bloqueo. Es un comportamiento indefinido realizar operaciones en el accelerator_view o cualquier contenedor de datos asociado con el accelerator_view desde el subproceso que contiene el bloqueo de acceso D3D. Consulte también scoped_d3d_access_lock, una clase de estilo RAII para un bloqueo de acceso D3D basado en ámbito.

```cpp
void __cdecl d3d_access_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parámetros

*_Av*<br/>
El accelerator_view de cerrar.

## <a name="d3d_access_try_lock"></a><a name="d3d_access_try_lock"></a>d3d_access_try_lock

Intente adquirir el bloqueo de acceso D3D en un accelerator_view sin bloquear.

```cpp
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parámetros

*_Av*<br/>
El accelerator_view de cerrar.

### <a name="return-value"></a>Valor devuelto

true si se adquirió el bloqueo, o false si actualmente está en manos de otro subproceso.

## <a name="d3d_access_unlock"></a><a name="d3d_access_unlock"></a>d3d_access_unlock

Suelte el bloqueo de acceso D3D en el accelerator_view dado. Si el subproceso que realiza la llamada no mantiene el bloqueo en el accelerator_view los resultados son indefinidos.

```cpp
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parámetros

*_Av*<br/>
El accelerator_view para el que se liberará el bloqueo.

## <a name="firstbithigh"></a><a name="firstbithigh"></a>firstbithigh

Obtiene la ubicación del primer bit de conjunto en _X, comenzando con el bit de orden más alto y moviéndose hacia el bit de orden más bajo.

```cpp
inline int firstbithigh(int _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

La ubicación del primer bit establecido

## <a name="firstbitlow"></a><a name="firstbitlow"></a>firstbitlow

Obtiene la ubicación del primer bit de conjunto en _X, comenzando con el bit de orden más bajo y trabajando hacia el bit de orden más alto.

```cpp
inline int firstbitlow(int _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

Devuelve la ubicación del primer bit establecido

## <a name="get_buffer"></a><a name="get_buffer"></a>get_buffer

Obtenga la interfaz de búfer de Direct3D subyacente a la matriz especificada.

```cpp
template<
    typename value_type,
    int _Rank
>
IUnknown *get_buffer(
    const array<value_type, _Rank>& _Array)  ;
```

### <a name="parameters"></a>Parámetros

*value_type*<br/>
Tipo de los elementos de la matriz.

*_Rank*<br/>
El rango de la matriz.

*_Array*<br/>
Matriz en un accelerator_view de Direct3D para el que se devuelve la interfaz de búfer de Direct3D subyacente.

### <a name="return-value"></a>Valor devuelto

El puntero de interfaz IUnknown correspondiente al búfer de Direct3D subyacente a la matriz.

## <a name="a-nameget_device-get_device"></a><a name="get_device">get_device

Obtenga la interfaz del dispositivo D3D subyacente a una accelerator_view.

```cpp
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>Parámetros

*Av*<br/>
El accelerator_view D3D para el que se devuelve la interfaz de dispositivo D3D subyacente.

### <a name="return-value"></a>Valor devuelto

El `IUnknown` puntero de interfaz del dispositivo D3D subyacente al accelerator_view.

## <a name="imax"></a><a name="imax"></a>Imax

Determinar el valor numérico máximo de los argumentos

```cpp
inline int imax(
    int _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero

*_Y*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

Devolver el valor numérico máximo de los argumentos

## <a name="imin"></a><a name="imin"></a>Imin

Determinar el valor numérico mínimo de los argumentos

```cpp
inline int imin(
    int _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero

*_Y*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

Devolver el valor numérico mínimo de los argumentos

## <a name="is_timeout_disabled"></a><a name="is_timeout_disabled"></a>is_timeout_disabled

Devuelve un indicador booleano que indica si el tiempo de espera está deshabilitado para el accelerator_view especificado. Esto corresponde a la marca D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT para la creación de dispositivos Direct3D.

```cpp
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```

### <a name="parameters"></a>Parámetros

*_Accelerator_view*<br/>
El accelerator_view para el que se va a consultar la configuración de tiempo de espera deshabilitado.

### <a name="return-value"></a>Valor devuelto

Un indicador booleano que indica si el tiempo de espera está deshabilitado para el accelerator_view especificado.

## <a name="mad"></a><a name="mad"></a>Enojado

Calcula el producto del primer y segundo argumento especificado y, a continuación, agrega el tercer argumento especificado.

```cpp
inline float mad(
    float _X,
    float _Y,
    float _Z) restrict(amp);

inline double mad(
    double _X,
    double _Y,
    double _Z) restrict(amp);

inline int mad(
    int _X,
    int _Y,
    int _Z) restrict(amp);

inline unsigned int mad(
    unsigned int _X,
    unsigned int _Y,
    unsigned int _Z) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
El primer argumento especificado.

*_Y*<br/>
El segundo argumento especificado.

*_Z*<br/>
El tercer argumento especificado.

### <a name="return-value"></a>Valor devuelto

El resultado `_X` \* `_Y`  +  `_Z`de .

## <a name="make_array"></a><a name="make_array"></a>make_array

Cree una matriz a partir de un puntero de interfaz de búfer de Direct3D.

```cpp
template<
    typename value_type,
    int _Rank
>
array<value_type, _Rank> make_array(
    const extent<_Rank>& _Extent,
    const Concurrency::accelerator_view& _Rv,
    IUnknown* _D3D_buffer)  ;
```

### <a name="parameters"></a>Parámetros

*value_type*<br/>
El tipo de elemento de la matriz que se va a crear.

*_Rank*<br/>
El rango de la matriz que se va a crear.

*_Extent*<br/>
Extensión que describe la forma del agregado de matriz.

*_Rv*<br/>
Una vista del acelerador D3D en la que se va a crear la matriz.

*_D3D_buffer*<br/>
Puntero de interfaz IUnknown del búfer D3D desde el que crear la matriz.

### <a name="return-value"></a>Valor devuelto

Matriz creada con el búfer de Direct3D proporcionado.

## <a name="noise"></a><a name="noise"></a>Ruido

Genera un valor aleatorio utilizando el algoritmo de ruido Perlin

```cpp
inline float noise(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante a partir del cual generar ruido de Perlin

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de ruido de Perlin dentro de un rango entre -1 y 1

## <a name="radians"></a><a name="radians"></a>Radianes

Convierte _X de grados a radianes

```cpp
inline float radians(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve _X convertido de grados a radianes

## <a name="rcp"></a><a name="rcp"></a>rcp

Calcula la reciprocidad del argumento especificado mediante una aproximación rápida.

```cpp
inline float rcp(float _X) restrict(amp);

inline double rcp(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
El valor para el que se calcula la reciprocidad.

### <a name="return-value"></a>Valor devuelto

La reciprocidad del argumento especificado.

## <a name="reversebits"></a><a name="reversebits"></a>reversebits

Invierte el orden de los bits en _X

```cpp
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero sin signo

### <a name="return-value"></a>Valor devuelto

Devuelve el valor con el orden de bits invertido en _X

## <a name="saturate"></a><a name="saturate"></a>Saturar

Las abrazaderas _X dentro del rango de 0 a 1

```cpp
inline float saturate(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devoluciones _X sujetas dentro del rango de 0 a 1

## <a name="sign"></a><a name="sign"></a>Firmar

Determina el signo del argumento especificado.

```cpp
inline int sign(int _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

El signo del argumento.

## <a name="smoothstep"></a><a name="smoothstep"></a>smoothstep

Devuelve una interpolación Hermite suave entre 0 y 1, si _X está en el intervalo [_Min, _Max].

```cpp
inline float smoothstep(
    float _Min,
    float _Max,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Min*<br/>
Valor de punto flotante

*_Max*<br/>
Valor de punto flotante

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve 0 si _X es menor que _Min; 1 si _X es mayor que _Max; de lo contrario, un valor entre 0 y 1 si _X está en el intervalo [_Min, _Max]

## <a name="step"></a><a name="step"></a>Paso

Compara dos valores, devolviendo 0 o 1 en función del cual el valor es mayor

```cpp
inline float step(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Y*<br/>
Valor de punto flotante

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve 1 si el _X es mayor o igual que _Y; de lo contrario, 0

## <a name="umax"></a><a name="umax"></a>Umax

Determinar el valor numérico máximo de los argumentos

```cpp
inline unsigned int umax(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero

*_Y*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

Devolver el valor numérico máximo de los argumentos

## <a name="umin"></a><a name="umin"></a>umin

Determinar el valor numérico mínimo de los argumentos

```cpp
inline unsigned int umin(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero

*_Y*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

Devolver el valor numérico mínimo de los argumentos

## <a name="see-also"></a>Consulte también

[Concurrency::direct3d (Espacio de nombres)](concurrency-direct3d-namespace.md)
