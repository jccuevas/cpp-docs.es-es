---
title: CFile (clase)
ms.date: 06/12/2018
f1_keywords:
- CFile
- AFX/CFile
- AFX/CFile::CFile
- AFX/CFile::Abort
- AFX/CFile::Close
- AFX/CFile::Duplicate
- AFX/CFile::Flush
- AFX/CFile::GetFileName
- AFX/CFile::GetFilePath
- AFX/CFile::GetFileTitle
- AFX/CFile::GetLength
- AFX/CFile::GetPosition
- AFX/CFile::GetStatus
- AFX/CFile::LockRange
- AFX/CFile::Open
- AFX/CFile::Read
- AFX/CFile::Remove
- AFX/CFile::Rename
- AFX/CFile::Seek
- AFX/CFile::SeekToBegin
- AFX/CFile::SeekToEnd
- AFX/CFile::SetFilePath
- AFX/CFile::SetLength
- AFX/CFile::SetStatus
- AFX/CFile::UnlockRange
- AFX/CFile::Write
- AFX/CFile::hFileNull
- AFX/CFile::m_hFile
- AFX/CFile::m_pTM
helpviewer_keywords:
- CFile [MFC], CFile
- CFile [MFC], Abort
- CFile [MFC], Close
- CFile [MFC], Duplicate
- CFile [MFC], Flush
- CFile [MFC], GetFileName
- CFile [MFC], GetFilePath
- CFile [MFC], GetFileTitle
- CFile [MFC], GetLength
- CFile [MFC], GetPosition
- CFile [MFC], GetStatus
- CFile [MFC], LockRange
- CFile [MFC], Open
- CFile [MFC], Read
- CFile [MFC], Remove
- CFile [MFC], Rename
- CFile [MFC], Seek
- CFile [MFC], SeekToBegin
- CFile [MFC], SeekToEnd
- CFile [MFC], SetFilePath
- CFile [MFC], SetLength
- CFile [MFC], SetStatus
- CFile [MFC], UnlockRange
- CFile [MFC], Write
- CFile [MFC], hFileNull
- CFile [MFC], m_hFile
- CFile [MFC], m_pTM
ms.assetid: b2eb5757-d499-4e67-b044-dd7d1abaa0f8
ms.openlocfilehash: 4ba37d481db73fb0556659ede267b3474c3f32f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373919"
---
# <a name="cfile-class"></a>CFile (clase)

La clase base para las clases de archivo de MFC (Microsoft Foundation Classes).

## <a name="syntax"></a>Sintaxis

