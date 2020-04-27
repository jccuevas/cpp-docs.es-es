---
title: Clase CAtlFile
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
ms.openlocfilehash: 83a0a89bf6e2e21be33cf8c6003228111eff5394
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168116"
---
# <a name="catlfile-class"></a>Clase CAtlFile

Esta clase proporciona un contenedor fino en torno a la API de control de archivos de Windows.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```cpp
class CAtlFile : public CHandle
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlFile::CAtlFile](#catlfile)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlFile:: Create](#create)|Llame a este método para crear o abrir un archivo.|
|[CAtlFile:: Flush](#flush)|Llame a este método para borrar los búferes del archivo y hacer que todos los datos almacenados en el búfer se escriban en el archivo.|
|[CAtlFile::GetOverlappedResult](#getoverlappedresult)|Llame a este método para obtener los resultados de una operación superpuesta en el archivo.|
|[CAtlFile:: GetPosition](#getposition)|Llame a este método para obtener la posición del puntero de archivo actual a partir del archivo.|
|[CAtlFile:: obtiene](#getsize)|Llame a este método para obtener el tamaño en bytes del archivo.|
|[CAtlFile::LockRange](#lockrange)|Llame a este método para bloquear una región del archivo a fin de evitar que otros procesos tengan acceso a ella.|
|[CAtlFile:: Read](#read)|Llame a este método para leer los datos de un archivo a partir de la posición indicada por el puntero de archivo.|
|[CAtlFile:: Seek](#seek)|Llame a este método para desplace el puntero de archivo del archivo.|
|[CAtlFile:: setSize](#setsize)|Llame a este método para establecer el tamaño del archivo.|
|[CAtlFile::UnlockRange](#unlockrange)|Llame a este método para desbloquear una región del archivo.|
|[CAtlFile:: Write](#write)|Llame a este método para escribir datos en el archivo a partir de la posición indicada por el puntero de archivo.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlFile:: m_pTM](#m_ptm)|Puntero a `CAtlTransactionManager` objeto|

## <a name="remarks"></a>Observaciones

Utilice esta clase cuando las necesidades de control de archivos son relativamente sencillas, pero se requiere más abstracción de la que proporciona la API de Windows, sin incluir dependencias de MFC.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CHandle](../../atl/reference/chandle-class.md)

`CAtlFile`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlfile. h

## <a name="catlfilecatlfile"></a><a name="catlfile"></a>CAtlFile::CAtlFile

El constructor.

```cpp
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```

### <a name="parameters"></a>Parámetros

*filesystem*<br/>
Objeto de archivo.

*hFile*<br/>
Identificador de archivo.

*pTM*<br/>
Puntero al objeto CAtlTransactionManager

### <a name="remarks"></a>Observaciones

El constructor de copias transfiere la propiedad del identificador de archivo del `CAtlFile` objeto original al objeto recién construido.

## <a name="catlfilecreate"></a><a name="create"></a>CAtlFile:: Create

Llame a este método para crear o abrir un archivo.

```cpp
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
El nombre del archivo.

*dwDesiredAccess*<br/>
El acceso deseado. Vea *dwDesiredAccess* en [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) en el Windows SDK.

*dwShareMode*<br/>
Modo de uso compartido. Vea *dwShareMode* en `CreateFile`.

*dwCreationDisposition*<br/>
Disposición de creación. Vea *dwCreationDisposition* en `CreateFile`.

*dwFlagsAndAttributes*<br/>
Marcas y atributos. Vea *dwFlagsAndAttributes* en `CreateFile`.

*lpsa*<br/>
Atributos de seguridad. Vea *lpSecurityAttributes* en `CreateFile`.

*hTemplateFile*<br/>
El archivo de plantilla. Vea *hTemplateFile* en `CreateFile`.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Llama a [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) para crear o abrir el archivo.

## <a name="catlfileflush"></a><a name="flush"></a>CAtlFile:: Flush

Llame a este método para borrar los búferes del archivo y hacer que todos los datos almacenados en el búfer se escriban en el archivo.

```cpp
HRESULT Flush() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Llama a [FlushFileBuffers](/windows/win32/api/fileapi/nf-fileapi-flushfilebuffers) para vaciar los datos almacenados en búfer en el archivo.

## <a name="catlfilegetoverlappedresult"></a><a name="getoverlappedresult"></a>CAtlFile::GetOverlappedResult

Llame a este método para obtener los resultados de una operación superpuesta en el archivo.

```cpp
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```

### <a name="parameters"></a>Parámetros

*pOverlapped*<br/>
Estructura superpuesta. Consulte *lpOverlapped* en [GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult) en el Windows SDK.

*dwBytesTransferred*<br/>
Bytes transferidos. Vea *lpNumberOfBytesTransferred* en `GetOverlappedResult`.

*bWait*<br/>
Opción wait. Vea *bWait* en `GetOverlappedResult`.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Llama a [GetOverlappedResult](/windows/win32/api/ioapiset/nf-ioapiset-getoverlappedresult) para obtener los resultados de una operación superpuesta en el archivo.

## <a name="catlfilegetposition"></a><a name="getposition"></a>CAtlFile:: GetPosition

Llame a este método para obtener la posición del puntero de archivo actual.

```cpp
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Posición en bytes.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Llama a [SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) para obtener la posición del puntero de archivo actual.

