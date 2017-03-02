---
title: Funciones del espacio de nombres de Concurrency::Direct3D (AMP) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28943b62-52c9-42dc-baf1-ca7b095c1a19
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 46cafc3c6d6f21eaf147ef0edfeca7f2c81d64e6
ms.lasthandoff: 02/24/2017

---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Funciones del espacio de nombres de Concurrency::Direct3D (AMP)
||||  
|-|-|-|  
|[ABS (función)](#abs)|[Clamp (función)](#clamp)|[countbits (función)](#countbits)|
|[create_accelerator_view (función)](#create_accelerator_view)|||
|[d3d_access_lock (función)](#d3d_access_lock)|[d3d_access_try_lock (función)](#d3d_access_try_lock)|[d3d_access_unlock (función)](#d3d_access_unlock)|  
|[firstbithigh (función)](#firstbithigh)|[firstbitlow (función)](#firstbitlow)|[get_buffer (función)](#get_buffer)|  
|[iMax (función)](#imax)|[imin (función)](#imin)|[is_timeout_disabled (función)](#is_timeout_disabled)|  
|[MAD (función)](#mad)|[make_array (función)](#make_array)|[noise (función)](#noise)|  
|[RADIANS (función)](#radians)|[RCP (función)](#rcp)|[reversebits (función)](#reversebits)|  
|[saturate (función)](#saturate)|[Sign (función)](#sign)|[smoothstep (función)](#smoothstep)|  
|[Step (función)](#step)|[UMAX (función)](#umax)|[umin (función)](#umin)|  
  
##  <a name="a-nameabsa--abs-function"></a><a name="abs"></a>ABS (función)  
 Devuelve el valor absoluto del argumento  
  
```  
inline int abs(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor entero  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor absoluto del argumento.  
  
##  <a name="a-nameclampa--clamp-function"></a><a name="clamp"></a>Clamp (función)  
 Calcula el valor del primer argumento especificado que se fija en un intervalo definido por el segundo y tercer argumento especificado.  
  
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
 `_X`  
 El valor que se fija  
  
 `_Min`  
 El límite inferior del intervalo de cierre.  
  
 `_Max`  
 El límite superior del intervalo de cierre.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor fijado de `_X`.  
  
##  <a name="a-namecountbitsa--countbits-function"></a><a name="countbits"></a>countbits (función)  
 Cuenta el número de bits de conjunto de _X  
  
```  
inline unsigned int countbits(unsigned int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor entero sin signo  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de bits del conjunto de _X  

## <a name="a-namecreateacceleratorviewa-createacceleratorview-function"></a><a name="create_accelerator_view"></a>create_accelerator_view (función)
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
 `_Accelerator`  
 El acelerador en el que es necesario crear el nuevo accelerator_view.  
  
 `_D3D_device`  
 Puntero a la interfaz de dispositivo Direct3D.  
  
 `_Disable_timeout`  
 Parámetro booleano que especifica si se debe deshabilitar el tiempo de espera para la accelerator_view recién creado. Esto corresponde a la marca D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT para crear un dispositivo Direct3D y se utiliza para indicar si el sistema operativo debe permitir cargas de trabajo que tardan más de 2 segundos en ejecutarse sin restablecer el dispositivo por el mecanismo de recuperación y detección de tiempo de espera de Windows. Se recomienda el uso de esta marca si necesita realizar tareas mucho tiempo en el accelerator_view.  
  
 `_Qmode`  
 El [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) que se utilizará para el accelerator_view recién creado. Este parámetro tiene un valor predeterminado de `queuing_mode_automatic`.  
  
## <a name="return-value"></a>Valor devuelto  
 La `accelerator_view` objeto creado a partir de la interfaz de dispositivo Direct3D pasada.  
  
## <a name="remarks"></a>Comentarios  
 Esta función crea un nuevo `accelerator_view` objeto de un puntero existente a una interfaz de dispositivo Direct3D. Si la llamada de función se realiza correctamente, se incrementa el recuento de referencias del parámetro por medio de un `AddRef` la llamada a la interfaz. Con seguridad, puede liberar el objeto cuando ya no sea necesario en el código de DirectX. Si se produce un error en la llamada al método, un [runtime_exception](runtime-exception-class.md) se produce.  
  
 La `accelerator_view` objeto que se crea mediante esta función es segura para subprocesos. Debe sincronizar uso simultáneo de la `accelerator_view` objeto. Uso simultáneo de la sincronización del `accelerator_view` objeto y la interfaz ID3D11Device sin formato produce un comportamiento indefinido.  
  
 El tiempo de ejecución de C++ AMP proporciona información detallada del error en modo de depuración utilizando la capa de D3D depurar si utiliza el `D3D11_CREATE_DEVICE_DEBUG` marca.  
  
  
##  <a name="a-named3daccesslocka--d3daccesslock-function"></a><a name="d3d_access_lock"></a>d3d_access_lock (función)  
 Adquirir un bloqueo en un accelerator_view con el fin de forma segura las operaciones de D3D en recursos compartidos con el accelerator_view. El accelerator_view y todos los recursos de C++ AMP asociados con este accelerator_view internamente toman este bloqueo al realizar operaciones y se bloqueará mientras otro subproceso mantiene el bloqueo de acceso de D3D. Este bloqueo no es recursiva: es llamar a esta función desde un subproceso que ya tiene el bloqueo de un comportamiento indefinido. Es un comportamiento no definido para realizar operaciones en el accelerator_view o cualquier contenedor de datos asociados con el accelerator_view desde el subproceso que mantiene el bloqueo del acceso de D3D. Consulte también scoped_d3d_access_lock, una clase de estilo RAII para un bloqueo de acceso basado en el ámbito D3D.  
  
```  
void __cdecl d3d_access_lock(accelerator_view& _Av);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Av`  
 Accelerator_view bloquear.  
  
##  <a name="a-named3daccesstrylocka--d3daccesstrylock-function"></a><a name="d3d_access_try_lock"></a>d3d_access_try_lock (función)  
 Intenta adquirir el bloqueo de acceso de D3D en un accelerator_view sin bloqueo.  
  
```  
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Av`  
 Accelerator_view bloquear.  
  
### <a name="return-value"></a>Valor devuelto  
 True si se adquirió el bloqueo, o falso si mantiene actualmente por otro subproceso.  
  
##  <a name="a-named3daccessunlocka--d3daccessunlock-function"></a><a name="d3d_access_unlock"></a>d3d_access_unlock (función)  
 Liberar el bloqueo de acceso de D3D en los accelerator_view determinado. Si el subproceso de llamada no se mantiene el bloqueo en el accelerator_view los resultados son indefinidos.  
  
```  
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Av`  
 Accelerator_view para el que es liberar el bloqueo.  
  
##  <a name="a-namefirstbithigha--firstbithigh-function"></a><a name="firstbithigh"></a>firstbithigh (función)  
 Obtiene la ubicación del primer bit establecido en _X, comenzando con el bit de orden superior y moverse hacia el bit de orden más bajo.  
  
```  
inline int firstbithigh(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor entero  
  
### <a name="return-value"></a>Valor devuelto  
 La ubicación del primer conjunto de bit  
  
##  <a name="a-namefirstbitlowa--firstbitlow-function"></a><a name="firstbitlow"></a>firstbitlow (función)  
 Obtiene la ubicación del primer bit establecido en _X, comenzando con el bit de orden más bajo y trabajar hacia el bit de orden superior.  
  
```  
inline int firstbitlow(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor entero  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la ubicación del primer bit establecido  
  
##  <a name="a-namegetbuffera--getbuffer-function"></a><a name="get_buffer"></a>get_buffer (función)  
 Obtener la interfaz del búfer de Direct3D subyacente de la matriz especificada.  
  
```  
template<
    typename value_type,  
    int _Rank  
>  
IUnknown *get_buffer(
    const array<value_type, _Rank>& _Array)  ;  
```  
  
### <a name="parameters"></a>Parámetros  
 `value_type`  
 Tipo de los elementos de la matriz.  
  
 `_Rank`  
 El rango de la matriz.  
  
 `_Array`  
 Una matriz en una accelerator_view de Direct3D que se devuelve la interfaz de búfer de Direct3D subyacente.  
  
### <a name="return-value"></a>Valor devuelto  
 El puntero de interfaz IUnknown correspondiente al búfer de Direct3D subyacente de la matriz.  
  
##  <a name="a-nameimaxa--imax-function"></a><a name="imax"></a>iMax (función)  
 Determinar el valor numérico máximo de los argumentos  
  
```  
inline int imax(
    int _X,  
    int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor entero  
  
 `_Y`  
 Valor entero  
  
### <a name="return-value"></a>Valor devuelto  
 Devolver el valor numérico máximo de los argumentos  
  
##  <a name="a-nameimina--imin-function"></a><a name="imin"></a>imin (función)  
 Determinar el valor numérico mínimo de los argumentos  
  
```  
inline int imin(
    int _X,  
    int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor entero  
  
 `_Y`  
 Valor entero  
  
### <a name="return-value"></a>Valor devuelto  
 Devolver el valor numérico mínimo de los argumentos  
  
##  <a name="a-nameistimeoutdisableda--istimeoutdisabled-function"></a><a name="is_timeout_disabled"></a>is_timeout_disabled (función)  
 Devuelve una marca booleana que indica si el tiempo de espera está deshabilitada para el accelerator_view especificado. Esto corresponde a la marca D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT para crear un dispositivo Direct3D.  
  
```  
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Accelerator_view`  
 Accelerator_view para que el tiempo de espera deshabilitada configuración consiste en consultar.  
  
### <a name="return-value"></a>Valor devuelto  
 Una marca booleana que indica si el tiempo de espera está deshabilitada para el accelerator_view especificado.  
  
##  <a name="a-namemada--mad-function"></a><a name="mad"></a>MAD (función)  
 Calcula el producto del primer y el segundo argumento especificado, a continuación, agrega el tercer argumento especificado.  
  
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
 `_X`  
 El primer argumento especificado.  
  
 `_Y`  
 El segundo argumento especificado.  
  
 `_Z`  
 El tercer argumento especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 The result of `_X` * `_Y` + `_Z`.  
  
##  <a name="a-namemakearraya--makearray-function"></a><a name="make_array"></a>make_array (función)  
 Cree una matriz de un puntero de interfaz de búfer de Direct3D.  
  
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
 `value_type`  
 El tipo de elemento de la matriz que se va a crear.  
  
 `_Rank`  
 El rango de la matriz que se va a crear.  
  
 `_Extent`  
 Una extensión que describe la forma de la agregación de la matriz.  
  
 `_Rv`  
 Vista de aceleradores de D3D en los que es necesario crear la matriz.  
  
 `_D3D_buffer`  
 Puntero de interfaz IUnknown del búfer para crear la matriz de D3D.  
  
### <a name="return-value"></a>Valor devuelto  
 Una matriz en el que se crea utilizando el búfer proporcionado de Direct3D.  
  
##  <a name="a-namenoisea--noise-function"></a><a name="noise"></a>noise (función)  
 Genera un valor aleatorio mediante el algoritmo de ruido de Perlin  
  
```  
inline float noise(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante de la que se va a generar ruido Perlin  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de ruido de Perlin el dentro de un intervalo comprendido entre -1 y 1  
  
##  <a name="a-nameradiansa--radians-function"></a><a name="radians"></a>RADIANS (función)  
 Convierte _X de grados a radianes  
  
```  
inline float radians(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve _X convertido de grados a radianes  
  
##  <a name="a-namercpa--rcp-function"></a><a name="rcp"></a>RCP (función)  
 Calcula el inverso del argumento especificado mediante una aproximación rápida.  
  
```  
inline float rcp(float _X) restrict(amp);

 
inline double rcp(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 El valor para el que se va a calcular el recíproco.  
  
### <a name="return-value"></a>Valor devuelto  
 El recíproco de los argumentos especificados.  
  
##  <a name="a-namereversebitsa--reversebits-function"></a><a name="reversebits"></a>reversebits (función)  
 Invierte el orden de los bits de _X  
  
```  
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor entero sin signo  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor con el orden de bit invertido en _X  
  
##  <a name="a-namesaturatea--saturate-function"></a><a name="saturate"></a>saturate (función)  
 Fija _X dentro del intervalo de 0 a 1  
  
```  
inline float saturate(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve _X fijados dentro del intervalo de 0 a 1  
  
##  <a name="a-namesigna--sign-function"></a><a name="sign"></a>Sign (función)  
 Determina el signo del argumento especificado.  
  
```  
inline int sign(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor entero  
  
### <a name="return-value"></a>Valor devuelto  
 El signo del argumento.  
  
##  <a name="a-namesmoothstepa--smoothstep-function"></a><a name="smoothstep"></a>smoothstep (función)  
 Devuelve una interpolación Hermite suave entre 0 y 1, si _X está en el intervalo [_Min, _Max].  
  
```  
inline float smoothstep(
    float _Min,  
    float _Max,  
    float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Min`  
 Valor de punto flotante  
  
 `_Max`  
 Valor de punto flotante  
  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve 0 si _X es menor que _Min; 1 si _X es mayor que _Max; de lo contrario, un valor entre 0 y 1 si _X está en el intervalo [_Min, _Max]  
  
##  <a name="a-namestepa--step-function"></a><a name="step"></a>Step (función)  
 Compara dos valores y devuelve 0 o 1 según cuyo valor es mayor  
  
```  
inline float step(
    float _Y,  
    float _X) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Y`  
 Valor de punto flotante  
  
 `_X`  
 Valor de punto flotante  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve 1 si el _X es mayor o igual que _Y; de lo contrario, 0  
  
##  <a name="a-nameumaxa--umax-function"></a><a name="umax"></a>UMAX (función)  
 Determinar el valor numérico máximo de los argumentos  
  
```  
inline unsigned int umax(
    unsigned int _X,  
    unsigned int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor entero  
  
 `_Y`  
 Valor entero  
  
### <a name="return-value"></a>Valor devuelto  
 Devolver el valor numérico máximo de los argumentos  
  
##  <a name="a-nameumina--umin-function"></a><a name="umin"></a>umin (función)  
 Determinar el valor numérico mínimo de los argumentos  
  
```  
inline unsigned int umin(
    unsigned int _X,  
    unsigned int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_X`  
 Valor entero  
  
 `_Y`  
 Valor entero  
  
### <a name="return-value"></a>Valor devuelto  
 Devolver el valor numérico mínimo de los argumentos  
  
## <a name="see-also"></a>Vea también  
 [Namespace Concurrency::Direct3D](concurrency-direct3d-namespace.md)

