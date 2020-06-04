---
title: IErrorRecordsImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL::IErrorRecordsImpl
- ATL.IErrorRecordsImpl
- IErrorRecordsImpl
- GetErrorDescriptionString
- IErrorRecordsImpl.GetErrorDescriptionString
- IErrorRecordsImpl::GetErrorDescriptionString
- GetErrorGUID
- IErrorRecordsImpl.GetErrorGUID
- IErrorRecordsImpl::GetErrorGUID
- GetErrorHelpContext
- IErrorRecordsImpl::GetErrorHelpContext
- IErrorRecordsImpl.GetErrorHelpContext
- IErrorRecordsImpl::GetErrorHelpFile
- GetErrorHelpFile
- IErrorRecordsImpl.GetErrorHelpFile
- IErrorRecordsImpl.GetErrorSource
- GetErrorSource
- IErrorRecordsImpl::GetErrorSource
- IErrorRecordsImpl.AddErrorRecord
- AddErrorRecord
- IErrorRecordsImpl::AddErrorRecord
- ATL::IErrorRecordsImpl::GetBasicErrorInfo
- IErrorRecordsImpl::GetBasicErrorInfo
- GetBasicErrorInfo
- ATL.IErrorRecordsImpl.GetBasicErrorInfo
- IErrorRecordsImpl.GetBasicErrorInfo
- ATL::IErrorRecordsImpl::GetCustomErrorObject
- IErrorRecordsImpl::GetCustomErrorObject
- ATL.IErrorRecordsImpl.GetCustomErrorObject
- IErrorRecordsImpl.GetCustomErrorObject
- IErrorRecordsImpl.GetErrorInfo
- IErrorRecordsImpl::GetErrorInfo
- IErrorRecordsImpl::GetErrorParameters
- ATL.IErrorRecordsImpl.GetErrorParameters
- IErrorRecordsImpl.GetErrorParameters
- GetErrorParameters
- ATL::IErrorRecordsImpl::GetErrorParameters
- IErrorRecordsImpl::GetRecordCount
- ATL::IErrorRecordsImpl::GetRecordCount
- IErrorRecordsImpl.GetRecordCount
- ATL.IErrorRecordsImpl.GetRecordCount
- IErrorRecordsImpl::m_rgErrors
- IErrorRecordsImpl.m_rgErrors
- ATL.IErrorRecordsImpl.m_rgErrors
- m_rgErrors
- ATL::IErrorRecordsImpl::m_rgErrors
helpviewer_keywords:
- IErrorRecordsImpl class
- GetErrorDescriptionString method
- GetErrorGUID method
- GetErrorHelpContext method
- GetErrorHelpFile method
- GetErrorSource method
- AddErrorRecord method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetRecordCount method
- m_rgErrors
ms.assetid: dea8e938-c5d8-45ab-86de-eb8fbf534ffb
ms.openlocfilehash: 40ac0b248e1e90dae29a787d59f6ded9581aca70
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210605"
---
# <a name="ierrorrecordsimpl-class"></a>IErrorRecordsImpl (Clase)

Implementa la interfaz OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) , agregando registros y recuperando registros de un miembro de datos ([m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)) de tipo **CAtlArray <** `RecordClass` **>** .

## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class RecordClass = ATLERRORINFO>
class IErrorRecordsImpl : public IErrorRecords
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Una clase derivada de `IErrorRecordsImpl`.

