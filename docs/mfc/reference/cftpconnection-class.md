---
title: Clase CFtpConnection
ms.date: 08/29/2019
f1_keywords:
- CFtpConnection
- AFXINET/CFtpConnection
- AFXINET/CFtpConnection::CFtpConnection
- AFXINET/CFtpConnection::Command
- AFXINET/CFtpConnection::CreateDirectory
- AFXINET/CFtpConnection::GetCurrentDirectory
- AFXINET/CFtpConnection::GetCurrentDirectoryAsURL
- AFXINET/CFtpConnection::GetFile
- AFXINET/CFtpConnection::OpenFile
- AFXINET/CFtpConnection::PutFile
- AFXINET/CFtpConnection::Remove
- AFXINET/CFtpConnection::RemoveDirectory
- AFXINET/CFtpConnection::Rename
- AFXINET/CFtpConnection::SetCurrentDirectory
helpviewer_keywords:
- CFtpConnection [MFC], CFtpConnection
- CFtpConnection [MFC], Command
- CFtpConnection [MFC], CreateDirectory
- CFtpConnection [MFC], GetCurrentDirectory
- CFtpConnection [MFC], GetCurrentDirectoryAsURL
- CFtpConnection [MFC], GetFile
- CFtpConnection [MFC], OpenFile
- CFtpConnection [MFC], PutFile
- CFtpConnection [MFC], Remove
- CFtpConnection [MFC], RemoveDirectory
- CFtpConnection [MFC], Rename
- CFtpConnection [MFC], SetCurrentDirectory
ms.assetid: 5e3a0501-8893-49cf-a3d5-0628d8d6b936
ms.openlocfilehash: a1fe516869aa98cc291597211eee175ef591e45d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373773"
---
# <a name="cftpconnection-class"></a>Clase CFtpConnection

Administra su conexión FTP a un servidor de Internet y permite la manipulación directa de directorios y archivos en ese servidor.

## <a name="syntax"></a>Sintaxis

