---
title: CFtpConnection (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3dce0efa8ced6e51557e4efc64b8c5f7441d662
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422381"
---
# <a name="cftpconnection-class"></a>CFtpConnection (clase)

Administra la conexión FTP a un servidor de Internet y permite la manipulación directa de directorios y archivos en ese servidor.

## <a name="syntax"></a>Sintaxis

```
class CFtpConnection : public CInternetConnection
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CFtpConnection::CFtpConnection](#cftpconnection)|Construye un objeto `CFtpConnection`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CFtpConnection::Command](#command)|Envía un comando directamente a un servidor FTP.|
|[CFtpConnection::CreateDirectory](#createdirectory)|Crea un directorio en el servidor.|
|[CFtpConnection:: GetCurrentDirectory](#getcurrentdirectory)|Obtiene el directorio actual para esta conexión.|
|[CFtpConnection:: GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)|Obtiene el directorio actual para esta conexión como una dirección URL.|
|[CFtpConnection::GetFile](#getfile)|Obtiene un archivo desde el servidor conectado|
|[CFtpConnection:: OpenFile](#openfile)|Abre un archivo en el servidor conectado.|
|[CFtpConnection::PutFile](#putfile)|Coloca un archivo en el servidor.|
|[CFtpConnection:: Remove](#remove)|Quita un archivo del servidor.|
|[CFtpConnection::RemoveDirectory](#removedirectory)|Quita el directorio especificado del servidor.|
|[CFtpConnection::Rename](#rename)|Cambia el nombre de un archivo en el servidor.|
|[CFtpConnection:: SetCurrentDirectory](#setcurrentdirectory)|Establece el directorio actual de FTP.|

## <a name="remarks"></a>Comentarios

FTP es uno de los tres servicios de Internet reconocidos por las clases WinInet de MFC.

Para comunicarse con un servidor FTP para Internet, primero debe crear una instancia de [CInternetSession](../../mfc/reference/cinternetsession-class.md)y, a continuación, cree un `CFtpConnection` objeto. No crear nunca un `CFtpConnection` objeto directamente; en su lugar, llame a [CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), que crea el `CFtpConnection` de objetos y devuelve un puntero a él.

Para obtener más información sobre cómo `CFtpConnection` funciona con las clases de Internet de MFC, vea el artículo [Internet programar con WinInet](../../mfc/win32-internet-extensions-wininet.md). Para obtener más información sobre la comunicación con los otros dos admitidos servicios HTTP y gopher, vea las clases [CHttpConnection](../../mfc/reference/chttpconnection-class.md) y [CGopherConnection](../../mfc/reference/cgopherconnection-class.md).

## <a name="example"></a>Ejemplo

  Vea el ejemplo de la [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) información general de clases.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

##  <a name="cftpconnection"></a>  CFtpConnection::CFtpConnection

Se llama a esta función miembro para construir un `CFtpConnection` objeto.

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
Un puntero a la que se relaciona [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto.

*hConnected*<br/>
El identificador de Windows de la sesión actual de Internet.

*pstrServer*<br/>
Un puntero a una cadena que contiene el nombre del servidor FTP.

*dwContext*<br/>
El identificador de contexto para la operación. *dwContext* identifica información de estado de la operación devuelta por [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). El valor predeterminado se establece en 1; Sin embargo, puede asignar explícitamente un identificador de contexto específico para la operación. El objeto y cualquier trabajo que se asociarán con ese identificador de contexto.

*pstrUserName*<br/>
Puntero a una cadena terminada en null que especifica el nombre del usuario para iniciar sesión. Si es NULL, el valor predeterminado es anónimo.

*pstrPassword*<br/>
Un puntero a una cadena terminada en null que especifica la contraseña que se utilizará para iniciar sesión. Si ambos *pstrPassword* y *pstrUserName* son NULL, la contraseña anónima predeterminada es el nombre de correo electrónico del usuario. Si *pstrPassword* es NULL (o una cadena vacía) pero *pstrUserName* no es NULL, se utiliza una contraseña en blanco. En la tabla siguiente describe el comportamiento de las cuatro configuraciones posibles de *pstrUserName* y *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Nombre de usuario se envía al servidor FTP|Contraseña que se envían al servidor FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL o ""|NULL o ""|"anónimo"|Nombre de correo electrónico del usuario|
|Cadena no nula|NULL o ""|*pstrUserName*|" "|
|Cadena no nula NULL|ERROR|ERROR||
|Cadena no nula|Cadena no nula|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
Número que identifica el puerto TCP/IP que se usará en el servidor.

*bPassive*<br/>
Especifica el modo pasivo o activo para esta sesión FTP. Si se establece en TRUE, Establece la API Win32 *dwFlag* a INTERNET_FLAG_PASSIVE.

### <a name="remarks"></a>Comentarios

No crear nunca un `CFtpConnection` objeto directamente. En su lugar, llame a [CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), que crea el `CFptConnection` objeto.

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
Determina si se espera una respuesta del servidor FTP. Puede presentar uno de los siguientes valores:

- `CmdRespNone` Se espera ninguna respuesta.

- `CmdRespRead` Se espera una respuesta.

*dwFlags*<br/>
Un valor que contiene las marcas que controlan esta función. Para obtener una lista completa, consulte [FTPCommand](/windows/desktop/api/wininet/nf-wininet-ftpcommanda).

*dwContext*<br/>
Un puntero a un valor que contiene un valor definido por la aplicación, que se utiliza para identificar el contexto de la aplicación en las devoluciones de llamada.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad de la [FTPCommand](/windows/desktop/api/wininet/nf-wininet-ftpcommanda) funcione, como se describe en el SDK de Windows.

Si se produce un error, MFC inicia una excepción de tipo [CInternetException](../../mfc/reference/cinternetexception-class.md).

##  <a name="createdirectory"></a>  CFtpConnection::CreateDirectory

Llame a esta función miembro para crear un directorio en el servidor conectado.

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parámetros

*pstrDirName*<br/>
Un puntero a una cadena que contiene el nombre del directorio que se va a crear.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función Windows [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.

### <a name="remarks"></a>Comentarios

Use `GetCurrentDirectory` para determinar el directorio de trabajo actual para esta conexión al servidor. No suponga que el sistema remoto ha conectado al directorio raíz.

El `pstrDirName` parámetro puede ser un parcialmente o un nombre de archivo completo en relación con el directorio actual. Una barra diagonal inversa (\\) o se puede usar la barra diagonal (/) como separador de directorio para cualquier nombre. `CreateDirectory` traduce los separadores de nombre de directorio en los caracteres correspondientes antes de usarse.

##  <a name="getcurrentdirectory"></a>  CFtpConnection:: GetCurrentDirectory

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
Un puntero a una cadena que recibirá el nombre del directorio.

*lpdwLen*<br/>
Un puntero a un valor DWORD que contiene la información siguiente:

|||
|-|-|
|En la entrada|El tamaño del búfer al que hace referencia *pstrDirName*.|
|Si la devolución|El número de caracteres almacenados en *pstrDirName*. Si se produce un error en la función miembro y, a continuación, se devuelve ERROR_INSUFFICIENT_BUFFER *lpdwLen* contiene el número de bytes que se debe asignar la aplicación con el fin de recibir la cadena.|

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.

### <a name="remarks"></a>Comentarios

Para obtener el nombre del directorio como una dirección URL en su lugar, llame a [GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl).

Los parámetros *pstrDirName* o *strDirName* puede ser cualquiera de los nombres de archivo parcialmente completo relativa al directorio actual o un nombre completo. Una barra diagonal inversa (\\) o se puede usar la barra diagonal (/) como separador de directorio para cualquier nombre. `GetCurrentDirectory` traduce los separadores de nombre de directorio en los caracteres correspondientes antes de usarse.

##  <a name="getcurrentdirectoryasurl"></a>  CFtpConnection:: GetCurrentDirectoryAsURL

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
Un puntero a una cadena que recibirá el nombre del directorio.

*lpdwLen*<br/>
Un puntero a un valor DWORD que contiene la información siguiente:

|||
|-|-|
|En la entrada|El tamaño del búfer al que hace referencia *pstrDirName*.|
|Si la devolución|El número de caracteres almacenados en *pstrDirName*. Si se produce un error en la función miembro y, a continuación, se devuelve ERROR_INSUFFICIENT_BUFFER *lpdwLen* contiene el número de bytes que se debe asignar la aplicación con el fin de recibir la cadena.|

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.

### <a name="remarks"></a>Comentarios

`GetCurrentDirectoryAsURL` se comporta igual que [GetCurrentDirectory](#getcurrentdirectory)

El parámetro *strDirName* puede ser cualquiera de los nombres de archivo parcialmente completo relativa al directorio actual o un nombre completo. Una barra diagonal inversa (\\) o se puede usar la barra diagonal (/) como separador de directorio para cualquier nombre. `GetCurrentDirectoryAsURL` traduce los separadores de nombre de directorio en los caracteres correspondientes antes de usarse.

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
Un puntero a una cadena terminada en null que contiene el nombre del archivo que desea recuperar del servidor FTP.

*pstrLocalFile*<br/>
Un puntero a una cadena terminada en null que contiene el nombre de archivo que se creará en el sistema local.

*bFailIfExists*<br/>
Indica si el nombre de archivo ya se puede usar un archivo existente. Si ya existe el nombre de archivo local, y este parámetro es TRUE, `GetFile` se produce un error. En caso contrario, `GetFile` borrará la copia existente del archivo.

*dwAttributes*<br/>
Indica los atributos del archivo. Esto puede ser cualquier combinación de los siguientes indicadores FILE_ATTRIBUTE_ *.

- El archivo FILE_ATTRIBUTE_ARCHIVE es un archivo de almacenamiento. Las aplicaciones utilizan este atributo para marcar los archivos de copia de seguridad o eliminación.

- FILE_ATTRIBUTE_COMPRESSED el archivo o directorio está comprimido. Para un archivo, la compresión significa que todos los datos en el archivo está comprimido. Para un directorio, la compresión es el valor predeterminado para los archivos recién creados y los subdirectorios.

- El archivo FILE_ATTRIBUTE_DIRECTORY es un directorio.

- El archivo FILE_ATTRIBUTE_NORMAL no tiene otros atributos establecido. Este atributo es válido sólo si se utiliza por sí solo. Todos los demás atributos de archivo de invalidación FILE_ATTRIBUTE_NORMAL:

- FILE_ATTRIBUTE_HIDDEN el archivo está oculto. No es incluirse en un listado de directorios ordinario.

- FILE_ATTRIBUTE_READONLY el archivo es de solo lectura. Las aplicaciones pueden leer el archivo, pero no se puede escribir en él o eliminarla.

- FILE_ATTRIBUTE_SYSTEM el archivo forma parte de o se usa exclusivamente por el sistema operativo.

- FILE_ATTRIBUTE_TEMPORARY el archivo se está usando para el almacenamiento temporal. Las aplicaciones deben escribir en el archivo solo si es absolutamente necesario. La mayoría de los datos del archivo permanece en memoria sin vuelca el medio dado que pronto se eliminará el archivo.

*dwFlags*<br/>
Especifica las condiciones en que se produce la transferencia. Este parámetro puede ser cualquiera de los *dwFlags* describen los valores en [FtpGetFile](/windows/desktop/api/wininet/nf-wininet-ftpgetfilea) en el SDK de Windows.

*dwContext*<br/>
El identificador de contexto para la recuperación de archivos. Consulte **comentarios** para obtener más información acerca de *dwContext*.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.

### <a name="remarks"></a>Comentarios

`GetFile` es una rutina de alto nivel que se encarga de toda la sobrecarga asociada a la lectura de un archivo desde un servidor FTP y almacenarlos localmente. Las aplicaciones que solo recuperan datos de archivo, o que requieren un control detallado sobre la transferencia de archivos, deben usar `OpenFile` y [CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read) en su lugar.

Si *dwFlags* FILE_TRANSFER_TYPE_ASCII, traducción de datos de archivo también convierte control y formato de caracteres a equivalentes de Windows. La transferencia predeterminado es el modo binario, donde se descarga el archivo en el mismo formato cuando se almacenan en el servidor.

Ambos *pstrRemoteFile* y *pstrLocalFile* puede ser cualquiera de los nombres de archivo parcialmente completo relativa al directorio actual o un nombre completo. Una barra diagonal inversa (\\) o se puede usar la barra diagonal (/) como separador de directorio para cualquier nombre. `GetFile` traduce los separadores de nombre de directorio en los caracteres correspondientes antes de usarse.

Invalidar el *dwContext* predeterminada para establecer el identificador de contexto en un valor de su elección. El identificador de contexto está asociado con esta operación específica de la `CFtpConnection` objeto creado por su [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto. El valor se devuelve al [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con el que se identifica. Consulte el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

##  <a name="openfile"></a>  CFtpConnection:: OpenFile

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
Un puntero a una cadena que contiene el nombre del archivo que se puede abrir.

*dwAccess*<br/>
Determina cómo se accederá a los archivos. Puede ser GENERIC_READ o GENERIC_WRITE, pero no ambos.

*dwFlags*<br/>
Especifica las condiciones en las que se producen transferencias posteriores. Esto puede ser cualquiera de las siguientes constantes FTP_TRANSFER_ *:

- FTP_TRANSFER_TYPE_ASCII el archivo se transfiere mediante el método de transferencia ASCII de FTP (tipo A). Convierte control y la información de formato a los equivalentes locales.

- El archivo FTP_TRANSFER_TYPE_BINARY transfiere los datos mediante el método de transferencia de la imagen como (tipo I). El archivo transfiere los datos tal y como existen, sin cambios. Este es el método de transferencia de forma predeterminada.

*dwContext*<br/>
El identificador de contexto para abrir el archivo. Consulte **comentarios** para obtener más información acerca de *dwContext*.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CInternetFile](../../mfc/reference/cinternetfile-class.md) objeto.

### <a name="remarks"></a>Comentarios

`OpenFile` debe usarse en las situaciones siguientes:

- Una aplicación tiene datos que necesita que se envíen y se crea como un archivo en el servidor FTP, pero que los datos no están en un archivo local. Una vez `OpenFile` abre un archivo, la aplicación usa [CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write) para enviar los datos del archivo FTP al servidor.

- Una aplicación debe recuperar un archivo del servidor y lo coloca en la memoria controlada a la aplicación, en lugar de escribir en el disco. La aplicación usa [CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read) después de usar `OpenFile` para abrir el archivo.

- Una aplicación necesita un gran nivel de control sobre una transferencia de archivos. Por ejemplo, la aplicación puede desear mostrar el progreso de un control indicar el progreso del estado de transferencia de archivos mientras se descarga un archivo.

Después de llamar a `OpenFile` y hasta que realiza la llamada `CInternetConnection::Close`, solo puede llamar la aplicación [CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read), [CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write), `CInternetConnection::Close`, o [ CFtpFileFind:: FindFile](../../mfc/reference/cftpfilefind-class.md#findfile). Las llamadas a otras funciones FTP para la misma sesión FTP se producirá un error y establece el código de error en FTP_ETRANSFER_IN_PROGRESS.

El *pstrFileName* parámetro puede ser un nombre parcialmente completo completo o relativo al directorio actual. Una barra diagonal inversa (\\) o se puede usar la barra diagonal (/) como separador de directorio para cualquier nombre. `OpenFile` traduce los separadores de nombre de directorio en los caracteres correspondientes antes de usarlo.

Invalidar el *dwContext* predeterminada para establecer el identificador de contexto en un valor de su elección. El identificador de contexto está asociado con esta operación específica de la `CFtpConnection` objeto creado por su [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto. El valor se devuelve al [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con el que se identifica. Consulte el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

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
Un puntero a una cadena que contiene el nombre del archivo que se envíe desde el sistema local.

*pstrRemoteFile*<br/>
Un puntero a una cadena que contiene el nombre de archivo que se creará en el servidor FTP.

*dwFlags*<br/>
Especifica las condiciones en que se produce la transferencia del archivo. Puede ser cualquiera de las constantes FTP_TRANSFER_ * descritas en [OpenFile](#openfile).

*dwContext*<br/>
El identificador de contexto para colocar el archivo. Consulte **comentarios** para obtener más información acerca de *dwContext*.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.

### <a name="remarks"></a>Comentarios

`PutFile` es una rutina de alto nivel que controla todas las operaciones asociadas al almacenamiento de un archivo en un servidor FTP. Las aplicaciones que solo enviar datos, o que requieren mayor control sobre la transferencia de archivos, deben usar [OpenFile](#openfile) y [CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write).

Reemplace el valor predeterminado de `dwContext` para establecer el identificador de contexto en un valor que desee. El identificador de contexto está asociado con esta operación específica de la `CFtpConnection` objeto creado por su [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto. El valor se devuelve al [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con el que se identifica. Consulte el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

##  <a name="remove"></a>  CFtpConnection:: Remove

Llame a esta función miembro para eliminar el archivo especificado desde el servidor conectado.

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>Parámetros

*pstrFileName*<br/>
Un puntero a una cadena que contiene el nombre de archivo para quitar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.

### <a name="remarks"></a>Comentarios

El *pstrFileName* parámetro puede ser un nombre parcialmente completo completo o relativo al directorio actual. Una barra diagonal inversa (\\) o se puede usar la barra diagonal (/) como separador de directorio para cualquier nombre. El `Remove` función traduce los separadores de nombre de directorio en los caracteres correspondientes antes de usarse.

##  <a name="removedirectory"></a>  CFtpConnection::RemoveDirectory

Llame a esta función miembro para quitar el directorio especificado desde el servidor conectado.

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parámetros

*pstrDirName*<br/>
Un puntero a una cadena que contiene el directorio que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.

### <a name="remarks"></a>Comentarios

Use [GetCurrentDirectory](#getcurrentdirectory) para determinar el directorio de trabajo actual del servidor. No suponga que el sistema remoto ha conectado al directorio raíz.

El *pstrDirName* parámetro puede ser cualquier un nombre completo o parcial relativa al directorio actual. Una barra diagonal inversa (\\) o se puede usar la barra diagonal (/) como separador de directorio para cualquier nombre. `RemoveDirectory` traduce los separadores de nombre de directorio en los caracteres correspondientes antes de usarse.

##  <a name="rename"></a>  CFtpConnection::Rename

Llame a esta función miembro para cambiar el nombre del archivo especificado en el servidor conectado.

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>Parámetros

*pstrExisting*<br/>
Un puntero a una cadena que contiene el nombre actual del archivo se va a cambiar.

*pstrNew*<br/>
Un puntero a una cadena que contiene el nombre del archivo nuevo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.

### <a name="remarks"></a>Comentarios

El *pstrExisting* y *pstrNew* parámetros pueden ser un nombre parcialmente completo completo o relativo al directorio actual. Una barra diagonal inversa (\\) o se puede usar la barra diagonal (/) como separador de directorio para cualquier nombre. `Rename` traduce los separadores de nombre de directorio en los caracteres correspondientes antes de usarse.

##  <a name="setcurrentdirectory"></a>  CFtpConnection:: SetCurrentDirectory

Llame a esta función miembro para cambiar a un directorio diferente en el servidor FTP.

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parámetros

*pstrDirName*<br/>
Un puntero a una cadena que contiene el nombre del directorio.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.

### <a name="remarks"></a>Comentarios

El *pstrDirName* parámetro puede ser cualquier un nombre completo o parcial relativa al directorio actual. Una barra diagonal inversa (\\) o se puede usar la barra diagonal (/) como separador de directorio para cualquier nombre. `SetCurrentDirectory` traduce los separadores de nombre de directorio en los caracteres correspondientes antes de usarse.

Use [GetCurrentDirectory](#getcurrentdirectory) para determinar el directorio de trabajo actual de un servidor FTP. No suponga que el sistema remoto ha conectado al directorio raíz.

## <a name="see-also"></a>Vea también

[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[CInternetSession (clase)](../../mfc/reference/cinternetsession-class.md)
