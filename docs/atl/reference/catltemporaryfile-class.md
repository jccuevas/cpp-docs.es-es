---
title: Clase CAtlTemporaryFile
ms.date: 11/04/2016
f1_keywords:
- CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::Close
- ATLFILE/ATL::CAtlTemporaryFile::Create
- ATLFILE/ATL::CAtlTemporaryFile::Flush
- ATLFILE/ATL::CAtlTemporaryFile::GetPosition
- ATLFILE/ATL::CAtlTemporaryFile::GetSize
- ATLFILE/ATL::CAtlTemporaryFile::HandsOff
- ATLFILE/ATL::CAtlTemporaryFile::HandsOn
- ATLFILE/ATL::CAtlTemporaryFile::LockRange
- ATLFILE/ATL::CAtlTemporaryFile::Read
- ATLFILE/ATL::CAtlTemporaryFile::Seek
- ATLFILE/ATL::CAtlTemporaryFile::SetSize
- ATLFILE/ATL::CAtlTemporaryFile::TempFileName
- ATLFILE/ATL::CAtlTemporaryFile::UnlockRange
- ATLFILE/ATL::CAtlTemporaryFile::Write
helpviewer_keywords:
- CAtlTemporaryFile class
ms.assetid: 05f0f2a5-94f6-4594-8dae-b114292ff5f9
ms.openlocfilehash: d6a7a61d1886a264f8575e8d7325d6639d21338d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497711"
---
# <a name="catltemporaryfile-class"></a>Clase CAtlTemporaryFile

