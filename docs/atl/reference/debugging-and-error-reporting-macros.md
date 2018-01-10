---
title: "Macros de informes de errores y depuración | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atldef/ATL::_ATL_DEBUG_INTERFACES
- atldef/ATL::_ATL_DEBUG_QI
- atldef/ATL::ATLASSERT
- afx/ATL::ATLENSURE
- atltrace/ATL::ATLTRACENOTIMPL
- atltrace/ATL::ATLTRACE
dev_langs: C++
helpviewer_keywords: macros, error reporting
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9098b944f70ab4e4448fe40aa2347b0128e6e1a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="debugging-and-error-reporting-macros"></a>Macros de informes de errores y depuración
Estas macros proporcionan funciones de seguimiento y depuración útiles.  
  
|||  
|-|-|  
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|Escribe, en la ventana de salida, cualquier interfaz pérdidas que se detectan cuando `_Module.Term` se llama.|  
|[_ATL_DEBUG_QI](#_atl_debug_qi)|Escribe todas las llamadas a `QueryInterface` en la ventana de salida.|  
|[ATLASSERT](#atlassert)|Realiza la misma funcionalidad que la [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) macro que encontró en la biblioteca de tiempo de ejecución de C.|  
|[ATLENSURE](#atlensure)|Realiza la validación de parámetros. Llamar a `AtlThrow` si es necesario|  
|[ATLTRACENOTIMPL](#atltracenotimpl)|Envía un mensaje en el dispositivo de volcado de memoria que no se implementa la función especificada.|  
|[ATLTRACE](#alttrace)|Informa de advertencias en un dispositivo de salida, como la ventana del depurador, según las marcas indicados y los niveles. Se incluye por compatibilidad con versiones anteriores.|  
|[ATLTRACE2](#atltrace2)|Informa de advertencias en un dispositivo de salida, como la ventana del depurador, según las marcas indicados y los niveles.|  
  
##  <a name="_atl_debug_interfaces"></a>_ATL_DEBUG_INTERFACES  
 Definir esta macro antes de incluir los archivos de encabezado ATL para realizar el seguimiento de todos los `AddRef` y **versión** llama en interfaces de los componentes en la ventana de salida.  
  
```
#define _ATL_DEBUG_INTERFACES
```  
  
### <a name="remarks"></a>Comentarios  
 El resultado del seguimiento aparecerán como se muestra a continuación:  
  
 `ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`  
  
 La primera parte de cada seguimiento siempre será `ATL: QIThunk`. A continuación figura un valor que identifica ese *código thunk de la interfaz* que se va a usar. Un código thunk de interfaz es un objeto que se usa para mantener un recuento de referencias y proporcionar la capacidad de seguimiento que se usa aquí. Se crea un nuevo código thunk de interfaz en todas las llamadas a `QueryInterface` excepto para las solicitudes para el **IUnknown** interfaz (en este caso, el código thunk mismo se devuelve cada vez que para cumplir las reglas de identidad de COM).  
  
 A continuación verá `AddRef` o **versión** que indica qué método se llamó. A continuación, verá un valor que identifica el objeto ha cambiado cuyo recuento de referencias de interfaz. El valor se realiza un seguimiento es el **esto** puntero del objeto.  
  
 El recuento de referencias que se realiza un seguimiento es el recuento de referencias en dicho código thunk después `AddRef` o **versión** se llamó. Tenga en cuenta que este recuento de referencias no puede coincidir con el recuento de referencias para el objeto. Cada código thunk mantiene su propio número de referencia para ayudarle a cumplir totalmente con las reglas de recuento de referencias de COM.  
  
 El último fragmento de información de seguimiento es el nombre del objeto y la interfaz que se vean afectados por la `AddRef` o **versión** llamar.  
  
 Cualquier interfaz pérdidas detectadas cuando se cierra el servidor y `_Module.Term` llamar registrará similar al siguiente:  
  
 `ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`  
  
 La información proporcionada aquí se asigna directamente a la información proporcionada en las instrucciones de seguimiento anterior, para poder examinar los recuentos de referencia a lo largo de la duración completa de un código thunk de interfaz. Además, obtendrá un valor que indica el número máximo de referencias en dicho código thunk de interfaz.  
  
> [!NOTE]
> `_ATL_DEBUG_INTERFACES`puede utilizarse en las compilaciones comerciales.  
  
##  <a name="_atl_debug_qi"></a>_ATL_DEBUG_QI  
 Escribe todas las llamadas a `QueryInterface` en la ventana de salida.  
  
```
#define _ATL_DEBUG_QI
```  
  
### <a name="remarks"></a>Comentarios  
 Si una llamada a `QueryInterface` error, se mostrará la ventana de salida:  
  
 *nombre de la interfaz* - `failed`  
  
##  <a name="atlassert"></a>ATLASSERT  
 El `ATLASSERT` macro realiza la misma funcionalidad que la [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) macro que encontró en la biblioteca de tiempo de ejecución de C.  
  
```
ATLASSERT(booleanExpression);
```  
  
### <a name="parameters"></a>Parámetros  
 `booleanExpression`  
 Expresión (incluidos los punteros) que se evalúa como cero o un valor 0.  
  
### <a name="remarks"></a>Comentarios  
 En las compilaciones de depuración, `ATLASSERT` se evalúa como `booleanExpression` y genera un informe de depuración cuando el resultado es false.  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldef.h  
    
##  <a name="atlensure"></a>ATLENSURE  
 Esta macro se usa para validar los parámetros pasados a una función.  
  
```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```  
  
### <a name="parameters"></a>Parámetros  
 `booleanExpression`  
 Especifica una expresión booleana que se va a probar.  
  
 `hr`  
 Especifica un código de error para devolver.  
  
### <a name="remarks"></a>Comentarios  
 Estas macros proporcionan un mecanismo para detectar y notificar al usuario de uso de parámetros incorrecto.  
  
 Las llamadas de macro `ATLASSERT` y si la condición da error llamadas `AtlThrow`.  
  
 En el **ATLENSURE** caso, `AtlThrow` se llama con E_FAIL.  
  
 En el **ATLENSURE_THROW** caso, `AtlThrow` se llama con el valor HRESULT especificado.  
  
 La diferencia entre **ATLENSURE** y `ATLASSERT` es que **ATLENSURE** produce una excepción en la versión se compila, así como en compilaciones de depuración.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  

##  <a name="atltracenotimpl"></a>ATLTRACENOTIMPL  
 En las compilaciones de depuración de ATL, envía la cadena " `funcname` no se ha implementado" en el dispositivo de volcado de memoria y devuelve **E_NOTIMPL**.  
  
```
ATLTRACENOTIMPL(funcname);
```  
  
### <a name="parameters"></a>Parámetros  
 `funcname`  
 [in] Una cadena que contiene el nombre de la función que no está implementada.  
  
### <a name="remarks"></a>Comentarios  
 En versiones de lanzamiento, simplemente devuelve **E_NOTIMPL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atltrace.h 

##  <a name="atltrace"></a>ATLTRACE
 Informa de advertencias en un dispositivo de salida, como la ventana del depurador, según las marcas indicados y los niveles. Se incluye por compatibilidad con versiones anteriores.  
  
```
ATLTRACE(exp);

ATLTRACE(  
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```  
  
### <a name="parameters"></a>Parámetros  
 `exp`  
 [in] La cadena y variables para enviarlas a la ventana de salida de Visual C++ o cualquier aplicación que intercepte estos mensajes.  
  
 `category`  
 [in] Tipo de evento o método en el que al informe. Vea la sección Comentarios para obtener una lista de categorías.  
  
 `level`  
 [in] El nivel de seguimiento para el informe. Vea la sección Comentarios para obtener más información.  
  
 `lpszFormat`  
 [in] La cadena con formato para enviar en el dispositivo de volcado de memoria.  
  
### <a name="remarks"></a>Comentarios  
 Vea [ATLTRACE2](#atltrace2) para obtener una descripción de **ATLTRACE**. **ATLTRACE** y `ATLTRACE2` tienen el mismo comportamiento, **ATLTRACE** se incluye por compatibilidad con versiones anteriores.  
  
##  <a name="atltrace2"></a>ATLTRACE2  
 Informa de advertencias en un dispositivo de salida, como la ventana del depurador, según las marcas indicados y los niveles.  
  
```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTRlpszFormat,  ...);
```  
  
### <a name="parameters"></a>Parámetros  
 `exp`  
 [in] Cadena que se envía a la ventana de salida de Visual C++ o cualquier aplicación que intercepte estos mensajes.  
  
 `category`  
 [in] Tipo de evento o método en el que al informe. Vea la sección Comentarios para obtener una lista de categorías.  
  
 `level`  
 [in] El nivel de seguimiento para el informe. Vea la sección Comentarios para obtener más información.  
  
 `lpszFormat`  
 [in] El `printf`-cadena de formato que se utiliza para crear una cadena que se envía al dispositivo de volcado de memoria de estilo.  
  
### <a name="remarks"></a>Comentarios  
 La forma abreviada de `ATLTRACE2` escribe una cadena en el depurador de la ventana de salida. La segunda forma de `ATLTRACE2` también escribe los resultados en la ventana de salida del depurador, pero está sujeto a la configuración de la herramienta de seguimiento ATL/MFC (vea [ejemplo ATLTraceTool](../../visual-cpp-samples.md)). Por ejemplo, si establece `level` 4 y la herramienta de seguimiento ATL/MFC nivel 0, no verá el mensaje. *nivel de* puede ser 0, 1, 2, 3 o 4. El valor predeterminado, 0, notifica únicamente los problemas más graves.  
  
 El `category` las marcas de seguimiento para establecer listas de parámetros. Estas marcas se corresponden con los tipos de métodos para los que desee notificar. Las tablas siguientes enumeran las marcas de seguimiento válido que se puede usar para la `category` parámetro.  
  
### <a name="atl-trace-flags"></a>Marcas de seguimiento ATL  
  
|Categoría ATL|Descripción|  
|------------------|-----------------|  
|`atlTraceGeneral`|Informa de todas las aplicaciones de ATL. El valor predeterminado.|  
|`atlTraceCOM`|Informa de los métodos COM.|  
|`atlTraceQI`|Informes en las llamadas de QueryInterface.|  
|`atlTraceRegistrar`|Informes en el registro de objetos.|  
|`atlTraceRefcount`|Informes acerca de cómo cambiar el recuento de referencias.|  
|`atlTraceWindowing`|Informes sobre los métodos de windows; Por ejemplo, informa de un identificador de asignación de mensaje no válido.|  
|`atlTraceControls`|Informes de controles; Por ejemplo, se emite cuando se destruye un control o en la ventana.|  
|`atlTraceHosting`|Informes de hospedaje de mensajes; Por ejemplo, se emite cuando se activa un cliente en un contenedor.|  
|`atlTraceDBClient`|Informes en la plantilla de consumidor OLE DB; Por ejemplo, cuando una llamada al método GetData produce un error, el resultado puede contener el valor HRESULT.|  
|`atlTraceDBProvider`|Informes en la plantilla de proveedores OLE DB; Por ejemplo, notifica si falló la creación de una columna.|  
|`atlTraceSnapin`|Informes de aplicación de complemento de MMC.|  
|`atlTraceNotImpl`|Informa de que la función indicada no está implementada.|  
|**atlTraceAllocation**|Mensajes de informes impresos por la memoria herramientas en atldbgmem.h de depuración.|  
  
### <a name="mfc-trace-flags"></a>Marcas de seguimiento MFC  
  
|Categoría MFC|Descripción|  
|------------------|-----------------|  
|**traceAppMsg**|Uso general, los mensajes MFC. Siempre se recomienda.|  
|**traceDumpContext**|Los mensajes procedentes de [CDumpContext](../../mfc/reference/cdumpcontext-class.md).|  
|**traceWinMsg**|Mensajes de código de control de mensajes de MFC.|  
|**traceMemory**|Mensajes de código de administración de memoria de MFC.|  
|**traceCmdRouting**|Mensajes de Windows de MFC código enrutamiento de comandos.|  
|**traceHtml**|Mensajes de compatibilidad de cuadro de diálogo DHTML de MFC.|  
|**traceSocket**|Mensajes de compatibilidad con el socket de MFC.|  
|**traceOle**|Mensajes del soporte técnico OLE de MFC.|  
|**traceDatabase**|Mensajes de compatibilidad de base de datos de MFC.|  
|**traceInternet**|Mensajes del soporte técnico de Internet de MFC.|  
  
 Para declarar una categoría de seguimiento personalizada, declare una instancia global de la `CTraceCategory` clase como sigue:  
  
 [!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]  
  
 El nombre de categoría, `MY_CATEGORY` en este ejemplo, es el nombre que especifique para el `category` parámetro. El primer parámetro es el nombre de categoría que va a aparecer en la herramienta de seguimiento ATL/MFC. El segundo parámetro es el nivel de seguimiento predeterminado. Este parámetro es opcional y el nivel de seguimiento predeterminado es 0.  
  
 Para usar una categoría definida por el usuario:  
  
 [!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]  
  
 Para especificar que desea filtrar los mensajes de seguimiento, inserte las definiciones de estas macros en Stdafx.h antes de la `#include <atlbase.h>` instrucción.  
  
 Como alternativa, puede establecer el filtro en las directivas de preprocesador en el **páginas de propiedades** cuadro de diálogo. Haga clic en el **preprocesador** ficha y, a continuación, insertar global en el **definiciones de preprocesador** cuadro de edición.  
  
 Atlbase.h contiene las definiciones predeterminadas de la `ATLTRACE2` macros y estas definiciones se utilizarán si no los defines estos símbolos antes de que se procese atlbase.h.  
  
 En versiones de lanzamiento, `ATLTRACE2` se compila a `(void) 0`.  
  
 `ATLTRACE2`limita el contenido de la cadena que se enviará al dispositivo de volcado de memoria a no más de 1023 caracteres, después de darle formato.  
  
 **ATLTRACE** y `ATLTRACE2` tienen el mismo comportamiento, **ATLTRACE** se incluye por compatibilidad con versiones anteriores.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)   
 [Funciones globales de depuración e informe de errores](../../atl/reference/debugging-and-error-reporting-global-functions.md)
