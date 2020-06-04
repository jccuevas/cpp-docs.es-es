---
title: Macros y funciones globales para las plantillas de consumidor OLE DB
ms.date: 02/11/2019
f1_keywords:
- ATL.AtlTraceErrorRecords
- ATL::AtlTraceErrorRecords
- AtlTraceErrorRecords
- BEGIN_ACCESSOR
- BEGIN_ACCESSOR_MAP
- END_ACCESSOR
- END_ACCESSOR_MAP
- BEGIN_COLUMN_MAP
- BLOB_ENTRY
- BLOB_ENTRY_LENGTH
- BLOB_ENTRY_LENGTH_STATUS
- BLOB_ENTRY_STATUS
- BLOB_NAME
- BLOB_NAME_LENGTH
- BLOB_NAME_LENGTH_STATUS
- BLOB_NAME_STATUS
- BOOKMARK_ENTRY
- COLUMN_ENTRY
- COLUMN_ENTRY_EX
- COLUMN_ENTRY_LENGTH
- COLUMN_ENTRY_LENGTH_STATUS
- COLUMN_ENTRY_PS
- COLUMN_ENTRY_PS_LENGTH
- COLUMN_ENTRY_PS_LENGTH_STATUS
- COLUMN_ENTRY_PS_STATUS
- COLUMN_ENTRY_STATUS
- COLUMN_ENTRY_TYPE
- COLUMN_ENTRY_TYPE_SIZE
- COLUMN_NAME
- COLUMN_NAME_EX
- COLUMN_NAME_LENGTH
- COLUMN_NAME_LENGTH_STATUS
- COLUMN_NAME_PS
- COLUMN_NAME_PS_LENGTH
- COLUMN_NAME_PS_LENGTH_STATUS
- COLUMN_NAME_PS_STATUS
- COLUMN_NAME_STATUS
- COLUMN_NAME_TYPE
- COLUMN_NAME_TYPE_PS
- COLUMN_NAME_TYPE_SIZE
- COLUMN_NAME_TYPE_STATUS
- END_COLUMN_MAP
- DEFINE_COMMAND
- DEFINE_COMMAND_EX
- BEGIN_PARAM_MAP
- END_PARAM_MAP
- SET_PARAM_TYPE
helpviewer_keywords:
- OLE DB consumer templates, macros
- macros, OLE DB consumer template
- AtlTraceErrorRecords function
- BEGIN_ACCESSOR macro, syntax
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR_MAP macro
- END_ACCESSOR macro
- END_ACCESSOR_MAP macro
- BEGIN_COLUMN_MAP macro
- BLOB_ENTRY macro
- BLOB_ENTRY_LENGTH macro
- BLOB_ENTRY_LENGTH_STATUS macro
- BLOB_ENTRY_STATUS macro
- BLOB_NAME macro
- BLOB_NAME_LENGTH macro
- BLOB_NAME_LENGTH_STATUS macro
- BLOB_NAME_STATUS macro
- BOOKMARK_ENTRY macro
- COLUMN_ENTRY macro
- COLUMN_ENTRY_EX macro
- COLUMN_ENTRY_LENGTH macro
- COLUMN_ENTRY_LENGTH_STATUS macro
- COLUMN_ENTRY_PS macro
- COLUMN_ENTRY_PS_LENGTH macro
- COLUMN_ENTRY_PS_LENGTH_STATUS macro
- COLUMN_ENTRY_PS_STATUS macro
- COLUMN_ENTRY_STATUS macro
- COLUMN_ENTRY_TYPE macro
- COLUMN_ENTRY_TYPE_SIZE macro
- COLUMN_NAME macro
- COLUMN_NAME_EX macro
- COLUMN_NAME_LENGTH macro
- COLUMN_NAME_LENGTH_STATUS macro
- COLUMN_NAME_PS macro
- COLUMN_NAME_PS_LENGTH macro
- COLUMN_NAME_PS_LENGTH_STATUS macro
- COLUMN_NAME_PS_STATUS macro
- COLUMN_NAME_STATUS macro
- COLUMN_NAME_TYPE macro
- COLUMN_NAME_TYPE_PS macro
- COLUMN_NAME_TYPE_SIZE macro
- COLUMN_NAME_TYPE_STATUS macro
- END_COLUMN_MAP macro
- DEFINE_COMMAND macro
- DEFINE_COMMAND_EX macro
- BEGIN_PARAM_MAP macro
- END_PARAM_MAP macro
- SET_PARAM_TYPE macro
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
ms.openlocfilehash: 8b898990672f590f6047eef6fdfd1ed7eecb3f92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369825"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>Macros y funciones globales para las plantillas de consumidor OLE DB

Las plantillas de consumidor OLE DB incluyen las siguientes macros y funciones globales:

## <a name="global-functions"></a>Funciones globales

