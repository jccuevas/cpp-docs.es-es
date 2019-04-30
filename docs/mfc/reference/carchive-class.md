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
ms.openlocfilehash: 8f169964c6a313f37b5ea50a5105af29af7b59b1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391327"
---
# <a name="carchive-class"></a>CArchive (clase)

Permite guardar una red compleja de objetos en un formato binario permanente (normalmente almacenamiento en disco) que se conserva después de que se eliminen esos objetos.

## <a name="syntax"></a>Sintaxis

```
class CArchive
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CArchive::CArchive](#carchive)|Crea un objeto `CArchive`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CArchive::Abort](#abort)|Cierra un archivo sin producir una excepción.|
|[CArchive::Close](#close)|Vacía los datos no escritos y desconecta el `CFile`.|
|[CArchive::Flush](#flush)|Vacía los datos no escritos del búfer de archivo.|
|[CArchive::GetFile](#getfile)|Obtiene el `CFile` puntero de objeto para este archivo.|
|[CArchive::GetObjectSchema](#getobjectschema)|Se llama desde el `Serialize` función para determinar la versión del objeto que se va a deserializar.|
|[CArchive::IsBufferEmpty](#isbufferempty)|Determina si el búfer se ha vaciado una Sockets de Windows durante el proceso de recepción.|
|[CArchive::IsLoading](#isloading)|Determina si se está cargando el archivo.|
|[CArchive::IsStoring](#isstoring)|Determina si está almacenando el archivo.|
|[CArchive::MapObject](#mapobject)|Coloca los objetos en el mapa que no se serializan en el archivo, pero que están disponibles para los objetos secundarios para hacer referencia a.|
|[CArchive::Read](#read)|Lee los bytes sin formato.|
|[CArchive::ReadClass](#readclass)|Lecturas previamente almacena una referencia de clase con `WriteClass`.|
|[CArchive::ReadObject](#readobject)|Llama a un objeto `Serialize` función para la carga.|
|[CArchive::ReadString](#readstring)|Lee una sola línea de texto.|
|[CArchive::SerializeClass](#serializeclass)|Lee o escribe la referencia de clase a la `CArchive` objeto según la dirección de la `CArchive`.|
|[CArchive::SetLoadParams](#setloadparams)|Establece el tamaño a la que crece la carga de matriz. Debe llamarse antes de carga cualquier objeto o antes de `MapObject` o `ReadObject` se llama.|
|[CArchive::SetObjectSchema](#setobjectschema)|Establece el esquema de objeto almacenado en el objeto de archivo.|
|[CArchive::SetStoreParams](#setstoreparams)|Establece el tamaño de la tabla hash y el tamaño del bloque de la asignación que se usa para identificar objetos únicos durante el proceso de serialización.|
|[CArchive::Write](#write)|Escribe los bytes sin formato.|
|[CArchive::WriteClass](#writeclass)|Escribe una referencia a la `CRuntimeClass` a la `CArchive`.|
|[CArchive::WriteObject](#writeobject)|Llama a un objeto `Serialize` función para almacenar.|
|[CArchive::WriteString](#writestring)|Escribe una sola línea de texto.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CArchive::operator &lt;&lt;](#operator_lt_lt)|Almacena los objetos y tipos primitivos al archivo.|
|[CArchive::operator &gt;&gt;](#operator_gt_gt)|Carga los tipos primitivos y los objetos desde el archivo.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CArchive::m_pDocument](#m_pdocument)||

## <a name="remarks"></a>Comentarios

`CArchive` no tiene una clase base.

Más adelante puede cargar los objetos desde el almacenamiento persistente, reconstituirlos en memoria. Este proceso de hacer persistentes los datos se denomina "serialización".

Se puede considerar un objeto de almacenamiento como un tipo de secuencia binaria. Como un flujo de entrada/salida, un archivo está asociado a un archivo y permite la escritura almacenada en búfer y lectura de datos hacia y desde el almacenamiento. Un flujo de entrada/salida procesa secuencias de caracteres ASCII, pero un archivo procesa los datos de objeto binario en un formato no redundante y eficaz.

Debe crear un [CFile](../../mfc/reference/cfile-class.md) objeto antes de poder crear un `CArchive` objeto. Además, debe asegurarse de que el estado de carga o almacenamiento del archivo es compatible con el modo del archivo abierto. Está limitado a un archivo activo por cada archivo.

Cuando se construye un `CArchive` objeto, se adjunta a un objeto de clase `CFile` (o una clase derivada) que representa un archivo abierto. También especifica si se utilizará para cargar o almacenar el archivo. Un `CArchive` puede procesar el objeto no solo los tipos primitivos, sino también los objetos de [CObject](../../mfc/reference/cobject-class.md)-diseñadas para la serialización de clases derivadas. Una clase serializable normalmente tiene un `Serialize` función miembro y se utiliza normalmente el [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) macros, como se describe en la clase `CObject`.

La extracción sobrecargada ( **>>**) y la inserción ( **<<**) operadores son interfaces de programación de archive cómodo que admiten ambos tipos primitivos y `CObject` -las clases derivadas.

`CArchive` también admite la programación con las clases MFC de Windows Sockets [CSocket](../../mfc/reference/csocket-class.md) y [CSocketFile](../../mfc/reference/csocketfile-class.md). El [IsBufferEmpty](#isbufferempty) admite que el uso de la función miembro.

Para obtener más información sobre `CArchive`, consulte los artículos [serialización](../../mfc/serialization-in-mfc.md) y [Windows Sockets: Usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CArchive`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="abort"></a>  CArchive::Abort

