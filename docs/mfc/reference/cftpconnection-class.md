---
title: CFtpConnection (clase)
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
ms.openlocfilehash: 94ee4cb938ee061470282eb2f08a94d83c908805
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177280"
---
# <a name="cftpconnection-class"></a>CFtpConnection (clase)

Administra la conexión FTP a un servidor de Internet y permite la manipulación directa de directorios y archivos en ese servidor.

## <a name="syntax"></a>Sintaxis

```
class CFtpConnection : public CInternetConnection
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFtpConnection::CFtpConnection](#cftpconnection)|Construye un objeto `CFtpConnection`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFtpConnection::Command](#command)|Envía un comando directamente a un servidor FTP.|
|[CFtpConnection::CreateDirectory](#createdirectory)|Crea un directorio en el servidor.|
|[CFtpConnection::GetCurrentDirectory](#getcurrentdirectory)|Obtiene el directorio actual para esta conexión.|
|[CFtpConnection::GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)|Obtiene el directorio actual para esta conexión como una dirección URL.|
|[CFtpConnection::GetFile](#getfile)|Obtiene un archivo del servidor conectado.|
|[CFtpConnection::OpenFile](#openfile)|Abre un archivo en el servidor conectado.|
|[CFtpConnection::PutFile](#putfile)|Coloca un archivo en el servidor.|
|[CFtpConnection::Remove](#remove)|Quita un archivo del servidor.|
|[CFtpConnection::RemoveDirectory](#removedirectory)|Quita el directorio especificado del servidor.|
|[CFtpConnection::Rename](#rename)|Cambia el nombre de un archivo en el servidor.|
|[CFtpConnection::SetCurrentDirectory](#setcurrentdirectory)|Establece el directorio FTP actual.|

## <a name="remarks"></a>Comentarios

FTP es uno de los tres servicios de Internet reconocidos por las clases WinInet de MFC.

Para comunicarse con un servidor de Internet FTP, primero debe crear una instancia de [CInternetSession](../../mfc/reference/cinternetsession-class.md)y, a continuación, `CFtpConnection` crear un objeto. Nunca se crea un `CFtpConnection` objeto directamente; en su lugar, se llama a [CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), que crea el `CFtpConnection` objeto y devuelve un puntero a él.

Para obtener más información sobre `CFtpConnection` cómo funciona con las otras clases de Internet de MFC, vea el artículo [programación en Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md). Para obtener más información sobre la comunicación con los otros dos servicios admitidos, HTTP y Gopher, vea las clases [CHttpConnection (](../../mfc/reference/chttpconnection-class.md) y [CGopherConnection](../../mfc/reference/cgopherconnection-class.md).

## <a name="example"></a>Ejemplo

  Vea el ejemplo de la información general de la clase [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet. h

##  <a name="cftpconnection"></a>  CFtpConnection::CFtpConnection

Se llama a esta función miembro para construir `CFtpConnection` un objeto.

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
Puntero al objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) relacionado.

*hConnected*<br/>
Identificador de Windows de la sesión de Internet actual.

*pstrServer*<br/>
Puntero a una cadena que contiene el nombre del servidor FTP.

*dwContext*<br/>
Identificador de contexto para la operación. *dwContext* identifica la información de estado de la operación devuelta por [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). El valor predeterminado se establece en 1; sin embargo, puede asignar explícitamente un identificador de contexto específico para la operación. El objeto y cualquier trabajo que tenga se asociarán a ese identificador de contexto.

*pstrUserName*<br/>
Puntero a una cadena terminada en null que especifica el nombre del usuario en el que se va a iniciar sesión. Si es NULL, el valor predeterminado es Anonymous.

*pstrPassword*<br/>
Puntero a una cadena terminada en null que especifica la contraseña que se va a usar para iniciar sesión. Si *pstrPassword* y *pstrUserName* son NULL, la contraseña anónima predeterminada es el nombre de correo electrónico del usuario. Si *pstrPassword* es null (o una cadena vacía), pero *PSTRUSERNAME* no es null, se usa una contraseña en blanco. En la tabla siguiente se describe el comportamiento de los cuatro valores posibles de *pstrUserName* y *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Nombre de usuario enviado al servidor FTP|Contraseña enviada al servidor FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL o ""|NULL o ""|Anonymous|Nombre de correo electrónico del usuario|
|Cadena que no es NULL|NULL o ""|*pstrUserName*|" "|
|Cadena nula que no es NULL|ERROR|ERROR||
|Cadena que no es NULL|Cadena que no es NULL|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
Número que identifica el puerto TCP/IP que se va a utilizar en el servidor.

*bPassive*<br/>
Especifica el modo pasivo o activo para esta sesión FTP. Si se establece en TRUE, establece la API de Win32 *dwFlag* en INTERNET_FLAG_PASSIVE.

### <a name="remarks"></a>Comentarios

Nunca se crea un `CFtpConnection` objeto directamente. En su lugar, llame a [CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), que `CFptConnection` crea el objeto.

##  <a name="command"></a>  CFtpConnection::Command

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
Especifica si se espera una respuesta del servidor FTP. Puede presentar uno de los siguientes valores:

- `CmdRespNone`No se espera ninguna respuesta.
- `CmdRespRead`Se espera una respuesta.
- `CmdRespWrite`No se usa.

CmdResponseType es un miembro de CFtpConnection, definido en *afxinet. h*.

*dwFlags*<br/>
Un valor que contiene las marcas que controlan esta función. Para obtener una lista completa, vea [FTPCommand](/windows/win32/api/wininet/nf-wininet-ftpcommandw).

*dwContext*<br/>
Un puntero a un valor que contiene un valor definido por la aplicación, que se utiliza para identificar el contexto de la aplicación en las devoluciones de llamada.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad de la función [FTPCommand](/windows/win32/api/wininet/nf-wininet-ftpcommandw) , tal como se describe en el Windows SDK.

Si se produce un error, MFC produce una excepción de tipo [CInternetException](../../mfc/reference/cinternetexception-class.md).

##  <a name="createdirectory"></a>  CFtpConnection::CreateDirectory

Llame a esta función miembro para crear un directorio en el servidor conectado.

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parámetros

*pstrDirName*<br/>
Puntero a una cadena que contiene el nombre del directorio que se va a crear.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) de Windows para determinar la causa del error.

### <a name="remarks"></a>Comentarios

Use `GetCurrentDirectory` para determinar el directorio de trabajo actual para esta conexión al servidor. No asuma que el sistema remoto se ha conectado al directorio raíz.

El `pstrDirName` parámetro puede ser un nombre de archivo parcial o completo en relación con el directorio actual. Se puede usar una\\barra diagonal inversa () o una barra diagonal (/) como separador de directorios para cualquier nombre. `CreateDirectory`convierte los separadores de nombre de directorio en los caracteres adecuados antes de usarlos.

##  <a name="getcurrentdirectory"></a>  CFtpConnection::GetCurrentDirectory

Llame a esta función miembro para obtener el nombre del directorio actual.

```
BOOL GetCurrentDirectory(CString& strDirName) const;

BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Parámetros

*strDirName*<br/>
Referencia a una cadena que recibirá el nombre del directorio.

*pstrDirName*<br/>
Un puntero a una cadena que recibirá el nombre del directorio.

*lpdwLen*<br/>
Un puntero a un valor DWORD que contiene la información siguiente:

|||
|-|-|
|Al entrar|Tamaño del búfer al que hace referencia *pstrDirName*.|
|Al devolverse|Número de caracteres almacenados en *pstrDirName*. Si se produce un error en la función miembro y se devuelve ERROR_INSUFFICIENT_BUFFER, *lpdwLen* contiene el número de bytes que la aplicación debe asignar para recibir la cadena.|

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función de Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para determinar la causa del error.

### <a name="remarks"></a>Comentarios

Para obtener el nombre de directorio como una dirección URL, llame a [GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl).

Los parámetros *pstrDirName* o *strDirName* pueden ser nombres de archivo parcialmente calificados en relación con el directorio actual o completo. Se puede usar una\\barra diagonal inversa () o una barra diagonal (/) como separador de directorios para cualquier nombre. `GetCurrentDirectory`convierte los separadores de nombre de directorio en los caracteres adecuados antes de usarlos.

##  <a name="getcurrentdirectoryasurl"></a>  CFtpConnection::GetCurrentDirectoryAsURL

