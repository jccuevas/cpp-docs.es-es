---
title: Macros de depuración e informe de errores
ms.date: 05/06/2019
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
ms.openlocfilehash: b666ba3debe164118c9b40b90313646592b04876
ms.sourcegitcommit: bf724dfc639b16d5410fab72183f8e6b781338bc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2019
ms.locfileid: "71062038"
---
# <a name="debugging-and-error-reporting-macros"></a>Macros de depuración e informe de errores

Estas macros proporcionan funciones de depuración y seguimiento útiles.

|||
|-|-|
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|Escribe en la ventana de salida cualquier fuga de interfaz que se detecte cuando `_Module.Term` se llama a.|
|[_ATL_DEBUG_QI](#_atl_debug_qi)|Escribe todas las llamadas `QueryInterface` a en la ventana de salida.|
|[ATLASSERT](#atlassert)|Realiza la misma funcionalidad que la macro _ [Asserte](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) que se encuentra en la biblioteca en tiempo de ejecución de C.|
|[ATLENSURE](#atlensure)|Realiza la validación de parámetros. Llamar `AtlThrow` a si es necesario|
|[ATLTRACENOTIMPL](#atltracenotimpl)|Envía un mensaje al dispositivo de volcado que indica que la función especificada no está implementada.|
|[ATLTRACE](#atltrace)|Notifica advertencias a un dispositivo de salida, como la ventana del depurador, según las marcas y los niveles indicados. Se incluye para la compatibilidad con versiones anteriores.|
|[ATLTRACE2](#atltrace2)|Notifica advertencias a un dispositivo de salida, como la ventana del depurador, según las marcas y los niveles indicados.|

##  <a name="_atl_debug_interfaces"></a>  _ATL_DEBUG_INTERFACES

Defina esta macro antes de incluir cualquier archivo de encabezado ATL para `AddRef` realizar `Release` el seguimiento de todos los archivos y las llamadas a la ventana de salida en las interfaces de los componentes.

```
#define _ATL_DEBUG_INTERFACES
```

### <a name="remarks"></a>Comentarios

El resultado del seguimiento aparecerá como se muestra a continuación:

`ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`

La primera parte de cada seguimiento siempre `ATL: QIThunk`será. A continuación se indica un valor que identifica el *código thunk* de la interfaz concreta que se está usando. Un código thunk de interfaz es un objeto que se usa para mantener un recuento de referencias y proporcionar la funcionalidad de seguimiento que se usa aquí. Se crea un nuevo código thunk de interfaz en cada `QueryInterface` llamada a, excepto para `IUnknown` las solicitudes de la interfaz (en este caso, se devuelve el mismo código thunk cada vez que se cumplan las reglas de identidad de com).

A continuación, verá `AddRef` o `Release` indicará el método al que se llamó. A continuación, verá un valor que identifica el objeto cuyo recuento de referencias de interfaz ha cambiado. El valor de seguimiento es el puntero **this** del objeto.

El recuento de referencias del que se realiza el seguimiento es el recuento `AddRef` de `Release` referencias de ese código thunk después de llamar a o. Tenga en cuenta que este recuento de referencias puede no coincidir con el recuento de referencias para el objeto. Cada thunk mantiene su propio recuento de referencias para ayudarle a cumplir todas las reglas de recuento de referencias de COM.

La parte final de la información a la que se hace seguimiento es el nombre del objeto y la interfaz `AddRef` que `Release` se ve afectada por la llamada o.

Cualquier pérdida de interfaz que se detecte cuando el servidor se apague `_Module.Term` y se llame a se registrará de la siguiente manera:

`ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`

La información que se proporciona aquí se asigna directamente a la información proporcionada en las instrucciones de seguimiento anteriores, por lo que puede examinar los recuentos de referencias durante todo el ciclo de vida de un código thunk de interfaz. Además, se obtiene una indicación del número máximo de referencias en el código thunk de la interfaz.

> [!NOTE]
> _ATL_DEBUG_INTERFACES se puede usar en las compilaciones comerciales.

##  <a name="_atl_debug_qi"></a>  _ATL_DEBUG_QI

Escribe todas las llamadas `QueryInterface` a en la ventana de salida.

```
#define _ATL_DEBUG_QI
```

### <a name="remarks"></a>Comentarios

Si se produce un `QueryInterface` error en una llamada a, se mostrará la ventana de salida:

*nombre de interfaz* - `failed`

##  <a name="atlassert"></a>ATLASSERT

La macro ATLASSERT realiza la misma funcionalidad que la macro _ [Asserte](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) que se encuentra en la biblioteca en tiempo de ejecución de C.

```
ATLASSERT(booleanExpression);
```

### <a name="parameters"></a>Parámetros

*booleanExpression*<br/>
Expresión (incluidos los punteros) que se evalúa como un valor distinto de cero o 0.

### <a name="remarks"></a>Comentarios

En las compilaciones de depuración, ATLASSERT evalúa *booleanExpression* y genera un informe de depuración cuando el resultado es false.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldef. h

##  <a name="atlensure"></a>ATLENSURE

Esta macro se utiliza para validar los parámetros pasados a una función.

```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```

### <a name="parameters"></a>Parámetros

*booleanExpression*<br/>
Especifica una expresión booleana que se va a probar.

*hr*<br/>
Especifica un código de error que se va a devolver.

### <a name="remarks"></a>Comentarios

Estas macros proporcionan un mecanismo para detectar y notificar al usuario sobre el uso incorrecto de parámetros.

La macro llama a ATLASSERT y si la condición no `AtlThrow`se realiza correctamente.

En el caso de ATLENSURE `AtlThrow` , se llama a con E_FAIL.

En el caso de ATLENSURE_THROW `AtlThrow` , se llama a con el HRESULT especificado.

La diferencia entre ATLENSURE y ATLASSERT es que ATLENSURE inicia una excepción en las compilaciones de versión, así como en las compilaciones de depuración.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="atltracenotimpl"></a>ATLTRACENOTIMPL

En las compilaciones de depuración de ATL, envía la cadena " *FuncName* no se implementa" al dispositivo de volcado y devuelve E_NOTIMPL.

```
ATLTRACENOTIMPL(funcname);
```

### <a name="parameters"></a>Parámetros

*funcname*<br/>
de Cadena que contiene el nombre de la función que no está implementada.

### <a name="remarks"></a>Comentarios

En las compilaciones de versión, simplemente devuelve E_NOTIMPL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** atltrace. h

##  <a name="atltrace"></a>ATLTRACE

Notifica advertencias a un dispositivo de salida, como la ventana del depurador, según las marcas y los niveles indicados. Se incluye para la compatibilidad con versiones anteriores.

```
ATLTRACE(exp);

ATLTRACE(
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```

### <a name="parameters"></a>Parámetros

*exp*<br/>
de Cadena y variables que se van a enviar a la ventana de salida o a cualquier aplicación que capture estos mensajes.

*category*<br/>
de Tipo de evento o método en el que se va a notificar. Vea los comentarios para obtener una lista de categorías.

*level*<br/>
de Nivel de seguimiento que se va a notificar. Vea los comentarios para obtener más información.

*lpszFormat*<br/>
de Cadena con formato que se va a enviar al dispositivo de volcado.

### <a name="remarks"></a>Comentarios

Consulte [ATLTRACE2](#atltrace2) para obtener una descripción de ATLTRACE. ATLTRACE y ATLTRACE2 tienen el mismo comportamiento, ATLTRACE se incluye por motivos de compatibilidad con versiones anteriores.

##  <a name="atltrace2"></a>  ATLTRACE2

Notifica advertencias a un dispositivo de salida, como la ventana del depurador, según las marcas y los niveles indicados.

```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTR lpszFormat,  ...);
```

### <a name="parameters"></a>Parámetros

*exp*<br/>
de Cadena que se va a enviar a la ventana de salida o a cualquier aplicación que capture estos mensajes.

*category*<br/>
de Tipo de evento o método en el que se va a notificar. Vea los comentarios para obtener una lista de categorías.

*level*<br/>
de Nivel de seguimiento que se va a notificar. Vea los comentarios para obtener más información.

*lpszFormat*<br/>
de Cadena `printf`de formato de estilo que se va a usar para crear una cadena que se va a enviar al dispositivo de volcado.

### <a name="remarks"></a>Comentarios

La forma abreviada de ATLTRACE2 escribe una cadena en la ventana de salida del depurador. La segunda forma de ATLTRACE2 también escribe la salida en la ventana de salida del depurador, pero está sujeta a la configuración de la herramienta de seguimiento de ATL/MFC (vea el [ejemplo ATLTraceTool](../../overview/visual-cpp-samples.md)). Por ejemplo, si establece el *nivel* 4 y la herramienta de seguimiento de ATL/MFC en el nivel 0, no verá el mensaje. *LEVEL* puede ser 0, 1, 2, 3 o 4. El valor predeterminado, 0, solo informa de los problemas más graves.

El parámetro *Category* muestra las marcas de seguimiento que se van a establecer. Estas marcas se corresponden con los tipos de métodos a los que desea informar. En las tablas siguientes se enumeran las marcas de seguimiento válidas que puede usar para el parámetro *Category* .

### <a name="atl-trace-flags"></a>Marcas de seguimiento de ATL

|Categoría ATL|DESCRIPCIÓN|
|------------------|-----------------|
|`atlTraceGeneral`|Informes en todas las aplicaciones ATL. El valor predeterminado.|
|`atlTraceCOM`|Informes sobre métodos COM.|
|`atlTraceQI`|Informes sobre llamadas QueryInterface.|
|`atlTraceRegistrar`|Informa sobre el registro de objetos.|
|`atlTraceRefcount`|Informes sobre el cambio del recuento de referencias.|
|`atlTraceWindowing`|Informes de métodos de Windows; por ejemplo, informa de un identificador de mapa de mensajes no válido.|
|`atlTraceControls`|Informes sobre controles; por ejemplo, los informes cuando se destruye un control o su ventana.|
|`atlTraceHosting`|Informes que hospedan mensajes; por ejemplo, informa cuando se activa un cliente en un contenedor.|
|`atlTraceDBClient`|Informes sobre OLE DB plantilla de consumidor; por ejemplo, cuando se produce un error en una llamada a GetData, la salida puede contener HRESULT.|
|`atlTraceDBProvider`|Informes sobre OLE DB plantilla de proveedor; por ejemplo, informa de si se ha producido un error en la creación de una columna.|
|`atlTraceSnapin`|Informes de la aplicación de complemento MMC.|
|`atlTraceNotImpl`|Informa de que la función indicada no está implementada.|
|`atlTraceAllocation`|Informa de los mensajes impresos por las herramientas de depuración de memoria en atldbgmem. h.|

### <a name="mfc-trace-flags"></a>Marcas de seguimiento de MFC

|Categoría MFC|DESCRIPCIÓN|
|------------------|-----------------|
|`traceAppMsg`|Uso general, mensajes MFC. Siempre se recomienda.|
|`traceDumpContext`|Mensajes de [CDumpContext](../../mfc/reference/cdumpcontext-class.md).|
|`traceWinMsg`|Mensajes del código de control de mensajes de MFC.|
|`traceMemory`|Mensajes del código de administración de memoria de MFC.|
|`traceCmdRouting`|Mensajes del código de enrutamiento de comandos de Windows de MFC.|
|`traceHtml`|Mensajes del compatible con el cuadro de diálogo DHTML de MFC.|
|`traceSocket`|Mensajes de la compatibilidad con sockets de MFC.|
|`traceOle`|Mensajes de la compatibilidad OLE de MFC.|
|`traceDatabase`|Mensajes de compatibilidad con bases de datos de MFC.|
|`traceInternet`|Mensajes del soporte técnico de Internet de MFC.|

Para declarar una categoría de seguimiento personalizada, declare una instancia global `CTraceCategory` de la clase como se indica a continuación:

[!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]

El nombre de la categoría, MY_CATEGORY en este ejemplo, es el nombre que se especifica para el parámetro *Category* . El primer parámetro es el nombre de la categoría que aparecerá en la herramienta de seguimiento de ATL/MFC. El segundo parámetro es el nivel de seguimiento predeterminado. Este parámetro es opcional y el nivel de seguimiento predeterminado es 0.

Para usar una categoría definida por el usuario:

[!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]

Para especificar que desea filtrar los mensajes de seguimiento, inserte las definiciones de estas macros en stdafx. h antes `#include <atlbase.h>` de la instrucción.

Como alternativa, puede establecer el filtro en las directivas de preprocesador en el cuadro de diálogo **páginas de propiedades** . Haga clic en la pestaña **preprocesador** y, a continuación, inserte el global en el cuadro de edición **definiciones del preprocesador** .

ATLBase. h contiene las definiciones predeterminadas de las macros ATLTRACE2 y estas definiciones se usarán si no se definen estos símbolos antes de que ATLBase. h se procese.

En las compilaciones de versión, ATLTRACE2 `(void) 0`se compila en.

ATLTRACE2 limita el contenido de la cadena que se va a enviar al dispositivo de volcado a un máximo de 1023 caracteres, después de aplicar el formato.

ATLTRACE y ATLTRACE2 tienen el mismo comportamiento, ATLTRACE se incluye por motivos de compatibilidad con versiones anteriores.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)<br/>
[Funciones globales de depuración e informe de errores](../../atl/reference/debugging-and-error-reporting-global-functions.md)
