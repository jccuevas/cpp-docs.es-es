---
title: Clase CAtlTransactionManager
ms.date: 11/04/2016
f1_keywords:
- CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::Close
- ATLTRANSACTIONMANAGER/ATL::Commit
- ATLTRANSACTIONMANAGER/ATL::Create
- ATLTRANSACTIONMANAGER/ATL::CreateFile
- ATLTRANSACTIONMANAGER/ATL::DeleteFile
- ATLTRANSACTIONMANAGER/ATL::FindFirstFile
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributesEx
- ATLTRANSACTIONMANAGER/ATL::GetHandle
- ATLTRANSACTIONMANAGER/ATL::IsFallback
- ATLTRANSACTIONMANAGER/ATL::MoveFile
- ATLTRANSACTIONMANAGER/ATL::RegCreateKeyEx
- ATLTRANSACTIONMANAGER/ATL::RegDeleteKey
- ATLTRANSACTIONMANAGER/ATL::RegOpenKeyEx
- ATLTRANSACTIONMANAGER/ATL::Rollback
- ATLTRANSACTIONMANAGER/ATL::SetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::m_bFallback
- ATLTRANSACTIONMANAGER/ATL::m_hTransaction
helpviewer_keywords:
- CAtlTransactionManager class
ms.assetid: b01732dc-1d16-4b42-bfac-b137fca2b740
ms.openlocfilehash: 968582feccd8ba9252ca009699eef6eae2c5c3d6
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167830"
---
# <a name="catltransactionmanager-class"></a>Clase CAtlTransactionManager

La clase CAtlTransactionManager proporciona un contenedor para las funciones del administrador de transacciones de kernel (KTM).

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```cpp
class CAtlTransactionManager;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[~ CAtlTransactionManager](#dtor)|Destructor CAtlTransactionManager.|
|[CAtlTransactionManager](#catltransactionmanager)|Constructor CAtlTransactionManager.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Cerrar](#close)|Cierra un identificador de transacción.|
|[Confirmar](#commit)|Solicita que se confirme la transacción.|
|[Crear](#create)|Crea el identificador de la transacción.|
|[CreateFile](#createfile)|Crea o abre un archivo, una secuencia de archivos o un directorio como una operación de transacción.|
|[DeleteFile](#deletefile)|Elimina un archivo existente como una operación de transacción.|
|[FindFirstFile](#findfirstfile)|Busca un archivo o un subdirectorio en un directorio como una operación de transacción.|
|[GetFileAttributes](#getfileattributes)|Recupera los atributos del sistema de archivos para un archivo o directorio especificado como una operación de transacción.|
|[GetFileAttributesEx](#getfileattributesex)|Recupera los atributos del sistema de archivos para un archivo o directorio especificado como una operación de transacción.|
|[GetHandle](#gethandle)|Devuelve el identificador de la transacción.|
|[IsFallback](#isfallback)|Determina si las llamadas de reserva están habilitadas.|
|[MoveFile](#movefile)|Mueve un archivo o un directorio existente, incluidos sus elementos secundarios, como una operación de transacción.|
|[RegCreateKeyEx](#regcreatekeyex)|Crea la clave del registro especificada y la asocia a una transacción. Si la clave ya existe, la función la abre.|
|[RegDeleteKey](#regdeletekey)|Elimina una subclave y sus valores de la vista específica de la plataforma especificada del registro como una operación de transacción.|
|[RegOpenKeyEx](#regopenkeyex)|Abre la clave del registro especificada y la asocia a una transacción.|
|[Reversión](#rollback)|Solicita que se revierta la transacción.|
|[SetFileAttributes](#setfileattributes)|Establece los atributos de un archivo o directorio como una operación de transacción.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[m_bFallback](#m_bfallback)|TRUE si se admite la reserva; De lo contrario, FALSE.|
|[m_hTransaction](#m_htransaction)|Identificador de la transacción.|

## <a name="remarks"></a>Observaciones

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[ATL:: CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** atltransactionmanager. h

## <a name="catltransactionmanager"></a><a name="dtor"></a>~ CAtlTransactionManager

Destructor CAtlTransactionManager.

```cpp
virtual ~CAtlTransactionManager();
```

### <a name="remarks"></a>Observaciones

En el procesamiento normal, la transacción se confirma y se cierra automáticamente. Si se llama al destructor durante el desenredado de una excepción, la transacción se revierte y se cierra.

## <a name="catltransactionmanager"></a><a name="catltransactionmanager"></a>CAtlTransactionManager

Constructor CAtlTransactionManager.

```cpp
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```

### <a name="parameters"></a>Parámetros

*bFallback*<br/>
TRUE indica compatibilidad de reserva. Si se produce un error en la función de transacción, la clase llama automáticamente a la función "sin transacciones". FALSE indica que no hay llamadas de "reserva".

*bAutoCreateTransaction*<br/>
TRUE indica que el controlador de transacciones se crea automáticamente en el constructor. FALSE indica que no lo es.

### <a name="remarks"></a>Observaciones

## <a name="close"></a><a name="close"></a>Cercanos

Cierra el identificador de la transacción.

```cpp
inline BOOL Close();
```

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este contenedor llama a `CloseHandle` la función. El método se llama automáticamente en el destructor.

## <a name="commit"></a><a name="commit"></a>Promete

Solicita que se confirme la transacción.

```cpp
inline BOOL Commit();
```

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este contenedor llama a `CommitTransaction` la función. El método se llama automáticamente en el destructor.

## <a name="create"></a><a name="create"></a>A

Crea el identificador de la transacción.

```cpp
inline BOOL Create();
```

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este contenedor llama a `CreateTransaction` la función. Compruébelo

## <a name="createfile"></a><a name="createfile"></a>CreateFile

Crea o abre un archivo, una secuencia de archivos o un directorio como una operación de transacción.

```cpp
inline HANDLE CreateFile(
    LPCTSTR lpFileName,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes,
    HANDLE hTemplateFile);
