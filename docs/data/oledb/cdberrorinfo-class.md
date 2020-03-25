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
- CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetBasicErrorInfo
- ATL.CDBErrorInfo.GetBasicErrorInfo
- CDBErrorInfo.GetBasicErrorInfo
- ATL::CDBErrorInfo::GetBasicErrorInfo
- CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetCustomErrorObject
- CDBErrorInfo.GetCustomErrorObject
- ATL::CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetErrorInfo
- CDBErrorInfo.GetErrorInfo
- ATL::CDBErrorInfo::GetErrorInfo
- CDBErrorInfo::GetErrorInfo
- ATL.CDBErrorInfo.GetErrorParameters
- CDBErrorInfo::GetErrorParameters
- ATL::CDBErrorInfo::GetErrorParameters
- CDBErrorInfo.GetErrorParameters
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
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
ms.openlocfilehash: 8c91beb2a305604f663d5e81b4a534a1699705cf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212045"
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo (Clase)

Proporciona compatibilidad para el procesamiento de errores de OLE DB mediante la interfaz OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) .

## <a name="syntax"></a>Sintaxis

```cpp
class CDBErrorInfo
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[GetAllErrorInfo](#getallerrorinfo)|Devuelve toda la información de error contenida en un registro de errores.|
|[GetBasicErrorInfo](#getbasicerrorinfo)|Llama a [IErrorRecords:: GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) para devolver información básica sobre el error especificado.|
|[GetCustomErrorObject](#getcustomerrorobject)|Llama a [IErrorRecords:: GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) para devolver un puntero a una interfaz en un objeto de error personalizado.|
|[GetErrorInfo](#geterrorinfo)|Llama a [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) para devolver un puntero de interfaz `IErrorInfo` al registro especificado.|
|[GetErrorParameters](#geterrorparameters)|Llama a [IErrorRecords:: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) para devolver los parámetros de error.|
|[GetErrorRecords](#geterrorrecords)|Obtiene los registros de error para el objeto especificado.|

## <a name="remarks"></a>Observaciones

Esta interfaz devuelve uno o más registros de error al usuario. Llame a [CDBErrorInfo:: GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md) en primer lugar para obtener un recuento de registros de error. A continuación, llame a una de las funciones de acceso, como [CDBErrorInfo:: GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md), para recuperar la información de error de cada registro.

## <a name="cdberrorinfogetallerrorinfo"></a><a name="getallerrorinfo"></a>CDBErrorInfo:: GetAllErrorInfo

Devuelve todos los tipos de información de error contenidos en un registro de errores.

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
de Número de base cero del registro para el que se va a devolver información de error.

*lcid*<br/>
de IDENTIFICADOR de configuración regional de la información de error que se va a devolver.

*pbstrDescription*<br/>
enuncia Un puntero a una descripción de texto del error o NULL si no se admite la configuración regional. Vea la sección Comentarios.

*pbstrSource*<br/>
enuncia Puntero a una cadena que contiene el nombre del componente que generó el error.

*pguid*<br/>
enuncia Puntero al GUID de la interfaz que definió el error.

*pdwHelpContext*<br/>
enuncia Puntero al identificador de contexto de ayuda para el error.

*pbstrHelpFile*<br/>
enuncia Puntero a una cadena que contiene la ruta de acceso al archivo de ayuda que describe el error.

### <a name="return-value"></a>Valor devuelto

S_OK,si se ejecuta correctamente. Vea [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) en la *Referencia del programador de OLE DB* para otros valores devueltos.

### <a name="remarks"></a>Observaciones

El valor de salida de *pbstrDescription* se obtiene internamente mediante una llamada a `IErrorInfo::GetDescription`, que establece el valor en NULL si no se admite la configuración regional o si se cumplen las dos condiciones siguientes:

1. el valor de *LCID* no es el Inglés de EE. UU.

1. el valor de *LCID* no es igual al valor devuelto por GetUserDefaultLCID.

## <a name="cdberrorinfogetbasicerrorinfo"></a><a name="getbasicerrorinfo"></a>CDBErrorInfo:: GetBasicErrorInfo

Llama a [IErrorRecords:: GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) para devolver información básica sobre el error, como el código de retorno y el número de error específico del proveedor.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetBasicErrorInfo(ULONG ulRecordNum,
   ERRORINFO* pErrorInfo) const throw();
```

#### <a name="parameters"></a>Parámetros

Vea [IErrorRecords:: GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

## <a name="cdberrorinfogetcustomerrorobject"></a><a name="getcustomerrorobject"></a>CDBErrorInfo:: GetCustomErrorObject

Llama a [IErrorRecords:: GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) para devolver un puntero a una interfaz en un objeto de error personalizado.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetCustomErrorObject(ULONG ulRecordNum,
   REFIID riid,IUnknown** ppObject) const throw();
```

#### <a name="parameters"></a>Parámetros

Vea [IErrorRecords:: GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

## <a name="cdberrorinfogeterrorinfo"></a><a name="geterrorinfo"></a>CDBErrorInfo:: GetErrorInfo

Llama a [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) para devolver un puntero de interfaz [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) al registro especificado.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetErrorInfo(ULONG ulRecordNum,
   LCID lcid,IErrorInfo** ppErrorInfo) const throw();
```

#### <a name="parameters"></a>Parámetros

Vea [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

## <a name="cdberrorinfogeterrorparameters"></a><a name="geterrorparameters"></a>CDBErrorInfo:: GetErrorParameters

Llama a [IErrorRecords:: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) para devolver los parámetros de error.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetErrorParameters(ULONG ulRecordNum,
   DISPPARAMS* pdispparams) const throw();
```

#### <a name="parameters"></a>Parámetros

Vea [IErrorRecords:: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

## <a name="cdberrorinfogeterrorrecords"></a><a name="geterrorrecords"></a>CDBErrorInfo:: GetErrorRecords

Obtiene los registros de error para el objeto especificado.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetErrorRecords(IUnknown* pUnk,
   const IID& iid,
   ULONG* pcRecords) throw();

HRESULT GetErrorRecords(ULONG* pcRecords) throw();
```

#### <a name="parameters"></a>Parámetros

*pUnk*<br/>
de Interfaz del objeto para el que se van a obtener los registros de error.

*suscripto*<br/>
de IID de la interfaz asociada al error.

*pcRecords*<br/>
enuncia Puntero al recuento (basado en uno) de los registros de errores.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Use la primera forma de la función si desea comprobar la interfaz de la que se va a obtener la información de error. De lo contrario, use el segundo formulario.

## <a name="see-also"></a>Consulte también

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
