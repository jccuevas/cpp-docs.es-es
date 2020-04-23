---
title: CArchive (clase)
ms.date: 11/04/2016
f1_keywords:
- CArchive
- AFX/CArchive
- AFX/CArchive::CArchive
- AFX/CArchive::Abort
- AFX/CArchive::Close
- AFX/CArchive::Flush
- AFX/CArchive::GetFile
- AFX/CArchive::GetObjectSchema
- AFX/CArchive::IsBufferEmpty
- AFX/CArchive::IsLoading
- AFX/CArchive::IsStoring
- AFX/CArchive::MapObject
- AFX/CArchive::Read
- AFX/CArchive::ReadClass
- AFX/CArchive::ReadObject
- AFX/CArchive::ReadString
- AFX/CArchive::SerializeClass
- AFX/CArchive::SetLoadParams
- AFX/CArchive::SetObjectSchema
- AFX/CArchive::SetStoreParams
- AFX/CArchive::Write
- AFX/CArchive::WriteClass
- AFX/CArchive::WriteObject
- AFX/CArchive::WriteString
- AFX/CArchive::m_pDocument
helpviewer_keywords:
- CArchive [MFC], CArchive
- CArchive [MFC], Abort
- CArchive [MFC], Close
- CArchive [MFC], Flush
- CArchive [MFC], GetFile
- CArchive [MFC], GetObjectSchema
- CArchive [MFC], IsBufferEmpty
- CArchive [MFC], IsLoading
- CArchive [MFC], IsStoring
- CArchive [MFC], MapObject
- CArchive [MFC], Read
- CArchive [MFC], ReadClass
- CArchive [MFC], ReadObject
- CArchive [MFC], ReadString
- CArchive [MFC], SerializeClass
- CArchive [MFC], SetLoadParams
- CArchive [MFC], SetObjectSchema
- CArchive [MFC], SetStoreParams
- CArchive [MFC], Write
- CArchive [MFC], WriteClass
- CArchive [MFC], WriteObject
- CArchive [MFC], WriteString
- CArchive [MFC], m_pDocument
ms.assetid: 9e950d23-b874-456e-ae4b-fe00781a7699
ms.openlocfilehash: ef8b6ec9060e8c15dd45f8203dadd2a2aca9e168
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753100"
---
# <a name="carchive-class"></a>CArchive (clase)

Le permite guardar una red compleja de objetos en una forma binaria permanente (normalmente almacenamiento en disco) que persiste después de eliminar esos objetos.

## <a name="syntax"></a>Sintaxis

