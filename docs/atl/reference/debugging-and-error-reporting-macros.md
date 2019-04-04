---
title: Macros de depuración e informe de errores
ms.date: 03/27/2019
f1_keywords:
- atldef/ATL::_ATL_DEBUG_INTERFACES
- atldef/ATL::_ATL_DEBUG_QI
- atldef/ATL::ATLASSERT
- afx/ATL::ATLENSURE
- atltrace/ATL::ATLTRACENOTIMPL
- atltrace/ATL::ATLTRACE
helpviewer_keywords:
- macros, error reporting
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
ms.openlocfilehash: 0d5010f913521848675987b145a1277c7b00decf
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775054"
---
# <a name="debugging-and-error-reporting-macros"></a>Macros de depuración e informe de errores

Estas macros proporcionan útiles instalaciones de depuración y seguimiento.

|||
|-|-|
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|Escribe, en la ventana de salida, las pérdidas de cualquier interfaz que se detectan cuando `_Module.Term` se llama.|
|[_ATL_DEBUG_QI](#_atl_debug_qi)|Escribe todas las llamadas a `QueryInterface` en la ventana de salida.|
|[ATLASSERT](#atlassert)|Realiza la misma funcionalidad que el [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) macro se encuentra en la biblioteca de tiempo de ejecución de C.|
|[ATLENSURE](#atlensure)|Realiza la validación de parámetros. Llamar a `AtlThrow` si es necesario|
|[ATLTRACENOTIMPL](#atltracenotimpl)|Envía un mensaje en el dispositivo de volcado de memoria que no implementa la función especificada.|
|[ATLTRACE](#atltrace)|Advertencias de informes a un dispositivo de salida, como la ventana del depurador, según las marcas indicadas y los niveles. Se incluye por compatibilidad con versiones anteriores.|
|[ATLTRACE2](#atltrace2)|Advertencias de informes a un dispositivo de salida, como la ventana del depurador, según las marcas indicadas y los niveles.|

##  <a name="_atl_debug_interfaces"></a>  _ATL_DEBUG_INTERFACES

Definir esta macro antes de incluir los archivos de encabezado ATL para realizar el seguimiento de todos los `AddRef` y `Release` llama en interfaces de los componentes en la ventana de salida.

```
#define _ATL_DEBUG_INTERFACES
```

### <a name="remarks"></a>Comentarios

El resultado del seguimiento aparecerán como se muestra a continuación:

`ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`

Siempre será la primera parte de cada seguimiento `ATL: QIThunk`. A continuación es un valor que identifica la instancia concreta *código thunk de la interfaz* que se va a usar. Un código thunk de interfaz es un objeto utilizado para mantener un recuento de referencias y proporcionar la funcionalidad de seguimiento usada aquí. Se crea un nuevo código thunk de interfaz en cada llamada a `QueryInterface` excepto para las solicitudes para el `IUnknown` interfaz (en este caso, el código thunk mismo se devuelve cada vez para cumplir con las reglas de identidad de COM).

A continuación verá `AddRef` o `Release` que indica qué método se llamó. A continuación, verá un valor que identifica el objeto cuyo número de referencia de la interfaz se ha cambiado. El valor de seguimiento es la **esto** el puntero del objeto.

El recuento de referencias que se realiza un seguimiento es el recuento de referencias en dicho código thunk después `AddRef` o `Release` llamó. Tenga en cuenta que este recuento de referencias no puede coincidir con el recuento de referencias para el objeto. Cada código thunk mantiene su propio recuento de referencias para ayudarle a cumplir las reglas de recuento de referencias de COM.

La última pieza de información de seguimiento es el nombre del objeto y la interfaz que se vean afectados por la `AddRef` o `Release` llamar.

Cualquier interfaz pérdidas detectadas cuando se cierra el servidor y `_Module.Term` llamar a haber iniciado similar al siguiente:

`ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`

La información proporcionada aquí se asigna directamente a la información proporcionada en las instrucciones de seguimiento anterior, para que pueda examinar los recuentos de referencia a lo largo de la duración completa de un código thunk de interfaz. Además, obtendrá una indicación de que el número máximo de referencias en el código thunk de esa interfaz.

> [!NOTE]
> _ATL_DEBUG_INTERFACES puede usarse en las compilaciones comerciales.

##  <a name="_atl_debug_qi"></a>  _ATL_DEBUG_QI

Escribe todas las llamadas a `QueryInterface` en la ventana de salida.

```
#define _ATL_DEBUG_QI
```

### <a name="remarks"></a>Comentarios

Si una llamada a `QueryInterface` error, se mostrará la ventana de salida:

*nombre de la interfaz* - `failed`

##  <a name="atlassert"></a>  ATLASSERT

La macro ATLASSERT realiza la misma funcionalidad que el [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) macro se encuentra en la biblioteca de tiempo de ejecución de C.

```
ATLASSERT(booleanExpression);
```

### <a name="parameters"></a>Parámetros

*booleanExpression*<br/>
Expresión (incluidos los punteros) que se evalúa como 0 o distinto de cero.

### <a name="remarks"></a>Comentarios

En las compilaciones de depuración, se evalúa como ATLASSERT *booleanExpression* y genera un informe de depuración cuando el resultado es false.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldef.h

##  <a name="atlensure"></a>  ATLENSURE

Esta macro se usa para validar los parámetros pasados a una función.

```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```

### <a name="parameters"></a>Parámetros

*booleanExpression*<br/>
Especifica una expresión booleana que va a probarse.

*hr*<br/>
Especifica un código de error para devolver.

### <a name="remarks"></a>Comentarios

Estas macros proporcionan un mecanismo para detectar y notificar al usuario sobre el uso de parámetros incorrecto.

Llama a la macro ATLASSERT y si la condición se produce un error en las llamadas `AtlThrow`.

En el caso ATLENSURE `AtlThrow` se llama con E_FAIL.

En el caso ATLENSURE_THROW `AtlThrow` se llama con el valor HRESULT especificado.

La diferencia entre ATLENSURE y ATLASSERT es que ATLENSURE produce una excepción en las compilaciones de versión, así como en las compilaciones de depuración.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="atltracenotimpl"></a>  ATLTRACENOTIMPL

En las compilaciones de depuración de ATL, envía la cadena " *funcname* no está implementado" en el dispositivo de volcado de memoria y devuelve E_NOTIMPL.

```
ATLTRACENOTIMPL(funcname);
```

### <a name="parameters"></a>Parámetros

*funcname*<br/>
[in] Una cadena que contiene el nombre de la función que no está implementada.

### <a name="remarks"></a>Comentarios

En versiones de lanzamiento, simplemente devuelva E_NOTIMPL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** atltrace.h

##  <a name="atltrace"></a>  ATLTRACE

Advertencias de informes a un dispositivo de salida, como la ventana del depurador, según las marcas indicadas y los niveles. Se incluye por compatibilidad con versiones anteriores.

```
ATLTRACE(exp);

ATLTRACE(
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```

### <a name="parameters"></a>Parámetros

*exp*<br/>
[in] La cadena y las variables para enviar a la ventana de salida de Visual C++ o cualquier aplicación que intercepta estos mensajes.

*category*<br/>
[in] Tipo de evento o método en el que al informe. Vea la sección Comentarios para obtener una lista de categorías.

*level*<br/>
[in] El nivel de seguimiento en el informe. Vea la sección Comentarios para obtener más información.

*lpszFormat*<br/>
[in] La cadena con formato para enviar al dispositivo de volcado de memoria.

### <a name="remarks"></a>Comentarios

Consulte [ATLTRACE2](#atltrace2) para obtener una descripción de ATLTRACE. ATLTRACE y ATLTRACE2 tienen el mismo comportamiento, ATLTRACE se incluye por compatibilidad con versiones anteriores.

##  <a name="atltrace2"></a>  ATLTRACE2

Advertencias de informes a un dispositivo de salida, como la ventana del depurador, según las marcas indicadas y los niveles.

```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTRlpszFormat,  ...);
```

### <a name="parameters"></a>Parámetros

*exp*<br/>
[in] La cadena para enviar a la ventana de salida de Visual C++ o cualquier aplicación que intercepta estos mensajes.

*category*<br/>
[in] Tipo de evento o método en el que al informe. Vea la sección Comentarios para obtener una lista de categorías.

*level*<br/>
[in] El nivel de seguimiento en el informe. Vea la sección Comentarios para obtener más información.

*lpszFormat*<br/>
[in] El `printf`-cadena de formato se utiliza para crear una cadena a enviar al dispositivo de volcado de memoria de estilo.

### <a name="remarks"></a>Comentarios

La forma abreviada de ATLTRACE2 escribe una cadena en la ventana de salida del depurador. La segunda forma de ATLTRACE2 también escribe la salida en la ventana de salida del depurador, pero está sujeto a la configuración de la herramienta de seguimiento ATL/MFC (vea [ejemplo ATLTraceTool](../../overview/visual-cpp-samples.md)). Por ejemplo, si establece *nivel* a 4 y la herramienta de seguimiento ATL/MFC al nivel 0, no verá el mensaje. *nivel* puede ser 0, 1, 2, 3 o 4. El valor predeterminado, 0, notifica solo los problemas más serios.

El *categoría* listas de parámetros para establecer las marcas de seguimiento. Estas marcas se corresponden con los tipos de métodos para el que desea informar. Las tablas siguientes muestran las marcas de seguimiento válido puede usar para la *categoría* parámetro.

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
|`atlTraceHosting`|Informes que hospeda los mensajes; Por ejemplo, se notifica cuando se activa un cliente en un contenedor.|
|`atlTraceDBClient`|Informes en la plantilla de consumidor OLE DB; Por ejemplo, cuando una llamada a GetData se produce un error, el resultado puede contener el valor HRESULT.|
|`atlTraceDBProvider`|Informes en la plantilla de proveedores OLE DB; Por ejemplo, notifica si la creación de una columna de error.|
|`atlTraceSnapin`|Informes de la aplicación de complemento de MMC.|
|`atlTraceNotImpl`|Informa de que la función indicada no está implementada.|
|`atlTraceAllocation`|Mensajes de informes impresos por la memoria de las herramientas en atldbgmem.h de depuración.|

### <a name="mfc-trace-flags"></a>Marcas de seguimiento MFC

|Categoría MFC|Descripción|
|------------------|-----------------|
|`traceAppMsg`|Uso general, los mensajes MFC. Siempre se recomienda.|
|`traceDumpContext`|Los mensajes procedentes de [CDumpContext](../../mfc/reference/cdumpcontext-class.md).|
|`traceWinMsg`|Mensajes de código de control de mensajes de MFC.|
|`traceMemory`|Mensajes desde el código de administración de memoria de MFC.|
|`traceCmdRouting`|Los mensajes de Windows de MFC código enrutamiento de comandos.|
|`traceHtml`|Mensajes de compatibilidad de cuadro de diálogo DHTML de MFC.|
|`traceSocket`|Mensajes de compatibilidad con el socket de MFC.|
|`traceOle`|Mensajes de soporte técnico OLE de MFC.|
|`traceDatabase`|Mensajes de compatibilidad de base de datos de MFC.|
|`traceInternet`|Mensajes de soporte técnico para Internet de MFC.|

Para declarar una categoría de seguimiento personalizado, declare una instancia global de la `CTraceCategory` clase como sigue:

[!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]

El nombre de categoría, MY_CATEGORY en este ejemplo, es el nombre que especifique para la *categoría* parámetro. El primer parámetro es el nombre de categoría que aparecerá en la herramienta de seguimiento ATL/MFC. El segundo parámetro es el nivel de seguimiento predeterminado. Este parámetro es opcional y el nivel de seguimiento predeterminado es 0.

Para usar una categoría definida por el usuario:

[!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]

Para especificar que desea filtrar los mensajes de seguimiento, inserte las definiciones de estas macros en Stdafx.h antes el `#include <atlbase.h>` instrucción.

Como alternativa, puede establecer el filtro en las directivas de preprocesador en el **páginas de propiedades** cuadro de diálogo. Haga clic en el **preprocesador** pestaña y, a continuación, insertar global en el **definiciones del preprocesador** cuadro de edición.

Atlbase.h contiene las definiciones predeterminadas de las macros ATLTRACE2 y estas definiciones se usará si no define estos símbolos antes de que atlbase.h se procesa.

En las compilaciones de versión se compila a ATLTRACE2 `(void) 0`.

ATLTRACE2 limita el contenido de la cadena que se enviará al dispositivo de volcado de memoria a no más de 1023 caracteres, después de darle formato.

ATLTRACE y ATLTRACE2 tienen el mismo comportamiento, ATLTRACE se incluye por compatibilidad con versiones anteriores.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)<br/>
[Funciones globales de depuración e informe de errores](../../atl/reference/debugging-and-error-reporting-global-functions.md)
