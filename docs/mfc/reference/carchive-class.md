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
ms.openlocfilehash: 3cf5c3b7a79e846928b5a7ee0af12a3324e141a3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855340"
---
# <a name="carchive-class"></a>CArchive (clase)

Permite guardar una red compleja de objetos en un formato binario permanente (normalmente almacenamiento en disco) que se conserva después de que se eliminen esos objetos.

## <a name="syntax"></a>Sintaxis

```
class CArchive
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CArchive:: CArchive](#carchive)|Crea un objeto `CArchive`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CArchive:: ABORT](#abort)|Cierra un archivo sin producir una excepción.|
|[CArchive:: Close](#close)|Vacía los datos sin escribir y desconecta del `CFile`.|
|[CArchive:: Flush](#flush)|Vacía los datos no escritos del búfer de archivo.|
|[CArchive:: GetFile](#getfile)|Obtiene el puntero de objeto `CFile` para este archivo.|
|[CArchive:: GetObjectSchema](#getobjectschema)|Se llama desde la función `Serialize` para determinar la versión del objeto que se está deserializando.|
|[CArchive:: IsBufferEmpty](#isbufferempty)|Determina si el búfer se ha vaciado durante un proceso de recepción de Windows Sockets.|
|[CArchive:: IsLoading](#isloading)|Determina si se está cargando el archivo.|
|[CArchive:: IsStoring](#isstoring)|Determina si el archivo está almacenando.|
|[CArchive:: MapObject](#mapobject)|Coloca los objetos en el mapa que no se serializan en el archivo, pero que están disponibles para que los subobjetos hagan referencia.|
|[CArchive:: Read](#read)|Lee los bytes sin formato.|
|[CArchive:: ReadClass](#readclass)|Lee una referencia de clase almacenada previamente con `WriteClass`.|
|[CArchive:: ReadObject](#readobject)|Llama a la función de `Serialize` de un objeto para cargar.|
|[CArchive:: ReadString](#readstring)|Lee una sola línea de texto.|
|[CArchive:: SerializeClass](#serializeclass)|Lee o escribe la referencia de clase en el objeto de `CArchive` en función de la dirección de la `CArchive`.|
|[CArchive:: SetLoadParams](#setloadparams)|Establece el tamaño con el que crece la matriz de carga. Se debe llamar a antes de que se cargue cualquier objeto o antes de que se llame a `MapObject` o `ReadObject`.|
|[CArchive:: SetObjectSchema](#setobjectschema)|Establece el esquema de objeto almacenado en el objeto de almacenamiento.|
|[CArchive:: SetStoreParams](#setstoreparams)|Establece el tamaño de la tabla hash y el tamaño de bloque de la asignación que se usa para identificar objetos únicos durante el proceso de serialización.|
|[CArchive:: Write](#write)|Escribe los bytes sin formato.|
|[CArchive:: WriteClass](#writeclass)|Escribe una referencia al `CRuntimeClass` en el `CArchive`.|
|[CArchive:: WriteObject](#writeobject)|Llama a la función de `Serialize` de un objeto para almacenar.|
|[CArchive:: WriteString](#writestring)|Escribe una sola línea de texto.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CArchive:: Operator &lt;&lt;](#operator_lt_lt)|Almacena objetos y tipos primitivos en el archivo.|
|[CArchive:: Operator &gt;&gt;](#operator_gt_gt)|Carga objetos y tipos primitivos del archivo.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CArchive:: m_pDocument](#m_pdocument)||

## <a name="remarks"></a>Observaciones

`CArchive` no tiene una clase base.

Más adelante, puede cargar los objetos desde almacenamiento persistente y reconstituirlos en la memoria. Este proceso de convertir los datos en persistentes se denomina "serialización".

Un objeto de almacenamiento se puede considerar como un tipo de flujo binario. Al igual que un flujo de entrada/salida, un archivo está asociado a un archivo y permite escribir y leer los datos en el búfer en el almacenamiento. Un flujo de entrada/salida procesa secuencias de caracteres ASCII, pero un archivo procesa los datos de objetos binarios en un formato eficaz y no redundante.

Debe crear un objeto [CFile](../../mfc/reference/cfile-class.md) antes de poder crear un objeto `CArchive`. Además, debe asegurarse de que el estado de carga o almacén del archivo es compatible con el modo de apertura del archivo. Está limitado a un archivo activo por archivo.

Al construir un objeto de `CArchive`, se asocia a un objeto de clase `CFile` (o una clase derivada) que representa un archivo abierto. También debe especificar si el archivo se usará para cargar o almacenar. Un objeto `CArchive` puede procesar no solo tipos primitivos sino también objetos de clases derivadas de [CObject](../../mfc/reference/cobject-class.md)diseñadas para la serialización. Una clase serializable normalmente tiene una función miembro `Serialize`, y normalmente usa las macros [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) , tal y como se describe en clase `CObject`.

Los operadores de extracción ( **>>** ) e inserción sobrecargados ( **<<** ) son interfaces de programación de archivo convenientes que admiten tanto tipos primitivos como clases derivadas de `CObject`.

`CArchive` también admite la programación con las clases de Windows Sockets de MFC [CSocket](../../mfc/reference/csocket-class.md) y [CSocketFile](../../mfc/reference/csocketfile-class.md). La función miembro [IsBufferEmpty](#isbufferempty) admite ese uso.

Para obtener más información sobre `CArchive`, vea los artículos sobre [serialización](../../mfc/serialization-in-mfc.md) y [Windows Sockets: usar sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CArchive`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="abort"></a>CArchive:: ABORT

