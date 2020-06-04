---
title: Depuración y macros de informes de errores
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
ms.openlocfilehash: 69ab6e17bfb1ec85ddb5b8c19c18010a9b4f3df6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330185"
---
# <a name="debugging-and-error-reporting-macros"></a>Depuración y macros de informes de errores

Estas macros proporcionan instalaciones útiles de depuración y seguimiento.

|||
|-|-|
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|Escribe, en la ventana de salida, cualquier `_Module.Term` pérdida de interfaz que se detecta cuando se llama.|
|[_ATL_DEBUG_QI](#_atl_debug_qi)|Escribe todas las `QueryInterface` llamadas a la ventana de salida.|
|[ATLASSERT](#atlassert)|Realiza la misma funcionalidad que la macro [de _ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) que se encuentra en la biblioteca en tiempo de ejecución de C.|
|[ATLENSURE](#atlensure)|Realiza la validación de parámetros. Llame `AtlThrow` si es necesario|
|[ATLTRACENOTIMPL](#atltracenotimpl)|Envía un mensaje al dispositivo de volcado de que no se implementa la función especificada.|
|[ATLTRACE](#atltrace)|Notifica advertencias a un dispositivo de salida, como la ventana del depurador, según los indicadores y niveles indicados. Incluido para compatibilidad con versiones anteriores.|
|[ATLTRACE2](#atltrace2)|Notifica advertencias a un dispositivo de salida, como la ventana del depurador, según los indicadores y niveles indicados.|

## <a name="_atl_debug_interfaces"></a><a name="_atl_debug_interfaces"></a>_ATL_DEBUG_INTERFACES

Defina esta macro antes de incluir los `AddRef` `Release` archivos de encabezado ATL para rastrear todo y las llamadas en las interfaces de los componentes a la ventana de salida.

```
#define _ATL_DEBUG_INTERFACES
```

### <a name="remarks"></a>Observaciones

La salida de seguimiento aparecerá como se muestra a continuación:

`ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`

La primera parte de cada `ATL: QIThunk`seguimiento siempre será . A continuación se encuentra un valor que identifica la interfaz concreta *thunk* que se está utilizando. Un thunk de interfaz es un objeto utilizado para mantener un recuento de referencias y proporcionar la capacidad de seguimiento utilizada aquí. Se crea un nuevo thunk `QueryInterface` de interfaz en `IUnknown` cada llamada a excepto para las solicitudes de la interfaz (en este caso, el mismo thunk se devuelve cada vez para cumplir con las reglas de identidad de COM).

A continuación, `AddRef` verá `Release` o indicaqué qué método se llamó. A continuación, verá un valor que identifica el objeto cuyo recuento de referencias de interfaz se ha cambiado. El valor rastreado es el puntero **this** del objeto.

El recuento de referencias que se rastrea es `AddRef` el `Release` recuento de referencias en ese thunk después o se llamó. Tenga en cuenta que es posible que este recuento de referencias no coincida con el recuento de referencias del objeto. Cada thunk mantiene su propio recuento de referencias para ayudarle a cumplir plenamente con las reglas de recuento de referencias de COM.

La última información rastreada es el nombre del objeto y `AddRef` `Release` la interfaz que se ve afectada por la llamada o.

Cualquier fuga de interfaz que se detecte cuando el servidor se apaga y `_Module.Term` se llama será registrado así:

`ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`

La información proporcionada aquí se asigna directamente a la información proporcionada en las instrucciones de seguimiento anteriores, por lo que puede examinar los recuentos de referencias durante toda la vida útil de un thunk de interfaz. Además, obtendrá una indicación del recuento máximo de referencias en ese thunk de interfaz.

> [!NOTE]
> _ATL_DEBUG_INTERFACES se puede utilizar en compilaciones comerciales.

## <a name="_atl_debug_qi"></a><a name="_atl_debug_qi"></a>_ATL_DEBUG_QI

Escribe todas las `QueryInterface` llamadas a la ventana de salida.

```
#define _ATL_DEBUG_QI
```

### <a name="remarks"></a>Observaciones

Si una `QueryInterface` llamada falla, se mostrará la ventana de salida:

*nombre de la interfaz* - `failed`

## <a name="atlassert"></a><a name="atlassert"></a>ATLASSERT

La macro ATLASSERT realiza la misma funcionalidad que la macro [de _ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) que se encuentra en la biblioteca en tiempo de ejecución de C.

```
ATLASSERT(booleanExpression);
```

### <a name="parameters"></a>Parámetros

*booleanExpression*<br/>
Expresión (incluidos los punteros) que se evalúa como distinto de cero o 0.

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, ATLASSERT evalúa *booleanExpression* y genera un informe de depuración cuando el resultado es false.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldef.h

## <a name="atlensure"></a><a name="atlensure"></a>ATLENSURE

Esta macro se utiliza para validar los parámetros pasados a una función.

```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```

### <a name="parameters"></a>Parámetros

*booleanExpression*<br/>
Especifica una expresión booleana que se va a probar.

*Hr*<br/>
Especifica un código de error que se va a devolver.

### <a name="remarks"></a>Observaciones

Estas macros proporcionan un mecanismo para detectar y notificar al usuario el uso incorrecto de parámetros.

La macro llama a ATLASSERT `AtlThrow`y si se produce un error en la condición llama a .

En el caso de `AtlThrow` ATLENSURE, se llama con E_FAIL.

En el caso `AtlThrow` de ATLENSURE_THROW, se llama con el HRESULT especificado.

La diferencia entre ATLENSURE y ATLASSERT es que ATLENSURE produce una excepción en las compilaciones de versión, así como en las compilaciones de depuración.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="atltracenotimpl"></a><a name="atltracenotimpl"></a>ATLTRACENOTIMPL

En las compilaciones de depuración de ATL, envía la cadena " *funcname* is not implemented" al dispositivo de volcado y devuelve E_NOTIMPL.

```
ATLTRACENOTIMPL(funcname);
```

### <a name="parameters"></a>Parámetros

*funcname*<br/>
[en] Cadena que contiene el nombre de la función que no se implementa.

### <a name="remarks"></a>Observaciones

En las compilaciones de lanzamiento, simplemente devuelve E_NOTIMPL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** atltrace.h

## <a name="atltrace"></a><a name="atltrace"></a>ATLTRACE

Notifica advertencias a un dispositivo de salida, como la ventana del depurador, según los indicadores y niveles indicados. Incluido para compatibilidad con versiones anteriores.

```
ATLTRACE(exp);

ATLTRACE(
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```

### <a name="parameters"></a>Parámetros

*Exp*<br/>
[en] La cadena y las variables que se enviarán a la ventana de salida o a cualquier aplicación que atrape estos mensajes.

*Categoría*<br/>
[en] Tipo de evento o método sobre el que se debe notificar. Consulte las observaciones para obtener una lista de categorías.

*Nivel*<br/>
[en] El nivel de seguimiento que se debe notificar. Consulte las Observaciones para obtener más información.

*lpszFormat*<br/>
[en] Cadena con formato que se va a enviar al dispositivo de volcado.

### <a name="remarks"></a>Observaciones

Consulte [ATLTRACE2](#atltrace2) para obtener una descripción de ATLTRACE. ATLTRACE y ATLTRACE2 tienen el mismo comportamiento, ATLTRACE se incluye por compatibilidad con versiones anteriores.

## <a name="atltrace2"></a><a name="atltrace2"></a>ATLTRACE2

Notifica advertencias a un dispositivo de salida, como la ventana del depurador, según los indicadores y niveles indicados.

```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTR lpszFormat,  ...);
```

### <a name="parameters"></a>Parámetros

*Exp*<br/>
[en] Cadena que se va a enviar a la ventana de salida o a cualquier aplicación que atrape estos mensajes.

*Categoría*<br/>
[en] Tipo de evento o método sobre el que se debe notificar. Consulte las observaciones para obtener una lista de categorías.

*Nivel*<br/>
[en] El nivel de seguimiento que se debe notificar. Consulte las Observaciones para obtener más información.

*lpszFormat*<br/>
[en] Cadena `printf`de formato -style que se va a usar para crear una cadena que se va a enviar al dispositivo de volcado.

### <a name="remarks"></a>Observaciones

La forma abreviada de ATLTRACE2 escribe una cadena en la ventana de salida del depurador. La segunda forma de ATLTRACE2 también escribe la salida en la ventana de salida del depurador, pero está sujeta a la configuración de la herramienta de seguimiento ATL/MFC (consulte Ejemplo de [ATLTraceTool](../../overview/visual-cpp-samples.md)). Por ejemplo, si establece el *nivel* en 4 y la herramienta de seguimiento ATL/MFC en el nivel 0, no verá el mensaje. *puede* ser 0, 1, 2, 3 o 4. El valor predeterminado, 0, sólo informa de los problemas más graves.

El parámetro *category* enumera los indicadores de seguimiento que se han establecido. Estos indicadores corresponden a los tipos de métodos para los que desea informar. En las tablas siguientes se enumeran los indicadores de seguimiento válidos que puede utilizar para el parámetro *category.*

### <a name="atl-trace-flags"></a>Indicadores de seguimiento ATL

|Categoría ATL|Descripción|
|------------------|-----------------|
|`atlTraceGeneral`|Informes sobre todas las aplicaciones ATL. El valor predeterminado.|
|`atlTraceCOM`|Informes sobre métodos COM.|
|`atlTraceQI`|Informes sobre llamadas QueryInterface.|
|`atlTraceRegistrar`|Informes sobre el registro de objetos.|
|`atlTraceRefcount`|Informes sobre el cambio de recuento de referencias.|
|`atlTraceWindowing`|Informes sobre métodos de Windows; por ejemplo, notifica un ID de mapa de mensajes no válido.|
|`atlTraceControls`|Informes sobre controles; por ejemplo, informa cuando se destruye un control o su ventana.|
|`atlTraceHosting`|Informes de mensajes de hospedaje; por ejemplo, informa cuando se activa un cliente en un contenedor.|
|`atlTraceDBClient`|Informes sobre la plantilla de consumidor OLE DB; por ejemplo, cuando se produce un error en una llamada a GetData, la salida puede contener el valor HRESULT.|
|`atlTraceDBProvider`|Informes sobre la plantilla de proveedor OLE DB; por ejemplo, informes si se produjo un error en la creación de una columna.|
|`atlTraceSnapin`|Informes para la aplicación MMC SnapIn.|
|`atlTraceNotImpl`|Informa de que la función indicada no está implementada.|
|`atlTraceAllocation`|Informa de los mensajes impresos por las herramientas de depuración de memoria en atldbgmem.h.|

### <a name="mfc-trace-flags"></a>Indicadores de seguimiento de MFC

|Categoría MFC|Descripción|
|------------------|-----------------|
|`traceAppMsg`|Propósito general, mensajes MFC. Siempre recomendado.|
|`traceDumpContext`|Mensajes de [CDumpContext](../../mfc/reference/cdumpcontext-class.md).|
|`traceWinMsg`|Mensajes del código de control de mensajes de MFC.|
|`traceMemory`|Mensajes del código de administración de memoria de MFC.|
|`traceCmdRouting`|Mensajes del código de enrutamiento de comandos de Windows de MFC.|
|`traceHtml`|Mensajes de compatibilidad con cuadros de diálogo DHTML de MFC.|
|`traceSocket`|Mensajes de compatibilidad con sockets de MFC.|
|`traceOle`|Mensajes de compatibilidad con OLE de MFC.|
|`traceDatabase`|Mensajes de compatibilidad con bases de datos de MFC.|
|`traceInternet`|Mensajes de compatibilidad con Internet de MFC.|

Para declarar una categoría de seguimiento personalizada, declare una instancia global de la clase de la `CTraceCategory` siguiente manera:

[!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]

El nombre de categoría, MY_CATEGORY en este ejemplo, es el nombre que especifique para el parámetro *category.* El primer parámetro es el nombre de categoría que aparecerá en la herramienta de seguimiento ATL/MFC. El segundo parámetro es el nivel de seguimiento predeterminado. Este parámetro es opcional y el nivel de seguimiento predeterminado es 0.

Para utilizar una categoría definida por el usuario:

[!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]

Para especificar que desea filtrar los mensajes de seguimiento, inserte definiciones para `#include <atlbase.h>` estas macros en Stdafx.h antes de la instrucción.

Como alternativa, puede establecer el filtro en las directivas de preprocesador en el cuadro de diálogo **Páginas** de propiedades. Haga clic en la ficha **Preprocesador** y, a continuación, inserte el global en el cuadro de edición Definiciones de **preprocesador.**

Atlbase.h contiene definiciones predeterminadas de las macros ATLTRACE2 y estas definiciones se utilizarán si no define estos símbolos antes de que se procese atlbase.h.

En las compilaciones de versiones, `(void) 0`ATLTRACE2 compila en .

ATLTRACE2 limita el contenido de la cadena que se enviará al dispositivo de volcado a no más de 1023 caracteres, después de formatear.

ATLTRACE y ATLTRACE2 tienen el mismo comportamiento, ATLTRACE se incluye por compatibilidad con versiones anteriores.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)<br/>
[Depuración e informe de errores funciones globales](../../atl/reference/debugging-and-error-reporting-global-functions.md)