```
class CArchive
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CArchive::CArchive](#carchive)|Crea un objeto `CArchive` .|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CArchive::Abort](#abort)|Cierra un archivo sin producir una excepción.|
|[CArchive::Cerrar](#close)|Vacía los datos no escritos `CFile`y se desconecta del archivo .|
|[CArchive::Flush](#flush)|Vacía los datos no escritos del búfer de archivado.|
|[CArchive::GetFile](#getfile)|Obtiene el `CFile` puntero de objeto para este archivo.|
|[CArchive::GetObjectSchema](#getobjectschema)|Se llama `Serialize` desde la función para determinar la versión del objeto que se está deserializando.|
|[CArchive::IsBufferEmpty](#isbufferempty)|Determina si el búfer se ha vaciado durante un proceso de recepción de Windows Sockets.|
|[CArchive::IsLoading](#isloading)|Determina si el archivo se está cargando.|
|[CArchive::IsStoring](#isstoring)|Determina si el archivo se está almacenando.|
|[CArchive::MapObject](#mapobject)|Coloca objetos en el mapa que no se serializan en el archivo, pero que están disponibles para que los subobjetos hagan referencia.|
|[CArchive::Leer](#read)|Lee bytes sin procesar.|
|[CArchive::ReadClass](#readclass)|Lee una referencia de `WriteClass`clase previamente almacenada con .|
|[CArchive::ReadObject](#readobject)|Llama a la `Serialize` función de un objeto para cargar.|
|[CArchive::ReadString](#readstring)|Lee una sola línea de texto.|
|[CArchive::SerializeClass](#serializeclass)|Lee o escribe la referencia `CArchive` de clase al objeto `CArchive`en función de la dirección del archivo .|
|[CArchive::SetLoadParams](#setloadparams)|Establece el tamaño al que crece la matriz de carga. Debe llamarse antes de cargar `MapObject` `ReadObject` cualquier objeto o antes o se llama.|
|[CArchive::SetObjectSchema](#setobjectschema)|Establece el esquema de objeto almacenado en el objeto de archivado.|
|[CArchive::SetStoreParams](#setstoreparams)|Establece el tamaño de la tabla hash y el tamaño de bloque del mapa utilizado para identificar objetos únicos durante el proceso de serialización.|
|[CArchive::Escribir](#write)|Escribe bytes sin procesar.|
|[CArchive::WriteClass](#writeclass)|Escribe una referencia `CRuntimeClass` al `CArchive`archivo .|
|[CArchive::WriteObject](#writeobject)|Llama a la `Serialize` función de un objeto para almacenar.|
|[CArchive::WriteString](#writestring)|Escribe una sola línea de texto.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CArchive::operador&lt;&lt;](#operator_lt_lt)|Almacena objetos y tipos primitivos en el archivo.|
|[CArchive::operador&gt;&gt;](#operator_gt_gt)|Carga objetos y tipos primitivos desde el archivo.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CArchive::m_pDocument](#m_pdocument)||

## <a name="remarks"></a>Observaciones

`CArchive`no tiene una clase base.

Más adelante puede cargar los objetos desde el almacenamiento persistente, reconstituyéndolos en la memoria. Este proceso de hacer que los datos sean persistentes se denomina "serialización".

Puede pensar en un objeto de archivo como un tipo de secuencia binaria. Al igual que una secuencia de entrada/salida, un archivo está asociado a un archivo y permite la escritura y lectura en búfer de datos hacia y desde el almacenamiento. Una secuencia de entrada/salida procesa secuencias de caracteres ASCII, pero un archivo procesa los datos de objetos binarios en un formato eficiente y no redundante.

Debe crear un [CFile](../../mfc/reference/cfile-class.md) objeto antes `CArchive` de poder crear un objeto. Además, debe asegurarse de que el estado de carga/tienda del archivo es compatible con el modo abierto del archivo. Está limitado a un archivo activo por archivo.

Cuando se `CArchive` construye un objeto, se adjunta `CFile` a un objeto de clase (o una clase derivada) que representa un archivo abierto. También se especifica si el archivo se utilizará para cargar o almacenar. Un `CArchive` objeto puede procesar no solo tipos primitivos, sino también objetos de clases derivadas de [CObject](../../mfc/reference/cobject-class.md)diseñadas para la serialización. Una clase serializable `Serialize` normalmente tiene una función miembro y normalmente `CObject`usa las macros [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL,](../../mfc/reference/run-time-object-model-services.md#implement_serial) como se describe en la clase .

Los operadores **>>** de extracción **<<** sobrecargada ( ) e inserción `CObject`( ) son interfaces de programación de archivado convenientes que admiten tipos primitivos y clases derivadas.

`CArchive`También admite la programación con las clases de Windows Sockets de MFC [CSocket](../../mfc/reference/csocket-class.md) y [CSocketFile](../../mfc/reference/csocketfile-class.md). El [IsBufferEmpty](#isbufferempty) función miembro admite ese uso.

Para obtener `CArchive`más información sobre , vea los artículos [Serialización](../../mfc/serialization-in-mfc.md) y [Windows Sockets: Uso](../../mfc/windows-sockets-using-sockets-with-archives.md)de sockets con archivos .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CArchive`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="carchiveabort"></a><a name="abort"></a>CArchive::Abort

Llame a esta función para cerrar el archivo sin producir una excepción.

```cpp
void Abort ();
```

### <a name="remarks"></a>Observaciones

Normalmente, `CArchive` el `Close`destructor llamará a , que vaciará `CFile` los datos que no se hayan guardado en el objeto asociado. Esto puede provocar excepciones.