Llame a esta función para cerrar el archivo sin producir una excepción.

```
void Abort ();
```

### <a name="remarks"></a>Observaciones

Normalmente, el destructor `CArchive` llamará a `Close`, que vaciará todos los datos que no se hayan guardado en el objeto `CFile` asociado. Esto puede producir excepciones.

Al detectar estas excepciones, se recomienda usar `Abort`, de modo que la desestructuración del objeto de `CArchive` no provoque más excepciones. Al controlar excepciones, `CArchive::Abort` no producirá una excepción en los errores porque, a diferencia de [CArchive:: Close](#close), `Abort` omite los errores.

Si ha usado **nuevo** para asignar el objeto de `CArchive` en el montón, debe eliminarlo después de cerrar el archivo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CArchive:: WriteClass](#writeclass).

##  <a name="carchive"></a>CArchive:: CArchive

Construye un objeto `CArchive` y especifica si se va a utilizar para cargar o almacenar objetos.

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>Parámetros

*pFile*<br/>
Puntero al objeto `CFile` que es el origen o el destino más avanzado de los datos persistentes.

*nMode*<br/>
Marca que especifica si los objetos se cargarán o almacenarán en el archivo. El parámetro *nMode* debe tener uno de los valores siguientes:

- `CArchive::load` carga los datos del archivo. Requiere solo `CFile` permiso de lectura.

- `CArchive::store` guarda los datos en el archivo. Requiere `CFile` permiso de escritura.

- `CArchive::bNoFlushOnDelete` impide que el archivo llame automáticamente a `Flush` cuando se llama al destructor de archivo. Si establece esta marca, es responsable de llamar explícitamente a `Close` antes de llamar al destructor. Si no lo hace, los datos se dañarán.

*nBufSize*<br/>
Entero que especifica el tamaño del búfer de archivos interno, en bytes. Tenga en cuenta que el tamaño de búfer predeterminado es de 4.096 bytes. Si normalmente archiva objetos grandes, mejorará el rendimiento si usa un tamaño de búfer mayor que sea un múltiplo del tamaño del búfer de archivos.

*lpBuf*<br/>
Un puntero opcional a un búfer proporcionado por el usuario de tamaño *nBufSize*. Si no se especifica este parámetro, el archivo asigna un búfer del montón local y lo libera cuando se destruye el objeto. El archivo no libera un búfer proporcionado por el usuario.

### <a name="remarks"></a>Observaciones

No se puede cambiar esta especificación después de haber creado el archivo.

No puede usar operaciones de `CFile` para modificar el estado del archivo hasta que cierre el archivo. Cualquier operación de este tipo dañará la integridad del archivo. Puede tener acceso a la posición del puntero de archivo en cualquier momento durante la serialización obteniendo el objeto de archivo del archivo de la función miembro [GetFile](#getfile) y usando después la función [CFile:: GetPosition](../../mfc/reference/cfile-class.md#getposition) . Debe llamar a [CArchive:: Flush](#flush) antes de obtener la posición del puntero de archivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

##  <a name="close"></a>CArchive:: Close

Vacía los datos restantes en el búfer, cierra el archivo y desconecta el archivo del archivo.

```
void Close();
```

### <a name="remarks"></a>Observaciones

No se permiten más operaciones en el archivo. Después de cerrar un archivo, puede crear otro archivo para el mismo archivo o puede cerrar el archivo.

La función miembro `Close` garantiza que todos los datos se transfieren del archivo al archivo y hace que el archivo no esté disponible. Para completar la transferencia del archivo al medio de almacenamiento, primero debe usar [CFile:: Close](../../mfc/reference/cfile-class.md#close) y, a continuación, destruir el objeto `CFile`.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CArchive:: WriteString](#writestring).

##  <a name="flush"></a>CArchive:: Flush

Fuerza la escritura de los datos restantes en el búfer de archivo en el archivo.

```
void Flush();
```

### <a name="remarks"></a>Observaciones

La función miembro `Flush` garantiza que todos los datos se transfieren desde el archivo al archivo. Debe llamar a [CFile:: Close](../../mfc/reference/cfile-class.md#close) para completar la transferencia desde el archivo al medio de almacenamiento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

##  <a name="getfile"></a>CArchive:: GetFile

Obtiene el puntero de objeto `CFile` para este archivo.

```
CFile* GetFile() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero constante al objeto de `CFile` en uso.

### <a name="remarks"></a>Observaciones

Debe vaciar el archivo antes de usar `GetFile`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

##  <a name="getobjectschema"></a>CArchive:: GetObjectSchema

Llame a esta función desde la función `Serialize` para determinar la versión del objeto que se está deserializando actualmente.

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>Valor devuelto

Durante la deserialización, la versión del objeto que se lee.

### <a name="remarks"></a>Observaciones

La llamada a esta función solo es válida cuando se está cargando el objeto de `CArchive` ( [CArchive:: IsLoading](#isloading) devuelve un valor distinto de cero). Debe ser la primera llamada en la función `Serialize` y llamar solo una vez. Un valor devuelto de (UINT)-1 indica que se desconoce el número de versión.

Una clase derivada de `CObject`puede utilizar VERSIONABLE_SCHEMA combinadas (mediante **OR bit a**bit) con la propia versión de esquema (en la macro IMPLEMENT_SERIAL) para crear un "objeto de la versión", es decir, un objeto cuya función miembro `Serialize` puede leer varias versiones. La funcionalidad predeterminada del marco de trabajo (sin VERSIONABLE_SCHEMA) es producir una excepción cuando la versión no coincide.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

##  <a name="isbufferempty"></a>CArchive:: IsBufferEmpty

Llame a esta función miembro para determinar si el búfer interno del objeto de almacenamiento está vacío.

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el búfer del archivo está vacío; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Esta función se proporciona para admitir la programación con la clase de Windows Sockets de MFC `CSocketFile`. No es necesario usarlo para un archivo asociado a un objeto de `CFile`.

La razón para usar `IsBufferEmpty` con un archivo asociado a un objeto `CSocketFile` es que el búfer del archivo puede contener más de un mensaje o registro. Después de recibir un mensaje, debe utilizar `IsBufferEmpty` para controlar un bucle que siga recibiendo datos hasta que el búfer esté vacío. Para obtener más información, vea la función miembro [Receive](../../mfc/reference/casyncsocket-class.md#receive) de la clase `CAsyncSocket`, que muestra cómo usar `IsBufferEmpty`.

Para obtener más información, vea [Windows Sockets: usar sockets con archivos](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="isloading"></a>CArchive:: IsLoading

Determina si el archivo está cargando datos.

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el archivo se está usando actualmente para cargar; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Las funciones de `Serialize` de las clases archivadas llaman a esta función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

##  <a name="isstoring"></a>CArchive:: IsStoring

Determina si el archivo almacena los datos.

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el archivo se está usando actualmente para el almacenamiento; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Las funciones de `Serialize` de las clases archivadas llaman a esta función miembro.

Si el estado de `IsStoring` de un archivo es distinto de cero, su estado de `IsLoading` es 0 y viceversa.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

##  <a name="mapobject"></a>CArchive:: MapObject

Llame a esta función miembro para colocar objetos en el mapa que no se serializan realmente en el archivo, pero que están disponibles para que los subobjetos hagan referencia.

```
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>Parámetros

*pOb*<br/>
Puntero constante al objeto que se va a almacenar.

### <a name="remarks"></a>Observaciones

Por ejemplo, es posible que no serialice un documento, pero serializaría los elementos que forman parte del documento. Mediante una llamada a `MapObject`, permite que dichos elementos, o subobjetos, hagan referencia al documento. Además, los subelementos serializados pueden serializar su *m_pDocument* puntero de retroceso.

Puede llamar a `MapObject` al almacenar y cargar desde el objeto `CArchive`. `MapObject` agrega el objeto especificado a las estructuras de datos internas que mantiene el objeto `CArchive` durante la serialización y deserialización, pero a diferencia de [ReadObject](#readobject) y [writeObject](#writeobject), no llama a Serialize en el objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

##  <a name="m_pdocument"></a>CArchive:: m_pDocument

De forma predeterminada, se establece en NULL, este puntero a un `CDocument` se puede establecer en cualquier valor que desee el usuario de la instancia de `CArchive`.

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>Observaciones

Un uso común de este puntero es transmitir información adicional sobre el proceso de serialización a todos los objetos que se están serializando. Esto se logra inicializando el puntero con el documento (una clase derivada de `CDocument`) que se está serializando, de tal forma que los objetos del documento puedan tener acceso al documento si es necesario. Este puntero también se usa en `COleClientItem` objetos durante la serialización.

El marco de trabajo establece *m_pDocument* en el documento que se está serializando cuando un usuario emite un comando para abrir o guardar un archivo. Si serializa un documento de contenedor de vinculación e incrustación de objetos (OLE) por motivos distintos al abrir o guardar un archivo, debe establecer explícitamente *m_pDocument*. Por ejemplo, esto se haría al serializar un documento contenedor en el portapapeles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

##  <a name="operator_lt_lt"></a>CArchive:: Operator &lt;&lt;

Almacena el objeto o el tipo primitivo indicado en el archivo.

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

`CArchive` referencia que habilita varios operadores de inserción en una sola línea.

### <a name="remarks"></a>Observaciones

Las dos últimas versiones anteriores son específicamente para almacenar enteros de 64 bits.

Si usó la macro IMPLEMENT_SERIAL en la implementación de la clase, el operador de inserción sobrecargado para `CObject` llama al `WriteObject`protegido. Esta función, a su vez, llama a la función `Serialize` de la clase.

El operador de inserción de [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) (< <) admite el volcado y el almacenamiento de diagnósticos en un archivo.

### <a name="example"></a>Ejemplo

En este ejemplo se muestra el uso del operador de inserción de `CArchive` < < con los tipos **int** y **Long** .

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>Ejemplo

En este ejemplo 2 se muestra el uso del operador de inserción de `CArchive` < < con el tipo de `CStringT`.

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

##  <a name="operator_gt_gt"></a>CArchive:: Operator &gt;&gt;

Carga el objeto o el tipo primitivo indicado desde el archivo.

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

`CArchive` referencia que habilita varios operadores de extracción en una sola línea.

### <a name="remarks"></a>Observaciones

Las dos últimas versiones anteriores son específicamente para cargar enteros de 64 bits.

Si usó la macro IMPLEMENT_SERIAL en la implementación de la clase, los operadores de extracción sobrecargados para `CObject` llamar a la función protegida `ReadObject` (con un puntero de clase en tiempo de ejecución distinto de cero). Esta función, a su vez, llama a la función `Serialize` de la clase.

El operador de extracción de [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) (> >) admite la carga desde un archivo.

### <a name="example"></a>Ejemplo

En este ejemplo se muestra el uso del operador de extracción `CArchive` > > con el tipo **int** .

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>Ejemplo

En este ejemplo se muestra el uso de los operadores de inserción y extracción de `CArchive` <\< y > > con el tipo `CStringT`.

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

##  <a name="read"></a>CArchive:: Read

Lee un número especificado de bytes del archivo.

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Un puntero a un búfer proporcionado por el usuario que va a recibir los datos leídos del archivo.

*Nmáx.*<br/>
Entero sin signo que especifica el número de bytes que se van a leer del archivo.

### <a name="return-value"></a>Valor devuelto

Entero sin signo que contiene el número de bytes leídos realmente. Si el valor devuelto es menor que el número solicitado, se ha alcanzado el final del archivo. No se produce ninguna excepción en la condición de final de archivo.

### <a name="remarks"></a>Observaciones

El archivo no interpreta los bytes.

Puede usar la función miembro `Read` dentro de la función `Serialize` para leer estructuras ordinarias que se encuentran en los objetos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

##  <a name="readclass"></a>CArchive:: ReadClass

Llame a esta función miembro para leer una referencia a una clase previamente almacenada con [WriteClass](#writeclass).

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>Parámetros

*pClassRefRequested*<br/>
Puntero a la estructura [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) que corresponde a la referencia de clase solicitada. Puede ser NULL.

*pSchema*<br/>
Un puntero a un esquema de la clase en tiempo de ejecución previamente almacenada.

*pObTag*<br/>
Número que hace referencia a la etiqueta única de un objeto. Lo utiliza internamente la implementación de [ReadObject](#readobject). Expuesto solo para la programación avanzada; Normalmente, *pObTag* debe ser null.

### <a name="return-value"></a>Valor devuelto

Puntero a la estructura [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) .

### <a name="remarks"></a>Observaciones

Si *pClassRefRequested* no es NULL, `ReadClass` comprueba que la información de la clase archivada es compatible con la clase en tiempo de ejecución. Si no es compatible, `ReadClass` producirá una [CArchiveException](../../mfc/reference/carchiveexception-class.md).

La clase en tiempo de ejecución debe utilizar [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); de lo contrario, `ReadClass` producirá una [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Si *pSchema* es null, se puede recuperar el esquema de la clase almacenada llamando a [CArchive:: GetObjectSchema](#getobjectschema); de lo contrario, <strong>\*</strong> *pSchema* contendrá el esquema de la clase en tiempo de ejecución que se almacenó previamente.

Puede usar [SerializeClass](#serializeclass) en lugar de `ReadClass`, que controla tanto la lectura como la escritura de la referencia de clase.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CArchive:: WriteClass](#writeclass).

##  <a name="readobject"></a>CArchive:: ReadObject

Lee datos de objeto del archivo y crea un objeto del tipo adecuado.

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>Parámetros

*pClass*<br/>
Puntero constante a la estructura [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) que corresponde al objeto que se espera leer.

### <a name="return-value"></a>Valor devuelto

Un puntero [CObject](../../mfc/reference/cobject-class.md) que debe convertirse de forma segura en la clase derivada correcta mediante [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof).

### <a name="remarks"></a>Observaciones

Esta función se llama normalmente mediante el operador `CArchive` extracción ( **>>** ) sobrecargado para un puntero [CObject](../../mfc/reference/cobject-class.md) . `ReadObject`, a su vez, llama a la función de `Serialize` de la clase archivada.

Si proporciona un parámetro *pClass* distinto de cero, que se obtiene mediante la macro [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) , la función comprueba la clase en tiempo de ejecución del objeto archivado. Se supone que ha usado la macro IMPLEMENT_SERIAL en la implementación de la clase.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CArchive:: writeObject](#writeobject).

##  <a name="readstring"></a>CArchive:: ReadString

Llame a esta función miembro para leer los datos de texto en un búfer del archivo asociado al objeto de `CArchive`.

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>Parámetros

*rString*<br/>
Referencia a un objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contendrá la cadena resultante una vez leída desde el archivo asociado al objeto CArchive.

*lpsz*<br/>
Especifica un puntero a un búfer proporcionado por el usuario que recibirá una cadena de texto terminada en NULL.

*Nmáx.*<br/>
Especifica el número máximo de caracteres que se van a leer. Debe ser uno menos que el tamaño del búfer de *lpsz* .

### <a name="return-value"></a>Valor devuelto

En la versión que devuelve BOOL, TRUE si se realiza correctamente; De lo contrario, FALSE.

En la versión que devuelve un `LPTSTR`, puntero al búfer que contiene los datos de texto; ES NULL si se alcanzó el final del archivo.

### <a name="remarks"></a>Observaciones

En la versión de la función miembro con el parámetro *nmáx.* , el búfer contendrá hasta un límite de *nmáx.* -1. La lectura está detenida por un par de retorno de carro y avance de línea. Los caracteres de nueva línea finales siempre se quitan. En cualquier caso, se anexa un carácter nulo (' \ 0 ').

[CArchive:: Read](#read) también está disponible para la entrada en modo de texto, pero no termina en un par de retorno de carro y avance de línea.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CArchive:: WriteString](#writestring).

##  <a name="serializeclass"></a>CArchive:: SerializeClass

Llame a esta función miembro cuando desee almacenar y cargar la información de versión de una clase base.

```
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parámetros

*pClassRef*<br/>
Un puntero a un objeto de clase en tiempo de ejecución para la clase base.

### <a name="remarks"></a>Observaciones

`SerializeClass` lee o escribe la referencia a una clase en el objeto `CArchive`, en función de la dirección de la `CArchive`. Use `SerializeClass` en lugar de [ReadClass](#readclass) y [WriteClass](#writeclass) como una manera cómoda de serializar objetos de clase base. `SerializeClass` requiere menos código y menos parámetros.

Como `ReadClass`, `SerializeClass` comprueba que la información de la clase archivada es compatible con la clase en tiempo de ejecución. Si no es compatible, `SerializeClass` producirá una [CArchiveException](../../mfc/reference/carchiveexception-class.md).

La clase en tiempo de ejecución debe utilizar [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); de lo contrario, `SerializeClass` producirá una [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Use la macro [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) para recuperar el valor del parámetro *pRuntimeClass* . La clase base debe haber usado la macro [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

##  <a name="setloadparams"></a>CArchive:: SetLoadParams

Llame a `SetLoadParams` cuando vaya a leer un gran número de objetos derivados de `CObject`desde un archivo.

```
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>Parámetros

*nGrowBy*<br/>
Número mínimo de espacios de elementos que se van a asignar si es necesario un aumento de tamaño.

### <a name="remarks"></a>Observaciones

`CArchive` usa una matriz de carga para resolver las referencias a los objetos almacenados en el archivo. `SetLoadParams` permite establecer el tamaño con el que crece la matriz de carga.

No debe llamar a `SetLoadParams` una vez que se haya cargado ningún objeto o después de llamar a [MapObject](#mapobject) o [ReadObject](#readobject) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="setobjectschema"></a>CArchive:: SetObjectSchema

Llame a esta función miembro para establecer el esquema de objeto almacenado en el objeto de almacenamiento en *nSchema*.

```
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>Parámetros

*nSchema*<br/>
Especifica el esquema del objeto.

### <a name="remarks"></a>Observaciones

La siguiente llamada a [GetObjectSchema](#getobjectschema) devolverá el valor almacenado en *nSchema*.

Usar `SetObjectSchema` para el control de versiones avanzado; por ejemplo, si desea forzar la lectura de una versión determinada en una función `Serialize` de una clase derivada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

##  <a name="setstoreparams"></a>CArchive:: SetStoreParams

Utilice `SetStoreParams` al almacenar un gran número de objetos derivados de `CObject`en un archivo.

```
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>Parámetros

*nHashSize*<br/>
Tamaño de la tabla hash para las asignaciones de puntero de interfaz. Debe ser un número primo.

*nBlockSize*<br/>
Especifica la granularidad de asignación de memoria para extender los parámetros. Debe ser una potencia de 2 para obtener el mejor rendimiento.

### <a name="remarks"></a>Observaciones

`SetStoreParams` permite establecer el tamaño de la tabla hash y el tamaño de bloque de la asignación que se usa para identificar objetos únicos durante el proceso de serialización.

No debe llamar a `SetStoreParams` una vez que se haya almacenado ningún objeto o después de llamar a [MapObject](#mapobject) o [writeObject](#writeobject) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="write"></a>CArchive:: Write

Escribe un número especificado de bytes en el archivo.

```
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Un puntero a un búfer proporcionado por el usuario que contiene los datos que se van a escribir en el archivo.

*Nmáx.*<br/>
Entero que especifica el número de bytes que se van a escribir en el archivo.

### <a name="remarks"></a>Observaciones

El archivo no formatea los bytes.

Puede usar la función miembro `Write` dentro de la función `Serialize` para escribir estructuras ordinarias contenidas en los objetos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

##  <a name="writeclass"></a>CArchive:: WriteClass

Utilice `WriteClass` para almacenar la información de versión y de clase de una clase base durante la serialización de la clase derivada.

```
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parámetros

*pClassRef*<br/>
Puntero a la estructura [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) que corresponde a la referencia de clase solicitada.

### <a name="remarks"></a>Observaciones

`WriteClass` escribe en el `CArchive`una referencia a [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) para la clase base. Use [CArchive:: ReadClass](#readclass) para recuperar la referencia.

`WriteClass` comprueba que la información de la clase archivada es compatible con la clase en tiempo de ejecución. Si no es compatible, `WriteClass` producirá una [CArchiveException](../../mfc/reference/carchiveexception-class.md).

La clase en tiempo de ejecución debe utilizar [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) y [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); de lo contrario, `WriteClass` producirá una [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Puede usar [SerializeClass](#serializeclass) en lugar de `WriteClass`, que controla tanto la lectura como la escritura de la referencia de clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

##  <a name="writeobject"></a>CArchive:: WriteObject

Almacena el `CObject` especificado en el archivo.

```
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>Parámetros

*pOb*<br/>
Puntero constante al objeto que se va a almacenar.

### <a name="remarks"></a>Observaciones

Esta función se llama normalmente mediante el operador de inserción de `CArchive` ( **<<** ) sobrecargado para `CObject`. `WriteObject`, a su vez, llama a la función de `Serialize` de la clase archivada.

Debe utilizar la macro IMPLEMENT_SERIAL para habilitar el archivado. `WriteObject` escribe el nombre de clase ASCII en el archivo. Este nombre de clase se validará más adelante durante el proceso de carga. Un esquema de codificación especial evita la duplicación innecesaria del nombre de clase para varios objetos de la clase. Este esquema también evita el almacenamiento redundante de objetos que están destinados a más de un puntero.

El método de codificación de objetos exacto (incluida la presencia del nombre de clase ASCII) es un detalle de implementación y podría cambiar en versiones futuras de la biblioteca.

> [!NOTE]
>  Termine de crear, eliminar y actualizar todos los objetos antes de empezar a archivarlos. El archivo se dañará si combina el archivado con la modificación de objetos.

### <a name="example"></a>Ejemplo

Para obtener una definición de la clase `CAge`, vea el ejemplo de [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist).

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

##  <a name="writestring"></a>CArchive:: WriteString

Utilice esta función miembro para escribir datos de un búfer en el archivo asociado al objeto de `CArchive`.

```
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parámetros

*lpsz*<br/>
Especifica un puntero a un búfer que contiene una cadena de texto terminada en NULL.

### <a name="remarks"></a>Observaciones

El carácter nulo de terminación (' \ 0 ') no se escribe en el archivo; ni se escribe automáticamente una nueva línea.

`WriteString` produce una excepción en respuesta a varias condiciones, incluida la condición Disk-Full.

`Write` también está disponible, pero en lugar de terminar en un carácter nulo, escribe el número solicitado de bytes en el archivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFile (clase)](../../mfc/reference/cfile-class.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[CSocket (clase)](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile (clase)](../../mfc/reference/csocketfile-class.md)