Llame a esta función para cerrar el archivo sin producir una excepción.

```
void Abort ();
```

### <a name="remarks"></a>Comentarios

El `CArchive` destructor llamará normalmente `Close`, lo que hará que vacíe cualquier dato que no se ha guardado asociado `CFile` objeto. Esto puede producir excepciones.

Al detectar estas excepciones, es una buena idea usar `Abort`, de modo que destruir la `CArchive` objeto no generarán más excepciones. Cuando el control de excepciones, `CArchive::Abort` no se iniciará una excepción en errores porque, a diferencia [CArchive::Close](#close), `Abort` omite los errores.

Si ha usado **nueva** para asignar el `CArchive` objeto en el montón, a continuación, debe eliminar después de cerrar el archivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CArchive::WriteClass](#writeclass).

##  <a name="carchive"></a>  CArchive::CArchive

Construye un `CArchive` de objeto y especifica si se utilizará para cargar o almacenar los objetos.

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>Parámetros

*pFile*<br/>
Un puntero a la `CFile` objeto que es el último origen o destino de los datos persistentes.

*nMode*<br/>
Una marca que especifica si los objetos se cargan desde o almacenados en el archivo. El *nMode* parámetro debe tener uno de los siguientes valores:

- `CArchive::load` Carga los datos del archivo. Sólo requiere `CFile` permiso de lectura.

- `CArchive::store` Guarda los datos en el archivo. Requiere `CFile` permiso de escritura.

- `CArchive::bNoFlushOnDelete` Impide que el archivo automáticamente una llamada a `Flush` cuando se llama al destructor del archivo. Si establece esta marca, usted es responsable de llamar explícitamente a `Close` antes de que se llama al destructor. Si no lo hace, se dañarán los datos.

*nBufSize*<br/>
Un entero que especifica el tamaño del búfer interno del archivo, en bytes. Tenga en cuenta que el tamaño de búfer predeterminado es de 4.096 bytes. Si archiva periódicamente objetos grandes, se mejorará el rendimiento si usa un tamaño de búfer que es un múltiplo del tamaño del búfer de archivo.

*lpBuf*<br/>
Un puntero a un búfer proporcionado por el usuario de tamaño opcional *nBufSize*. Si no especifica este parámetro, el archivo asigna un búfer desde el montón local y libera cuando se destruye el objeto. El archivo no liberar un búfer proporcionado por el usuario.

### <a name="remarks"></a>Comentarios

No se puede cambiar esta especificación después de haber creado el archivo.

No se puede usar `CFile` operaciones para modificar el estado del archivo hasta que haya cerrado el archivo. Cualquier operación de este tipo puede dañar la integridad del archivo. Puede tener acceso a la posición del puntero de archivo en cualquier momento durante la serialización mediante la obtención del objeto de archivo del archivo desde el [GetFile](#getfile) función miembro y, a continuación, usar el [CFile::GetPosition](../../mfc/reference/cfile-class.md#getposition) (función) . Debe llamar a [CArchive::Flush](#flush) antes de obtener la posición del puntero del archivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

##  <a name="close"></a>  CArchive::Close

Vacía los datos permanecen en el búfer, se cierra el archivo y se desconecta el archivo desde el archivo.

```
void Close();
```

### <a name="remarks"></a>Comentarios

No se permite ninguna otra operación en el archivo. Después de cerrar un archivo, puede crear otro archivo para el mismo archivo o puede cerrar el archivo.

La función miembro `Close` garantiza que todos los datos se transfieren desde el archivo en el archivo y hace que el archivo que no está disponible. Para completar la transferencia del archivo en el medio de almacenamiento, primero debe usar [CFile::Close](../../mfc/reference/cfile-class.md#close) y, a continuación, destruya el `CFile` objeto.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CArchive::WriteString](#writestring).

##  <a name="flush"></a>  CArchive::Flush

Obliga a los datos permanecen en el búfer de archivo que se escriban en el archivo.

```
void Flush();
```

### <a name="remarks"></a>Comentarios

La función miembro `Flush` garantiza que todos los datos se transfieren desde el archivo en el archivo. Debe llamar a [CFile::Close](../../mfc/reference/cfile-class.md#close) para completar la transferencia del archivo en el medio de almacenamiento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

##  <a name="getfile"></a>  CArchive::GetFile

Obtiene el `CFile` puntero de objeto para este archivo.

```
CFile* GetFile() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero constante a la `CFile` objeto en uso.

### <a name="remarks"></a>Comentarios

Debe vaciar el archivo antes de usar `GetFile`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

##  <a name="getobjectschema"></a>  CArchive::GetObjectSchema

Llame a esta función desde el `Serialize` función para determinar la versión del objeto que se está deserializando.

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>Valor devuelto

Durante la deserialización, la versión del objeto que se va a leer.

### <a name="remarks"></a>Comentarios

Llamar a esta función solo es válida cuando la `CArchive` se está cargando el objeto ( [CArchive::IsLoading](#isloading) devuelve distinto de cero). Debe ser la primera llamada en el `Serialize` función y llamada solo una vez. Un valor devuelto de -1 (UINT) indica que el número de versión es desconocido.

Un `CObject`-clase derivada puede usar VERSIONABLE_SCHEMA combinado (bit a bit con **o**) con la versión de esquema (en la macro IMPLEMENT_SERIAL) para crear un "objeto versionable", es decir, un objeto cuyo `Serialize` función miembro puede leer varias versiones. La funcionalidad del marco predeterminado (sin VERSIONABLE_SCHEMA) es producir una excepción si la versión es no coincide.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

##  <a name="isbufferempty"></a>  CArchive::IsBufferEmpty

Llame a esta función miembro para determinar si el búfer interno del objeto de archivo está vacío.

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el búfer del archivo está vacío; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función se proporciona para admitir la programación con la clase MFC de Windows Sockets `CSocketFile`. No es necesario usarlo para que un archivo asociado con un `CFile` objeto.

La razón para usar `IsBufferEmpty` con un archivo asociado con un `CSocketFile` objeto es que el búfer del archivo puede contener más de un mensaje o registro. Después de recibir un mensaje, debe usar `IsBufferEmpty` para controlar un bucle que continúa recibiendo datos hasta que el búfer está vacío. Para obtener más información, consulte el [recepción](../../mfc/reference/casyncsocket-class.md#receive) función miembro de clase `CAsyncSocket`, que muestra cómo usar `IsBufferEmpty`.

Para obtener más información, consulte [Windows Sockets: Usar Sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="isloading"></a>  CArchive::IsLoading

Determina si el archivo se está cargando datos.

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el archivo se está usando actualmente para la carga; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función miembro llama a la `Serialize` las funciones de las clases de archivado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

##  <a name="isstoring"></a>  CArchive::IsStoring

Determina si el archivo está almacenando datos.

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el archivo se está usando actualmente para almacenar; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función miembro llama a la `Serialize` las funciones de las clases de archivado.

Si el `IsStoring` estado de un archivo es distinto de cero, entonces su `IsLoading` status es 0 y viceversa.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

##  <a name="mapobject"></a>  CArchive::MapObject

Llame a esta función miembro para colocar en el mapa que no se serializan realmente en el archivo, pero que están disponibles para los objetos secundarios para hacer referencia a los objetos.

```
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>Parámetros

*pOb*<br/>
Un puntero constante para el objeto que se almacena.

### <a name="remarks"></a>Comentarios

Por ejemplo, no se puede serializar un documento, pero podría serializar los artículos que forman parte del documento. Mediante una llamada a `MapObject`, permite que los elementos o subobjetos, para hacer referencia al documento. Además, pueden serializar subelementos serializados sus *m_pDocument* puntero trasero.

Puede llamar a `MapObject` al almacenar y cargar desde el `CArchive` objeto. `MapObject` Agrega el objeto especificado a las estructuras de datos interna mantenidas por el `CArchive` objeto durante la serialización y deserialización, pero a diferencia de [ReadObject](#readobject) y [WriteObject](#writeobject), no se ejecuta serializar en el objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

##  <a name="m_pdocument"></a>  CArchive::m_pDocument

Establecer en NULL de forma predeterminada, este puntero en un `CDocument` se puede establecer en nada al usuario de la `CArchive` el departamento de la instancia.

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>Comentarios

Un uso común de este puntero es transmitir información adicional sobre el proceso de serialización para todos los objetos que se está serializando. Esto se logra al inicializar el puntero con el documento (un `CDocument`-clase derivada) que se está serializando, de tal forma que los objetos dentro del documento pueden tener acceso al documento si es necesario. También usa este puntero `COleClientItem` objetos durante la serialización.

Los conjuntos de framework *m_pDocument* al documento que se está serializando cuando un usuario emite un archivo, abrir o guardar comandos. Si se serializa un documento del contenedor de objeto vinculación e incrustación de objetos (OLE) por motivos distintos a abrir archivo o guardar, debe establecer explícitamente *m_pDocument*. Por ejemplo, podría hacer esto al serializar un documento de contenedor en el Portapapeles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

##  <a name="operator_lt_lt"></a>  CArchive::operator &lt;&lt;

Almacena el objeto indicado o un tipo primitivo al archivo.

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

Un `CArchive` referencia que permite que varios operadores de inserción en una sola línea.

### <a name="remarks"></a>Comentarios

Las dos últimas versiones anteriores son específicamente para almacenar números enteros de 64 bits.

Si usa la macro IMPLEMENT_SERIAL en su implementación de la clase, el operador de inserción sobrecargado para `CObject` llama al método protegido `WriteObject`. Esta función, a su vez, llama a la `Serialize` función de la clase.

El [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) operador de inserción (<<) admite el volcado de diagnóstico y almacenar en un archivo.

### <a name="example"></a>Ejemplo

En este ejemplo se muestra el uso de la `CArchive` operador de inserción << con el **int** y **largo** tipos.

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>Ejemplo

En este ejemplo 2 muestra el uso de la `CArchive` operador de inserción << con el `CStringT` tipo.

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

##  <a name="operator_gt_gt"></a>  CArchive::operator &gt;&gt;

Carga el objeto indicado o tipo primitivo del archivo.

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

Un `CArchive` referencia que permite varios operadores de extracción en una sola línea.

### <a name="remarks"></a>Comentarios

Las dos últimas versiones anteriores están diseñadas específicamente para cargar los enteros de 64 bits.

Si usa la macro IMPLEMENT_SERIAL en su implementación de la clase, se sobrecargan los operadores de extracción para `CObject` llamar protegido `ReadObject` función (con un puntero de la clase de tiempo de ejecución distinto de cero). Esta función, a su vez, llama a la `Serialize` función de la clase.

El [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) operador de extracción (>>) admite la carga de un archivo.

### <a name="example"></a>Ejemplo

En este ejemplo se muestra el uso de la `CArchive` operador de extracción >> con el **int** tipo.

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>Ejemplo

En este ejemplo se muestra el uso de la `CArchive` operadores de inserción y extracción <\< y >> con el `CStringT` tipo.

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

##  <a name="read"></a>  CArchive::Read

Lee un número especificado de bytes del archivo.

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Un puntero a un búfer proporcionado por el usuario que va a recibir los datos leídos desde el archivo.

*nMax*<br/>
Un entero sin signo especifica el número de bytes para leerse desde el archivo.

### <a name="return-value"></a>Valor devuelto

Un entero sin signo que contiene el número de bytes leídos realmente. Si el valor devuelto es menor que el número solicitado, se alcanzó el final del archivo. Se produce ninguna excepción en la condición de final de archivo.

### <a name="remarks"></a>Comentarios

El archivo no interpreta los bytes.

Puede usar el `Read` función miembro dentro de su `Serialize` función para leer estructuras normales que se encuentran en los objetos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

##  <a name="readclass"></a>  CArchive::ReadClass

Llame a esta función miembro para leer una referencia a una clase almacenada previamente con [WriteClass](#writeclass).

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>Parámetros

*pClassRefRequested*<br/>
Un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) estructura que corresponde a la referencia de la clase solicitada. Puede ser NULL.

*pSchema*<br/>
Un puntero a un esquema de la clase de tiempo de ejecución almacenado previamente.

*pObTag*<br/>
Un número que hace referencia a la etiqueta de un objeto único. Utilizado internamente por la implementación de [ReadObject](#readobject). Expuestas para programación avanzada solo; *pObTag* normalmente debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) estructura.

### <a name="remarks"></a>Comentarios

Si *pClassRefRequested* no es NULL, `ReadClass` comprueba que la información de la clase archivada es compatible con la clase en tiempo de ejecución. Si no es compatible, `ReadClass` producirá un [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Debe usar la clase en tiempo de ejecución [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); en caso contrario, `ReadClass` producirá un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Si *pSchema* es NULL, se puede recuperar el esquema de la clase almacenado mediante una llamada a [CArchive::GetObjectSchema](#getobjectschema); en caso contrario, <strong>\*</strong>  *pSchema* contendrá el esquema de la clase de tiempo de ejecución que se almacenó anteriormente.

Puede usar [SerializeClass](#serializeclass) en lugar de `ReadClass`, que controla la lectura y escritura de la referencia de clase.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CArchive::WriteClass](#writeclass).

##  <a name="readobject"></a>  CArchive::ReadObject

Lee datos de objetos desde el archivo y crea un objeto del tipo adecuado.

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>Parámetros

*pClass*<br/>
Un puntero constante a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) estructura que se corresponde con el objeto que esperen leer.

### <a name="return-value"></a>Valor devuelto

Un [CObject](../../mfc/reference/cobject-class.md) puntero que se debe convertir con seguridad en el valor correcto de clase derivada mediante el uso de [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof).

### <a name="remarks"></a>Comentarios

Esta función normalmente se llama el `CArchive` extracción ( **>>**) operador sobrecargado para un [CObject](../../mfc/reference/cobject-class.md) puntero. `ReadObject`, a su vez, llama a la `Serialize` función de la clase archivada.

Si proporciona un distinto de cero *pClass* parámetro, que se obtiene mediante la [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) macro y, a continuación, la función comprueba la clase de tiempo de ejecución del objeto archivado. Se supone que ha usado la macro IMPLEMENT_SERIAL en la implementación de la clase.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CArchive::WriteObject](#writeobject).

##  <a name="readstring"></a>  CArchive::ReadString

Llame a esta función miembro para leer datos de texto en un búfer desde el archivo asociado con el `CArchive` objeto.

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>Parámetros

*rString*<br/>
Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contendrá la cadena resultante después de leerlo desde el archivo asociado al objeto CArchive.

*lpsz*<br/>
Especifica un puntero a un búfer proporcionado por el usuario que va a recibir una cadena de texto terminada en null.

*nMax*<br/>
Especifica el número máximo de caracteres que se va a leer. Debe ser uno menor que el tamaño de la *lpsz* búfer.

### <a name="return-value"></a>Valor devuelto

En la versión que devuelve TRUE si es correcto; BOOL, FALSE en caso contrario.

En la versión que devuelve un `LPTSTR`, un puntero al búfer que contiene los datos de texto; Es NULL si se ha alcanzado el final del archivo.

### <a name="remarks"></a>Comentarios

En la versión de la función miembro con el *Nmáx* parámetro, el búfer contendrá a un límite de *Nmáx* - 1 caracteres. Lectura se detiene por un par de retorno de carro. Siempre se quitan los caracteres de nueva línea al final. En cualquier caso, se anexa un carácter nulo ('\0').

[CArchive::Read](#read) también está disponible para su entrada de modo de texto, pero no termina en un par de retorno de carro.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CArchive::WriteString](#writestring).

##  <a name="serializeclass"></a>  CArchive::SerializeClass

Llame a esta función miembro cuando desee almacenar y cargar la información de versión de una clase base.

```
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parámetros

*pClassRef*<br/>
Un puntero a un objeto de clase de tiempo de ejecución de la clase base.

### <a name="remarks"></a>Comentarios

`SerializeClass` lee o escribe la referencia a una clase para el `CArchive` objeto, dependiendo de la dirección del `CArchive`. Use `SerializeClass` en lugar de [ReadClass](#readclass) y [WriteClass](#writeclass) como una manera cómoda para serializar los objetos de clase base; `SerializeClass` requiere menos código y menos parámetros.

Al igual que `ReadClass`, `SerializeClass` comprueba que la información de la clase archivada es compatible con la clase en tiempo de ejecución. Si no es compatible, `SerializeClass` producirá un [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Debe usar la clase en tiempo de ejecución [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); en caso contrario, `SerializeClass` producirá un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Use la [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) macro para recuperar el valor para el *pRuntimeClass* parámetro. La clase base debe haber usado el [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) macro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

##  <a name="setloadparams"></a>  CArchive::SetLoadParams

Llame a `SetLoadParams` cuando va a leer un gran número de `CObject`-objetos derivados de un archivo.

```
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>Parámetros

*nGrowBy*<br/>
El número mínimo de ranuras de elemento para asignar si es necesario un aumento de tamaño.

### <a name="remarks"></a>Comentarios

`CArchive` utiliza una matriz de carga para resolver las referencias a objetos almacenados en el archivo. `SetLoadParams` permite establecer el tamaño a la que crece la carga de matriz.

No se debe llamar a `SetLoadParams` después de cargar cualquier objeto, o después de [MapObject](#mapobject) o [ReadObject](#readobject) se llama.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="setobjectschema"></a>  CArchive::SetObjectSchema

Llame a esta función miembro para establecer el esquema de objeto almacenado en el objeto de archivo a *nSchema*.

```
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>Parámetros

*nSchema*<br/>
Especifica el esquema del objeto.

### <a name="remarks"></a>Comentarios

La siguiente llamada a [GetObjectSchema](#getobjectschema) devolverá el valor almacenado en *nSchema*.

Use `SetObjectSchema` para controlar las versiones avanzadas; por ejemplo, cuando desee forzar una versión determinada se deben leer en un `Serialize` función de una clase derivada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

##  <a name="setstoreparams"></a>  CArchive::SetStoreParams

Use `SetStoreParams` al almacenar un gran número de `CObject`-derivados de los objetos en un archivo.

```
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>Parámetros

*nHashSize*<br/>
Asigna el tamaño de la tabla hash para el puntero de interfaz. Debe ser un número primo.

*nBlockSize*<br/>
Especifica la granularidad de asignación de memoria para extender los parámetros. Debe ser una potencia de 2 para optimizar el rendimiento.

### <a name="remarks"></a>Comentarios

`SetStoreParams` permite establecer el tamaño de la tabla hash y el tamaño del bloque de la asignación que se usa para identificar objetos únicos durante el proceso de serialización.

No se debe llamar a `SetStoreParams` se almacenan todos los objetos, o después de [MapObject](#mapobject) o [WriteObject](#writeobject) se llama.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="write"></a>  CArchive::Write

Escribe un número especificado de bytes en el archivo.

```
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Un puntero a un búfer proporcionado por el usuario que contiene los datos se escriban en el archivo.

*nMax*<br/>
Un entero que especifica el número de bytes que se escribirán en el archivo.

### <a name="remarks"></a>Comentarios

El archivo de formato no los bytes.

Puede usar el `Write` función miembro dentro de su `Serialize` función escribir normal de las estructuras que están contenidos en los objetos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

##  <a name="writeclass"></a>  CArchive::WriteClass

Use `WriteClass` para almacenar la información de versión y la clase de una clase base durante la serialización de la clase derivada.

```
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parámetros

*pClassRef*<br/>
Un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) estructura que corresponde a la referencia de la clase solicitada.

### <a name="remarks"></a>Comentarios

`WriteClass` escribe una referencia a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) de la clase base para el `CArchive`. Use [CArchive::ReadClass](#readclass) para recuperar la referencia.

`WriteClass` comprueba que la información de la clase archivada es compatible con la clase en tiempo de ejecución. Si no es compatible, `WriteClass` producirá un [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Debe usar la clase en tiempo de ejecución [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); en caso contrario, `WriteClass` producirá un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Puede usar [SerializeClass](#serializeclass) en lugar de `WriteClass`, que controla la lectura y escritura de la referencia de clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

##  <a name="writeobject"></a>  CArchive::WriteObject

Almacena especificado `CObject` al archivo.

```
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>Parámetros

*pOb*<br/>
Un puntero constante para el objeto que se almacena.

### <a name="remarks"></a>Comentarios

Esta función normalmente se llama el `CArchive` inserción ( **<<**) operador sobrecargado para `CObject`. `WriteObject`, a su vez, llama a la `Serialize` función de la clase archivada.

Debe utilizar la macro IMPLEMENT_SERIAL para habilitar el archivado. `WriteObject` Escribe el nombre de clase ASCII en el archivo. Este nombre de clase se valida posteriormente durante el proceso de carga. Un esquema de codificación especial evita la duplicación innecesaria de nombre de clase para varios objetos de la clase. Este esquema también impide que el almacenamiento con redundancia de los objetos que son destinos de más de un puntero.

El objeto exacto (incluida la presencia del nombre de clase ASCII) del método de codificación es un detalle de implementación y podría cambiar en futuras versiones de la biblioteca.

> [!NOTE]
>  Fin de crear, eliminar y actualizar todos los objetos antes de empezar a archivarlos. Si mezcla archivado con la modificación de objetos, se dañará el archivo.

### <a name="example"></a>Ejemplo

Para obtener una definición de la clase `CAge`, vea el ejemplo de [CObList::CObList](../../mfc/reference/coblist-class.md#coblist).

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

##  <a name="writestring"></a>  CArchive::WriteString

Utilice esta función miembro para escribir datos de un búfer en el archivo asociado con el `CArchive` objeto.

```
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parámetros

*lpsz*<br/>
Especifica un puntero a un búfer que contiene una cadena de texto terminada en null.

### <a name="remarks"></a>Comentarios

El carácter nulo ('\0') no se escribe en el archivo. tampoco es una nueva línea escribe automáticamente.

`WriteString` produce una excepción en respuesta a varias condiciones, incluidas la condición de disco lleno.

`Write` También está disponible, pero en lugar de terminar en un carácter nulo, escribe el número de bytes solicitado en el archivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFile (clase)](../../mfc/reference/cfile-class.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[CSocket (clase)](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile (clase)](../../mfc/reference/csocketfile-class.md)
