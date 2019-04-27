---
title: CDBErrorInfo (Clase)
ms.date: 11/04/2016
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetBasicErrorInfo
- ATL.CDBErrorInfo.GetBasicErrorInfo
- CDBErrorInfo.GetBasicErrorInfo
- ATL::CDBErrorInfo::GetBasicErrorInfo
- GetBasicErrorInfo
- CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetCustomErrorObject
- CDBErrorInfo.GetCustomErrorObject
- ATL::CDBErrorInfo::GetCustomErrorObject
- GetCustomErrorObject
- GetErrorInfo
- ATL.CDBErrorInfo.GetErrorInfo
- CDBErrorInfo.GetErrorInfo
- ATL::CDBErrorInfo::GetErrorInfo
- CDBErrorInfo::GetErrorInfo
- ATL.CDBErrorInfo.GetErrorParameters
- CDBErrorInfo::GetErrorParameters
- ATL::CDBErrorInfo::GetErrorParameters
- CDBErrorInfo.GetErrorParameters
- GetErrorParameters
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
- GetErrorRecords
- CDBErrorInfo::GetErrorRecords
helpviewer_keywords:
- CDBErrorInfo class
- GetAllErrorInfo method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetErrorRecords method
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
ms.openlocfilehash: bc13137a4222ba51cf3745f9706353d48068a072
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209339"
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo (Clase)

Proporciona compatibilidad para el procesamiento de errores de OLE DB mediante OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) interfaz.

## <a name="syntax"></a>Sintaxis

```cpp
class CDBErrorInfo
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[GetAllErrorInfo](#getallerrorinfo)|Devuelve toda la información de error incluida en un registro de errores.|
|[GetBasicErrorInfo](#getbasicerrorinfo)|Las llamadas [IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) para devolver información básica sobre el error especificado.|
|[GetCustomErrorObject](#getcustomerrorobject)|Las llamadas [IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) para devolver un puntero a una interfaz en un objeto de error personalizado.|
|[GetErrorInfo](#geterrorinfo)|Las llamadas [IErrorRecords::GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) para devolver un `IErrorInfo` puntero de interfaz para el registro especificado.|
|[GetErrorParameters](#geterrorparameters)|Las llamadas [IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) para devolver los parámetros de error.|
|[GetErrorRecords](#geterrorrecords)|Obtiene los registros de errores para el objeto especificado.|

## <a name="remarks"></a>Comentarios

Esta interfaz devuelve uno o más registros de error al usuario. Llame a [cdberrorinfo:: Geterrorrecords](../../data/oledb/cdberrorinfo-geterrorrecords.md) primero, para obtener un recuento de registros de errores. Llame a uno del acceso a las funciones, como [cdberrorinfo:: Getallerrorinfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md), para recuperar información de error para cada registro.

## <a name="getallerrorinfo"></a> CDBErrorInfo::GetAllErrorInfo

Devuelve todos los tipos de información de error contenida en un registro de errores.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetAllErrorInfo(ULONG ulRecordNum,
   LCID lcid,  BSTR* pbstrDescription,
   BSTR* pbstrSource = NULL,
   GUID* pguid = NULL,
   DWORD* pdwHelpContext = NULL,
   BSTR* pbstrHelpFile = NULL) const throw();
```

#### <a name="parameters"></a>Parámetros

*ulRecordNum*<br/>
[in] El número de base cero del registro para el que se va a devolver información de error.

*lcid*<br/>
[in] El identificador de configuración regional de la información de error va a devolver.

*pbstrDescription*<br/>
[out] Un puntero a una descripción de texto del error o NULL si no se admite la configuración regional. Vea la sección Comentarios.

*pbstrSource*<br/>
[out] Un puntero a una cadena que contiene el nombre del componente que generó el error.

*pguid*<br/>
[out] Un puntero al GUID de la interfaz que definió el error.

*pdwHelpContext*<br/>
[out] Puntero al identificador de contexto de ayuda para el error.

*pbstrHelpFile*<br/>
[out] Un puntero a una cadena que contiene la ruta de acceso al archivo de ayuda que describe el error.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente. Consulte [IErrorRecords::GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) en el *referencia del programador de OLE DB* para otros valores devueltos.

### <a name="remarks"></a>Comentarios

El valor de salida *pbstrDescription* se obtiene internamente mediante una llamada a `IErrorInfo::GetDescription`, que establece el valor en NULL si no se admite la configuración regional, o si se cumplen las condiciones siguientes:

1. el valor de *lcid* no es de EE. UU. Inglés y

1. el valor de *lcid* es no es igual al valor devuelto por GetUserDefaultLCID.

## <a name="getbasicerrorinfo"></a> CDBErrorInfo::GetBasicErrorInfo

Las llamadas [IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) para devolver información básica sobre el error, como el código de retorno y el número de error específico del proveedor.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetBasicErrorInfo(ULONG ulRecordNum,
   ERRORINFO* pErrorInfo) const throw();
```

#### <a name="parameters"></a>Parámetros

Consulte [IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) en el *referencia del programador OLE DB*.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="getcustomerrorobject"></a> CDBErrorInfo::GetCustomErrorObject

Las llamadas [IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) para devolver un puntero a una interfaz en un objeto de error personalizado.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetCustomErrorObject(ULONG ulRecordNum,
   REFIID riid,IUnknown** ppObject) const throw();
```

#### <a name="parameters"></a>Parámetros

Consulte [IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) en el *referencia del programador OLE DB*.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="geterrorinfo"></a> CDBErrorInfo::GetErrorInfo

Las llamadas [IErrorRecords::GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) para devolver un [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) puntero de interfaz para el registro especificado.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetErrorInfo(ULONG ulRecordNum,
   LCID lcid,IErrorInfo** ppErrorInfo) const throw();
```

#### <a name="parameters"></a>Parámetros

Consulte [IErrorRecords::GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) en el *referencia del programador OLE DB*.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="geterrorparameters"></a> CDBErrorInfo::GetErrorParameters

Las llamadas [IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) para devolver los parámetros de error.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetErrorParameters(ULONG ulRecordNum,
   DISPPARAMS* pdispparams) const throw();
```

#### <a name="parameters"></a>Parámetros

Consulte [IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) en el *referencia del programador OLE DB*.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="geterrorrecords"></a> CDBErrorInfo::GetErrorRecords

Obtiene los registros de errores para el objeto especificado.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetErrorRecords(IUnknown* pUnk,
   const IID& iid,
   ULONG* pcRecords) throw();

HRESULT GetErrorRecords(ULONG* pcRecords) throw();
```

#### <a name="parameters"></a>Parámetros

*pUnk*<br/>
[in] Interfaz para el objeto que se va a obtener los registros de errores.

*iid*<br/>
[in] IID de la interfaz asociada con el error.

*pcRecords*<br/>
[out] Un puntero al número de registros de errores de (basado en uno).

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Comentarios

Utilice la primera forma de la función de si desea comprobar qué interfaz para obtener la información de error. En caso contrario, use el segundo formulario.

## <a name="see-also"></a>Vea también

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)