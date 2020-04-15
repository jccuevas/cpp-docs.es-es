---
title: CAtlTransactionManager (clase)
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
ms.openlocfilehash: 5c2814f963ea4814e0d7585e0e4d6dda26c1f04d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321324"
---
# <a name="catltransactionmanager-class"></a>CAtlTransactionManager (clase)

CAtlTransactionManager clase proporciona un contenedor a kernel Transaction Manager (KTM) funciones.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CAtlTransactionManager;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[•CAtlTransactionManager](#dtor)|CAtlTransactionManager destructor.|
|[CAtlTransactionManager](#catltransactionmanager)|CAtlTransactionManager constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Cerrar](#close)|Cierra uno del identificador de transacción.|
|[Commit](#commit)|Solicita que se confirme la transacción.|
|[Crear](#create)|Crea el identificador de transacción.|
|[CreateFile](#createfile)|Crea o abre un archivo, una secuencia de archivos o un directorio como una operación de transacción.|
|[DeleteFile](#deletefile)|Elimina un archivo existente como una operación de transacción.|
|[FindFirstFile](#findfirstfile)|Busca un archivo o subdirectorio en un directorio como una operación de transacción.|
|[GetFileAttributes](#getfileattributes)|Recupera los atributos del sistema de archivos para un archivo o directorio especificado como una operación de transacción.|
|[GetFileAttributesEx](#getfileattributesex)|Recupera los atributos del sistema de archivos para un archivo o directorio especificado como una operación de transacción.|
|[GetHandle](#gethandle)|Devuelve el identificador de transacción.|
|[IsFallback](#isfallback)|Determina si las llamadas de reserva están habilitadas.|
|[MoveFile](#movefile)|Mueve un archivo existente o un directorio, incluidos sus elementos secundarios, como una operación de transacción.|
|[RegCreateKeyEx](#regcreatekeyex)|Crea la clave del Registro especificada y la asocia a una transacción. Si la clave ya existe, la función la abre.|
|[RegDeleteKey](#regdeletekey)|Elimina una subclave y sus valores de la vista específica de la plataforma especificada del registro como una operación de transacción.|
|[RegOpenKeyEx](#regopenkeyex)|Abre la clave del Registro especificada y la asocia a una transacción.|
|[Reversión](#rollback)|Solicita que se revierta la transacción.|
|[SetFileAttributes](#setfileattributes)|Establece los atributos de un archivo o directorio como una operación de transacción.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[m_bFallback](#m_bfallback)|TRUESi se admite la reserva; FALSE en caso contrario.|
|[m_hTransaction](#m_htransaction)|El identificador de transacción.|

## <a name="remarks"></a>Observaciones

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[ATL::CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** atltransactionmanager.h

## <a name="catltransactionmanager"></a><a name="dtor"></a>•CAtlTransactionManager

CAtlTransactionManager destructor.

```
virtual ~CAtlTransactionManager();
```

### <a name="remarks"></a>Observaciones

En el procesamiento normal, la transacción se confirma y cierra automáticamente. Si se llama al destructor durante un desenredado de excepción, la transacción se revierte y se cierra.

## <a name="catltransactionmanager"></a><a name="catltransactionmanager"></a>CAtlTransactionManager

CAtlTransactionManager constructor.

```
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```

### <a name="parameters"></a>Parámetros

*bFallback*<br/>
TRUE indica la reserva de compatibilidad. Si se produce un error en la función transacted, la clase llama automáticamente a la función "non-transacted". FALSE indica que no hay llamadas de "retroceso".

*bAutoCreateTransaction*<br/>
TRUE indica que el controlador de transacciones se crea automáticamente en el constructor. FALSE indica que no lo es.

### <a name="remarks"></a>Observaciones

## <a name="close"></a><a name="close"></a>Cerca

Cierra el identificador de transacción.

```
inline BOOL Close();
```

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este contenedor `CloseHandle` llama a la función. El método se llama automáticamente en el destructor.

## <a name="commit"></a><a name="commit"></a>Cometer

Solicita que se confirme la transacción.

```
inline BOOL Commit();
```

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este contenedor `CommitTransaction` llama a la función. El método se llama automáticamente en el destructor.

## <a name="create"></a><a name="create"></a>Crear

Crea el identificador de transacción.

```
inline BOOL Create();
```

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este contenedor `CreateTransaction` llama a la función. Compruérelo para

## <a name="createfile"></a><a name="createfile"></a>CreateFile

Crea o abre un archivo, una secuencia de archivos o un directorio como una operación de transacción.

```
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
El nombre de un objeto que se va a crear o abrir.

*dwDesiredAccess*<br/>
El acceso al objeto, que se puede resumir como lectura, escritura, ambos o ninguno (cero). Los valores más utilizados son GENERIC_READ, GENERIC_WRITE o ambos: GENERIC_READ &#124; GENERIC_WRITE.

*dwShareMode*<br/>
El modo de uso compartido de un objeto, que se puede leer, escribir, ambos, eliminar, todos estos o ninguno: 0, FILE_SHARE_DELETE, FILE_SHARE_READ, FILE_SHARE_WRITE.

*lpSecurityAttributes*<br/>
Un puntero a una estructura de SECURITY_ATTRIBUTES que contiene un descriptor de seguridad opcional y también determina si los procesos secundarios pueden heredar o no el identificador devuelto. El parámetro puede ser NULL.

*dwCreationDisposición*<br/>
Una acción para realizar archivos que existen y no existen. Este parámetro debe ser uno de los siguientes valores, que no se pueden combinar: CREATE_ALWAYS, CREATE_NEW, OPEN_ALWAYS, OPEN_EXISTING o TRUNCATE_EXISTING.

*dwFlagsAndAttributes*<br/>
Los atributos y marcas de archivo. Este parámetro puede incluir cualquier combinación de los atributos de archivo disponibles (FILE_ATTRIBUTE_*). Todos los demás atributos de archivo anulan FILE_ATTRIBUTE_NORMAL. Este parámetro también puede contener combinaciones de indicadores (FILE_FLAG_\*) para controlar el comportamiento de almacenamiento en búfer, los modos de acceso y otros indicadores de propósito especial. Estos se combinan\* con cualquier FILE_ATTRIBUTE_ valores.

*hTemplateFile*<br/>
Identificador válido de un archivo de plantilla con el derecho de acceso GENERIC_READ. El archivo de plantilla proporciona atributos de archivo y atributos extendidos para el archivo que se está creando. Este parámetro puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador que se puede usar para tener acceso al objeto.

### <a name="remarks"></a>Observaciones

Este contenedor `CreateFileTransacted` llama a la función.

## <a name="deletefile"></a><a name="deletefile"></a>DeleteFile

Elimina un archivo existente como una operación de transacción.

```
inline BOOL DeleteFile(LPCTSTR lpFileName);
```

### <a name="parameters"></a>Parámetros

*lpFileName*<br/>
Nombre del archivo que se va a eliminar.

### <a name="remarks"></a>Observaciones

Este contenedor `DeleteFileTransacted` llama a la función.

## <a name="findfirstfile"></a><a name="findfirstfile"></a>FindFirstFile

Busca un archivo o subdirectorio en un directorio como una operación de transacción.

```
inline HANDLE FindFirstFile(
    LPCTSTR lpFileName,
    WIN32_FIND_DATA* pNextInfo);
```

### <a name="parameters"></a>Parámetros

*lpFileName*<br/>
El directorio o la ruta de acceso y el nombre de archivo que se va a buscar. Este parámetro puede incluir caracteres comodín, como un asterisco (*) o un signo de interrogación ().

*pNextInfo*<br/>
Puntero a la estructura WIN32_FIND_DATA que recibe información sobre un archivo o subdirectorio encontrado.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto `FindNextFile` `FindClose`es un identificador de búsqueda utilizado en una llamada posterior a o . Si se produce un error en la función o no se pueden localizar archivos de la cadena de búsqueda en el parámetro *lpFileName,* el valor devuelto es INVALID_HANDLE_VALUE.

### <a name="remarks"></a>Observaciones

Este contenedor `FindFirstFileTransacted` llama a la función.

## <a name="getfileattributes"></a><a name="getfileattributes"></a>GetFileAttributes

Recupera los atributos del sistema de archivos para un archivo o directorio especificado como una operación de transacción.

```
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```

### <a name="parameters"></a>Parámetros

*lpFileName*<br/>
El nombre del archivo o directorio.

### <a name="remarks"></a>Observaciones

Este contenedor `GetFileAttributesTransacted` llama a la función.

## <a name="getfileattributesex"></a><a name="getfileattributesex"></a>GetFileAttributesEx

Recupera los atributos del sistema de archivos para un archivo o directorio especificado como una operación de transacción.

```
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```

### <a name="parameters"></a>Parámetros

*lpFileName*<br/>
El nombre del archivo o directorio.

*fInfoLevelId*<br/>
El nivel de información de atributo que se va a recuperar.

*lpFileInformation*<br/>
Puntero a un búfer que recibe la información de atributo. El tipo de información de atributo que se almacena en este búfer viene determinado por el valor de *fInfoLevelId*. Si el *fInfoLevelId* parámetro es GetFileExInfoStandard a continuación, este parámetro apunta a un WIN32_FILE_ATTRIBUTE_DATA estructura.

### <a name="remarks"></a>Observaciones

Este contenedor `GetFileAttributesTransacted` llama a la función.

## <a name="gethandle"></a><a name="gethandle"></a>GetHandle

Devuelve el identificador de transacción.

```
HANDLE GetHandle() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador de transacción de una clase. Devuelve NULL `CAtlTransactionManager` si no está asociado a un identificador.

### <a name="remarks"></a>Observaciones

## <a name="isfallback"></a><a name="isfallback"></a>IsFallback

Determina si las llamadas de reserva están habilitadas.

```
BOOL IsFallback() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE es la clase admite llamadas de reserva. FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

## <a name="m_bfallback"></a><a name="m_bfallback"></a>m_bFallback

TRUESi se admite la reserva; FALSE en caso contrario.

```
BOOL m_bFallback;
```

### <a name="remarks"></a>Observaciones

## <a name="m_htransaction"></a><a name="m_htransaction"></a>m_hTransaction

El identificador de transacción.

```
HANDLE m_hTransaction;
```

### <a name="remarks"></a>Observaciones

## <a name="movefile"></a><a name="movefile"></a>MoveFile

Mueve un archivo existente o un directorio, incluidos sus elementos secundarios, como una operación de transacción.

```
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```

### <a name="parameters"></a>Parámetros

*lpOldFileName*<br/>
El nombre actual del archivo o directorio existente en el equipo local.

*lpNewFileName*<br/>
El nuevo nombre del archivo o directorio. Este nombre no debe existir ya. Un nuevo archivo puede estar en un sistema de archivos o unidad diferente. Un nuevo directorio debe estar en la misma unidad.

### <a name="remarks"></a>Observaciones

Este contenedor `MoveFileTransacted` llama a la función.

## <a name="regcreatekeyex"></a><a name="regcreatekeyex"></a>RegCreateKeyEx

Crea la clave del Registro especificada y la asocia a una transacción. Si la clave ya existe, la función la abre.

```
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
Identificador de una clave de registro abierta.

*lpSubKey*<br/>
El nombre de una subclave que esta función abre o crea.

*dwReserved*<br/>
Este parámetro está reservado y debe ser cero.

*lpClass*<br/>
La clase definida por el usuario de esta clave. Este parámetro puede omitirse. Este parámetro puede ser NULL.

*dwOptions*<br/>
Este parámetro puede ser uno de los siguientes valores: REG_OPTION_BACKUP_RESTORE, REG_OPTION_NON_VOLATILE o REG_OPTION_VOLATILE.

*samDesired*<br/>
Máscara que especifica los derechos de acceso de la clave.

*lpSecurityAttributes*<br/>
Puntero a una estructura de SECURITY_ATTRIBUTES que determina si el identificador devuelto se puede heredar de procesos secundarios. Si *lpSecurityAttributes* es NULL, el identificador no se puede heredar.

*phkResult*<br/>
Puntero a una variable que recibe un identificador de la clave abierta o creada. Si la clave no es una de las `RegCloseKey` claves de registro predefinidas, llame a la función después de haber terminado de usar el identificador.

*lpdwDisposition*<br/>
Puntero a una variable que recibe uno de los siguientes valores de disposición: REG_CREATED_NEW_KEY o REG_OPENED_EXISTING_KEY.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto se ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror.h.

### <a name="remarks"></a>Observaciones

Este contenedor `RegCreateKeyTransacted` llama a la función.

## <a name="regdeletekey"></a><a name="regdeletekey"></a>RegDeleteKey

Elimina una subclave y sus valores de la vista específica de la plataforma especificada del registro como una operación de transacción.

```
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*hKey*|Identificador de una clave de registro abierta.|
|*lpSubKey*|El nombre de la clave que se va a eliminar.|

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto se ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror.h.

### <a name="remarks"></a>Observaciones

Este contenedor `RegDeleteKeyTransacted` llama a la función.

## <a name="regopenkeyex"></a><a name="regopenkeyex"></a>RegOpenKeyEx

Abre la clave del Registro especificada y la asocia a una transacción.

```
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```

### <a name="parameters"></a>Parámetros

*hKey*<br/>
Identificador de una clave de registro abierta.

*lpSubKey*<br/>
El nombre de la subclave del Registro que se va a abrir.

*ulOptions*<br/>
Este parámetro está reservado y debe ser cero.

*samDesired*<br/>
Máscara que especifica los derechos de acceso de la clave.

*phkResult*<br/>
Puntero a una variable que recibe un identificador de la clave abierta o creada. Si la clave no es una de las `RegCloseKey` claves de registro predefinidas, llame a la función después de haber terminado de usar el identificador.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto se ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror.h

### <a name="remarks"></a>Observaciones

Este contenedor `RegOpenKeyTransacted` llama a la función.

## <a name="rollback"></a><a name="rollback"></a>Rollback

Solicita que se revierta la transacción.

```
inline BOOL Rollback();
```

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este contenedor `RollbackTransaction` llama a la función.

## <a name="setfileattributes"></a><a name="setfileattributes"></a>SetFileAttributes

Establece los atributos de un archivo o directorio como una operación de transacción.

```
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```

### <a name="parameters"></a>Parámetros

*lpFileName*<br/>
El nombre del archivo o directorio.

*dwAttributes*<br/>
Los atributos de archivo que se establecerán para el archivo. Para obtener más información, vea [SetFileAttributesTransacted](/windows/win32/api/winbase/nf-winbase-setfileattributestransactedw).

### <a name="remarks"></a>Observaciones

Este contenedor `SetFileAttributesTransacted` llama a la función.

## <a name="see-also"></a>Consulte también

[Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md)