```

### <a name="parameters"></a>Parámetros

*lpFileName*<br/>
Nombre de un objeto que se va a crear o abrir.

*dwDesiredAccess*<br/>
El acceso al objeto, que se puede resumir como lectura, escritura, ambos o ninguno (cero). Los valores que se usan con más frecuencia son GENERIC_READ, GENERIC_WRITE o ambos: GENERIC_READ &#124; GENERIC_WRITE.

*dwShareMode*<br/>
El modo de uso compartido de un objeto, que se puede leer, escribir, ambos, eliminar, todos ellos o ninguno: 0, FILE_SHARE_DELETE, FILE_SHARE_READ FILE_SHARE_WRITE.

*lpSecurityAttributes*<br/>
Puntero a una estructura de SECURITY_ATTRIBUTES que contiene un descriptor de seguridad opcional y que también determina si los procesos secundarios pueden heredar el identificador devuelto. El parámetro puede ser NULL.

*dwCreationDisposition*<br/>
Acción que se va a realizar en los archivos que existen y que no existen. Este parámetro debe ser uno de los siguientes valores, que no se pueden combinar: CREATE_ALWAYS, CREATE_NEW, OPEN_ALWAYS, OPEN_EXISTING o TRUNCATE_EXISTING.

*dwFlagsAndAttributes*<br/>
Atributos y marcas de archivo. Este parámetro puede incluir cualquier combinación de los atributos de archivo disponibles (FILE_ATTRIBUTE_ *). Todos los demás atributos de archivo invalidan FILE_ATTRIBUTE_NORMAL. Este parámetro también puede contener combinaciones de marcas (FILE_FLAG_\*) para el control del comportamiento de almacenamiento en búfer, los modos de acceso y otras marcas de propósito especial. Se combinan con los valores\* de FILE_ATTRIBUTE_.

*hTemplateFile*<br/>
Un identificador válido para un archivo de plantilla con el derecho de acceso GENERIC_READ. El archivo de plantilla proporciona atributos de archivo y atributos extendidos para el archivo que se va a crear. Este parámetro puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador que se puede utilizar para tener acceso al objeto.

### <a name="remarks"></a>Observaciones

Este contenedor llama a `CreateFileTransacted` la función.

## <a name="deletefile"></a><a name="deletefile"></a>DeleteFile

Elimina un archivo existente como una operación de transacción.

```cpp
inline BOOL DeleteFile(LPCTSTR lpFileName);
```

### <a name="parameters"></a>Parámetros

*lpFileName*<br/>
Nombre del archivo que se va a eliminar.

### <a name="remarks"></a>Observaciones

Este contenedor llama a `DeleteFileTransacted` la función.

## <a name="findfirstfile"></a><a name="findfirstfile"></a>FindFirstFile

Busca un archivo o un subdirectorio en un directorio como una operación de transacción.

```cpp
inline HANDLE FindFirstFile(
    LPCTSTR lpFileName,
    WIN32_FIND_DATA* pNextInfo);
