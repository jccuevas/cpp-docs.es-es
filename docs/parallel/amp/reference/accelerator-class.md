---
title: Accelerator (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amprt/Concurrency::accelerator
dev_langs:
- C++
helpviewer_keywords:
- accelerator class
ms.assetid: 37eed593-cf87-4611-9cdc-e98df6c2377a
caps.latest.revision: 29
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: b1bdd7f6979094658d1de6f9690bc44dc50ee8bb
ms.lasthandoff: 02/24/2017

---
# <a name="accelerator-class"></a>accelerator (Clase)
Un acelerador es una capacidad de hardware que está optimizada para la informática paralela de los datos. Una tecla de aceleración puede ser un dispositivo conectado a un bus de PCIe (por ejemplo, una GPU), o puede ser una instrucción extendida establecer en la CPU principal.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class accelerator;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Acelerador de Constructor](#ctor)|Inicializa una nueva instancia de la clase `accelerator`.|  
|[~ accelerator (destructor)](#ctor)|Destruye el objeto `accelerator`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CREATE_VIEW (método)](#create_view)|Crea y devuelve un `accelerator_view` objeto en este acelerador.|  
|[get_all (método)](#get_all)|Devuelve un vector de `accelerator` objetos que representan todos los aceleradores disponibles.|  
|[get_auto_selection_view (método)](#get_auto_selection_view)|Devuelve la selección automática de `accelerator_view`.|  
|[get_dedicated_memory (método)](#get_dedicated_memory)|Devuelve la memoria dedicada para la `accelerator`, en kilobytes.|  
|[get_default_cpu_access_type (método)](#get_default_cpu_access_type)|Devuelve el valor predeterminado [access_type ()](concurrency-namespace-enums-amp.md#access_type) de búferes creados en este acelerador.|  
|[get_default_view (método)](#get_default_view)|Devuelve el valor predeterminado `accelerator_view` objeto que está asociado el `accelerator`.|  
|[get_description (método)](#get_description)|Devuelve una breve descripción de la `accelerator` dispositivo.|  
|[get_device_path (método)](#get_device_path)|Devuelve la ruta de acceso del dispositivo.|  
|[get_has_display (método)](#get_has_display)|Determina si el `accelerator` se adjunta a una pantalla.|  
|[get_is_debug (método)](#get_is_debug)|Determina si el `accelerator` tiene la capa de depuración habilitada para los informes de error importante.|  
|[get_is_emulated (método)](#get_is_emulated)|Determina si el `accelerator` se emula.|  
|[get_supports_cpu_shared_memory (método)](#get_supports_cpu_shared_memory)|Determina si la `accelerator` es compatible con memoria compartida|  
|[get_supports_double_precision (método)](#get_supports_double_precision)|Determina si el `accelerator` se adjunta a una pantalla.|  
|[get_supports_limited_double_precision (método)](#get_supports_limited_double_precision)|Determina si el `accelerator` proporciona compatibilidad limitada para matemáticas de precisión doble.|  
|[get_version (método)](#get_version)|Devuelve la versión de la `accelerator`.|  
|[set_default (método)](#set_default)|Devuelve la ruta de acceso del Acelerador predeterminado.|  
|[set_default_cpu_access_type (método)](#set_default_cpu_access_type)|Establece el valor predeterminado CPU [access_type ()](concurrency-namespace-enums-amp.md#access_type)para matrices y asignaciones de memoria implícitas realizadas en este `accelerator`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[operador! = (operador)](#operator_neq)|Compara este `accelerator` objeto con otro y devuelve `false` si son iguales; en caso contrario, devuelve `true`.|  
|[operador = (operador)](#operator_eq)|Copia el contenido del elemento `accelerator` objeto a ésta.|  
|[Operator == (operador)](#operator_eq_eq)|Compara este `accelerator` objeto con otro y devuelve `true` si son iguales; en caso contrario, devuelve `false`.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[cpu_accelerator miembro de datos](#cpu_accelerator)|Obtiene una cadena constante para la CPU `accelerator`.|  
|[dedicated_memory miembro de datos](#dedicated_memory)|Obtiene la memoria dedicada para la `accelerator`, en kilobytes.|  
|[default_accelerator miembro de datos](#default_accelerator)|Obtiene una cadena constante para el valor predeterminado `accelerator`.|  
|[Miembro de datos de default_cpu_access_type](#default_cpu_access_type)|Obtiene o establece el valor predeterminado CPU [access_type ()](concurrency-namespace-enums-amp.md#access_type)para matrices y asignaciones de memoria implícitas realizadas en este `accelerator`.|  
|[default_view miembro de datos](#default_view)|Obtiene el valor predeterminado `accelerator_view` objeto que está asociado el `accelerator`.|  
|[Descripción del miembro de datos](#description)|Obtiene una breve descripción de la `accelerator` dispositivo.|  
|[device_path miembro de datos](#device_path)|Obtiene la ruta de acceso del dispositivo.|  
|[Miembro de datos direct3d_ref](#direct3d_ref)|Obtiene una cadena constante para una referencia de Direct3D `accelerator`.|  
|[Miembro de datos direct3d_warp](#direct3d_warp)|Obtiene la cadena de constante para un `accelerator` de objeto que puede usar para ejecutar el código de C++ AMP en las CPU de varios núcleo que usan extensiones de SIMD de transmisión (SSE).|  
|[has_display miembro de datos](#has_display)|Obtiene un valor booleano que indica si el `accelerator` se adjunta a una pantalla.|  
|[is_debug miembro de datos](#is_debug)|Indica si la `accelerator` tiene la capa de depuración habilitada para los informes de error importante.|  
|[is_emulated miembro de datos](#is_emulated)|Indica si el `accelerator` se emula.|  
|[Miembro de datos de supports_cpu_shared_memory](#supports_cpu_shared_memory)|Indica si la `accelerator` es compatible con la memoria compartida.|  
|[Miembro de datos de supports_double_precision](#supports_double_precision)|Indica si el Acelerador admite matemáticas de precisión doble.|  
|[Miembro de datos de supports_limited_double_precision](#supports_limited_double_precision)|Indica si el acelerador proporciona compatibilidad limitada para matemáticas de precisión doble.|  
|[Miembro de datos de la versión](#version)|Obtiene la versión de la `accelerator`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `accelerator`  
  
## <a name="remarks"></a>Comentarios  
 Un acelerador es una capacidad de hardware que está optimizada para la informática paralela de los datos. Un acelerador suele ser una GPU, pero también puede ser una entidad del host virtual como un dispositivo de DirectX REF, una deformación (un dispositivo de lado de CPU que se acelera por medio de instrucciones SSE) o la propia CPU.  
  
 Puede construir un `accelerator` objeto enumerando los dispositivos disponibles, u obteniendo el dispositivo de forma predeterminada, el dispositivo de referencia o el dispositivo WARP.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** Concurrency  
  
##  <a name="dtor"></a></a> ~ Acelerador 

 Destruye el objeto `accelerator`.  
  
```  
~accelerator();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="a-namectora-accelerator"></a><a name="ctor"></a>Acelerador 

 Inicializa una nueva instancia de la [accelerator (clase)](accelerator-class.md).  
  
```  
accelerator();

 
explicit accelerator(const std::wstring& _Device_path);

 
accelerator(const accelerator& _Other);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Device_path`  
 La ruta de acceso del dispositivo físico.  
  
 `_Other`  
 El Acelerador para copiar.  
  
##  <a name="a-namecpuacceleratora-cpuaccelerator"></a><a name="cpu_accelerator"></a>cpu_accelerator 

 Obtiene una cadena constante para el Acelerador de CPU.  
  
```  
static const wchar_t cpu_accelerator[];  
```  
  
##  <a name="a-namecreateviewa-createview"></a><a name="create_view"></a>CREATE_VIEW 

 Crea y devuelve un `accelerator_view` objeto en este acelerador, utilizando el modo de cola especificado. Cuando no se especifica el modo de cola, la nueva `accelerator_view` utiliza la [queuing_mode::immediate](concurrency-namespace-enums-amp.md#queuing_mode) modo de cola.  
  
```  
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```  
  
### <a name="parameters"></a>Parámetros  
 `qmode`  
 El modo de cola.  
  
### <a name="return-value"></a>Valor devuelto  
 Un nuevo `accelerator_view` objeto en este acelerador, utilizando el modo de cola especificado.  
  
##  <a name="a-namededicatedmemorya-dedicatedmemory"></a><a name="dedicated_memory"></a>dedicated_memory 

 Obtiene la memoria dedicada para la `accelerator`, en kilobytes.  
  
```  
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;  
```  
  
##  <a name="a-namedefaultacceleratora-defaultaccelerator"></a><a name="default_accelerator"></a>default_accelerator 

 Obtiene una cadena constante para el valor predeterminado `accelerator`.  
  
```  
static const wchar_t default_accelerator[];  
```  
  
##  <a name="a-namedefaultcpuaccesstypea-defaultcpuaccesstype"></a><a name="default_cpu_access_type"></a>default_cpu_access_type 

 El valor predeterminado cpu [access_type ()](concurrency-namespace-enums-amp.md#access_type)para matrices y asignaciones de memoria implícitas realizadas en esta este `accelerator`.  
  
```  
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;  
```  
  
##  <a name="a-namedefaultviewa-defaultview"></a><a name="default_view"></a>default_view 

 Obtiene la vista de acelerador predeterminado que está asociada el `accelerator`.  
  
```  
__declspec(property(get= get_default_view)) accelerator_view default_view;  
```  
  
##  <a name="a-namedescriptiona-description"></a><a name="description"></a>Descripción 

 Obtiene una breve descripción de la `accelerator` dispositivo.  
  
```  
__declspec(property(get= get_description)) std::wstring description;  
```  
  
##  <a name="a-namedevicepatha-devicepath"></a><a name="device_path"></a>device_path 

 Obtiene la ruta de acceso del acelerador. La ruta de acceso es único en el sistema.  
  
```  
__declspec(property(get= get_device_path)) std::wstring device_path;  
```  
  
##  <a name="a-namedirect3drefa-direct3dref"></a><a name="direct3d_ref"></a>direct3d_ref 

 Obtiene una cadena constante para un acelerador de referencia de Direct3D.  
  
```  
static const wchar_t direct3d_ref[];  
```  
  
##  <a name="a-namedirect3dwarpa-direct3dwarp"></a><a name="direct3d_warp"></a>direct3d_warp 

 Obtiene la cadena de constante para un `accelerator` de objeto que puede usar para ejecutar el código de C++ AMP en las CPU de varios núcleo con extensiones SIMD de transmisión (SSE).  
  
```  
static const wchar_t direct3d_warp[];  
```  
  
##  <a name="a-namegetalla-getall"></a><a name="get_all"></a>get_all 

 Devuelve un vector de `accelerator` objetos que representan todos los aceleradores disponibles.  
  
```  
static inline std::vector<accelerator> get_all();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El vector de aceleradores disponibles  
  
##  <a name="a-namegetautoselectionviewa-getautoselectionview"></a><a name="get_auto_selection_view"></a>get_auto_selection_view 

 Devuelve el accelerator_view de selección automática, que, cuando especifica que los resultados de destino parallel_for_each en el accelerator_view de destino para ejecutar el kernel parallel_for_each seleccionarse automáticamente en tiempo de ejecución. Para todos los demás casos, la accelerator_view devuelta por este método es igual que el accelerator_view predeterminada del Acelerador predeterminado  
  
```  
static accelerator_view __cdecl get_auto_selection_view();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El accelerator_view de selección automática.  
  
##  <a name="a-namegetdedicatedmemorya-getdedicatedmemory"></a><a name="get_dedicated_memory"></a>get_dedicated_memory 

 Devuelve la memoria dedicada para la `accelerator`, en kilobytes.  
  
```  
size_t get_dedicated_memory() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 La memoria dedicada para la `accelerator`, en kilobytes.  
  
##  <a name="a-namegetdefaultcpuaccesstypea-getdefaultcpuaccesstype"></a><a name="get_default_cpu_access_type"></a>get_default_cpu_access_type 

 Obtiene la cpu de forma predeterminada, access_type () para los búferes creados en este acelerador  
  
```  
access_type get_default_cpu_access_type() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Parámetro access_type de cpu de predeterminado para los búferes creados en este acelerador.  
  
##  <a name="a-namegetdefaultviewa-getdefaultview"></a><a name="get_default_view"></a>get_default_view 

 Devuelve el valor predeterminado `accelerator_view` objeto que está asociado el `accelerator`.  
  
```  
accelerator_view get_default_view() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor predeterminado `accelerator_view` objeto que está asociado el `accelerator`.  
  
##  <a name="a-namegetdescriptiona-getdescription"></a><a name="get_description"></a>get_description 

 Devuelve una breve descripción de la `accelerator` dispositivo.  
  
```  
std::wstring get_description() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una breve descripción de la `accelerator` dispositivo.  
  
##  <a name="a-namegetdevicepatha-getdevicepath"></a><a name="get_device_path"></a>get_device_path 

 Devuelve la ruta de acceso del acelerador. La ruta de acceso es único en el sistema.  
  
```  
std::wstring get_device_path() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 La ruta de acceso de la instancia de dispositivo único de todo el sistema.  
  
##  <a name="a-namegethasdisplaya-gethasdisplay"></a><a name="get_has_display"></a>get_has_display 

 Devuelve un valor booleano que indica si la `accelerator` puede enviar a una pantalla.  
  
```  
bool get_has_display() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el `accelerator` puede enviar a una pantalla; en caso contrario, `false`.  
  
##  <a name="a-namegetisdebuga-getisdebug"></a><a name="get_is_debug"></a>get_is_debug 

 Determina si el `accelerator` tiene la capa de depuración habilitada para los informes de error importante.  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el `accelerator` tiene la capa de depuración habilitada para los informes de error importante. En caso contrario, es `false`.  
  
##  <a name="a-namegetisemulateda-getisemulated"></a><a name="get_is_emulated"></a>get_is_emulated 

 Determina si el `accelerator` se emula.  
  
```  
bool get_is_emulated() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el `accelerator` se emula. En caso contrario, es `false`.  
  
##  <a name="a-namegetsupportscpusharedmemorya-getsupportscpusharedmemory"></a><a name="get_supports_cpu_shared_memory"></a>get_supports_cpu_shared_memory 

 Devuelve un valor booleano que indica si el Acelerador admite memoria accesible el acelerador y la CPU.  
  
```  
bool get_supports_cpu_shared_memory() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el acelerador es compatible con memoria compartida de CPU; de lo contrario, `false`.  
  
##  <a name="a-namegetsupportsdoubleprecisiona-getsupportsdoubleprecision"></a><a name="get_supports_double_precision"></a>get_supports_double_precision 

 Devuelve un valor booleano que indica si el Acelerador admite matemáticas de precisión doble, incluidos fusionada multiplicar agrega (FMA), división, recíproco y la conversión entre `int` y `double`.  
  
```  
bool get_supports_double_precision() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el Acelerador admite double matemáticas de precisión; de lo contrario, `false`.  
  
##  <a name="a-namegetsupportslimiteddoubleprecisiona-getsupportslimiteddoubleprecision"></a><a name="get_supports_limited_double_precision"></a>get_supports_limited_double_precision 

 Devuelve un valor booleano que indica si el acelerador proporciona compatibilidad limitada para matemáticas de precisión doble. Si el acelerador tiene sólo una compatibilidad limitada, a continuación, fundida multiplicar agregar (FMA), división, recíproco y la conversión entre `int` y `double` no son compatibles.  
  
```  
bool get_supports_limited_double_precision() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el acelerador proporciona compatibilidad limitada para double matemáticas de precisión; de lo contrario, `false`.  
  
##  <a name="a-namegetversiona-getversion"></a><a name="get_version"></a>get_version 

 Devuelve la versión de la `accelerator`.  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 La versión de la `accelerator`.  
  
##  <a name="a-namehasdisplaya-hasdisplay"></a><a name="has_display"></a>has_display 

 Obtiene un valor booleano que indica si la `accelerator` puede enviar a una pantalla.  
  
```  
__declspec(property(get= get_has_display)) bool has_display;  
```  
  
##  <a name="a-nameisdebuga-isdebug"></a><a name="is_debug"></a>is_debug 

 Obtiene un valor booleano que indica si el `accelerator` tiene la capa de depuración habilitada para los informes de error importante.  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="a-nameisemulateda-isemulated"></a><a name="is_emulated"></a>is_emulated 

 Obtiene un valor booleano que indica si el `accelerator` se emula.  
  
```  
__declspec(property(get= get_is_emulated)) bool is_emulated;  
```  
  
##  <a name="a-nameoperatorneqa-operator"></a><a name="operator_neq"></a>operador! = 

 Compara este `accelerator` objeto con otro y devuelve `false` si son iguales; en caso contrario, devuelve `true`.  
  
```  
bool operator!= (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `accelerator` objeto que se va a comparar con éste.  
  
### <a name="return-value"></a>Valor devuelto  
 `false`Si los dos `accelerator` objetos son iguales; en caso contrario, `true`.  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>operador = 

 Copia el contenido del elemento `accelerator` objeto a ésta.  
  
```  
accelerator& operator= (const accelerator& _Other);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `accelerator` objeto que se va a copiar de.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a este `accelerator` objeto.  
  
##  <a name="a-nameoperatoreqeqa-operator"></a><a name="operator_eq_eq"></a>operador == 

 Compara este `accelerator` objeto con otro y devuelve `true` si son iguales; en caso contrario, devuelve `false`.  
  
```  
bool operator== (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `accelerator` objeto que se va a comparar con éste.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el otro `accelerator` es igual que este objeto `accelerator` objeto; en caso contrario, `false`.  
  
##  <a name="a-namesetdefaulta-setdefault"></a><a name="set_default"></a>set_default 

 Establece el Acelerador predeterminado que se usará para cualquier operación que utiliza implícitamente el Acelerador predeterminado. Este método solo se realiza correctamente si el Acelerador de tiempo de ejecución predeterminado seleccionado ya no se ha utilizado en una operación que utiliza implícitamente el Acelerador predeterminado  
  
```  
static inline bool set_default(std::wstring _Path);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Path`  
 La ruta de acceso para el acelerador.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si la llamada se realiza correctamente en la configuración del Acelerador predeterminado. En caso contrario, es `false`.  
  
##  <a name="a-namesetdefaultcpuaccesstypea-setdefaultcpuaccesstype"></a><a name="set_default_cpu_access_type"></a>set_default_cpu_access_type 

 Establezca la cpu de predeterminado access_type () para matrices creadas en este acelerador o para asignaciones de memoria implícita como parte de array_views acceder a él en este este acelerador. Este método solo se realiza correctamente si el default_cpu_access_type para el Acelerador no ha sido ya reemplaza por una llamada anterior a este método y el default_cpu_access_type en tiempo de ejecución seleccionado para este acelerador todavía no ha usado para asignar una matriz o una asignación de memoria implícita un array_view tiene acceso en este acelerador de seguridad.  
  
```  
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Default_cpu_access_type`  
 Parámetro access_type de cpu de predeterminada que se usará para las asignaciones de memoria de matriz/array_view en este acelerador.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor booleano que indica si la cpu de predeterminado access_type () para que el Acelerador se estableció correctamente.  
  
##  <a name="a-namesupportscpusharedmemorya-supportscpusharedmemory"></a><a name="supports_cpu_shared_memory"></a>supports_cpu_shared_memory 

 Obtiene un valor booleano que indica si la `accelerator` es compatible con la memoria compartida.  
  
```  
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;  
```  
  
##  <a name="a-namesupportsdoubleprecisiona-supportsdoubleprecision"></a><a name="supports_double_precision"></a>supports_double_precision 

 Obtiene un valor booleano que indica si el Acelerador admite matemáticas de doble precisión.  
  
```  
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;  
```  
  
##  <a name="a-namesupportslimiteddoubleprecisiona-supportslimiteddoubleprecision"></a><a name="supports_limited_double_precision"></a>supports_limited_double_precision 

 Obtiene un valor booleano que indica si el acelerador proporciona compatibilidad limitada para matemáticas de precisión doble. Si el acelerador tiene sólo una compatibilidad limitada, a continuación, fundida multiplicar agregar (FMA), división, recíproco y la conversión entre `int` y `double` no son compatibles.  
  
```  
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;  
```  
  
##  <a name="a-nameversiona-version"></a><a name="version"></a>Versión 

 Obtiene la versión de la `accelerator`.  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
##  <a name="dtor"></a></a> ~ accelerator_view 

 Destruye el [accelerator_view](accelerator-view-class.md) objeto.  
  
```  
~accelerator_view();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="a-nameacceleratora-accelerator"></a><a name="accelerator"></a>Acelerador 

 Obtiene el `accelerator` el objeto para el [accelerator_view](accelerator-view-class.md) objeto.  
  
```  
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;  
```  
  
##  <a name="a-namectora-acceleratorview"></a><a name="ctor"></a>accelerator_view 

 Inicializa una nueva instancia de la [accelerator_view](accelerator-view-class.md) clase copiando una existente `accelerator_view` objeto.  
  
```  
accelerator_view(const accelerator_view& _Other);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `accelerator_view` objeto que se va a copiar.  
  
##  <a name="a-namecreatemarkera-createmarker"></a><a name="create_marker"></a>create_marker 

 Devuelve un futuro para realizar un seguimiento de la finalización de todos los comandos enviados hasta ahora a este `accelerator_view` objeto.  
  
```  
concurrency::completion_future create_marker();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un futuro para realizar el seguimiento de la finalización de todos los comandos enviados hasta ahora a este `accelerator_view` objeto.  
  
##  <a name="a-nameflusha-flush"></a><a name="flush"></a>Vaciar 

 Envía todos los comandos pendientes en cola para la [accelerator_view](accelerator-view-class.md) objeto para el Acelerador para su ejecución.  
  
```  
void flush();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `void`.  
  
##  <a name="a-namegetacceleratora-getaccelerator"></a><a name="get_accelerator"></a>get_accelerator 

 Devuelve el `accelerator` el objeto para el [accelerator_view](accelerator-view-class.md) objeto.  
  
```  
accelerator get_accelerator() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El `accelerator` el objeto para el `accelerator_view` objeto.  
  
##  <a name="a-namegetisautoselectiona-getisautoselection"></a><a name="get_is_auto_selection"></a>get_is_auto_selection 

 Devuelve un valor booleano que indica si el tiempo de ejecución selecciona automáticamente un acelerador adecuado cuando se pasa el accelerator_view a una [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each).  
  
```  
bool get_is_auto_selection() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el tiempo de ejecución selecciona automáticamente un acelerador adecuado; de lo contrario, `false`.  
  
##  <a name="a-namegetisdebuga-getisdebug"></a><a name="get_is_debug"></a>get_is_debug 

 Devuelve un valor booleano que indica si la [accelerator_view](accelerator-view-class.md) objeto tiene la capa de depuración habilitada para los informes de error importante.  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor booleano que indica si la `accelerator_view` objeto tiene la capa de depuración habilitada para los informes de error importante.  
  
##  <a name="a-namegetqueuingmodea-getqueuingmode"></a><a name="get_queuing_mode"></a>get_queuing_mode 

 Devuelve el modo de cola para la [accelerator_view](accelerator-view-class.md) objeto.  
  
```  
queuing_mode get_queuing_mode() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de cola para el `accelerator_view` objeto.  
  
##  <a name="a-namegetversiona-getversion"></a><a name="get_version"></a>get_version 

 Devuelve la versión de la [accelerator_view](accelerator-view-class.md).  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 La versión de la `accelerator_view`.  
  
##  <a name="a-nameisautoselectiona-isautoselection"></a><a name="is_auto_selection"></a>is_auto_selection 

 Obtiene un valor booleano que indica si el tiempo de ejecución selecciona automáticamente un acelerador adecuado cuando se pasa el accelerator_view a una [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each).  
  
```  
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;  
```  
  
##  <a name="a-nameisdebuga-isdebug"></a><a name="is_debug"></a>is_debug 

 Obtiene un valor booleano que indica si la [accelerator_view](accelerator-view-class.md) objeto tiene la capa de depuración habilitada para los informes de error importante.  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="a-nameoperatorneqa-operator"></a><a name="operator_neq"></a>operador! = 

 Compara este [accelerator_view](accelerator-view-class.md) objeto con otro y devuelve `false` si son iguales; en caso contrario, devuelve `true`.  
  
```  
bool operator!= (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `accelerator_view` objeto que se va a comparar con éste.  
  
### <a name="return-value"></a>Valor devuelto  
 `false` si los dos objetos son iguales; de lo contrario, `true`.  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>operador = 

 Copia el contenido del elemento [accelerator_view](accelerator-view-class.md) objeto en éste.  
  
```  
accelerator_view& operator= (const accelerator_view& _Other);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `accelerator_view` objeto que se va a copiar de.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la modificación `accelerator_view` objeto.  
  
##  <a name="a-nameoperatoreqeqa-operator"></a><a name="operator_eq_eq"></a>operador == 

 Compara este [accelerator_view](accelerator-view-class.md) objeto con otro y devuelve `true` si son iguales; en caso contrario, devuelve `false`.  
  
```  
bool operator== (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `accelerator_view` objeto que se va a comparar con éste.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si los dos objetos son iguales; de lo contrario, `false`.  
  
##  <a name="a-namequeuingmodea-queuingmode"></a><a name="queuing_mode"></a>queuing_mode 

 Obtiene el modo de cola para la [accelerator_view](accelerator-view-class.md) objeto.  
  
```  
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;  
```  
  
##  <a name="a-nameversiona-version"></a><a name="version"></a>Versión 

 Obtiene la versión de la [accelerator_view](accelerator-view-class.md).  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
##  <a name="a-namewaita-wait"></a><a name="wait"></a>esperar 

 Espera a que todos los comandos que se envían a la [accelerator_view](accelerator-view-class.md) objeto que se va a finalizar.  
  
```  
void wait();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `void`.  
  
## <a name="see-also"></a>Vea también  
 [Namespace de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)

