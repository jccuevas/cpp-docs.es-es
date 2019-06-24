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
ms.openlocfilehash: dcfe2fb30269f3f3a4c14664d9f57f5b937c8c6d
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344432"
---
# <a name="cfile-class"></a>CFile (clase)

La clase base para las clases de archivo de MFC (Microsoft Foundation Classes).

## <a name="syntax"></a>Sintaxis

```
class CFile : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CFile::CFile](#cfile)|Construye un `CFile` objeto a partir de un identificador de archivo o ruta de acceso.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CFile::Abort](#abort)|Cierra un archivo se omitirá todas las advertencias y errores.|
|[CFile::Close](#close)|Cierra un archivo y elimina el objeto.|
|[CFile::Duplicate](#duplicate)|Construye un objeto duplicado en función de este archivo.|
|[CFile::Flush](#flush)|Vacía los datos aún se escriban.|
|[CFile::GetFileName](#getfilename)|Recupera el nombre de archivo del archivo seleccionado.|
|[CFile::GetFilePath](#getfilepath)|Recupera la ruta de acceso completa del archivo seleccionado.|
|[CFile::GetFileTitle](#getfiletitle)|Recupera el título del archivo seleccionado.|
|[CFile::GetLength](#getlength)|Recupera la longitud del archivo.|
|[CFile::GetPosition](#getposition)|Recupera el puntero de archivo actual.|
|[CFile::GetStatus](#getstatus)|Recupera el estado del archivo abierto o en la versión estática, recupera el estado del archivo especificado (función static, virtual).|
|[CFile::LockRange](#lockrange)|Bloquea un intervalo de bytes en un archivo.|
|[CFile::Open](#open)|Con seguridad abre un archivo con una opción de prueba de errores.|
|[CFile::Read](#read)|Lecturas de datos (sin almacenamiento en búfer) desde un archivo en la posición de archivo actual.|
|[CFile::Remove](#remove)|Elimina el archivo especificado (función estática).|
|[CFile::Rename](#rename)|Cambia el nombre del archivo especificado (función estática).|
|[CFile::Seek](#seek)|Coloca el puntero de archivo actual.|
|[CFile::SeekToBegin](#seektobegin)|Coloca el puntero de archivo actual al principio del archivo.|
|[CFile::SeekToEnd](#seektoend)|Coloca el puntero de archivo actual al final del archivo.|
|[CFile::SetFilePath](#setfilepath)|Establece la ruta de acceso completa del archivo seleccionado.|
|[CFile::SetLength](#setlength)|Cambia la longitud del archivo.|
|[CFile::SetStatus](#setstatus)|Establece el estado del archivo especificado (función static, virtual).|
|[CFile::UnlockRange](#unlockrange)|Desbloquea un intervalo de bytes en un archivo.|
|[CFile::Write](#write)|Escribe los datos (sin almacenamiento en búfer) en un archivo a la posición actual del archivo.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CFile::operator HANDLE](#operator_handle)|Un identificador para un `CFile` objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CFile::hFileNull](#hfilenull)|Determina si el `CFile` objeto tiene un identificador válido.|
|[CFile::m_hFile](#m_hfile)|Normalmente, contiene el identificador de archivo del sistema operativo.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Name|Descripción|
|----------|-----------------|
|[CFile::m_pTM](#m_ptm)|Puntero a `CAtlTransactionManager` objeto.|

## <a name="remarks"></a>Comentarios

Proporciona servicios de entrada/salida de disco no almacenado en búfer, binarios directamente e indirectamente admite archivos de texto y archivos de memoria a través de sus clases derivadas. `CFile` funciona junto con el `CArchive` clase para admitir la serialización de objetos de Microsoft Foundation Class.

La relación jerárquica entre esta clase y sus clases derivadas permite al programa para que funcione en todos los objetos de archivo a través de la polimórfico `CFile` interfaz. Un archivo de memoria, por ejemplo, se comporta como un archivo de disco.

Use `CFile` y sus clases derivadas para E/S de disco de uso general. Use `ofstream` u otro Microsoft `iostream` clases para el texto con formato que se envían a un archivo de disco.

Normalmente, un archivo de disco se abre automáticamente en `CFile` construcción y destrucción cerrada en. Las funciones miembro estáticas permiten consultar el estado de un archivo sin tener que abrir el archivo.

Para obtener más información sobre el uso de `CFile`, consulte los artículos [archivos en MFC](../../mfc/files-in-mfc.md) y [manejo de archivos](../../c-runtime-library/file-handling.md) en el *referencia de la biblioteca de tiempo de ejecución*.

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

Si aún no lo ha cerrado el archivo antes de destruir el objeto, el destructor cierra automáticamente.

Cuando el control de excepciones, `CFile::Abort` difiere `CFile::Close` en dos aspectos importantes. En primer lugar, el `Abort` función no arrojará una excepción en errores, porque se omiten los errores por `Abort`. Segundo, `Abort` no **ASSERT** si aún no se ha abierto el archivo o se ha cerrado previamente.

Si ha usado **nueva** para asignar el `CFile` objeto en el montón, a continuación, debe eliminar después de cerrar el archivo. `Abort` establece `m_hFile` a `CFile::hFileNull`.

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

Las cinco tablas siguientes enumeran las opciones posibles para el *nOpenFlags* parámetro.

Elija solo una de las siguientes opciones de modo de acceso de archivo. El modo de acceso de archivo predeterminado es `CFile::modeRead`, que es de solo lectura.

|Valor|Descripción|
|-----------|-----------------|
|`CFile::modeRead`|Solicita únicamente acceso de lectura.|
|`CFile::modeWrite`|Solicita únicamente acceso de escritura.|
|`CFile::modeReadWrite`|Solicita acceso de lectura y escritura.|

Elija solo una de las siguientes opciones de modo de carácter.

|Valor|Descripción|
|-----------|-----------------|
|`CFile::typeBinary`|Establece el modo binario (solo se usa en clases derivadas).|
|`CFile::typeText`|Establece el modo de texto con un procesamiento especial para los pares de avance de línea de retorno de carro (que se usa en clases derivadas solo).|
|`CFile::typeUnicode`|Establece el modo Unicode (solo se usa en clases derivadas). El texto se escribe en el archivo en formato Unicode cuando la aplicación se basa en una configuración de Unicode. No se escriba ninguna BOM en el archivo.|

Elija solo una de las siguientes opciones de modo de uso compartido de archivo. El modo de uso compartido de archivo predeterminado es `CFile::shareExclusive`, que es exclusivo.

|Valor|Descripción|
|-----------|-----------------|
|`CFile::shareDenyNone`|No hay restricciones de uso compartido.|
|`CFile::shareDenyRead`|Deniega el acceso de lectura al resto.|
|`CFile::shareDenyWrite`|Deniega el acceso de escritura al resto.|
|`CFile::shareExclusive`|Deniega el acceso de lectura y escritura al resto.|

Elija la primera (o ambas) de las siguientes opciones de modo de creación de archivo. El modo de creación de archivo predeterminado es `CFile::modeNoTruncate`, que solo permite abrir archivos existentes.

|Valor|Descripción|
|-----------|-----------------|
|`CFile::modeCreate`|Crea un nuevo archivo si no existe ningún archivo. Si el archivo ya existe, tiene sobrescribe y se establecen inicialmente a longitud cero.|
|`CFile::modeNoTruncate`|Crea un nuevo archivo si no existe ningún archivo; en caso contrario, si el archivo ya existe, se adjunta a la `CFile` objeto.|

Elija de entre las siguientes opciones de almacenamiento en caché según la descripción. De forma predeterminada, el sistema usa un esquema de almacenamiento en caché de uso general que no está disponible como una opción.

|Valor|Descripción|
|-----------|-----------------|
|`CFile::osNoBuffer`|El sistema no usa una caché intermedia para el archivo. Esta opción anula las dos opciones siguientes.|
|`CFile::osRandomAccess`|La memoria caché de archivos se optimiza para el acceso aleatorio. No use esta opción y la opción de exploración secuencial.|
|`CFile::osSequentialScan`|La memoria caché de archivos se optimiza para el acceso secuencial. No use esta opción y la opción de acceso aleatorio.|
|`CFile::osWriteThrough`|Escribir las operaciones se realizan sin retraso.|

Elija la siguiente opción de seguridad para impedir que el identificador de archivos se herede. Cualquier proceso secundario nuevo puede usar el identificador de archivos de forma predeterminada.

|Valor|Descripción|
|-----------|-----------------|
|`CFile::modeNoInherit`|Impide que los procesos secundarios puedan usar el identificador de archivos.|

El constructor predeterminado inicializa miembros, pero no adjunta un archivo a la `CFile` objeto. Después de utilizar este constructor, utilice el [CFile::Open](#open) método para abrir un archivo y adjuntarlo a la `CFile` objeto.

El constructor con un parámetro inicializa miembros y adjunta un archivo existente al objeto `CFile`.

El constructor con dos parámetros inicializa miembros y trata de abrir el archivo especificado. Si este constructor abre el archivo especificado sin problemas, dicho archivo se adjunta al objeto `CFile`; de lo contrario, el constructor produce un puntero al objeto `CInvalidArgException`. Para obtener más información acerca de cómo controlar las excepciones, vea [excepciones](../../mfc/exception-handling-in-mfc.md).

Si un `CFile` objeto abre correctamente un archivo especificado, cerrará automáticamente cuando el `CFile` se destruye el objeto; en caso contrario, debe cerrar explícitamente el archivo después de que ya no está adjunto a la `CFile` objeto.

### <a name="example"></a>Ejemplo

En el siguiente código se muestra cómo usar un `CFile`.

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

##  <a name="close"></a>  CFile::Close

Cierra el archivo asociado a este objeto y hace que el archivo no esté disponible para lectura o escritura.

```
virtual void Close();
```

### <a name="remarks"></a>Comentarios

Si aún no lo ha cerrado el archivo antes de destruir el objeto, el destructor cierra automáticamente.

Si ha usado **nueva** para asignar el `CFile` objeto en el montón, a continuación, debe eliminar después de cerrar el archivo. `Close` establece `m_hFile` a `CFile::hFileNull`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFile::CFile](#cfile).

##  <a name="duplicate"></a>  CFile::Duplicate

Crea un duplicado `CFile` objeto para un archivo determinado.

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un duplicado `CFile` objeto.

### <a name="remarks"></a>Comentarios

Esta función es equivalente a la función de tiempo de ejecución de C `_dup`.

##  <a name="flush"></a>  CFile::Flush

Obliga a los datos permanecen en el búfer de archivo que se escriban en el archivo.

```
virtual void Flush();
```

### <a name="remarks"></a>Comentarios

El uso de `Flush` no garantiza el vaciado de `CArchive` búferes. Si usa un archivo, llame a [CArchive::Flush](../../mfc/reference/carchive-class.md#flush) primero.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CFile::SetFilePath](#setfilepath).

##  <a name="getfilename"></a>  CFile::GetFileName

Llame a esta función miembro para recuperar el nombre de un archivo especificado.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Valor devuelto

Nombre del archivo.

### <a name="remarks"></a>Comentarios

Por ejemplo, cuando se llama a `GetFileName` para generar un mensaje al usuario sobre el archivo `c:\windows\write\myfile.wri`, el nombre de archivo, `myfile.wri`, se devuelve.

Para devolver la ruta de acceso completa del archivo, incluido el nombre, llame a [GetFilePath](#getfilepath). Para devolver el título del archivo ( `myfile`), llame a [GetFileTitle](#getfiletitle).

### <a name="example"></a>Ejemplo

Este fragmento de código abre el sistema. Archivo INI en el directorio de WINDOWS. Si se encuentra, en el ejemplo se imprimirá el nombre y la ruta de acceso y el título, como se muestra en la salida:

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

##  <a name="getfilepath"></a>  CFile::GetFilePath

Llame a esta función miembro para recuperar la ruta de acceso completa de un archivo especificado.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Valor devuelto

La ruta de acceso completa del archivo especificado.

### <a name="remarks"></a>Comentarios

Por ejemplo, cuando se llama a `GetFilePath` para generar un mensaje al usuario sobre el archivo `c:\windows\write\myfile.wri`, la ruta de acceso de archivo, `c:\windows\write\myfile.wri`, se devuelve.

Para devolver solo el nombre del archivo (`myfile.wri`), llame a [GetFileName](#getfilename). Para devolver el título del archivo (`myfile`), llame a [GetFileTitle](#getfiletitle).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetFileName](#getfilename).

##  <a name="getfiletitle"></a>  CFile::GetFileTitle

Llame a esta función miembro para recuperar el título del archivo (el nombre para mostrar) para el archivo.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Valor devuelto

El título del archivo subyacente.

### <a name="remarks"></a>Comentarios

Este método llama a [GetFileTitle](/windows/desktop/api/commdlg/nf-commdlg-getfiletitlea) para recuperar el título del archivo. Si se realiza correctamente, el método devuelve la cadena que utilizaría el sistema para mostrar el nombre de archivo para el usuario. En caso contrario, se llama al método [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea) para recuperar el nombre de archivo (incluida la extensión de archivo) del archivo subyacente. Esto significa que la extensión de archivo no se incluye siempre en la cadena de título de archivo devuelto. Para obtener más información, consulte [GetFileTitle](/windows/desktop/api/commdlg/nf-commdlg-getfiletitlea) y [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea) en el SDK de Windows.

Para devolver la ruta de acceso completa del archivo, incluido el nombre, llame a [GetFilePath](#getfilepath). Para devolver solo el nombre del archivo, llame a [GetFileName](#getfilename).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [GetFileName](#getfilename).

##  <a name="getlength"></a>  CFile::GetLength

Obtiene la longitud de la lógica actual del archivo en bytes.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud del archivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

##  <a name="getposition"></a>  CFile::GetPosition

Obtiene el valor actual del puntero de archivo, que se puede usar en las llamadas posteriores a `Seek`.

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>Valor devuelto

El puntero de archivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

##  <a name="getstatus"></a>  CFile::GetStatus

Este método recupera información de estado relacionada con un determinado `CFile` instancia de objeto o una ruta de acceso de archivo dado.

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*rStatus*<br/>
Una referencia a la proporcionada por el usuario `CFileStatus` estructura que recibirá la información de estado. El `CFileStatus` estructura tiene los siguientes campos:

- `CTime m_ctime` La fecha y hora de que creación del archivo.

- `CTime m_mtime` La fecha y hora de que última modificación del archivo.

- `CTime m_atime` La fecha y hora por última vez acceso al archivo para leerlo.

- `ULONGLONG m_size` El tamaño lógico del archivo en bytes, devuelto por el comando DIR.

- `BYTE m_attribute` El byte de atributo del archivo.

- `char m_szFullName[_MAX_PATH]` El nombre de archivo absoluta en el juego de caracteres de Windows.

*lpszFileName*<br/>
Es decir, una cadena en el carácter de Windows establece la ruta de acceso al archivo deseado. La ruta de acceso puede ser absoluta o relativa, o puede contener un nombre de ruta de acceso de red.

*pTM*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="return-value"></a>Valor devuelto

TRUE si la información de estado para el archivo especificado se obtiene correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

La versión no estáticos de `GetStatus` recupera información de estado del archivo abierto asociado a la determinada `CFile` objeto.  La versión estática de `GetStatus` Obtiene el estado del archivo de una ruta de acceso de archivo determinado sin necesidad de abrir el archivo. Esta versión es útil para probar la existencia y derechos de acceso de un archivo.

El `m_attribute` miembro de la `CFileStatus` estructura hace referencia al conjunto de atributos de archivo. El `CFile` clase proporciona el **atributo** tipo de enumeración, por lo que se pueden especificar atributos de archivo simbólicamente:

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

Determina la presencia de un identificador de archivo válido para el `CFile` objeto.

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>Comentarios

Esta constante se usa para determinar si el `CFile` objeto tiene un identificador de archivo válido.

El ejemplo siguiente muestra esta operación:

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

##  <a name="lockrange"></a>  CFile::LockRange

Bloquea un intervalo de bytes en un archivo abierto, producir una excepción si el archivo ya está bloqueado.

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Parámetros

*dwPos*<br/>
El desplazamiento de bytes del inicio del intervalo de bytes a bloquear.

*dwCount*<br/>
El número de bytes del intervalo que se va a bloquear.

### <a name="remarks"></a>Comentarios

El bloqueo de bytes en un archivo impide que otros procesos obtengan acceso a dichos bytes. Puede bloquear más de una región de un archivo, pero no se permite ninguna región que se superponen.

Al desbloquear la región mediante la `UnlockRange` función miembro, el intervalo de bytes debe corresponder exactamente con la región que se ha bloqueado anteriormente. El `LockRange` función no combina regiones adyacentes. Si dos regiones bloqueadas son adyacentes, se debe desbloquear por separado cada región.

> [!NOTE]
>  Esta función no está disponible para el `CMemFile`-clase derivada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="m_hfile"></a>  CFile::m_hFile

Contiene el identificador de archivo del sistema operativo de un archivo abierto.

```
HANDLE m_hFile;
```

### <a name="remarks"></a>Comentarios

`m_hFile` es una variable pública de tipo UINT. Contiene `CFile::hFileNull`, un indicador de archivo vacío independiente del sistema operativo, si no se ha asignado el identificador.

El uso de `m_hFile` no se recomienda porque el significado del miembro depende de la clase derivada. `m_hFile` se realiza a un miembro público para su comodidad en auxiliares no son polimórficos el uso de la clase.

##  <a name="m_ptm"></a>  CFile::m_pTM

Puntero a un `CAtlTransactionManager` objeto.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Comentarios

##  <a name="open"></a>  CFile::Open

Sobrecargado. `Open` está diseñado para su uso con el valor predeterminado `CFile` constructor.

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
Una cadena que contiene la ruta de acceso al archivo deseado. La ruta de acceso puede ser un nombre de red (UNC), absoluta o relativa.

*nOpenFlags*<br/>
Un tipo UINT que define el modo de acceso y uso compartido del archivo. Especifica la acción que se realizará al abrir el archivo. Puede combinar las opciones mediante el uso de la operación bit a bit OR ( **&#124;** ) operador. Permiso de acceso uno a y un recurso compartido de opción son necesarios; el `modeCreate` y `modeNoInherit` modos son opcionales. Consulte la [CFile](#cfile) constructor para obtener una lista de opciones de modo.

*pError*<br/>
Un puntero a un objeto de excepción de archivo existente que va a recibir el estado de una operación con errores.

*pTM*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la apertura se realizó correctamente; en caso contrario, es 0. El *pError* parámetro solo es significativo si se devuelve 0.

### <a name="remarks"></a>Comentarios

Los dos `Open` funciones son métodos "seguros" para abrir un archivo, donde es una condición normal, se esperaba un error.

Mientras el `CFile` constructor produce una excepción en una condición de error, `Open` devuelve FALSE para las condiciones de error. `Open` todavía puede inicializar un [CFileException](../../mfc/reference/cfileexception-class.md) objeto para describir el error, sin embargo. Si no se proporciona el *pError* parámetro, o si se pasa NULL para *pError*, `Open` devuelve FALSE y no produce una excepción una `CFileException`. Si se pasa un puntero a una existente `CFileException`, y `Open` encuentra un error, la función rellena con información que describe ese error. `Open` no genere una excepción en cualquier caso.

La tabla siguiente describen los posibles resultados de `Open`.

|`pError`|Se encontró un error|Valor devuelto|CFileException contenido|
|--------------|------------------------|------------------|----------------------------|
|NULL|No|true|N/D|
|PTR para `CFileException`|No|true|sin cambios|
|NULL|Sí|false|N/D|
|PTR para `CFileException`|Sí|false|inicializar para describir el error|

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

##  <a name="operator_handle"></a>  CFile::operator identificador

Utilice este operador para pasar un identificador de un `CFile` de objeto a funciones como [ReadFileEx](/windows/desktop/api/fileapi/nf-fileapi-readfileex) y [GetFileTime](/windows/desktop/api/fileapi/nf-fileapi-getfiletime) que esperan un `HANDLE`.

```
operator HANDLE() const;
```

##  <a name="read"></a>  CFile::Read

Lee los datos en un búfer desde el archivo asociado con el `CFile` objeto.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Puntero al búfer proporcionado por el usuario que va a recibir los datos leídos desde el archivo.

*nCount*<br/>
El número máximo de bytes que se leen desde el archivo. Para los archivos del modo de texto, los pares de retorno de carro se cuentan como caracteres individuales.

### <a name="return-value"></a>Valor devuelto

Número de bytes que se transfieren al búfer. Para todos los `CFile` clases, el valor devuelto puede ser menor que *nCount* si se alcanzó el final del archivo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

Para obtener otro ejemplo, vea [CFile::Open](#open).

##  <a name="remove"></a>  CFile::Remove

Esta función estática elimina el archivo especificado por la ruta de acceso.

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszFileName*<br/>
Cadena que es la ruta de acceso al archivo deseado. La ruta de acceso puede ser absoluta o relativa y puede contener un nombre de red.

*pTM*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="remarks"></a>Comentarios

`Remove` No quite un directorio.

El `Remove` función miembro produce una excepción si el archivo conectado está abierto o si no se puede quitar el archivo. Esta función es equivalente al DEL comando.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

##  <a name="rename"></a>  CFile::Rename

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

No se puede cambiar el nombre de directorios. Esta función es equivalente al comando REN.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

##  <a name="seek"></a>  CFile::Seek

Recoloca el puntero de archivo en un archivo abierto.

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>Parámetros

*lOff*<br/>
Número de bytes para mover el puntero de archivo. Los valores positivos mueven el puntero de archivo hacia el final del archivo; los valores negativos mueven el puntero de archivo hacia el principio del archivo.

*nFrom*<br/>
Posición para buscar desde. Consulte la sección Comentarios para los valores posibles.

### <a name="return-value"></a>Valor devuelto

La posición del puntero del archivo si el método se realizó correctamente; en caso contrario, el valor devuelto es indefinido y un puntero a un `CFileException` es una excepción.

### <a name="remarks"></a>Comentarios

En la tabla siguiente se enumera los valores posibles para el *nde* parámetro.

|Valor|Descripción|
|-----------|-----------------|
|`CFile::begin`|Buscar desde el principio del archivo.|
|`CFile::current`|Buscar desde la ubicación actual del puntero del archivo.|
|`CFile::end`|Buscar desde el final del archivo.|

Cuando se abre un archivo, se coloca el puntero de archivo en 0, el inicio del archivo.

Puede establecer el puntero de archivo a una posición más allá del final de un archivo. Si lo hace, no aumenta el tamaño del archivo hasta que escriben en el archivo.

El controlador de excepciones para este método debe eliminar el objeto de excepción después de procesa la excepción.

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

Establece el valor del puntero de archivo al final del archivo lógico.

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

Llame a esta función para especificar la ruta de acceso del archivo. Por ejemplo, si la ruta de acceso de un archivo no está disponible cuando una [CFile](../../mfc/reference/cfile-class.md) se construye el objeto, llame a `SetFilePath` para proporcionarla.

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parámetros

*lpszNewName*<br/>
Puntero a una cadena que especifica la ruta de acceso nuevo.

### <a name="remarks"></a>Comentarios

> [!NOTE]
> `SetFilePath` no se abra el archivo o crear el archivo. simplemente asocia el `CFile` objeto con un nombre de ruta de acceso, que, a continuación, se puede usar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

##  <a name="setlength"></a>  CFile::SetLength

Llame a esta función para cambiar la longitud del archivo.

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>Parámetros

*dwNewLen*<br/>
Longitud deseada del archivo en bytes. Este valor puede ser mayor o menor que la longitud actual del archivo. El archivo se se amplíe o trunca según corresponda.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Con `CMemFile`, esta función puede producir un `CMemoryException` objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

##  <a name="setstatus"></a>  CFile::SetStatus

Establece el estado de archivo asociado a esta ubicación de archivo.

```
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,
    const CFileStatus& status,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszFileName*<br/>
