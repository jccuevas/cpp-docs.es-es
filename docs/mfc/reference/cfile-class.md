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
ms.openlocfilehash: a9161764f6c8646766a73add01c25cce5619ad19
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506581"
---
# <a name="cfile-class"></a>CFile (clase)

La clase base para las clases de archivo de MFC (Microsoft Foundation Classes).

## <a name="syntax"></a>Sintaxis

```
class CFile : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFile::CFile](#cfile)|Construye un `CFile` objeto a partir de una ruta de acceso o un identificador de archivo.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFile::Abort](#abort)|Cierra un archivo que omite todas las advertencias y errores.|
|[CFile::Close](#close)|Cierra un archivo y elimina el objeto.|
|[CFile::Duplicate](#duplicate)|Construye un objeto duplicado basado en este archivo.|
|[CFile::Flush](#flush)|Vacía los datos que todavía se van a escribir.|
|[CFile::GetFileName](#getfilename)|Recupera el nombre de archivo del archivo seleccionado.|
|[CFile::GetFilePath](#getfilepath)|Recupera la ruta de acceso completa del archivo seleccionado.|
|[CFile::GetFileTitle](#getfiletitle)|Recupera el título del archivo seleccionado.|
|[CFile::GetLength](#getlength)|Recupera la longitud del archivo.|
|[CFile::GetPosition](#getposition)|Recupera el puntero de archivo actual.|
|[CFile::GetStatus](#getstatus)|Recupera el estado del archivo abierto, o en la versión estática, recupera el estado del archivo especificado (función virtual estática).|
|[CFile::LockRange](#lockrange)|Bloquea un intervalo de bytes en un archivo.|
|[CFile::Open](#open)|Abre de forma segura un archivo con una opción de prueba de errores.|
|[CFile::Read](#read)|Lee datos (no almacenados en búfer) de un archivo en la posición actual del archivo.|
|[CFile::Remove](#remove)|Elimina el archivo especificado (función estática).|
|[CFile::Rename](#rename)|Cambia el nombre del archivo especificado (función estática).|
|[CFile::Seek](#seek)|Coloca el puntero de archivo actual.|
|[CFile::SeekToBegin](#seektobegin)|Coloca el puntero del archivo actual al principio del archivo.|
|[CFile::SeekToEnd](#seektoend)|Coloca el puntero del archivo actual al final del archivo.|
|[CFile::SetFilePath](#setfilepath)|Establece la ruta de acceso completa del archivo seleccionado.|
|[CFile::SetLength](#setlength)|Cambia la longitud del archivo.|
|[CFile::SetStatus](#setstatus)|Establece el estado del archivo especificado (función virtual estática).|
|[CFile::UnlockRange](#unlockrange)|Desbloquea un intervalo de bytes en un archivo.|
|[CFile::Write](#write)|Escribe datos (sin almacenar en búfer) en un archivo en la posición actual del archivo.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFile:: Operator (identificador)](#operator_handle)|Identificador de un `CFile` objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFile::hFileNull](#hfilenull)|Determina si el `CFile` objeto tiene un identificador válido.|
|[CFile::m_hFile](#m_hfile)|Normalmente contiene el identificador de archivo del sistema operativo.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFile::m_pTM](#m_ptm)|Puntero al `CAtlTransactionManager` objeto.|

## <a name="remarks"></a>Comentarios

Proporciona directamente servicios de entrada/salida de disco binarios sin almacenamiento en búfer y admite indirectamente archivos de texto y archivos de memoria a través de sus clases derivadas. `CFile`funciona junto con la clase `CArchive` para admitir la serialización de objetos de Microsoft Foundation Class.

La relación jerárquica entre esta clase y sus clases derivadas permite que el programa opere en todos los objetos de archivo a través `CFile` de la interfaz polimórfica. Un archivo de memoria, por ejemplo, se comporta como un archivo de disco.

Use `CFile` y sus clases derivadas para la e/s de disco de uso general. Use `ofstream` u otras clases `iostream` de Microsoft para el texto con formato que se envía a un archivo de disco.

Normalmente, un archivo de disco se abre automáticamente `CFile` al construirse y cerrarse en la destrucción. Las funciones miembro estáticas permiten consultar el estado de un archivo sin abrir el archivo.

Para obtener más información sobre `CFile`el uso de, vea los artículos [archivos en MFC](../../mfc/files-in-mfc.md) y [control de archivos](../../c-runtime-library/file-handling.md) en la referencia de la *biblioteca en tiempo de ejecución*.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** afx.h

##  <a name="abort"></a>  CFile::Abort

Cierra el archivo asociado a este objeto y hace que el archivo no esté disponible para lectura o escritura.

```
virtual void Abort();
```

### <a name="remarks"></a>Comentarios

Si no ha cerrado el archivo antes de destruir el objeto, el destructor lo cierra automáticamente.

Al controlar excepciones, `CFile::Abort` difiere de `CFile::Close` en dos aspectos importantes. En primer lugar `Abort` , la función no producirá una excepción en los errores, porque `Abort`omite los errores. En segundo `Abort` lugar, no se **validará** si el archivo no se ha abierto o se ha cerrado previamente.

Si ha usado **nuevo** para asignar el `CFile` objeto en el montón, debe eliminarlo después de cerrar el archivo. `Abort`establece `m_hFile` en `CFile::hFileNull`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]

##  <a name="cfile"></a>  CFile::CFile

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

*hFile*<br/>
Identificador de un archivo que se va a adjuntar al objeto `CFile`.

*lpszFileName*<br/>
Ruta completa o relativa de un archivo que se va a adjuntar al objeto `CFile`.

*nOpenFlags*<br/>
Combinación bit a bit (OR) de las opciones de acceso de archivo relativas al archivo especificado. Consulte la sección Comentarios para ver las opciones posibles.

*pTM*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="remarks"></a>Comentarios

En las cinco tablas siguientes se enumeran las posibles opciones del parámetro *nOpenFlags* .

Elija solo una de las siguientes opciones de modo de acceso de archivo. El modo de acceso de archivo predeterminado es `CFile::modeRead`, que es de solo lectura.

|Valor|DESCRIPCIÓN|
|-----------|-----------------|
|`CFile::modeRead`|Solicita únicamente acceso de lectura.|
|`CFile::modeWrite`|Solicita únicamente acceso de escritura.|
|`CFile::modeReadWrite`|Solicita acceso de lectura y escritura.|

Elija solo una de las siguientes opciones de modo de carácter.

|Valor|DESCRIPCIÓN|
|-----------|-----------------|
|`CFile::typeBinary`|Establece el modo binario (solo se usa en clases derivadas).|
|`CFile::typeText`|Establece el modo de texto con procesamiento especial para los pares de retorno de carro y avance de línea (solo se usa en clases derivadas).|
|`CFile::typeUnicode`|Establece el modo Unicode (solo se usa en clases derivadas). El texto se escribe en el archivo en formato Unicode cuando la aplicación se basa en una configuración de Unicode. No se escriba ninguna BOM en el archivo.|

Elija solo una de las siguientes opciones de modo de uso compartido de archivo. El modo de uso compartido de archivo predeterminado es `CFile::shareExclusive`, que es exclusivo.

|Value|DESCRIPCIÓN|
|-----------|-----------------|
|`CFile::shareDenyNone`|No hay restricciones de uso compartido.|
|`CFile::shareDenyRead`|Deniega el acceso de lectura al resto.|
|`CFile::shareDenyWrite`|Deniega el acceso de escritura al resto.|
|`CFile::shareExclusive`|Deniega el acceso de lectura y escritura al resto.|

Elija la primera (o ambas) de las siguientes opciones de modo de creación de archivo. El modo de creación de archivo predeterminado es `CFile::modeNoTruncate`, que solo permite abrir archivos existentes.

|Value|DESCRIPCIÓN|
|-----------|-----------------|
|`CFile::modeCreate`|Crea un nuevo archivo si no existe ningún archivo. Si el archivo ya existe, se sobrescribe y se establece inicialmente en una longitud de cero.|
|`CFile::modeNoTruncate`|Crea un nuevo archivo si no existe ningún archivo; de lo contrario, si el archivo ya existe, se adjunta al `CFile` objeto.|

Elija de entre las siguientes opciones de almacenamiento en caché según la descripción. De forma predeterminada, el sistema utiliza un esquema de almacenamiento en caché de uso general que no está disponible como opción.

|Valor|DESCRIPCIÓN|
|-----------|-----------------|
|`CFile::osNoBuffer`|El sistema no usa una caché intermedia para el archivo. Esta opción anula las dos opciones siguientes.|
|`CFile::osRandomAccess`|La memoria caché de archivos se optimiza para el acceso aleatorio. No use esta opción y la opción de examen secuencial.|
|`CFile::osSequentialScan`|La memoria caché de archivos se optimiza para el acceso secuencial. No use esta opción y la opción de acceso aleatorio.|
|`CFile::osWriteThrough`|Las operaciones de escritura se realizan sin retraso.|

Elija la siguiente opción de seguridad para impedir que el identificador de archivos se herede. Cualquier proceso secundario nuevo puede usar el identificador de archivos de forma predeterminada.

|Valor|DESCRIPCIÓN|
|-----------|-----------------|
|`CFile::modeNoInherit`|Impide que los procesos secundarios puedan usar el identificador de archivos.|

El constructor predeterminado inicializa los miembros pero no adjunta un archivo al `CFile` objeto. Después de usar este constructor, use el método [CFile:: Open](#open) para abrir un archivo y adjuntarlo `CFile` al objeto.

El constructor con un parámetro inicializa miembros y adjunta un archivo existente al objeto `CFile`.

El constructor con dos parámetros inicializa miembros y trata de abrir el archivo especificado. Si este constructor abre el archivo especificado sin problemas, dicho archivo se adjunta al objeto `CFile`; de lo contrario, el constructor produce un puntero al objeto `CInvalidArgException`. Para obtener más información sobre cómo controlar las excepciones, vea [excepciones](../../mfc/exception-handling-in-mfc.md).

Si un `CFile` objeto abre correctamente un archivo especificado, lo cerrará automáticamente cuando se destruya el `CFile` objeto; de lo contrario, debe cerrar explícitamente el archivo después de que `CFile` ya no esté asociado al objeto.

### <a name="example"></a>Ejemplo

En el siguiente código se muestra cómo usar un `CFile`.

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

##  <a name="close"></a>  CFile::Close

Cierra el archivo asociado a este objeto y hace que el archivo no esté disponible para lectura o escritura.

```
virtual void Close();
```

### <a name="remarks"></a>Comentarios

Si no ha cerrado el archivo antes de destruir el objeto, el destructor lo cierra automáticamente.

Si ha usado **nuevo** para asignar el `CFile` objeto en el montón, debe eliminarlo después de cerrar el archivo. `Close`establece `m_hFile` en `CFile::hFileNull`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFile:: CFile](#cfile).

##  <a name="duplicate"></a>  CFile::Duplicate

Construye un objeto duplicado `CFile` para un archivo determinado.

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto `CFile` duplicado.

### <a name="remarks"></a>Comentarios

Esta función es equivalente a la función `_dup`en tiempo de ejecución de C.

##  <a name="flush"></a>  CFile::Flush

Fuerza la escritura de los datos restantes en el búfer de archivos en el archivo.

```
virtual void Flush();
```

### <a name="remarks"></a>Comentarios

El uso de `Flush` no garantiza el vaciado `CArchive` de búferes. Si utiliza un archivo, llame a [CArchive:: Flush](../../mfc/reference/carchive-class.md#flush) primero.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFile:: SetFilePath](#setfilepath).

##  <a name="getfilename"></a>  CFile::GetFileName

Llame a esta función miembro para recuperar el nombre de un archivo especificado.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Valor devuelto

Nombre del archivo.

### <a name="remarks"></a>Comentarios

Por ejemplo, cuando se llama `GetFileName` a para generar un mensaje al usuario sobre el archivo `c:\windows\write\myfile.wri`, se devuelve el `myfile.wri`nombre de archivo,.

Para devolver la ruta de acceso completa del archivo, incluido el nombre, llame a [GetFilePath](#getfilepath). Para devolver el título del archivo ( `myfile`), llame a [GetFileTitle](#getfiletitle).

### <a name="example"></a>Ejemplo

Este fragmento de código abre el sistema. Archivo INI en el directorio de WINDOWS. Si se encuentra, el ejemplo imprimirá el nombre y la ruta de acceso y el título, como se muestra en la salida:

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

##  <a name="getfilepath"></a>  CFile::GetFilePath

Llame a esta función miembro para recuperar la ruta de acceso completa de un archivo especificado.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Valor devuelto

Ruta de acceso completa del archivo especificado.

### <a name="remarks"></a>Comentarios

Por ejemplo, cuando se llama `GetFilePath` a para generar un mensaje al usuario sobre el archivo `c:\windows\write\myfile.wri` `c:\windows\write\myfile.wri`, se devuelve la ruta de acceso del archivo.

Para devolver solo el nombre del archivo (`myfile.wri`), llame a [GetFileName](#getfilename). Para devolver el título del archivo (`myfile`), llame a [GetFileTitle](#getfiletitle).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetFileName](#getfilename).

##  <a name="getfiletitle"></a>  CFile::GetFileTitle

Llame a esta función miembro para recuperar el título del archivo (nombre para mostrar) del archivo.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Valor devuelto

Título del archivo subyacente.

### <a name="remarks"></a>Comentarios

Este método llama a [GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew) para recuperar el título del archivo. Si se realiza correctamente, el método devuelve la cadena que el sistema usaría para mostrar el nombre de archivo al usuario. De lo contrario, el método llama a [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) para recuperar el nombre de archivo (incluida la extensión de archivo) del archivo subyacente. Esto significa que la extensión de archivo no siempre se incluye en la cadena de título de archivo devuelta. Para obtener más información, consulte [GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew) y [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) en el Windows SDK.

Para devolver la ruta de acceso completa del archivo, incluido el nombre, llame a [GetFilePath](#getfilepath). Para devolver solo el nombre del archivo, llame a [GetFileName](#getfilename).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetFileName](#getfilename).

##  <a name="getlength"></a>  CFile::GetLength

Obtiene la longitud lógica actual del archivo en bytes.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Valor devuelto

Longitud del archivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

##  <a name="getposition"></a>  CFile::GetPosition

Obtiene el valor actual del puntero de archivo, que se puede utilizar en llamadas posteriores a `Seek`.

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero de archivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

##  <a name="getstatus"></a>  CFile::GetStatus

Este método recupera información de estado relacionada con una `CFile` instancia de objeto determinada o una ruta de acceso de archivo determinada.

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*rStatus*<br/>
Referencia a una estructura proporcionada `CFileStatus` por el usuario que recibirá la información de estado. La `CFileStatus` estructura tiene los siguientes campos:

- `CTime m_ctime`Fecha y hora en que se creó el archivo.

- `CTime m_mtime`Fecha y hora en que se modificó por última vez el archivo.

- `CTime m_atime`Fecha y hora en que se obtuvo acceso por última vez al archivo para leerlo.

- `ULONGLONG m_size`Tamaño lógico del archivo en bytes, tal y como lo ha indicado el comando DIR.

- `BYTE m_attribute`Byte del atributo del archivo.

- `char m_szFullName[_MAX_PATH]`Nombre de archivo absoluto en el juego de caracteres de Windows.

*lpszFileName*<br/>
Una cadena del juego de caracteres de Windows que es la ruta de acceso al archivo deseado. La ruta de acceso puede ser relativa o absoluta, o puede contener un nombre de ruta de acceso de red.

*pTM*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="return-value"></a>Valor devuelto

TRUE si la información de estado para el archivo especificado se obtiene correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

La versión no estática de `GetStatus` recupera información de estado del archivo abierto asociado al objeto dado. `CFile`  La versión estática de `GetStatus` obtiene el estado del archivo de una ruta de acceso de archivo determinada sin abrir realmente el archivo. Esta versión es útil para probar la existencia y los derechos de acceso de un archivo.

El `m_attribute` miembro de la `CFileStatus` estructura hace referencia al conjunto de atributos de archivo. La `CFile` clase proporciona el tipo de enumeración de **atributos** , por lo que los atributos de archivo se pueden especificar de forma simbólica:

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

##  <a name="hfilenull"></a>  CFile::hFileNull

Determina la presencia de un identificador de archivo válido para `CFile` el objeto.

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>Comentarios

Esta constante se usa para determinar si el `CFile` objeto tiene un identificador de archivo válido.

En el ejemplo siguiente se muestra esta operación:

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

##  <a name="lockrange"></a>  CFile::LockRange

Bloquea un intervalo de bytes en un archivo abierto y produce una excepción si el archivo ya está bloqueado.

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Parámetros

*dwPos*<br/>
Desplazamiento de bytes del inicio del intervalo de bytes que se va a bloquear.

*dwCount*<br/>
Número de bytes del intervalo que se va a bloquear.

### <a name="remarks"></a>Comentarios

El bloqueo de bytes en un archivo impide que otros procesos obtengan acceso a dichos bytes. Puede bloquear más de una región de un archivo, pero no se permiten regiones superpuestas.

Al desbloquear la región mediante la `UnlockRange` función miembro, el intervalo de bytes debe corresponderse exactamente con la región que se bloqueó previamente. La `LockRange` función no combina regiones adyacentes. Si dos regiones bloqueadas son adyacentes, debe desbloquear cada región por separado.

> [!NOTE]
>  Esta función no está disponible para `CMemFile`la clase derivada de.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="m_hfile"></a>  CFile::m_hFile

Contiene el identificador de archivo del sistema operativo para un archivo abierto.

```
HANDLE m_hFile;
```

### <a name="remarks"></a>Comentarios

`m_hFile`es una variable pública de tipo UINT. Contiene `CFile::hFileNull`un indicador de archivo vacío independiente del sistema operativo, si el identificador no se ha asignado.

No se `m_hFile` recomienda el uso de, porque el significado del miembro depende de la clase derivada. `m_hFile`se convierte en un miembro público por comodidad para admitir el uso no polimorfismo de la clase.

##  <a name="m_ptm"></a>  CFile::m_pTM

Puntero a un `CAtlTransactionManager` objeto.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Comentarios

##  <a name="open"></a>CFile:: Open

Sobrecargado. `Open`está diseñado para su uso con el `CFile` constructor predeterminado.

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
Un UINT que define el modo de acceso y el uso compartido del archivo. Especifica la acción que se realizará al abrir el archivo. Puede combinar opciones mediante el operador bit a bit or ( **&#124;** ). Se requieren un permiso de acceso y una opción de recurso compartido; los `modeCreate` modos `modeNoInherit` y son opcionales. Vea el constructor [CFile](#cfile) para obtener una lista de opciones de modo.

*pError*<br/>
Un puntero a un objeto de excepción de archivo existente que recibirá el estado de una operación con errores.

*pTM*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación de apertura se realizó correctamente; de lo contrario, es 0. El parámetro *perror* solo es significativo si se devuelve 0.

### <a name="remarks"></a>Comentarios

Las dos `Open` funciones son métodos "seguros" para abrir un archivo, donde un error es una condición normal y esperada.

Aunque el `CFile` constructor produce una excepción en una condición de error, `Open` devuelve false para las condiciones de error. `Open`sin embargo, puede inicializar un objeto [CFileException](../../mfc/reference/cfileexception-class.md) para describir el error. Si no se proporciona el parámetro *perror* , o si se pasa null para el `Open` `CFileException` *perror*, devuelve false y no inicia. Si se pasa un puntero a un existente `CFileException`y `Open` se encuentra un error, la función lo llena con información que describe ese error. `Open`no produce una excepción en ningún caso.

En la tabla siguiente se describen los posibles `Open`resultados de.

|`pError`|Error detectado|Valor devuelto|Contenido de CFileException|
|--------------|------------------------|------------------|----------------------------|
|NULL|Sin|TRUE|N/D|
|PTR a`CFileException`|Sin|TRUE|sin cambios|
|NULL|Sí|FALSE|N/D|
|PTR a`CFileException`|Sí|FALSE|inicializado para describir el error|

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

##  <a name="operator_handle"></a>CFile:: Operator (identificador)

Utilice este operador para pasar un identificador a un `CFile` objeto a funciones como [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) y [GetFileTime](/windows/win32/api/fileapi/nf-fileapi-getfiletime) que esperan `HANDLE`.

```
operator HANDLE() const;
```

##  <a name="read"></a>  CFile::Read

Lee datos en un búfer del archivo asociado `CFile` al objeto.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Puntero al búfer proporcionado por el usuario que va a recibir los datos leídos del archivo.

*nCount*<br/>
Número máximo de bytes que se van a leer del archivo. En el caso de los archivos de modo de texto, los pares de retorno de carro y avance de línea se cuentan como caracteres individuales.

### <a name="return-value"></a>Valor devuelto

Número de bytes que se transfieren al búfer. Para todas `CFile` las clases, el valor devuelto puede ser menor que *nCount* si se alcanza el final del archivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

Para ver otro ejemplo, vea [CFile:: Open](#open).

##  <a name="remove"></a>  CFile::Remove

Esta función estática elimina el archivo especificado por la ruta de acceso.

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszFileName*<br/>
Cadena que es la ruta de acceso al archivo deseado. La ruta de acceso puede ser relativa o absoluta y puede contener un nombre de red.

*pTM*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="remarks"></a>Comentarios

`Remove`no quitará un directorio.

La `Remove` función miembro produce una excepción si el archivo conectado está abierto o si no se puede quitar el archivo. Esta función es equivalente al comando DEL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

##  <a name="rename"></a>CFile:: Rename

Esta función estática cambia el nombre del archivo especificado.

```
static void PASCAL Rename(
    LPCTSTR lpszOldName,
    LPCTSTR lpszNewName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszOldName*<br/>
La ruta de acceso anterior.

*lpszNewName*<br/>
La nueva ruta de acceso.

*pTM*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="remarks"></a>Comentarios

No se puede cambiar el nombre de los directorios. Esta función es equivalente al comando REN.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

##  <a name="seek"></a>CFile:: Seek

Cambia la posición del puntero de archivo en un archivo abierto.

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>Parámetros

*lOff*<br/>
Número de bytes que se van a trasladar al puntero de archivo. Los valores positivos mueven el puntero de archivo hacia el final del archivo; los valores negativos mueven el puntero de archivo hacia el principio del archivo.

*nFrom*<br/>
Posición desde la que se va a buscar. Vea la sección Comentarios para ver los posibles valores.

### <a name="return-value"></a>Valor devuelto

La posición del puntero de archivo si el método se realizó correctamente; de lo contrario, el valor devuelto es indefinido y se `CFileException` produce un puntero a una excepción.

### <a name="remarks"></a>Comentarios

En la tabla siguiente se enumeran los posibles valores para el parámetro *nde* .

|Value|DESCRIPCIÓN|
|-----------|-----------------|
|`CFile::begin`|Buscar desde el principio del archivo.|
|`CFile::current`|Busca desde la ubicación actual del puntero de archivo.|
|`CFile::end`|Busque desde el final del archivo.|

Cuando se abre un archivo, el puntero de archivo se coloca en 0, el inicio del archivo.

Puede establecer el puntero de archivo en una posición más allá del final de un archivo. Si lo hace, el tamaño del archivo no aumenta hasta que escribe en el archivo.

El controlador de excepciones para este método debe eliminar el objeto de excepción una vez procesada la excepción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]

