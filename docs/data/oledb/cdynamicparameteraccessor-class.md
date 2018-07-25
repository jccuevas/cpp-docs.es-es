---
title: CDynamicParameterAccessor (clase) | Microsoft Docs
ms.custom: ''
ms.date: 02/14/2018
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4395f19367cac69ad1e1d20b3d637437b5614603
ms.sourcegitcommit: b217daee32d3413cf33753d9b4dc35a0022b1bfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233482"
---
# <a name="cdynamicparameteraccessor-class"></a>CDynamicParameterAccessor (clase)

Similar a [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) , pero obtiene la información de parámetros que se puede establecer mediante una llamada a la [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) interfaz.

## <a name="syntax"></a>Sintaxis

```cpp
class CDynamicParameterAccessor : public CDynamicAccessor
```

## <a name="requirements"></a>Requisitos

**Encabezado**: atldbcli.h

## <a name="members"></a>Miembros

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

## <a name="remarks"></a>Comentarios

El proveedor debe admitir `ICommandWithParameters` para que el consumidor pueda usar esta clase.

La información de parámetros se almacena en un búfer creado y administrado por esta clase. Obtenga los datos de parámetros que están en el búfer mediante [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) y [GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md).

Para obtener un ejemplo que muestra cómo utilizar esta clase para ejecutar un procedimiento almacenado de SQL Server y obtener los valores de parámetro de salida, vea el [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) código de ejemplo en el [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) repositorio de GitHub.

## <a name="cdynamicparameteraccessor"></a> CDynamicParameterAccessor:: CDynamicParameterAccessor
El constructor.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
      typedef CDynamicParameterAccessor _ParamClass;  
CDynamicParameterAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,   
   DBLENGTH nBlobSize = 8000 )   
   : CDynamicAccessor(eBlobHandling, nBlobSize )  
```  
  
#### <a name="parameters"></a>Parámetros  
 *eBlobHandling*  
 Especifica cómo se controlan los datos de BLOB. El valor predeterminado es DBBLOBHANDLING_DEFAULT. Consulte [CDynamicAccessor:: Setblobhandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) para obtener una descripción de los valores DBBLOBHANDLINGENUM.  
  
 *nBlobSize*  
 El tamaño máximo de BLOB en bytes; datos de la columna a través de este valor se tratan como un BLOB. El valor predeterminado es 8000. Consulte [CDynamicAccessor:: Setblobsizelimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) para obtener más información.  
  
### <a name="remarks"></a>Comentarios  
 Consulte la [CDynamicAccessor:: CDynamicAccessor](../../data/oledb/cdynamicaccessor-cdynamicaccessor.md) constructor para obtener más información sobre el control de blobs. 

## <a name="getparam"></a> CDynamicParameterAccessor:: GetParam
Recupera los datos que no son cadenas para un parámetro especificado desde el búfer de parámetro.  
  
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
 *ctype*  
 Un parámetro de plantilla que es el tipo de datos.  
  
 *nParam*  
 [in] El número de parámetro (desplazamiento de 1). Parámetro 0 se reserva para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en el SQL o una llamada al procedimiento almacenado. Consulte [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
 *pParamName*  
 [in] El nombre del parámetro.  
  
 *pData*  
 [out] Puntero a la memoria que contiene los datos recuperados desde el búfer.  
  
### <a name="return-value"></a>Valor devuelto  
 En las versiones sin plantilla, apunta a la memoria que contiene los datos recuperados desde el búfer. En las versiones con plantilla, devuelve **true** en caso de éxito o **false** en caso de error.  
  
 Use `GetParam` para recuperar datos de parámetro que no sean del búfer. Use [GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md) para recuperar datos de parámetro de cadena desde el búfer.  

## <a name="getparamcount"></a> CDynamicParameterAccessor:: Getparamcount
Recupera el número de parámetros almacenados en el búfer.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
DB_UPARAMS GetParamCount() const throw();  
  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de parámetros.  

## <a name="getparamio"></a> CDynamicParameterAccessor:: Getparamio
Determina si el parámetro especificado es un parámetro de entrada o salida.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
bool GetParamIO(DBORDINAL nParam,   
   DBPARAMIO* pParamIO) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *nParam*  
 [in] El número de parámetro (desplazamiento de 1). Parámetro 0 se reserva para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en el SQL o una llamada al procedimiento almacenado. Consulte [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
 *pParamIO*  
 Un puntero a la variable que contiene el `DBPARAMIO` (entrada o salida) de tipo del parámetro especificado. Se define como sigue:  
  
```cpp  
typedef DWORD DBPARAMIO;  
  
