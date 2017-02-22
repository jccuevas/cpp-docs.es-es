---
title: "accelerator (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amprt/Concurrency::accelerator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "accelerator (clase)"
ms.assetid: 37eed593-cf87-4611-9cdc-e98df6c2377a
caps.latest.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# accelerator (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Un acelerador es una capacidad de hardware que está optimizada para la informática paralela de los datos. Una tecla de aceleración puede ser un dispositivo conectado a un bus de PCIe (por ejemplo, una GPU), o puede ser una instrucción extendida establecer en la CPU principal.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class accelerator;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Constructor de Accelerator::Accelerator](#accelerator__accelerator_constructor)|Inicializa una nueva instancia de la clase `accelerator`.|  
|[Accelerator:: ~ accelerator (destructor)](#accelerator___dtoraccelerator_destructor)|Destruye el objeto `accelerator`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Accelerator:: CREATE_VIEW (método)](#accelerator__create_view_method)|Crea y devuelve un `accelerator_view` objeto en este acelerador.|  
|[Accelerator:: get_all (método)](#accelerator__get_all_method)|Devuelve un vector de `accelerator` objetos que representan todos los aceleradores disponibles.|  
|[Accelerator:: get_auto_selection_view (método)](#accelerator__get_auto_selection_view_method)|Devuelve la selección automática de `accelerator_view`.|  
|[Accelerator:: get_dedicated_memory (método)](#accelerator__get_dedicated_memory_method)|Devuelve la memoria dedicada para la `accelerator`, en kilobytes.|  
|[Accelerator:: get_default_cpu_access_type (método)](#accelerator__get_default_cpu_access_type_method)|Devuelve el valor predeterminado [access_type ()](../Topic/concurrency%20namespace%20enums.md#access_type) de búferes creados en este acelerador.|  
|[Accelerator:: get_default_view (método)](#accelerator__get_default_view_method)|Devuelve el valor predeterminado `accelerator_view` objeto que está asociado el `accelerator`.|  
|[Accelerator:: get_description (método)](#accelerator__get_description_method)|Devuelve una breve descripción de la `accelerator` dispositivo.|  
|[Accelerator:: get_device_path (método)](#accelerator__get_device_path_method)|Devuelve la ruta de acceso del dispositivo.|  
|[Accelerator:: get_has_display (método)](#accelerator__get_has_display_method)|Determina si el `accelerator` se adjunta a una pantalla.|  
|[Accelerator:: get_is_debug (método)](#accelerator__get_is_debug_method)|Determina si el `accelerator` tiene la capa de DEPURACIÓN habilitada para los informes de error importante.|  
|[Accelerator:: get_is_emulated (método)](#accelerator__get_is_emulated_method)|Determina si el `accelerator` se emula.|  
|[Accelerator:: get_supports_cpu_shared_memory (método)](#accelerator__get_supports_cpu_shared_memory_method)|Determina si la `accelerator` es compatible con memoria compartida|  
|[Accelerator:: get_supports_double_precision (método)](#accelerator__get_supports_double_precision_method)|Determina si el `accelerator` se adjunta a una pantalla.|  
|[Accelerator:: get_supports_limited_double_precision (método)](#accelerator__get_supports_limited_double_precision_method)|Determina si el `accelerator` proporciona compatibilidad limitada para matemáticas de precisión doble.|  
|[Accelerator:: get_version (método)](#accelerator__get_version_method)|Devuelve la versión de la `accelerator`.|  
|[Accelerator:: set_default (método)](#accelerator__set_default_method)|Devuelve la ruta de acceso del Acelerador predeterminado.|  
|[Accelerator:: set_default_cpu_access_type (método)](#accelerator__set_default_cpu_access_type_method)|Establece el valor predeterminado CPU [access_type ()](../Topic/concurrency%20namespace%20enums.md#access_type) para matrices y asignaciones de memoria implícitas realizadas en este `accelerator`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Accelerator:: operator! = (operador)](#accelerator__operator_neq_operator)|Compara este `accelerator` objeto con otro y devuelve `false` si son iguales; en caso contrario, devuelve `true`.|  
|[Accelerator:: operator = (operador)](#accelerator__operator_eq_operator)|Copia el contenido del elemento `accelerator` objeto a ésta.|  
|[Accelerator:: operator == (operador)](#accelerator__operator_eq_eq_operator)|Compara este `accelerator` objeto con otro y devuelve `true` si son iguales; en caso contrario, devuelve `false`.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Miembro de datos de Accelerator::cpu_accelerator](#accelerator__cpu_accelerator_data_member)|Obtiene una cadena constante para la CPU `accelerator`.|  
|[Miembro de datos de Accelerator::dedicated_memory](#accelerator__dedicated_memory_data_member)|Obtiene la memoria dedicada para la `accelerator`, en kilobytes.|  
|[Miembro de datos de Accelerator::default_accelerator](#accelerator__default_accelerator_data_member)|Obtiene una cadena constante para el valor predeterminado `accelerator`.|  
|[Miembro de datos de Accelerator::default_cpu_access_type](#accelerator__default_cpu_access_type_data_member)|Obtiene o establece el valor predeterminado CPU [access_type ()](../Topic/concurrency%20namespace%20enums.md#access_type) para matrices y asignaciones de memoria implícitas realizadas en este `accelerator`.|  
|[Miembro de datos de Accelerator::default_view](#accelerator__default_view_data_member)|Obtiene el valor predeterminado `accelerator_view` objeto que está asociado el `accelerator`.|  
|[Miembro de datos de Accelerator::Description](#accelerator__description_data_member)|Obtiene una breve descripción de la `accelerator` dispositivo.|  
|[Miembro de datos de Accelerator::device_path](#accelerator__device_path_data_member)|Obtiene la ruta de acceso del dispositivo.|  
|[Miembro de datos direct3d_ref](#accelerator__direct3d_ref_data_member)|Obtiene una cadena constante para una referencia de Direct3D `accelerator`.|  
|[Miembro de datos direct3d_warp](#accelerator__direct3d_warp_data_member)|Obtiene la cadena de constante para un [Acelerador](../../../parallel/amp/reference/accelerator-class.md) objeto que puede usar para ejecutar el código de C++ AMP en las CPU de varios núcleo que usan extensiones de SIMD de transmisión (SSE).|  
|[Miembro de datos de Accelerator::has_display](#accelerator__has_display_data_member)|Obtiene un valor booleano que indica si el `accelerator` se adjunta a una pantalla.|  
|[Miembro de datos de Accelerator::is_debug](#accelerator__is_debug_data_member)|Indica si la `accelerator` tiene la capa de DEPURACIÓN habilitada para los informes de error importante.|  
|[Miembro de datos de Accelerator::is_emulated](#accelerator__is_emulated_data_member)|Indica si el `accelerator` se emula.|  
|[Miembro de datos de Accelerator::supports_cpu_shared_memory](#accelerator__supports_cpu_shared_memory_data_member)|Indica si la `accelerator` es compatible con la memoria compartida.|  
|[Miembro de datos de Accelerator::supports_double_precision](#accelerator__supports_double_precision_data_member)|Indica si el Acelerador admite matemáticas de precisión doble.|  
|[Miembro de datos de Accelerator::supports_limited_double_precision](#accelerator__supports_limited_double_precision_data_member)|Indica si el acelerador proporciona compatibilidad limitada para matemáticas de precisión doble.|  
|[Miembro de datos de Accelerator::Version](#accelerator__version_data_member)|Obtiene la versión de la `accelerator`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `accelerator`  
  
## <a name="remarks"></a>Comentarios  
 Un acelerador es una capacidad de hardware que está optimizada para la informática paralela de los datos. Un acelerador suele ser una GPU, pero también puede ser una entidad del host virtual como un dispositivo de DirectX REF, una DEFORMACIÓN (un dispositivo de lado de CPU que se acelera por medio de instrucciones SSE) o la propia CPU.  
  
 Puede construir un `accelerator` objeto enumerando los dispositivos disponibles, u obteniendo el dispositivo de forma predeterminada, el dispositivo de referencia o el dispositivo WARP.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** Concurrency  
  
##  <a name="a-nameacceleratordtoracceleratordestructora-acceleratoraccelerator-destructor"></a><a name="accelerator___dtoraccelerator_destructor"></a>  Accelerator:: ~ accelerator (destructor)  
 Destruye el [Acelerador](../../../parallel/amp/reference/accelerator-class.md) objeto.  
  
```  
~accelerator();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="a-nameacceleratoracceleratorconstructora-acceleratoraccelerator-constructor"></a><a name="accelerator__accelerator_constructor"></a>  Constructor de Accelerator::Accelerator  
 Inicializa una nueva instancia de la [accelerator (clase)](../../../parallel/amp/reference/accelerator-class.md).  
  
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
  
##  <a name="a-nameacceleratorcpuacceleratordatamembera-acceleratorcpuaccelerator-data-member"></a><a name="accelerator__cpu_accelerator_data_member"></a>  Miembro de datos de Accelerator::cpu_accelerator  
 Obtiene una cadena constante para el Acelerador de CPU.  
  
```  
static const wchar_t cpu_accelerator[];  
```  
  
##  <a name="a-nameacceleratorcreateviewmethoda-acceleratorcreateview-method"></a><a name="accelerator__create_view_method"></a>  Accelerator:: CREATE_VIEW (método)  
 Crea y devuelve un `accelerator_view` objeto en este acelerador, utilizando el modo de cola especificado. Cuando no se especifica el modo de cola, la nueva `accelerator_view` utiliza el [queuing_mode::immediate](../Topic/concurrency%20namespace%20enums.md#queuing_mode) modo de cola.  
  
```  
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```  
  
### <a name="parameters"></a>Parámetros  
 `qmode`  
 El modo de cola.  
  
### <a name="return-value"></a>Valor devuelto  
 Un nuevo `accelerator_view` objeto en este acelerador, utilizando el modo de cola especificado.  
  
##  <a name="a-nameacceleratordedicatedmemorydatamembera-acceleratordedicatedmemory-data-member"></a><a name="accelerator__dedicated_memory_data_member"></a>  Miembro de datos de Accelerator::dedicated_memory  
 Obtiene la memoria dedicada para la [Acelerador](../../../parallel/amp/reference/accelerator-class.md), en kilobytes.  
  
```  
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;  
```  
  
##  <a name="a-nameacceleratordefaultacceleratordatamembera-acceleratordefaultaccelerator-data-member"></a><a name="accelerator__default_accelerator_data_member"></a>  Miembro de datos de Accelerator::default_accelerator  
 Obtiene una cadena constante para el valor predeterminado [Acelerador](../../../parallel/amp/reference/accelerator-class.md).  
  
```  
static const wchar_t default_accelerator[];  
```  
  
##  <a name="a-nameacceleratordefaultcpuaccesstypedatamembera-acceleratordefaultcpuaccesstype-data-member"></a><a name="accelerator__default_cpu_access_type_data_member"></a>  Miembro de datos de Accelerator::default_cpu_access_type  
 El valor predeterminado cpu [access_type ()](../Topic/concurrency%20namespace%20enums.md#access_type) para matrices y asignaciones de memoria implícitas realizadas en esta este `accelerator`.  
  
```  
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;  
```  
  
##  <a name="a-nameacceleratordefaultviewdatamembera-acceleratordefaultview-data-member"></a><a name="accelerator__default_view_data_member"></a>  Miembro de datos de Accelerator::default_view  
 Obtiene la vista de acelerador predeterminado que está asociada el [Acelerador](../../../parallel/amp/reference/accelerator-class.md).  
  
```  
__declspec(property(get= get_default_view)) accelerator_view default_view;  
```  
  
##  <a name="a-nameacceleratordescriptiondatamembera-acceleratordescription-data-member"></a><a name="accelerator__description_data_member"></a>  Miembro de datos de Accelerator::Description  
 Obtiene una breve descripción de la [Acelerador](../../../parallel/amp/reference/accelerator-class.md) dispositivo.  
  
```  
__declspec(property(get= get_description)) std::wstring description;  
```  
  
##  <a name="a-nameacceleratordevicepathdatamembera-acceleratordevicepath-data-member"></a><a name="accelerator__device_path_data_member"></a>  Miembro de datos de Accelerator::device_path  
 Obtiene la ruta de acceso del acelerador. La ruta de acceso es único en el sistema.  
  
```  
__declspec(property(get= get_device_path)) std::wstring device_path;  
```  
  
##  <a name="a-nameacceleratordirect3drefdatamembera-acceleratordirect3dref-data-member"></a><a name="accelerator__direct3d_ref_data_member"></a>  Miembro de datos direct3d_ref  
 Obtiene una cadena constante para un acelerador de referencia de Direct3D.  
  
```  
static const wchar_t direct3d_ref[];  
```  
  
##  <a name="a-nameacceleratordirect3dwarpdatamembera-acceleratordirect3dwarp-data-member"></a><a name="accelerator__direct3d_warp_data_member"></a>  Miembro de datos direct3d_warp  
 Obtiene la cadena de constante para un [Acelerador](../../../parallel/amp/reference/accelerator-class.md) objeto que puede usar para ejecutar el código de C++ AMP en las CPU de varios núcleo con extensiones SIMD de transmisión (SSE).  
  
```  
static const wchar_t direct3d_warp[];  
```  
  
##  <a name="a-nameacceleratorgetallmethoda-acceleratorgetall-method"></a><a name="accelerator__get_all_method"></a>  Accelerator:: get_all (método)  
 Devuelve un vector de `accelerator` objetos que representan todos los aceleradores disponibles.  
  
```  
static inline std::vector<accelerator> get_all();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El vector de aceleradores disponibles  
  
##  <a name="a-nameacceleratorgetautoselectionviewmethoda-acceleratorgetautoselectionview-method"></a><a name="accelerator__get_auto_selection_view_method"></a>  Accelerator:: get_auto_selection_view (método)  
 Devuelve el accelerator_view de selección automática, que, cuando especifica que los resultados de destino parallel_for_each en el accelerator_view de destino para ejecutar el kernel parallel_for_each seleccionarse automáticamente en tiempo de ejecución. Para todos los demás casos, la accelerator_view devuelta por este método es igual que el accelerator_view predeterminada del Acelerador predeterminado  
  
```  
static accelerator_view __cdecl get_auto_selection_view();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El accelerator_view de selección automática.  
  
##  <a name="a-nameacceleratorgetdedicatedmemorymethoda-acceleratorgetdedicatedmemory-method"></a><a name="accelerator__get_dedicated_memory_method"></a>  Accelerator:: get_dedicated_memory (método)  
 Devuelve la memoria dedicada para la [Acelerador](../../../parallel/amp/reference/accelerator-class.md), en kilobytes.  
  
```  
size_t get_dedicated_memory() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 La memoria dedicada para la `accelerator`, en kilobytes.  
  
##  <a name="a-nameacceleratorgetdefaultcpuaccesstypemethoda-acceleratorgetdefaultcpuaccesstype-method"></a><a name="accelerator__get_default_cpu_access_type_method"></a>  Accelerator:: get_default_cpu_access_type (método)  
 Obtiene la cpu de forma predeterminada, access_type () para los búferes creados en este acelerador  
  
```  
access_type get_default_cpu_access_type() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Parámetro access_type de cpu de predeterminado para los búferes creados en este acelerador.  
  
##  <a name="a-nameacceleratorgetdefaultviewmethoda-acceleratorgetdefaultview-method"></a><a name="accelerator__get_default_view_method"></a>  Accelerator:: get_default_view (método)  
 Devuelve el valor predeterminado `accelerator_view` objeto que está asociado el [Acelerador](../../../parallel/amp/reference/accelerator-class.md).  
  
```  
accelerator_view get_default_view() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor predeterminado `accelerator_view` objeto que está asociado el `accelerator`.  
  
##  <a name="a-nameacceleratorgetdescriptionmethoda-acceleratorgetdescription-method"></a><a name="accelerator__get_description_method"></a>  Accelerator:: get_description (método)  
 Devuelve una breve descripción de la [Acelerador](../../../parallel/amp/reference/accelerator-class.md) dispositivo.  
  
```  
std::wstring get_description() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una breve descripción de la `accelerator` dispositivo.  
  
##  <a name="a-nameacceleratorgetdevicepathmethoda-acceleratorgetdevicepath-method"></a><a name="accelerator__get_device_path_method"></a>  Accelerator:: get_device_path (método)  
 Devuelve la ruta de acceso del acelerador. La ruta de acceso es único en el sistema.  
  
```  
std::wstring get_device_path() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 La ruta de acceso de la instancia de dispositivo único de todo el sistema.  
  
##  <a name="a-nameacceleratorgethasdisplaymethoda-acceleratorgethasdisplay-method"></a><a name="accelerator__get_has_display_method"></a>  Accelerator:: get_has_display (método)  
 Devuelve un valor booleano que indica si la [Acelerador](../../../parallel/amp/reference/accelerator-class.md) puede enviar a una pantalla.  
  
```  
bool get_has_display() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el `accelerator` puede enviar a una pantalla; en caso contrario, `false`.  
  
##  <a name="a-nameacceleratorgetisdebugmethoda-acceleratorgetisdebug-method"></a><a name="accelerator__get_is_debug_method"></a>  Accelerator:: get_is_debug (método)  
 Determina si el [Acelerador](../../../parallel/amp/reference/accelerator-class.md) tiene la capa de DEPURACIÓN habilitada para los informes de error importante.  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el `accelerator` tiene la capa de DEPURACIÓN habilitada para los informes de error importante. En caso contrario, es `false`.  
  
##  <a name="a-nameacceleratorgetisemulatedmethoda-acceleratorgetisemulated-method"></a><a name="accelerator__get_is_emulated_method"></a>  Accelerator:: get_is_emulated (método)  
 Determina si el [Acelerador](../../../parallel/amp/reference/accelerator-class.md) se emula.  
  
```  
bool get_is_emulated() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el `accelerator` se emula. En caso contrario, es `false`.  
  
##  <a name="a-nameacceleratorgetsupportscpusharedmemorymethoda-acceleratorgetsupportscpusharedmemory-method"></a><a name="accelerator__get_supports_cpu_shared_memory_method"></a>  Accelerator:: get_supports_cpu_shared_memory (método)  
 Devuelve un valor booleano que indica si el Acelerador admite memoria accesible el acelerador y la CPU.  
  
```  
bool get_supports_cpu_shared_memory() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el acelerador es compatible con memoria compartida de CPU; de lo contrario, `false`.  
  
##  <a name="a-nameacceleratorgetsupportsdoubleprecisionmethoda-acceleratorgetsupportsdoubleprecision-method"></a><a name="accelerator__get_supports_double_precision_method"></a>  Accelerator:: get_supports_double_precision (método)  
 Devuelve un valor booleano que indica si el Acelerador admite matemáticas de precisión doble, incluidos fusionada multiplicar agrega (FMA), división, recíproco y la conversión entre `int` y `double`.  
  
```  
bool get_supports_double_precision() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el Acelerador admite double matemáticas de precisión; de lo contrario, `false`.  
  
##  <a name="a-nameacceleratorgetsupportslimiteddoubleprecisionmethoda-acceleratorgetsupportslimiteddoubleprecision-method"></a><a name="accelerator__get_supports_limited_double_precision_method"></a>  Accelerator:: get_supports_limited_double_precision (método)  
 Devuelve un valor booleano que indica si el acelerador proporciona compatibilidad limitada para matemáticas de precisión doble. Si el acelerador tiene sólo una compatibilidad limitada, a continuación, fundida multiplicar agregar (FMA), división, recíproco y la conversión entre `int` y `double` no son compatibles.  
  
```  
bool get_supports_limited_double_precision() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el acelerador proporciona compatibilidad limitada para double matemáticas de precisión; de lo contrario, `false`.  
  
##  <a name="a-nameacceleratorgetversionmethoda-acceleratorgetversion-method"></a><a name="accelerator__get_version_method"></a>  Accelerator:: get_version (método)  
 Devuelve la versión de la [Acelerador](../../../parallel/amp/reference/accelerator-class.md).  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 La versión de la `accelerator`.  
  
##  <a name="a-nameacceleratorhasdisplaydatamembera-acceleratorhasdisplay-data-member"></a><a name="accelerator__has_display_data_member"></a>  Miembro de datos de Accelerator::has_display  
 Obtiene un valor booleano que indica si la [Acelerador](../../../parallel/amp/reference/accelerator-class.md) puede enviar a una pantalla.  
  
```  
__declspec(property(get= get_has_display)) bool has_display;  
```  
  
##  <a name="a-nameacceleratorisdebugdatamembera-acceleratorisdebug-data-member"></a><a name="accelerator__is_debug_data_member"></a>  Miembro de datos de Accelerator::is_debug  
 Obtiene un valor booleano que indica si la [Acelerador](../../../parallel/amp/reference/accelerator-class.md) tiene la capa de DEPURACIÓN habilitada para los informes de error importante.  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="a-nameacceleratorisemulateddatamembera-acceleratorisemulated-data-member"></a><a name="accelerator__is_emulated_data_member"></a>  Miembro de datos de Accelerator::is_emulated  
 Obtiene un valor booleano que indica si la [Acelerador](../../../parallel/amp/reference/accelerator-class.md) se emula.  
  
```  
__declspec(property(get= get_is_emulated)) bool is_emulated;  
```  
  
##  <a name="a-nameacceleratoroperatorneqoperatora-acceleratoroperator-operator"></a><a name="accelerator__operator_neq_operator"></a>  Accelerator:: operator! = (operador)  
 Compara este `accelerator` objeto con otro y devuelve `false` si son iguales; en caso contrario, devuelve `true`.  
  
```  
bool operator!= (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `accelerator` objeto que se va a comparar con éste.  
  
### <a name="return-value"></a>Valor devuelto  
 `false` Si los dos `accelerator` objetos son iguales; en caso contrario, `true`.  
  
##  <a name="a-nameacceleratoroperatoreqoperatora-acceleratoroperator-operator"></a><a name="accelerator__operator_eq_operator"></a>  Accelerator:: operator = (operador)  
 Copia el contenido del elemento [Acelerador](../../../parallel/amp/reference/accelerator-class.md) objeto a ésta.  
  
```  
accelerator& operator= (const accelerator& _Other);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `accelerator` objeto que se va a copiar de.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a este `accelerator` objeto.  
  
##  <a name="a-nameacceleratoroperatoreqeqoperatora-acceleratoroperator-operator"></a><a name="accelerator__operator_eq_eq_operator"></a>  Accelerator:: operator == (operador)  
 Compara este [Acelerador](../../../parallel/amp/reference/accelerator-class.md) objeto con otro y devuelve `true` si son iguales; en caso contrario, devuelve `false`.  
  
```  
bool operator== (const accelerator& _Other) const;

 
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `accelerator` objeto que se va a comparar con éste.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el otro `accelerator` es igual que este objeto `accelerator` objeto; en caso contrario, `false`.  
  
##  <a name="a-nameacceleratorsetdefaultmethoda-acceleratorsetdefault-method"></a><a name="accelerator__set_default_method"></a>  Accelerator:: set_default (método)  
 Establece el Acelerador predeterminado que se usará para cualquier operación que utiliza implícitamente el Acelerador predeterminado. Este método solo se realiza correctamente si el Acelerador de tiempo de ejecución predeterminado seleccionado ya no se ha utilizado en una operación que utiliza implícitamente el Acelerador predeterminado  
  
```  
static inline bool set_default(std::wstring _Path);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Path`  
 La ruta de acceso para el acelerador.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si la llamada se realiza correctamente en la configuración del Acelerador predeterminado. En caso contrario, es `false`.  
  
##  <a name="a-nameacceleratorsetdefaultcpuaccesstypemethoda-acceleratorsetdefaultcpuaccesstype-method"></a><a name="accelerator__set_default_cpu_access_type_method"></a>  Accelerator:: set_default_cpu_access_type (método)  
 Establezca la cpu de predeterminado access_type () para matrices creadas en este acelerador o para asignaciones de memoria implícita como parte de array_views acceder a él en este este acelerador. Este método solo se realiza correctamente si el default_cpu_access_type para el Acelerador no ha sido ya reemplaza por una llamada anterior a este método y el default_cpu_access_type en tiempo de ejecución seleccionado para este acelerador todavía no ha usado para asignar una matriz o una asignación de memoria implícita un array_view tiene acceso en este acelerador de seguridad.  
  
```  
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Default_cpu_access_type`  
 Parámetro access_type de cpu de predeterminada que se usará para las asignaciones de memoria de matriz/array_view en este acelerador.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor booleano que indica si la cpu de predeterminado access_type () para que el Acelerador se estableció correctamente.  
  
##  <a name="a-nameacceleratorsupportscpusharedmemorydatamembera-acceleratorsupportscpusharedmemory-data-member"></a><a name="accelerator__supports_cpu_shared_memory_data_member"></a>  Miembro de datos de Accelerator::supports_cpu_shared_memory  
 Obtiene un valor booleano que indica si la `accelerator` es compatible con la memoria compartida.  
  
```  
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;  
```  
  
##  <a name="a-nameacceleratorsupportsdoubleprecisiondatamembera-acceleratorsupportsdoubleprecision-data-member"></a><a name="accelerator__supports_double_precision_data_member"></a>  Miembro de datos de Accelerator::supports_double_precision  
 Obtiene un valor booleano que indica si el Acelerador admite matemáticas de doble precisión.  
  
```  
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;  
```  
  
##  <a name="a-nameacceleratorsupportslimiteddoubleprecisiondatamembera-acceleratorsupportslimiteddoubleprecision-data-member"></a><a name="accelerator__supports_limited_double_precision_data_member"></a>  Miembro de datos de Accelerator::supports_limited_double_precision  
 Obtiene un valor booleano que indica si el acelerador proporciona compatibilidad limitada para matemáticas de precisión doble. Si el acelerador tiene sólo una compatibilidad limitada, a continuación, fundida multiplicar agregar (FMA), división, recíproco y la conversión entre `int` y `double` no son compatibles.  
  
```  
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;  
```  
  
##  <a name="a-nameacceleratorversiondatamembera-acceleratorversion-data-member"></a><a name="accelerator__version_data_member"></a>  Miembro de datos de Accelerator::Version  
 Obtiene la versión de la [Acelerador](../../../parallel/amp/reference/accelerator-class.md).  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
##  <a name="a-nameacceleratorviewdtoracceleratorviewdestructora-acceleratorviewacceleratorview-destructor"></a><a name="accelerator_view___dtoraccelerator_view_destructor"></a>  accelerator_view:: ~ accelerator_view (destructor)  
 Destruye el [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto.  
  
```  
~accelerator_view();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="a-nameacceleratorviewacceleratordatamembera-acceleratorviewaccelerator-data-member"></a><a name="accelerator_view__accelerator_data_member"></a>  Miembro de datos de accelerator_view::Accelerator  
 Obtiene el [Acelerador](../../../parallel/amp/reference/accelerator-class.md) de objeto para el [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto.  
  
```  
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;  
```  
  
##  <a name="a-nameacceleratorviewacceleratorviewconstructora-acceleratorviewacceleratorview-constructor"></a><a name="accelerator_view__accelerator_view_constructor"></a>  Constructor de accelerator_view::accelerator_view  
 Inicializa una nueva instancia de la [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) clase copiando una existente `accelerator_view` objeto.  
  
```  
accelerator_view(const accelerator_view& _Other);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `accelerator_view` objeto que se va a copiar.  
  
##  <a name="a-nameacceleratorviewcreatemarkermethoda-acceleratorviewcreatemarker-method"></a><a name="accelerator_view__create_marker_method"></a>  accelerator_view:: create_marker (método)  
 Devuelve un futuro para realizar un seguimiento de la finalización de todos los comandos enviados hasta ahora a este `accelerator_view` objeto.  
  
```  
concurrency::completion_future create_marker();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un futuro para realizar el seguimiento de la finalización de todos los comandos enviados hasta ahora a este `accelerator_view` objeto.  
  
##  <a name="a-nameacceleratorviewflushmethoda-acceleratorviewflush-method"></a><a name="accelerator_view__flush_method"></a>  accelerator_view:: Flush (método)  
 Envía todos los comandos pendientes en cola para la [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto para el Acelerador para su ejecución.  
  
```  
void flush();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `void`.  
  
##  <a name="a-nameacceleratorviewgetacceleratormethoda-acceleratorviewgetaccelerator-method"></a><a name="accelerator_view__get_accelerator_method"></a>  accelerator_view:: get_accelerator (método)  
 Devuelve el [Acelerador](../../../parallel/amp/reference/accelerator-class.md) de objeto para el [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto.  
  
```  
accelerator get_accelerator() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El `accelerator` de objeto para el `accelerator_view` objeto.  
  
##  <a name="a-nameacceleratorviewgetisautoselectionmethoda-acceleratorviewgetisautoselection-method"></a><a name="accelerator_view__get_is_auto_selection_method"></a>  accelerator_view:: get_is_auto_selection (método)  
 Devuelve un valor booleano que indica si el tiempo de ejecución selecciona automáticamente un acelerador adecuado cuando se pasa el accelerator_view a una [parallel_for_each](../Topic/concurrency%20namespace%20functions.md#parallel_for_each).  
  
```  
bool get_is_auto_selection() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el tiempo de ejecución selecciona automáticamente un acelerador adecuado; de lo contrario, `false`.  
  
##  <a name="a-nameacceleratorviewgetisdebugmethoda-acceleratorviewgetisdebug-method"></a><a name="accelerator_view__get_is_debug_method"></a>  accelerator_view:: get_is_debug (método)  
 Devuelve un valor booleano que indica si la [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto tiene la capa de DEPURACIÓN habilitada para los informes de error importante.  
  
```  
bool get_is_debug() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor booleano que indica si la `accelerator_view` objeto tiene la capa de DEPURACIÓN habilitada para los informes de error importante.  
  
##  <a name="a-nameacceleratorviewgetqueuingmodemethoda-acceleratorviewgetqueuingmode-method"></a><a name="accelerator_view__get_queuing_mode_method"></a>  accelerator_view:: get_queuing_mode (método)  
 Devuelve el modo de cola para la [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto.  
  
```  
queuing_mode get_queuing_mode() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de cola para el `accelerator_view` objeto.  
  
##  <a name="a-nameacceleratorviewgetversionmethoda-acceleratorviewgetversion-method"></a><a name="accelerator_view__get_version_method"></a>  accelerator_view:: get_version (método)  
 Devuelve la versión de la [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md).  
  
```  
unsigned int get_version() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 La versión de la `accelerator_view`.  
  
##  <a name="a-nameacceleratorviewisautoselectiondatamembera-acceleratorviewisautoselection-data-member"></a><a name="accelerator_view__is_auto_selection_data_member"></a>  Miembro de datos de accelerator_view::is_auto_selection  
 Obtiene un valor booleano que indica si el tiempo de ejecución selecciona automáticamente un acelerador adecuado cuando se pasa el accelerator_view a una [parallel_for_each](concurrency%20namespace%20functions.md#parallel_for_each).  
  
```  
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;  
```  
  
##  <a name="a-nameacceleratorviewisdebugdatamembera-acceleratorviewisdebug-data-member"></a><a name="accelerator_view__is_debug_data_member"></a>  Miembro de datos de accelerator_view::is_debug  
 Obtiene un valor booleano que indica si la [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto tiene la capa de DEPURACIÓN habilitada para los informes de error importante.  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
##  <a name="a-nameacceleratorviewoperatorneqoperatora-acceleratorviewoperator-operator"></a><a name="accelerator_view__operator_neq_operator"></a>  accelerator_view:: operator! = (operador)  
 Compara este [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto con otro y devuelve `false` si son iguales; en caso contrario, devuelve `true`.  
  
```  
bool operator!= (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `accelerator_view` objeto que se va a comparar con éste.  
  
### <a name="return-value"></a>Valor devuelto  
 `false` si los dos objetos son iguales; de lo contrario, `true`.  
  
##  <a name="a-nameacceleratorviewoperatoreqoperatora-acceleratorviewoperator-operator"></a><a name="accelerator_view__operator_eq_operator"></a>  accelerator_view:: operator = (operador)  
 Copia el contenido del elemento [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto en éste.  
  
```  
accelerator_view& operator= (const accelerator_view& _Other);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `accelerator_view` objeto que se va a copiar de.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la modificación `accelerator_view` objeto.  
  
##  <a name="a-nameacceleratorviewoperatoreqeqoperatora-acceleratorviewoperator-operator"></a><a name="accelerator_view__operator_eq_eq_operator"></a>  accelerator_view:: operator == (operador)  
 Compara este [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto con otro y devuelve `true` si son iguales; en caso contrario, devuelve `false`.  
  
```  
bool operator== (const accelerator_view& _Other) const;

 
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `accelerator_view` objeto que se va a comparar con éste.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si los dos objetos son iguales; de lo contrario, `false`.  
  
##  <a name="a-nameacceleratorviewqueuingmodedatamembera-acceleratorviewqueuingmode-data-member"></a><a name="accelerator_view__queuing_mode_data_member"></a>  Miembro de datos de accelerator_view::queuing_mode  
 Obtiene el modo de cola para la [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto.  
  
```  
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;  
```  
  
##  <a name="a-nameacceleratorviewversiondatamembera-acceleratorviewversion-data-member"></a><a name="accelerator_view__version_data_member"></a>  Miembro de datos de accelerator_view::Version  
 Obtiene la versión de la [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md).  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
##  <a name="a-nameacceleratorviewwaitmethoda-acceleratorviewwait-method"></a><a name="accelerator_view__wait_method"></a>  accelerator_view:: Wait (método)  
 Espera a que todos los comandos que se envían a la [accelerator_view](../../../parallel/amp/reference/accelerator-view-class.md) objeto que se va a finalizar.  
  
```  
void wait();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `void`.  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de simultaneidad (C++ AMP)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)