##  <a name="seektobegin"></a>  CFile::SeekToBegin

Establece el valor del puntero de archivo al principio del archivo.

```
void SeekToBegin();
```

### <a name="remarks"></a>Comentarios

`SeekToBegin()` es equivalente a `Seek( 0L, CFile::begin )`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="seektoend"></a>  CFile::SeekToEnd

Establece el valor del puntero de archivo en el extremo lógico del archivo.

```
ULONGLONG SeekToEnd();
```

### <a name="return-value"></a>Valor devuelto

La longitud del archivo en bytes.

### <a name="remarks"></a>Comentarios

`SeekToEnd()` es equivalente a `CFile::Seek( 0L, CFile::end )`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="setfilepath"></a>  CFile::SetFilePath

Llame a esta función para especificar la ruta de acceso del archivo. Por ejemplo, si la ruta de acceso de un archivo no está disponible cuando se construye un objeto [CFile](../../mfc/reference/cfile-class.md), llame a `SetFilePath` para proporcionarlo.

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parámetros

*lpszNewName*<br/>
Puntero a una cadena que especifica la nueva ruta de acceso.

### <a name="remarks"></a>Comentarios

> [!NOTE]
> `SetFilePath`no abre el archivo ni crea el archivo; simplemente asocia el `CFile` objeto con un nombre de ruta de acceso, que se puede usar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

