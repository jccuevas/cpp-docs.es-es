---
title: CDynamicParameterAccessor (clase)
ms.date: 02/14/2018
f1_keywords:
- ATL.CDynamicParameterAccessor
- ATL::CDynamicParameterAccessor
- CDynamicParameterAccessor
- CDynamicParameterAccessor::CDynamicParameterAccessor
- CDynamicParameterAccessor.CDynamicParameterAccessor
- CDynamicParameterAccessor::GetParam
- ATL.CDynamicParameterAccessor.GetParam
- CDynamicParameterAccessor::GetParam<ctype>
- CDynamicParameterAccessor.GetParam
- GetParam
- ATL::CDynamicParameterAccessor::GetParam<ctype>
- ATL::CDynamicParameterAccessor::GetParam
- ATL::CDynamicParameterAccessor::GetParamCount
- CDynamicParameterAccessor::GetParamCount
- CDynamicParameterAccessor.GetParamCount
- GetParamCount
- ATL.CDynamicParameterAccessor.GetParamCount
- GetParamIO
- CDynamicParameterAccessor::GetParamIO
- ATL.CDynamicParameterAccessor.GetParamIO
- CDynamicParameterAccessor.GetParamIO
- ATL::CDynamicParameterAccessor::GetParamIO
- ATL::CDynamicParameterAccessor::GetParamLength
- ATL.CDynamicParameterAccessor.GetParamLength
- CDynamicParameterAccessor.GetParamLength
- CDynamicParameterAccessor::GetParamLength
- GetParamLength
- CDynamicParameterAccessor::GetParamName
- ATL.CDynamicParameterAccessor.GetParamName
- GetParamName
- CDynamicParameterAccessor.GetParamName
- ATL::CDynamicParameterAccessor::GetParamName
- CDynamicParameterAccessor::GetParamStatus
- CDynamicParameterAccessor.GetParamStatus
- ATL.CDynamicParameterAccessor.GetParamStatus
- ATL::CDynamicParameterAccessor::GetParamStatus
- GetParamStatus
- CDynamicParameterAccessor.GetParamString
- GetParamString
- CDynamicParameterAccessor::GetParamString
- ATL.CDynamicParameterAccessor.GetParamString
- ATL::CDynamicParameterAccessor::GetParamString
- CDynamicParameterAccessor.GetParamType
- CDynamicParameterAccessor:GetParamType
- CDynamicParameterAccessor::GetParamType
- ATL.CDynamicParameterAccessor.GetParamType
- GetParamType
- ATL::CDynamicParameterAccessor::GetParamType
- ATL::CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor.SetParam
- ATL.CDynamicParameterAccessor.SetParam
- SetParam
- CDynamicParameterAccessor:SetParam
- CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParamLength
- CDynamicParameterAccessor.SetParamLength
- ATL.CDynamicParameterAccessor.SetParamLength
- CDynamicParameterAccessor::SetParamLength
- SetParamLength
- CDynamicParameterAccessor::SetParamStatus
- ATL.CDynamicParameterAccessor.SetParamStatus
- ATL::CDynamicParameterAccessor::SetParamStatus
- CDynamicParameterAccessor.SetParamStatus
- SetParamStatus
- ATL.CDynamicParameterAccessor.SetParamString
- ATL::CDynamicParameterAccessor::SetParamString
- SetParamString
- CDynamicParameterAccessor::SetParamString
- CDynamicParameterAccessor.SetParamString
helpviewer_keywords:
- CDynamicParameterAccessor class
- CDynamicParameterAccessor class, constructor
- CDynamicParameterAccessor method
- GetParam method
- GetParamCount method
- GetParamIO method
- GetParamLength method
- GetParamName method
- GetParamStatus method
- GetParamString method
- GetParamType method
- SetParam method
- SetParamLength method
- SetParamStatus method
- SetParamString method
ms.assetid: 5f22626e-e80d-491f-8b3b-cedc50331960
ms.openlocfilehash: 9c326c337ff210ef9de26b3fd88c0d853832b260
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211878"
---
# <a name="cdynamicparameteraccessor-class"></a>CDynamicParameterAccessor (clase)

Similar a [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) , pero obtiene la información de parámetros que se va a establecer llamando a la interfaz [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) .