```
class CFile : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFile::CFile](#cfile)|Construye un `CFile` objeto a partir de una ruta de acceso o un identificador de archivo.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFile::Abort](#abort)|Cierra un archivo ignorando todas las advertencias y errores.|
|[CFile::Cerrar](#close)|Cierra un archivo y elimina el objeto.|
|[CFile::Duplicate](#duplicate)|Construye un objeto duplicado basado en este archivo.|
|[CFile::Flush](#flush)|Vacía los datos que aún no se han escrito.|
|[CFile::GetFileName](#getfilename)|Recupera el nombre de archivo del archivo seleccionado.|
|[CFile::GetFilePath](#getfilepath)|Recupera la ruta de acceso completa del archivo seleccionado.|
|[CFile::GetFileTitle](#getfiletitle)|Recupera el título del archivo seleccionado.|
|[CFile::GetLength](#getlength)|Recupera la longitud del archivo.|
|[CFile::GetPosition](#getposition)|Recupera el puntero de archivo actual.|
|[CFile::GetStatus](#getstatus)|Recupera el estado del archivo abierto, o en la versión estática, recupera el estado del archivo especificado (estático, función virtual).|
|[CFile::LockRange](#lockrange)|Bloquea un intervalo de bytes en un archivo.|
|[CFile::Abrir](#open)|Abre un archivo de forma segura con una opción de prueba de errores.|
|[CFile::Leer](#read)|Lee (sin búfer) los datos de un archivo en la posición actual del archivo.|
|[CFile::Quitar](#remove)|Elimina el archivo especificado (función estática).|
|[CFile::Rename](#rename)|Cambia el nombre del archivo especificado (función estática).|
|[CFile::Buscar](#seek)|Coloca el puntero de archivo actual.|
|[CFile::SeekToBegin](#seektobegin)|Coloca el puntero de archivo actual al principio del archivo.|
|[CFile::SeekToEnd](#seektoend)|Coloca el puntero de archivo actual al final del archivo.|
|[CFile::SetFilePath](#setfilepath)|Establece la ruta de archivo completa del archivo seleccionado.|
|[CFile::SetLength](#setlength)|Cambia la longitud del archivo.|
|[CFile::SetStatus](#setstatus)|Establece el estado del archivo especificado (estático, función virtual).|
|[CFile::UnlockRange](#unlockrange)|Desbloquea un intervalo de bytes en un archivo.|
|[CFile::Write](#write)|Escribe datos (sin búfer) en un archivo en la posición actual del archivo.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFile::operador HANDLE](#operator_handle)|Identificador de `CFile` un objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFile::hFileNull](#hfilenull)|Determina si `CFile` el objeto tiene un identificador válido.|
|[CFile::m_hFile](#m_hfile)|Normalmente contiene el identificador de archivo del sistema operativo.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CFile::m_pTM](#m_ptm)|Puntero al objeto `CAtlTransactionManager`.|

## <a name="remarks"></a>Observaciones

Proporciona directamente servicios de entrada/salida de disco binario sin búfer, y admite indirectamente archivos de texto y archivos de memoria a través de sus clases derivadas. `CFile`funciona junto con `CArchive` la clase para admitir la serialización de objetos de Microsoft Foundation Class.

La relación jerárquica entre esta clase y sus clases derivadas permite que `CFile` el programa funcione en todos los objetos de archivo a través de la interfaz polimórfica. Un archivo de memoria, por ejemplo, se comporta como un archivo de disco.

Uso `CFile` y sus clases derivadas para E/S de disco de uso general. Usar `ofstream` u `iostream` otras clases de Microsoft para el texto con formato enviado a un archivo de disco.

Normalmente, un archivo de `CFile` disco se abre automáticamente en la construcción y se cierra al destruirlo. Las funciones miembro estáticas le permiten interrogar el estado de un archivo sin abrir el archivo.

Para obtener más `CFile`información sobre el uso , vea los artículos [Archivos en MFC](../../mfc/files-in-mfc.md) y [Control](../../c-runtime-library/file-handling.md) de archivos en la Referencia de biblioteca en tiempo *de ejecución*.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

## <a name="cfileabort"></a><a name="abort"></a>CFile::Abort

Cierra el archivo asociado a este objeto y hace que el archivo no esté disponible para su lectura o escritura.

```
virtual void Abort();
```

### <a name="remarks"></a>Observaciones

Si no ha cerrado el archivo antes de destruir el objeto, el destructor lo cierra por usted.

Al controlar excepciones, `CFile::Abort` `CFile::Close` difiere de dos maneras importantes. En primer `Abort` lugar, la función no producirá una excepción `Abort`en los errores, porque . En `Abort` segundo lugar, no **ASSERT** si el archivo no se ha abierto o se ha cerrado anteriormente.

Si usó **new** para `CFile` asignar el objeto en el montón, debe eliminarlo después de cerrar el archivo. `Abort`establece `m_hFile` `CFile::hFileNull`en .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]

## <a name="cfilecfile"></a><a name="cfile"></a>CFile::CFile

Construye e inicializa un objeto `CFile`.

```
CFile();
CFile(CAtlTransactionManager* pTM);
CFile(HANDLE hFile);

CFile(
LPCTSTR lpszFileName,
UINT nOpenFlags);