```

### <a name="parameters"></a>Parámetros

*lpFileName*<br/>
Directorio o ruta de acceso y nombre de archivo que se va a buscar. Este parámetro puede incluir caracteres comodín, como un asterisco (*) o un signo de interrogación ().

*pNextInfo*<br/>
Puntero a la estructura de WIN32_FIND_DATA que recibe información sobre un archivo o subdirectorio encontrado.

### <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es un identificador de búsqueda que se utiliza `FindNextFile` en `FindClose`una llamada subsiguiente a o. Si se produce un error en la función o no encuentra los archivos de la cadena de búsqueda en el parámetro *lpFileName* , el valor devuelto es INVALID_HANDLE_VALUE.

### <a name="remarks"></a>Observaciones

Este contenedor llama a `FindFirstFileTransacted` la función.

## <a name="getfileattributes"></a><a name="getfileattributes"></a>GetFileAttributes

Recupera los atributos del sistema de archivos para un archivo o directorio especificado como una operación de transacción.

```cpp
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```

### <a name="parameters"></a>Parámetros

*lpFileName*<br/>
Nombre del archivo o directorio.

### <a name="remarks"></a>Observaciones

Este contenedor llama a `GetFileAttributesTransacted` la función.

## <a name="getfileattributesex"></a><a name="getfileattributesex"></a>GetFileAttributesEx

Recupera los atributos del sistema de archivos para un archivo o directorio especificado como una operación de transacción.

```cpp
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```

### <a name="parameters"></a>Parámetros

*lpFileName*<br/>
Nombre del archivo o directorio.

*fInfoLevelId*<br/>
Nivel de información de atributo que se va a recuperar.

*lpFileInformation*<br/>
Puntero a un búfer que recibe la información de atributo. El tipo de información de atributo que se almacena en este búfer viene determinado por el valor de *fInfoLevelId*. Si el parámetro *fInfoLevelId* es GetFileExInfoStandard, este parámetro señala a una estructura de WIN32_FILE_ATTRIBUTE_DATA.

### <a name="remarks"></a>Observaciones

Este contenedor llama a `GetFileAttributesTransacted` la función.

## <a name="gethandle"></a><a name="gethandle"></a>GetHandle

Devuelve el identificador de la transacción.

```cpp
HANDLE GetHandle() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador de transacción de una clase. Devuelve NULL si no `CAtlTransactionManager` está asociado a un identificador.

### <a name="remarks"></a>Observaciones

## <a name="isfallback"></a><a name="isfallback"></a>IsFallback

Determina si las llamadas de reserva están habilitadas.

```cpp
BOOL IsFallback() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la clase admite llamadas de reserva. FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

## <a name="m_bfallback"></a><a name="m_bfallback"></a>m_bFallback

TRUE si se admite la reserva; De lo contrario, FALSE.

```cpp
BOOL m_bFallback;
```

### <a name="remarks"></a>Observaciones

## <a name="m_htransaction"></a><a name="m_htransaction"></a>m_hTransaction

Identificador de la transacción.

```cpp
HANDLE m_hTransaction;
```

### <a name="remarks"></a>Observaciones

## <a name="movefile"></a><a name="movefile"></a>MoveFile

Mueve un archivo o un directorio existente, incluidos sus elementos secundarios, como una operación de transacción.

```cpp
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```

### <a name="parameters"></a>Parámetros

*lpOldFileName*<br/>
Nombre actual del archivo o directorio existente en el equipo local.

*lpNewFileName*<br/>
Nuevo nombre del archivo o directorio. Este nombre no debe existir todavía. Un archivo nuevo puede estar en una unidad o sistema de archivos diferente. Un directorio nuevo debe estar en la misma unidad.

### <a name="remarks"></a>Observaciones

Este contenedor llama a `MoveFileTransacted` la función.

## <a name="regcreatekeyex"></a><a name="regcreatekeyex"></a>RegCreateKeyEx

Crea la clave del registro especificada y la asocia a una transacción. Si la clave ya existe, la función la abre.

```cpp
inline LSTATUS RegCreateKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD dwReserved,
    LPTSTR lpClass,
    DWORD dwOptions,
    REGSAM samDesired,
    CONST LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    PHKEY phkResult,
    LPDWORD lpdwDisposition);
