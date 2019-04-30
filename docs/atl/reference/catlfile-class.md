---
title: CAtlFile (clase)
ms.date: 11/04/2016
f1_keywords:
- CAtlFile
- ATLFILE/ATL::CAtlFile
- ATLFILE/ATL::CAtlFile::CAtlFile
- ATLFILE/ATL::CAtlFile::Create
- ATLFILE/ATL::CAtlFile::Flush
- ATLFILE/ATL::CAtlFile::GetOverlappedResult
- ATLFILE/ATL::CAtlFile::GetPosition
- ATLFILE/ATL::CAtlFile::GetSize
- ATLFILE/ATL::CAtlFile::LockRange
- ATLFILE/ATL::CAtlFile::Read
- ATLFILE/ATL::CAtlFile::Seek
- ATLFILE/ATL::CAtlFile::SetSize
- ATLFILE/ATL::CAtlFile::UnlockRange
- ATLFILE/ATL::CAtlFile::Write
- ATLFILE/ATL::CAtlFile::m_pTM
helpviewer_keywords:
- CAtlFile class
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
ms.openlocfilehash: 0faae50afcd26948bdcb4d4333efb25d5cca33ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260232"
---
# <a name="catlfile-class"></a>CAtlFile (clase)

Esta clase proporciona un contenedor fino alrededor de la Windows API de administración de archivos.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
class CAtlFile : public CHandle
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlFile::CAtlFile](#catlfile)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlFile::Create](#create)|Llame a este método para crear o abrir un archivo.|
|[CAtlFile::Flush](#flush)|Llame a este método para borrar los búferes para el archivo y hacer que todos los datos almacenados en búfer se escriban en el archivo.|
|[CAtlFile::GetOverlappedResult](#getoverlappedresult)|Llame a este método para obtener los resultados de una operación superpuesta en el archivo.|
|[CAtlFile::GetPosition](#getposition)|Llame a este método para obtener la posición actual del puntero de archivo del archivo.|
|[CAtlFile::GetSize](#getsize)|Llame a este método para obtener el tamaño en bytes del archivo.|
|[CAtlFile::LockRange](#lockrange)|Llame a este método para bloquear una región en el archivo para evitar que otros procesos tengan acceso a él.|
|[CAtlFile::Read](#read)|Llame a este método para leer datos desde un archivo a partir de la posición indicada por el puntero de archivo.|
|[CAtlFile::Seek](#seek)|Llame a este método para mover el puntero de archivo del archivo.|
|[CAtlFile::SetSize](#setsize)|Llame a este método para establecer el tamaño del archivo.|
|[CAtlFile::UnlockRange](#unlockrange)|Llame a este método para desbloquear una región del archivo.|
|[CAtlFile::Write](#write)|Llame a este método para escribir datos en el archivo en la posición indicada por el puntero de archivo.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Name|Descripción|
|----------|-----------------|
|[CAtlFile::m_pTM](#m_ptm)|Puntero a `CAtlTransactionManager` objeto|

## <a name="remarks"></a>Comentarios

Utilice esta clase cuando las necesidades de administración de archivos son relativamente simples, pero más de abstracción que proporciona la API de Windows es necesario, sin incluir las dependencias MFC.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CHandle](../../atl/reference/chandle-class.md)

`CAtlFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlfile.h

##  <a name="catlfile"></a>  CAtlFile::CAtlFile

El constructor.

```
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```

### <a name="parameters"></a>Parámetros

*file*<br/>
El objeto de archivo.

*hFile*<br/>
El identificador de archivo.

*pTM*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="remarks"></a>Comentarios

El constructor de copias transfiere la propiedad del identificador del archivo de los originales `CAtlFile` objeto para el objeto recién creado.

##  <a name="create"></a>  CAtlFile::Create

Llame a este método para crear o abrir un archivo.

```
HRESULT Create(
    LPCTSTR szFilename,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes = FILE_ATTRIBUTE_NORMAL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    HANDLE hTemplateFile = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*szFilename*<br/>
Nombre del archivo.

*dwDesiredAccess*<br/>
El acceso deseado. Consulte *dwDesiredAccess* en [CreateFile](/windows/desktop/api/fileapi/nf-fileapi-createfilea) en el SDK de Windows.

*dwShareMode*<br/>
El modo de uso compartido. Consulte *dwShareMode* en `CreateFile`.

*dwCreationDisposition*<br/>
La disposición de creación. Consulte *dwCreationDisposition* en `CreateFile`.

*dwFlagsAndAttributes*<br/>
Las marcas y los atributos. Consulte *dwFlagsAndAttributes* en `CreateFile`.

*lpsa*<br/>
Los atributos de seguridad. Consulte *lpSecurityAttributes* en `CreateFile`.

*hTemplateFile*<br/>
El archivo de plantilla. Consulte *hTemplateFile* en `CreateFile`.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Las llamadas [CreateFile](/windows/desktop/api/fileapi/nf-fileapi-createfilea) para crear o abrir el archivo.

##  <a name="flush"></a>  CAtlFile::Flush

Llame a este método para borrar los búferes para el archivo y hacer que todos los datos almacenados en búfer se escriban en el archivo.

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Las llamadas [FlushFileBuffers](/windows/desktop/api/fileapi/nf-fileapi-flushfilebuffers) vaciar datos almacenados en búfer en el archivo.

##  <a name="getoverlappedresult"></a>  CAtlFile::GetOverlappedResult

Llame a este método para obtener los resultados de una operación superpuesta en el archivo.

```
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```

### <a name="parameters"></a>Parámetros

*pOverlapped*<br/>
La estructura superpuesta. Consulte *lpOverlapped* en [GetOverlappedResult](/windows/desktop/api/ioapiset/nf-ioapiset-getoverlappedresult) en el SDK de Windows.

*dwBytesTransferred*<br/>
Los bytes transfieren. Consulte *lpNumberOfBytesTransferred* en `GetOverlappedResult`.

*bWait*<br/>
La opción de espera. Consulte *bWait* en `GetOverlappedResult`.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Las llamadas [GetOverlappedResult](/windows/desktop/api/ioapiset/nf-ioapiset-getoverlappedresult) para obtener los resultados de una operación superpuesta en el archivo.

##  <a name="getposition"></a>  CAtlFile::GetPosition

Llame a este método para obtener la posición actual del puntero de archivo.

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
La posición en bytes.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Las llamadas [SetFilePointer](/windows/desktop/api/fileapi/nf-fileapi-setfilepointer) para obtener la posición actual del puntero de archivo.

##  <a name="getsize"></a>  CAtlFile::GetSize

Llame a este método para obtener el tamaño en bytes del archivo.

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Parámetros

*nLen*<br/>
El número de bytes en el archivo.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Las llamadas [GetFileSize](/windows/desktop/api/fileapi/nf-fileapi-getfilesize) para obtener el tamaño en bytes del archivo.

##  <a name="lockrange"></a>  CAtlFile::LockRange

Llame a este método para bloquear una región en el archivo para evitar que otros procesos tengan acceso a él.

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
La posición en el archivo donde debe comenzar el bloqueo.

*nCount*<br/>
La longitud del intervalo de bytes se bloquee.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Las llamadas [encontraba](/windows/desktop/api/fileapi/nf-fileapi-lockfile) bloquear una región en el archivo. El bloqueo de bytes en un archivo impide que otros procesos obtengan acceso a dichos bytes. Puede bloquear más de una región de un archivo, pero no se permite ninguna región que se superponen. Al desbloquear una región, utilizando [CAtlFile::UnlockRange](#unlockrange), el intervalo de bytes debe corresponder exactamente con la región que se ha bloqueado anteriormente. `LockRange` no combina regiones adyacentes; Si dos regiones bloqueadas son adyacentes, debe desbloquear cada uno por separado.

##  <a name="m_ptm"></a>  CAtlFile::m_pTM

Puntero a un `CAtlTransactionManager` objeto.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Comentarios

##  <a name="read"></a>  CAtlFile::Read

Llame a este método para leer datos desde un archivo a partir de la posición indicada por el puntero de archivo.

```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();
```

### <a name="parameters"></a>Parámetros

*pBuffer*<br/>
Puntero al búfer que recibirá los datos leídos desde el archivo.

*nBufSize*<br/>
El tamaño del búfer en bytes.

*nBytesRead*<br/>
Número de bytes leídos.

*pOverlapped*<br/>
La estructura superpuesta. Consulte *lpOverlapped* en [ReadFile](/windows/desktop/api/fileapi/nf-fileapi-readfile) en el SDK de Windows.

*pfnCompletionRoutine*<br/>
La rutina de finalización. Consulte *lpCompletionRoutine* en [ReadFileEx](/windows/desktop/api/fileapi/nf-fileapi-readfileex) en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Llamar los tres primeros formularios [ReadFile](/windows/desktop/api/fileapi/nf-fileapi-readfile), la última [ReadFileEx](/windows/desktop/api/fileapi/nf-fileapi-readfileex) para leer datos desde el archivo. Use [CAtlFile::Seek](#seek) para mover el puntero de archivo.

##  <a name="seek"></a>  CAtlFile::Seek

Llame a este método para mover el puntero de archivo del archivo.

```
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Parámetros

*nOffset*<br/>
El desplazamiento desde el punto inicial dado por *dwFrom*.

*dwFrom*<br/>
El punto de partida (FILE_BEGIN, FILE_CURRENT o FILE_END).

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Las llamadas [SetFilePointer](/windows/desktop/api/fileapi/nf-fileapi-setfilepointer) para mover el puntero de archivo.

##  <a name="setsize"></a>  CAtlFile::SetSize

Llame a este método para establecer el tamaño del archivo.

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Parámetros

*nNewLen*<br/>
La nueva longitud del archivo en bytes.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Las llamadas [SetFilePointer](/windows/desktop/api/fileapi/nf-fileapi-setfilepointer) y [SetEndOfFile](/windows/desktop/api/fileapi/nf-fileapi-setendoffile) para establecer el tamaño del archivo. Si la devolución, el puntero de archivo se coloca al final del archivo.

##  <a name="unlockrange"></a>  CAtlFile::UnlockRange

Llame a este método para desbloquear una región del archivo.

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
La posición en el archivo donde debe comenzar el desbloqueo.

*nCount*<br/>
La longitud de desbloquea el intervalo de bytes.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Las llamadas [UnlockFile](/windows/desktop/api/fileapi/nf-fileapi-unlockfile) para desbloquear una región del archivo.

##  <a name="write"></a>  CAtlFile::Write

Llame a este método para escribir datos en el archivo en la posición indicada por el puntero de archivo.

```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();
```

### <a name="parameters"></a>Parámetros

*pBuffer*<br/>
El búfer que contiene los datos se escriban en el archivo.

*nBufSize*<br/>
El número de bytes que se transfieren desde el búfer.

*pOverlapped*<br/>
La estructura superpuesta. Consulte *lpOverlapped* en [WriteFile](/windows/desktop/api/fileapi/nf-fileapi-writefile) en el SDK de Windows.

*pfnCompletionRoutine*<br/>
La rutina de finalización. Consulte *lpCompletionRoutine* en [WriteFileEx](/windows/desktop/api/fileapi/nf-fileapi-writefileex) en el SDK de Windows.

*pnBytesWritten*<br/>
Bytes escritos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Llamar los tres primeros formularios [WriteFile](/windows/desktop/api/fileapi/nf-fileapi-writefile), las llamadas de la última [WriteFileEx](/windows/desktop/api/fileapi/nf-fileapi-writefileex) para escribir datos en el archivo. Use [CAtlFile::Seek](#seek) para mover el puntero de archivo.

## <a name="see-also"></a>Vea también

[Ejemplo de marquesina](../../overview/visual-cpp-samples.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[CHandle (clase)](../../atl/reference/chandle-class.md)