Llame a esta función miembro para obtener el nombre del directorio actual como una dirección URL.

```
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;

BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Parámetros

*strDirName*<br/>
Referencia a una cadena que recibirá el nombre del directorio.

*pstrDirName*<br/>
Un puntero a una cadena que recibirá el nombre del directorio.

*lpdwLen*<br/>
Un puntero a un valor DWORD que contiene la información siguiente:

|||
|-|-|
|Al entrar|Tamaño del búfer al que hace referencia *pstrDirName*.|
|Al devolverse|Número de caracteres almacenados en *pstrDirName*. Si se produce un error en la función miembro y se devuelve ERROR_INSUFFICIENT_BUFFER, *lpdwLen* contiene el número de bytes que la aplicación debe asignar para recibir la cadena.|

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función de Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para determinar la causa del error.

### <a name="remarks"></a>Comentarios

`GetCurrentDirectoryAsURL`se comporta igual que [GetCurrentDirectory](#getcurrentdirectory)

El parámetro *strDirName* puede ser nombres de archivo parcialmente calificados en relación con el directorio actual o completo. Se puede usar una\\barra diagonal inversa () o una barra diagonal (/) como separador de directorios para cualquier nombre. `GetCurrentDirectoryAsURL`convierte los separadores de nombre de directorio en los caracteres adecuados antes de usarlos.

##  <a name="getfile"></a>  CFtpConnection::GetFile

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
Indica si un archivo existente ya puede utilizar el nombre de archivo. Si el nombre de archivo local ya existe y este parámetro es true, `GetFile` se produce un error. De lo `GetFile` contrario, borrará la copia existente del archivo.

*dwAttributes*<br/>
Indica los atributos del archivo. Puede ser cualquier combinación de las siguientes marcas de FILE_ATTRIBUTE_ *.

- FILE_ATTRIBUTE_ARCHIVE el archivo es un archivo de almacenamiento. Las aplicaciones usan este atributo para marcar los archivos para la copia de seguridad o la eliminación.

- FILE_ATTRIBUTE_COMPRESSED el archivo o el directorio está comprimido. En el caso de un archivo, la compresión significa que se comprimen todos los datos del archivo. Para un directorio, la compresión es el valor predeterminado para los archivos y subdirectorios recién creados.

- FILE_ATTRIBUTE_DIRECTORY el archivo es un directorio.

- FILE_ATTRIBUTE_NORMAL el archivo no tiene ningún otro conjunto de atributos. Este atributo solo es válido si se usa por sí solo. Todos los demás atributos de archivo reemplazan a FILE_ATTRIBUTE_NORMAL:

- FILE_ATTRIBUTE_HIDDEN el archivo está oculto. No se incluirá en una lista de directorios normal.

- FILE_ATTRIBUTE_READONLY el archivo es de solo lectura. Las aplicaciones pueden leer el archivo pero no pueden escribir en él ni eliminarlo.

- FILE_ATTRIBUTE_SYSTEM el archivo forma parte de o lo utiliza exclusivamente el sistema operativo.

- FILE_ATTRIBUTE_TEMPORARY el archivo se usa para el almacenamiento temporal. Las aplicaciones solo deben escribir en el archivo si es absolutamente necesario. La mayoría de los datos del archivo permanecen en la memoria sin vaciarse en el medio porque el archivo se eliminará pronto.

*dwFlags*<br/>
Especifica las condiciones en las que se produce la transferencia. Este parámetro puede ser cualquiera de los valores *dwFlags* descritos en [FtpGetFile](/windows/win32/api/wininet/nf-wininet-ftpgetfilew) en el Windows SDK.

*dwContext*<br/>
Identificador de contexto para la recuperación de archivos. Vea la **sección Comentarios** para obtener más información sobre *dwContext*.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función de Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para determinar la causa del error.

### <a name="remarks"></a>Comentarios

`GetFile`es una rutina de alto nivel que controla toda la sobrecarga asociada con la lectura de un archivo desde un servidor FTP y su almacenamiento local. Las aplicaciones que solo recuperan datos de archivos, o que requieren un control de cierre sobre la `OpenFile` transferencia de archivos, deben usar y [CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read) en su lugar.

Si *dwFlags* es FILE_TRANSFER_TYPE_ASCII, la traducción de datos de archivo también convierte los caracteres de formato y control en los equivalentes de Windows. La transferencia predeterminada es el modo binario, donde el archivo se descarga en el mismo formato que se almacena en el servidor.

Tanto *pstrRemoteFile* como *pstrLocalFile* pueden ser nombres de archivo parcialmente calificados en relación con el directorio actual o completo. Se puede usar una\\barra diagonal inversa () o una barra diagonal (/) como separador de directorios para cualquier nombre. `GetFile`convierte los separadores de nombre de directorio en los caracteres adecuados antes de usarlos.

Invalide el valor predeterminado de *dwContext* para establecer el identificador de contexto en un valor de su elección. El identificador de contexto está asociado a esta operación específica del `CFtpConnection` objeto creado por su objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) . El valor se devuelve a [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con la que se identifica. Consulte el artículo [Internet First Steps: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

##  <a name="openfile"></a>  CFtpConnection::OpenFile

Llame a esta función miembro para abrir un archivo ubicado en un servidor FTP para lectura o escritura.

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
Determina cómo se va a obtener acceso al archivo. Puede ser GENERIC_READ o GENERIC_WRITE, pero no ambos.

*dwFlags*<br/>
Especifica las condiciones en las que se producen las transferencias posteriores. Puede ser cualquiera de las siguientes constantes de FTP_TRANSFER_ *:

- FTP_TRANSFER_TYPE_ASCII las transferencias de archivos mediante el método de transferencia FTP ASCII (Type A). Convierte la información de control y formato en equivalentes locales.

- FTP_TRANSFER_TYPE_BINARY el archivo transfiere datos mediante el método de transferencia de imágenes (tipo I) de FTP. El archivo transfiere los datos exactamente como existen, sin cambios. Este es el método de transferencia predeterminado.

*dwContext*<br/>
Identificador de contexto para abrir el archivo. Vea la **sección Comentarios** para obtener más información sobre *dwContext*.

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [CInternetFile](../../mfc/reference/cinternetfile-class.md) .

### <a name="remarks"></a>Comentarios

`OpenFile`debe usarse en las siguientes situaciones:

- Una aplicación tiene datos que deben enviarse y crearse como un archivo en el servidor FTP, pero los datos no están en un archivo local. Una `OpenFile` vez que abre un archivo, la aplicación usa [CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write) para enviar los datos del archivo FTP al servidor.

- Una aplicación debe recuperar un archivo del servidor y colocarlo en la memoria controlada por la aplicación, en lugar de escribirlo en el disco. La aplicación usa [CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read) después de `OpenFile` usar para abrir el archivo.

- Una aplicación necesita un nivel preciso de control sobre una transferencia de archivos. Por ejemplo, es posible que la aplicación desee mostrar un control de progreso que indique el progreso del estado de la transferencia de archivos durante la descarga de un archivo.

Después de llamar a `OpenFile` y hasta que se llama a `CInternetConnection::Close`, la aplicación solo puede llamar a [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read), [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write), `CInternetConnection::Close`, o [CFtpFileFind::FindFile](../../mfc/reference/cftpfilefind-class.md#findfile). Se producirá un error en las llamadas a otras funciones FTP para la misma sesión FTP y se establecerá el código de error en FTP_ETRANSFER_IN_PROGRESS.

El parámetro *pstrFileName* puede ser un nombre de archivo parcial en relación con el directorio actual o completo. Se puede usar una\\barra diagonal inversa () o una barra diagonal (/) como separador de directorios para cualquier nombre. `OpenFile`convierte los separadores de nombre de directorio en los caracteres adecuados antes de utilizarlos.

Invalide el valor predeterminado de *dwContext* para establecer el identificador de contexto en un valor de su elección. El identificador de contexto está asociado a esta operación específica del `CFtpConnection` objeto creado por su objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) . El valor se devuelve a [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con la que se identifica. Consulte el artículo [Internet First Steps: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

##  <a name="putfile"></a>  CFtpConnection::PutFile

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
Especifica las condiciones en las que se produce la transferencia del archivo. Puede ser cualquiera de las constantes FTP_TRANSFER_ * descritas en [OpenFile](#openfile).

*dwContext*<br/>
Identificador de contexto para colocar el archivo. Vea la **sección Comentarios** para obtener más información sobre *dwContext*.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función de Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para determinar la causa del error.

### <a name="remarks"></a>Comentarios

`PutFile`es una rutina de alto nivel que controla todas las operaciones asociadas al almacenamiento de un archivo en un servidor FTP. Las aplicaciones que solo envían datos, o que requieren un control más profundo sobre la transferencia de archivos, deben usar [OpenFile](#openfile) y [CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write).

Reemplace el valor predeterminado de `dwContext` para establecer el identificador de contexto en un valor que desee. El identificador de contexto está asociado a esta operación específica del `CFtpConnection` objeto creado por su objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) . El valor se devuelve a [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con la que se identifica. Consulte el artículo [Internet First Steps: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

##  <a name="remove"></a>  CFtpConnection::Remove

Llame a esta función miembro para eliminar el archivo especificado del servidor conectado.

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>Parámetros

*pstrFileName*<br/>
Puntero a una cadena que contiene el nombre de archivo que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función de Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para determinar la causa del error.

### <a name="remarks"></a>Comentarios

El parámetro *pstrFileName* puede ser un nombre de archivo parcial en relación con el directorio actual o completo. Se puede usar una\\barra diagonal inversa () o una barra diagonal (/) como separador de directorios para cualquier nombre. La `Remove` función convierte los separadores de nombre de directorio en los caracteres adecuados antes de usarlos.

##  <a name="removedirectory"></a>  CFtpConnection::RemoveDirectory

Llame a esta función miembro para quitar el directorio especificado del servidor conectado.

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parámetros

*pstrDirName*<br/>
Puntero a una cadena que contiene el directorio que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función de Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para determinar la causa del error.

### <a name="remarks"></a>Comentarios

Use [GetCurrentDirectory](#getcurrentdirectory) para determinar el directorio de trabajo actual del servidor. No asuma que el sistema remoto se ha conectado al directorio raíz.

El parámetro *pstrDirName* puede ser un nombre de archivo parcial o completo en relación con el directorio actual. Se puede usar una\\barra diagonal inversa () o una barra diagonal (/) como separador de directorios para cualquier nombre. `RemoveDirectory`convierte los separadores de nombre de directorio en los caracteres adecuados antes de usarlos.

##  <a name="rename"></a>  CFtpConnection::Rename

Llame a esta función miembro para cambiar el nombre del archivo especificado en el servidor conectado.

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>Parámetros

*pstrExisting*<br/>
Puntero a una cadena que contiene el nombre actual del archivo cuyo nombre se va a cambiar.

*pstrNew*<br/>
Puntero a una cadena que contiene el nuevo nombre del archivo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función de Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para determinar la causa del error.

### <a name="remarks"></a>Comentarios

Los parámetros *pstrExisting* y *pstrNew* pueden ser un nombre de archivo parcial en relación con el directorio actual o completo. Se puede usar una\\barra diagonal inversa () o una barra diagonal (/) como separador de directorios para cualquier nombre. `Rename`convierte los separadores de nombre de directorio en los caracteres adecuados antes de usarlos.

##  <a name="setcurrentdirectory"></a>  CFtpConnection::SetCurrentDirectory

Llame a esta función miembro para cambiar a un directorio diferente en el servidor FTP.

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parámetros

*pstrDirName*<br/>
Puntero a una cadena que contiene el nombre del directorio.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, se puede llamar a la función de Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) para determinar la causa del error.

### <a name="remarks"></a>Comentarios

El parámetro *pstrDirName* puede ser un nombre de archivo parcial o completo en relación con el directorio actual. Se puede usar una\\barra diagonal inversa () o una barra diagonal (/) como separador de directorios para cualquier nombre. `SetCurrentDirectory`convierte los separadores de nombre de directorio en los caracteres adecuados antes de usarlos.

Use [GetCurrentDirectory](#getcurrentdirectory) para determinar el directorio de trabajo actual de un servidor FTP. No asuma que el sistema remoto se ha conectado al directorio raíz.

## <a name="see-also"></a>Vea también

[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[CInternetSession (clase)](../../mfc/reference/cinternetsession-class.md)