```

### <a name="parameters"></a>Parámetros

*hKey*<br/>
Identificador de una clave del registro abierta.

*lpSubKey*<br/>
Nombre de una subclave que esta función abre o crea.

*dwReserved*<br/>
Este parámetro está reservado y debe ser cero.

*lpClass*<br/>
Clase definida por el usuario de esta clave. Este parámetro se puede omitir. Este parámetro puede ser NULL.

*dwOptions*<br/>
Este parámetro puede ser uno de los siguientes valores: REG_OPTION_BACKUP_RESTORE, REG_OPTION_NON_VOLATILE o REG_OPTION_VOLATILE.

*samDesired*<br/>
Máscara que especifica los derechos de acceso para la clave.

*lpSecurityAttributes*<br/>
Puntero a una estructura de SECURITY_ATTRIBUTES que determina si el identificador devuelto se puede heredar de procesos secundarios. Si *lpSecurityAttributes* es null, el identificador no se puede heredar.

*phkResult*<br/>
Puntero a una variable que recibe un identificador de la clave abierta o creada. Si la clave no es una de las claves del registro predefinidas, `RegCloseKey` llame a la función una vez que haya terminado de usar el identificador.

*lpdwDisposition*<br/>
Puntero a una variable que recibe uno de los siguientes valores de disposición: REG_CREATED_NEW_KEY o REG_OPENED_EXISTING_KEY.

### <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror. h.

### <a name="remarks"></a>Observaciones

Este contenedor llama a `RegCreateKeyTransacted` la función.

## <a name="regdeletekey"></a><a name="regdeletekey"></a>RegDeleteKey

Elimina una subclave y sus valores de la vista específica de la plataforma especificada del registro como una operación de transacción.

```cpp
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*hKey*|Identificador de una clave del registro abierta.|
|*lpSubKey*|Nombre de la clave que se va a eliminar.|

### <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror. h.

### <a name="remarks"></a>Observaciones

Este contenedor llama a `RegDeleteKeyTransacted` la función.

## <a name="regopenkeyex"></a><a name="regopenkeyex"></a>RegOpenKeyEx

Abre la clave del registro especificada y la asocia a una transacción.

```cpp
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```

### <a name="parameters"></a>Parámetros

*hKey*<br/>
Identificador de una clave del registro abierta.

*lpSubKey*<br/>
Nombre de la subclave del registro que se va a abrir.

*ulOptions*<br/>
Este parámetro está reservado y debe ser cero.

*samDesired*<br/>
Máscara que especifica los derechos de acceso para la clave.

*phkResult*<br/>
Puntero a una variable que recibe un identificador de la clave abierta o creada. Si la clave no es una de las claves del registro predefinidas, `RegCloseKey` llame a la función una vez que haya terminado de usar el identificador.

### <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror. h.

### <a name="remarks"></a>Observaciones

Este contenedor llama a `RegOpenKeyTransacted` la función.

## <a name="rollback"></a><a name="rollback"></a>Recuperación

Solicita que se revierta la transacción.

```cpp
inline BOOL Rollback();
```

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este contenedor llama a `RollbackTransaction` la función.

## <a name="setfileattributes"></a><a name="setfileattributes"></a>SetFileAttributes

Establece los atributos de un archivo o directorio como una operación de transacción.

```cpp
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```

### <a name="parameters"></a>Parámetros

*lpFileName*<br/>
Nombre del archivo o directorio.

*dwAttributes*<br/>
Atributos de archivo que se van a establecer para el archivo. Para obtener más información, vea [SetFileAttributesTransacted](/windows/win32/api/winbase/nf-winbase-setfileattributestransactedw).

### <a name="remarks"></a>Observaciones

Este contenedor llama a `SetFileAttributesTransacted` la función.

## <a name="see-also"></a>Consulte también

[Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md)
