---
title: Depuración e informe de errores funciones globales
ms.date: 11/04/2016
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
ms.openlocfilehash: f7636b1f4e13340b223edd8c63c39bbeb21c8bd0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330209"
---
# <a name="debugging-and-error-reporting-global-functions"></a>Depuración e informe de errores funciones globales

Estas funciones proporcionan instalaciones útiles de depuración y seguimiento.

|||
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|Devuelve `GetLastError` un código de error en forma de HRESULT.|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|Convierte un código de error Win32 en un valor HRESULT.|
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|Se `IErrorInfo` configura para proporcionar detalles de error a un cliente.|
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|Genera una `CAtlException`.|
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|Llame a esta función para notificar un error en función del resultado de la función de Windows `GetLastError`.|

## <a name="atlhresultfromlasterror"></a><a name="atlhresultfromlasterror"></a>AtlHResultFromLastError

Devuelve el último valor de código de error del subproceso que realiza la llamada con el formato HRESULT.

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>Observaciones

`AtlHresultFromLastError`llama `GetLastError` para obtener el último error y devuelve el error después de convertirlo en un HRESULT mediante la macro HRESULT_FROM_WIN32.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlcomcli.h

## <a name="atlhresultfromwin32"></a><a name="atlhresultfromwin32"></a>AtlHresultFromWin32

Convierte un código de error Win32 en un valor HRESULT.

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>Parámetros

*error*<br/>
El valor de error que se va a convertir.

### <a name="remarks"></a>Observaciones

Convierte un código de error Win32 en un HRESULT, utilizando la macro HRESULT_FROM_WIN32.

> [!NOTE]
> En lugar `HRESULT_FROM_WIN32(GetLastError())`de utilizar , utilice la función [AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror).

### <a name="requirements"></a>Requisitos

**Encabezado:** atlcomcli.h

## <a name="atlreporterror"></a><a name="atlreporterror"></a>AtlReportError

Configura la `IErrorInfo` interfaz para proporcionar información de error a los clientes del objeto.

```
HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
[en] El CLSID del objeto notificando el error.

*lpszDesc*<br/>
[en] Cadena que describe el error. Las versiones Unicode especifican que *lpszDesc* es de tipo LPCOLESTR; la versión ANSI especifica un tipo de LPCSTR.

*Iid*<br/>
[en] El IID de la interfaz que define el error o GUID_NULL si el error es definido por el sistema operativo.

*hRes*<br/>
[en] El valor HRESULT que desea que se devuelva al autor de la llamada.

*nID*<br/>
[en] Identificador de recurso donde se almacena la cadena de descripción del error. Este valor debe estar entre 0x0200 y 0xFFFF, inclusive. En compilaciones de depuración, se producirá un **ASSERT** si *nID* no indexa una cadena válida. En las compilaciones de la versión, la cadena de descripción del error se establecerá en "Error desconocido."

*dwHelpID*<br/>
[en] Identificador de contexto de ayuda para el error.

*lpszHelpFile*<br/>
[en] La ruta de acceso y el nombre del archivo de ayuda que describe el error.

*hInst*<br/>
[en] El identificador del recurso. De forma predeterminada, `__AtlBaseModuleModule::GetResourceInstance`este `__AtlBaseModuleModule` parámetro es , donde está la instancia global de [CAtlBaseModule](../../atl/reference/catlbasemodule-class.md) o una clase derivada de él.

### <a name="return-value"></a>Valor devuelto

Si el *hRes* parámetro es distinto de cero, devuelve el valor de *hRes*. Si *hRes* es cero, las `AtlReportError` primeras cuatro versiones de return DISP_E_EXCEPTION. Las dos últimas versiones devuelven el resultado de la macro **MAKE_HRESULT( 1, FACILITY_ITF,** `nID` **).**

### <a name="remarks"></a>Observaciones

La cadena *lpszDesc* se utiliza como la descripción de texto del error. Cuando el cliente recibe las *hRes* que devuelve `AtlReportError` `IErrorInfo` de , el cliente puede tener acceso a la estructura para obtener detalles sobre el error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
> No usar `AtlReportError` en controladores de captura C++. Algunas invalidaciones de estas funciones utilizan las macros de `_alloca` conversión de cadenas ATL internamente, que a su vez utilizan la función internamente. El `AtlReportError` uso de un controlador catch de C++ puede provocar excepciones en los controladores catch de C++.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="atlthrow"></a><a name="atlthrow"></a>AtlThrow

Llame a esta función para indicar un error basado en un código de estado HRESULT.

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>Parámetros

*Hr*<br/>
Valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Esta función es utilizada por el código ATL y MFC en caso de una condición de error. También se puede llamar desde su propio código. La implementación predeterminada de esta función depende de la definición del símbolo _ATL_NO_EXCEPTIONS y del tipo de proyecto, MFC o ATL.

En todos los casos, esta función rastrea el HRESULT hasta el depurador.

En Visual Studio 2015 Update 3 y versiones posteriores, esta función se atribuye __declspec(noreturn) para evitar advertencias SAL falsas.

Si _ATL_NO_EXCEPTIONS no está definido en un proyecto MFC, esta función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o un [COleException](../../mfc/reference/coleexception-class.md) basado en el valor de la HRESULT.

Si _ATL_NO_EXCEPTIONS no está definido en un proyecto ATL, la función produce una [excepción CAtlException](../../atl/reference/catlexception-class.md).

Si se define _ATL_NO_EXCEPTIONS, la función provoca un error de aserción en lugar de producir una excepción.

Para los proyectos ATL, es posible proporcionar su propia implementación de esta función para que la utilice ATL en caso de error. Para ello, defina su propia función `AtlThrow` con `AtlThrow` la misma firma y #define que sea el nombre de la función. Esto debe hacerse antes de incluir atlexcept.h (lo que significa que debe hacerse antes de incluir cualquier encabezado ATL ya que atlbase.h incluye atlexcept.h). Atribuya la función `__declspec(noreturn)` para evitar advertencias SAL falsas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]

## <a name="requirements"></a>Requisitos

**Encabezado:** atldef.h

## <a name="atlthrowlastwin32"></a><a name="atlthrowlastwin32"></a>AtlThrowLastWin32

Llame a esta función para notificar un error en función del resultado de la función de Windows `GetLastError`.

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>Observaciones

Esta función rastrea el resultado del `GetLastError` depurador.

Si _ATL_NO_EXCEPTIONS no está definido en un proyecto MFC, esta función produce una [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o un [COleException](../../mfc/reference/coleexception-class.md) en función del valor devuelto por `GetLastError`.

Si _ATL_NO_EXCEPTIONS no está definido en un proyecto ATL, la función produce una [excepción CAtlException](../../atl/reference/catlexception-class.md).

Si se define _ATL_NO_EXCEPTIONS, la función provoca un error de aserción en lugar de producir una excepción.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldef.h

## <a name="see-also"></a>Consulte también

[Functions](../../atl/reference/atl-functions.md)<br/>
[Depuración y macros de informes de errores](../../atl/reference/debugging-and-error-reporting-macros.md)