## <a name="syntax"></a>Sintaxis

```cpp
class CDynamicParameterAccessor : public CDynamicAccessor
```

## <a name="requirements"></a>Requisitos

**Encabezado**: atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[CDynamicParameterAccessor](#cdynamicparameteraccessor)|El constructor.|
|[GetParam](#getparam)|Recupera los datos de parámetros del búfer.|
|[GetParamCount](#getparamcount)|Recupera el número de parámetros en el descriptor de acceso.|
|[GetParamIO](#getparamio)|Determina si el parámetro especificado es un parámetro de entrada o salida.|
|[GetParamLength](#getparamlength)|Recupera la longitud del parámetro especificado almacenado en el búfer.|
|[GetParamName](#getparamname)|Recupera el nombre de un parámetro especificado.|
|[GetParamStatus](#getparamstatus)|Recupera el estado del parámetro especificado almacenado en el búfer.|
|[GetParamString](#getparamstring)|Recupera los datos de cadena del parámetro especificado almacenado en el búfer.|
|[GetParamType](#getparamtype)|Recupera el tipo de datos de un parámetro especificado.|
|[SetParam](#setparam)|Establece el búfer con los datos de parámetros.|
|[SetParamLength](#setparamlength)|Establece la longitud del parámetro especificado almacenado en el búfer.|
|[SetParamStatus](#setparamstatus)|Establece el estado del parámetro especificado almacenado en el búfer.|
|[SetParamString](#setparamstring)|Establece los datos de cadena del parámetro especificado almacenado en el búfer.|

## <a name="remarks"></a>Observaciones

El proveedor debe admitir `ICommandWithParameters` para que el consumidor pueda usar esta clase.

La información de parámetros se almacena en un búfer creado y administrado por esta clase. Obtenga los datos de parámetros que están en el búfer mediante [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) y [GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md).

Para ver un ejemplo en el que se muestra cómo usar esta clase para ejecutar un SQL Server procedimiento almacenado y obtener los valores de los parámetros de salida, consulte el código de ejemplo de [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) en el repositorio de [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) en github.

## <a name="cdynamicparameteraccessorcdynamicparameteraccessor"></a><a name="cdynamicparameteraccessor"></a>CDynamicParameterAccessor:: CDynamicParameterAccessor

El constructor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef CDynamicParameterAccessor _ParamClass;
CDynamicParameterAccessor(
   DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000 )
   : CDynamicAccessor(eBlobHandling, nBlobSize )
```

#### <a name="parameters"></a>Parámetros

*eBlobHandling*<br/>
Especifica cómo se van a controlar los datos del BLOB. El valor predeterminado es DBBLOBHANDLING_DEFAULT. Vea [CDynamicAccessor:: SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) para obtener una descripción de los valores de DBBLOBHANDLINGENUM.

*nBlobSize*<br/>
Tamaño máximo del BLOB en bytes; los datos de columna a través de este valor se tratan como un BLOB. El valor predeterminado es 8.000. Consulte [CDynamicAccessor:: SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) para obtener más información.

### <a name="remarks"></a>Observaciones

Vea el constructor [CDynamicAccessor:: CDynamicAccessor](../../data/oledb/cdynamicaccessor-cdynamicaccessor.md) para obtener más información sobre el control de blobs.

## <a name="cdynamicparameteraccessorgetparam"></a><a name="getparam"></a>CDynamicParameterAccessor:: GetParam

Recupera los datos que no son de cadena para un parámetro especificado del búfer de parámetros.

### <a name="syntax"></a>Sintaxis

```cpp
template <class ctype>bool GetParam(DBORDINAL nParam,
   ctype* pData) const throw();

template <class ctype> bool GetParam(TCHAR* pParamName,
   ctype* pData) const throw();

void* GetParam(DBORDINAL nParam) const throw();

void* GetParam(TCHAR* pParamName) const throw();
```

#### <a name="parameters"></a>Parámetros

*ctype*<br/>
Parámetro de plantilla que es el tipo de datos.

*nParam*<br/>
de El número de parámetro (desplazamiento desde 1). El parámetro 0 está reservado para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en la llamada al procedimiento almacenado o SQL. Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.

*pParamName*<br/>
de Nombre del parámetro.

*pData*<br/>
enuncia Puntero a la memoria que contiene los datos recuperados del búfer.

### <a name="return-value"></a>Valor devuelto

En el caso de las versiones no plantilla, apunta a la memoria que contiene los datos recuperados del búfer. En el caso de las versiones con plantilla, devuelve **true** si se realiza correctamente o **false** en caso de error.

Use `GetParam` para recuperar datos de parámetros que no son de cadena del búfer. Use [GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md) para recuperar datos de parámetros de cadena del búfer.

## <a name="cdynamicparameteraccessorgetparamcount"></a><a name="getparamcount"></a>CDynamicParameterAccessor:: GetParamCount

Recupera el número de parámetros almacenados en el búfer.

### <a name="syntax"></a>Sintaxis

```cpp
DB_UPARAMS GetParamCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Número de parámetros.

## <a name="cdynamicparameteraccessorgetparamio"></a><a name="getparamio"></a>CDynamicParameterAccessor:: GetParamIO

Determina si el parámetro especificado es un parámetro de entrada o salida.

### <a name="syntax"></a>Sintaxis

```cpp
bool GetParamIO(DBORDINAL nParam,
   DBPARAMIO* pParamIO) const throw();
```

#### <a name="parameters"></a>Parámetros

*nParam*<br/>
de El número de parámetro (desplazamiento desde 1). El parámetro 0 está reservado para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en la llamada al procedimiento almacenado o SQL. Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.

*pParamIO*<br/>
Puntero a la variable que contiene el tipo de `DBPARAMIO` (entrada o salida) del parámetro especificado. Se define de la manera siguiente:

```cpp
typedef DWORD DBPARAMIO;

enum DBPARAMIOENUM {
    DBPARAMIO_NOTPARAM   = 0,
    DBPARAMIO_INPUT      = 0x1,
    DBPARAMIO_OUTPUT     = 0x2
};
```

### <a name="return-value"></a>Valor devuelto

Devuelve **verdadero** si se realiza correctamente o **falso** en caso de error.

## <a name="cdynamicparameteraccessorgetparamlength"></a><a name="getparamlength"></a>CDynamicParameterAccessor:: GetParamLength

Recupera la longitud del parámetro especificado almacenado en el búfer.

### <a name="syntax"></a>Sintaxis

```cpp
bool GetParamLength(DBORDINAL nParam,
   DBLENGTH* pLength);

DBLENGTH* GetParamLength(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>Parámetros

*nParam*<br/>
de El número de parámetro (desplazamiento desde 1). El parámetro 0 está reservado para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en la llamada al procedimiento almacenado o SQL. Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.

*pLength*<br/>
enuncia Puntero a la variable que contiene la longitud en bytes del parámetro especificado.

### <a name="remarks"></a>Observaciones

La primera invalidación devuelve **true** si se realiza correctamente o **false** en caso de error. La segunda invalidación apunta a la memoria que contiene la longitud del parámetro.

## <a name="cdynamicparameteraccessorgetparamname"></a><a name="getparamname"></a>CDynamicParameterAccessor:: GetParamName

Recupera el nombre del parámetro especificado.

### <a name="syntax"></a>Sintaxis

```cpp
LPOLESTR GetParamName(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>Parámetros

*nParam*<br/>
de El número de parámetro (desplazamiento desde 1). El parámetro 0 está reservado para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en la llamada al procedimiento almacenado o SQL. Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.

### <a name="return-value"></a>Valor devuelto

Nombre del parámetro especificado.

## <a name="cdynamicparameteraccessorgetparamstatus"></a><a name="getparamstatus"></a>CDynamicParameterAccessor:: GetParamStatus

Recupera el estado del parámetro especificado almacenado en el búfer.

### <a name="syntax"></a>Sintaxis

```cpp
bool GetParamStatus(DBORDINAL nParam,
   DBSTATUS* pStatus);

DBSTATUS* GetParamStatus(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>Parámetros

*nParam*<br/>
de El número de parámetro (desplazamiento desde 1). El parámetro 0 está reservado para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en la llamada al procedimiento almacenado o SQL. Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.

*pStatus*<br/>
enuncia Puntero a la variable que contiene el estado de DBSTATUS del parámetro especificado. Para obtener información sobre los valores de DBSTATUS, vea [status](/previous-versions/windows/desktop/ms722617(v=vs.85)) en la *Referencia del programador de OLE DB*o busque DBSTATUS en OleDb. h.

### <a name="remarks"></a>Observaciones

La primera invalidación devuelve **true** si se realiza correctamente o **false** en caso de error. La segunda invalidación apunta a la memoria que contiene el estado del parámetro especificado.

## <a name="cdynamicparameteraccessorgetparamstring"></a><a name="getparamstring"></a>CDynamicParameterAccessor:: GetParamString

Recupera los datos de cadena del parámetro especificado almacenado en el búfer.

### <a name="syntax"></a>Sintaxis

```cpp
bool GetParamString(DBORDINAL nParam,
   CSimpleStringA& strOutput) throw();

bool GetParamString(DBORDINAL nParam,
   CSimpleStringW& strOutput) throw();

bool GetParamString(DBORDINAL nParam,
   CHAR* pBuffer,
   size_t* pMaxLen) throw();

bool GetParamString(DBORDINAL nParam,
   WCHAR* pBuffer,
   size_t* pMaxLen) throw();
```

#### <a name="parameters"></a>Parámetros

*nParam*<br/>
de El número de parámetro (desplazamiento desde 1). El parámetro 0 está reservado para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en la llamada al procedimiento almacenado o SQL. Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.

*strOutput*<br/>
enuncia Datos de cadena ANSI (`CSimpleStringA`) o Unicode (`CSimpleStringW`) del parámetro especificado. Debe pasar un parámetro de tipo `CString`, por ejemplo:

[!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-getparamstring_1.cpp)]

*pBuffer*<br/>
enuncia Puntero a los datos de cadena ANSI (**Char**) o Unicode (**WCHAR**) del parámetro especificado.

*pMaxLen*<br/>
enuncia Puntero al tamaño del búfer al que apunta *pBuffer* (en caracteres, incluido el valor nulo final).

### <a name="remarks"></a>Observaciones

Devuelve **verdadero** si se realiza correctamente o **falso** en caso de error.

Si *pBuffer* es null, este método establecerá el tamaño de búfer necesario en la memoria a la que apunta *pMaxLen* y devolverá **true** sin copiar los datos.

Este método producirá un error si el búfer *pBuffer* no es suficientemente grande para contener la cadena completa.

Use `GetParamString` para recuperar datos de parámetros de cadena del búfer. Use [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) para recuperar datos de parámetros que no son de cadena del búfer.

## <a name="cdynamicparameteraccessorgetparamtype"></a><a name="getparamtype"></a>CDynamicParameterAccessor:: GetParamType

Recupera el tipo de datos de un parámetro especificado.

### <a name="syntax"></a>Sintaxis

```cpp
bool GetParamType(DBORDINAL nParam,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>Parámetros

*nParam*<br/>
de El número de parámetro (desplazamiento desde 1). El parámetro 0 está reservado para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en la llamada al procedimiento almacenado o SQL. Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.

*pType*<br/>
enuncia Puntero a la variable que contiene el tipo de datos del parámetro especificado.

### <a name="return-value"></a>Valor devuelto

Devuelve **verdadero** si se realiza correctamente o **falso** en caso de error.

## <a name="cdynamicparameteraccessorsetparam"></a><a name="setparam"></a>CDynamicParameterAccessor:: SetParam

Establece el búfer de parámetros con los datos especificados (sin cadena).

### <a name="syntax"></a>Sintaxis

```cpp
template <class ctype>
bool SetParam(DBORDINAL nParam,
   constctype* pData,
   DBSTATUS status = DBSTATUS_S_OK) throw();

template <class ctype>
bool SetParam(TCHAR* pParamName,
   const ctype* pData,
   DBSTATUS status = DBSTATUS_S_OK) throw();
```

#### <a name="parameters"></a>Parámetros

*ctype*<br/>
Parámetro de plantilla que es el tipo de datos.

*nParam*<br/>
de El número de parámetro (desplazamiento desde 1). El parámetro 0 está reservado para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en la llamada al procedimiento almacenado o SQL. Por ejemplo:

[!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-setparam_1.cpp)]

*pParamName*<br/>
de Nombre del parámetro.

*pData*<br/>
de Puntero a la memoria que contiene los datos que se van a escribir en el búfer.

*status*<br/>
de El estado de la columna DBSTATUS. Para obtener información sobre los valores de DBSTATUS, vea [status](/previous-versions/windows/desktop/ms722617(v=vs.85)) en la *Referencia del programador de OLE DB*o busque DBSTATUS en OleDb. h.

### <a name="return-value"></a>Valor devuelto

Devuelve **verdadero** si se realiza correctamente o **falso** en caso de error.

Use `SetParam` para establecer datos de parámetros que no son de cadena en el búfer. Use [SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md) para establecer los datos de los parámetros de cadena en el búfer.

## <a name="cdynamicparameteraccessorsetparamlength"></a><a name="setparamlength"></a>CDynamicParameterAccessor:: SetParamLength

Establece la longitud del parámetro especificado almacenado en el búfer.

### <a name="syntax"></a>Sintaxis

```cpp
bool SetParamLength(DBORDINAL nParam,
   DBLENGTH length);
```

#### <a name="parameters"></a>Parámetros

*nParam*<br/>
de El número de parámetro (desplazamiento desde 1). El parámetro 0 está reservado para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en la llamada al procedimiento almacenado o SQL. Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.

*length*<br/>
de La longitud en bytes del parámetro especificado.

### <a name="remarks"></a>Observaciones

Devuelve **verdadero** si se realiza correctamente o **falso** en caso de error.

## <a name="cdynamicparameteraccessorsetparamstatus"></a><a name="setparamstatus"></a>CDynamicParameterAccessor:: SetParamStatus

Establece el estado del parámetro especificado almacenado en el búfer.

### <a name="syntax"></a>Sintaxis

```cpp
bool SetParamStatus(DBORDINAL nParam,
   DBSTATUS status);
```

#### <a name="parameters"></a>Parámetros

*nParam*<br/>
de El número de parámetro (desplazamiento desde 1). El parámetro 0 está reservado para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en la llamada al procedimiento almacenado o SQL. Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.

*status*<br/>
de Estado de DBSTATUS del parámetro especificado. Para obtener información sobre los valores de DBSTATUS, vea [status](/previous-versions/windows/desktop/ms722617(v=vs.85)) en la *Referencia del programador de OLE DB*o busque DBSTATUS en OleDb. h.

### <a name="remarks"></a>Observaciones

Devuelve **verdadero** si se realiza correctamente o **falso** en caso de error.

## <a name="cdynamicparameteraccessorsetparamstring"></a><a name="setparamstring"></a>CDynamicParameterAccessor:: SetParamString

Establece los datos de cadena del parámetro especificado almacenado en el búfer.

### <a name="syntax"></a>Sintaxis

```cpp
bool SetParamString(DBORDINAL nParam,
   constCHAR* pString,
   DBSTATUS status = DBSTATUS_S_OK) throw();bool SetParamString(DBORDINAL nParam,
   constWCHAR* pString,
   DBSTATUS status = DBSTATUS_S_OK) throw();
```

#### <a name="parameters"></a>Parámetros

*nParam*<br/>
de El número de parámetro (desplazamiento desde 1). El parámetro 0 está reservado para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en la llamada al procedimiento almacenado o SQL. Vea [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.

*pString*<br/>
de Puntero a los datos de cadena ANSI (**Char**) o Unicode (**WCHAR**) del parámetro especificado. Vea DBSTATUS en OleDb. h.

*status*<br/>
de Estado de DBSTATUS del parámetro especificado. Para obtener información sobre los valores de DBSTATUS, vea [status](/previous-versions/windows/desktop/ms722617(v=vs.85)) en la *Referencia del programador de OLE DB*o busque DBSTATUS en OleDb. h.

### <a name="remarks"></a>Observaciones

Devuelve **verdadero** si se realiza correctamente o **falso** en caso de error.

`SetParamString` producirá un error si intenta establecer una cadena mayor que el tamaño máximo especificado para *pString*.

Use `SetParamString` para establecer datos de parámetros de cadena en el búfer. Use [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para establecer datos de parámetros que no son de cadena en el búfer.

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor (Clase)](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CManualAccessor (Clase)](../../data/oledb/cmanualaccessor-class.md)
