---
title: Funciones globales de depuración e informes de errores
ms.date: 11/04/2016
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
ms.openlocfilehash: f7483b7473383958089b0c88d0b3c2645ddc2a4f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864895"
---
# <a name="debugging-and-error-reporting-global-functions"></a>Funciones globales de depuración e informes de errores

Estas funciones proporcionan funciones de depuración y seguimiento útiles.

|||
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|Devuelve un código de error `GetLastError` en forma de HRESULT.|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|Convierte un código de error Win32 en un valor HRESULT.|
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|Configura `IErrorInfo` para proporcionar los detalles del error a un cliente.|
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|Genera una `CAtlException`.|
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|Llame a esta función para notificar un error en función del resultado de la función de Windows `GetLastError`.|

##  <a name="atlhresultfromlasterror"></a>AtlHresultFromLastError

Devuelve el último valor de código de error del subproceso que realiza la llamada con el formato HRESULT.

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>Observaciones

`AtlHresultFromLastError` llama a `GetLastError` para obtener el último error y devuelve el error después de convertirlo en un valor HRESULT mediante la macro HRESULT_FROM_WIN32.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlcomcli. h

##  <a name="atlhresultfromwin32"></a>AtlHresultFromWin32

Convierte un código de error Win32 en un valor HRESULT.

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>Parámetros

*error*<br/>
Valor de error que se va a convertir.

### <a name="remarks"></a>Observaciones

Convierte un código de error de Win32 en un valor HRESULT mediante el HRESULT_FROM_WIN32 de macros.

> [!NOTE]
>  En lugar de usar `HRESULT_FROM_WIN32(GetLastError())`, use la función [AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror).

### <a name="requirements"></a>Requisitos

**Encabezado:** atlcomcli. h

##  <a name="atlreporterror"></a>AtlReportError

Configura la interfaz de `IErrorInfo` para proporcionar información de error a los clientes del objeto.

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

*CLSID*<br/>
de CLSID del objeto que informa del error.

*lpszDesc*<br/>
de Cadena que describe el error. Las versiones de Unicode especifican que *lpszDesc* es del tipo LPCOLESTR; la versión ANSI especifica un tipo de LPCSTR.

*suscripto*<br/>
de IID de la interfaz que define el error o GUID_NULL si el sistema operativo define el error.

*hRes*<br/>
de HRESULT que se va a devolver al autor de la llamada.

*nID*<br/>
de Identificador de recurso donde se almacena la cadena de Descripción del error. Este valor debe estar entre 0x0200 y 0xFFFF, ambos inclusive. En las compilaciones de depuración, se producirá una **aserción** si *nID* no indiza una cadena válida. En las compilaciones de versión, la cadena de Descripción del error se establecerá en "error desconocido".

*dwHelpID*<br/>
de Identificador del contexto de ayuda para el error.

*lpszHelpFile*<br/>
de La ruta de acceso y el nombre del archivo de ayuda que describe el error.

*hInst*<br/>
de Identificador del recurso. De forma predeterminada, este parámetro es `__AtlBaseModuleModule::GetResourceInstance`, donde `__AtlBaseModuleModule` es la instancia global de [CAtlBaseModule](../../atl/reference/catlbasemodule-class.md) o una clase derivada de él.

### <a name="return-value"></a>Valor devuelto

Si el parámetro *hRes* es distinto de cero, devuelve el valor de *hRes*. Si *hRes* es cero, las cuatro primeras versiones de `AtlReportError` devuelven DISP_E_EXCEPTION. Las dos últimas versiones devuelven el resultado de la macro **MAKE_HRESULT (1, FACILITY_ITF,** `nID` **)** .

### <a name="remarks"></a>Observaciones

La cadena *lpszDesc* se utiliza como la descripción de texto del error. Cuando el cliente recibe el *hRes* que devuelve de `AtlReportError`, el cliente puede tener acceso a la estructura de `IErrorInfo` para obtener más detalles sobre el error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
>  No utilice `AtlReportError` en C++ controladores Catch. Algunas invalidaciones de estas funciones usan internamente las macros de conversión de cadenas de ATL, que a su vez utilizan la función `_alloca` internamente. El uso de `AtlReportError` C++ en un controlador catch puede producir C++ excepciones en los controladores Catch.

### <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="atlthrow"></a>AtlThrow

Llame a esta función para indicar un error basado en un código de estado HRESULT.

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>Parámetros

*hora*<br/>
Valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Esta función se usa en el código de ATL y MFC en caso de que se produce una condición de error. También se puede llamar desde su propio código. La implementación predeterminada de esta función depende de la definición del símbolo _ATL_NO_EXCEPTIONS y del tipo de proyecto, MFC o ATL.

En todos los casos, esta función realiza un seguimiento de HRESULT en el depurador.

En la actualización 3 de Visual Studio 2015 y versiones posteriores, esta función tiene el atributo __declspec (noreturn) para evitar advertencias SAL falsas.

Si _ATL_NO_EXCEPTIONS no está definido en un proyecto MFC, esta función produce [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md) basándose en el valor de HRESULT.

Si _ATL_NO_EXCEPTIONS no está definido en un proyecto ATL, la función produce un [CAtlException](../../atl/reference/catlexception-class.md).

Si se define _ATL_NO_EXCEPTIONS, la función genera un error de aserción en lugar de producir una excepción.

En el caso de los proyectos ATL, es posible proporcionar su propia implementación de esta función para que ATL la use en caso de que se produzca un error. Para ello, defina su propia función con la misma firma que `AtlThrow` y #define `AtlThrow` para que sea el nombre de la función. Esto debe hacerse antes de incluir atlexcept. h (lo que significa que debe realizarse antes de incluir los encabezados ATL, ya que ATLBase. h incluye atlexcept. h). Atributo de la función `__declspec(noreturn)` para evitar advertencias SAL falsas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]

## <a name="requirements"></a>Requisitos

**Encabezado:** atldef. h

##  <a name="atlthrowlastwin32"></a>AtlThrowLastWin32

Llame a esta función para notificar un error en función del resultado de la función de Windows `GetLastError`.

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>Observaciones

Esta función realiza un seguimiento del resultado de `GetLastError` al depurador.

Si _ATL_NO_EXCEPTIONS no está definido en un proyecto MFC, esta función produce [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md) basándose en el valor devuelto por `GetLastError`.

Si _ATL_NO_EXCEPTIONS no está definido en un proyecto ATL, la función produce un [CAtlException](../../atl/reference/catlexception-class.md).

Si se define _ATL_NO_EXCEPTIONS, la función genera un error de aserción en lugar de producir una excepción.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldef. h

## <a name="see-also"></a>Consulte también

[Funciones](../../atl/reference/atl-functions.md)<br/>
[Macros de depuración e informe de errores](../../atl/reference/debugging-and-error-reporting-macros.md)
