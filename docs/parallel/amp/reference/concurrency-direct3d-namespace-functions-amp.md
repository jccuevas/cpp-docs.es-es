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
ms.openlocfilehash: 438d211ac2f15bf781b704a7d0d7484d1542f131
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127051"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Concurrency::direct3d (Funciones del espacio de nombres) (AMP)

||||
|-|-|-|
|[abs](#abs)|[Sujet](#clamp)|[countbits (](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|[d3d_access_lock](#d3d_access_lock)||
|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|[firstbithigh (](#firstbithigh)|
|[firstbitlow (](#firstbitlow)|[get_buffer](#get_buffer)|[get_device](#get_device)|
|[imax](#imax)|[imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|
|[Mad](#mad)|[make_array](#make_array)|[producido](#noise)|
|[radianes](#radians)|[Rep](#rcp)|[reversebits (](#reversebits)|
|[saturar](#saturate)|[sign](#sign)|[smoothstep (](#smoothstep)|
|[pasar](#step)|[escáner](#umax)|[umin](#umin)|

## <a name="requirements"></a>Requisitos

**Encabezado:** amp. h **espacio de nombres:** simultaneidad

## <a name="abs"></a>  abs

Devuelve el valor absoluto del argumento.

```cpp
inline int abs(int _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

Devuelve el valor absoluto del argumento.

## <a name="clamp"></a>Sujet

Calcula el valor del primer argumento especificado fijado en un intervalo definido por el segundo y tercer argumento especificado.

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
Valor que se va a fijar.

*_Min*<br/>
Límite inferior del intervalo de fijación.

*_Max*<br/>
Límite superior del intervalo de fijación.

### <a name="return-value"></a>Valor devuelto

Valor con compresión de `_X`.

## <a name="countbits"></a>countbits (

Cuenta el número de bits establecidos en _X

```cpp
inline unsigned int countbits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero sin signo

### <a name="return-value"></a>Valor devuelto

Devuelve el número de bits establecidos en _X

## <a name="create_accelerator_view"></a>create_accelerator_view

Crea un objeto [accelerator_view](accelerator-view-class.md) a partir de un puntero a una interfaz de dispositivo Direct3D.

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
Acelerador en el que se va a crear el nuevo accelerator_view.

*_D3D_device*<br/>
Puntero a la interfaz de dispositivo Direct3D.

*_Disable_timeout*<br/>
Parámetro booleano que especifica si se debe deshabilitar el tiempo de espera para el accelerator_view recién creado. Esto corresponde a la marca de D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT para la creación de dispositivos de Direct3D y se usa para indicar si el sistema operativo debe permitir que las cargas de trabajo que tardan más de 2 segundos en ejecutarse sin restablecer el dispositivo según el tiempo de espera de Windows mecanismo de detección y recuperación. Se recomienda el uso de esta marca si necesita realizar tareas que consumen mucho tiempo en el accelerator_view.

*_Qmode*<br/>
[Queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) que se va a utilizar para el accelerator_view que se acaba de crear. Este parámetro tiene un valor predeterminado de `queuing_mode_automatic`.

## <a name="return-value"></a>Valor devuelto

Objeto `accelerator_view` creado a partir de la interfaz de dispositivo Direct3D que se ha pasado.

## <a name="remarks"></a>Observaciones

Esta función crea un nuevo objeto `accelerator_view` a partir de un puntero existente a una interfaz de dispositivo Direct3D. Si la llamada de función se realiza correctamente, el recuento de referencias del parámetro se incrementa por medio de una llamada `AddRef` a la interfaz. Puede liberar el objeto de forma segura cuando ya no sea necesario en el código de DirectX. Si se produce un error en la llamada al método, se produce una [runtime_exception](runtime-exception-class.md) .

El objeto `accelerator_view` que se crea mediante esta función es seguro para subprocesos. Debe sincronizar el uso simultáneo del objeto `accelerator_view`. El uso simultáneo no sincronizado del objeto `accelerator_view` y de la interfaz ID3D11Device sin procesar produce un comportamiento indefinido.

El C++ tiempo de ejecución del amp proporciona información detallada del error en modo de depuración mediante el uso de la capa de depuración D3D si usa la marca `D3D11_CREATE_DEVICE_DEBUG`.

## <a name="d3d_access_lock"></a>d3d_access_lock

Adquiera un bloqueo en un accelerator_view para realizar operaciones D3D con seguridad en recursos compartidos con la accelerator_view. El accelerator_view y todos C++ los recursos de amp asociados a este accelerator_view realizar este bloqueo internamente al realizar operaciones y se bloqueará mientras otro subproceso tenga el bloqueo de acceso de D3D. Este bloqueo no es recursivo: es un comportamiento indefinido para llamar a esta función desde un subproceso que ya contiene el bloqueo. Es un comportamiento indefinido para realizar operaciones en el accelerator_view o en cualquier contenedor de datos asociado a la accelerator_view desde el subproceso que contiene el bloqueo de acceso de D3D. Vea también scoped_d3d_access_lock, una clase de estilo RAII para un bloqueo de acceso de D3D basado en el ámbito.

```cpp
void __cdecl d3d_access_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parámetros

*_Av*<br/>
Accelerator_view que se va a bloquear.

## <a name="d3d_access_try_lock"></a>d3d_access_try_lock

Intento de adquirir el bloqueo de acceso de D3D en un accelerator_view sin bloqueos.

```cpp
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parámetros

*_Av*<br/>
Accelerator_view que se va a bloquear.

### <a name="return-value"></a>Valor devuelto

True si se adquirió el bloqueo, o false si está ocupado actualmente por otro subproceso.

## <a name="d3d_access_unlock"></a>d3d_access_unlock

Libera el bloqueo de acceso de D3D en el accelerator_view especificado. Si el subproceso que realiza la llamada no mantiene el bloqueo en la accelerator_view los resultados no están definidos.

```cpp
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```

### <a name="parameters"></a>Parámetros

*_Av*<br/>
Accelerator_view para el que se va a liberar el bloqueo.

## <a name="firstbithigh"></a>firstbithigh (

Obtiene la ubicación del primer bit establecido en _X, empezando por el bit de orden superior y desplazándose hacia el bit de orden más bajo.

```cpp
inline int firstbithigh(int _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

La ubicación del primer bit establecido

## <a name="firstbitlow"></a>firstbitlow (

Obtiene la ubicación del primer bit establecido en _X, empezando por el bit de orden más bajo y trabajando hacia el bit de orden superior.

```cpp
inline int firstbitlow(int _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

Devuelve la ubicación del primer bit establecido

## <a name="get_buffer"></a>get_buffer

Obtiene la interfaz de búfer de Direct3D subyacente a la matriz especificada.

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

Puntero a la interfaz IUnknown correspondiente al búfer de Direct3D subyacente a la matriz.

## <a name="a-nameget_device-get_device"></a><a name="get_device"> get_device

Obtiene la interfaz de dispositivo D3D que subyace a un accelerator_view.

```cpp
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>Parámetros

*Av*<br/>
Accelerator_view D3D para el que se devuelve la interfaz de dispositivo D3D subyacente.

### <a name="return-value"></a>Valor devuelto

Puntero de interfaz de `IUnknown` del dispositivo D3D subyacente al accelerator_view.

## <a name="imax"></a>imax

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

Devuelve el valor numérico máximo de los argumentos.

## <a name="imin"></a>imin

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

Devuelve el valor numérico mínimo de los argumentos.

## <a name="is_timeout_disabled"></a>is_timeout_disabled

Devuelve una marca booleana que indica si el tiempo de espera está deshabilitado para el accelerator_view especificado. Esto corresponde a la marca D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT para la creación del dispositivo Direct3D.

```cpp
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```

### <a name="parameters"></a>Parámetros

*_Accelerator_view*<br/>
Accelerator_view para el que se va a consultar el valor de tiempo de espera deshabilitado.

### <a name="return-value"></a>Valor devuelto

Marca booleana que indica si el tiempo de espera está deshabilitado para el accelerator_view especificado.

## <a name="mad"></a>Mad

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
Primer argumento especificado.

*_Y*<br/>
Segundo argumento especificado.

*_Z*<br/>
Tercer argumento especificado.

### <a name="return-value"></a>Valor devuelto

El resultado de `_X` \* `_Y` + `_Z`.

## <a name="make_array"></a>make_array

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
Tipo de elemento de la matriz que se va a crear.

*_Rank*<br/>
Rango de la matriz que se va a crear.

*_Extent*<br/>
Una extensión que describe la forma del agregado de matriz.

*_Rv*<br/>
Una vista de acelerador D3D en la que se va a crear la matriz.

*_D3D_buffer*<br/>
Puntero de interfaz IUnknown del búfer D3D del que se va a crear la matriz.

### <a name="return-value"></a>Valor devuelto

Una matriz creada con el búfer de Direct3D proporcionado.

## <a name="noise"></a>producido

Genera un valor aleatorio mediante el algoritmo de ruido de Perlen.

```cpp
inline float noise(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante a partir del cual se generará el ruido de Perl

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de ruido de Perlen dentro de un intervalo entre-1 y 1

## <a name="radians"></a>radianes

Convierte _X de grados a radianes.

```cpp
inline float radians(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve _X convertido de grados a radianes.

## <a name="rcp"></a>Rep

Calcula el recíproco del argumento especificado mediante una aproximación rápida.

```cpp
inline float rcp(float _X) restrict(amp);

inline double rcp(double _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor para el que se va a calcular el recíproco.

### <a name="return-value"></a>Valor devuelto

Recíproco del argumento especificado.

## <a name="reversebits"></a>reversebits (

Invierte el orden de los bits en _X

```cpp
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero sin signo

### <a name="return-value"></a>Valor devuelto

Devuelve el valor con el orden de bits invertido en _X

## <a name="saturate"></a>saturar

Las abrazaderas _X en el intervalo de 0 a 1

```cpp
inline float saturate(float _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto

Devuelve _X fija en el intervalo de 0 a 1

## <a name="sign"></a>sesión

Determina el signo del argumento especificado.

```cpp
inline int sign(int _X) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_X*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto

Signo del argumento.

## <a name="smoothstep"></a>smoothstep (

Devuelve una interpolación Smooth Hermite entre 0 y 1, si _X está en el intervalo [_Min, _Max].

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

Devuelve 0 si _X es menor que _Min; 1 si _X es mayor que _Max; de lo contrario, un valor comprendido entre 0 y 1 si _X está en el intervalo [_Min, _Max]

## <a name="step"></a>pasar

Compara dos valores y devuelve 0 o 1 según el valor que sea mayor.

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

## <a name="umax"></a>escáner

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

Devuelve el valor numérico máximo de los argumentos.

## <a name="umin"></a>umin

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

Devuelve el valor numérico mínimo de los argumentos.

## <a name="see-also"></a>Consulte también

[Concurrency::direct3d (espacio de nombres)](concurrency-direct3d-namespace.md)
