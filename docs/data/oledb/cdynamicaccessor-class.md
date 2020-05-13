---
title: CDynamicAccessor (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
- ATL::CDynamicAccessor::AddBindEntry
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
ms.openlocfilehash: 160e5b6d8eb4b45850dc071299413d9ad2cfcee9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212072"
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor (Clase)

Permite tener acceso a un origen de datos cuando no se conoce el esquema de la base de datos (la estructura subyacente de la base de datos).

## <a name="syntax"></a>Sintaxis

```cpp
class CDynamicAccessor : public CAccessorBase
```

## <a name="requirements"></a>Requisitos

**Encabezado**: atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[AddBindEntry](#addbindentry)|Agrega una entrada de enlace a las columnas de salida al reemplazar el descriptor de acceso predeterminado.|
|[CDynamicAccessor](#cdynamicaccessor)|Crea una instancia e inicializa el objeto `CDynamicAccessor`.|
|[Close](#close)|Desenlaza todas las columnas, libera la memoria asignada y libera el puntero de interfaz [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) en la clase.|
|[GetBlobHandling](#getblobhandling)|Recupera el valor de control de BLOBs para la fila actual.|
|[GetBlobSizeLimit](#getblobsizelimit)|Recupera el tamaño máximo del BLOB en bytes.|
|[GetBookmark](#getbookmark)|Recupera el marcador de la fila actual.|
|[GetColumnCount](#getcolumncount)|Recupera el número de columnas del conjunto de filas.|
|[GetColumnFlags](#getcolumnflags)|Recupera las características de la columna.|
|[GetColumnInfo](#getcolumninfo)|Recupera los metadatos de la columna.|
|[GetColumnName](#getcolumnname)|Recupera el nombre de una columna especificada.|
|[GetColumnType](#getcolumntype)|Recupera el tipo de datos de una columna especificada.|
|[GetLength](#getlength)|Recupera la longitud máxima posible de una columna en bytes.|
|[GetOrdinal](#getordinal)|Recupera el índice de la columna dado un nombre de columna.|
|[GetStatus](#getstatus)|Recupera el estado de una columna especificada.|
|[GetValue](#getvalue)|Recupera los datos del búfer.|
|[SetBlobHandling](#setblobhandling)|Establece el valor de control de BLOBs para la fila actual.|
|[SetBlobSizeLimit](#setblobsizelimit)|Establece el tamaño máximo del BLOB en bytes.|
|[SetLength](#setlength)|Establece la longitud de la columna en bytes.|
|[SetStatus](#setstatus)|Establece el estado de una columna especificada.|
|[SetValue](#setvalue)|Almacena los datos en el búfer.|

## <a name="remarks"></a>Observaciones

Utilice `CDynamicAccessor` métodos para obtener información de columna, como nombres de columna, número de columnas, tipo de datos, etc. A continuación, use esta información de columna para crear un descriptor de acceso dinámicamente en tiempo de ejecución.

La información de la columna se almacena en un búfer creado y administrado por esta clase. Obtener datos del búfer mediante [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md).

Para obtener una explicación y ejemplos del uso de las clases de descriptor de acceso dinámico, vea usar descriptores de [acceso dinámicos](../../data/oledb/using-dynamic-accessors.md).

## <a name="cdynamicaccessoraddbindentry"></a><a name="addbindentry"></a>CDynamicAccessor:: AddBindEntry

Agrega una entrada de enlace a las columnas de salida.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT AddBindEntry(const DBCOLUMNINFO& info) throw();
```

#### <a name="parameters"></a>Parámetros

*info*<br/>
de `DBCOLUMNINFO` estructura que contiene información de columna. Vea "estructuras DBCOLUMNINFOs" en [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) en la *Referencia del programador de OLE DB*.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Use este método al reemplazar el descriptor de acceso predeterminado creado con `CDynamicAccessor` (vea [¿cómo se capturan datos?](../../data/oledb/fetching-data.md)).

## <a name="cdynamicaccessorcdynamicaccessor"></a><a name="cdynamicaccessor"></a>CDynamicAccessor:: CDynamicAccessor

Crea una instancia e inicializa el objeto `CDynamicAccessor`.

### <a name="syntax"></a>Sintaxis

```cpp
CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000);
```

#### <a name="parameters"></a>Parámetros

*eBlobHandling*<br/>
Especifica cómo se van a controlar los datos de objetos binarios grandes (BLOB). El valor predeterminado es DBBLOBHANDLING_DEFAULT. Consulte [SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) para obtener una descripción de los valores de DBBLOBHANDLINGENUM.

*nBlobSize*<br/>
Tamaño máximo del BLOB en bytes; los datos de columna a través de este valor se tratan como un BLOB. El valor predeterminado es 8.000. Consulte [SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) para obtener más información.

### <a name="remarks"></a>Observaciones

Si utiliza el constructor para inicializar el objeto `CDynamicAccessor`, puede especificar cómo enlazará los BLOBs. Los blobs pueden contener datos binarios como gráficos, sonido o código compilado. El comportamiento predeterminado consiste en tratar las columnas más de 8.000 bytes como Blobs e intentar enlazarlas a un objeto `ISequentialStream`. Sin embargo, puede especificar un valor diferente para que sea el tamaño del BLOB.

También puede especificar cómo administra `CDynamicAccessor` los datos de columna que se califican como datos de BLOB: puede administrar los datos de BLOBs de la manera predeterminada. puede omitir (no enlazar) los datos de BLOBs; o bien, puede enlazar datos de BLOBs en la memoria asignada por el proveedor.

## <a name="cdynamicaccessorclose"></a><a name="close"></a>CDynamicAccessor:: Close

Desenlaza todas las columnas, libera la memoria asignada y libera el puntero de interfaz [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) en la clase.

### <a name="syntax"></a>Sintaxis

```cpp
void Close() throw();
```

## <a name="cdynamicaccessorgetblobhandling"></a><a name="getblobhandling"></a>CDynamicAccessor:: GetBlobHandling

Recupera el valor de control de BLOBs para la fila actual.

### <a name="syntax"></a>Sintaxis

```cpp
const DBBLOBHANDLINGENUM GetBlobHandling() const;
```

### <a name="remarks"></a>Observaciones

Devuelve el valor de control de BLOB *eBlobHandling* tal y como lo establece [SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md).

## <a name="cdynamicaccessorgetblobsizelimit"></a><a name="getblobsizelimit"></a>CDynamicAccessor:: GetBlobSizeLimit

Recupera el tamaño máximo del BLOB en bytes.

### <a name="syntax"></a>Sintaxis

```cpp
const DBLENGTH GetBlobSizeLimit() const;
```

### <a name="remarks"></a>Observaciones

Devuelve el valor de control de BLOB *nBlobSize* tal y como lo establece [SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md).

## <a name="cdynamicaccessorgetbookmark"></a><a name="getbookmark"></a>CDynamicAccessor:: GetBookmark

Recupera el marcador de la fila actual.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetBookmark(CBookmark< >* pBookmark) const throw();
```

#### <a name="parameters"></a>Parámetros

*pBookmark*<br/>
enuncia Puntero al objeto [CBookmark](../../data/oledb/cbookmark-class.md) .

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Debe establecer `DBPROP_IRowsetLocate` en VARIANT_TRUE para recuperar un marcador.

## <a name="cdynamicaccessorgetcolumncount"></a><a name="getcolumncount"></a>CDynamicAccessor:: GetColumnCount

Recupera el número de columnas.

### <a name="syntax"></a>Sintaxis

```cpp
DBORDINAL GetColumnCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

El número de columnas recuperadas.

## <a name="cdynamicaccessorgetcolumnflags"></a><a name="getcolumnflags"></a>CDynamicAccessor:: GetColumnFlags

Recupera las características de la columna.

### <a name="syntax"></a>Sintaxis

```cpp
bool GetColumnFlags(DBORDINAL nColumn,
   DBCOLUMNFLAGS* pFlags) const throw();
```

#### <a name="parameters"></a>Parámetros

*nColumn*<br/>
de El número de columna. Los números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

*pFlags*<br/>
enuncia Puntero a una máscara de máscara que describe las características de las columnas. Vea el tema sobre el tipo enumerado DBCOLUMNFLAGS en [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) en la *Referencia del programador de OLE DB*.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** si las características de la columna se han recuperado correctamente. En caso contrario, devuelve **false**.

### <a name="remarks"></a>Observaciones

El número de columna está desplazado desde uno. La columna cero es un caso especial; Si está disponible, es el marcador.

## <a name="cdynamicaccessorgetcolumninfo"></a><a name="getcolumninfo"></a>CDynamicAccessor:: GetColumnInfo

Devuelve los metadatos de columna que necesitan la mayoría de los consumidores.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetColumnInfo(IRowset* pRowset,
   DBORDINAL* pColumns,
   DBCOLUMNINFO** ppColumnInfo,
   OLECHAR** ppStringsBuffer) throw();
```

#### <a name="parameters"></a>Parámetros

*pRowset*<br/>
de Puntero a la interfaz [IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85)) .

*pColumns*<br/>
enuncia Puntero a la memoria en la que se va a devolver el número de columnas del conjunto de filas; Este número incluye la columna de marcador, si hay alguna.

*ppColumnInfo*<br/>
enuncia Puntero a la memoria en la que se va a devolver una matriz de estructuras `DBCOLUMNINFO`. Vea "estructuras DBCOLUMNINFOs" en [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) en la *Referencia del programador de OLE DB*.

*ppStringsBuffer*<br/>
enuncia Puntero a la memoria en la que se va a devolver un puntero al almacenamiento de todos los valores de cadena (nombres usados en *columnid* o para *pwszName*) dentro de un único bloque de asignación.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Vea [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) en la *Referencia del programador de OLE DB* para obtener información sobre los tipos de datos `DBORDINAL`, `DBCOLUMNINFO`y `OLECHAR`.

## <a name="cdynamicaccessorgetcolumnname"></a><a name="getcolumnname"></a>CDynamicAccessor:: GetColumnName

Recupera el nombre de la columna especificada.

### <a name="syntax"></a>Sintaxis

```cpp
LPOLESTR GetColumnName(DBORDINAL nColumn) const throw();
```

#### <a name="parameters"></a>Parámetros

*nColumn*<br/>
de El número de columna. Los números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

### <a name="return-value"></a>Valor devuelto

El nombre de la columna especificada.

## <a name="cdynamicaccessorgetcolumntype"></a><a name="getcolumntype"></a>CDynamicAccessor:: GetColumnType

Recupera el tipo de datos de una columna especificada.

### <a name="syntax"></a>Sintaxis

```cpp
bool GetColumnType(DBORDINAL nColumn,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>Parámetros

*nColumn*<br/>
de El número de columna. Los números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

*pType*<br/>
enuncia Puntero al tipo de datos de la columna especificada.

### <a name="return-value"></a>Valor devuelto

Devuelve **verdadero** si se realiza correctamente o **falso** en caso de error.

## <a name="cdynamicaccessorgetlength"></a><a name="getlength"></a>CDynamicAccessor:: GetLength

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
de El número de columna. Los números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

*pColumnName*<br/>
de Puntero a una cadena de caracteres que contiene el nombre de columna.

*pLength*<br/>
enuncia Puntero al entero que contiene la longitud de la columna en bytes.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** si se encuentra la columna especificada. De lo contrario, esta función devuelve **false**.

### <a name="remarks"></a>Observaciones

La primera invalidación toma el número de columna y la segunda y tercera invalidaciones toman el nombre de la columna en formato ANSI o Unicode, respectivamente.

## <a name="cdynamicaccessorgetordinal"></a><a name="getordinal"></a>CDynamicAccessor:: GetOrdinal

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
de Puntero a una cadena de caracteres que contiene el nombre de columna.

*pOrdinal*<br/>
enuncia Puntero al número de columna.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** si se encuentra una columna con el nombre especificado. De lo contrario, esta función devuelve **false**.

## <a name="cdynamicaccessorgetstatus"></a><a name="getstatus"></a>CDynamicAccessor:: GetStatus

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
de El número de columna. Los números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

*pColumnName*<br/>
de Puntero a una cadena de caracteres que contiene el nombre de columna.

*pStatus*<br/>
enuncia Puntero a la variable que contiene el estado de la columna. Vea [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) en la *Referencia del programador de OLE DB* para obtener más información.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** si se encuentra la columna especificada. De lo contrario, esta función devuelve **false**.

## <a name="cdynamicaccessorgetvalue"></a><a name="getvalue"></a>CDynamicAccessor:: GetValue

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
de Un parámetro con plantilla que controla cualquier tipo de datos excepto los tipos de cadena (`CHAR*`, `WCHAR*`), que requieren un tratamiento especial. `GetValue` usa el tipo de datos adecuado en función de lo que especifique aquí.

*nColumn*<br/>
de El número de columna. Los números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

*pColumnName*<br/>
de Nombre de la columna.

*pData*<br/>
enuncia Puntero al contenido de la columna especificada.

### <a name="return-value"></a>Valor devuelto

Si desea pasar datos de cadena, use las versiones no plantilla de `GetValue`. Las versiones no plantilla de este método devuelven `void*`, que apunta a la parte del búfer que contiene los datos de columna especificados. Devuelve NULL si no se encuentra la columna.

Para el resto de tipos de datos, es más fácil usar las versiones con plantilla de `GetValue`. Las versiones con plantilla devuelven **true** si se ejecuta correctamente o **false** en caso de error.

### <a name="remarks"></a>Observaciones

Use las versiones no plantilla para devolver las columnas que contienen cadenas y las versiones con plantilla para las columnas que contienen otros tipos de datos.

En el modo de depuración, obtendrá una aserción si el tamaño de *pdata* no es igual al tamaño de la columna a la que señala.

## <a name="cdynamicaccessorsetblobhandling"></a><a name="setblobhandling"></a>CDynamicAccessor:: SetBlobHandling

Establece el valor de control de BLOBs para la fila actual.

### <a name="syntax"></a>Sintaxis

```cpp
bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);
```

#### <a name="parameters"></a>Parámetros

*eBlobHandling*<br/>
Especifica cómo se van a controlar los datos del BLOB. Puede tomar los siguientes valores:

- DBBLOBHANDLING_DEFAULT: controlar los datos de las columnas mayores que *nBlobSize* (como se establece en `SetBlobSizeLimit`) como datos BLOB y recuperarlos a través de un objeto `ISequentialStream` o `IStream`. Esta opción intentará enlazar cada columna que contenga datos de más de *nBlobSize* o que se muestren como DBTYPE_IUNKNOWN como datos de BLOB.

- DBBLOBHANDLING_NOSTREAMS: controlar los datos de las columnas mayores que *nBlobSize* (como se establece en `SetBlobSizeLimit`) como datos BLOB y recuperarlos a través de la referencia en la memoria asignada por el consumidor y la asignación del proveedor. Esta opción es útil para las tablas que tienen más de una columna BLOB y el proveedor solo admite un objeto `ISequentialStream` por descriptor de acceso.

- DBBLOBHANDLING_SKIP: omitir (no enlazar) columnas que cumplan los blobs que los contienen (el descriptor de acceso no enlazará ni recuperará el valor de la columna, pero seguirá recuperando el estado y la longitud de la columna).

### <a name="remarks"></a>Observaciones

Debe llamar a `SetBlobHandling` antes de llamar a `Open`.

El método de constructor [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) establece el valor de control de BLOB en DBBLOBHANDLING_DEFAULT.

## <a name="cdynamicaccessorsetblobsizelimit"></a><a name="setblobsizelimit"></a>CDynamicAccessor:: SetBlobSizeLimit

Establece el tamaño máximo del BLOB en bytes.

### <a name="syntax"></a>Sintaxis

```cpp
void SetBlobSizeLimit(DBLENGTH nBlobSize);
```

#### <a name="parameters"></a>Parámetros

*nBlobSize*<br/>
Especifica el límite de tamaño del BLOB.

### <a name="remarks"></a>Observaciones

Establece el tamaño máximo del BLOB en bytes; los datos de columna mayores que este valor se tratan como un BLOB. Algunos proveedores proporcionan tamaños sumamente grandes para las columnas (por ejemplo, 2 GB). En lugar de intentar asignar memoria para una columna de este tamaño, normalmente intentaría enlazar estas columnas como BLOBs. De este modo, no tiene que asignar toda la memoria, pero todavía puede leer todos los datos sin temor de truncamiento. Sin embargo, hay algunos casos en los que podría querer forzar `CDynamicAccessor` para enlazar columnas grandes en sus tipos de datos nativos. Para ello, llame a `SetBlobSizeLimit` antes de llamar a `Open`.

El método de constructor [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) establece el tamaño máximo del BLOB en un valor predeterminado de 8.000 bytes.

## <a name="cdynamicaccessorsetlength"></a><a name="setlength"></a>CDynamicAccessor:: SetLength

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
de El número de columna. Los números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

*nLength*<br/>
de Longitud de la columna en bytes.

*pColumnName*<br/>
de Puntero a una cadena de caracteres que contiene el nombre de columna.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** si la longitud de la columna especificada se establece correctamente. De lo contrario, esta función devuelve **false**.

## <a name="cdynamicaccessorsetstatus"></a><a name="setstatus"></a>CDynamicAccessor:: SetStatus

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
de El número de columna. Los números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

*status*<br/>
de El estado de la columna. Vea [DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) en la *Referencia del programador de OLE DB* para obtener más información.

*pColumnName*<br/>
de Puntero a una cadena de caracteres que contiene el nombre de columna.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** si el estado de la columna especificada se establece correctamente. De lo contrario, esta función devuelve **false**.

## <a name="cdynamicaccessorsetvalue"></a><a name="setvalue"></a>CDynamicAccessor:: SetValue

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
de Un parámetro con plantilla que controla cualquier tipo de datos excepto los tipos de cadena (`CHAR*`, `WCHAR*`), que requieren un tratamiento especial. `GetValue` usa el tipo de datos adecuado en función de lo que especifique aquí.

*pColumnName*<br/>
de Puntero a una cadena de caracteres que contiene el nombre de columna.

*data*<br/>
de Puntero a la memoria que contiene los datos.

*nColumn*<br/>
de El número de columna. Los números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

### <a name="return-value"></a>Valor devuelto

Si desea establecer datos de cadena, use las versiones no plantilla de `GetValue`. Las versiones no plantilla de este método devuelven `void*`, que apunta a la parte del búfer que contiene los datos de columna especificados. Devuelve NULL si no se encuentra la columna.

Para el resto de tipos de datos, es más fácil usar las versiones con plantilla de `GetValue`. Las versiones con plantilla devuelven **true** si se ejecuta correctamente o **false** en caso de error.

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor (Clase)](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor (Clase)](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor (Clase)](../../data/oledb/cmanualaccessor-class.md)
