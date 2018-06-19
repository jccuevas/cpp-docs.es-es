---
title: Clase CAtlTransactionManager | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlTransactionManager class
ms.assetid: b01732dc-1d16-4b42-bfac-b137fca2b740
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02ab9cd6f8867f9e6bc9d81ff825e8fe8f7b57d7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365944"
---
# <a name="catltransactionmanager-class"></a>Clase CAtlTransactionManager
Clase CAtlTransactionManager proporciona un contenedor para las funciones de administrador de transacciones de Kernel (KTM).  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CAtlTransactionManager;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[~ CAtlTransactionManager](#dtor)|Destructor de CAtlTransactionManager.|  
|[CAtlTransactionManager](#catltransactionmanager)|Constructor CAtlTransactionManager.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Cerrar](#close)|Uno cierra el identificador de transacción.|  
|[Confirmación](#commit)|Solicitudes que se confirma la transacción.|  
|[Crear](#create)|Crea el identificador de transacción.|  
|[CreateFile](#createfile)|Crea o abre un archivo, una secuencia de archivos o un directorio como una operación con transacciones.|  
|[DeleteFile](#deletefile)|Elimina un archivo existente como una operación con transacciones.|  
|[FindFirstFile](#findfirstfile)|Busca un directorio de un archivo o un subdirectorio como una operación con transacciones.|  
|[GetFileAttributes](#getfileattributes)|Recupera los atributos de sistema de archivos para un archivo o directorio especificado como una operación con transacciones.|  
|[GetFileAttributesEx](#getfileattributesex)|Recupera los atributos de sistema de archivos para un archivo o directorio especificado como una operación con transacciones.|  
|[GetHandle](#gethandle)|Devuelve el identificador de transacción.|  
|[IsFallback](#isfallback)|Determina si están habilitadas las llamadas de reserva.|  
|[MoveFile](#movefile)|Mueve un archivo existente o un directorio, incluidos a sus elementos secundarios, como una operación con transacciones.|  
|[RegCreateKeyEx](#regcreatekeyex)|Crea la clave del registro especificada y lo asocia con una transacción. Si la clave ya existe, la función lo abre.|  
|[RegDeleteKey](#regdeletekey)|Elimina una subclave y sus valores de la vista específica de la plataforma especificada del registro como una operación con transacciones.|  
|[Error en RegOpenKeyEx](#regopenkeyex)|Abre la clave del registro especificada y lo asocia con una transacción.|  
|[Reversión](#rollback)|Solicitudes que se revierte la transacción.|  
|[SetFileAttributes](#setfileattributes)|Establece los atributos de un archivo o directorio como una operación con transacciones.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[m_bFallback](#m_bfallback)|`TRUE` Si la reserva es compatible; `FALSE` en caso contrario.|  
|[m_hTransaction](#m_htransaction)|El identificador de la transacción.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [ATL::CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atltransactionmanager.h  
  
##  <a name="dtor"></a>  ~ CAtlTransactionManager  
 Destructor de CAtlTransactionManager.  
  
```
virtual ~CAtlTransactionManager();
```  
  
### <a name="remarks"></a>Comentarios  
 En el procesamiento normal, la transacción se confirma automáticamente y cerrada. Si se llama al destructor durante una operación de desenredo de la excepción, la transacción se revierte y se cierra.  
  
##  <a name="catltransactionmanager"></a>  CAtlTransactionManager  
 Constructor CAtlTransactionManager.  
  
```
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bFallback`  
 `TRUE` Indica compatibilidad con reserva. Si se produce un error en la transacción de función, la clase llama automáticamente a la función "sin transacciones". `FALSE` indica que no hay llamadas "reserva".  
  
 `bAutoCreateTransaction`  
 `TRUE` indica que el controlador de transacciones se crea automáticamente en el constructor. `FALSE` indica que no lo están.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="close"></a>  Cerrar  
 Cierra el identificador de transacción.  
  
```
inline BOOL Close();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si es correcto; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llama a este contenedor el `CloseHandle` función. Automáticamente se llama al método en el destructor.  
  
##  <a name="commit"></a>  Confirmación  
 Solicitudes que se confirma la transacción.  
  
```
inline BOOL Commit();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si es correcto; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llama a este contenedor el `CommitTransaction` función. Automáticamente se llama al método en el destructor.  
  
##  <a name="create"></a>  Crear  
 Crea el identificador de transacción.  
  
```
inline BOOL Create();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si es correcto; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llama a este contenedor el `CreateTransaction` función. Consulte  
  
##  <a name="createfile"></a>  Creación de archivo  
 Crea o abre un archivo, una secuencia de archivos o un directorio como una operación con transacciones.  
  
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
 `lpFileName`  
 El nombre de un objeto para crear o abrir.  
  
 `dwDesiredAccess`  
 El acceso al objeto, que se puede resumir de lectura, escritura, ambos o ninguno (cero). Los valores más usados son GENERIC_READ, GENERIC_WRITE o ambos: GENERIC_READ &#124; GENERIC_WRITE.  
  
 `dwShareMode`  
 El modo de uso compartido de un objeto, que pueden ser de lectura, escritura, ambos, eliminar, todos ellos o ninguno: 0, FILE_SHARE_DELETE, FILE_SHARE_READ, FILE_SHARE_WRITE.  
  
 `lpSecurityAttributes`  
 Un puntero a una estructura SECURITY_ATTRIBUTES que contiene un descriptor de seguridad opcional y también determina si se permite o no el identificador devuelto se puede heredar mediante procesos secundarios. El parámetro puede ser `NULL`.  
  
 `dwCreationDisposition`  
 Acción que se realizan sobre los archivos que existen y no existen. Este parámetro debe ser uno de los valores siguientes, que no se pueden combinar: CREATE_ALWAYS, CREATE_NEW, OPEN_ALWAYS, OPEN_EXISTING o TRUNCATE_EXISTING.  
  
 `dwFlagsAndAttributes`  
 Los atributos de archivo y las marcas. Este parámetro puede incluir cualquier combinación de los atributos de archivo disponibles (FILE_ATTRIBUTE_ *). Todos los demás atributos de archivo invalidan FILE_ATTRIBUTE_NORMAL. Este parámetro puede contener también combinaciones de indicadores (FILE_FLAG_\*) para el control de comportamiento de almacenamiento en búfer, tener acceso a modos y otras marcas de propósito especial. Estos valores se combinan con cualquier FILE_ATTRIBUTE_\* valores.  
  
 `hTemplateFile`  
 Un identificador válido en un archivo de plantilla con el derecho de acceso GENERIC_READ. El archivo de plantilla proporciona los atributos de archivo y sus atributos extendidos para el archivo que se va a crear. Este parámetro puede ser `NULL`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un identificador que puede utilizarse para tener acceso al objeto.  
  
### <a name="remarks"></a>Comentarios  
 Llama a este contenedor el `CreateFileTransacted` función.  
  
##  <a name="deletefile"></a>  DeleteFile  
 Elimina un archivo existente como una operación con transacciones.  
  
```
inline BOOL DeleteFile(LPCTSTR lpFileName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpFileName`  
 Nombre del archivo que se va a eliminar.  
  
### <a name="remarks"></a>Comentarios  
 Llama a este contenedor el `DeleteFileTransacted` función.  
  
##  <a name="findfirstfile"></a>  FindFirstFile  
 Busca un directorio de un archivo o un subdirectorio como una operación con transacciones.  
  
```
inline HANDLE FindFirstFile(
  LPCTSTR lpFileName,
  WIN32_FIND_DATA* pNextInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpFileName`  
 El directorio o ruta de acceso y el nombre de archivo que se buscará. Este parámetro puede incluir caracteres comodín, como un asterisco (*) o un (signo de interrogación).  
  
 `pNextInfo`  
 Un puntero a la estructura WIN32_FIND_DATA que recibe información sobre un archivo se encuentra o un subdirectorio.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es un identificador de búsqueda que se utiliza en una llamada subsiguiente a `FindNextFile` o `FindClose`. Si la función genera un error o buscar archivos de la cadena de búsqueda en el `lpFileName` parámetro, el valor devuelto es INVALID_HANDLE_VALUE.  
  
### <a name="remarks"></a>Comentarios  
 Llama a este contenedor el `FindFirstFileTransacted` función.  
  
##  <a name="getfileattributes"></a>  GetFileAttributes  
 Recupera los atributos de sistema de archivos para un archivo o directorio especificado como una operación con transacciones.  
  
```
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpFileName`  
 El nombre del archivo o directorio.  
  
### <a name="remarks"></a>Comentarios  
 Llama a este contenedor el `GetFileAttributesTransacted` función.  
  
##  <a name="getfileattributesex"></a>  GetFileAttributesEx  
 Recupera los atributos de sistema de archivos para un archivo o directorio especificado como una operación con transacciones.  
  
```
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpFileName`  
 El nombre del archivo o directorio.  
  
 `fInfoLevelId`  
 El nivel de información de atributo que se va a recuperar.  
  
 `lpFileInformation`  
 Un puntero a un búfer que recibe la información del atributo. El tipo de información de atributos que se almacena en este búfer se determina por el valor de `fInfoLevelId`. Si el `fInfoLevelId` parámetro es GetFileExInfoStandard, a continuación, este parámetro señala a una estructura WIN32_FILE_ATTRIBUTE_DATA.  
  
### <a name="remarks"></a>Comentarios  
 Llama a este contenedor el `GetFileAttributesTransacted` función.  
  
##  <a name="gethandle"></a>  GetHandle  
 Devuelve el identificador de transacción.  
  
```
HANDLE GetHandle() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el identificador de transacción para una clase. Devuelve `NULL` si el `CAtlTransactionManager` no está conectado a un identificador.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isfallback"></a>  IsFallback  
 Determina si están habilitadas las llamadas de reserva.  
  
```
BOOL IsFallback() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` es la clase es compatible con llamadas de reserva. En caso contrario, es `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_bfallback"></a>  m_bFallback  
 `TRUE` Si la reserva es compatible; `FALSE` en caso contrario.  
  
```
BOOL m_bFallback;
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_htransaction"></a>  m_hTransaction  
 El identificador de la transacción.  
  
```
HANDLE m_hTransaction;
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="movefile"></a>  MoveFile  
 Mueve un archivo existente o un directorio, incluidos a sus elementos secundarios, como una operación con transacciones.  
  
```
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpOldFileName`  
 El nombre actual del directorio en el equipo local o archivo existente.  
  
 `lpNewFileName`  
 El nuevo nombre para el archivo o directorio. Este nombre no debe existir. Puede ser un nuevo archivo en un sistema de archivos diferente o la unidad. Debe ser un nuevo directorio en la misma unidad.  
  
### <a name="remarks"></a>Comentarios  
 Llama a este contenedor el `MoveFileTransacted` función.  
  
##  <a name="regcreatekeyex"></a>  RegCreateKeyEx  
 Crea la clave del registro especificada y lo asocia con una transacción. Si la clave ya existe, la función lo abre.  
  
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
 `hKey`  
 Un identificador a una clave del registro abierta.  
  
 `lpSubKey`  
 El nombre de una subclave que esta función se abre o se crea.  
  
 `dwReserved`  
 Este parámetro está reservado y debe ser cero.  
  
 `lpClass`  
 La clase definida por el usuario de esta clave. Este parámetro se puede omitir. Este parámetro puede ser NULL.  
  
 `dwOptions`  
 Este parámetro puede ser uno de los siguientes valores: REG_OPTION_BACKUP_RESTORE, REG_OPTION_NON_VOLATILE o REG_OPTION_VOLATILE.  
  
 `samDesired`  
 Máscara que especifica los derechos de acceso para la clave.  
  
 `lpSecurityAttributes`  
 Puntero a una estructura SECURITY_ATTRIBUTES que determina si los procesos secundarios puede heredar el identificador devuelto. Si `lpSecurityAttributes` es `NULL`, el identificador no puede heredarse.  
  
 `phkResult`  
 Un puntero a una variable que recibe un identificador de la clave creado o abierto. Si la clave no es una de las claves del registro predefinida, llame a la `RegCloseKey` funcionando después de que haya terminado de utilizar el identificador.  
  
 `lpdwDisposition`  
 Un puntero a una variable que recibe uno de los siguientes valores de disposición: REG_CREATED_NEW_KEY o REG_OPENED_EXISTING_KEY.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror.h.  
  
### <a name="remarks"></a>Comentarios  
 Llama a este contenedor el `RegCreateKeyTransacted` función.  
  
##  <a name="regdeletekey"></a>  RegDeleteKey  
 Elimina una subclave y sus valores de la vista específica de la plataforma especificada del registro como una operación con transacciones.  
  
```
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`hKey`|Un identificador a una clave del registro abierta.|  
|`lpSubKey`|El nombre de la clave que se va a eliminar.|  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror.h.  
  
### <a name="remarks"></a>Comentarios  
 Llama a este contenedor el `RegDeleteKeyTransacted` función.  
  
##  <a name="regopenkeyex"></a>  Error en RegOpenKeyEx  
 Abre la clave del registro especificada y lo asocia con una transacción.  
  
```
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```  
  
### <a name="parameters"></a>Parámetros  
 `hKey`  
 Un identificador a una clave del registro abierta.  
  
 `lpSubKey`  
 El nombre de la subclave del registro que se abran.  
  
 `ulOptions`  
 Este parámetro está reservado y debe ser cero.  
  
 `samDesired`  
 Máscara que especifica los derechos de acceso para la clave.  
  
 `phkResult`  
 Un puntero a una variable que recibe un identificador de la clave creado o abierto. Si la clave no es una de las claves del registro predefinida, llame a la `RegCloseKey` funcionando después de que haya terminado de utilizar el identificador.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror.h  
  
### <a name="remarks"></a>Comentarios  
 Llama a este contenedor el `RegOpenKeyTransacted` función.  
  
##  <a name="rollback"></a>  Reversión  
 Solicitudes que se revierte la transacción.  
  
```
inline BOOL Rollback();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si es correcto; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llama a este contenedor el `RollbackTransaction` función.  
  
##  <a name="setfileattributes"></a>  SetFileAttributes  
 Establece los atributos de un archivo o directorio como una operación con transacciones.  
  
```
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpFileName`  
 El nombre del archivo o directorio.  
  
 `dwAttributes`  
 Los atributos de archivo establecido para el archivo. Para obtener más información, consulte [SetFileAttributesTransacted](http://go.microsoft.com/fwlink/p/?linkid=158699).  
  
### <a name="remarks"></a>Comentarios  
 Llama a este contenedor el `SetFileAttributesTransacted` función.  
  
## <a name="see-also"></a>Vea también  
 [Componentes de escritorio COM de ATL](../../atl/atl-com-desktop-components.md)
