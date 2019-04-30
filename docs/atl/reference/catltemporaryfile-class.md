---
title: CAtlTemporaryFile (clase)
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
ms.openlocfilehash: c1da5037deb0143c6d05009baccc8c1553616028
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246907"
---
# <a name="catltemporaryfile-class"></a>CAtlTemporaryFile (clase)

Esta clase proporciona métodos para la creación y uso de un archivo temporal.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
class CAtlTemporaryFile
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|El constructor.|
|[CAtlTemporaryFile::~CAtlTemporaryFile](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlTemporaryFile::Close](#close)|Llame a este método para cerrar un archivo temporal y eliminar su contenido o almacenarlas en el nombre de archivo especificado.|
|[CAtlTemporaryFile::Create](#create)|Llame a este método para crear un archivo temporal.|
|[CAtlTemporaryFile::Flush](#flush)|Llame a este método para obligar a los datos permanecen en el búfer de archivo que se escriban en el archivo temporal.|
|[CAtlTemporaryFile::GetPosition](#getposition)|Llame a este método para obtener la posición actual del puntero de archivo.|
|[CAtlTemporaryFile::GetSize](#getsize)|Llame a este método para obtener el tamaño en bytes del archivo temporal.|
|[CAtlTemporaryFile::HandsOff](#handsoff)|Llame a este método para desasociar el archivo desde el `CAtlTemporaryFile` objeto.|
|[CAtlTemporaryFile::HandsOn](#handson)|Llame a este método para abrir un archivo temporal existente y coloque el puntero al final del archivo.|
|[CAtlTemporaryFile::LockRange](#lockrange)|Llame a este método para bloquear una región en el archivo para evitar que otros procesos tengan acceso a él.|
|[CAtlTemporaryFile::Read](#read)|Llame a este método para leer datos desde el archivo temporal en la posición indicada por el puntero de archivo.|
|[CAtlTemporaryFile::Seek](#seek)|Llame a este método para mover el puntero de archivo del archivo temporal.|
|[CAtlTemporaryFile::SetSize](#setsize)|Llame a este método para establecer el tamaño del archivo temporal.|
|[CAtlTemporaryFile::TempFileName](#tempfilename)|Llame a este método para devolver el nombre del archivo temporal.|
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|Llame a este método para desbloquear una región del archivo temporal.|
|[CAtlTemporaryFile::Write](#write)|Llame a este método para escribir datos en el archivo temporal en la posición indicada por el puntero de archivo.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlTemporaryFile::operator HANDLE](#operator_handle)|Devuelve un identificador en el archivo temporal.|

## <a name="remarks"></a>Comentarios

`CAtlTemporaryFile` facilita la creación y uso de un archivo temporal. Automáticamente el archivo es denominado, abierto, cerrado y eliminado. Si el contenido del archivo es necesario después de cerrar el archivo, pueden guardar en un archivo nuevo con un nombre especificado.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlfile.h

## <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="catltemporaryfile"></a>  CAtlTemporaryFile::CAtlTemporaryFile

El constructor.

```
CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Comentarios

No se abre realmente un archivo hasta que se realiza una llamada a [CAtlTemporaryFile::Create](#create).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]

##  <a name="dtor"></a>  CAtlTemporaryFile::~CAtlTemporaryFile

Destructor.

```
~CAtlTemporaryFile() throw();
```

### <a name="remarks"></a>Comentarios

El destructor llama a [CAtlTemporaryFile::Close](#close).

##  <a name="close"></a>  CAtlTemporaryFile::Close

Llame a este método para cerrar un archivo temporal y eliminar su contenido o almacenarlas en el nombre de archivo especificado.

```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*szNewName*<br/>
El nombre para el nuevo archivo almacenar el contenido del archivo temporal en. Si este argumento es NULL, se elimina el contenido del archivo temporal.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="create"></a>  CAtlTemporaryFile::Create

Llame a este método para crear un archivo temporal.

```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```

### <a name="parameters"></a>Parámetros

*pszDir*<br/>
La ruta de acceso para el archivo temporal. Si es NULL, [GetTempPath](/windows/desktop/api/fileapi/nf-fileapi-gettemppatha) se llamará para asignar una ruta de acceso.

*dwDesiredAccess*<br/>
El acceso deseado. Consulte *dwDesiredAccess* en [CreateFile](/windows/desktop/api/fileapi/nf-fileapi-createfilea) en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="flush"></a>  CAtlTemporaryFile::Flush

Llame a este método para obligar a los datos permanecen en el búfer de archivo que se escriban en el archivo temporal.

```
HRESULT Flush() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Similar a [CAtlTemporaryFile::HandsOff](#handsoff), salvo que no se cierra el archivo.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="getposition"></a>  CAtlTemporaryFile::GetPosition

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

Para cambiar la posición del puntero de archivo, use [CAtlTemporaryFile::Seek](#seek).

##  <a name="getsize"></a>  CAtlTemporaryFile::GetSize

Llame a este método para obtener el tamaño en bytes del archivo temporal.

```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```

### <a name="parameters"></a>Parámetros

*nLen*<br/>
El número de bytes en el archivo.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

##  <a name="handsoff"></a>  CAtlTemporaryFile::HandsOff

Llame a este método para desasociar el archivo desde el `CAtlTemporaryFile` objeto.

```
HRESULT HandsOff() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

`HandsOff` y [CAtlTemporaryFile::HandsOn](#handson) se usan para desasociar el archivo desde el objeto y volver a conectarlo si es necesario. `HandsOff` se forzar los datos permanecen en el búfer de archivo que se escriban en el archivo temporal y, a continuación, cierre el archivo. Si desea cerrar y eliminar permanentemente el archivo, o si desea cerrar y conservar el contenido del archivo con un nombre determinado, use [CAtlTemporaryFile::Close](#close).

##  <a name="handson"></a>  CAtlTemporaryFile::HandsOn

Llame a este método para abrir un archivo temporal existente y coloque el puntero al final del archivo.

```
HRESULT HandsOn() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

[CAtlTemporaryFile::HandsOff](#handsoff) y `HandsOn` se usan para desasociar el archivo desde el objeto y volver a conectarlo si es necesario.

##  <a name="lockrange"></a>  CAtlTemporaryFile::LockRange

Llame a este método para bloquear una región en el archivo temporal para evitar que otros procesos tengan acceso a él.

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

El bloqueo de bytes en un archivo impide que otros procesos obtengan acceso a dichos bytes. Puede bloquear más de una región de un archivo, pero no se permite ninguna región que se superponen. Para desbloquear correctamente una región, utilice [CAtlTemporaryFile::UnlockRange](#unlockrange), lo que garantiza el intervalo de bytes corresponde exactamente a la región que se ha bloqueado anteriormente. `LockRange` no combina regiones adyacentes; Si dos regiones bloqueadas son adyacentes, debe desbloquear cada uno por separado.

##  <a name="operator_handle"></a>  CAtlTemporaryFile::operator HANDLE

Devuelve un identificador en el archivo temporal.

```
operator HANDLE() throw();
```

##  <a name="read"></a>  CAtlTemporaryFile::Read

Llame a este método para leer datos desde el archivo temporal en la posición indicada por el puntero de archivo.

```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```

### <a name="parameters"></a>Parámetros

*pBuffer*<br/>
Puntero al búfer que recibirá los datos leídos desde el archivo.

*nBufSize*<br/>
El tamaño del búfer en bytes.

*nBytesRead*<br/>
Número de bytes leídos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Las llamadas [CAtlFile::Read](../../atl/reference/catlfile-class.md#read). Para cambiar la posición del puntero de archivo, llame a [CAtlTemporaryFile::Seek](#seek).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="seek"></a>  CAtlTemporaryFile::Seek

Llame a este método para mover el puntero de archivo del archivo temporal.

```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```

### <a name="parameters"></a>Parámetros

*nOffset*<br/>
El desplazamiento, en bytes, desde el punto inicial dado por *dwFrom.*

*dwFrom*<br/>
El punto de partida (FILE_BEGIN, FILE_CURRENT o FILE_END).

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Las llamadas [CAtlFile::Seek](../../atl/reference/catlfile-class.md#seek). Para obtener la posición actual del puntero de archivo, llame a [CAtlTemporaryFile::GetPosition](#getposition).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

##  <a name="setsize"></a>  CAtlTemporaryFile::SetSize

Llame a este método para establecer el tamaño del archivo temporal.

```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```

### <a name="parameters"></a>Parámetros

*nNewLen*<br/>
La nueva longitud del archivo en bytes.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Las llamadas [CAtlFile::SetSize](../../atl/reference/catlfile-class.md#setsize). Si la devolución, el puntero de archivo se coloca al final del archivo.

##  <a name="tempfilename"></a>  CAtlTemporaryFile::TempFileName

Llame a este método para devolver el nombre de archivo temporal.

```
LPCTSTR TempFileName() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el LPCTSTR que señala al nombre de archivo.

### <a name="remarks"></a>Comentarios

El nombre de archivo se genera en [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile) con una llamada a la [GetTempFile](/windows/desktop/api/fileapi/nf-fileapi-gettempfilenamea)función del SDK de Windows. La extensión de archivo siempre será "TFR" para el archivo temporal.

##  <a name="unlockrange"></a>  CAtlTemporaryFile::UnlockRange

Llame a este método para desbloquear una región del archivo temporal.

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

Las llamadas [CAtlFile::UnlockRange](../../atl/reference/catlfile-class.md#unlockrange).

##  <a name="write"></a>  CAtlTemporaryFile::Write

Llame a este método para escribir datos en el archivo temporal en la posición indicada por el puntero de archivo.

```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```

### <a name="parameters"></a>Parámetros

*pBuffer*<br/>
El búfer que contiene los datos se escriban en el archivo.

*nBufSize*<br/>
El número de bytes que se transfieren desde el búfer.

*pnBytesWritten*<br/>
Número de bytes escritos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Las llamadas [CAtlFile::Write](../../atl/reference/catlfile-class.md#write).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[CAtlFile (clase)](../../atl/reference/catlfile-class.md)