enum DBPARAMIOENUM {  
    DBPARAMIO_NOTPARAM   = 0,  
    DBPARAMIO_INPUT      = 0x1,  
    DBPARAMIO_OUTPUT     = 0x2  
};  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** en caso de éxito o **false** en caso de error.  

## <a name="getparamlength"></a> CDynamicParameterAccessor:: Getparamlength
Recupera la longitud del parámetro especificado almacenado en el búfer.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
bool GetParamLength(DBORDINAL nParam,  
  DBLENGTH* pLength);  

DBLENGTH* GetParamLength(DBORDINAL nParam) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *nParam*  
 [in] El número de parámetro (desplazamiento de 1). Parámetro 0 se reserva para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en el SQL o una llamada al procedimiento almacenado. Consulte [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
 *pLength*  
 [out] Un puntero a la variable que contiene la longitud en bytes del parámetro especificado.  
  
### <a name="remarks"></a>Comentarios  
 La primera invalidación devuelve **true** en caso de éxito o **false** en caso de error. La segunda invalidación apunta a la memoria que contiene la longitud del parámetro. 

## <a name="getparamname"></a> CDynamicParameterAccessor:: Getparamname
Recupera el nombre del parámetro especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
      LPOLESTR GetParamName(DBORDINAL nParam) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *nParam*  
 [in] El número de parámetro (desplazamiento de 1). Parámetro 0 se reserva para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en el SQL o una llamada al procedimiento almacenado. Consulte [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
### <a name="return-value"></a>Valor devuelto  
 El nombre del parámetro especificado.  

## <a name="getparamstatus"></a> CDynamicParameterAccessor:: Getparamstatus
Recupera el estado del parámetro especificado almacenado en el búfer.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
bool GetParamStatus(DBORDINAL nParam,  
  DBSTATUS* pStatus);  

DBSTATUS* GetParamStatus(DBORDINAL nParam) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *nParam*  
 [in] El número de parámetro (desplazamiento de 1). Parámetro 0 se reserva para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en el SQL o una llamada al procedimiento almacenado. Consulte [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
 *pStatus*  
 [out] Un puntero a la variable que contiene el estado DBSTATUS del parámetro especificado. Para obtener información sobre los valores DBSTATUS, consulte [estado](https://msdn.microsoft.com/library/ms722617.aspx) en el *referencia del programador de OLE DB*, o busque DBSTATUS en oledb.h.  
  
### <a name="remarks"></a>Comentarios  
 La primera invalidación devuelve **true** en caso de éxito o **false** en caso de error. La segunda invalidación apunta a la memoria que contiene el estado del parámetro especificado.

## <a name="getparamstring"></a> CDynamicParameterAccessor:: Getparamstring
Recupera los datos de cadena del parámetro especificado almacenado en el búfer.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
bool GetParamString(DBORDINAL nParam,  
  CSimpleStringA& strOutput) throw();bool GetParamString(DBORDINAL nParam,  
  CSimpleStringW& strOutput) throw();bool GetParamString(DBORDINAL nParam,  
  CHAR* pBuffer,  
   size_t* pMaxLen) throw();bool GetParamString(DBORDINAL nParam,  
  WCHAR* pBuffer,  
   size_t* pMaxLen) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *nParam*  
 [in] El número de parámetro (desplazamiento de 1). Parámetro 0 se reserva para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en el SQL o una llamada al procedimiento almacenado. Consulte [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
 *strOutput*  
 [out] El ANSI (`CSimpleStringA`) o Unicode (`CSimpleStringW`) los datos del parámetro especificado de cadena. Debe pasar un parámetro de tipo `CString`, por ejemplo:  
  
 [!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-getparamstring_1.cpp)]  
  
 *pBuffer*  
 [out] Un puntero a ANSI (**CHAR**) o Unicode (**WCHAR**) los datos del parámetro especificado de cadena.  
  
 *pMaxLen*  
 [out] Un puntero al tamaño del búfer señalado por *pBuffer* (en caracteres, incluido el carácter nulo final).  
  
### <a name="remarks"></a>Comentarios  
 Devuelve **true** en caso de éxito o **false** en caso de error.  
  
 Si *pBuffer* es NULL, este método establecerá el tamaño de búfer necesario en la memoria que apunta *pMaxLen* y devolver **true** sin copiar los datos.  
  
 Este método se producirá un error si el búfer *pBuffer* no es lo suficientemente grande como para contener la cadena completa.  
  
 Use `GetParamString` para recuperar datos de parámetro de cadena desde el búfer. Use [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) para recuperar datos de parámetro que no sean del búfer.  

## <a name="getparamtype"></a> CDynamicParameterAccessor:: GetParamType
Recupera el tipo de datos de un parámetro especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
bool GetParamType(DBORDINAL nParam,  
  DBTYPE* pType) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *nParam*  
 [in] El número de parámetro (desplazamiento de 1). Parámetro 0 se reserva para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en el SQL o una llamada al procedimiento almacenado. Consulte [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
 *PEscriba*  
 [out] Un puntero a la variable que contiene el tipo de datos del parámetro especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** en caso de éxito o **false** en caso de error.  

## <a name="setparam"></a> CDynamicParameterAccessor:: SetParam
Establece el búfer de parámetro con los datos (que no son de cadena) especificados.  
  
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
 *ctype*  
 Un parámetro de plantilla que es el tipo de datos.  
  
 *nParam*  
 [in] El número de parámetro (desplazamiento de 1). Parámetro 0 se reserva para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en el SQL o una llamada al procedimiento almacenado. Por ejemplo:  
  
 [!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-setparam_1.cpp)]  
  
 *pParamName*  
 [in] El nombre del parámetro.  
  
 *pData*  
 [in] Puntero a la memoria que contiene los datos se escriban en el búfer.  
  
 *status*  
 [in] El estado de la columna DBSTATUS. Para obtener información sobre los valores DBSTATUS, consulte [estado](https://msdn.microsoft.com/library/ms722617.aspx) en el *referencia del programador de OLE DB*, o busque DBSTATUS en oledb.h.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** en caso de éxito o **false** en caso de error.  
  
 Use `SetParam` para establecer datos de parámetro que no sean en el búfer. Use [SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md) para establecer datos de parámetro de cadena en el búfer.  

## <a name="setparamlength"></a> CDynamicParameterAccessor:: Setparamlength
Establece la longitud del parámetro especificado almacenado en el búfer.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
bool SetParamLength(DBORDINAL nParam,  
   DBLENGTH length);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *nParam*  
 [in] El número de parámetro (desplazamiento de 1). Parámetro 0 se reserva para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en el SQL o una llamada al procedimiento almacenado. Consulte [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
 *length*  
 [in] La longitud en bytes del parámetro especificado.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve **true** en caso de éxito o **false** en caso de error. 

## <a name="setparamstatus"></a> CDynamicParameterAccessor:: Setparamstatus
Establece el estado del parámetro especificado almacenado en el búfer.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
bool SetParamStatus(DBORDINAL nParam,  
   DBSTATUS status);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *nParam*  
 [in] El número de parámetro (desplazamiento de 1). Parámetro 0 se reserva para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en el SQL o una llamada al procedimiento almacenado. Consulte [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
 *status*  
 [in] El estado DBSTATUS del parámetro especificado. Para obtener información sobre los valores DBSTATUS, consulte [estado](https://msdn.microsoft.com/library/ms722617.aspx) en el *referencia del programador de OLE DB*, o busque DBSTATUS en oledb.h.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve **true** en caso de éxito o **false** en caso de error. 

## <a name="setparamstring"></a> CDynamicParameterAccessor:: Setparamstring
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
 *nParam*  
 [in] El número de parámetro (desplazamiento de 1). Parámetro 0 se reserva para los valores devueltos. El número de parámetro es el índice del parámetro en función de su orden en el SQL o una llamada al procedimiento almacenado. Consulte [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para obtener un ejemplo.  
  
 *pString*  
 [in] Un puntero a ANSI (**CHAR**) o Unicode (**WCHAR**) los datos del parámetro especificado de cadena. Vea DBSTATUS en oledb.h.  
  
 *status*  
 [in] El estado DBSTATUS del parámetro especificado. Para obtener información sobre los valores DBSTATUS, consulte [estado](https://msdn.microsoft.com/library/ms722617.aspx) en el *referencia del programador de OLE DB*, o busque DBSTATUS en oledb.h.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve **true** en caso de éxito o **false** en caso de error.  
  
 `SetParamString` se producirá un error si intenta establecer una cadena que es mayor que el tamaño máximo especificado para *pString*.  
  
 Use `SetParamString` para establecer datos de parámetro de cadena en el búfer. Use [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) para establecer datos de parámetro que no sean en el búfer. 

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)  
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)  
[CAccessor (Clase)](../../data/oledb/caccessor-class.md)  
[CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)  
[CManualAccessor (Clase)](../../data/oledb/cmanualaccessor-class.md)  