Al detectar estas excepciones, es una `Abort`buena idea usar `CArchive` , para que la destrucción del objeto no cause más excepciones. Al controlar excepciones, `CArchive::Abort` no se producirá una excepción en los errores porque, a diferencia de [CArchive::Close](#close), `Abort` omite los errores.

Si usó **new** para `CArchive` asignar el objeto en el montón, debe eliminarlo después de cerrar el archivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CArchive::WriteClass](#writeclass).

## <a name="carchivecarchive"></a><a name="carchive"></a>CArchive::CArchive

Construye un `CArchive` objeto y especifica si se usará para cargar o almacenar objetos.

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>Parámetros

*pFile*<br/>
Puntero al `CFile` objeto que es el origen o destino final de los datos persistentes.

*nMode*<br/>
Marca que especifica si los objetos se cargarán o almacenarán en el archivo. El *nMode* parámetro debe tener uno de los siguientes valores:

- `CArchive::load`Carga datos del archivo. Solo requiere `CFile` permiso de lectura.

- `CArchive::store`Guarda los datos en el archivo. Requiere `CFile` permiso de escritura.

- `CArchive::bNoFlushOnDelete`Impide que el `Flush` archivo llame automáticamente cuando se llama al destructor de archivado. Si establece esta marca, es responsable `Close` de llamar explícitamente antes de llamar al destructor. Si no lo hace, sus datos estarán dañados.

*nBufSize*<br/>
Entero que especifica el tamaño del búfer de archivos interno, en bytes. Tenga en cuenta que el tamaño de búfer predeterminado es de 4.096 bytes. Si archiva objetos grandes de forma rutinaria, mejorará el rendimiento si utiliza un tamaño de búfer mayor que es un múltiplo del tamaño del búfer de archivos.

*lpBuf*<br/>
Un puntero opcional a un búfer proporcionado por el usuario de tamaño *nBufSize*. Si no especifica este parámetro, el archivo asigna un búfer del montón local y lo libera cuando se destruye el objeto. El archivo no libera un búfer proporcionado por el usuario.

### <a name="remarks"></a>Observaciones

No puede cambiar esta especificación después de haber creado el archivo.

No puede `CFile` utilizar operaciones para modificar el estado del archivo hasta que haya cerrado el archivo. Cualquier operación de este tipo dañará la integridad del archivo. Puede tener acceso a la posición del puntero de archivo en cualquier momento durante la serialización obteniendo el objeto de archivo del archivo de la [GetFile](#getfile) función miembro y, a continuación, mediante el [CFile::GetPosition](../../mfc/reference/cfile-class.md#getposition) función. Debe llamar a [CArchive::Flush](#flush) antes de obtener la posición del puntero de archivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

## <a name="carchiveclose"></a><a name="close"></a>CArchive::Cerrar

Vacía los datos restantes en el búfer, cierra el archivo y desconecta el archivo del archivo.

```cpp
void Close();
```

### <a name="remarks"></a>Observaciones

No se permiten más operaciones en el archivo. Después de cerrar un archivo, puede crear otro archivo para el mismo archivo o puede cerrar el archivo.

La función `Close` miembro garantiza que todos los datos se transfieren desde el archivo al archivo y hace que el archivo no esté disponible. Para completar la transferencia del archivo al medio de almacenamiento, primero debe `CFile` usar [CFile::Close](../../mfc/reference/cfile-class.md#close) y, a continuación, destruir el objeto.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CArchive::WriteString](#writestring).

## <a name="carchiveflush"></a><a name="flush"></a>CArchive::Flush

Obliga a que los datos que queden en el búfer de archivado se escriban en el archivo.

```cpp
void Flush();
```

### <a name="remarks"></a>Observaciones

La función `Flush` miembro garantiza que todos los datos se transfieren desde el archivo al archivo. Debe llamar a [CFile::Close](../../mfc/reference/cfile-class.md#close) para completar la transferencia desde el archivo al medio de almacenamiento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

## <a name="carchivegetfile"></a><a name="getfile"></a>CArchive::GetFile

Obtiene el `CFile` puntero de objeto para este archivo.

```
CFile* GetFile() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero constante `CFile` al objeto en uso.

### <a name="remarks"></a>Observaciones

Debe vaciar el archivo `GetFile`antes de utilizar .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

## <a name="carchivegetobjectschema"></a><a name="getobjectschema"></a>CArchive::GetObjectSchema

Llame a esta `Serialize` función desde la función para determinar la versión del objeto que se está deserializando actualmente.

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>Valor devuelto

Durante la deserialización, la versión del objeto que se está leyendo.

### <a name="remarks"></a>Observaciones

Llamar a esta función `CArchive` solo es válido cuando se carga el objeto ( [CArchive::IsLoading](#isloading) devuelve distinto de cero). Debe ser la primera `Serialize` llamada en la función y llamar sólo una vez. Un valor devuelto de ( UINT)-1 indica que el número de versión es desconocido.

Una `CObject`clase derivada puede utilizar VERSIONABLE_SCHEMA combinado (mediante **OR**bit a bit ) con la propia versión del esquema (en la macro IMPLEMENT_SERIAL) para crear un "objeto versionable", es decir, un objeto cuya `Serialize` función miembro puede leer varias versiones. La funcionalidad de marco predeterminada (sin VERSIONABLE_SCHEMA) es producir una excepción cuando la versión no coincide.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

## <a name="carchiveisbufferempty"></a><a name="isbufferempty"></a>CArchive::IsBufferEmpty

Llame a esta función miembro para determinar si el búfer interno del objeto de archivado está vacío.

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el búfer del archivo está vacío; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función se proporciona para admitir `CSocketFile`la programación con la clase Mfc Windows Sockets . No es necesario utilizarlo para un `CFile` archivo asociado a un objeto.

La razón `IsBufferEmpty` para usar con `CSocketFile` un archivo asociado a un objeto es que el búfer del archivo puede contener más de un mensaje o registro. Después de recibir un `IsBufferEmpty` mensaje, debe usar para controlar un bucle que continúa recibiendo datos hasta que el búfer está vacío. Para obtener más información, vea `CAsyncSocket`la función miembro `IsBufferEmpty` [Receive](../../mfc/reference/casyncsocket-class.md#receive) de la clase , que muestra cómo usar .

Para obtener más información, consulte [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="carchiveisloading"></a><a name="isloading"></a>CArchive::IsLoading

Determina si el archivo está cargando datos.

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el archivo se utiliza actualmente para la carga; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Las funciones de `Serialize` las clases archivadas llaman a esta función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

## <a name="carchiveisstoring"></a><a name="isstoring"></a>CArchive::IsStoring

Determina si el archivo almacena datos.

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el archivo se utiliza actualmente para almacenar; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Las funciones de `Serialize` las clases archivadas llaman a esta función miembro.

Si `IsStoring` el estado de un archivo `IsLoading` es distinto de cero, su estado es 0, y viceversa.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

## <a name="carchivemapobject"></a><a name="mapobject"></a>CArchive::MapObject

Llame a esta función miembro para colocar objetos en el mapa que no se serializan realmente en el archivo, pero que están disponibles para que los subobjetos hagan referencia.

```cpp
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>Parámetros

*Pob*<br/>
Puntero constante al objeto que se va a almacenar.

### <a name="remarks"></a>Observaciones

Por ejemplo, es posible que no serialice un documento, pero serializaría los elementos que forman parte del documento. Al `MapObject`llamar a , permite que esos elementos, o subobjetos, hagan referencia al documento. Además, los subelementos serializados pueden serializar su *puntero m_pDocument* hacia atrás.

Puede llamar `MapObject` cuando almacene y cargue `CArchive` desde el objeto. `MapObject`agrega el objeto especificado a las estructuras `CArchive` de datos internas mantenidas por el objeto durante la serialización y deserialización, pero a diferencia de [ReadObject](#readobject) y [WriteObject](#writeobject), no llama a serializar en el objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

## <a name="carchivem_pdocument"></a><a name="m_pdocument"></a>CArchive::m_pDocument

Establecido en NULL de forma `CDocument` predeterminada, este puntero a `CArchive` a se puede establecer en cualquier cosa que el usuario de la instancia desee.

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>Observaciones

Un uso común de este puntero es transmitir información adicional sobre el proceso de serialización a todos los objetos que se serializan. Esto se logra inicializando el puntero con `CDocument`el documento (una clase derivada) que se está serializando, de tal manera que los objetos dentro del documento pueden tener acceso al documento si es necesario. Este puntero también `COleClientItem` se utiliza para los objetos durante la serialización.

El marco de trabajo establece *m_pDocument* en el documento que se serializa cuando un usuario emite un comando Abrir archivo o Guardar. Si serializa un documento contenedor de vinculación e incrustación de objetos (OLE) por motivos distintos de Abrir archivo o Guardar, debe establecer explícitamente *m_pDocument*. Por ejemplo, lo haría al serializar un documento contenedor en el Portapapeles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

## <a name="carchiveoperator-ltlt"></a><a name="operator_lt_lt"></a>CArchive::operador&lt;&lt;

Almacena el objeto indicado o el tipo primitivo en el archivo.

```
friend CArchive& operator<<(
    CArchive& ar,
    const CObject* pOb);

throw(
    CArchiveException*,
    CFileException*);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    const RECT& rect);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    POINT point);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    SIZE size);

template<typename BaseType,
    class StringTraits> CArchive& operator<<(
    const ATL::CStringT<BaseType,
    StringTraits>& str);

CArchive& operator<<(BYTE by);
CArchive& operator<<(WORD w);
CArchive& operator<<(LONG l);
CArchive& operator<<(DWORD dw);
CArchive& operator<<(float f);
CArchive& operator<<(double d);
CArchive& operator<<(int i);
CArchive& operator<<(short w);
CArchive& operator<<(char ch);
CArchive& operator<<(wchar_t ch);
CArchive& operator<<(unsigned u);
CArchive& operator<<(bool b);
CArchive& operator<<(ULONGLONG dwdw);
CArchive& operator<<(LONGLONG dwdw);
```

### <a name="return-value"></a>Valor devuelto

Una `CArchive` referencia que habilita varios operadores de inserción en una sola línea.

### <a name="remarks"></a>Observaciones

Las dos últimas versiones anteriores son específicamente para almacenar enteros de 64 bits.

Si usó la macro IMPLEMENT_SERIAL en la implementación de `CObject` la `WriteObject`clase, el operador de inserción sobrecargado para las llamadas a la protección . Esta función, a `Serialize` su vez, llama a la función de la clase.

El operador de inserción [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) (<<) admite el volcado de diagnóstico y el almacenamiento en un archivo.

### <a name="example"></a>Ejemplo

En este ejemplo se `CArchive` muestra el uso del operador de inserción << con los tipos **int** y **long.**

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>Ejemplo

En este ejemplo 2 se `CArchive` muestra el `CStringT` uso del operador de inserción << con el tipo.

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

## <a name="carchiveoperator-gtgt"></a><a name="operator_gt_gt"></a>CArchive::operador&gt;&gt;

Carga el objeto indicado o el tipo primitivo del archivo.

```
friend CArchive& operator>>(
    CArchive& ar,
    CObject *& pOb);

throw(
    CArchiveException*,
    CFileException*,
    CMemoryException*);

friend CArchive& operator>>(
    CArchive& ar,
    const CObject *& pOb);

throw(
    CArchiveException*,
    CFileException*,
    CMemoryException*);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    const RECT& rect);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    POINT point);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    SIZE size);

template<typename BaseType,
    class StringTraits> CArchive& operator>>(
    ATL::CStringT<BaseType,
    StringTraits>& str);

CArchive& operator>>(BYTE& by);
CArchive& operator>>(WORD& w);
CArchive& operator>>(int& i);
CArchive& operator>>(LONG& l);
CArchive& operator>>(DWORD& dw);
CArchive& operator>>(float& f);
CArchive& operator>>(double& d);
CArchive& operator>>(short& w);
CArchive& operator>>(char& ch);
CArchive& operator>>(wchar_t& ch);
CArchive& operator>>(unsigned& u);
CArchive& operator>>(bool& b);
CArchive& operator>>(ULONGLONG& dwdw);
CArchive& operator>>(LONGLONG& dwdw);
```

### <a name="return-value"></a>Valor devuelto

Una `CArchive` referencia que habilita varios operadores de extracción en una sola línea.

### <a name="remarks"></a>Observaciones

Las dos últimas versiones anteriores son específicamente para cargar enteros de 64 bits.

Si usó la macro IMPLEMENT_SERIAL en la implementación de `CObject` la `ReadObject` clase, los operadores de extracción sobrecargados para llamar a la función protegida (con un puntero de clase en tiempo de ejecución distinto de cero). Esta función, a `Serialize` su vez, llama a la función de la clase.

El operador de extracción [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) (>>) admite la carga desde un archivo.

### <a name="example"></a>Ejemplo

En este ejemplo se `CArchive` muestra el uso del operador de extracción >> con el tipo **int.**

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>Ejemplo

En este ejemplo se `CArchive` muestra el uso \< de los `CStringT` operadores de inserción y extracción <y >> con el tipo.

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

## <a name="carchiveread"></a><a name="read"></a>CArchive::Leer

Lee un número especificado de bytes del archivo.

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Puntero a un búfer proporcionado por el usuario que va a recibir los datos leídos del archivo.

*nMax*<br/>
Entero sin signo que especifica el número de bytes que se leerán del archivo.

### <a name="return-value"></a>Valor devuelto

Entero sin signo que contiene el número de bytes realmente leídos. Si el valor devuelto es menor que el número solicitado, se ha alcanzado el final del archivo. No se produce ninguna excepción en la condición de fin de archivo.

### <a name="remarks"></a>Observaciones

El archivo no interpreta los bytes.

Puede utilizar `Read` la función `Serialize` miembro dentro de la función para leer las estructuras ordinarias contenidas en los objetos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

## <a name="carchivereadclass"></a><a name="readclass"></a>CArchive::ReadClass

Llame a esta función miembro para leer una referencia a una clase almacenada anteriormente con [WriteClass](#writeclass).

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>Parámetros

*pClassRefRequested*<br/>
Puntero a la [estructura CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) que corresponde a la referencia de clase solicitada. Puede ser NULL.

*pSchema*<br/>
Puntero a un esquema de la clase en tiempo de ejecución almacenada anteriormente.

*pObTag*<br/>
Número que hace referencia a la etiqueta única de un objeto. Utilizado internamente por la implementación de [ReadObject](#readobject). Expuesto solo para programación avanzada; *pObTag* normalmente debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) estructura.

### <a name="remarks"></a>Observaciones

Si *pClassRefRequested* no `ReadClass` es NULL, comprueba que la información de clase archivada es compatible con la clase en tiempo de ejecución. Si no es `ReadClass` compatible, se producirá una [excepción CArchiveException](../../mfc/reference/carchiveexception-class.md).

La clase en tiempo de ejecución debe usar [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL;](../../mfc/reference/run-time-object-model-services.md#implement_serial) de `ReadClass` lo contrario, producirá una [excepción CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Si *pSchema* es NULL, el esquema de la clase almacenada se puede recuperar llamando a [CArchive::GetObjectSchema](#getobjectschema); de <strong>\*</strong>lo contrario, *pSchema* contendrá el esquema de la clase en tiempo de ejecución que se almacenó anteriormente.

Puede usar [SerializeClass](#serializeclass) `ReadClass`en lugar de , que controla la lectura y escritura de la referencia de clase.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CArchive::WriteClass](#writeclass).

## <a name="carchivereadobject"></a><a name="readobject"></a>CArchive::ReadObject

Lee los datos de objeto del archivo y construye un objeto del tipo adecuado.

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>Parámetros

*pClass*<br/>
Puntero constante a la [estructura CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) que corresponde al objeto que espera leer.

### <a name="return-value"></a>Valor devuelto

Puntero [CObject](../../mfc/reference/cobject-class.md) que se debe convertir de forma segura a la clase derivada correcta mediante [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof).

### <a name="remarks"></a>Observaciones

Normalmente, el `CArchive` operador de **>>** extracción ( ) sobrecarga para un puntero [CObject](../../mfc/reference/cobject-class.md) llama a esta función. `ReadObject`, a su `Serialize` vez, llama a la función de la clase archivada.

Si proporciona un parámetro *pClass* distinto de cero, que se obtiene mediante la macro [RUNTIME_CLASS,](../../mfc/reference/run-time-object-model-services.md#runtime_class) la función comprueba la clase en tiempo de ejecución del objeto archivado. Esto supone que ha utilizado la macro IMPLEMENT_SERIAL en la implementación de la clase.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CArchive::WriteObject](#writeobject).

## <a name="carchivereadstring"></a><a name="readstring"></a>CArchive::ReadString

Llame a esta función miembro para leer datos `CArchive` de texto en un búfer desde el archivo asociado con el objeto.

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>Parámetros

*rString*<br/>
Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contendrá la cadena resultante después de leerlo desde el archivo asociado con el CArchive objeto.

*lpsz*<br/>
Especifica un puntero a un búfer proporcionado por el usuario que recibirá una cadena de texto terminada en null.

*nMax*<br/>
Especifica el número máximo de caracteres que se leerá. Debe ser uno menos que el tamaño del búfer *lpsz.*

### <a name="return-value"></a>Valor devuelto

En la versión que devuelve BOOL, TRUE si se realiza correctamente; FALSE en caso contrario.

En la versión `LPTSTR`que devuelve un , un puntero al búfer que contiene los datos de texto; NULL si se alcanzó el final del archivo.

### <a name="remarks"></a>Observaciones

En la versión de la función miembro con el *nMax* parámetro, el búfer contendrá hasta un límite de *nMax* - 1 caracteres. La lectura se detiene mediante un par de avance de línea de retorno de carro. Los personajes finales de la nueva línea siempre se eliminan. En cualquier caso, se añade un carácter nulo ('-0').

[CArchive::Read](#read) también está disponible para la entrada en modo de texto, pero no termina en un par de avance de línea de retorno de carro.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CArchive::WriteString](#writestring).

## <a name="carchiveserializeclass"></a><a name="serializeclass"></a>CArchive::SerializeClass

Llame a esta función miembro cuando desee almacenar y cargar la información de versión de una clase base.

```cpp
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parámetros

*pClassRef*<br/>
Puntero a un objeto de clase en tiempo de ejecución para la clase base.

### <a name="remarks"></a>Observaciones

`SerializeClass`lee o escribe la referencia a `CArchive` una clase en el objeto, dependiendo de la dirección del `CArchive`archivo . Usar `SerializeClass` en lugar de [ReadClass](#readclass) y [WriteClass](#writeclass) como una manera conveniente de serializar objetos de clase base; `SerializeClass` requiere menos código y menos parámetros.

Like `ReadClass` `SerializeClass` , comprueba que la información de clase archivada es compatible con la clase en tiempo de ejecución. Si no es `SerializeClass` compatible, se producirá una [excepción CArchiveException](../../mfc/reference/carchiveexception-class.md).

La clase en tiempo de ejecución debe usar [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL;](../../mfc/reference/run-time-object-model-services.md#implement_serial) de `SerializeClass` lo contrario, producirá una [excepción CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Utilice la macro [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) para recuperar el valor del parámetro *pRuntimeClass.* La clase base debe haber utilizado la [macro IMPLEMENT_SERIAL.](../../mfc/reference/run-time-object-model-services.md#implement_serial)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

## <a name="carchivesetloadparams"></a><a name="setloadparams"></a>CArchive::SetLoadParams

Llame `SetLoadParams` cuando vaya a leer un `CObject`gran número de objetos derivados de un archivo.

```cpp
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>Parámetros

*nGrowBy*<br/>
El número mínimo de ranuras de elementos que se asignarán si es necesario un aumento de tamaño.

### <a name="remarks"></a>Observaciones

`CArchive`utiliza una matriz de carga para resolver referencias a objetos almacenados en el archivo. `SetLoadParams`le permite establecer el tamaño al que crece la matriz de carga.

No debe `SetLoadParams` llamar después de cargar ningún objeto, o después de [MapObject](#mapobject) o [ReadObject](#readobject) se llama.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivesetobjectschema"></a><a name="setobjectschema"></a>CArchive::SetObjectSchema

Llame a esta función miembro para establecer el esquema de objeto almacenado en el objeto de archivo en *nSchema*.

```cpp
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>Parámetros

*nSchema*<br/>
Especifica el esquema del objeto.

### <a name="remarks"></a>Observaciones

La siguiente llamada a [GetObjectSchema](#getobjectschema) devolverá el valor almacenado en *nSchema*.

Uso `SetObjectSchema` para el control de versiones avanzado; por ejemplo, cuando desea forzar una versión `Serialize` determinada para que se lea en una función de una clase derivada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

## <a name="carchivesetstoreparams"></a><a name="setstoreparams"></a>CArchive::SetStoreParams

Se `SetStoreParams` utiliza al almacenar `CObject`un gran número de objetos derivados en un archivo.

```cpp
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>Parámetros

*nHashSize*<br/>
El tamaño de la tabla hash para los mapas de puntero de interfaz. Debe ser un número primo.

*nBlockSize*<br/>
Especifica la granularidad de asignación de memoria para extender los parámetros. Debe ser una potencia de 2 para el mejor rendimiento.

### <a name="remarks"></a>Observaciones

`SetStoreParams`le permite establecer el tamaño de la tabla hash y el tamaño de bloque del mapa utilizado para identificar objetos únicos durante el proceso de serialización.

No debe `SetStoreParams` llamar después de almacenar ningún objeto, o después [de MapObject](#mapobject) o [WriteObject](#writeobject) se llama.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivewrite"></a><a name="write"></a>CArchive::Escribir

Escribe un número especificado de bytes en el archivo.

```cpp
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Puntero a un búfer proporcionado por el usuario que contiene los datos que se van a escribir en el archivo.

*nMax*<br/>
Entero que especifica el número de bytes que se escribirán en el archivo.

### <a name="remarks"></a>Observaciones

El archivo no da formato a los bytes.

Puede utilizar `Write` la función `Serialize` miembro dentro de la función para escribir estructuras normales que se encuentran en los objetos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

## <a name="carchivewriteclass"></a><a name="writeclass"></a>CArchive::WriteClass

Se `WriteClass` utiliza para almacenar la información de versión y clase de una clase base durante la serialización de la clase derivada.

```cpp
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parámetros

*pClassRef*<br/>
Puntero a la [estructura CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) que corresponde a la referencia de clase solicitada.

### <a name="remarks"></a>Observaciones

`WriteClass`escribe una referencia a [la CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) para `CArchive`la clase base en el archivo . Utilice [CArchive::ReadClass](#readclass) para recuperar la referencia.

`WriteClass`comprueba que la información de clase archivada es compatible con la clase en tiempo de ejecución. Si no es `WriteClass` compatible, se producirá una [excepción CArchiveException](../../mfc/reference/carchiveexception-class.md).

La clase en tiempo de ejecución debe usar [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL;](../../mfc/reference/run-time-object-model-services.md#implement_serial) de `WriteClass` lo contrario, producirá una [excepción CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Puede usar [SerializeClass](#serializeclass) `WriteClass`en lugar de , que controla la lectura y escritura de la referencia de clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

## <a name="carchivewriteobject"></a><a name="writeobject"></a>CArchive::WriteObject

Almacena el `CObject` especificado en el archivo.

```cpp
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>Parámetros

*Pob*<br/>
Puntero constante al objeto que se va a almacenar.

### <a name="remarks"></a>Observaciones

Normalmente, el `CArchive` operador de **<<** inserción `CObject`( ) sobrecarga para . `WriteObject`, a su `Serialize` vez, llama a la función de la clase archivada.

Debe utilizar la macro IMPLEMENT_SERIAL para habilitar el archivado. `WriteObject`escribe el nombre de clase ASCII en el archivo. Este nombre de clase se valida más adelante durante el proceso de carga. Un esquema de codificación especial evita la duplicación innecesaria del nombre de clase para varios objetos de la clase. Este esquema también impide el almacenamiento redundante de objetos que son destinos de más de un puntero.

El método de codificación de objetos exacto (incluida la presencia del nombre de clase ASCII) es un detalle de implementación y podría cambiar en versiones futuras de la biblioteca.

> [!NOTE]
> Termine de crear, eliminar y actualizar todos los objetos antes de empezar a archivarlos. El archivo se dañará si mezcla el archivado con la modificación de objetos.

### <a name="example"></a>Ejemplo

Para obtener una `CAge`definición de la clase , vea el ejemplo de [CObList::CObList](../../mfc/reference/coblist-class.md#coblist).

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

## <a name="carchivewritestring"></a><a name="writestring"></a>CArchive::WriteString

Utilice esta función miembro para escribir datos de `CArchive` un búfer en el archivo asociado al objeto.

```cpp
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parámetros

*lpsz*<br/>
Especifica un puntero a un búfer que contiene una cadena de texto terminada en null.

### <a name="remarks"></a>Observaciones

El carácter nulo de terminación ('-0') no se escribe en el archivo; tampoco se escribe automáticamente una nueva línea.

`WriteString`produce una excepción en respuesta a varias condiciones, incluida la condición de disco completo.

`Write`también está disponible, pero en lugar de terminar en un carácter nulo, escribe el número solicitado de bytes en el archivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFile (clase)](../../mfc/reference/cfile-class.md)<br/>
[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[CSocket (clase)](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile (clase)](../../mfc/reference/csocketfile-class.md)
