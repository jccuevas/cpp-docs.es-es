---
title: CAtlTemporaryFile (Clase)
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
ms.openlocfilehash: 605e4bcbe7208b18d8d1a50507e8e142a93bde5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321307"
---
# <a name="catltemporaryfile-class"></a>CAtlTemporaryFile (Clase)

Esta clase proporciona métodos para la creación y el uso de un archivo temporal.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CAtlTemporaryFile
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|El constructor.|
|[CAtlTemporaryFile::-CAtlTemporaryFile](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlTemporaryFile::Cerrar](#close)|Llame a este método para cerrar un archivo temporal y eliminar su contenido o almacenarlo bajo el nombre de archivo especificado.|
|[CAtlTemporaryFile::Crear](#create)|Llame a este método para crear un archivo temporal.|
|[CAtlTemporaryFile::Flush](#flush)|Llame a este método para forzar que los datos restantes en el búfer de archivos se escriban en el archivo temporal.|
|[CAtlTemporaryFile::GetPosition](#getposition)|Llame a este método para obtener la posición actual del puntero de archivo.|
|[CAtlTemporaryFile::GetSize](#getsize)|Llame a este método para obtener el tamaño en bytes del archivo temporal.|
|[CAtlTemporaryFile::HandsOff](#handsoff)|Llame a este método para desasociar el archivo del `CAtlTemporaryFile` objeto.|
|[CAtlTemporaryFile::HandsOn](#handson)|Llame a este método para abrir un archivo temporal existente y colocar el puntero al final del archivo.|
|[CAtlTemporaryFile::LockRange](#lockrange)|Llame a este método para bloquear una región en el archivo para evitar que otros procesos accedan a ella.|
|[CAtlTemporaryFile::Leer](#read)|Llame a este método para leer los datos del archivo temporal a partir de la posición indicada por el puntero de archivo.|
|[CAtlTemporaryFile::Buscar](#seek)|Llame a este método para mover el puntero de archivo del archivo temporal.|
|[CAtlTemporaryFile::SetSize](#setsize)|Llame a este método para establecer el tamaño del archivo temporal.|
|[CAtlTemporaryFile::TempFileName](#tempfilename)|Llame a este método para devolver el nombre del archivo temporal.|
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|Llame a este método para desbloquear una región del archivo temporal.|
|[CAtlTemporaryFile::Escribir](#write)|Llame a este método para escribir datos en el archivo temporal a partir de la posición indicada por el puntero de archivo.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlTemporaryFile::operador HANDLE](#operator_handle)|Devuelve un identificador al archivo temporal.|

## <a name="remarks"></a>Observaciones

`CAtlTemporaryFile`facilita la creación y el uso de un archivo temporal. El archivo se nombra, abre, cierra y elimina automáticamente. Si el contenido del archivo es necesario después de cerrar el archivo, se pueden guardar en un nuevo archivo con un nombre especificado.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlfile.h

## <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="catltemporaryfile"></a>CAtlTemporaryFile::CAtlTemporaryFile

El constructor.

```
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Observaciones

Un archivo no se abre realmente hasta que se realiza una llamada a [CAtlTemporaryFile::Create](#create).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

## <a name="catltemporaryfilecatltemporaryfile"></a><a name="dtor"></a>CAtlTemporaryFile::-CAtlTemporaryFile

Destructor.

```
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Observaciones

El destructor llama a [CAtlTemporaryFile::Close](#close).

## <a name="catltemporaryfileclose"></a><a name="close"></a>CAtlTemporaryFile::Cerrar

Llame a este método para cerrar un archivo temporal y eliminar su contenido o almacenarlo bajo el nombre de archivo especificado.

```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*szNewName*<br/>
El nombre del nuevo archivo en el que almacenar el contenido del archivo temporal. Si este argumento es NULL, se elimina el contenido del archivo temporal.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilecreate"></a><a name="create"></a>CAtlTemporaryFile::Crear

Llame a este método para crear un archivo temporal.

```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>Parámetros

*pszDir*<br/>
La ruta de acceso del archivo temporal. Si se trata de NULL, [GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppathw) se llamará para asignar una ruta de acceso.

*dwDesiredAccess*<br/>
El acceso deseado. Consulte *dwDesiredAccess* en [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfileflush"></a><a name="flush"></a>CAtlTemporaryFile::Flush

Llame a este método para forzar que los datos restantes en el búfer de archivos se escriban en el archivo temporal.

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Similar a [CAtlTemporaryFile::HandsOff](#handsoff), excepto que el archivo no está cerrado.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilegetposition"></a><a name="getposition"></a>CAtlTemporaryFile::GetPosition

Llame a este método para obtener la posición actual del puntero de archivo.

```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```

### <a name="parameters"></a>Parámetros

*Fnco*<br/>
La posición en bytes.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Para cambiar la posición del puntero de archivo, utilice [CAtlTemporaryFile::Seek](#seek).

## <a name="catltemporaryfilegetsize"></a><a name="getsize"></a>CAtlTemporaryFile::GetSize

Llame a este método para obtener el tamaño en bytes del archivo temporal.

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Parámetros

*nLen*<br/>
El número de bytes en el archivo.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="catltemporaryfilehandsoff"></a><a name="handsoff"></a>CAtlTemporaryFile::HandsOff

Llame a este método para desasociar el archivo del `CAtlTemporaryFile` objeto.

```
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

`HandsOff`y [CAtlTemporaryFile::HandsOn](#handson) se utilizan para desasociar el archivo del objeto y volver a adjuntarlo si es necesario. `HandsOff`obligará a los datos restantes en el búfer de archivos a escribirse en el archivo temporal y, a continuación, cerrar el archivo. Si desea cerrar y eliminar el archivo de forma permanente, o si desea cerrar y conservar el contenido del archivo con un nombre determinado, utilice [CAtlTemporaryFile::Close](#close).

## <a name="catltemporaryfilehandson"></a><a name="handson"></a>CAtlTemporaryFile::HandsOn

Llame a este método para abrir un archivo temporal existente y colocar el puntero al final del archivo.

```
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

[CAtlTemporaryFile::HandsOff](#handsoff) `HandsOn` y se utilizan para desasociar el archivo del objeto y volver a adjuntarlo si es necesario.

## <a name="catltemporaryfilelockrange"></a><a name="lockrange"></a>CAtlTemporaryFile::LockRange

Llame a este método para bloquear una región en el archivo temporal para evitar que otros procesos accedan a ella.

```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parámetros

*Fnco*<br/>
La posición en el archivo donde debe comenzar el bloqueo.

*nCount*<br/>
La longitud del intervalo de bytes que se va a bloquear.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

El bloqueo de bytes en un archivo impide que otros procesos obtengan acceso a dichos bytes. Puede bloquear más de una región de un archivo, pero no se permiten regiones superpuestas. Para desbloquear correctamente una región, utilice [CAtlTemporaryFile::UnlockRange](#unlockrange), asegurándose de que el intervalo de bytes corresponde exactamente a la región que se bloqueó anteriormente. `LockRange`no fusiona regiones adyacentes; si dos regiones bloqueadas son adyacentes, debe desbloquear cada una por separado.

## <a name="catltemporaryfileoperator-handle"></a><a name="operator_handle"></a>CAtlTemporaryFile::operador HANDLE

Devuelve un identificador al archivo temporal.

```
operator HANDLE() throw();
```

## <a name="catltemporaryfileread"></a><a name="read"></a>CAtlTemporaryFile::Leer

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
El número de bytes leídos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Llama a [CAtlFile::Read](../../atl/reference/catlfile-class.md#read). Para cambiar la posición del puntero de archivo, llame a [CAtlTemporaryFile::Seek](#seek).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfileseek"></a><a name="seek"></a>CAtlTemporaryFile::Buscar

Llame a este método para mover el puntero de archivo del archivo temporal.

```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Parámetros

*nOffset*<br/>
El desplazamiento, en bytes, desde el punto de partida dado por *dwFrom.*

*dwFrom*<br/>
El punto de partida (FILE_BEGIN, FILE_CURRENT o FILE_END).

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Llama a [CAtlFile::Seek](../../atl/reference/catlfile-class.md#seek). Para obtener la posición actual del puntero de archivo, llame a [CAtlTemporaryFile::GetPosition](#getposition).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="catltemporaryfilesetsize"></a><a name="setsize"></a>CAtlTemporaryFile::SetSize

Llame a este método para establecer el tamaño del archivo temporal.

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Parámetros

*nNewLen*<br/>
La nueva longitud del archivo en bytes.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Llama a [CAtlFile::SetSize](../../atl/reference/catlfile-class.md#setsize). Al volver, el puntero del archivo se coloca al final del archivo.

## <a name="catltemporaryfiletempfilename"></a><a name="tempfilename"></a>CAtlTemporaryFile::TempFileName

Llame a este método para devolver el nombre del archivo temporal.

```
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el LPCTSTR que apunta al nombre de archivo.

### <a name="remarks"></a>Observaciones

El nombre de archivo se genera en [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile) con una llamada a la [función GetTempFile](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamew)windows SDK. La extensión de archivo siempre será "TFR" para el archivo temporal.

## <a name="catltemporaryfileunlockrange"></a><a name="unlockrange"></a>CAtlTemporaryFile::UnlockRange

Llame a este método para desbloquear una región del archivo temporal.

```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```

### <a name="parameters"></a>Parámetros

*Fnco*<br/>
La posición en el archivo donde debe comenzar el desbloqueo.

*nCount*<br/>
La longitud del intervalo de bytes que se va a desbloquear.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Llama a [CAtlFile::UnlockRange](../../atl/reference/catlfile-class.md#unlockrange).

## <a name="catltemporaryfilewrite"></a><a name="write"></a>CAtlTemporaryFile::Escribir

Llame a este método para escribir datos en el archivo temporal a partir de la posición indicada por el puntero de archivo.

```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*pBuffer*<br/>
El búfer que contiene los datos que se van a escribir en el archivo.

*nBufSize*<br/>
El número de bytes que se transferirán desde el búfer.

*pnBytesWritten*<br/>
El número de bytes escritos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Llama a [CAtlFile::Write](../../atl/reference/catlfile-class.md#write).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[CAtlFile (Clase)](../../atl/reference/catlfile-class.md)