Esta clase proporciona métodos para la creación y el uso de un archivo temporal.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CAtlTemporaryFile
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|El constructor.|
|[CAtlTemporaryFile::~CAtlTemporaryFile](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAtlTemporaryFile::Close](#close)|Llame a este método para cerrar un archivo temporal y eliminar su contenido o almacenarlo en el nombre de archivo especificado.|
|[CAtlTemporaryFile::Create](#create)|Llame a este método para crear un archivo temporal.|
|[CAtlTemporaryFile::Flush](#flush)|Llame a este método para forzar que los datos restantes en el búfer de archivos se escriban en el archivo temporal.|
|[CAtlTemporaryFile::GetPosition](#getposition)|Llame a este método para obtener la posición del puntero de archivo actual.|
|[CAtlTemporaryFile::GetSize](#getsize)|Llame a este método para obtener el tamaño en bytes del archivo temporal.|
|[CAtlTemporaryFile::HandsOff](#handsoff)|Llame a este método para desasociar el `CAtlTemporaryFile` archivo del objeto.|
|[CAtlTemporaryFile::HandsOn](#handson)|Llame a este método para abrir un archivo temporal existente y colocar el puntero al final del archivo.|
|[CAtlTemporaryFile::LockRange](#lockrange)|Llame a este método para bloquear una región del archivo a fin de evitar que otros procesos tengan acceso a ella.|
|[CAtlTemporaryFile::Read](#read)|Llame a este método para leer los datos del archivo temporal a partir de la posición indicada por el puntero de archivo.|
|[CAtlTemporaryFile::Seek](#seek)|Llame a este método para desplace el puntero de archivo del archivo temporal.|
|[CAtlTemporaryFile::SetSize](#setsize)|Llame a este método para establecer el tamaño del archivo temporal.|
|[CAtlTemporaryFile::TempFileName](#tempfilename)|Llame a este método para devolver el nombre del archivo temporal.|
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|Llame a este método para desbloquear una región del archivo temporal.|
|[CAtlTemporaryFile::Write](#write)|Llame a este método para escribir datos en el archivo temporal a partir de la posición indicada por el puntero de archivo.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAtlTemporaryFile:: Operator (identificador)](#operator_handle)|Devuelve un identificador para el archivo temporal.|

## <a name="remarks"></a>Comentarios

`CAtlTemporaryFile`facilita la creación y el uso de un archivo temporal. El archivo se denomina, se abre, se cierra y se elimina automáticamente. Si el contenido del archivo es necesario después de cerrar el archivo, se puede guardar en un archivo nuevo con un nombre especificado.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlfile. h

## <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

##  <a name="catltemporaryfile"></a>  CAtlTemporaryFile::CAtlTemporaryFile

El constructor.

```
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Comentarios

Un archivo no se abre realmente hasta que se realiza una llamada a [CAtlTemporaryFile:: Create](#create).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

##  <a name="dtor"></a>  CAtlTemporaryFile::~CAtlTemporaryFile

Destructor.

```
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Comentarios

El destructor llama a [CAtlTemporaryFile:: Close](#close).

##  <a name="close"></a>  CAtlTemporaryFile::Close

Llame a este método para cerrar un archivo temporal y eliminar su contenido o almacenarlo en el nombre de archivo especificado.

```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*szNewName*<br/>
Nombre del nuevo archivo en el que se va a almacenar el contenido del archivo temporal. Si este argumento es NULL, se elimina el contenido del archivo temporal.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

##  <a name="create"></a>  CAtlTemporaryFile::Create

Llame a este método para crear un archivo temporal.

```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>Parámetros

*pszDir*<br/>
Ruta de acceso del archivo temporal. Si es NULL, se llamará a [GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppathw) para asignar una ruta de acceso.

*dwDesiredAccess*<br/>
El acceso deseado. Vea *dwDesiredAccess* en [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

##  <a name="flush"></a>  CAtlTemporaryFile::Flush

Llame a este método para forzar que los datos restantes en el búfer de archivos se escriban en el archivo temporal.

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Similar a [CAtlTemporaryFile:: HandsOff](#handsoff), salvo que el archivo no está cerrado.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

##  <a name="getposition"></a>  CAtlTemporaryFile::GetPosition

Llame a este método para obtener la posición del puntero de archivo actual.

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Posición en bytes.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Para cambiar la posición del puntero de archivo, use [CAtlTemporaryFile:: Seek](#seek).

##  <a name="getsize"></a>  CAtlTemporaryFile::GetSize

Llame a este método para obtener el tamaño en bytes del archivo temporal.

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Parámetros

*nLen*<br/>
Número de bytes del archivo.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

##  <a name="handsoff"></a>  CAtlTemporaryFile::HandsOff

Llame a este método para desasociar el `CAtlTemporaryFile` archivo del objeto.

```
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

`HandsOff`y [CAtlTemporaryFile:: Handon](#handson) se usa para desasociar el archivo del objeto y volver a adjuntarlo si es necesario. `HandsOff`forzará que los datos restantes en el búfer de archivos se escriban en el archivo temporal y, a continuación, cierre el archivo. Si desea cerrar y eliminar el archivo de forma permanente, o si desea cerrar y conservar el contenido del archivo con un nombre determinado, use [CAtlTemporaryFile:: Close](#close).

##  <a name="handson"></a>  CAtlTemporaryFile::HandsOn

Llame a este método para abrir un archivo temporal existente y colocar el puntero al final del archivo.

```
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

[CAtlTemporaryFile:: HandsOff](#handsoff) y `HandsOn` se usan para desasociar el archivo del objeto y volver a adjuntarlo si es necesario.

##  <a name="lockrange"></a>  CAtlTemporaryFile::LockRange

Llame a este método para bloquear una región en el archivo temporal para evitar que otros procesos tengan acceso a ella.

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Posición en el archivo donde debe comenzar el bloqueo.

*nCount*<br/>
Longitud del intervalo de bytes que se va a bloquear.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

El bloqueo de bytes en un archivo impide que otros procesos obtengan acceso a dichos bytes. Puede bloquear más de una región de un archivo, pero no se permiten regiones superpuestas. Para desbloquear correctamente una región, use [CAtlTemporaryFile:: UnlockRange](#unlockrange), asegurándose de que el intervalo de bytes corresponde exactamente a la región que se bloqueó previamente. `LockRange`no combina regiones adyacentes; Si dos regiones bloqueadas son adyacentes, debe desbloquear cada una de ellas por separado.

##  <a name="operator_handle"></a>CAtlTemporaryFile:: Operator (identificador)

Devuelve un identificador para el archivo temporal.

```
operator HANDLE() throw();
```

##  <a name="read"></a>  CAtlTemporaryFile::Read

Llame a este método para leer los datos del archivo temporal a partir de la posición indicada por el puntero de archivo.

```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```

### <a name="parameters"></a>Parámetros

*pBuffer*<br/>
Puntero al búfer que recibirá los datos leídos del archivo.

*nBufSize*<br/>
El tamaño del búfer en bytes.

*nBytesRead*<br/>
Número de bytes leídos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Llama a [CAtlFile:: Read](../../atl/reference/catlfile-class.md#read). Para cambiar la posición del puntero de archivo, llame a [CAtlTemporaryFile:: Seek](#seek).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

##  <a name="seek"></a>  CAtlTemporaryFile::Seek

Llame a este método para desplace el puntero de archivo del archivo temporal.

```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Parámetros

*nOffset*<br/>
Desplazamiento, en bytes, desde el punto inicial proporcionado por *dwFrom.*

*dwFrom*<br/>
Punto inicial (FILE_BEGIN, FILE_CURRENT o FILE_END).

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Llama a [CAtlFile:: Seek](../../atl/reference/catlfile-class.md#seek). Para obtener la posición del puntero de archivo actual, llame a [CAtlTemporaryFile:: GetPosition](#getposition).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

##  <a name="setsize"></a>  CAtlTemporaryFile::SetSize

Llame a este método para establecer el tamaño del archivo temporal.

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Parámetros

*nNewLen*<br/>
La nueva longitud del archivo en bytes.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Llama a [CAtlFile:: setSize](../../atl/reference/catlfile-class.md#setsize). En la devolución, el puntero de archivo se coloca al final del archivo.

##  <a name="tempfilename"></a>  CAtlTemporaryFile::TempFileName

Llame a este método para devolver el nombre del archivo temporal.

```
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el LPCTSTR que apunta al nombre de archivo.

### <a name="remarks"></a>Comentarios

El nombre de archivo se genera en [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile) con una llamada a la función Windows SDK de [GetTempFile](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamew). La extensión de archivo siempre será "TFR" para el archivo temporal.

##  <a name="unlockrange"></a>  CAtlTemporaryFile::UnlockRange

Llame a este método para desbloquear una región del archivo temporal.

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Posición en el archivo donde debe comenzar el desbloqueo.

*nCount*<br/>
Longitud del intervalo de bytes que se va a desbloquear.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Llama a [CAtlFile:: UnlockRange](../../atl/reference/catlfile-class.md#unlockrange).

##  <a name="write"></a>  CAtlTemporaryFile::Write

Llame a este método para escribir datos en el archivo temporal a partir de la posición indicada por el puntero de archivo.

```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*pBuffer*<br/>
Búfer que contiene los datos que se van a escribir en el archivo.

*nBufSize*<br/>
Número de bytes que se van a transferir desde el búfer.

*pnBytesWritten*<br/>
Número de bytes escritos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Llama a [CAtlFile:: Write](../../atl/reference/catlfile-class.md#write).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile:: CAtlTemporaryFile](#catltemporaryfile).

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[CAtlFile (clase)](../../atl/reference/catlfile-class.md)