## <a name="catlfilegetsize"></a><a name="getsize"></a>CAtlFile:: obtiene

Llame a este método para obtener el tamaño en bytes del archivo.

```cpp
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Parámetros

*nLen*<br/>
Número de bytes del archivo.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Llama a [GetFileSize](/windows/win32/api/fileapi/nf-fileapi-getfilesize) para obtener el tamaño en bytes del archivo.

## <a name="catlfilelockrange"></a><a name="lockrange"></a>CAtlFile::LockRange

Llame a este método para bloquear una región del archivo a fin de evitar que otros procesos tengan acceso a ella.

```cpp
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Posición en el archivo donde debe comenzar el bloqueo.

*nCount*<br/>
Longitud del intervalo de bytes que se va a bloquear.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Llama a [LockFile](/windows/win32/api/fileapi/nf-fileapi-lockfile) para bloquear una región en el archivo. El bloqueo de bytes en un archivo impide que otros procesos obtengan acceso a dichos bytes. Puede bloquear más de una región de un archivo, pero no se permiten regiones superpuestas. Al desbloquear una región, mediante [CAtlFile:: UnlockRange](#unlockrange), el intervalo de bytes debe corresponderse exactamente con la región que se bloqueó previamente. `LockRange`no combina regiones adyacentes; Si dos regiones bloqueadas son adyacentes, debe desbloquear cada una de ellas por separado.

## <a name="catlfilem_ptm"></a><a name="m_ptm"></a>CAtlFile:: m_pTM

Puntero a un `CAtlTransactionManager` objeto.

```cpp
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Observaciones

## <a name="catlfileread"></a><a name="read"></a>CAtlFile:: Read

Llame a este método para leer los datos de un archivo a partir de la posición indicada por el puntero de archivo.

```cpp
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
Puntero al búfer que recibirá los datos leídos del archivo.

*nBufSize*<br/>
El tamaño del búfer en bytes.

*nBytesRead*<br/>
El número de bytes leídos.

*pOverlapped*<br/>
Estructura superpuesta. Vea *lpOverlapped* en [ReadFile](/windows/win32/api/fileapi/nf-fileapi-readfile) en el Windows SDK.

*pfnCompletionRoutine*<br/>
La rutina de finalización. Consulte *lpCompletionRoutine* en [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Los tres primeros formularios llaman a [readfile](/windows/win32/api/fileapi/nf-fileapi-readfile), el último [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) para leer los datos del archivo. Use [CAtlFile:: Seek](#seek) para desplace el puntero de archivo.

## <a name="catlfileseek"></a><a name="seek"></a>CAtlFile:: Seek

Llame a este método para desplace el puntero de archivo del archivo.

```cpp
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Parámetros

*nOffset*<br/>
Desplazamiento desde el punto inicial proporcionado por *dwFrom*.

*dwFrom*<br/>
Punto inicial (FILE_BEGIN, FILE_CURRENT o FILE_END).

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Llama a [SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) para desplace el puntero de archivo.

## <a name="catlfilesetsize"></a><a name="setsize"></a>CAtlFile:: setSize

Llame a este método para establecer el tamaño del archivo.

```cpp
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Parámetros

*nNewLen*<br/>
La nueva longitud del archivo en bytes.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Llama a [SetFilePointer](/windows/win32/api/fileapi/nf-fileapi-setfilepointer) y [SetEndOfFile](/windows/win32/api/fileapi/nf-fileapi-setendoffile) para establecer el tamaño del archivo. En la devolución, el puntero de archivo se coloca al final del archivo.

## <a name="catlfileunlockrange"></a><a name="unlockrange"></a>CAtlFile::UnlockRange

Llame a este método para desbloquear una región del archivo.

```cpp
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Posición en el archivo donde debe comenzar el desbloqueo.

*nCount*<br/>
Longitud del intervalo de bytes que se va a desbloquear.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Llama a [UnlockFile](/windows/win32/api/fileapi/nf-fileapi-unlockfile) para desbloquear una región del archivo.

## <a name="catlfilewrite"></a><a name="write"></a>CAtlFile:: Write

Llame a este método para escribir datos en el archivo a partir de la posición indicada por el puntero de archivo.

```cpp
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
Búfer que contiene los datos que se van a escribir en el archivo.

*nBufSize*<br/>
Número de bytes que se van a transferir desde el búfer.

*pOverlapped*<br/>
Estructura superpuesta. Vea *lpOverlapped* en [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile) en el Windows SDK.

*pfnCompletionRoutine*<br/>
La rutina de finalización. Consulte *lpCompletionRoutine* en [WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex) en el Windows SDK.

*pnBytesWritten*<br/>
Bytes escritos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Los tres primeros formularios llaman a [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile), el último llama a [WriteFileEx](/windows/win32/api/fileapi/nf-fileapi-writefileex) para escribir datos en el archivo. Use [CAtlFile:: Seek](#seek) para desplace el puntero de archivo.

## <a name="see-also"></a>Consulte también

[Ejemplo de marquesina](../../overview/visual-cpp-samples.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clase CHandle](../../atl/reference/chandle-class.md)