|||
|-|-|
|[AtlTraceErrorRecords](#atltraceerrorrecords)|Vuelca la información del registro de errores OLE DB al dispositivo de volcado si se devuelve un error.|

## <a name="accessor-map-macros"></a>Macros de mapas de accesorios

|||
|-|-|
|[BEGIN_ACCESSOR](#begin_accessor)|Marca el comienzo de una entrada de descriptor de acceso.|
|[BEGIN_ACCESSOR_MAP](#begin_accessor_map)|Marca el principio de las entradas de asignación de descriptores de acceso.|
|[END_ACCESSOR](#end_accessor)|Marca el final de una entrada de descriptor de acceso.|
|[END_ACCESSOR_MAP](#end_accessor_map)|Marca el final de las entradas del mapa del descriptor de acceso.|

## <a name="column-map-macros"></a>Macros de mapa de columnas

|||
|-|-|
|[BEGIN_COLUMN_MAP](#begin_column_map)|Marca el principio de las entradas de mapa de columna en la clase de registro de usuario.|
|[BLOB_ENTRY](#blob_entry)|Se utiliza para enlazar un objeto binario grande (BLOB).|
|[BLOB_ENTRY_LENGTH](#blob_entry_length)|Notifica la longitud de la columna de datos BLOB.|
|[BLOB_ENTRY_LENGTH_STATUS](#blob_entry_length_status)|Notifica la longitud y el estado de la columna de datos BLOB.|
|[BLOB_ENTRY_STATUS](#blob_entry_status)|Notifica el estado de la columna de datos BLOB.|
|[BLOB_NAME](#blob_name)|Se utiliza para enlazar un objeto binario grande por nombre de columna.|
|[BLOB_NAME_LENGTH](#blob_name_length)|Notifica la longitud de la columna de datos BLOB.|
|[BLOB_NAME_LENGTH_STATUS](#blob_name_length_status)|Notifica la longitud y el estado de la columna de datos BLOB.|
|[BLOB_NAME_STATUS](#blob_name_status)|Notifica el estado de la columna de datos BLOB.|
|[BOOKMARK_ENTRY](#bookmark_entry)|Representa una entrada de marcador en el conjunto de filas. Una entrada de marcador es un tipo especial de entrada de columna.|
|[COLUMN_ENTRY](#column_entry)|Representa un enlace a una columna específica de la base de datos.|
|[COLUMN_ENTRY_EX](#column_entry_ex)|Representa un enlace a la columna específica de la base de datos. Admite parámetros *de tipo,* *longitud,* *precisión,* *escala*y *estado.*|
|[COLUMN_ENTRY_LENGTH](#column_entry_length)|Representa un enlace a la columna específica de la base de datos. Admite la variable *de longitud.*|
|[COLUMN_ENTRY_LENGTH_STATUS](#column_entry_length_status)|Representa un enlace a la columna específica de la base de datos. Admite parámetros *de estado* y *longitud.*|
|[COLUMN_ENTRY_PS](#column_entry_ps)|Representa un enlace a la columna específica de la base de datos. Admite parámetros de *precisión* y *escala.*|
|[COLUMN_ENTRY_PS_LENGTH](#column_entry_ps_length)|Representa un enlace a la columna específica de la base de datos. Admite los parámetros de *longitud* variable, *precisión* y *escala.*|
|[COLUMN_ENTRY_PS_LENGTH_STATUS](#column_entry_ps_length_status)|Representa un enlace a la columna específica de la base de datos. Admite variables de *estado* y *longitud,* *precisión* y parámetros de *escala.*|
|[COLUMN_ENTRY_PS_STATUS](#column_entry_ps_status)|Representa un enlace a la columna específica de la base de datos. Admite la variable de *estado,* la *precisión* y los parámetros de *escala.*|
|[COLUMN_ENTRY_STATUS](#column_entry_status)|Representa un enlace a la columna específica de la base de datos. Admite la variable *de estado.*|
|[COLUMN_ENTRY_TYPE](#column_entry_type)|Representa un enlace a una columna específica de la base de datos. Admite el parámetro *de tipo.*|
|[COLUMN_ENTRY_TYPE_SIZE](#column_entry_type_size)|Representa un enlace a la columna específica de la base de datos. Admite parámetros de *tipo* y *tamaño.*|
|[COLUMN_NAME](#column_name)|Representa un enlace a una columna específica de la base de datos por nombre.|
|[COLUMN_NAME_EX](#column_name_ex)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación del tipo de datos, el tamaño, la precisión, la escala, la longitud de la columna y el estado de la columna.|
|[COLUMN_NAME_LENGTH](#column_name_length)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación de la longitud de columna.|
|[COLUMN_NAME_LENGTH_STATUS](#column_name_length_status)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación de la longitud y el estado de la columna.|
|[COLUMN_NAME_PS](#column_name_ps)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación de precisión y escala.|
|[COLUMN_NAME_PS_LENGTH](#column_name_ps_length)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación de precisión, escala y longitud de columna.|
|[COLUMN_NAME_PS_LENGTH_STATUS](#column_name_ps_length_status)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación de precisión, escala, longitud de columna y estado de columna.|
|[COLUMN_NAME_PS_STATUS](#column_name_ps_status)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación de precisión, escala y estado de columna.|
|[COLUMN_NAME_STATUS](#column_name_status)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación del estado de la columna.|
|[COLUMN_NAME_TYPE](#column_name_type)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación del tipo de datos.|
|[COLUMN_NAME_TYPE_PS](#column_name_type_ps)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación del tipo de datos, la precisión y la escala.|
|[COLUMN_NAME_TYPE_SIZE](#column_name_type_size)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación del tipo y tamaño de los datos.|
|[COLUMN_NAME_TYPE_STATUS](#column_name_type_status)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación del tipo de datos y el estado de columna.|
|[END_COLUMN_MAP](#end_column_map)|Marca el final de las entradas del mapa de columnas.|

## <a name="command-macros"></a>Macros de comandos

|||
|-|-|
|[DEFINE_COMMAND](#define_command)|Especifica el comando que se usará para crear el conjunto de filas cuando se utiliza la [Clase CCommand.](../../data/oledb/ccommand-class.md) Solo acepta tipos de cadena que coincidan con el tipo de aplicación especificado (ANSI o Unicode). Se recomienda utilizar [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) en lugar de DEFINE_COMMAND.|
|[DEFINE_COMMAND_EX](#define_command_ex)|Especifica el comando que se usará para crear el conjunto de filas cuando se utiliza la [Clase CCommand.](../../data/oledb/ccommand-class.md) Soporta aplicaciones ANSI y Unicode.|

## <a name="parameter-map-macros"></a>Macros de mapa de parámetros

|||
|-|-|
|[BEGIN_PARAM_MAP](#begin_param_map)|Marca el principio de las entradas de mapa de parámetros en la clase de registro de usuario.|
|[END_PARAM_MAP](#end_param_map)|Marca el final de las entradas del mapa de parámetros.|
|[SET_PARAM_TYPE](#set_param_type)|Especifica COLUMN_ENTRY macros que siguen la macro de SET_PARAM_TYPE como entrada, salida o entrada/salida.|

### <a name="atltraceerrorrecords"></a><a name="atltraceerrorrecords"></a>AtlTraceErrorRecords

Vuelca la información del registro de errores OLE DB al dispositivo de volcado si se devuelve un error.

#### <a name="syntax"></a>Sintaxis

```cpp
inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);
```

#### <a name="parameters"></a>Parámetros

*Herr*<br/>
[en] Un HRESULT devuelto por una función miembro de plantilla de consumidor OLE DB.

#### <a name="remarks"></a>Observaciones

Si *hErr* no `AtlTraceErrorRecords` está S_OK, vuelca la información del registro de errores OLE DB en el dispositivo de volcado (la pestaña **Depurar** de la ventana Salida o un archivo). La información de registro de errores, que se obtiene del proveedor, incluye el número de fila, el origen, la descripción, el archivo de ayuda, el contexto y el GUID para cada entrada de registro de error. `AtlTraceErrorRecords`vuelca esta información solo en compilaciones de depuración. En las compilaciones de versión, es un código auxiliar vacío que se optimiza. Para obtener más información, vea [CDBErrorInfo (Clase)](../../data/oledb/cdberrorinfo-class.md).

### <a name="begin_accessor"></a><a name="begin_accessor"></a>BEGIN_ACCESSOR

Marca el comienzo de una entrada de descriptor de acceso.

#### <a name="syntax"></a>Sintaxis

```cpp
BEGIN_ACCESSOR(num, bAuto)
```

#### <a name="parameters"></a>Parámetros

*num*<br/>
[en] El número de desplazamiento cero para el descriptor de acceso en este mapa de descriptores de acceso.

*bAuto*<br/>
[en] Especifica si este descriptor de acceso es un descriptor de acceso automático o un descriptor de acceso manual. Si **es true**, el descriptor de acceso es auto; si **es false**, el descriptor de acceso es manual. Un descriptor de acceso automático significa que los datos se recuperan automáticamente en las operaciones de movimiento.

#### <a name="remarks"></a>Observaciones

En el caso de varios descriptores de acceso en un conjunto de filas, debe especificar BEGIN_ACCESSOR_MAP y usar la macro BEGIN_ACCESSOR para cada descriptor de acceso individual. La macro BEGIN_ACCESSOR se completa con la macro END_ACCESSOR. La macro BEGIN_ACCESSOR_MAP se completa con la macro END_ACCESSOR_MAP.

#### <a name="example"></a>Ejemplo

Consulte [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_accessor_map"></a><a name="begin_accessor_map"></a>BEGIN_ACCESSOR_MAP

Marca el principio de las entradas de asignación de descriptores de acceso.

#### <a name="syntax"></a>Sintaxis

```cpp
BEGIN_ACCESSOR_MAP(x, num)
```

#### <a name="parameters"></a>Parámetros

*X*<br/>
[in] Nombre de la clase de registro de usuario.

*num*<br/>
[in] Número de descriptores de acceso de esta asignación de descriptores de acceso.

#### <a name="remarks"></a>Observaciones

En el caso de varios descriptores de acceso en un conjunto de filas, debe especificar BEGIN_ACCESSOR_MAP al principio y usar la macro BEGIN_ACCESSOR para cada descriptor de acceso individual. La macro BEGIN_ACCESSOR se completa con la macro END_ACCESSOR. El mapa de descriptores de acceso se completa con la macro END_ACCESSOR_MAP.

Si solo tiene un descriptor de acceso en el registro de usuario, use la macro [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).

#### <a name="example"></a>Ejemplo

```cpp
class CArtistsAccessor
{
public:
// Data Elements
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];
   short m_nAge;

// Output binding map
BEGIN_ACCESSOR_MAP(CArtistsAccessor, 2)
   BEGIN_ACCESSOR(0, true)
      COLUMN_ENTRY(1, m_szFirstName)
      COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false) // Not an auto accessor
      COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsAccessor, L" \
   SELECT \
      FirstName, \
      LastName, \
      Age \
      FROM Artists")
};
```

### <a name="end_accessor"></a><a name="end_accessor"></a>END_ACCESSOR

Marca el final de una entrada de descriptor de acceso.

#### <a name="syntax"></a>Sintaxis

```cpp
END_ACCESSOR()
```

#### <a name="remarks"></a>Observaciones

Para varios descriptores de acceso en un conjunto de filas, debe especificar BEGIN_ACCESSOR_MAP y usar la macro BEGIN_ACCESSOR para cada descriptor de acceso individual. La macro BEGIN_ACCESSOR se completa con la macro END_ACCESSOR. La macro BEGIN_ACCESSOR_MAP se completa con la macro END_ACCESSOR_MAP.

#### <a name="example"></a>Ejemplo

Consulte [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="end_accessor_map"></a><a name="end_accessor_map"></a>END_ACCESSOR_MAP

Marca el final de las entradas del mapa del descriptor de acceso.

#### <a name="syntax"></a>Sintaxis

```cpp
END_ACCESSOR_MAP()
```

#### <a name="remarks"></a>Observaciones

Para varios descriptores de acceso en un conjunto de filas, debe especificar BEGIN_ACCESSOR_MAP y usar la macro BEGIN_ACCESSOR para cada descriptor de acceso individual. La macro BEGIN_ACCESSOR se completa con la macro END_ACCESSOR. La macro BEGIN_ACCESSOR_MAP se completa con la macro END_ACCESSOR_MAP.

#### <a name="example"></a>Ejemplo

Consulte [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_column_map"></a><a name="begin_column_map"></a>BEGIN_COLUMN_MAP

Marca el inicio de una entrada de mapa de columnas.

#### <a name="syntax"></a>Sintaxis

```cpp
BEGIN_COLUMN_MAP(x)
```

#### <a name="parameters"></a>Parámetros

*X*<br/>
[in] Nombre de la clase de registro de usuario derivada de `CAccessor`.

#### <a name="remarks"></a>Observaciones

Esta macro se usa en el caso de un único descriptor de acceso en un conjunto de filas. Si tiene varios descriptores de acceso en un conjunto de filas, use [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

La macro BEGIN_COLUMN_MAP se completa con la macro END_COLUMN_MAP. Esta macro se usa cuando solamente hay un descriptor de acceso necesario en el registro de usuario.

Las columnas corresponden a los campos del conjunto de filas que quiere enlazar.

#### <a name="example"></a>Ejemplo

Este es un mapa de columnas y parámetros de ejemplo:

<!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->

### <a name="blob_entry"></a><a name="blob_entry"></a>BLOB_ENTRY

Se utiliza con BEGIN_COLUMN_MAP y END_COLUMN_MAP para enlazar un objeto binario grande ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))).

#### <a name="syntax"></a>Sintaxis

```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)
```

#### <a name="parameters"></a>Parámetros

*nOrdinal*<br/>
[en] El número de columna.

*IID*<br/>
[en] GUID de interfaz, como `IDD_ISequentialStream`, utilizado para recuperar el BLOB.

*Banderas*<br/>
[en] Marcas de modo de almacenamiento según lo definido `STGM_READ`por el modelo de almacenamiento estructurado OLE (por ejemplo, ).

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

#### <a name="example"></a>Ejemplo

Consulte [¿Cómo puedo recuperar un BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length"></a><a name="blob_entry_length"></a>BLOB_ENTRY_LENGTH

Se utiliza con BEGIN_COLUMN_MAP y END_COLUMN_MAP para enlazar un objeto binario grande ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Similar a [BLOB_ENTRY](../../data/oledb/blob-entry.md), excepto que esta macro también obtiene la longitud en bytes de la columna BLOB.

#### <a name="syntax"></a>Sintaxis

```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)
```

#### <a name="parameters"></a>Parámetros

*nOrdinal*<br/>
[en] El número de columna.

*IID*<br/>
[en] GUID de interfaz, como `IDD_ISequentialStream`, utilizado para recuperar el BLOB.

*Banderas*<br/>
[en] Marcas de modo de almacenamiento según lo definido `STGM_READ`por el modelo de almacenamiento estructurado OLE (por ejemplo, ).

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[fuera] La longitud (real) en bytes de la columna BLOB.

#### <a name="example"></a>Ejemplo

Consulte [¿Cómo puedo recuperar un BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length_status"></a><a name="blob_entry_length_status"></a>BLOB_ENTRY_LENGTH_STATUS

Se utiliza con BEGIN_COLUMN_MAP y END_COLUMN_MAP para enlazar un objeto binario grande ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). De forma similar a [BLOB_ENTRY](../../data/oledb/blob-entry.md), excepto que esta macro también obtiene la longitud y el estado de la columna BLOB.

#### <a name="syntax"></a>Sintaxis

```cpp
BLOB_ENTRY_LENGTH_STATUS(
    nOrdinal,
    IID,
    flags,
    data,
    length,
    status )
```

#### <a name="parameters"></a>Parámetros

*nOrdinal*<br/>
[en] El número de columna.

*IID*<br/>
[en] GUID de interfaz, como `IDD_ISequentialStream`, utilizado para recuperar el BLOB.

*Banderas*<br/>
[en] Marcas de modo de almacenamiento según lo definido `STGM_READ`por el modelo de almacenamiento estructurado OLE (por ejemplo, ).

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[fuera] La longitud (real) en bytes de la columna BLOB.

*status*<br/>
[fuera] El estado de la columna de datos BLOB.

#### <a name="example"></a>Ejemplo

Consulte [¿Cómo puedo recuperar un BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_status"></a><a name="blob_entry_status"></a>BLOB_ENTRY_STATUS

Se utiliza con BEGIN_COLUMN_MAP o BEGIN_ACCESSOR_MAP para enlazar un objeto binario grande ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Similar a [BLOB_ENTRY](../../data/oledb/blob-entry.md), excepto que esta macro también obtiene el estado de la columna BLOB.

#### <a name="syntax"></a>Sintaxis

```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)
```

#### <a name="parameters"></a>Parámetros

*nOrdinal*<br/>
[en] El número de columna.

*IID*<br/>
[en] GUID de interfaz, como `IDD_ISequentialStream`, utilizado para recuperar el BLOB.

*Banderas*<br/>
[en] Marcas de modo de almacenamiento según lo definido `STGM_READ`por el modelo de almacenamiento estructurado OLE (por ejemplo, ).

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*status*<br/>
[fuera] El estado del campo BLOB.

#### <a name="example"></a>Ejemplo

Consulte [¿Cómo puedo recuperar un BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name"></a><a name="blob_name"></a>BLOB_NAME

Se utiliza con BEGIN_COLUMN_MAP y END_COLUMN_MAP para enlazar un objeto binario grande ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Similar a [BLOB_ENTRY](../../data/oledb/blob-entry.md), excepto que esta macro toma un nombre de columna en lugar de un número de columna.

#### <a name="syntax"></a>Sintaxis

```cpp
BLOB_NAME(pszName, IID, flags, data )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[en] Un puntero al nombre de la columna. El nombre debe ser una cadena Unicode. Puede lograr esto poniendo una 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*IID*<br/>
[en] GUID de interfaz, como `IDD_ISequentialStream`, utilizado para recuperar el BLOB.

*Banderas*<br/>
[en] Marcas de modo de almacenamiento según lo definido `STGM_READ`por el modelo de almacenamiento estructurado OLE (por ejemplo, ).

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

#### <a name="example"></a>Ejemplo

Consulte [¿Cómo puedo recuperar un BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name_length"></a><a name="blob_name_length"></a>BLOB_NAME_LENGTH

Se utiliza con BEGIN_COLUMN_MAP y END_COLUMN_MAP para enlazar un objeto binario grande ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Similar a [BLOB_NAME](../../data/oledb/blob-name.md), excepto que esta macro también obtiene la longitud en bytes de la columna de datos BLOB.

#### <a name="syntax"></a>Sintaxis

```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[en] Un puntero al nombre de la columna. El nombre debe ser una cadena Unicode. Puede lograr esto poniendo una 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*IID*<br/>
[en] GUID de interfaz, como `IDD_ISequentialStream`, utilizado para recuperar el BLOB.

*Banderas*<br/>
[en] Marcas de modo de almacenamiento según lo definido `STGM_READ`por el modelo de almacenamiento estructurado OLE (por ejemplo, ).

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[fuera] La longitud (real) en bytes de la columna BLOB.

### <a name="blob_name_length_status"></a><a name="blob_name_length_status"></a>BLOB_NAME_LENGTH_STATUS

Se utiliza con BEGIN_COLUMN_MAP y END_COLUMN_MAP para enlazar un objeto binario grande ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Similar a [BLOB_NAME](../../data/oledb/blob-name.md), excepto que esta macro también obtiene la longitud y el estado de la columna de datos BLOB.

#### <a name="syntax"></a>Sintaxis

```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length, status )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[en] Un puntero al nombre de la columna. El nombre debe ser una cadena Unicode. Puede lograr esto poniendo una 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*IID*<br/>
[en] GUID de interfaz, como `IDD_ISequentialStream`, utilizado para recuperar el BLOB.

*Banderas*<br/>
[en] Marcas de modo de almacenamiento según lo definido `STGM_READ`por el modelo de almacenamiento estructurado OLE (por ejemplo, ).

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[fuera] La longitud (real) en bytes de la columna BLOB.

*status*<br/>
[fuera] El estado del campo BLOB.

### <a name="blob_name_status"></a><a name="blob_name_status"></a>BLOB_NAME_STATUS

Se utiliza con BEGIN_COLUMN_MAP y END_COLUMN_MAP para enlazar un objeto binario grande ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Similar a [BLOB_NAME](../../data/oledb/blob-name.md), excepto que esta macro también obtiene el estado de la columna de datos BLOB.

#### <a name="syntax"></a>Sintaxis

```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data, status )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[en] Un puntero al nombre de la columna. El nombre debe ser una cadena Unicode. Puede lograr esto poniendo una 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*IID*<br/>
[en] GUID de interfaz, como `IDD_ISequentialStream`, utilizado para recuperar el BLOB.

*Banderas*<br/>
[en] Marcas de modo de almacenamiento según lo definido `STGM_READ`por el modelo de almacenamiento estructurado OLE (por ejemplo, ).

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*status*<br/>
[fuera] El estado del campo BLOB.

### <a name="bookmark_entry"></a><a name="bookmark_entry"></a>BOOKMARK_ENTRY

Enlaza la columna de marcador.

#### <a name="syntax"></a>Sintaxis

```cpp
BOOKMARK_ENTRY(variable)
```

#### <a name="parameters"></a>Parámetros

*Variable*<br/>
[en] La variable que se va a enlazar a la columna de marcador.

#### <a name="example"></a>Ejemplo

```cpp
class CArtistsBookmark
{
public:
// Data Elements
   CBookmark<4> m_bookmark;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

// Output binding map
BEGIN_COLUMN_MAP(CArtistsBookmark)
   BOOKMARK_ENTRY(m_bookmark)
   COLUMN_ENTRY(1, m_nAge)
   COLUMN_ENTRY(2, m_szFirstName)
   COLUMN_ENTRY(3, m_szLastName)
END_COLUMN_MAP()

   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_BOOKMARKS, true);
   }

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsBookmark, L" \
   SELECT \
      Age, \
      FirstName, \
      LastName \
      FROM Artists")
};
```

Para obtener más información, consulte Uso de [marcadores](using-bookmarks.md) y [clase CBookmark](../../data/oledb/cbookmark-class.md).

### <a name="column_entry"></a><a name="column_entry"></a>COLUMN_ENTRY

Representa un enlace del conjunto de filas a la columna específica del conjunto de filas.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY(nOrdinal, data)
```

#### <a name="parameters"></a>Parámetros

Consulte [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) en la *referencia del programador OLE DB*.

*nOrdinal*<br/>
[en] El número de columna.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Observaciones

La macro COLUMN_ENTRY se utiliza en los siguientes lugares:

- Entre las macros [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre las macros [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre las macros [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

#### <a name="example"></a>Ejemplo

Consulte los ejemplos de los temas de macro, [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="column_entry_ex"></a><a name="column_entry_ex"></a>COLUMN_ENTRY_EX

Representa un enlace en el conjunto de filas a la columna específica de la base de datos.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_EX(nOrdinal, wType, nLength, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parámetros

Consulte [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) en la *referencia del programador OLE DB*.

*nOrdinal*<br/>
[en] El número de columna.

*wType*<br/>
[en] El tipo de datos.

*nLongitud*<br/>
[en] El tamaño de los datos en bytes.

*nPrecisión*<br/>
[en] La precisión máxima que se debe `DBTYPE_NUMERIC`utilizar al obtener datos y *wType* es . De lo contrario, este parámetro se omite.

*nScale*<br/>
[en] La escala que se usará al `DBTYPE_NUMERIC` `DBTYPE_DECIMAL`obtener datos y *wType* es o .

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[en] La variable que se va a enlazar a la longitud de la columna.

*status*<br/>
[en] La variable que se va a enlazar al estado de columna.

#### <a name="remarks"></a>Observaciones

La macro COLUMN_ENTRY_EX se utiliza en los siguientes lugares:

- Entre las macros [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre las macros [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre las macros [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

#### <a name="example"></a>Ejemplo

Consulte [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="column_entry_length"></a><a name="column_entry_length"></a>COLUMN_ENTRY_LENGTH

Representa un enlace en el conjunto de filas a la columna específica de la base de datos.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)
```

#### <a name="parameters"></a>Parámetros

Consulte [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) en la *referencia del programador OLE DB*.

*nOrdinal*<br/>
[en] El número de columna, empezando por uno. El marcador corresponde a la columna cero.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[en] La variable que se va a enlazar a la longitud de la columna.

#### <a name="remarks"></a>Observaciones

Esta macro admite la variable *length.* Se utiliza en los siguientes lugares:

- Entre las macros [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre las macros [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre las macros [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

### <a name="column_entry_length_status"></a><a name="column_entry_length_status"></a>COLUMN_ENTRY_LENGTH_STATUS

Representa un enlace en el conjunto de filas a la columna específica de la base de datos.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)
```

#### <a name="parameters"></a>Parámetros

Consulte [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) en la *referencia del programador OLE DB*.

*nOrdinal*<br/>
[en] El número de columna.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[en] La variable que se va a enlazar a la longitud de la columna.

*status*<br/>
[en] La variable que se va a enlazar al estado de columna.

#### <a name="remarks"></a>Observaciones

Utilice esta macro cuando desee admitir variables de longitud y estado. Se utiliza en los siguientes lugares:

- Entre las macros [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre las macros [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre las macros [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

### <a name="column_entry_ps"></a><a name="column_entry_ps"></a>COLUMN_ENTRY_PS

Representa un enlace del conjunto de filas a la columna específica del conjunto de filas.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parámetros

Consulte [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) en la *referencia del programador OLE DB*.

*nOrdinal*<br/>
[en] El número de columna.

*nPrecisión*<br/>
[en] La precisión máxima de la columna que desea enlazar.

*nScale*<br/>
[en] La escala de la columna que desea enlazar.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Observaciones

Le permite especificar la precisión y la escala de la columna que desea enlazar. Se utiliza en los siguientes lugares:

- Entre las macros [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre las macros [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre las macros [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

### <a name="column_entry_ps_length"></a><a name="column_entry_ps_length"></a>COLUMN_ENTRY_PS_LENGTH

Representa un enlace en el conjunto de filas a la columna específica de la base de datos.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_PS_LENGTH(nOrdinal, nPrecision, nScale, data, length)
```

#### <a name="parameters"></a>Parámetros

Consulte [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) en la *referencia del programador OLE DB*.

*nOrdinal*<br/>
[en] El número de columna, empezando por uno. El marcador corresponde a la columna cero.

*nPrecisión*<br/>
[en] La precisión máxima de la columna que desea enlazar.

*nScale*<br/>
[en] La escala de la columna que desea enlazar.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[en] La variable que se va a enlazar a la longitud de la columna.

#### <a name="remarks"></a>Observaciones

Le permite especificar la precisión y la escala de la columna que desea enlazar. Esta macro admite la variable *length.* Se utiliza en los siguientes lugares:

- Entre las macros [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre las macros [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre las macros [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

### <a name="column_entry_ps_length_status"></a><a name="column_entry_ps_length_status"></a>COLUMN_ENTRY_PS_LENGTH_STATUS

Representa un enlace en el conjunto de filas a la columna específica de la base de datos.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_PS_LENGTH_STATUS(nOrdinal, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parámetros

Consulte [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) en la *referencia del programador OLE DB*.

*nOrdinal*<br/>
[en] El número de columna.

*nPrecisión*<br/>
[en] La precisión máxima de la columna que desea enlazar.

*nScale*<br/>
[en] La escala de la columna que desea enlazar.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[en] La variable que se va a enlazar a la longitud de la columna.

*status*<br/>
[en] La variable que se va a enlazar al estado de columna.

#### <a name="remarks"></a>Observaciones

Le permite especificar la precisión y la escala de la columna que desea enlazar. Utilice esta macro cuando desee admitir variables de longitud y estado. Se utiliza en los siguientes lugares:

- Entre las macros [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre las macros [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre las macros [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

### <a name="column_entry_ps_status"></a><a name="column_entry_ps_status"></a>COLUMN_ENTRY_PS_STATUS

Representa un enlace en el conjunto de filas a la columna específica de la base de datos.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_PS_STATUS(nOrdinal, nPrecision, nScale, data, status)
```

#### <a name="parameters"></a>Parámetros

Consulte [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) en la *referencia del programador OLE DB*.

*nOrdinal*<br/>
[en] El número de columna.

*nPrecisión*<br/>
[en] La precisión máxima de la columna que desea enlazar.

*nScale*<br/>
[en] La escala de la columna que desea enlazar.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*status*<br/>
[en] La variable que se va a enlazar al estado de columna.

#### <a name="remarks"></a>Observaciones

Le permite especificar la precisión y la escala de la columna que desea enlazar. Esta macro admite la variable *de estado.* Se utiliza en los siguientes lugares:

- Entre las macros [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre las macros [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre las macros [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

### <a name="column_entry_status"></a><a name="column_entry_status"></a>COLUMN_ENTRY_STATUS

Representa un enlace en el conjunto de filas a la columna específica de la base de datos.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)
```

#### <a name="parameters"></a>Parámetros

Consulte [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) en la *referencia del programador OLE DB*.

*nOrdinal*<br/>
[en] El número de columna.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*status*<br/>
[en] La variable que se va a enlazar al estado de columna.

#### <a name="remarks"></a>Observaciones

Esta macro admite la variable *de estado.* Se utiliza en los siguientes lugares:

- Entre las macros [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre las macros [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre las macros [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

### <a name="column_entry_type"></a><a name="column_entry_type"></a>COLUMN_ENTRY_TYPE

Representa un enlace a la columna específica de la base de datos. Admite el parámetro *de tipo.*

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)
```

#### <a name="parameters"></a>Parámetros

*nOrdinal*<br/>
[en] El número de columna.

*wType*<br/>
[en] Tipo de datos de entrada de columna.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Observaciones

Esta macro es una variante especializada de la [macro COLUMN_ENTRY](../../data/oledb/column-entry.md) que proporciona un medio para especificar el tipo de datos.

### <a name="column_entry_type_size"></a><a name="column_entry_type_size"></a>COLUMN_ENTRY_TYPE_SIZE

Representa un enlace a la columna específica de la base de datos. Admite parámetros de *tipo* y *tamaño.*

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)
```

#### <a name="parameters"></a>Parámetros

*nOrdinal*<br/>
[en] El número de columna.

*wType*<br/>
[en] Tipo de datos de entrada de columna.

*nLongitud*<br/>
[en] Tamaño de la entrada de columna en bytes.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Observaciones

Esta macro es una variante especializada de la macro [COLUMN_ENTRY](../../data/oledb/column-entry.md) que proporciona un medio para especificar el tamaño y el tipo de datos.

### <a name="column_name"></a><a name="column_name"></a>COLUMN_NAME

Representa un enlace del conjunto de filas a la columna específica del conjunto de filas. Similar a [COLUMN_ENTRY](../../data/oledb/column-entry.md), excepto que esta macro toma el nombre de columna en lugar del número de columna.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME(pszName, data)
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[en] Un puntero al nombre de la columna. El nombre debe ser una cadena Unicode. Puede lograr esto poniendo una 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Observaciones

Las macros COLUMN_NAME_* se utilizan en los mismos lugares que [COLUMN_ENTRY:](../../data/oledb/column-entry.md)

- Entre las macros [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Entre las macros [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Entre las macros [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

### <a name="column_name_ex"></a><a name="column_name_ex"></a>COLUMN_NAME_EX

Representa un enlace del conjunto de filas a la columna específica del conjunto de filas. De forma similar a [COLUMN_NAME](../../data/oledb/column-name.md), excepto que esta macro también toma el tipo de datos, el tamaño, la precisión, la escala, la longitud de columna y el estado de columna.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[en] Un puntero al nombre de la columna. El nombre debe ser una cadena Unicode. Puede lograr esto poniendo una 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*wType*<br/>
[en] El tipo de datos.

*nLongitud*<br/>
[en] El tamaño de los datos en bytes.

*nPrecisión*<br/>
[en] La precisión máxima que se debe `DBTYPE_NUMERIC`utilizar al obtener datos y *wType* es . De lo contrario, este parámetro se omite.

*nScale*<br/>
[en] La escala que se usará al `DBTYPE_NUMERIC` `DBTYPE_DECIMAL`obtener datos y *wType* es o .

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[en] La variable que se va a enlazar a la longitud de la columna.

*status*<br/>
[en] La variable que se va a enlazar al estado de columna.

#### <a name="remarks"></a>Observaciones

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_*.

### <a name="column_name_length"></a><a name="column_name_length"></a>COLUMN_NAME_LENGTH

Representa un enlace del conjunto de filas a la columna específica del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), excepto que esta macro también toma longitud de columna.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_LENGTH(pszName, data, length)
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[en] Un puntero al nombre de la columna. El nombre debe ser una cadena Unicode. Puede lograr esto poniendo una 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[en] La variable que se va a enlazar a la longitud de la columna.

#### <a name="remarks"></a>Observaciones

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_*.

### <a name="column_name_length_status"></a><a name="column_name_length_status"></a>COLUMN_NAME_LENGTH_STATUS

Representa un enlace del conjunto de filas a la columna específica del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), excepto que esta macro también toma la longitud de columna y el estado de columna.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_LENGTH_STATUS(pszName, data, length, status )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[en] Un puntero al nombre de la columna. El nombre debe ser una cadena Unicode. Puede lograr esto poniendo una 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[en] La variable que se va a enlazar a la longitud de la columna.

*status*<br/>
[en] La variable que se va a enlazar al estado de columna.

#### <a name="remarks"></a>Observaciones

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_*.

### <a name="column_name_ps"></a><a name="column_name_ps"></a>COLUMN_NAME_PS

Representa un enlace del conjunto de filas a la columna específica del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), excepto que esta macro también toma precisión y escala.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_PS(pszName, nPrecision, nScale, data )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[en] Un puntero al nombre de la columna. El nombre debe ser una cadena Unicode. Puede lograr esto poniendo una 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*nPrecisión*<br/>
[en] La precisión máxima de la columna que desea enlazar.

*nScale*<br/>
[en] La escala de la columna que desea enlazar.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Observaciones

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_*.

### <a name="column_name_ps_length"></a><a name="column_name_ps_length"></a>COLUMN_NAME_PS_LENGTH

Representa un enlace del conjunto de filas a la columna específica del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), excepto que esta macro también toma precisión, escala y longitud de columna.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_PS_LENGTH(pszName, nPrecision, nScale, data, length )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[en] Un puntero al nombre de la columna. El nombre debe ser una cadena Unicode. Puede lograr esto poniendo una 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*nPrecisión*<br/>
[en] La precisión máxima de la columna que desea enlazar.

*nScale*<br/>
[en] La escala de la columna que desea enlazar.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[en] La variable que se va a enlazar a la longitud de la columna.

#### <a name="remarks"></a>Observaciones

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_*.

### <a name="column_name_ps_length_status"></a><a name="column_name_ps_length_status"></a>COLUMN_NAME_PS_LENGTH_STATUS

Representa un enlace del conjunto de filas a la columna específica del conjunto de filas. De forma similar a [COLUMN_NAME](../../data/oledb/column-name.md), excepto que esta macro también toma precisión, escala, longitud de columna y estado de columna.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[en] Un puntero al nombre de la columna. El nombre debe ser una cadena Unicode. Puede lograr esto poniendo una 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*nPrecisión*<br/>
[en] La precisión máxima de la columna que desea enlazar.

*nScale*<br/>
[en] La escala de la columna que desea enlazar.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[en] La variable que se va a enlazar a la longitud de la columna.

*status*<br/>
[en] La variable que se va a enlazar al estado de columna.

#### <a name="remarks"></a>Observaciones

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_*.

### <a name="column_name_ps_status"></a><a name="column_name_ps_status"></a>COLUMN_NAME_PS_STATUS

Representa un enlace del conjunto de filas a la columna específica del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), excepto que esta macro también toma precisión, escala y estado de columna.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_PS_STATUS(pszName, nPrecision, nScale, data, status )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[en] Un puntero al nombre de la columna. El nombre debe ser una cadena Unicode. Puede lograr esto poniendo una 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*nPrecisión*<br/>
[en] La precisión máxima de la columna que desea enlazar.

*nScale*<br/>
[en] La escala de la columna que desea enlazar.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*status*<br/>
[en] La variable que se va a enlazar al estado de columna.

#### <a name="remarks"></a>Observaciones

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_*.

### <a name="column_name_status"></a><a name="column_name_status"></a>COLUMN_NAME_STATUS

Representa un enlace del conjunto de filas a la columna específica del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), excepto que esta macro también toma el estado de columna.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_STATUS(pszName, data, status )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[en] Un puntero al nombre de la columna. El nombre debe ser una cadena Unicode. Puede lograr esto poniendo una 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

*status*<br/>
[en] La variable que se va a enlazar al estado de columna.

#### <a name="remarks"></a>Observaciones

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_*.

### <a name="column_name_type"></a><a name="column_name_type"></a>COLUMN_NAME_TYPE

Representa un enlace del conjunto de filas a la columna específica del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), excepto que esta macro también toma el tipo de datos.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_TYPE(pszName, wType, data)
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[en] Un puntero al nombre de la columna. El nombre debe ser una cadena Unicode. Puede lograr esto poniendo una 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*wType*<br/>
[en] El tipo de datos.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Observaciones

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_*.

### <a name="column_name_type_ps"></a><a name="column_name_type_ps"></a>COLUMN_NAME_TYPE_PS

Representa un enlace del conjunto de filas a la columna específica del conjunto de filas. De forma similar a [COLUMN_NAME](../../data/oledb/column-name.md), excepto que esta macro también toma el tipo de datos, la precisión y la escala.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[en] Un puntero al nombre de la columna. El nombre debe ser una cadena Unicode. Puede lograr esto poniendo una 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*wType*<br/>
[en] El tipo de datos.

*nPrecisión*<br/>
[en] La precisión máxima que se debe `DBTYPE_NUMERIC`utilizar al obtener datos y *wType* es . De lo contrario, este parámetro se omite.

*nScale*<br/>
[en] La escala que se usará al `DBTYPE_NUMERIC` `DBTYPE_DECIMAL`obtener datos y *wType* es o .

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Observaciones

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_*.

### <a name="column_name_type_size"></a><a name="column_name_type_size"></a>COLUMN_NAME_TYPE_SIZE

Representa un enlace del conjunto de filas a la columna específica del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), excepto que esta macro también toma el tipo de datos y el tamaño.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[en] Un puntero al nombre de la columna. El nombre debe ser una cadena Unicode. Puede lograr esto poniendo una 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*wType*<br/>
[en] El tipo de datos.

*nLongitud*<br/>
[en] El tamaño de los datos en bytes.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Observaciones

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_*.

### <a name="column_name_type_status"></a><a name="column_name_type_status"></a>COLUMN_NAME_TYPE_STATUS

Representa un enlace del conjunto de filas a la columna específica del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), excepto que esta macro también toma el tipo de datos y el estado de columna.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_TYPE_STATUS(pszName, wType, status, data)
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[en] Un puntero al nombre de la columna. El nombre debe ser una cadena Unicode. Puede lograr esto poniendo una 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*wType*<br/>
[en] El tipo de datos.

*status*<br/>
[en] La variable que se va a enlazar al estado de columna.

*datos*<br/>
[en] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Observaciones

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_*.

### <a name="end_column_map"></a><a name="end_column_map"></a>END_COLUMN_MAP

Marca el final de las entradas del mapa de columnas.

#### <a name="syntax"></a>Sintaxis

```cpp
END_COLUMN_MAP()
```

#### <a name="remarks"></a>Observaciones

Se utiliza con un único descriptor de acceso en un conjunto de filas. La macro BEGIN_COLUMN_MAP se completa con la macro END_COLUMN_MAP.

#### <a name="example"></a>Ejemplo

Consulte [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).

### <a name="define_command"></a><a name="define_command"></a>DEFINE_COMMAND

Especifica el comando que se usará para crear el conjunto de filas cuando se utiliza la [Clase CCommand.](../../data/oledb/ccommand-class.md) Solo acepta tipos de cadena que coincidan con el tipo de aplicación especificado (ANSI o Unicode).

> [!NOTE]
> Se recomienda utilizar [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) en lugar de DEFINE_COMMAND.

#### <a name="syntax"></a>Sintaxis

```cpp
DEFINE_COMMAND(x, szCommand)
```

#### <a name="parameters"></a>Parámetros

*X*<br/>
[en] El nombre de la clase de registro de usuario (comando).

*szCommand*<br/>
[en] Cadena de comandos que se usará para crear el conjunto de filas al usar [CCommand](../../data/oledb/ccommand-class.md).

#### <a name="remarks"></a>Observaciones

La cadena de comandos que especifique se utilizará como valor predeterminado si no especifica el texto del comando en el método [CCommand::Open.](../../data/oledb/ccommand-open.md)

Esta macro acepta cadenas ANSI si compila la aplicación como cadenas ANSI o Unicode si compila la aplicación como Unicode. Se recomienda utilizar [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) en lugar de DEFINE_COMMAND, porque la primera acepta cadenas Unicode, independientemente del tipo de aplicación ANSI o Unicode.

#### <a name="example"></a>Ejemplo

Consulte [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="define_command_ex"></a><a name="define_command_ex"></a>DEFINE_COMMAND_EX

Especifica el comando que se usará para crear el conjunto de filas cuando se utiliza la [Clase CCommand.](../../data/oledb/ccommand-class.md) Admite aplicaciones Unicode y ANSI.

#### <a name="syntax"></a>Sintaxis

```cpp
DEFINE_COMMAND_EX(x, wszCommand)
```

#### <a name="parameters"></a>Parámetros

*X*<br/>
[en] El nombre de la clase de registro de usuario (comando).

*wszCommand*<br/>
[en] Cadena de comandos que se usará para crear el conjunto de filas al usar [CCommand](../../data/oledb/ccommand-class.md).

#### <a name="remarks"></a>Observaciones

La cadena de comandos que especifique se utilizará como valor predeterminado si no especifica el texto del comando en el método [CCommand::Open.](../../data/oledb/ccommand-open.md)

Esta macro acepta cadenas Unicode, independientemente del tipo de aplicación. Esta macro es preferible a [DEFINE_COMMAND](../../data/oledb/define-command.md) porque admite aplicaciones Unicode y ANSI.

#### <a name="example"></a>Ejemplo

Consulte [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="begin_param_map"></a><a name="begin_param_map"></a>BEGIN_PARAM_MAP

Marca el principio de las entradas del mapa de parámetros.

#### <a name="syntax"></a>Sintaxis

```cpp
BEGIN_PARAM_MAP(x)
```

#### <a name="parameters"></a>Parámetros

*X*<br/>
[in] Nombre de la clase de registro de usuario.

#### <a name="remarks"></a>Observaciones

Los parámetros son utilizados por los [comandos](/previous-versions/windows/desktop/ms724608(v=vs.85)).

#### <a name="example"></a>Ejemplo

Consulte el ejemplo de la macro [BEGIN_COLUMN_MAP.](../../data/oledb/begin-column-map.md)

### <a name="end_param_map"></a><a name="end_param_map"></a>END_PARAM_MAP

Marca el final de las entradas del mapa de parámetros.

#### <a name="syntax"></a>Sintaxis

```cpp
END_PARAM_MAP()
```

#### <a name="example"></a>Ejemplo

Consulte el ejemplo de la [macro BEGIN_PARAM_MAP.](../../data/oledb/begin-param-map.md)

### <a name="set_param_type"></a><a name="set_param_type"></a>SET_PARAM_TYPE

Especifica COLUMN_ENTRY macros que siguen a la entrada, salida o entrada/salida de macros de SET_PARAM_TYPE.

#### <a name="syntax"></a>Sintaxis

```cpp
SET_PARAM_TYPE(type)
```

#### <a name="parameters"></a>Parámetros

*type*<br/>
[in] El tipo del conjunto para el parámetro.

#### <a name="remarks"></a>Observaciones

Los proveedores solo admiten los tipos de entrada y salida de parámetros admitidos por el origen de datos subyacente. El tipo es una combinación de uno o más `DBPARAMIO` valores (consulte [Estructuras DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) en la referencia del programador OLE *DB):*

- `DBPARAMIO_NOTPARAM`El descriptor de acceso no tiene parámetros. Normalmente, se `eParamIO` establece en este valor en descriptores de acceso de fila para recordar al usuario que se omiten los parámetros.

- `DBPARAMIO_INPUT`Un parámetro de entrada.

- `DBPARAMIO_OUTPUT`Un parámetro de salida.

- `DBPARAMIO_INPUT | DBPARAMIO_OUTPUT`El parámetro es un parámetro de entrada y un parámetro de salida.

#### <a name="example"></a>Ejemplo

```cpp
class CArtistsProperty
{
public:
   short m_nReturn;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

BEGIN_PARAM_MAP(CArtistsProperty)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_nReturn)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_nAge)
END_PARAM_MAP()

BEGIN_COLUMN_MAP(CArtistsProperty)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
END_COLUMN_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsProperty, L" \
      { ? = SELECT Age FROM Artists WHERE Age < ? }")
};
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="see-also"></a>Consulte también

[Macros y funciones globales para plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