*RecordClass*<br/>
Una clase que representa un objeto de error de OLE DB.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[GetErrorDescriptionString](#geterrordescriptionstring)|Obtiene la cadena de Descripción del error de un registro de errores.|
|[GetErrorGUID](#geterrorguid)|Obtiene el GUID de error de un registro de error.|
|[GetErrorHelpContext](#geterrorhelpcontext)|Obtiene el identificador de contexto de ayuda de un registro de error.|
|[GetErrorHelpFile](#geterrorhelpfile)|Obtiene la ruta de acceso completa del archivo de ayuda de un registro de errores.|
|[GetErrorSource](#geterrorsource)|Obtiene el código fuente del error de un registro de errores.|

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[AddErrorRecord](#adderrorrecord)|Agrega un registro al objeto de error OLE DB.|
|[GetBasicErrorInfo](#getbasicerrorinfo)|Devuelve información básica sobre el error, como el código de retorno y el número de error específico del proveedor.|
|[GetCustomErrorObject](#getcustomerrorobject)|Devuelve un puntero a una interfaz en un objeto de error personalizado.|
|[GetErrorInfo](#geterrorinfo)|Devuelve un puntero de interfaz [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) en el registro especificado.|
|[GetErrorParameters](#geterrorparameters)|Devuelve los parámetros de error.|
|[GetRecordCount](#getrecordcount)|Devuelve el número de registros en el objeto de registro de OLE DB.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_rgErrors](#rgerrors)|Matriz de registros de error.|

## <a name="ierrorrecordsimplgeterrordescriptionstring"></a><a name="geterrordescriptionstring"></a>IErrorRecordsImpl:: GetErrorDescriptionString

Obtiene la cadena de Descripción del error de un registro de errores.

### <a name="syntax"></a>Sintaxis

```cpp
LPOLESTR GetErrorDescriptionString(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parámetros

*rCurError*<br/>
Un registro de `ERRORINFO` en una interfaz de `IErrorInfo`.

### <a name="return-value"></a>Valor devuelto

Puntero a una cadena que describe el error.

## <a name="ierrorrecordsimplgeterrorguid"></a><a name="geterrorguid"></a>IErrorRecordsImpl:: GetErrorGUID

Obtiene el GUID de error de un registro de error.

### <a name="syntax"></a>Sintaxis

```cpp
REFGUID GetErrorGUID(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parámetros

*rCurError*<br/>
Un registro de `ERRORINFO` en una interfaz de `IErrorInfo`.

### <a name="return-value"></a>Valor devuelto

Referencia a un GUID para el error.

## <a name="ierrorrecordsimplgeterrorhelpcontext"></a><a name="geterrorhelpcontext"></a>IErrorRecordsImpl:: GetErrorHelpContext

Obtiene el identificador de contexto de ayuda de un registro de error.

### <a name="syntax"></a>Sintaxis

```cpp
DWORD GetErrorHelpContext(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parámetros

*rCurError*<br/>
Un registro de `ERRORINFO` en una interfaz de `IErrorInfo`.

### <a name="return-value"></a>Valor devuelto

IDENTIFICADOR del contexto de ayuda para el error.

## <a name="ierrorrecordsimplgeterrorhelpfile"></a><a name="geterrorhelpfile"></a>IErrorRecordsImpl:: GetErrorHelpFile

Obtiene el nombre de la ruta de acceso del archivo de ayuda de un registro de errores.

### <a name="syntax"></a>Sintaxis

```cpp
LPOLESTR GetErrorHelpFile(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parámetros

*rCurError*<br/>
Un registro de `ERRORINFO` en una interfaz de `IErrorInfo`.

### <a name="return-value"></a>Valor devuelto

Puntero a una cadena que contiene el nombre de la ruta de acceso del archivo de ayuda para el error.

## <a name="ierrorrecordsimplgeterrorsource"></a><a name="geterrorsource"></a>IErrorRecordsImpl:: GetErrorSource

Obtiene el código fuente que produjo el error de un registro de errores.

### <a name="syntax"></a>Sintaxis

```cpp
LPOLESTR GetErrorSource(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parámetros

*rCurError*<br/>
Un registro de `ERRORINFO` en una interfaz de `IErrorInfo`.

### <a name="return-value"></a>Valor devuelto

Puntero a una cadena que contiene el código fuente para el error.

## <a name="ierrorrecordsimpladderrorrecord"></a><a name="adderrorrecord"></a>IErrorRecordsImpl:: AddErrorRecord

Agrega un registro al objeto de error OLE DB.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(AddErrorRecord )(ERRORINFO *pErrorInfo,
   DWORD dwLookupID,
   DISPPARAMS *pdispparams,
   IUnknown *punkCustomError,
   DWORD dwDynamicErrorID);
```

#### <a name="parameters"></a>Parámetros

Vea [IErrorRecords:: AddErrorRecord](/previous-versions/windows/desktop/ms725362(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="ierrorrecordsimplgetbasicerrorinfo"></a><a name="getbasicerrorinfo"></a>IErrorRecordsImpl:: GetBasicErrorInfo

Devuelve información básica sobre el error, como el código de retorno y el número de error específico del proveedor.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetBasicErrorInfo )(ULONG ulRecordNum,
   ERRORINFO *pErrorInfo);
```

#### <a name="parameters"></a>Parámetros

Vea [IErrorRecords:: GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="ierrorrecordsimplgetcustomerrorobject"></a><a name="getcustomerrorobject"></a>IErrorRecordsImpl:: GetCustomErrorObject

Devuelve un puntero a una interfaz en un objeto de error personalizado.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetCustomErrorObject )(ULONG ulRecordNum,
   REFIID riid,
   IUnknown **ppObject);
```

#### <a name="parameters"></a>Parámetros

Vea [IErrorRecords:: GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="ierrorrecordsimplgeterrorinfo"></a><a name="geterrorinfo"></a>IErrorRecordsImpl:: GetErrorInfo

Devuelve un puntero de interfaz [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) en el registro especificado.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetErrorInfo )(ULONG ulRecordNum,
   LCID lcid,
   IErrorInfo **ppErrorInfo);
```

#### <a name="parameters"></a>Parámetros

Vea [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="ierrorrecordsimplgeterrorparameters"></a><a name="geterrorparameters"></a>IErrorRecordsImpl:: GetErrorParameters

Devuelve los parámetros de error.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetErrorParameters )(ULONG ulRecordNum,
   DISPPARAMS *pdispparams);
```

#### <a name="parameters"></a>Parámetros

Vea [IErrorRecords:: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="ierrorrecordsimplgetrecordcount"></a><a name="getrecordcount"></a>IErrorRecordsImpl:: GetRecordCount

Devuelve el número de registros en el objeto de registro de OLE DB.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(GetRecordCount )(ULONG *pcRecords);
```

#### <a name="parameters"></a>Parámetros

Vea [IErrorRecords:: GetRecordCount](/previous-versions/windows/desktop/ms722724(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="ierrorrecordsimplm_rgerrors"></a><a name="rgerrors"></a>IErrorRecordsImpl:: m_rgErrors

Matriz de registros de error.

### <a name="syntax"></a>Sintaxis

```cpp
CAtlArray< RecordClass > m_rgErrors;
```

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
