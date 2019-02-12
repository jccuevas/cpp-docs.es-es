---
title: Macros y funciones globales para las plantillas de consumidor OLE DB
ms.date: 02/11/2019
f1_keywords:
- vc.templates.ole
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
ms.openlocfilehash: 1826f674e219b850e62fdae07b3a97e8b8cf2d48
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149003"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>Macros y funciones globales para las plantillas de consumidor OLE DB

Las plantillas de consumidor OLE DB se incluyen las siguientes macros y funciones globales:

## <a name="global-functions"></a>Funciones globales

|||
|-|-|
|[AtlTraceErrorRecords](#atltraceerrorrecords)|Vuelca la información de registro de Error de OLE DB para el dispositivo de volcado de memoria si se devuelve un error.|

## <a name="accessor-map-macros"></a>Macros de mapa de descriptor de acceso

|||
|-|-|
|[BEGIN_ACCESSOR](#begin_accessor)|Marca el principio de una entrada de descriptor de acceso.|
|[BEGIN_ACCESSOR_MAP](#begin_accessor_map)|Marca el principio de las entradas de asignación de descriptores de acceso.|
|[END_ACCESSOR](#end_accessor)|Marca el final de una entrada de descriptor de acceso.|
|[END_ACCESSOR_MAP](#end_accessor_map)|Marca el final de las entradas de asignación de descriptor de acceso.|

## <a name="column-map-macros"></a>Macros de mapa de columna

|||
|-|-|
|[BEGIN_COLUMN_MAP](#begin_column_map)|Marca el principio de las entradas de asignación de columna en la clase de registro de usuario.|
|[BLOB_ENTRY](#blob_entry)|Se usa para enlazar un objeto binario grande (BLOB).|
|[BLOB_ENTRY_LENGTH](#blob_entry_length)|Notifica la longitud de la columna de datos BLOB.|
|[BLOB_ENTRY_LENGTH_STATUS](#blob_entry_length_status)|Informa de la longitud y el estado de la columna de datos BLOB.|
|[BLOB_ENTRY_STATUS](#blob_entry_status)|Informa del estado de la columna de datos BLOB.|
|[BLOB_NAME](#blob_name)|Se usa para enlazar un objeto binario grande por nombre de columna.|
|[BLOB_NAME_LENGTH](#blob_name_length)|Notifica la longitud de la columna de datos BLOB.|
|[BLOB_NAME_LENGTH_STATUS](#blob_name_length_status)|Informa de la longitud y el estado de la columna de datos BLOB.|
|[BLOB_NAME_STATUS](#blob_name_status)|Informa del estado de la columna de datos BLOB.|
|[BOOKMARK_ENTRY](#bookmark_entry)|Representa una entrada de marcador en el conjunto de filas. Una entrada de marcador es un tipo especial de entrada de la columna.|
|[COLUMN_ENTRY](#column_entry)|Representa un enlace a una columna específica de la base de datos.|
|[COLUMN_ENTRY_EX](#column_entry_ex)|Representa un enlace a la columna concreta de la base de datos. Admite *tipo*, *longitud*, *precisión*, *escala*, y *estado* parámetros.|
|[COLUMN_ENTRY_LENGTH](#column_entry_length)|Representa un enlace a la columna concreta de la base de datos. Admite la *longitud* variable.|
|[COLUMN_ENTRY_LENGTH_STATUS](#column_entry_length_status)|Representa un enlace a la columna concreta de la base de datos. Admite *estado* y *longitud* parámetros.|
|[COLUMN_ENTRY_PS](#column_entry_ps)|Representa un enlace a la columna concreta de la base de datos. Admite *precisión* y *escala* parámetros.|
|[COLUMN_ENTRY_PS_LENGTH](#column_entry_ps_length)|Representa un enlace a la columna concreta de la base de datos. Admite la *longitud* variable, *precisión* y *escala* parámetros.|
|[COLUMN_ENTRY_PS_LENGTH_STATUS](#column_entry_ps_length_status)|Representa un enlace a la columna concreta de la base de datos. Admite *estado* y *longitud* variables, *precisión* y *escala* parámetros.|
|[COLUMN_ENTRY_PS_STATUS](#column_entry_ps_status)|Representa un enlace a la columna concreta de la base de datos. Admite la *estado* variable, *precisión* y *escala* parámetros.|
|[COLUMN_ENTRY_STATUS](#column_entry_status)|Representa un enlace a la columna concreta de la base de datos. Admite la *estado* variable.|
|[COLUMN_ENTRY_TYPE](#column_entry_type)|Representa un enlace a una columna específica de la base de datos. Admite *tipo* parámetro.|
|[COLUMN_ENTRY_TYPE_SIZE](#column_entry_type_size)|Representa un enlace a la columna concreta de la base de datos. Admite *tipo* y *tamaño* parámetros.|
|[COLUMN_NAME](#column_name)|Representa un enlace a una columna específica de la base de datos por nombre.|
|[COLUMN_NAME_EX](#column_name_ex)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación de tipo de datos, tamaño, precisión, escala, longitud de la columna y estado de la columna.|
|[COLUMN_NAME_LENGTH](#column_name_length)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación de longitud de la columna.|
|[COLUMN_NAME_LENGTH_STATUS](#column_name_length_status)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación de longitud de columna y el estado.|
|[COLUMN_NAME_PS](#column_name_ps)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación de precisión y escala.|
|[COLUMN_NAME_PS_LENGTH](#column_name_ps_length)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación de precisión, escala y columna de longitud.|
|[COLUMN_NAME_PS_LENGTH_STATUS](#column_name_ps_length_status)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación de precisión, escala, longitud de la columna y estado de la columna.|
|[COLUMN_NAME_PS_STATUS](#column_name_ps_status)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación de precisión, escala y columna de estado.|
|[COLUMN_NAME_STATUS](#column_name_status)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación de estado de la columna.|
|[COLUMN_NAME_TYPE](#column_name_type)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación de tipo de datos.|
|[COLUMN_NAME_TYPE_PS](#column_name_type_ps)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación de tipo de datos, precisión y escala.|
|[COLUMN_NAME_TYPE_SIZE](#column_name_type_size)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación de tamaño y tipo de datos.|
|[COLUMN_NAME_TYPE_STATUS](#column_name_type_status)|Representa un enlace a una columna específica de la base de datos por nombre. Admite la especificación de estado de tipo y la columna de datos.|
|[END_COLUMN_MAP](#end_column_map)|Marca el final de las entradas de asignación de columna.|

## <a name="command-macros"></a>Macros de comandos

|||
|-|-|
|[DEFINE_COMMAND](#define_command)|Especifica el comando que se usará para crear el conjunto de filas cuando se usa el [CCommand](../../data/oledb/ccommand-class.md) clase. Acepta solo los tipos de cadena que coincida con el tipo de aplicación especificado (ANSI o Unicode). Se recomienda que utilice [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) en lugar de DEFINE_COMMAND.|
|[DEFINE_COMMAND_EX](#define_command_ex)|Especifica el comando que se usará para crear el conjunto de filas cuando se usa el [CCommand](../../data/oledb/ccommand-class.md) clase. Admite aplicaciones ANSI y Unicode.|

## <a name="parameter-map-macros"></a>Macros de mapa de parámetro

|||
|-|-|
|[BEGIN_PARAM_MAP](#begin_param_map)|Marca el principio de las entradas de asignación de parámetro en la clase de registro de usuario.|
|[END_PARAM_MAP](#end_param_map)|Marca el final de las entradas de asignación de parámetro.|
|[SET_PARAM_TYPE](#set_param_type)|Especifica las macros COLUMN_ENTRY que siguen el set_param_type (macro) como entrada, salida o entrada/salida.|

### <a name="atltraceerrorrecords"></a> AtlTraceErrorRecords

Vuelca la información de registro de Error de OLE DB para el dispositivo de volcado de memoria si se devuelve un error.

#### <a name="syntax"></a>Sintaxis

```cpp
inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);
```

#### <a name="parameters"></a>Parámetros

*hErr*<br/>
[in] Un valor HRESULT devuelto por una función miembro de plantilla de consumidor OLE DB.

#### <a name="remarks"></a>Comentarios

Si *hErr* no es S_OK, `AtlTraceErrorRecords` vuelca la información de registro de Error de OLE DB para el dispositivo de volcado de memoria (el **depurar** la ficha de la ventana de salida o un archivo). La información de registro de Error que se obtiene desde el proveedor, incluye el número de fila, origen, descripción, archivo de ayuda, contexto y GUID para cada entrada de registro de error. `AtlTraceErrorRecords` Esta información sólo en las compilaciones de depuración de volcados de memoria. En las compilaciones de versión es un código auxiliar vacío que se ha optimizado fuera. Para obtener más información, consulte [CDBErrorInfo (clase)](../../data/oledb/cdberrorinfo-class.md).

### <a name="begin_accessor"></a> BEGIN_ACCESSOR

Marca el principio de una entrada de descriptor de acceso.

#### <a name="syntax"></a>Sintaxis

```cpp
BEGIN_ACCESSOR(num, bAuto)
```

#### <a name="parameters"></a>Parámetros

*num*<br/>
[in] El número de desplazamiento de cero para el descriptor de acceso en esta asignación de descriptor de acceso.

*bAuto*<br/>
[in] Especifica si este descriptor de acceso es un descriptor de acceso automático o manual un descriptor de acceso. Si **true**, el descriptor de acceso es automático; si **false**, el descriptor de acceso es manual. Un descriptor de acceso automático significa que los datos se capturan en las operaciones de movimiento.

#### <a name="remarks"></a>Comentarios

En el caso de varios descriptores de acceso en un conjunto de filas, deberá especificar BEGIN_ACCESSOR_MAP y utilizar la macro BEGIN_ACCESSOR para cada descriptor de acceso individual. La macro BEGIN_ACCESSOR finaliza con la macro END_ACCESSOR. La macro BEGIN_ACCESSOR_MAP se ha completado con el END_ACCESSOR_MAP (macro).

#### <a name="example"></a>Ejemplo

Consulte [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_accessor_map"></a> BEGIN_ACCESSOR_MAP

Marca el principio de las entradas de asignación de descriptores de acceso.

#### <a name="syntax"></a>Sintaxis

```cpp
BEGIN_ACCESSOR_MAP(x, num)
```

#### <a name="parameters"></a>Parámetros

*x*<br/>
[in] Nombre de la clase de registro de usuario.

*num*<br/>
[in] Número de descriptores de acceso de esta asignación de descriptores de acceso.

#### <a name="remarks"></a>Comentarios

En el caso de varios descriptores de acceso en un conjunto de filas, deberá especificar BEGIN_ACCESSOR_MAP al principio y usar la macro BEGIN_ACCESSOR para cada descriptor de acceso individual. La macro BEGIN_ACCESSOR finaliza con la macro END_ACCESSOR. Se ha completado la asignación de descriptor de acceso con el END_ACCESSOR_MAP (macro).

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

### <a name="end_accessor"></a> END_ACCESSOR

Marca el final de una entrada de descriptor de acceso.

#### <a name="syntax"></a>Sintaxis

```cpp
END_ACCESSOR()
```

#### <a name="remarks"></a>Comentarios

Para varios descriptores de acceso en un conjunto de filas, deberá especificar BEGIN_ACCESSOR_MAP y utilizar la macro BEGIN_ACCESSOR para cada descriptor de acceso individual. La macro BEGIN_ACCESSOR finaliza con la macro END_ACCESSOR. La macro BEGIN_ACCESSOR_MAP se ha completado con el END_ACCESSOR_MAP (macro).

#### <a name="example"></a>Ejemplo

Consulte [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="end_accessor_map"></a> END_ACCESSOR_MAP

Marca el final de las entradas de asignación de descriptor de acceso.

#### <a name="syntax"></a>Sintaxis

```cpp
END_ACCESSOR_MAP()
```

#### <a name="remarks"></a>Comentarios

Para varios descriptores de acceso en un conjunto de filas, deberá especificar BEGIN_ACCESSOR_MAP y utilizar la macro BEGIN_ACCESSOR para cada descriptor de acceso individual. La macro BEGIN_ACCESSOR finaliza con la macro END_ACCESSOR. La macro BEGIN_ACCESSOR_MAP se ha completado con el END_ACCESSOR_MAP (macro).

#### <a name="example"></a>Ejemplo

Consulte [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_column_map"></a> BEGIN_COLUMN_MAP

Marca el inicio de una entrada de mapa de columnas.

#### <a name="syntax"></a>Sintaxis

```cpp
BEGIN_COLUMN_MAP(x)
```

#### <a name="parameters"></a>Parámetros

*x*<br/>
[in] Nombre de la clase de registro de usuario derivada de `CAccessor`.

#### <a name="remarks"></a>Comentarios

Esta macro se usa en el caso de un único descriptor de acceso en un conjunto de filas. Si tiene varios descriptores de acceso en un conjunto de filas, use [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

La macro BEGIN_COLUMN_MAP finaliza con la macro END_COLUMN_MAP. Esta macro se usa cuando solamente hay un descriptor de acceso necesario en el registro de usuario.

Las columnas corresponden a los campos del conjunto de filas que quiere enlazar.

#### <a name="example"></a>Ejemplo

Este es un mapa de columnas y parámetros de ejemplo:

<!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->

### <a name="blob_entry"></a> BLOB_ENTRY

Se utiliza con BEGIN_COLUMN_MAP y END_COLUMN_MAP para enlazar un objeto binario grande ([BLOB](https://docs.microsoft.com/previous-versions/windows/desktop/ms711511(v=vs.85))).

#### <a name="syntax"></a>Sintaxis

```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)
```

#### <a name="parameters"></a>Parámetros

*nOrdinal*<br/>
[in] El número de columna.

*IID*<br/>
[in] Interfaz GUID, tales como `IDD_ISequentialStream`, que se usa para recuperar el BLOB.

*flags*<br/>
[in] Modo de almacenamiento se marca como se define en el modelo de almacenamiento estructurado OLE (por ejemplo, `STGM_READ`).

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

#### <a name="example"></a>Ejemplo

Consulte [¿cómo se puede recuperar un BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length"></a> BLOB_ENTRY_LENGTH

Se utiliza con BEGIN_COLUMN_MAP y END_COLUMN_MAP para enlazar un objeto binario grande ([BLOB](https://docs.microsoft.com/previous-versions/windows/desktop/ms711511(v=vs.85))). Similar a [BLOB_ENTRY](../../data/oledb/blob-entry.md), salvo que esta macro también obtiene la longitud en bytes de la columna BLOB.

#### <a name="syntax"></a>Sintaxis

```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)
```

#### <a name="parameters"></a>Parámetros

*nOrdinal*<br/>
[in] El número de columna.

*IID*<br/>
[in] Interfaz GUID, tales como `IDD_ISequentialStream`, que se usa para recuperar el BLOB.

*flags*<br/>
[in] Modo de almacenamiento se marca como se define en el modelo de almacenamiento estructurado OLE (por ejemplo, `STGM_READ`).

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[out] La longitud en bytes (real) de la columna BLOB.

#### <a name="example"></a>Ejemplo

Consulte [¿cómo se puede recuperar un BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length_status"></a> BLOB_ENTRY_LENGTH_STATUS

Se utiliza con BEGIN_COLUMN_MAP y END_COLUMN_MAP para enlazar un objeto binario grande ([BLOB](https://docs.microsoft.com/previous-versions/windows/desktop/ms711511(v=vs.85))). Similar a [BLOB_ENTRY](../../data/oledb/blob-entry.md), salvo que esta macro también obtiene la longitud y el estado de la columna BLOB.

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
[in] El número de columna.

*IID*<br/>
[in] Interfaz GUID, tales como `IDD_ISequentialStream`, que se usa para recuperar el BLOB.

*flags*<br/>
[in] Modo de almacenamiento se marca como se define en el modelo de almacenamiento estructurado OLE (por ejemplo, `STGM_READ`).

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[out] La longitud en bytes (real) de la columna BLOB.

*status*<br/>
[out] El estado de la columna de datos BLOB.

#### <a name="example"></a>Ejemplo

Consulte [¿cómo se puede recuperar un BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_status"></a> BLOB_ENTRY_STATUS

Se utiliza con BEGIN_COLUMN_MAP o BEGIN_ACCESSOR_MAP para enlazar un objeto binario grande ([BLOB](https://docs.microsoft.com/previous-versions/windows/desktop/ms711511(v=vs.85))). Similar a [BLOB_ENTRY](../../data/oledb/blob-entry.md), salvo que esta macro también obtiene el estado de la columna BLOB.

#### <a name="syntax"></a>Sintaxis

```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)
```

#### <a name="parameters"></a>Parámetros

*nOrdinal*<br/>
[in] El número de columna.

*IID*<br/>
[in] Interfaz GUID, tales como `IDD_ISequentialStream`, que se usa para recuperar el BLOB.

*flags*<br/>
[in] Modo de almacenamiento se marca como se define en el modelo de almacenamiento estructurado OLE (por ejemplo, `STGM_READ`).

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*status*<br/>
[out] El estado del campo BLOB.

#### <a name="example"></a>Ejemplo

Consulte [¿cómo se puede recuperar un BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name"></a> BLOB_NAME

Se utiliza con BEGIN_COLUMN_MAP y END_COLUMN_MAP para enlazar un objeto binario grande ([BLOB](https://docs.microsoft.com/previous-versions/windows/desktop/ms711511(v=vs.85))). Similar a [BLOB_ENTRY](../../data/oledb/blob-entry.md), salvo que esta macro toma un nombre de columna en lugar de un número de columna.

#### <a name="syntax"></a>Sintaxis

```cpp
BLOB_NAME(pszName, IID, flags, data )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*IID*<br/>
[in] Interfaz GUID, tales como `IDD_ISequentialStream`, que se usa para recuperar el BLOB.

*flags*<br/>
[in] Modo de almacenamiento se marca como se define en el modelo de almacenamiento estructurado OLE (por ejemplo, `STGM_READ`).

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

#### <a name="example"></a>Ejemplo

Consulte [¿cómo se puede recuperar un BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name_length"></a> BLOB_NAME_LENGTH

Se utiliza con BEGIN_COLUMN_MAP y END_COLUMN_MAP para enlazar un objeto binario grande ([BLOB](https://docs.microsoft.com/previous-versions/windows/desktop/ms711511(v=vs.85))). Similar a [BLOB_NAME](../../data/oledb/blob-name.md), salvo que esta macro también obtiene la longitud en bytes de la columna de datos BLOB.

#### <a name="syntax"></a>Sintaxis

```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*IID*<br/>
[in] Interfaz GUID, tales como `IDD_ISequentialStream`, que se usa para recuperar el BLOB.

*flags*<br/>
[in] Modo de almacenamiento se marca como se define en el modelo de almacenamiento estructurado OLE (por ejemplo, `STGM_READ`).

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[out] La longitud en bytes (real) de la columna BLOB.

### <a name="blob_name_length_status"></a> BLOB_NAME_LENGTH_STATUS

Se utiliza con BEGIN_COLUMN_MAP y END_COLUMN_MAP para enlazar un objeto binario grande ([BLOB](https://docs.microsoft.com/previous-versions/windows/desktop/ms711511(v=vs.85))). Similar a [BLOB_NAME](../../data/oledb/blob-name.md), salvo que esta macro también obtiene la longitud y el estado de la columna de datos BLOB.

#### <a name="syntax"></a>Sintaxis

```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length, status )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*IID*<br/>
[in] Interfaz GUID, tales como `IDD_ISequentialStream`, que se usa para recuperar el BLOB.

*flags*<br/>
[in] Modo de almacenamiento se marca como se define en el modelo de almacenamiento estructurado OLE (por ejemplo, `STGM_READ`).

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[out] La longitud en bytes (real) de la columna BLOB.

*status*<br/>
[out] El estado del campo BLOB.

### <a name="blob_name_status"></a> BLOB_NAME_STATUS

Se utiliza con BEGIN_COLUMN_MAP y END_COLUMN_MAP para enlazar un objeto binario grande ([BLOB](https://docs.microsoft.com/previous-versions/windows/desktop/ms711511(v=vs.85))). Similar a [BLOB_NAME](../../data/oledb/blob-name.md), salvo que esta macro también obtiene el estado de la columna de datos BLOB.

#### <a name="syntax"></a>Sintaxis

```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data, status )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*IID*<br/>
[in] Interfaz GUID, tales como `IDD_ISequentialStream`, que se usa para recuperar el BLOB.

*flags*<br/>
[in] Modo de almacenamiento se marca como se define en el modelo de almacenamiento estructurado OLE (por ejemplo, `STGM_READ`).

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*status*<br/>
[out] El estado del campo BLOB.

### <a name="bookmark_entry"></a> BOOKMARK_ENTRY

Enlaza la columna de marcador.

#### <a name="syntax"></a>Sintaxis

```cpp
BOOKMARK_ENTRY(variable)
```

#### <a name="parameters"></a>Parámetros

*variable*<br/>
[in] La variable esté enlazado con la columna de marcador.

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

Para obtener más información, consulte [utilizar marcadores](using-bookmarks.md) y [CBookmark (clase)](../../data/oledb/cbookmark-class.md).

### <a name="column_entry"></a> COLUMN_ENTRY

Representa un enlace en el conjunto de filas a la columna del conjunto de filas.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY(nOrdinal, data)
```

#### <a name="parameters"></a>Parámetros

Consulte [DBBINDING](https://docs.microsoft.com/previous-versions/windows/desktop/ms716845(v=vs.85)) en el *referencia del programador OLE DB*.

*nOrdinal*<br/>
[in] El número de columna.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Comentarios

La macro COLUMN_ENTRY se usa en los lugares siguientes:

- Entre los [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.

- Entre los [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.

- Entre los [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

#### <a name="example"></a>Ejemplo

Vea los ejemplos en los temas de la macro, [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="column_entry_ex"></a> COLUMN_ENTRY_EX

Representa un enlace en el conjunto de filas a la columna concreta de la base de datos.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_EX(nOrdinal, wType, nLength, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parámetros

Consulte [DBBINDING](https://docs.microsoft.com/previous-versions/windows/desktop/ms716845(v=vs.85)) en el *referencia del programador OLE DB*.

*nOrdinal*<br/>
[in] El número de columna.

*wType*<br/>
[in] El tipo de datos.

*nLength*<br/>
[in] El tamaño de los datos en bytes.

*nPrecision*<br/>
[in] La precisión máxima que se utilizará al obtener datos y *wType* es `DBTYPE_NUMERIC`. En caso contrario, se omite este parámetro.

*nScale*<br/>
[in] La escala que se utilizará al obtener datos y *wType* es `DBTYPE_NUMERIC` o `DBTYPE_DECIMAL`.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[in] La variable esté enlazado con la longitud de columna.

*status*<br/>
[in] La variable esté enlazado con el estado de la columna.

#### <a name="remarks"></a>Comentarios

La macro COLUMN_ENTRY_EX se utiliza en los lugares siguientes:

- Entre los [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.

- Entre los [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.

- Entre los [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

#### <a name="example"></a>Ejemplo

Consulte [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="column_entry_length"></a> COLUMN_ENTRY_LENGTH

Representa un enlace en el conjunto de filas a la columna concreta de la base de datos.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)
```

#### <a name="parameters"></a>Parámetros

Consulte [DBBINDING](https://docs.microsoft.com/previous-versions/windows/desktop/ms716845(v=vs.85)) en el *referencia del programador OLE DB*.

*nOrdinal*<br/>
[in] El número de columna, empezando por uno. Marcador corresponde a la columna cero.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[in] La variable esté enlazado con la longitud de columna.

#### <a name="remarks"></a>Comentarios

Esta macro es compatible con la *longitud* variable. Se usa en los lugares siguientes:

- Entre los [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.

- Entre los [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.

- Entre los [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

### <a name="column_entry_length_status"></a> COLUMN_ENTRY_LENGTH_STATUS

Representa un enlace en el conjunto de filas a la columna concreta de la base de datos.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)
```

#### <a name="parameters"></a>Parámetros

Consulte [DBBINDING](https://docs.microsoft.com/previous-versions/windows/desktop/ms716845(v=vs.85)) en el *referencia del programador OLE DB*.

*nOrdinal*<br/>
[in] El número de columna.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[in] La variable esté enlazado con la longitud de columna.

*status*<br/>
[in] La variable esté enlazado con el estado de la columna.

#### <a name="remarks"></a>Comentarios

Use esta macro si desea admitir variables de estado y longitud. Se usa en los lugares siguientes:

- Entre los [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.

- Entre los [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.

- Entre los [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

### <a name="column_entry_ps"></a> COLUMN_ENTRY_PS

Representa un enlace en el conjunto de filas a la columna del conjunto de filas.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parámetros

Consulte [DBBINDING](https://docs.microsoft.com/previous-versions/windows/desktop/ms716845(v=vs.85)) en el *referencia del programador OLE DB*.

*nOrdinal*<br/>
[in] El número de columna.

*nPrecision*<br/>
[in] La precisión máxima de la columna que desea enlazar.

*nScale*<br/>
[in] La escala de la columna que desea enlazar.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Comentarios

Permite especificar la precisión y escala de la columna que desea enlazar. Se usa en los lugares siguientes:

- Entre los [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.

- Entre los [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.

- Entre los [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

### <a name="column_entry_ps_length"></a> COLUMN_ENTRY_PS_LENGTH

Representa un enlace en el conjunto de filas a la columna concreta de la base de datos.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_PS_LENGTH(nOrdinal, nPrecision, nScale, data, length)
```

#### <a name="parameters"></a>Parámetros

Consulte [DBBINDING](https://docs.microsoft.com/previous-versions/windows/desktop/ms716845(v=vs.85)) en el *referencia del programador OLE DB*.

*nOrdinal*<br/>
[in] El número de columna, empezando por uno. Marcador corresponde a la columna cero.

*nPrecision*<br/>
[in] La precisión máxima de la columna que desea enlazar.

*nScale*<br/>
[in] La escala de la columna que desea enlazar.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[in] La variable esté enlazado con la longitud de columna.

#### <a name="remarks"></a>Comentarios

Permite especificar la precisión y escala de la columna que desea enlazar. Esta macro es compatible con la *longitud* variable. Se usa en los lugares siguientes:

- Entre los [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.

- Entre los [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.

- Entre los [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

### <a name="column_entry_ps_length_status"></a> COLUMN_ENTRY_PS_LENGTH_STATUS

Representa un enlace en el conjunto de filas a la columna concreta de la base de datos.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_PS_LENGTH_STATUS(nOrdinal, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parámetros

Consulte [DBBINDING](https://docs.microsoft.com/previous-versions/windows/desktop/ms716845(v=vs.85)) en el *referencia del programador OLE DB*.

*nOrdinal*<br/>
[in] El número de columna.

*nPrecision*<br/>
[in] La precisión máxima de la columna que desea enlazar.

*nScale*<br/>
[in] La escala de la columna que desea enlazar.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[in] La variable esté enlazado con la longitud de columna.

*status*<br/>
[in] La variable esté enlazado con el estado de la columna.

#### <a name="remarks"></a>Comentarios

Permite especificar la precisión y escala de la columna que desea enlazar. Use esta macro si desea admitir variables de estado y longitud. Se usa en los lugares siguientes:

- Entre los [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.

- Entre los [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.

- Entre los [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

### <a name="column_entry_ps_status"></a> COLUMN_ENTRY_PS_STATUS

Representa un enlace en el conjunto de filas a la columna concreta de la base de datos.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_PS_STATUS(nOrdinal, nPrecision, nScale, data, status)
```

#### <a name="parameters"></a>Parámetros

Consulte [DBBINDING](https://docs.microsoft.com/previous-versions/windows/desktop/ms716845(v=vs.85)) en el *referencia del programador OLE DB*.

*nOrdinal*<br/>
[in] El número de columna.

*nPrecision*<br/>
[in] La precisión máxima de la columna que desea enlazar.

*nScale*<br/>
[in] La escala de la columna que desea enlazar.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*status*<br/>
[in] La variable esté enlazado con el estado de la columna.

#### <a name="remarks"></a>Comentarios

Permite especificar la precisión y escala de la columna que desea enlazar. Esta macro es compatible con la *estado* variable. Se usa en los lugares siguientes:

- Entre los [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.

- Entre los [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.

- Entre los [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

### <a name="column_entry_status"></a> COLUMN_ENTRY_STATUS

Representa un enlace en el conjunto de filas a la columna concreta de la base de datos.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)
```

#### <a name="parameters"></a>Parámetros

Consulte [DBBINDING](https://docs.microsoft.com/previous-versions/windows/desktop/ms716845(v=vs.85)) en el *referencia del programador OLE DB*.

*nOrdinal*<br/>
[in] El número de columna.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*status*<br/>
[in] La variable esté enlazado con el estado de la columna.

#### <a name="remarks"></a>Comentarios

Esta macro es compatible con la *estado* variable. Se usa en los lugares siguientes:

- Entre los [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.

- Entre los [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.

- Entre los [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

### <a name="column_entry_type"></a> COLUMN_ENTRY_TYPE

Representa un enlace a la columna concreta de la base de datos. Admite *tipo* parámetro.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)
```

#### <a name="parameters"></a>Parámetros

*nOrdinal*<br/>
[in] El número de columna.

*wType*<br/>
[in] Tipo de datos de entrada de la columna.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Comentarios

Esta macro es una variante especializada de la [COLUMN_ENTRY](../../data/oledb/column-entry.md) macro que proporciona una forma de especificar el tipo de datos.

### <a name="column_entry_type_size"></a> COLUMN_ENTRY_TYPE_SIZE

Representa un enlace a la columna concreta de la base de datos. Admite *tipo* y *tamaño* parámetros.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)
```

#### <a name="parameters"></a>Parámetros

*nOrdinal*<br/>
[in] El número de columna.

*wType*<br/>
[in] Tipo de datos de entrada de la columna.

*nLength*<br/>
[in] Tamaño de entrada de columna en bytes.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Comentarios

Esta macro es una variante especializada de la [COLUMN_ENTRY](../../data/oledb/column-entry.md) macro que proporciona una forma de especificar el tipo y tamaño de datos.

### <a name="column_name"></a> COLUMN_NAME

Representa un enlace en el conjunto de filas a la columna del conjunto de filas. Similar a [COLUMN_ENTRY](../../data/oledb/column-entry.md), salvo que esta macro toma el nombre de columna en lugar del número de columna.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME(pszName, data)
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Comentarios

Las macros COLUMN_NAME_ * se usan en los mismos lugares como [COLUMN_ENTRY](../../data/oledb/column-entry.md):

- Entre los [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.

- Entre los [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.

- Entre los [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.

### <a name="column_name_ex"></a> COLUMN_NAME_EX

Representa un enlace en el conjunto de filas a la columna del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), salvo que esta macro toma también el tipo de datos, tamaño, precisión, escala, longitud de la columna y estado de la columna.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*wType*<br/>
[in] El tipo de datos.

*nLength*<br/>
[in] El tamaño de los datos en bytes.

*nPrecision*<br/>
[in] La precisión máxima que se utilizará al obtener datos y *wType* es `DBTYPE_NUMERIC`. En caso contrario, se omite este parámetro.

*nScale*<br/>
[in] La escala que se utilizará al obtener datos y *wType* es `DBTYPE_NUMERIC` o `DBTYPE_DECIMAL`.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[in] La variable esté enlazado con la longitud de columna.

*status*<br/>
[in] La variable esté enlazado con el estado de la columna.

#### <a name="remarks"></a>Comentarios

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_ *.

### <a name="column_name_length"></a> COLUMN_NAME_LENGTH

Representa un enlace en el conjunto de filas a la columna del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), salvo que esta macro toma también la longitud de la columna.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_LENGTH(pszName, data, length)
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[in] La variable esté enlazado con la longitud de columna.

#### <a name="remarks"></a>Comentarios

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_ *.

### <a name="column_name_length_status"></a> COLUMN_NAME_LENGTH_STATUS

Representa un enlace en el conjunto de filas a la columna del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), salvo que esta macro también tiene la longitud de columna y el estado de la columna.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_LENGTH_STATUS(pszName, data, length, status )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[in] La variable esté enlazado con la longitud de columna.

*status*<br/>
[in] La variable esté enlazado con el estado de la columna.

#### <a name="remarks"></a>Comentarios

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_ *.

### <a name="column_name_ps"></a> COLUMN_NAME_PS

Representa un enlace en el conjunto de filas a la columna del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), salvo que esta macro también toma la precisión y escala.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_PS(pszName, nPrecision, nScale, data )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*nPrecision*<br/>
[in] La precisión máxima de la columna que desea enlazar.

*nScale*<br/>
[in] La escala de la columna que desea enlazar.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Comentarios

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_ *.

### <a name="column_name_ps_length"></a> COLUMN_NAME_PS_LENGTH

Representa un enlace en el conjunto de filas a la columna del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), salvo que esta macro también toma la precisión, escala y columna de longitud.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_PS_LENGTH(pszName, nPrecision, nScale, data, length )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*nPrecision*<br/>
[in] La precisión máxima de la columna que desea enlazar.

*nScale*<br/>
[in] La escala de la columna que desea enlazar.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[in] La variable esté enlazado con la longitud de columna.

#### <a name="remarks"></a>Comentarios

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_ *.

### <a name="column_name_ps_length_status"></a> COLUMN_NAME_PS_LENGTH_STATUS

Representa un enlace en el conjunto de filas a la columna del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), salvo que esta macro toma también precisión, escala, longitud de la columna y estado de la columna.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*nPrecision*<br/>
[in] La precisión máxima de la columna que desea enlazar.

*nScale*<br/>
[in] La escala de la columna que desea enlazar.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*length*<br/>
[in] La variable esté enlazado con la longitud de columna.

*status*<br/>
[in] La variable esté enlazado con el estado de la columna.

#### <a name="remarks"></a>Comentarios

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_ *.

### <a name="column_name_ps_status"></a> COLUMN_NAME_PS_STATUS

Representa un enlace en el conjunto de filas a la columna del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), salvo que esta macro también toma la precisión, escala y columna de estado.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_PS_STATUS(pszName, nPrecision, nScale, data, status )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*nPrecision*<br/>
[in] La precisión máxima de la columna que desea enlazar.

*nScale*<br/>
[in] La escala de la columna que desea enlazar.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*status*<br/>
[in] La variable esté enlazado con el estado de la columna.

#### <a name="remarks"></a>Comentarios

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_ *.

### <a name="column_name_status"></a> COLUMN_NAME_STATUS

Representa un enlace en el conjunto de filas a la columna del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), salvo que esta macro toma también el estado de la columna.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_STATUS(pszName, data, status )
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

*status*<br/>
[in] La variable esté enlazado con el estado de la columna.

#### <a name="remarks"></a>Comentarios

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_ *.

### <a name="column_name_type"></a> COLUMN_NAME_TYPE

Representa un enlace en el conjunto de filas a la columna del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), salvo que esta macro toma también el tipo de datos.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_TYPE(pszName, wType, data)
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*wType*<br/>
[in] El tipo de datos.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Comentarios

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_ *.

### <a name="column_name_type_ps"></a> COLUMN_NAME_TYPE_PS

Representa un enlace en el conjunto de filas a la columna del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), salvo que esta macro toma también el tipo de datos, precisión y escala.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*wType*<br/>
[in] El tipo de datos.

*nPrecision*<br/>
[in] La precisión máxima que se utilizará al obtener datos y *wType* es `DBTYPE_NUMERIC`. En caso contrario, se omite este parámetro.

*nScale*<br/>
[in] La escala que se utilizará al obtener datos y *wType* es `DBTYPE_NUMERIC` o `DBTYPE_DECIMAL`.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Comentarios

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_ *.

### <a name="column_name_type_size"></a> COLUMN_NAME_TYPE_SIZE

Representa un enlace en el conjunto de filas a la columna del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), salvo que esta macro toma también el tipo de datos y el tamaño.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*wType*<br/>
[in] El tipo de datos.

*nLength*<br/>
[in] El tamaño de los datos en bytes.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Comentarios

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_ *.

### <a name="column_name_type_status"></a> COLUMN_NAME_TYPE_STATUS

Representa un enlace en el conjunto de filas a la columna del conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), salvo que esta macro toma también el estado de tipo y la columna de datos.

#### <a name="syntax"></a>Sintaxis

```cpp
COLUMN_NAME_TYPE_STATUS(pszName, wType, status, data)
```

#### <a name="parameters"></a>Parámetros

*pszName*<br/>
[in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando 'L' delante del nombre, por ejemplo: `L"MyColumn"`.

*wType*<br/>
[in] El tipo de datos.

*status*<br/>
[in] La variable esté enlazado con el estado de la columna.

*data*<br/>
[in] El miembro de datos correspondiente en el registro de usuario.

#### <a name="remarks"></a>Comentarios

Consulte [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde se utilizan las macros COLUMN_NAME_ *.

### <a name="end_column_map"></a> END_COLUMN_MAP

Marca el final de las entradas de asignación de columna.

#### <a name="syntax"></a>Sintaxis

```cpp
END_COLUMN_MAP()
```

#### <a name="remarks"></a>Comentarios

Se usa con un descriptor de acceso en un conjunto de filas. La macro BEGIN_COLUMN_MAP finaliza con la macro END_COLUMN_MAP.

#### <a name="example"></a>Ejemplo

See [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).

### <a name="define_command"></a> DEFINE_COMMAND

Especifica el comando que se usará para crear el conjunto de filas cuando se usa el [CCommand](../../data/oledb/ccommand-class.md) clase. Acepta solo los tipos de cadena que coincida con el tipo de aplicación especificado (ANSI o Unicode).

> [!NOTE]
>  Se recomienda que utilice [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) en lugar de DEFINE_COMMAND.

#### <a name="syntax"></a>Sintaxis

```cpp
DEFINE_COMMAND(x, szCommand)
```

#### <a name="parameters"></a>Parámetros

*x*<br/>
[in] El nombre de la clase de registro (comando) del usuario.

*szCommand*<br/>
[in] La cadena de comandos que se usará para crear el conjunto de filas cuando se usa [CCommand](../../data/oledb/ccommand-class.md).

#### <a name="remarks"></a>Comentarios

La cadena de comandos que especifique se usará como el valor predeterminado si no especifica el texto del comando en el [CCommand:: Open](../../data/oledb/ccommand-open.md) método.

Esta macro acepta cadenas de ANSI si compila la aplicación como ANSI o cadenas Unicode si compila la aplicación como Unicode. Se recomienda que utilice [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) en lugar de DEFINE_COMMAND, porque la primera acepta cadenas Unicode, independientemente del tipo de aplicación ANSI o Unicode.

#### <a name="example"></a>Ejemplo

Consulte [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="define_command_ex"></a> DEFINE_COMMAND_EX

Especifica el comando que se usará para crear el conjunto de filas cuando se usa el [CCommand](../../data/oledb/ccommand-class.md) clase. Es compatible con las aplicaciones de Unicode y ANSI.

#### <a name="syntax"></a>Sintaxis

```cpp
DEFINE_COMMAND_EX(x, wszCommand)
```

#### <a name="parameters"></a>Parámetros

*x*<br/>
[in] El nombre de la clase de registro (comando) del usuario.

*wszCommand*<br/>
[in] La cadena de comandos que se usará para crear el conjunto de filas cuando se usa [CCommand](../../data/oledb/ccommand-class.md).

#### <a name="remarks"></a>Comentarios

La cadena de comandos que especifique se usará como el valor predeterminado si no especifica el texto del comando en el [CCommand:: Open](../../data/oledb/ccommand-open.md) método.

Esta macro acepta cadenas Unicode, independientemente del tipo de aplicación. Esta macro es preferible [DEFINE_COMMAND](../../data/oledb/define-command.md) porque es compatible con Unicode, así como aplicaciones ANSI.

#### <a name="example"></a>Ejemplo

Consulte [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="begin_param_map"></a> BEGIN_PARAM_MAP

Marca el principio de las entradas de asignación de parámetro.

#### <a name="syntax"></a>Sintaxis

```cpp
BEGIN_PARAM_MAP(x)
```

#### <a name="parameters"></a>Parámetros

*x*<br/>
[in] Nombre de la clase de registro de usuario.

#### <a name="remarks"></a>Comentarios

Usa parámetros [comandos](https://docs.microsoft.com/previous-versions/windows/desktop/ms724608(v=vs.85)).

#### <a name="example"></a>Ejemplo

Vea el ejemplo de la [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) macro.

### <a name="end_param_map"></a> END_PARAM_MAP

Marca el final de las entradas de asignación de parámetro.

#### <a name="syntax"></a>Sintaxis

```cpp
END_PARAM_MAP()
```

#### <a name="example"></a>Ejemplo

Vea el ejemplo de la [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) macro.

### <a name="set_param_type"></a> SET_PARAM_TYPE

Especifica las macros COLUMN_ENTRY que siguen a la entrada de la macro SET_PARAM_TYPE, salida o entrada/salida.

#### <a name="syntax"></a>Sintaxis

```cpp
SET_PARAM_TYPE(type)
```

#### <a name="parameters"></a>Parámetros

*type*<br/>
[in] El tipo del conjunto para el parámetro.

#### <a name="remarks"></a>Comentarios

Los proveedores solo admiten los tipos de entrada y salida de parámetros admitidos por el origen de datos subyacente. El tipo es una combinación de uno o varios `DBPARAMIO` valores (consulte [estructuras DBBINDING](https://docs.microsoft.com/previous-versions/windows/desktop/ms716845(v=vs.85)) en el *referencia del programador de OLE DB*):

- `DBPARAMIO_NOTPARAM` El descriptor de acceso no tiene parámetros. Normalmente, se establece `eParamIO` en este valor en los descriptores de acceso de fila para recordar al usuario que se omiten los parámetros.

- `DBPARAMIO_INPUT` Un parámetro de entrada.

- `DBPARAMIO_OUTPUT` Un parámetro de salida.

- `DBPARAMIO_INPUT | DBPARAMIO_OUTPUT` El parámetro es una entrada y un parámetro de salida.

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

## <a name="see-also"></a>Vea también

[Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)