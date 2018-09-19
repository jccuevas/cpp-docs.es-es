---
title: 'Funciones de espacio de nombres Concurrency:: Direct3D (AMP) | Microsoft Docs'
ms.custom: ''
ms.date: 08/31/2018
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 28943b62-52c9-42dc-baf1-ca7b095c1a19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aefb11f8028aa2af9822bc6433e85d06d0609a9d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039171"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Funciones de espacio de nombres Concurrency:: Direct3D (AMP)
||||
|-|-|-|
|[abs](#abs)|[clamp](#clamp)|[countbits](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|[d3d_access_lock](#d3d_access_lock)||
|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|[firstbithigh](#firstbithigh)|
|[firstbitlow](#firstbitlow)|[get_buffer](#get_buffer)|[get_device](#get_device)|
|[imax](#imax)|[imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|
|[mad](#mad)|[make_array](#make_array)|[ruido](#noise)|
|[radianes](#radians)|[rcp](#rcp)|[reversebits](#reversebits)|
|[saturate](#saturate)|[sign](#sign)|[smoothstep](#smoothstep)|
|[step](#step)|[umax](#umax)|[umin](#umin)|

## <a name="requirements"></a>Requisitos
**Encabezado:** amp.h **Namespace:** simultaneidad

##  <a name="abs"></a>  abs
Devuelve el valor absoluto del argumento.

```  
inline int abs(int _X) restrict(amp);
```  

### <a name="parameters"></a>Parámetros
*_X*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto
Devuelve el valor absoluto del argumento.

##  <a name="clamp"></a>  Clamp
Calcula el valor del primer argumento especificado filtrado a un intervalo definido por el segundo y tercer argumentos especificados.

```  
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
El valor que se va a filtrar

*_Min*<br/>
El límite inferior del intervalo de filtrado.

*_Max*<br/>
El límite superior del intervalo de filtrado.

### <a name="return-value"></a>Valor devuelto
El valor restringido de `_X`.

##  <a name="countbits"></a>  countbits
Cuenta el número de bits establecidos en _X

```  
inline unsigned int countbits(unsigned int _X) restrict(amp);
```  

### <a name="parameters"></a>Parámetros
*_X*<br/>
Valor entero sin signo

### <a name="return-value"></a>Valor devuelto
Devuelve el número de bits establecidos en _X

## <a name="create_accelerator_view"></a> create_accelerator_view
Crea un [accelerator_view](accelerator-view-class.md) objeto de un puntero a una interfaz de dispositivo Direct3D.

## <a name="syntax"></a>Sintaxis

```  
accelerator_view create_accelerator_view(  
    IUnknown * _D3D_device
    queuing_mode _Qmode = queuing_mode_automatic);

accelerator_view create_accelerator_view(  
    accelerator& _Accelerator,
    bool _Disable_timeout
    queuing_mode _Qmode = queuing_mode_automatic);
```  

#### <a name="parameters"></a>Parámetros
*_Accelerator*<br/>
El acelerador en el que es necesario crear la nueva vista.

*_D3D_device*<br/>
Puntero a la interfaz de dispositivo Direct3D.

*_Disable_timeout*<br/>
Un parámetro booleano que especifica si se debe deshabilitar el tiempo de espera para el accelerator_view recién creado. Esto corresponde a la marca D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT para la creación del dispositivo Direct3D y se usa para indicar si el sistema operativo debe permitir las cargas de trabajo que tardan más de 2 segundos en ejecutarse sin restablecer el dispositivo por el tiempo de espera de Windows mecanismo de detección y recuperación. Se recomienda usar esta marca si necesita realizar tareas prolongadas en accelerator_view.

*_Qmode*<br/>
El [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) que se usará para el accelerator_view recién creado. Este parámetro tiene un valor predeterminado de `queuing_mode_automatic`.

## <a name="return-value"></a>Valor devuelto
La `accelerator_view` objeto creado a partir de la interfaz de dispositivo Direct3D pasada.

## <a name="remarks"></a>Comentarios
Esta función crea un nuevo `accelerator_view` objeto de un puntero existente a una interfaz de dispositivo Direct3D. Si la llamada de función se realiza correctamente, se incrementa el recuento de referencias del parámetro por medio de un `AddRef` la llamada a la interfaz. Puede liberar con seguridad el objeto cuando ya no es necesario en el código de DirectX. Si se produce un error en la llamada al método, un [runtime_exception](runtime-exception-class.md) se produce.

La `accelerator_view` objeto que se crea mediante el uso de esta función es segura para subprocesos. Debe sincronizar el uso simultáneo de la `accelerator_view` objeto. Uso simultáneo de la `accelerator_view` objeto y la interfaz sin formato de ID3D11Device produce un comportamiento indefinido.

El runtime de C++ AMP proporciona información detallada del error en modo de depuración mediante el nivel de depuración de D3D si usas el `D3D11_CREATE_DEVICE_DEBUG` marca.


##  <a name="d3d_access_lock"></a>  d3d_access_lock
Adquirir un bloqueo en un accelerator_view para realizar operaciones D3D en recursos compartidos con el accelerator_view de forma segura con. El objeto accelerator_view y todos los recursos de C++ AMP asociados a este objeto accelerator_view internamente toman este bloqueo al realizar operaciones y se bloquean mientras otro subproceso mantiene el bloqueo de acceso de D3D. Este bloqueo es no recursivo: es un comportamiento indefinido para llamar a esta función desde un subproceso que ya tenía el bloqueo. Es un comportamiento indefinido realizar operaciones en el elemento accelerator_view o cualquier contenedor de datos asociada al accelerator_view desde el subproceso que mantiene el bloqueo de acceso de D3D. Vea también scoped_d3d_access_lock, una clase de estilo RAII para un bloqueo de acceso D3D basado en ámbitos.

```  
void __cdecl d3d_access_lock(accelerator_view& _Av);
```  

### <a name="parameters"></a>Parámetros
*_Av*<br/>
El objeto accelerator_view para bloquear.

##  <a name="d3d_access_try_lock"></a>  d3d_access_try_lock
Intento de adquirir el bloqueo de acceso de D3D en un accelerator_view sin bloquearse.

```  
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```  

### <a name="parameters"></a>Parámetros
*_Av*<br/>
El objeto accelerator_view para bloquear.

### <a name="return-value"></a>Valor devuelto
True si se adquirió el bloqueo, o false si está mantenido actualmente por otro subproceso.

##  <a name="d3d_access_unlock"></a>  d3d_access_unlock
Libere el bloqueo de acceso de D3D en el objeto accelerator_view especificado. Si el subproceso de llamada no mantiene el bloqueo de accelerator_view los resultados son indefinidos.

```  
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```  

### <a name="parameters"></a>Parámetros
*_Av*<br/>
El objeto accelerator_view para el que es se libere el bloqueo.

##  <a name="firstbithigh"></a>  firstbithigh
Obtiene la ubicación del primer bit establecido en _X, empezando por el bit de orden superior y desplazándose hacia el bit de orden inferior.

```  
inline int firstbithigh(int _X) restrict(amp);
```  

### <a name="parameters"></a>Parámetros
*_X*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto
La ubicación del primer bit establecido

##  <a name="firstbitlow"></a>  firstbitlow
Obtiene la ubicación del primer bit establecido en _X, empezando por el bit de orden inferior y trabajando hacia el bit de orden superior.

```  
inline int firstbitlow(int _X) restrict(amp);
```  

### <a name="parameters"></a>Parámetros
*_X*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto
Devuelve la ubicación del primer bit establecido

##  <a name="get_buffer"></a>  get_buffer
Obtener la interfaz del búfer Direct3D subyacente de la matriz especificada.

```  
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
Una matriz en un accelerator_view Direct3D para el que se devuelve la interfaz del búfer Direct3D subyacente.

### <a name="return-value"></a>Valor devuelto
El puntero de interfaz IUnknown correspondiente al búfer de Direct3D subyacente del array.

## <a name="a-namegetdevice-getdevice"></a><a name="get_device"> get_device
Obtener la interfaz de dispositivo D3D subyacente en un accelerator_view.

```
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>Parámetros
*AV*<br/>
El objeto accelerator_view de D3D para el que se devuelve la interfaz de dispositivo D3D subyacente.


### <a name="return-value"></a>Valor devuelto
El `IUnknown` puntero de interfaz del dispositivo D3D subyacente el accelerator_view.

##  <a name="imax"></a>  imax
Determinar el valor numérico máximo de los argumentos

```  
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

##  <a name="imin"></a>  Imín
Determinar el valor numérico mínimo de los argumentos

```  
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

##  <a name="is_timeout_disabled"></a>  is_timeout_disabled
Devuelve una marca booleana que indica si el tiempo de espera está deshabilitado para el accelerator_view especificado. Esto corresponde a la marca D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT para la creación del dispositivo Direct3D.

```  
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```  

### <a name="parameters"></a>Parámetros
*_Accelerator_view*<br/>
El objeto accelerator_view para el que el tiempo de espera deshabilita esta opción consiste en consultar.

### <a name="return-value"></a>Valor devuelto
Una marca booleana que indica si el tiempo de espera está deshabilitado para el accelerator_view especificado.

##  <a name="mad"></a>  mad
Calcula el producto del primer y segundo argumento especificado, a continuación, agrega el tercer argumento especificado.

```  
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
El resultado de `_X` \* `_Y`  +  `_Z`.

##  <a name="make_array"></a>  make_array
Crear una matriz de un puntero de interfaz del búfer de Direct3D.

```  
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
El tipo de elemento de la matriz que se creará.

*_Rank*<br/>
El rango de la matriz que se creará.

*_Extent*<br/>
Una extensión que describe la forma del agregado de matriz.

*_Rv*<br/>
En el que la matriz es crear una vista del Acelerador D3D.

*_D3D_buffer*<br/>
Puntero de interfaz IUnknown del búfer D3D para crear la matriz a partir de.

### <a name="return-value"></a>Valor devuelto
Matriz creada con el búfer de Direct3D proporcionado.

##  <a name="noise"></a>  ruido
Genera un valor aleatorio mediante el algoritmo de ruido de Perlin

```  
inline float noise(float _X) restrict(amp);
```  

### <a name="parameters"></a>Parámetros
*_X*<br/>
Valor de punto flotante de la que se va a generar ruido de Perlin

### <a name="return-value"></a>Valor devuelto
Devuelve el valor de ruido de Perlin The dentro de un intervalo comprendido entre -1 y 1

##  <a name="radians"></a>  radianes
Convierte _X de grados en radianes.

```  
inline float radians(float _X) restrict(amp);
```  

### <a name="parameters"></a>Parámetros
*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto
Devuelve _X convertido de grados a radianes

##  <a name="rcp"></a>  rcp
Calcula el recíproco del argumento especificado mediante una aproximación rápida.

```  
inline float rcp(float _X) restrict(amp);


inline double rcp(double _X) restrict(amp);
```  

### <a name="parameters"></a>Parámetros
*_X*<br/>
El valor de la cual se calcula el recíproco.

### <a name="return-value"></a>Valor devuelto
El recíproco del argumento especificado.

##  <a name="reversebits"></a>  reversebits
Invierte el orden de los bits en _X

```  
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```  

### <a name="parameters"></a>Parámetros
*_X*<br/>
Valor entero sin signo

### <a name="return-value"></a>Valor devuelto
Devuelve el valor con el orden de bit invertido en _X

##  <a name="saturate"></a>  saturate
Ajusta _X dentro del intervalo de 0 a 1

```  
inline float saturate(float _X) restrict(amp);
```  

### <a name="parameters"></a>Parámetros
*_X*<br/>
Valor de punto flotante

### <a name="return-value"></a>Valor devuelto
Devuelve _X fijados dentro del intervalo de 0 a 1

##  <a name="sign"></a>  sign
Determina el signo del argumento especificado.

```  
inline int sign(int _X) restrict(amp);
```  

### <a name="parameters"></a>Parámetros
*_X*<br/>
Valor entero

### <a name="return-value"></a>Valor devuelto
El signo del argumento.

##  <a name="smoothstep"></a>  smoothstep
Devuelve una interpolación suavizada de Hermite entre 0 y 1, si _X está en el intervalo de [_Min, _Max].

```  
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
Devuelve 0 si _X es menor que _Min; 1 si es mayor que _Max; _X en caso contrario, un valor entre 0 y 1 si _X está en el intervalo de [_Min, _Max]

##  <a name="step"></a>  step
Compara dos valores, devolviendo 0 o 1 según el valor que es mayor

```  
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
Devuelve 1 si el _X es mayor o igual que _Y; en caso contrario, 0

##  <a name="umax"></a>  umax
Determinar el valor numérico máximo de los argumentos

```  
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

##  <a name="umin"></a>  umin
Determinar el valor numérico mínimo de los argumentos

```  
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

## <a name="see-also"></a>Vea también
[Concurrency::direct3d (espacio de nombres)](concurrency-direct3d-namespace.md)