Cadena que es la ruta de acceso al archivo deseado. La ruta de acceso puede ser absoluta o relativa y puede contener un nombre de red.

*status*<br/>
El búfer que contiene la nueva información de estado. Llame a la `GetStatus` función miembro para rellenar previamente el `CFileStatus` estructura con los valores actuales y, después, realizar cambios según sea necesario. Si un valor es 0, no se actualiza el elemento de estado correspondiente. Consulte la [GetStatus](#getstatus) función miembro para obtener una descripción de la `CFileStatus` estructura.

*pTM*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="remarks"></a>Comentarios

Para establecer el tiempo, modifique la `m_mtime` campo de *estado*.

Al realizar una llamada a `SetStatus` en un intento para cambiar únicamente los atributos del archivo y el `m_mtime` miembro de la estructura de estado de archivo es distinto de cero, también puede afectar los atributos (cambiar la hora marca puede tener efectos en los atributos). Si desea cambiar solo los atributos del archivo, establezca primero la `m_mtime` miembro de la estructura de estado de archivo en cero y, a continuación, realice una llamada a `SetStatus`.

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
El desplazamiento de bytes del inicio del intervalo de bytes a desbloquear.

*dwCount*<br/>
El número de bytes del intervalo que se va a desbloquear.

### <a name="remarks"></a>Comentarios

Vea la descripción de la [LockRange](#lockrange) función miembro para obtener más información.

> [!NOTE]
>  Esta función no está disponible para el `CMemFile`-clase derivada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="write"></a>  CFile::Write

Escribe datos de un búfer en el archivo asociado con el `CFile` objeto.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parámetros

*lpBuf*<br/>
Un puntero al búfer proporcionado por el usuario que contiene los datos se escriban en el archivo.

*nCount*<br/>
El número de bytes que se transfieren desde el búfer. Para los archivos del modo de texto, los pares de retorno de carro se cuentan como caracteres individuales.

### <a name="remarks"></a>Comentarios

`Write` produce una excepción en respuesta a varias condiciones, incluidas la condición de disco lleno.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

Consulte también los ejemplos de [CFile::CFile](#cfile) y [CFile::Open](#open).

## <a name="see-also"></a>Vea también

[Ejemplo de MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CStdioFile (clase)](../../mfc/reference/cstdiofile-class.md)<br/>
[CMemFile (clase)](../../mfc/reference/cmemfile-class.md)