CFile(
LPCTSTR lpszFileName,
UINT nOpenFlags,
CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Parámetros

*hArchivo*<br/>
Identificador de un archivo que se va a adjuntar al objeto `CFile`.

*lpszFileName*<br/>
Ruta completa o relativa de un archivo que se va a adjuntar al objeto `CFile`.

*nOpenFlags*<br/>
Combinación bit a bit (OR) de las opciones de acceso de archivo relativas al archivo especificado. Consulte la sección Comentarios para ver las opciones posibles.

*Ptm*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="remarks"></a>Observaciones

En las cinco tablas siguientes se enumeran las opciones posibles para el *nOpenFlags* parámetro.

Elija solo una de las siguientes opciones de modo de acceso de archivo. El modo de acceso de archivo predeterminado es `CFile::modeRead`, que es de solo lectura.

|Value|Descripción|
|-----------|-----------------|
|`CFile::modeRead`|Solicita únicamente acceso de lectura.|
|`CFile::modeWrite`|Solicita únicamente acceso de escritura.|
|`CFile::modeReadWrite`|Solicita acceso de lectura y escritura.|

Elija solo una de las siguientes opciones de modo de carácter.

|Value|Descripción|
|-----------|-----------------|
|`CFile::typeBinary`|Establece el modo binario (solo se usa en clases derivadas).|
|`CFile::typeText`|Establece el modo de texto con procesamiento especial para los pares de avance de línea de retorno de carro (utilizado solo en clases derivadas).|
|`CFile::typeUnicode`|Establece el modo Unicode (solo se usa en clases derivadas). El texto se escribe en el archivo en formato Unicode cuando la aplicación se basa en una configuración de Unicode. No se escriba ninguna BOM en el archivo.|

Elija solo una de las siguientes opciones de modo de uso compartido de archivo. El modo de uso compartido de archivo predeterminado es `CFile::shareExclusive`, que es exclusivo.

|Value|Descripción|
|-----------|-----------------|
|`CFile::shareDenyNone`|No hay restricciones de uso compartido.|
|`CFile::shareDenyRead`|Deniega el acceso de lectura al resto.|
|`CFile::shareDenyWrite`|Deniega el acceso de escritura al resto.|
|`CFile::shareExclusive`|Deniega el acceso de lectura y escritura al resto.|

Elija la primera (o ambas) de las siguientes opciones de modo de creación de archivo. El modo de creación de archivo predeterminado es `CFile::modeNoTruncate`, que solo permite abrir archivos existentes.

|Value|Descripción|
|-----------|-----------------|
|`CFile::modeCreate`|Crea un nuevo archivo si no existe ningún archivo. Si el archivo ya existe, se sobrescribe y se establece inicialmente en longitud cero.|
|`CFile::modeNoTruncate`|Crea un nuevo archivo si no existe ningún archivo; de lo contrario, si el archivo ya `CFile` existe, se adjunta al objeto.|

Elija de entre las siguientes opciones de almacenamiento en caché según la descripción. De forma predeterminada, el sistema utiliza un esquema de almacenamiento en caché de uso general que no está disponible como opción.

|Value|Descripción|
|-----------|-----------------|
|`CFile::osNoBuffer`|El sistema no utiliza una memoria caché intermedia para el archivo. Esta opción anula las dos opciones siguientes.|
|`CFile::osRandomAccess`|La memoria caché de archivos se optimiza para el acceso aleatorio. No utilice esta opción ni la opción de análisis secuencial.|
|`CFile::osSequentialScan`|La memoria caché de archivos se optimiza para el acceso secuencial. No utilice esta opción ni la opción de acceso aleatorio.|
|`CFile::osWriteThrough`|Las operaciones de escritura se realizan sin demora.|

Elija la siguiente opción de seguridad para impedir que el identificador de archivos se herede. Cualquier proceso secundario nuevo puede usar el identificador de archivos de forma predeterminada.

|Value|Descripción|
|-----------|-----------------|
|`CFile::modeNoInherit`|Impide que los procesos secundarios puedan usar el identificador de archivos.|

El constructor predeterminado inicializa los miembros, pero `CFile` no adjunta un archivo al objeto. Después de usar este constructor, utilice el [CFile::Open](#open) `CFile` método para abrir un archivo y adjuntarlo al objeto.

El constructor con un parámetro inicializa miembros y adjunta un archivo existente al objeto `CFile`.

El constructor con dos parámetros inicializa miembros y trata de abrir el archivo especificado. Si este constructor abre el archivo especificado sin problemas, dicho archivo se adjunta al objeto `CFile`; de lo contrario, el constructor produce un puntero al objeto `CInvalidArgException`. Para obtener más información acerca de cómo controlar las excepciones, vea [Excepciones](../../mfc/exception-handling-in-mfc.md).

Si `CFile` un objeto abre correctamente un archivo especificado, cerrará `CFile` este archivo automáticamente cuando se destruya el objeto; de lo contrario, debe cerrar explícitamente el archivo `CFile` después de que ya no se adjunta al objeto.

### <a name="example"></a>Ejemplo

En el siguiente código se muestra cómo usar un `CFile`.

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

## <a name="cfileclose"></a><a name="close"></a>CFile::Cerrar

Cierra el archivo asociado a este objeto y hace que el archivo no esté disponible para su lectura o escritura.

```
virtual void Close();
```

### <a name="remarks"></a>Observaciones

Si no ha cerrado el archivo antes de destruir el objeto, el destructor lo cierra por usted.

Si usó **new** para `CFile` asignar el objeto en el montón, debe eliminarlo después de cerrar el archivo. `Close`establece `m_hFile` `CFile::hFileNull`en .

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFile::CFile](#cfile).

## <a name="cfileduplicate"></a><a name="duplicate"></a>CFile::Duplicate

Construye un `CFile` objeto duplicado para un archivo determinado.

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a un `CFile` objeto duplicado.

### <a name="remarks"></a>Observaciones

Esta función es equivalente a `_dup`la función de tiempo de ejecución de C.

## <a name="cfileflush"></a><a name="flush"></a>CFile::Flush

Obliga a que los datos que queden en el búfer de archivos se escriban en el archivo.

```
virtual void Flush();
```

### <a name="remarks"></a>Observaciones

El uso `Flush` de no garantiza `CArchive` el vaciado de los búferes. Si utiliza un archivo, llame primero a [CArchive::Flush.](../../mfc/reference/carchive-class.md#flush)

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFile::SetFilePath](#setfilepath).

## <a name="cfilegetfilename"></a><a name="getfilename"></a>CFile::GetFileName

Llame a esta función miembro para recuperar el nombre de un archivo especificado.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Valor devuelto

Nombre del archivo.

### <a name="remarks"></a>Observaciones

Por ejemplo, cuando `GetFileName` se llama para generar un `c:\windows\write\myfile.wri`mensaje al `myfile.wri`usuario sobre el archivo, se devuelve el nombre de archivo, , .

Para devolver la ruta de acceso completa del archivo, incluido el nombre, llame a [GetFilePath](#getfilepath). Para devolver el título `myfile`del archivo ( ), llame a [GetFileTitle](#getfiletitle).

### <a name="example"></a>Ejemplo

Este fragmento de código abre el SISTEMA. INI en el directorio WINDOWS. Si se encuentra, el ejemplo imprimirá el nombre y la ruta y el título, como se muestra en Salida:

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

## <a name="cfilegetfilepath"></a><a name="getfilepath"></a>CFile::GetFilePath

Llame a esta función miembro para recuperar la ruta de acceso completa de un archivo especificado.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Valor devuelto

La ruta de acceso completa del archivo especificado.

### <a name="remarks"></a>Observaciones

Por ejemplo, cuando `GetFilePath` se llama para generar un `c:\windows\write\myfile.wri`mensaje al `c:\windows\write\myfile.wri`usuario sobre el archivo , se devuelve la ruta de acceso del archivo, , .

Para devolver solo el nombre`myfile.wri`del archivo ( ), llame a [GetFileName](#getfilename). Para devolver el título`myfile`del archivo ( ), llame a [GetFileTitle](#getfiletitle).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetFileName](#getfilename).

## <a name="cfilegetfiletitle"></a><a name="getfiletitle"></a>CFile::GetFileTitle

Llame a esta función miembro para recuperar el título del archivo (el nombre para mostrar) para el archivo.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Valor devuelto

El título del archivo subyacente.

### <a name="remarks"></a>Observaciones

Este método llama a [GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew) para recuperar el título del archivo. Si se realiza correctamente, el método devuelve la cadena que el sistema usaría para mostrar el nombre de archivo al usuario. De lo contrario, el método llama a [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) para recuperar el nombre de archivo (incluida la extensión de archivo) del archivo subyacente. Esto significa que la extensión de archivo no siempre se incluye en la cadena de título del archivo devuelto. Para obtener más información, vea [GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew) y [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) en el Windows SDK.

Para devolver la ruta de acceso completa del archivo, incluido el nombre, llame a [GetFilePath](#getfilepath). Para devolver solo el nombre del archivo, llame a [GetFileName](#getfilename).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetFileName](#getfilename).

## <a name="cfilegetlength"></a><a name="getlength"></a>CFile::GetLength

Obtiene la longitud lógica actual del archivo en bytes.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud del archivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

## <a name="cfilegetposition"></a><a name="getposition"></a>CFile::GetPosition

Obtiene el valor actual del puntero de archivo, que `Seek`se puede utilizar en llamadas posteriores a .

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>Valor devuelto

El puntero de archivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

## <a name="cfilegetstatus"></a><a name="getstatus"></a>CFile::GetStatus

Este método recupera información de `CFile` estado relacionada con una instancia de objeto determinada o una ruta de acceso de archivo determinada.

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*rStatus*<br/>
Una referencia a una `CFileStatus` estructura proporcionada por el usuario que recibirá la información de estado. La `CFileStatus` estructura tiene los siguientes campos:

- `CTime m_ctime`La fecha y hora en que se creó el archivo.

- `CTime m_mtime`La fecha y hora en que se modificó por última vez el archivo.

- `CTime m_atime`La fecha y la hora en que se accedió por última vez al archivo para su lectura.

- `ULONGLONG m_size`El tamaño lógico del archivo en bytes, según lo informado por el comando DIR.

- `BYTE m_attribute`El byte de atributo del archivo.

- `char m_szFullName[_MAX_PATH]`El nombre de archivo absoluto en el juego de caracteres de Windows.

*lpszFileName*<br/>
Cadena en el juego de caracteres de Windows que es la ruta de acceso al archivo deseado. La ruta de acceso puede ser relativa o absoluta, o puede contener un nombre de ruta de acceso de red.

*Ptm*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="return-value"></a>Valor devuelto

TRUESi la información de estado del archivo especificado se obtiene correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

La versión no `GetStatus` estática de recupera información de estado `CFile` del archivo abierto asociado con el objeto especificado.  La versión `GetStatus` estática de obtiene el estado del archivo de una ruta de acceso de archivo determinada sin abrir realmente el archivo. Esta versión es útil para probar la existencia y los derechos de acceso de un archivo.

El `m_attribute` miembro `CFileStatus` de la estructura hace referencia al conjunto de atributos de archivo. La `CFile` clase proporciona el tipo de enumeración **Attribute** para que los atributos de archivo se puedan especificar simbólicamente:

```
enum Attribute {
    normal =    0x00,
    readOnly =  0x01,
    hidden =    0x02,
    system =    0x04,
    volume =    0x08,
    directory = 0x10,
    archive =   0x20
    };
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#10](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_6.cpp)]

## <a name="cfilehfilenull"></a><a name="hfilenull"></a>CFile::hFileNull

Determina la presencia de un identificador `CFile` de archivo válido para el objeto.

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>Observaciones

Esta constante se utiliza `CFile` para determinar si el objeto tiene un identificador de archivo válido.

En el ejemplo siguiente se muestra esta operación:

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

## <a name="cfilelockrange"></a><a name="lockrange"></a>CFile::LockRange

Bloquea un intervalo de bytes en un archivo abierto, iniciando una excepción si el archivo ya está bloqueado.

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Parámetros

*dwPos*<br/>
Desplazamiento de bytes del inicio del intervalo de bytes que se va a bloquear.

*dwCount*<br/>
El número de bytes en el intervalo que se va a bloquear.

### <a name="remarks"></a>Observaciones

El bloqueo de bytes en un archivo impide que otros procesos obtengan acceso a dichos bytes. Puede bloquear más de una región de un archivo, pero no se permiten regiones superpuestas.

Al desbloquear la región `UnlockRange` mediante la función miembro, el intervalo de bytes debe corresponder exactamente a la región que se bloqueó anteriormente. La `LockRange` función no combina regiones adyacentes. Si dos regiones bloqueadas son adyacentes, debe desbloquear cada región por separado.

> [!NOTE]
> Esta función no está `CMemFile`disponible para la clase derivada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

## <a name="cfilem_hfile"></a><a name="m_hfile"></a>CFile::m_hFile

Contiene el identificador de archivo del sistema operativo para un archivo abierto.

```
HANDLE m_hFile;
```

### <a name="remarks"></a>Observaciones

`m_hFile`es una variable pública de tipo UINT. Contiene `CFile::hFileNull`, un indicador de archivo vacío independiente del sistema operativo, si el identificador no se ha asignado.

No `m_hFile` se recomienda el uso de, porque el significado del miembro depende de la clase derivada. `m_hFile`se hace un miembro público para mayor comodidad en el apoyo al uso no polimórfico de la clase.

## <a name="cfilem_ptm"></a><a name="m_ptm"></a>CFile::m_pTM

Puntero a `CAtlTransactionManager` un objeto.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Observaciones

## <a name="cfileopen"></a><a name="open"></a>CFile::Abrir

Sobrecargado. `Open`está diseñado para su `CFile` uso con el constructor predeterminado.

```
virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszFileName*<br/>
Cadena que contiene la ruta de acceso al archivo deseado. La ruta de acceso puede ser relativa, absoluta o un nombre de red (UNC).

*nOpenFlags*<br/>
UINT que define el modo de acceso y uso compartido del archivo. Especifica la acción que se debe realizar al abrir el archivo. Puede combinar opciones mediante el operador OR ( **&#124;** ) bit a bit. Se requiere un permiso de acceso y una opción de recurso compartido; los `modeCreate` `modeNoInherit` modos y son opcionales. Consulte el [CFile](#cfile) constructor para obtener una lista de opciones de modo.

*pError*<br/>
Puntero a un objeto de excepción de archivo existente que recibirá el estado de una operación con errores.

*Ptm*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el abierto se realizó correctamente; de lo contrario 0. El parámetro *pError* solo es significativo si se devuelve 0.

### <a name="remarks"></a>Observaciones

Las `Open` dos funciones son métodos "seguros" para abrir un archivo, donde un error es una condición normal y esperada.

Mientras `CFile` que el constructor produce una `Open` excepción en una condición de error, devuelve FALSE para las condiciones de error. `Open`Sin embargo, todavía puede inicializar un objeto [CFileException](../../mfc/reference/cfileexception-class.md) para describir el error. Si no proporciona el parámetro *pError,* o si pasa `Open` NULL para *pError*, `CFileException`devuelve FALSE y no produce un archivo . Si pasa un puntero `CFileException`a `Open` un archivo , y encuentra un error, la función lo rellena con información que describe ese error. `Open`no produce una excepción en ninguno de los dos casos.

En la tabla siguiente se `Open`describen los posibles resultados de .

|`pError`|Error encontrado|Valor devuelto|Contenido de CFileException|
|--------------|------------------------|------------------|----------------------------|
|NULL|No|TRUE|N/D|
|ptr a`CFileException`|No|TRUE|sin cambios|
|NULL|Sí|FALSE|N/D|
|ptr a`CFileException`|Sí|FALSE|inicializado para describir el error|

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

## <a name="cfileoperator-handle"></a><a name="operator_handle"></a>CFile::operador HANDLE

Utilice este operador para pasar `CFile` un identificador a un objeto a funciones `HANDLE`como [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) y [GetFileTime](/windows/win32/api/fileapi/nf-fileapi-getfiletime) que esperan un archivo .

```
operator HANDLE() const;
```

## <a name="cfileread"></a><a name="read"></a>CFile::Leer

Lee los datos en un búfer `CFile` del archivo asociado al objeto.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Puntero al búfer proporcionado por el usuario que va a recibir los datos leídos del archivo.

*nCount*<br/>
El número máximo de bytes que se leerán del archivo. Para los archivos de modo de texto, los pares de avance de línea de retorno de carro se cuentan como caracteres únicos.

### <a name="return-value"></a>Valor devuelto

Número de bytes que se transfieren al búfer. Para `CFile` todas las clases, el valor devuelto puede ser menor que *nCount* si se alcanzó el final del archivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

Para obtener otro ejemplo, vea [CFile::Open](#open).

## <a name="cfileremove"></a><a name="remove"></a>CFile::Quitar

Esta función estática elimina el archivo especificado por la ruta de acceso.

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszFileName*<br/>
Cadena que es la ruta de acceso al archivo deseado. La ruta de acceso puede ser relativa o absoluta y puede contener un nombre de red.

*Ptm*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="remarks"></a>Observaciones

`Remove`no eliminará un directorio.

La `Remove` función miembro produce una excepción si el archivo conectado está abierto o si el archivo no se puede quitar. Esta función es equivalente al comando DEL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

## <a name="cfilerename"></a><a name="rename"></a>CFile::Rename

Esta función estática cambia el nombre del archivo especificado.

```
static void PASCAL Rename(
    LPCTSTR lpszOldName,
    LPCTSTR lpszNewName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszOldName*<br/>
El viejo camino.

*lpszNewName*<br/>
El nuevo camino.

*Ptm*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="remarks"></a>Observaciones

No se puede cambiar el nombre de los directorios. Esta función es equivalente al comando REN.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

## <a name="cfileseek"></a><a name="seek"></a>CFile::Buscar

Cambia la posición del puntero de archivo en un archivo abierto.

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>Parámetros

*Loff*<br/>
Número de bytes para mover el puntero de archivo. Los valores positivos mueven el puntero del archivo hacia el final del archivo; los valores negativos mueven el puntero del archivo hacia el inicio del archivo.

*nDe*<br/>
Posición para buscar. Consulte la sección Comentarios para ver los valores posibles.

### <a name="return-value"></a>Valor devuelto

La posición del puntero de archivo si el método se realizó correctamente; de lo contrario, el valor devuelto `CFileException` es indefinido y se produce un puntero a una excepción.

### <a name="remarks"></a>Observaciones

En la tabla siguiente se enumeran los valores posibles para el *nFrom* parámetro.

|Value|Descripción|
|-----------|-----------------|
|`CFile::begin`|Busque desde el principio del archivo.|
|`CFile::current`|Busque en la ubicación actual del puntero de archivo.|
|`CFile::end`|Busque desde el final del archivo.|

Cuando se abre un archivo, el puntero del archivo se coloca en 0, el inicio del archivo.

Puede establecer el puntero de archivo en una posición más allá del final de un archivo. Si lo hace, el tamaño del archivo no aumenta hasta que escribe en el archivo.

El controlador de excepciones para este método debe eliminar el objeto de excepción después de procesar la excepción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]

## <a name="cfileseektobegin"></a><a name="seektobegin"></a>CFile::SeekToBegin

Establece el valor del puntero de archivo al principio del archivo.

```
void SeekToBegin();
```

### <a name="remarks"></a>Observaciones

`SeekToBegin()` equivale a `Seek( 0L, CFile::begin )`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

## <a name="cfileseektoend"></a><a name="seektoend"></a>CFile::SeekToEnd

Establece el valor del puntero de archivo en el extremo lógico del archivo.

```
ULONGLONG SeekToEnd();
```

### <a name="return-value"></a>Valor devuelto

La longitud del archivo en bytes.

### <a name="remarks"></a>Observaciones

`SeekToEnd()` equivale a `CFile::Seek( 0L, CFile::end )`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

## <a name="cfilesetfilepath"></a><a name="setfilepath"></a>CFile::SetFilePath

Llame a esta función para especificar la ruta de acceso del archivo. Por ejemplo, si la ruta de acceso de un archivo no `SetFilePath` está disponible cuando se construye un [CFile](../../mfc/reference/cfile-class.md) objeto, llame para proporcionarlo.

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parámetros

*lpszNewName*<br/>
Puntero a una cadena que especifica la nueva ruta de acceso.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> `SetFilePath`no abre el archivo ni crea el archivo; simplemente asocia `CFile` el objeto con un nombre de ruta de acceso, que luego se puede utilizar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

## <a name="cfilesetlength"></a><a name="setlength"></a>CFile::SetLength

Llame a esta función para cambiar la longitud del archivo.

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>Parámetros

*dwNewLen*<br/>
Longitud deseada del archivo en bytes. Este valor puede ser mayor o menor que la longitud actual del archivo. El archivo se extenderá o truncará según corresponda.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Con `CMemFile`, esta función podría lanzar un `CMemoryException` objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

## <a name="cfilesetstatus"></a><a name="setstatus"></a>CFile::SetStatus

Establece el estado del archivo asociado a esta ubicación del archivo.

```
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,
    const CFileStatus& status,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszFileName*<br/>
Cadena que es la ruta de acceso al archivo deseado. La ruta de acceso puede ser relativa o absoluta y puede contener un nombre de red.

*status*<br/>
El búfer que contiene la nueva información de estado. Llame `GetStatus` a la función `CFileStatus` miembro para rellenar previamente la estructura con los valores actuales y, a continuación, realice los cambios según sea necesario. Si un valor es 0, el elemento de estado correspondiente no se actualiza. Vea el [GetStatus](#getstatus) función miembro `CFileStatus` para obtener una descripción de la estructura.

*Ptm*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="remarks"></a>Observaciones

Para establecer la hora, modifique el `m_mtime` campo de *estado*.

Cuando se realiza `SetStatus` una llamada en un intento de cambiar `m_mtime` solo los atributos del archivo y el miembro de la estructura de estado del archivo es distinto de cero, los atributos también pueden verse afectados (cambiar la marca de tiempo puede tener efectos secundarios en los atributos). Si solo desea cambiar los atributos del `m_mtime` archivo, establezca primero el miembro de la `SetStatus`estructura de estado del archivo en cero y, a continuación, realice una llamada a .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]

## <a name="cfileunlockrange"></a><a name="unlockrange"></a>CFile::UnlockRange

Desbloquea un intervalo de bytes en un archivo abierto.

```
virtual void UnlockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Parámetros

*dwPos*<br/>
Desplazamiento de bytes del inicio del intervalo de bytes que se va a desbloquear.

*dwCount*<br/>
El número de bytes en el intervalo que se va a desbloquear.

### <a name="remarks"></a>Observaciones

Consulte la descripción de la [LockRange](#lockrange) función miembro para obtener más información.

> [!NOTE]
> Esta función no `CMemFile`está disponible para la clase derivada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

## <a name="cfilewrite"></a><a name="write"></a>CFile::Write

Escribe datos de un búfer en `CFile` el archivo asociado al objeto.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Puntero al búfer proporcionado por el usuario que contiene los datos que se van a escribir en el archivo.

*nCount*<br/>
El número de bytes que se transferirán desde el búfer. Para los archivos de modo de texto, los pares de avance de línea de retorno de carro se cuentan como caracteres únicos.

### <a name="remarks"></a>Observaciones

`Write`produce una excepción en respuesta a varias condiciones, incluida la condición de disco completo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

Consulte también los ejemplos de [CFile::CFile](#cfile) y [CFile::Open](#open).

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CStdioFile](../../mfc/reference/cstdiofile-class.md)<br/>
[Clase CMemFile](../../mfc/reference/cmemfile-class.md)
