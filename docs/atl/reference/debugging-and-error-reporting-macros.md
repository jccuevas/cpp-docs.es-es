---
title: "Macros de informes de errores y depuración | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- macros, error reporting
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
caps.latest.revision: 18
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 112b43c325d4b73d2cc15ba41d9aac255c74da8a
ms.lasthandoff: 02/24/2017

---
# <a name="debugging-and-error-reporting-macros"></a>Macros de informes de errores y depuración
Estas macros proporcionan útiles funciones de depuración y seguimiento.  
  
|||  
|-|-|  
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|Escribe en la ventana de resultados, pérdidas de cualquier interfaz que se detectan cuando `_Module.Term` se llama.|  
|[_ATL_DEBUG_QI](#_atl_debug_qi)|Escribe todas las llamadas a `QueryInterface` en la ventana de salida.|  
|[ATLASSERT](#atlassert)|Realiza la misma funcionalidad que la [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) macro que se encuentra en la biblioteca de tiempo de ejecución de C.|  
|[ATLENSURE](#atlensure)|Realiza la validación de parámetros. Llamar a `AtlThrow` si es necesario|  
|[ATLTRACENOTIMPL](#atltracenotimpl)|Envía un mensaje en el dispositivo de volcado de memoria que no se implementa la función especificada.|  
|[ATLTRACE](http://msdn.microsoft.com/library/c796baa5-e2b9-4814-a27d-d800590b102e)|Informa de advertencias a un dispositivo de salida, como la ventana del depurador, según los niveles y marcas indicados. Se incluye por compatibilidad con versiones anteriores.|  
|[ATLTRACE2](#atltrace2)|Informa de advertencias a un dispositivo de salida, como la ventana del depurador, según los niveles y marcas indicados.|  
  
##  <a name="a-nameatldebuginterfacesa--atldebuginterfaces"></a><a name="_atl_debug_interfaces"></a>_ATL_DEBUG_INTERFACES  
 Definir esta macro antes de incluir los archivos de encabezado ATL para realizar el seguimiento de todos los `AddRef` y **versión** llama a interfaces de los componentes en la ventana de salida.  
  
```
#define _ATL_DEBUG_INTERFACES
```  
  
### <a name="remarks"></a>Comentarios  
 El resultado de seguimiento aparecerá como se muestra a continuación:  
  
 `ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`  
  
 La primera parte de cada seguimiento siempre será `ATL: QIThunk`. Lo siguiente es un valor que identifica el particular *interfaz thunk* que se va a utilizar. Un código thunk de interfaz es un objeto que se utiliza para mantener un recuento de referencias y proporcionar la capacidad de seguimiento que se usa aquí. Se crea un nuevo código thunk de interfaz en cada llamada a `QueryInterface` excepto para las solicitudes de la **IUnknown** interfaz (en este caso, el código thunk mismo se devuelve cada vez para cumplir con las reglas de identidad de COM).  
  
 A continuación verá `AddRef` o **versión** que indica qué método se llamó. A continuación, verá un valor que identifica el objeto cuyo número de referencia de la interfaz se ha cambiado. El valor que se realiza un seguimiento es el **esto** el puntero del objeto.  
  
 El recuento de referencias que se realiza un seguimiento es el recuento de referencias en ese código thunk después `AddRef` o **versión** se llamó. Tenga en cuenta que este recuento de referencias no puede coincidir con el recuento de referencias para el objeto. Cada código thunk mantiene su propio número de referencias para ayudarle a cumplir las reglas de recuento de referencias de COM.  
  
 El último fragmento de información de seguimiento es el nombre del objeto y la interfaz que se ve afectado por la `AddRef` o **versión** llamar.  
  
 Cualquier interfaz pérdidas detectadas cuando se apaga el servidor y `_Module.Term` llamar registrará similar al siguiente:  
  
 `ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`  
  
 La información proporcionada aquí se asigna directamente a la información proporcionada en las instrucciones de seguimiento anterior, por lo que puede examinar los recuentos de referencia a lo largo de la duración completa de un código thunk de interfaz. Además, obtendrá una indicación de que el número máximo de referencias en ese código thunk de interfaz.  
  
> [!NOTE]
> `_ATL_DEBUG_INTERFACES`puede utilizarse en las compilaciones comerciales.  
  
##  <a name="a-nameatldebugqia--atldebugqi"></a><a name="_atl_debug_qi"></a>_ATL_DEBUG_QI  
 Escribe todas las llamadas a `QueryInterface` en la ventana de salida.  
  
```
#define _ATL_DEBUG_QI
```  
  
### <a name="remarks"></a>Comentarios  
 Si una llamada a `QueryInterface` con error, se mostrará la ventana de salida:  
  
 *nombre de la interfaz* - `failed`  
  
##  <a name="a-nameatlasserta--atlassert"></a><a name="atlassert"></a>ATLASSERT  
 El `ATLASSERT` macro realiza la misma funcionalidad que la [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) macro que se encuentra en la biblioteca de tiempo de ejecución de C.  
  
```
ATLASSERT(booleanExpression);
```  
  
### <a name="parameters"></a>Parámetros  
 `booleanExpression`  
 (Incluidos los punteros) que se evalúa como cero o un valor 0.  
  
### <a name="remarks"></a>Comentarios  
 En compilaciones de depuración, `ATLASSERT` se evalúa como `booleanExpression` y genera un informe de depuración cuando el resultado es false.  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldef.h  
    
##  <a name="a-nameatlensurea--atlensure"></a><a name="atlensure"></a>ATLENSURE  
 Esta macro se utiliza para validar los parámetros pasados a una función.  
  
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
  
 Las llamadas a macros `ATLASSERT` y si la condición no se llama `AtlThrow`.  
  
 En el **ATLENSURE** caso, `AtlThrow` se llama con E_FAIL.  
  
 En el **ATLENSURE_THROW** caso, `AtlThrow` se llama con el valor HRESULT especificado.  
  
 La diferencia entre **ATLENSURE** y `ATLASSERT` es que **ATLENSURE** produce una excepción en la versión se basa, así como en las compilaciones de depuración.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#108;](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** afx.h  

##  <a name="a-nameatltracenotimpla--atltracenotimpl"></a><a name="atltracenotimpl"></a>ATLTRACENOTIMPL  
 En compilaciones de depuración de ATL, envía la cadena " `funcname` no está implementado" para el dispositivo de volcado de memoria y devuelve **E_NOTIMPL**.  
  
```
ATLTRACENOTIMPL(funcname);
```  
  
### <a name="parameters"></a>Parámetros  
 `funcname`  
 [in] Una cadena que contiene el nombre de la función que no está implementada.  
  
### <a name="remarks"></a>Comentarios  
 En versiones de lanzamiento, simplemente devuelve **E_NOTIMPL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[127 NVC_ATL_Utilities](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atltrace.h 

##  <a name="a-nameatla--atltrace"></a><a name="atl_"></a>ATLTRACE
 Informa de advertencias a un dispositivo de salida, como la ventana del depurador, según los niveles y marcas indicados. Se incluye por compatibilidad con versiones anteriores.  
  
```
ATLTRACE(exp);

ATLTRACE(  
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```  
  
### <a name="parameters"></a>Parámetros  
 `exp`  
 [in] La cadena y variables para enviar a la ventana de salida de Visual C++ o cualquier aplicación que intercepta estos mensajes.  
  
 `category`  
 [in] Tipo de evento o método en el que al informe. Vea la sección Comentarios para obtener una lista de categorías.  
  
 `level`  
 [in] El nivel de seguimiento en el informe. Vea la sección Comentarios para obtener más información.  
  
 `lpszFormat`  
 [in] La cadena con formato para enviar al dispositivo de volcado de memoria.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [ATLTRACE2](#atltrace2) para obtener una descripción de **ATLTRACE**. **ATLTRACE** y `ATLTRACE2` tienen el mismo comportamiento, **ATLTRACE** se incluye por compatibilidad con versiones anteriores.  
  
##  <a name="a-nameatltrace2a--atltrace2"></a><a name="atltrace2"></a>ATLTRACE2  
 Informa de advertencias a un dispositivo de salida, como la ventana del depurador, según los niveles y marcas indicados.  
  
```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTRlpszFormat,  ...);
```  
  
### <a name="parameters"></a>Parámetros  
 `exp`  
 [in] La cadena para enviar a la ventana de salida de Visual C++ o cualquier aplicación que intercepta estos mensajes.  
  
 `category`  
 [in] Tipo de evento o método en el que al informe. Vea la sección Comentarios para obtener una lista de categorías.  
  
 `level`  
 [in] El nivel de seguimiento en el informe. Vea la sección Comentarios para obtener más información.  
  
 `lpszFormat`  
 [in] El `printf`: estilo de cadena de formato se utiliza para crear una cadena a enviar al dispositivo de volcado de memoria.  
  
### <a name="remarks"></a>Comentarios  
 La forma abreviada de `ATLTRACE2` escribe una cadena en el depurador de la ventana de resultados. La segunda forma de `ATLTRACE2` también escribe los resultados en la ventana de salida del depurador, pero está sujeto a la configuración de la herramienta de seguimiento ATL/MFC (vea [ejemplo ATLTraceTool](../../visual-cpp-samples.md)). Por ejemplo, si establece `level` 4 y la herramienta de seguimiento ATL/MFC al nivel 0, no verá el mensaje. *nivel de* puede ser 0, 1, 2, 3 o 4. El valor predeterminado, 0, informa sólo de los problemas más serios.  
  
 El `category` las marcas de seguimiento para establecer listas de parámetros. Estas marcas se corresponden con los tipos de métodos para los que desee notificar. Las tablas siguientes muestran las marcas de seguimiento válido que se puede usar para el `category` parámetro.  
  
### <a name="atl-trace-flags"></a>Marcas de seguimiento ATL  
  
|Categoría ATL|Descripción|  
|------------------|-----------------|  
|`atlTraceGeneral`|Informa sobre todas las aplicaciones de ATL. El valor predeterminado.|  
|`atlTraceCOM`|Informa sobre los métodos COM.|  
|`atlTraceQI`|Informes sobre llamadas a QueryInterface.|  
|`atlTraceRegistrar`|Informa sobre el registro de objetos.|  
|`atlTraceRefcount`|Informes acerca de cómo cambiar el recuento de referencias.|  
|`atlTraceWindowing`|Informes sobre los métodos de windows; Por ejemplo, informa de un identificador de asignación de mensaje no válido.|  
|`atlTraceControls`|Informes de controles; Por ejemplo, los informes cuando se destruye un control o en la ventana.|  
|`atlTraceHosting`|Informes de hospedaje de mensajes; Por ejemplo, informes cuando se activa un cliente en un contenedor.|  
|`atlTraceDBClient`|Informes de la plantilla de consumidor OLE DB; Por ejemplo, cuando una llamada a GetData se produce un error, el resultado puede contener el valor HRESULT.|  
|`atlTraceDBProvider`|Informes en la plantilla de proveedor OLE DB; Por ejemplo, notifica si no la creación de una columna.|  
|`atlTraceSnapin`|Informes de aplicación de complemento de MMC.|  
|`atlTraceNotImpl`|Informa de que la función indicada no está implementada.|  
|**atlTraceAllocation**|Mensajes de informes impresos por la memoria depurar herramientas en atldbgmem.h.|  
  
### <a name="mfc-trace-flags"></a>Marcas de seguimiento MFC  
  
|Categoría MFC|Descripción|  
|------------------|-----------------|  
|**traceAppMsg**|Propósito general, los mensajes MFC. Siempre se recomienda.|  
|**traceDumpContext**|Los mensajes procedentes de [CDumpContext](../../mfc/reference/cdumpcontext-class.md).|  
|**traceWinMsg**|Mensajes de código de control de mensajes de MFC.|  
|**traceMemory**|Mensajes de código de administración de memoria de MFC.|  
|**traceCmdRouting**|Mensajes de ventanas de MFC comando código de ruta.|  
|**traceHtml**|Mensajes de soporte de cuadro de diálogo DHTML de MFC.|  
|**traceSocket**|Mensajes de compatibilidad con el socket de MFC.|  
|**traceOle**|Mensajes de compatibilidad con OLE de MFC.|  
|**traceDatabase**|Mensajes de compatibilidad de base de datos de MFC.|  
|**traceInternet**|Mensajes de soporte técnico para Internet de MFC.|  
  
 Para declarar una categoría de seguimiento personalizada, declare una instancia global de la `CTraceCategory` clase como sigue:  
  
 [!code-cpp[NVC_ATL_Utilities&#109;](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]  
  
 El nombre de categoría, `MY_CATEGORY` en este ejemplo, es el nombre que especifique para el `category` parámetro. El primer parámetro es el nombre de categoría que aparece en la herramienta de seguimiento ATL/MFC. El segundo parámetro es el nivel de seguimiento predeterminado. Este parámetro es opcional y el nivel de seguimiento predeterminado es 0.  
  
 Para utilizar una categoría definida por el usuario:  
  
 [!code-cpp[NVC_ATL_Utilities&#110;](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]  
  
 Para especificar que desea filtrar los mensajes de seguimiento, inserte las definiciones de estas macros en Stdafx.h antes de la `#include <atlbase.h>` instrucción.  
  
 Como alternativa, puede establecer el filtro en las directivas de preprocesador en el **páginas de propiedades** cuadro de diálogo. Haga clic en el **preprocesador** ficha y, a continuación, insertar global a la **definiciones de preprocesador** cuadro de edición.  
  
 Atlbase.h contiene las definiciones predeterminadas de la `ATLTRACE2` macros y estas definiciones se utilizarán si no define estos símbolos antes de procesar atlbase.h.  
  
 En versiones de lanzamiento, `ATLTRACE2` se compila a `(void) 0`.  
  
 `ATLTRACE2`limita el contenido de la cadena que se enviará al dispositivo de volcado de memoria a no más de 1023 caracteres, después de dar formato.  
  
 **ATLTRACE** y `ATLTRACE2` tienen el mismo comportamiento, **ATLTRACE** se incluye por compatibilidad con versiones anteriores.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#111;](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)   
 [Funciones globales de notificación de errores y depuración](../../atl/reference/debugging-and-error-reporting-global-functions.md)

