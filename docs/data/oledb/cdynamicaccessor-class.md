---
title: CDynamicAccessor (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
- ATL::CDynamicAccessor::AddBindEntry
- AddBindEntry
- CDynamicAccessor.AddBindEntry
- CDynamicAccessor::AddBindEntry
- ATL.CDynamicAccessor.AddBindEntry
- CDynamicAccessor::CDynamicAccessor
- ATL::CDynamicAccessor::CDynamicAccessor
- ATL.CDynamicAccessor.CDynamicAccessor
- CDynamicAccessor.CDynamicAccessor
- ATL::CDynamicAccessor::Close
- ATL.CDynamicAccessor.Close
- CDynamicAccessor.Close
- CDynamicAccessor::Close
- ATL.CDynamicAccessor.GetBlobHandling
- CDynamicAccessor::GetBlobHandling
- ATL::CDynamicAccessor::GetBlobHandling
- GetBlobHandling
- CDynamicAccessor.GetBlobHandling
- ATL::CDynamicAccessor::GetBlobSizeLimit
- CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor::GetBlobSizeLimit
- GetBlobSizeLimit
- ATL.CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor.GetBookmark
- GetBookmark
- CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetBookmark
- ATL::CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetColumnCount
- ATL::CDynamicAccessor::GetColumnCount
- CDynamicAccessor::GetColumnCount
- CDynamicAccessor.GetColumnCount
- GetColumnCount
- CDynamicAccessor.GetColumnFlags
- ATL::CDynamicAccessor::GetColumnFlags
- ATL.CDynamicAccessor.GetColumnFlags
- CDynamicAccessor::GetColumnFlags
- GetColumnFlags
- GetColumnInfo
- ATL.CDynamicAccessor.GetColumnInfo
- ATL::CDynamicAccessor::GetColumnInfo
- CDynamicAccessor.GetColumnInfo
- CDynamicAccessor::GetColumnInfo
- ATL::CDynamicAccessor::GetColumnName
- GetColumnName
- ATL.CDynamicAccessor.GetColumnName
- CDynamicAccessor::GetColumnName
- CDynamicAccessor.GetColumnName
- ATL.CDynamicAccessor.GetColumnType
- CDynamicAccessor::GetColumnType
- GetColumnType
- CDynamicAccessor.GetColumnType
- ATL::CDynamicAccessor::GetColumnType
- CDynamicAccessor.GetLength
- ATL.CDynamicAccessor.GetLength
- CDynamicAccessor::GetLength
- ATL::CDynamicAccessor::GetLength
- CDynamicAccessor.GetOrdinal
- ATL::CDynamicAccessor::GetOrdinal
- CDynamicAccessor::GetOrdinal
- ATL.CDynamicAccessor.GetOrdinal
- GetOrdinal
- ATL::CDynamicAccessor::GetStatus
- CDynamicAccessor.GetStatus
- ATL.CDynamicAccessor.GetStatus
- CDynamicAccessor::GetStatus
- GetValue
- CDynamicAccessor::GetValue<ctype>
- ATL.CDynamicAccessor.GetValue<ctype>
- CDynamicAccessor.GetValue
- CDynamicAccessor::GetValue
- ATL.CDynamicAccessor.GetValue
- ATL::CDynamicAccessor::GetValue
- ATL::CDynamicAccessor::GetValue<ctype>
- CDynamicAccessor::SetBlobHandling
- CDynamicAccessor.SetBlobHandling
- ATL::CDynamicAccessor::SetBlobHandling
- SetBlobHandling
- ATL.CDynamicAccessor.SetBlobHandling
- CDynamicAccessor::SetBlobSizeLimit
- SetBlobSizeLimit
- CDynamicAccessor.SetBlobSizeLimit
- ATL.CDynamicAccessor.SetBlobSizeLimit
- ATL::CDynamicAccessor::SetBlobSizeLimit
- ATL::CDynamicAccessor::SetLength
- CDynamicAccessor.SetLength
- CDynamicAccessor::SetLength
- ATL.CDynamicAccessor.SetLength
- CDynamicAccessor::SetStatus
- ATL::CDynamicAccessor::SetStatus
- CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetValue
- ATL::CDynamicAccessor::SetValue
- ATL::CDynamicAccessor::SetValue<ctype>
- CDynamicAccessor.SetValue
- ATL.CDynamicAccessor.SetValue<ctype>
- CDynamicAccessor::SetValue
- CDynamicAccessor::SetValue<ctype>
helpviewer_keywords:
- CDynamicAccessor class
- AddBindEntry method
- CDynamicAccessor class, constructor
- Close method
- GetBlobHandling method
- GetBlobSizeLimit method
- GetBookmark method
- GetColumnCount method
- GetColumnFlags method
- GetColumnInfo method
- GetColumnName method
- GetColumnType method
- GetLength method
- GetOrdinal method
- GetStatus method
- GetValue method
- SetBlobHandling method
- SetBlobSizeLimit method
- SetLength method
- SetStatus method
- SetValue method
ms.assetid: 374b13b7-1f09-457d-9e6b-df260ff4d178
ms.openlocfilehash: ba456f11973a33eb3b65b8de940e5be76b821f89
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461491"
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor (Clase)

Permite obtener acceso a un origen de datos cuando no tiene conocimiento del esquema de base de datos (estructura subyacente de la base de datos).

## <a name="syntax"></a>Sintaxis

```cpp
class CDynamicAccessor : public CAccessorBase
```

## <a name="requirements"></a>Requisitos

**Encabezado**: atldbcli.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[AddBindEntry](#addbindentry)|Agrega una entrada de enlace a las columnas de salida al reemplazar el descriptor de acceso de forma predeterminada.|
|[CDynamicAccessor](#cdynamicaccessor)|Crea una instancia e inicializa el `CDynamicAccessor` objeto.|
|[Cerrar](#close)|Desenlaza todas las columnas, libera la memoria asignada y libera el [IAccessor](/previous-versions/windows/desktop/ms719672) puntero de interfaz en la clase.|
|[GetBlobHandling](#getblobhandling)|Recupera el objeto binario de controlar el valor de la fila actual.|
|[GetBlobSizeLimit](#getblobsizelimit)|Recupera el tamaño máximo de BLOB en bytes.|
|[GetBookmark](#getbookmark)|Obtiene el marcador de la fila actual.|
|[GetColumnCount](#getcolumncount)|Recupera el número de columnas del conjunto de filas.|
|[GetColumnFlags](#getcolumnflags)|Recupera las características de la columna.|
|[GetColumnInfo](#getcolumninfo)|Recupera los metadatos de columna.|
|[GetColumnName](#getcolumnname)|Recupera el nombre de una columna especificada.|
|[GetColumnType](#getcolumntype)|Recupera el tipo de datos de una columna especificada.|
|[GetLength](#getlength)|Recupera la longitud máxima posible de una columna en bytes.|
|[GetOrdinal](#getordinal)|Recupera el índice de columna dado un nombre de columna.|
|[GetStatus](#getstatus)|Recupera el estado de una columna especificada.|
|[GetValue](#getvalue)|Recupera los datos desde el búfer.|
|[SetBlobHandling](#setblobhandling)|Establece el objeto binario de controlar el valor de la fila actual.|
|[SetBlobSizeLimit](#setblobsizelimit)|Establece el tamaño máximo de BLOB en bytes.|
|[SetLength](#setlength)|Establece la longitud de la columna en bytes.|
|[SetStatus](#setstatus)|Establece el estado de una columna especificada.|
|[SetValue](#setvalue)|Almacena los datos en el búfer.|

## <a name="remarks"></a>Comentarios

Use `CDynamicAccessor` métodos para obtener información de columna como nombres de columna, el número de columnas, tipo de datos y así sucesivamente. Utilizamos esta información de columna para crear un descriptor de acceso de forma dinámica en tiempo de ejecución.

La información de columna se almacena en un búfer que se crea y administrado por esta clase. Obtener datos desde el búfer mediante [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md).

Para obtener una explicación y ejemplos del uso de las clases de descriptor de acceso dinámico, consulte [utilizar descriptores de acceso dinámico](../../data/oledb/using-dynamic-accessors.md).

## <a name="addbindentry"></a> CDynamicAccessor:: AddBindEntry

Agrega una entrada de enlace a las columnas de salida.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT AddBindEntry(const DBCOLUMNINFO& info) throw();
```

#### <a name="parameters"></a>Parámetros

*Info*<br/>
[in] Un `DBCOLUMNINFO` estructura que contiene información de columna. Vea "Estructuras DBCOLUMNINFO" en [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704) en el *referencia del programador OLE DB*.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

Utilice este método cuando se reemplaza el descriptor de acceso predeterminado creado con `CDynamicAccessor` (consulte [¿cómo puedo recuperar datos?](../../data/oledb/fetching-data.md)).

## <a name="cdynamicaccessor"></a> CDynamicAccessor:: CDynamicAccessor

Crea una instancia e inicializa el `CDynamicAccessor` objeto.

### <a name="syntax"></a>Sintaxis

```cpp
CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000);
```

#### <a name="parameters"></a>Parámetros

*eBlobHandling*<br/>
Especifica cómo se controlan los datos de objeto binario grande (BLOB). El valor predeterminado es DBBLOBHANDLING_DEFAULT. Consulte [SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) para obtener una descripción de los valores DBBLOBHANDLINGENUM.

*nBlobSize*<br/>
El tamaño máximo de BLOB en bytes; datos de la columna a través de este valor se tratan como un BLOB. El valor predeterminado es 8000. Consulte [SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) para obtener más información.

### <a name="remarks"></a>Comentarios

Si usa el constructor para inicializar el `CDynamicAccessor` de objeto, puede especificar cómo unir los BLOBs. Los bLOBs pueden contener datos binarios tales como gráficos, sonido o compilado el código. El comportamiento predeterminado consiste en tratar las columnas más de 8.000 bytes como BLOBs y vuelva enlazarlos a un `ISequentialStream` objeto. Sin embargo, puede especificar un valor diferente para que sea el tamaño del BLOB.

También puede especificar cómo `CDynamicAccessor` controla los datos de columna que se consideran datos BLOB: pueden controlar datos BLOB de la manera predeterminada; puede omitir (no enlazar) datos BLOB; o bien puede enlazar datos BLOB en la memoria asignada por el proveedor.

## <a name="close"></a> CDynamicAccessor:: Close

Desenlaza todas las columnas, libera la memoria asignada y libera el [IAccessor](/previous-versions/windows/desktop/ms719672) puntero de interfaz en la clase.

### <a name="syntax"></a>Sintaxis

```cpp
void Close() throw();
```

## <a name="getblobhandling"></a> CDynamicAccessor:: Getblobhandling

Recupera el objeto binario de controlar el valor de la fila actual.

### <a name="syntax"></a>Sintaxis

```cpp
const DBBLOBHANDLINGENUM GetBlobHandling() const;
```

### <a name="remarks"></a>Comentarios

Devuelve el valor de control de BLOB *eBlobHandling* como lo establece [SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md).

## <a name="getblobsizelimit"></a> CDynamicAccessor:: Getblobsizelimit

Recupera el tamaño máximo de BLOB en bytes.

### <a name="syntax"></a>Sintaxis

```cpp
const DBLENGTH GetBlobSizeLimit() const;
```

### <a name="remarks"></a>Comentarios

Devuelve el valor de control de BLOB *nBlobSize* como lo establece [SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md).

## <a name="getbookmark"></a> CDynamicAccessor:: GetBookmark

Obtiene el marcador de la fila actual.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetBookmark(CBookmark< >* pBookmark) const throw();
```

#### <a name="parameters"></a>Parámetros

*pBookmark*<br/>
[out] Un puntero a la [CBookmark](../../data/oledb/cbookmark-class.md) objeto.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

Deberá establecer `DBPROP_IRowsetLocate` en VARIANT_TRUE para recuperar un marcador.

## <a name="getcolumncount"></a> CDynamicAccessor:: GetColumnCount

Recupera el número de columnas.

### <a name="syntax"></a>Sintaxis

```cpp
DBORDINAL GetColumnCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Recupera el número de columnas.

## <a name="getcolumnflags"></a> CDynamicAccessor:: Getcolumnflags

Recupera las características de la columna.

### <a name="syntax"></a>Sintaxis

```cpp
bool GetColumnFlags(DBORDINAL nColumn, 
   DBCOLUMNFLAGS* pFlags) const throw();
```

#### <a name="parameters"></a>Parámetros

*nColumn*<br/>
[in] El número de columna. Números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

*pFlags*<br/>
[out] Un puntero a una máscara de bits que describe las características de la columna. Vea "Tipo enumerado DBCOLUMNFLAGS" en [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704) en el *referencia del programador OLE DB*.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** si las características de la columna se ha recuperado correctamente. En caso contrario, devuelve **false**.

### <a name="remarks"></a>Comentarios

El número de columna se desvía de uno. Columna cero es un caso especial; es el marcador si está disponible.

## <a name="getcolumninfo"></a> CDynamicAccessor:: GetColumnInfo

Devuelve los metadatos de columna necesarios para la mayoría de los consumidores.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetColumnInfo(IRowset* pRowset, 
   DBORDINAL* pColumns, 
   DBCOLUMNINFO** ppColumnInfo, 
   OLECHAR** ppStringsBuffer) throw();
```

#### <a name="parameters"></a>Parámetros

*pRowset*<br/>
[in] Un puntero a la [IRowset](/previous-versions/windows/desktop/ms720986) interfaz.

*pColumns*<br/>
[out] Un puntero a la memoria en el que se va a devolver el número de columnas del conjunto de filas; Este número incluye la columna de marcador, si hay alguno.

*ppColumnInfo*<br/>
[out] Un puntero a la memoria en el que se va a devolver una matriz de `DBCOLUMNINFO` estructuras. Vea "Estructuras DBCOLUMNINFO" en [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704) en el *referencia del programador OLE DB*.

*ppStringsBuffer*<br/>
[out] Un puntero a la memoria en el que se va a devolver un puntero al almacenamiento de todos los valores de cadena (nombres usan dentro de *columnid* o para *pwszName*) dentro de un bloque de asignación único.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

Consulte [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704) en el *referencia del programador de OLE DB* para obtener información sobre los tipos de datos `DBORDINAL`, `DBCOLUMNINFO`, y `OLECHAR`.

## <a name="getcolumnname"></a> CDynamicAccessor:: Getcolumnname

Recupera el nombre de la columna especificada.

### <a name="syntax"></a>Sintaxis

```cpp
LPOLESTR GetColumnName(DBORDINAL nColumn) const throw();
```

#### <a name="parameters"></a>Parámetros

*nColumn*<br/>
[in] El número de columna. Números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

### <a name="return-value"></a>Valor devuelto

El nombre de la columna especificada.

## <a name="getcolumntype"></a> CDynamicAccessor:: Getcolumntype

Recupera el tipo de datos de una columna especificada.

### <a name="syntax"></a>Sintaxis

```cpp
bool GetColumnType(DBORDINAL nColumn, 
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>Parámetros

*nColumn*<br/>
[in] El número de columna. Números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

*PEscriba*<br/>
[out] Un puntero al tipo de datos de la columna especificada.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** en caso de éxito o **false** en caso de error.

## <a name="getlength"></a> CDynamicAccessor:: GetLength

Recupera la longitud de la columna especificada.

### <a name="syntax"></a>Sintaxis

```cpp
bool GetLength(DBORDINAL nColumn, 
   DBLENGTH* pLength) const throw();

bool GetLength(const CHAR* pColumnName, 
   DBLENGTH* pLength) const throw();

bool GetLength(const WCHAR* pColumnName, 
   DBLENGTH* pLength) const throw();
```

#### <a name="parameters"></a>Parámetros

*nColumn*<br/>
[in] El número de columna. Números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

*pColumnName*<br/>
[in] Un puntero a una cadena de caracteres que contiene el nombre de columna.

*pLength*<br/>
[out] Un puntero al entero que contiene la longitud de la columna en bytes.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** si se encuentra la columna especificada. En caso contrario, esta función devuelve **false**.

### <a name="remarks"></a>Comentarios

El primer reemplazo toma el número de columna y la segunda y tercera toman el nombre de columna en formato ANSI o Unicode, respectivamente.

## <a name="getordinal"></a> CDynamicAccessor:: GetOrdinal

Recupera el número de columna dado un nombre de columna.

### <a name="syntax"></a>Sintaxis

```cpp
bool GetOrdinal(const CHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();

bool GetOrdinal(const WCHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();
```

#### <a name="parameters"></a>Parámetros

*pColumnName*<br/>
[in] Un puntero a una cadena de caracteres que contiene el nombre de columna.

*pOrdinal*<br/>
[out] Un puntero al número de columna.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** si se encuentra una columna con el nombre especificado. En caso contrario, esta función devuelve **false**.

## <a name="getstatus"></a> CDynamicAccessor:: GetStatus

Recupera el estado de la columna especificada.

### <a name="syntax"></a>Sintaxis

```cpp
bool GetStatus(DBORDINAL nColumn, 
   DBSTATUS* pStatus) const throw();

bool GetStatus(const CHAR* pColumnName,
   DBSTATUS* pStatus) const throw();

bool GetStatus(const WCHAR* pColumnName,
   DBSTATUS* pStatus) const throw();
```

#### <a name="parameters"></a>Parámetros

*nColumn*<br/>
[in] El número de columna. Números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

*pColumnName*<br/>
[in] Un puntero a una cadena de caracteres que contiene el nombre de columna.

*pStatus*<br/>
[out] Un puntero a la variable que contiene el estado de la columna. Consulte [DBSTATUS](/previous-versions/windows/desktop/ms722617) en el *referencia del programador de OLE DB* para obtener más información.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** si se encuentra la columna especificada. En caso contrario, esta función devuelve **false**.

## <a name="getvalue"></a> CDynamicAccessor:: GetValue

Recupera los datos de una columna especificada.

### <a name="syntax"></a>Sintaxis

```cpp
void* GetValue(DBORDINAL nColumn) const throw();

void* GetValue(const CHAR* pColumnName) const throw();

void* GetValue(const WCHAR* pColumnName) const throw();

template < class ctype >
bool GetValue(DBORDINAL nColumn, ctype* pData) const throw();

template < class ctype >
bool GetValue(const CHAR* pColumnName, ctype* pData) const throw();

template < class ctype >
bool GetValue(const WCHAR* pColumnName, ctype* pData) const throw();
```

#### <a name="parameters"></a>Parámetros

*ctype*<br/>
[in] Un parámetro de plantilla que controla cualquier tipo de datos, excepto los tipos de cadena (`CHAR*`, `WCHAR*`), que requieren un tratamiento especial. `GetValue` usa el tipo de datos adecuado en función de lo que se especifica aquí.

*nColumn*<br/>
[in] El número de columna. Números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

*pColumnName*<br/>
[in] El nombre de columna.

*pData*<br/>
[out] Puntero al contenido de la columna especificada.

### <a name="return-value"></a>Valor devuelto

Si desea pasar datos de cadena, utilice las versiones sin plantilla de `GetValue`. Las versiones sin plantilla de este método devuelven `void*`, que apunta a la parte del búfer que contiene los datos de la columna especificada. Devuelve NULL si no se encuentra la columna.

Para los demás tipos de datos, es más fácil de usar las versiones con plantillas de `GetValue`. Devuelven las versiones con plantilla **true** en caso de éxito o **false** en caso de error.

### <a name="remarks"></a>Comentarios

Utilice las versiones sin plantilla para devolver las columnas que contienen cadenas y las versiones con plantilla para las columnas que contienen otros tipos de datos.

En modo de depuración, obtendrá una aserción si el tamaño de *pData* no es igual al tamaño de la columna a la que señala.

## <a name="setblobhandling"></a> CDynamicAccessor:: Setblobhandling

Establece el objeto binario de controlar el valor de la fila actual.

### <a name="syntax"></a>Sintaxis

```cpp
bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);
```

#### <a name="parameters"></a>Parámetros

*eBlobHandling*<br/>
Especifica cómo se controlan los datos de BLOB. Pueden tomar los siguientes valores:

- DBBLOBHANDLING_DEFAULT: Controlar los datos de columna mayor que *nBlobSize* (como lo establece `SetBlobSizeLimit`) como datos de BLOB y recuperarlo a través de un `ISequentialStream` o `IStream` objeto. Esta opción intentará enlazar cada columna que contiene los datos ocupan más *nBlobSize* o aparece como DBTYPE_IUNKNOWN como datos de BLOB.

- DBBLOBHANDLING_NOSTREAMS: Controlar los datos de columna mayor que *nBlobSize* (como lo establece `SetBlobSizeLimit`) como datos de BLOB y recuperarlo a través de referencia en la memoria asignada por el proveedor, propia del consumidor. Esta opción es útil para las tablas que tienen más de una columna BLOB y el proveedor admite solo un `ISequentialStream` objeto por el descriptor de acceso.

- DBBLOBHANDLING_SKIP: Omitir (no enlazar) columnas calificar como contenedor de BLOBs (el descriptor de acceso no enlazar o recuperar el valor de columna pero todavía recuperará el estado de la columna y la longitud).

### <a name="remarks"></a>Comentarios

Debe llamar a `SetBlobHandling` antes de llamar a `Open`.

El método de constructor [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) establece el objeto binario de control de valor a DBBLOBHANDLING_DEFAULT.

## <a name="setblobsizelimit"></a> CDynamicAccessor:: Setblobsizelimit

Establece el tamaño máximo de BLOB en bytes.

### <a name="syntax"></a>Sintaxis

```cpp
void SetBlobSizeLimit(DBLENGTH nBlobSize);
```

#### <a name="parameters"></a>Parámetros

*nBlobSize*<br/>
Especifica el límite de tamaño BLOB.

### <a name="remarks"></a>Comentarios

Establece el tamaño máximo de BLOB en bytes; datos de columna mayores que este valor se tratan como un BLOB. Algunos proveedores proporcionan extremadamente grandes tamaños para las columnas (por ejemplo, 2 GB). En lugar de intentar asignar memoria para una columna de este tamaño, se haría normalmente intenta enlazar estas columnas como BLOBs. En este modo no tiene que asignar toda la memoria, pero todavía puede leer todos los datos sin temor de truncamiento. Sin embargo, hay algunos casos en los que desea forzar `CDynamicAccessor` para enlazar las columnas de gran tamaño en sus tipos de datos nativos. Para ello, llame a `SetBlobSizeLimit` antes de llamar a `Open`.

El método de constructor [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) establece el tamaño máximo de BLOB en un valor predeterminado de 8.000 bytes.

## <a name="setlength"></a> CDynamicAccessor:: SetLength

Establece la longitud de la columna especificada.

### <a name="syntax"></a>Sintaxis

```cpp
bool SetLength(DBORDINAL nColumn, 
   DBLENGTH nLength)throw();

bool SetLength(const CHAR* pColumnName, 
   DBLENGTH nLength) throw();

bool SetLength(const WCHAR* pColumnName, 
   DBLENGTH nLength) throw();
```

#### <a name="parameters"></a>Parámetros

*nColumn*<br/>
[in] El número de columna. Números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

*nLength*<br/>
[in] La longitud de la columna en bytes.

*pColumnName*<br/>
[in] Un puntero a una cadena de caracteres que contiene el nombre de columna.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** si la longitud de la columna especificada está establecida correctamente. En caso contrario, esta función devuelve **false**.

## <a name="setstatus"></a> CDynamicAccessor:: SetStatus

Establece el estado de la columna especificada.

### <a name="syntax"></a>Sintaxis

```cpp
bool SetStatus(DBORDINAL nColumn, 
   DBSTATUS status)throw();

bool SetStatus(const CHAR* pColumnName, 
   DBSTATUS status) throw();

bool SetStatus(const WCHAR* pColumnName, 
   DBSTATUS status) throw();
```

#### <a name="parameters"></a>Parámetros

*nColumn*<br/>
[in] El número de columna. Números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

*status*<br/>
[in] El estado de la columna. Consulte [DBSTATUS](/previous-versions/windows/desktop/ms722617) en el *referencia del programador de OLE DB* para obtener más información.

*pColumnName*<br/>
[in] Un puntero a una cadena de caracteres que contiene el nombre de columna.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** si el estado de la columna especificada está establecido correctamente. En caso contrario, esta función devuelve **false**.

## <a name="setvalue"></a> CDynamicAccessor:: SetValue

Almacena los datos en una columna especificada.

### <a name="syntax"></a>Sintaxis

```cpp
template <class ctype>
bool SetValue( 
   DBORDINAL nColumn, 
   constctype& data) throw( );

template <class ctype>  
bool SetValue( 
   const CHAR * pColumnName, 
   const ctype& data) throw( );

template <class ctype> 
bool SetValue(
   const WCHAR *pColumnName,
   const ctype& data) throw( );
```

#### <a name="parameters"></a>Parámetros

*ctype*<br/>
[in] Un parámetro de plantilla que controla cualquier tipo de datos, excepto los tipos de cadena (`CHAR*`, `WCHAR*`), que requieren un tratamiento especial. `GetValue` usa el tipo de datos adecuado en función de lo que se especifica aquí.

*pColumnName*<br/>
[in] Un puntero a una cadena de caracteres que contiene el nombre de columna.

*data*<br/>
[in] Puntero a la memoria que contiene los datos.

*nColumn*<br/>
[in] El número de columna. Números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

### <a name="return-value"></a>Valor devuelto

Si desea establecer los datos de cadena, utilice las versiones sin plantilla de `GetValue`. Las versiones sin plantilla de este método devuelven `void*`, que apunta a la parte del búfer que contiene los datos de la columna especificada. Devuelve NULL si no se encuentra la columna.

Para los demás tipos de datos, es más fácil de usar las versiones con plantillas de `GetValue`. Devuelven las versiones con plantilla **true** en caso de éxito o **false** en caso de error.

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor (Clase)](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor (Clase)](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor (Clase)](../../data/oledb/cmanualaccessor-class.md)