##  <a name="setlength"></a>  CFile::SetLength

Llame a esta función para cambiar la longitud del archivo.

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>Parámetros

*dwNewLen*<br/>
Longitud deseada del archivo en bytes. Este valor puede ser mayor o menor que la longitud actual del archivo. El archivo se extenderá o se truncará según corresponda.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Con `CMemFile`, esta función podría producir un `CMemoryException` objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

##  <a name="setstatus"></a>  CFile::SetStatus

Establece el estado del archivo asociado a la ubicación de este archivo.

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
Búfer que contiene la nueva información de estado. Llame a `GetStatus` la función miembro para rellenar previamente la `CFileStatus` estructura con los valores actuales y, a continuación, realice los cambios necesarios. Si un valor es 0, no se actualiza el elemento de estado correspondiente. Vea la función miembro [getStatus](#getstatus) para obtener una descripción de `CFileStatus` la estructura.

*pTM*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="remarks"></a>Comentarios

Para establecer la hora, modifique el `m_mtime` campo de *Estado*.

Cuando realiza una llamada a `SetStatus` en un intento de cambiar solo los atributos del archivo y el `m_mtime` miembro de la estructura de estado del archivo es distinto de cero, los atributos también pueden verse afectados (el cambio de la marca de tiempo puede tener efectos secundarios en los atributos). Si solo desea cambiar los atributos del archivo, primero establezca el `m_mtime` miembro de la estructura de estado de archivo en cero y, a continuación, realice una llamada a. `SetStatus`

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]

##  <a name="unlockrange"></a>  CFile::UnlockRange

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
Número de bytes del intervalo que se va a desbloquear.

### <a name="remarks"></a>Comentarios

Vea la descripción de la función miembro [LockRange](#lockrange) para obtener más información.

> [!NOTE]
>  Esta función no está disponible para la `CMemFile`clase derivada de.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="write"></a>CFile:: Write

Escribe los datos de un búfer en el archivo asociado `CFile` al objeto.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Puntero al búfer proporcionado por el usuario que contiene los datos que se van a escribir en el archivo.

*nCount*<br/>
Número de bytes que se van a transferir desde el búfer. En el caso de los archivos de modo de texto, los pares de retorno de carro y avance de línea se cuentan como caracteres individuales.

### <a name="remarks"></a>Comentarios

`Write`produce una excepción en respuesta a varias condiciones, incluida la condición Disk-Full.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

Vea también los ejemplos de [CFile:: CFile](#cfile) y [CFile:: Open](#open).

## <a name="see-also"></a>Vea también

[Ejemplo de MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CStdioFile (clase)](../../mfc/reference/cstdiofile-class.md)<br/>
[CMemFile (clase)](../../mfc/reference/cmemfile-class.md)