```
class CFtpConnection : public CInternetConnection
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFtpConnection::CFtpConnection](#cftpconnection)|Construye un objeto `CFtpConnection`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFtpConnection::Command](#command)|Envía un comando directamente a un servidor FTP.|
|[CFtpConnection::CreateDirectory](#createdirectory)|Crea un directorio en el servidor.|
|[CFtpConnection::GetCurrentDirectory](#getcurrentdirectory)|Obtiene el directorio actual para esta conexión.|
|[CFtpConnection::GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)|Obtiene el directorio actual para esta conexión como una dirección URL.|
|[CFtpConnection::GetFile](#getfile)|Obtiene un archivo del servidor conectado|
|[CFtpConnection::OpenFile](#openfile)|Abre un archivo en el servidor conectado.|
|[CFtpConnection::PutFile](#putfile)|Coloca un archivo en el servidor.|
|[CFtpConnection::Quitar](#remove)|Quita un archivo del servidor.|
|[CFtpConnection::RemoveDirectory](#removedirectory)|Quita el directorio especificado del servidor.|
|[CFtpConnection::Rename](#rename)|Cambia el nombre de un archivo en el servidor.|
|[CFtpConnection::SetCurrentDirectory](#setcurrentdirectory)|Establece el directorio FTP actual.|

## <a name="remarks"></a>Observaciones

FTP es uno de los tres servicios de Internet reconocidos por las clases WinInet de MFC.

Para comunicarse con un servidor de Internet FTP, primero debe crear `CFtpConnection` una instancia de [CInternetSession](../../mfc/reference/cinternetsession-class.md)y, a continuación, crear un objeto. Nunca se `CFtpConnection` crea un objeto directamente; en su lugar, llame a [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), que crea el `CFtpConnection` objeto y devuelve un puntero a él.

Para obtener más `CFtpConnection` información sobre cómo funciona con las otras clases de Internet MFC, vea el artículo Programación de [Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md). Para obtener más información acerca de la comunicación con los otros dos servicios admitidos, HTTP y gopher, vea las clases [CHttpConnection](../../mfc/reference/chttpconnection-class.md) y [CGopherConnection](../../mfc/reference/cgopherconnection-class.md).

## <a name="example"></a>Ejemplo

  Vea el ejemplo en la información general de la clase [CFtpFileFind.](../../mfc/reference/cftpfilefind-class.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

## <a name="cftpconnectioncftpconnection"></a><a name="cftpconnection"></a>CFtpConnection::CFtpConnection

Esta función miembro se `CFtpConnection` llama para construir un objeto.

```
CFtpConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CFtpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 0,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    BOOL bPassive = FALSE);
```

### <a name="parameters"></a>Parámetros

*pSession*<br/>
Un puntero al objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) relacionado.

*hConectado*<br/>
El identificador de Windows de la sesión de Internet actual.

*pstrServer*<br/>
Puntero a una cadena que contiene el nombre del servidor FTP.

*dwContext*<br/>
Identificador de contexto para la operación. *dwContext* identifica la información de estado de la operación devuelta por [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). El valor predeterminado se establece en 1; sin embargo, puede asignar explícitamente un identificador de contexto específico para la operación. El objeto y cualquier trabajo que realice se asociarán con ese identificador de contexto.

*pstrUserName*<br/>
Puntero a una cadena terminada en null que especifica el nombre del usuario para iniciar sesión. Si NULL, el valor predeterminado es anónimo.

*pstrPassword*<br/>
Puntero a una cadena terminada en null que especifica la contraseña que se usará para iniciar sesión. Si *pstrPassword* y *pstrUserName* son NULL, la contraseña anónima predeterminada es el nombre de correo electrónico del usuario. Si *pstrPassword* es NULL (o una cadena vacía) pero *pstrUserName* no es NULL, se usa una contraseña en blanco. En la tabla siguiente se describe el comportamiento de las cuatro configuraciones posibles de *pstrUserName* y *pstrPassword:*

|*pstrUserName*|*pstrPassword*|Nombre de usuario enviado al servidor FTP|Contraseña enviada al servidor FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL o " "|NULL o " "|"anónimo"|Nombre de correo electrónico del usuario|
|Cadena no NUNULL|NULL o " "|*pstrUserName*|" "|
|NULL Non- NULL String|ERROR|ERROR||
|Cadena no NUNULL|Cadena no NUNULL|*pstrUserName*|*pstrPassword*|

*Nport*<br/>
Número que identifica el puerto TCP/IP que se va a utilizar en el servidor.

*bPasivo*<br/>
Especifica el modo pasivo o activo para esta sesión FTP. Si se establece en TRUE, establece la API de Win32 *dwFlag en* INTERNET_FLAG_PASSIVE.

### <a name="remarks"></a>Observaciones

Nunca se `CFtpConnection` crea un objeto directamente. En su lugar, llame a [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), que crea el `CFptConnection` objeto.

## <a name="cftpconnectioncommand"></a><a name="command"></a>CFtpConnection::Command

Envía un comando directamente a un servidor FTP.

```
CInternetFile* Command(
    LPCTSTR pszCommand,
    CmdResponseType eResponse = CmdRespNone,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parámetros

*pszCommand*<br/>
Un puntero a una cadena que contiene el comando que se enviará.

*eResponse*<br/>
Especifica si se espera una respuesta del servidor FTP. Puede ser uno de los siguientes valores:

- `CmdRespNone`No se espera respuesta.
- `CmdRespRead`Se espera una respuesta.
- `CmdRespWrite`No se usa.

CmdResponseType es un miembro de CFtpConnection, definido en *afxinet.h*.

*dwFlags*<br/>
Un valor que contiene las marcas que controlan esta función. Para obtener una lista completa, consulte [FTPCommand](/windows/win32/api/wininet/nf-wininet-ftpcommandw).

*dwContext*<br/>
Un puntero a un valor que contiene un valor definido por la aplicación, que se utiliza para identificar el contexto de la aplicación en las devoluciones de llamada.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro emula la funcionalidad de la función [FTPCommand,](/windows/win32/api/wininet/nf-wininet-ftpcommandw) como se describe en el Windows SDK.

Si se produce un error, MFC produce una excepción de tipo [CInternetException](../../mfc/reference/cinternetexception-class.md).

## <a name="cftpconnectioncreatedirectory"></a><a name="createdirectory"></a>CFtpConnection::CreateDirectory

Llame a esta función miembro para crear un directorio en el servidor conectado.

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parámetros

*pstrDirName*<br/>
Puntero a una cadena que contiene el nombre del directorio que se va a crear.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función de Windows [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para determinar la causa del error.

### <a name="remarks"></a>Observaciones

Se `GetCurrentDirectory` utiliza para determinar el directorio de trabajo actual para esta conexión con el servidor. No asuma que el sistema remoto le ha conectado al directorio raíz.

El `pstrDirName` parámetro puede ser un nombre de archivo parcial o completo en relación con el directorio actual. Se puede\\utilizar una barra diagonal inversa ( ) o una barra diagonal (/) como separador de directorios para cualquiera de los nombres. `CreateDirectory`traduce los separadores de nombre de directorio a los caracteres adecuados antes de que se utilicen.

## <a name="cftpconnectiongetcurrentdirectory"></a><a name="getcurrentdirectory"></a>CFtpConnection::GetCurrentDirectory

Llame a esta función miembro para obtener el nombre del directorio actual.

```
BOOL GetCurrentDirectory(CString& strDirName) const;

BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Parámetros

*strDirName*<br/>
Una referencia a una cadena que recibirá el nombre del directorio.

*pstrDirName*<br/>
Puntero a una cadena que recibirá el nombre del directorio.

*lpdwLen*<br/>
Puntero a un DWORD que contiene la siguiente información:

|||
|-|-|
|A la entrada|El tamaño del búfer al que hace referencia *pstrDirName*.|
|A la vuelta|El número de caracteres almacenados en *pstrDirName*. Si se produce un error en la función miembro y se devuelve ERROR_INSUFFICIENT_BUFFER, *lpdwLen* contiene el número de bytes que la aplicación debe asignar para recibir la cadena.|

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) de Win32 para determinar la causa del error.

### <a name="remarks"></a>Observaciones

Para obtener el nombre del directorio como una dirección URL, llame a [GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl).

Los parámetros *pstrDirName* o *strDirName* pueden ser nombres de archivo parcialmente calificados en relación con el directorio actual o completos. Se puede\\utilizar una barra diagonal inversa ( ) o una barra diagonal (/) como separador de directorios para cualquiera de los nombres. `GetCurrentDirectory`traduce los separadores de nombre de directorio a los caracteres adecuados antes de que se utilicen.

## <a name="cftpconnectiongetcurrentdirectoryasurl"></a><a name="getcurrentdirectoryasurl"></a>CFtpConnection::GetCurrentDirectoryAsURL

Llame a esta función miembro para obtener el nombre del directorio actual como una dirección URL.

```
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;

BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Parámetros

*strDirName*<br/>
Una referencia a una cadena que recibirá el nombre del directorio.

*pstrDirName*<br/>
Puntero a una cadena que recibirá el nombre del directorio.

*lpdwLen*<br/>
Puntero a un DWORD que contiene la siguiente información:

|||
|-|-|
|A la entrada|El tamaño del búfer al que hace referencia *pstrDirName*.|
|A la vuelta|El número de caracteres almacenados en *pstrDirName*. Si se produce un error en la función miembro y se devuelve ERROR_INSUFFICIENT_BUFFER, *lpdwLen* contiene el número de bytes que la aplicación debe asignar para recibir la cadena.|

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) de Win32 para determinar la causa del error.

### <a name="remarks"></a>Observaciones

`GetCurrentDirectoryAsURL`se comporta igual que [GetCurrentDirectory](#getcurrentdirectory)

El parámetro *strDirName* puede ser nombres de archivo parcialmente calificados en relación con el directorio actual o completos. Se puede\\utilizar una barra diagonal inversa ( ) o una barra diagonal (/) como separador de directorios para cualquiera de los nombres. `GetCurrentDirectoryAsURL`traduce los separadores de nombre de directorio a los caracteres adecuados antes de que se utilicen.

## <a name="cftpconnectiongetfile"></a><a name="getfile"></a>CFtpConnection::GetFile

Llame a esta función miembro para obtener un archivo de un servidor FTP y almacenarlo en el equipo local.

```
BOOL GetFile(
    LPCTSTR pstrRemoteFile,
    LPCTSTR pstrLocalFile,
    BOOL bFailIfExists = TRUE,
    DWORD dwAttributes = FILE_ATTRIBUTE_NORMAL,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parámetros

*pstrRemoteFile*<br/>
Puntero a una cadena terminada en null que contiene el nombre de un archivo que se va a recuperar del servidor FTP.

*pstrLocalFile*<br/>
Puntero a una cadena terminada en null que contiene el nombre del archivo que se va a crear en el sistema local.

*bFailIfExists*<br/>
Indica si un archivo existente ya puede utilizar el nombre de archivo. Si el nombre de archivo local ya `GetFile` existe y este parámetro es TRUE, se produce un error. De `GetFile` lo contrario, borrará la copia existente del archivo.

*dwAttributes*<br/>
Indica los atributos del archivo. Puede ser cualquier combinación de los siguientes indicadores FILE_ATTRIBUTE_*.

- FILE_ATTRIBUTE_ARCHIVE El archivo es un archivo de almacenamiento. Las aplicaciones utilizan este atributo para marcar los archivos para la copia de seguridad o eliminación.

- FILE_ATTRIBUTE_COMPRESSED El archivo o directorio está comprimido. Para un archivo, la compresión significa que todos los datos del archivo están comprimidos. Para un directorio, la compresión es el valor predeterminado para los archivos y subdirectorios recién creados.

- FILE_ATTRIBUTE_DIRECTORY El archivo es un directorio.

- FILE_ATTRIBUTE_NORMAL El archivo no tiene ningún otro atributo establecido. Este atributo solo es válido si se usa solo. Todos los demás atributos de archivo anulan FILE_ATTRIBUTE_NORMAL:

- FILE_ATTRIBUTE_HIDDEN El archivo está oculto. No debe incluirse en una lista de directorios normal.

- FILE_ATTRIBUTE_READONLY El archivo es de solo lectura. Las aplicaciones pueden leer el archivo, pero no pueden escribir en él ni eliminarlo.

- FILE_ATTRIBUTE_SYSTEM El archivo forma parte o es utilizado exclusivamente por el sistema operativo.

- FILE_ATTRIBUTE_TEMPORARY El archivo se utiliza para el almacenamiento temporal. Las aplicaciones deben escribir en el archivo sólo si es absolutamente necesario. La mayoría de los datos del archivo permanecen en la memoria sin ser vaciados en el medio porque el archivo se eliminará pronto.

*dwFlags*<br/>
Especifica las condiciones en las que se produce la transferencia. Este parámetro puede ser cualquiera de los *valores dwFlags* descritos en [FtpGetFile](/windows/win32/api/wininet/nf-wininet-ftpgetfilew) en el Windows SDK.

*dwContext*<br/>
Identificador de contexto para la recuperación de archivos. Consulte **Comentarios** para obtener más información sobre *dwContext*.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) de Win32 para determinar la causa del error.

### <a name="remarks"></a>Observaciones

`GetFile`es una rutina de alto nivel que controla toda la sobrecarga asociada con la lectura de un archivo de un servidor FTP y el almacenamiento local. Las aplicaciones que solo recuperan datos de archivo, o `OpenFile` que requieren un control estrecho sobre la transferencia de archivos, deben usar y [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read) en su lugar.

Si *dwFlags* se FILE_TRANSFER_TYPE_ASCII, la traducción de datos de archivo también convierte los caracteres de control y formato a equivalentes de Windows. La transferencia predeterminada es el modo binario, donde el archivo se descarga en el mismo formato que se almacena en el servidor.

*PstrRemoteFile* y *pstrLocalFile* pueden ser nombres de archivo parcialmente calificados en relación con el directorio actual o completos. Se puede\\utilizar una barra diagonal inversa ( ) o una barra diagonal (/) como separador de directorios para cualquiera de los nombres. `GetFile`traduce los separadores de nombre de directorio a los caracteres adecuados antes de que se utilicen.

Invalide el valor predeterminado *dwContext* para establecer el identificador de contexto en un valor de su elección. El identificador de contexto está asociado `CFtpConnection` a esta operación específica del objeto creado por su [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto. El valor se devuelve a [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con la que se identifica. Consulte el artículo Primeros pasos de [Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

## <a name="cftpconnectionopenfile"></a><a name="openfile"></a>CFtpConnection::OpenFile

Llame a esta función miembro para abrir un archivo ubicado en un servidor FTP para leer o escribir.

```
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,
    DWORD dwAccess = GENERIC_READ,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parámetros

*pstrFileName*<br/>
Puntero a una cadena que contiene el nombre del archivo que se va a abrir.

*dwAccess*<br/>
Determina cómo se accederá al archivo. Puede ser GENERIC_READ o GENERIC_WRITE, pero no ambos.

*dwFlags*<br/>
Especifica las condiciones en las que se producen las transferencias posteriores. Puede ser cualquiera de las siguientes constantes FTP_TRANSFER_*:

- FTP_TRANSFER_TYPE_ASCII Las transferencias de archivos mediante el método de transferencia FTP ASCII (Tipo A). Convierte la información de control y formato en equivalentes locales.

- FTP_TRANSFER_TYPE_BINARY El archivo transfiere datos mediante el método de transferencia imagen (tipo I) de FTP. El archivo transfiere los datos exactamente como existen, sin cambios. Este es el método de transferencia predeterminado.

*dwContext*<br/>
Identificador de contexto para abrir el archivo. Consulte **Comentarios** para obtener más información sobre *dwContext*.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CInternetFile](../../mfc/reference/cinternetfile-class.md) objeto.

### <a name="remarks"></a>Observaciones

`OpenFile`debe utilizarse en las siguientes situaciones:

- Una aplicación tiene datos que deben enviarse y crearse como un archivo en el servidor FTP, pero esos datos no están en un archivo local. Una `OpenFile` vez que abre un archivo, la aplicación utiliza [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write) para enviar los datos del archivo FTP al servidor.

- Una aplicación debe recuperar un archivo del servidor y colocarlo en la memoria controlada por la aplicación, en lugar de escribirlo en el disco. La aplicación utiliza [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read) después de usar `OpenFile` para abrir el archivo.

- Una aplicación necesita un nivel fino de control sobre una transferencia de archivos. Por ejemplo, es posible que la aplicación desee mostrar un control de progreso para indicar el progreso del estado de transferencia de archivos durante la descarga de un archivo.

Después `OpenFile` de `CInternetConnection::Close`llamar y hasta llamar a , la aplicación solo puede `CInternetConnection::Close`llamar a [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read), [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write), o [CFtpFileFind::FindFile](../../mfc/reference/cftpfilefind-class.md#findfile). Las llamadas a otras funciones FTP para la misma sesión FTP fallarán y establecerán el código de error en FTP_ETRANSFER_IN_PROGRESS.

El parámetro *pstrFileName* puede ser un nombre de archivo parcialmente calificado en relación con el directorio actual o completo. Se puede\\utilizar una barra diagonal inversa ( ) o una barra diagonal (/) como separador de directorios para cualquiera de los nombres. `OpenFile`traduce los separadores de nombre de directorio a los caracteres adecuados antes de usarlo.

Invalide el valor predeterminado *dwContext* para establecer el identificador de contexto en un valor de su elección. El identificador de contexto está asociado `CFtpConnection` a esta operación específica del objeto creado por su [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto. El valor se devuelve a [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con la que se identifica. Consulte el artículo Primeros pasos de [Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

## <a name="cftpconnectionputfile"></a><a name="putfile"></a>CFtpConnection::PutFile

Llame a esta función miembro para almacenar un archivo en un servidor FTP.

```
BOOL PutFile(
    LPCTSTR pstrLocalFile,
    LPCTSTR pstrRemoteFile,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parámetros

*pstrLocalFile*<br/>
Puntero a una cadena que contiene el nombre del archivo que se va a enviar desde el sistema local.

*pstrRemoteFile*<br/>
Puntero a una cadena que contiene el nombre del archivo que se va a crear en el servidor FTP.

*dwFlags*<br/>
Especifica las condiciones en las que se produce la transferencia del archivo. Puede ser cualquiera de las constantes FTP_TRANSFER_* descritas en [OpenFile](#openfile).

*dwContext*<br/>
Identificador de contexto para colocar el archivo. Consulte **Comentarios** para obtener más información sobre *dwContext*.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) de Win32 para determinar la causa del error.

### <a name="remarks"></a>Observaciones

`PutFile`es una rutina de alto nivel que controla todas las operaciones asociadas con el almacenamiento de un archivo en un servidor FTP. Las aplicaciones que solo envían datos, o que requieren un control más estrecho sobre la transferencia de archivos, deben usar [OpenFile](#openfile) y [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write).

Reemplace el valor predeterminado de `dwContext` para establecer el identificador de contexto en un valor que desee. El identificador de contexto está asociado `CFtpConnection` a esta operación específica del objeto creado por su [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto. El valor se devuelve a [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con la que se identifica. Consulte el artículo Primeros pasos de [Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

## <a name="cftpconnectionremove"></a><a name="remove"></a>CFtpConnection::Quitar

Llame a esta función miembro para eliminar el archivo especificado del servidor conectado.

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>Parámetros

*pstrFileName*<br/>
Puntero a una cadena que contiene el nombre de archivo que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) de Win32 para determinar la causa del error.

### <a name="remarks"></a>Observaciones

El parámetro *pstrFileName* puede ser un nombre de archivo parcialmente calificado en relación con el directorio actual o completo. Se puede\\utilizar una barra diagonal inversa ( ) o una barra diagonal (/) como separador de directorios para cualquiera de los nombres. La `Remove` función traduce los separadores de nombre de directorio a los caracteres adecuados antes de que se utilicen.

## <a name="cftpconnectionremovedirectory"></a><a name="removedirectory"></a>CFtpConnection::RemoveDirectory

Llame a esta función miembro para quitar el directorio especificado del servidor conectado.

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parámetros

*pstrDirName*<br/>
Puntero a una cadena que contiene el directorio que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) de Win32 para determinar la causa del error.

### <a name="remarks"></a>Observaciones

Use [GetCurrentDirectory](#getcurrentdirectory) para determinar el directorio de trabajo actual del servidor. No asuma que el sistema remoto le ha conectado al directorio raíz.

El parámetro *pstrDirName* puede ser un nombre de archivo parcial o completo en relación con el directorio actual. Se puede\\utilizar una barra diagonal inversa ( ) o una barra diagonal (/) como separador de directorios para cualquiera de los nombres. `RemoveDirectory`traduce los separadores de nombre de directorio a los caracteres adecuados antes de que se utilicen.

## <a name="cftpconnectionrename"></a><a name="rename"></a>CFtpConnection::Rename

Llame a esta función miembro para cambiar el nombre del archivo especificado en el servidor conectado.

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>Parámetros

*pstrExisting*<br/>
Puntero a una cadena que contiene el nombre actual del archivo al que se va a cambiar el nombre.

*pstrNew*<br/>
Puntero a una cadena que contiene el nuevo nombre del archivo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) de Win32 para determinar la causa del error.

### <a name="remarks"></a>Observaciones

Los *parámetros pstrExisting* y *pstrNew* pueden ser un nombre de archivo parcialmente calificado en relación con el directorio actual o completo. Se puede\\utilizar una barra diagonal inversa ( ) o una barra diagonal (/) como separador de directorios para cualquiera de los nombres. `Rename`traduce los separadores de nombre de directorio a los caracteres adecuados antes de que se utilicen.

## <a name="cftpconnectionsetcurrentdirectory"></a><a name="setcurrentdirectory"></a>CFtpConnection::SetCurrentDirectory

Llame a esta función miembro para cambiar a un directorio diferente en el servidor FTP.

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parámetros

*pstrDirName*<br/>
Puntero a una cadena que contiene el nombre del directorio.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) de Win32 para determinar la causa del error.

### <a name="remarks"></a>Observaciones

El parámetro *pstrDirName* puede ser un nombre de archivo parcial o completo en relación con el directorio actual. Se puede\\utilizar una barra diagonal inversa ( ) o una barra diagonal (/) como separador de directorios para cualquiera de los nombres. `SetCurrentDirectory`traduce los separadores de nombre de directorio a los caracteres adecuados antes de que se utilicen.

Utilice [GetCurrentDirectory](#getcurrentdirectory) para determinar el directorio de trabajo actual de un servidor FTP. No asuma que el sistema remoto le ha conectado al directorio raíz.

## <a name="see-also"></a>Consulte también

[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[CInternetSession (clase)](../../mfc/reference/cinternetsession-class.md)
