---
title: Clase de objeto CFtpConnection | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6a800ff5c8c071e966bbc1e5297fb706627c8d17
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cftpconnection-class"></a>Clase de objeto CFtpConnection
Administra la conexión FTP a un servidor de Internet y permite la manipulación directa de directorios y archivos en ese servidor.  
  
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
  
 Para comunicarse con un servidor FTP para Internet, primero debe crear una instancia de [CInternetSession](../../mfc/reference/cinternetsession-class.md)y, a continuación, cree un `CFtpConnection` objeto. No cree nunca un `CFtpConnection` objeto directamente; en su lugar, llame a [CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), que crea el `CFtpConnection` de objetos y devuelve un puntero a ella.  
  
 Para obtener más información sobre cómo `CFtpConnection` funciona con las demás clases de Internet de MFC, vea el artículo [programación para Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md). Para obtener más información sobre la comunicación con los otros dos admitidos servicios, HTTP y gopher, vea las clases de [CHttpConnection](../../mfc/reference/chttpconnection-class.md) y [objeto CGopherConnection](../../mfc/reference/cgopherconnection-class.md).  
  
## <a name="example"></a>Ejemplo  
  Vea el ejemplo de la [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) Introducción a la clase.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CFtpConnection`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxinet.h  
  
##  <a name="cftpconnection"></a>CFtpConnection::CFtpConnection  
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
 `pSession`  
 Un puntero a relacionado [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto.  
  
 `hConnected`  
 El identificador de Windows de la sesión actual de Internet.  
  
 `pstrServer`  
 Un puntero a una cadena que contiene el nombre del servidor FTP.  
  
 `dwContext`  
 El identificador de contexto para la operación. `dwContext`identifica la información de estado de la operación devuelta por [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). El valor predeterminado se establece en 1; Sin embargo, puede asignar explícitamente un identificador de contexto específico para la operación. El objeto y cualquier trabajo que se asociarán con ese identificador de contexto.  
  
 `pstrUserName`  
 Puntero a una cadena terminada en null que especifica el nombre del usuario para iniciar sesión. Si **NULL**, el valor predeterminado es anónimo.  
  
 `pstrPassword`  
 Un puntero a una cadena terminada en null que especifica la contraseña que se utilizará para iniciar sesión. Si ambos `pstrPassword` y `pstrUserName` son **NULL**, la contraseña anónima predeterminada es el nombre de correo electrónico del usuario. Si `pstrPassword` es **NULL** (o una cadena vacía), pero `pstrUserName` no **NULL**, se utiliza una contraseña en blanco. En la tabla siguiente describe el comportamiento de las cuatro configuraciones posibles de `pstrUserName` y `pstrPassword`:  
  
|`pstrUserName`|`pstrPassword`|Nombre de usuario que se envía al servidor FTP|Contraseña que se envían al servidor FTP|  
|--------------------|--------------------|---------------------------------|---------------------------------|  
|**NULL** o ""|**NULL** o ""|"anónimo"|Nombre de correo electrónico del usuario|  
|No- **NULL** cadena|**NULL** o ""|`pstrUserName`|" "|  
|**NULL** no **NULL** cadena|**ERROR**|**ERROR**||  
|No- **NULL** cadena|No- **NULL** cadena|`pstrUserName`|`pstrPassword`|  
  
 `nPort`  
 Número que identifica el puerto TCP/IP que se usará en el servidor.  
  
 `bPassive`  
 Especifica el modo pasivo o activo para esta sesión FTP. Si establece en **TRUE**, Establece la API de Win32 `dwFlag` a **INTERNET_FLAG_PASSIVE**.  
  
### <a name="remarks"></a>Comentarios  
 No cree nunca un `CFtpConnection` objeto directamente. En su lugar, llame a [CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), que crea el **CFptConnection** objeto.  
  
##  <a name="command"></a>CFtpConnection::Command  
 Envía un comando directamente a un servidor FTP.  
  
```  
CInternetFile* Command(
    LPCTSTR pszCommand,  
    CmdResponseType eResponse = CmdRespNone,  
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parámetros  
 `pszCommand`  
 Un puntero a una cadena que contiene el comando que se enviará.  
  
 *eResponse*  
 Determina si se espera una respuesta del servidor FTP. Puede presentar uno de los siguientes valores:  
  
- **CmdRespNone** se espera ninguna respuesta.  
  
- **CmdRespRead** se espera una respuesta.  
  
 `dwFlags`  
 Un valor que contiene las marcas que controlan esta función. Para obtener una lista completa, consulte [FTPCommand](http://msdn.microsoft.com/library/windows/desktop/aa384133).  
  
 `dwContext`  
 Un puntero a un valor que contiene un valor definido por la aplicación, que se utiliza para identificar el contexto de la aplicación en las devoluciones de llamada.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la [FTPCommand](http://msdn.microsoft.com/library/windows/desktop/aa384133) funcione, tal y como se describe en el SDK de Windows.  
  
 Si se produce un error, MFC inicia una excepción de tipo [CInternetException](../../mfc/reference/cinternetexception-class.md).  
  
##  <a name="createdirectory"></a>CFtpConnection::CreateDirectory  
 Llame a esta función miembro para crear un directorio en el servidor conectado.  
  
```  
BOOL CreateDirectory(LPCTSTR pstrDirName);
```  
  
### <a name="parameters"></a>Parámetros  
 `pstrDirName`  
 Un puntero a una cadena que contiene el nombre del directorio que se va a crear.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Windows [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.  
  
### <a name="remarks"></a>Comentarios  
 Utilice `GetCurrentDirectory` para determinar el directorio de trabajo actual para esta conexión al servidor. No se da por supuesto que el sistema remoto ha conectado al directorio raíz.  
  
 El `pstrDirName` parámetro puede ser un parcialmente o un nombre de archivo completo en relación con el directorio actual. Una barra diagonal inversa (\\) o barra diagonal (/) se puede utilizar como separador de directorio para cualquier nombre. `CreateDirectory`traduce los separadores de nombre de directorio para los caracteres apropiados antes de utilizarlos.  
  
##  <a name="getcurrentdirectory"></a>CFtpConnection:: GetCurrentDirectory  
 Llame a esta función miembro para obtener el nombre del directorio actual.  
  
```  
BOOL GetCurrentDirectory(CString& strDirName) const;  
  
BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,  
    LPDWORD lpdwLen) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `strDirName`  
 Una referencia a una cadena que recibirá el nombre del directorio.  
  
 `pstrDirName`  
 Un puntero a una cadena que recibirá el nombre del directorio.  
  
 `lpdwLen`  
 Un puntero a un valor de DWORD que contiene la información siguiente:  
  
|||  
|-|-|  
|En la entrada|El tamaño del búfer al que hace referencia `pstrDirName`.|  
|Una vez devuelta|El número de caracteres que se almacenan en `pstrDirName`. Si se produce un error en la función miembro y, a continuación, se devuelve ERROR_INSUFFICIENT_BUFFER `lpdwLen` contiene el número de bytes que se debe asignar la aplicación para recibir la cadena.|  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener el nombre del directorio como una dirección URL en su lugar, llame a [GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl).  
  
 Los parámetros `pstrDirName` o `strDirName` puede ser cualquiera de los nombres de archivo parciales relativo al directorio actual o completo. Una barra diagonal inversa (\\) o barra diagonal (/) se puede utilizar como separador de directorio para cualquier nombre. `GetCurrentDirectory`traduce los separadores de nombre de directorio para los caracteres apropiados antes de utilizarlos.  
  
##  <a name="getcurrentdirectoryasurl"></a>CFtpConnection:: GetCurrentDirectoryAsURL  
 Llame a esta función miembro para obtener el nombre del directorio actual como una dirección URL.  
  
```  
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;  
  
BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,  
    LPDWORD lpdwLen) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `strDirName`  
 Una referencia a una cadena que recibirá el nombre del directorio.  
  
 `pstrDirName`  
 Un puntero a una cadena que recibirá el nombre del directorio.  
  
 `lpdwLen`  
 Un puntero a un valor de DWORD que contiene la información siguiente:  
  
|||  
|-|-|  
|En la entrada|El tamaño del búfer al que hace referencia `pstrDirName`.|  
|Una vez devuelta|El número de caracteres que se almacenan en `pstrDirName`. Si se produce un error en la función miembro y, a continuación, se devuelve ERROR_INSUFFICIENT_BUFFER `lpdwLen` contiene el número de bytes que se debe asignar la aplicación para recibir la cadena.|  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.  
  
### <a name="remarks"></a>Comentarios  
 `GetCurrentDirectoryAsURL`se comporta igual que [GetCurrentDirectory](#getcurrentdirectory)  
  
 El parámetro `strDirName` puede ser cualquiera de los nombres de archivo parciales relativo al directorio actual o completo. Una barra diagonal inversa (\\) o barra diagonal (/) se puede utilizar como separador de directorio para cualquier nombre. `GetCurrentDirectoryAsURL`traduce los separadores de nombre de directorio para los caracteres apropiados antes de utilizarlos.  
  
##  <a name="getfile"></a>CFtpConnection::GetFile  
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
 `pstrRemoteFile`  
 Un puntero a una cadena terminada en null que contiene el nombre de un archivo que se va a recuperar desde el servidor FTP.  
  
 `pstrLocalFile`  
 Un puntero a una cadena terminada en null que contiene el nombre del archivo que se crea en el sistema local.  
  
 *bFailIfExists*  
 Indica si el nombre de archivo ya se puede usar un archivo existente. Si ya existe el nombre de archivo local, y este parámetro es **TRUE**, `GetFile` se produce un error. En caso contrario, `GetFile` borrará la copia existente del archivo.  
  
 `dwAttributes`  
 Indica los atributos del archivo. Esto puede ser cualquier combinación de las siguientes marcas FILE_ATTRIBUTE_ *.  
  
-   FILE_ATTRIBUTE_ARCHIVE el archivo es un archivo de almacenamiento. Las aplicaciones utilizan este atributo para marcar los archivos de copia de seguridad o eliminación.  
  
-   FILE_ATTRIBUTE_COMPRESSED el archivo o directorio se comprime. Para un archivo, la compresión significa que todos los datos en el archivo se comprime. Para un directorio, la compresión es el valor predeterminado para los archivos recién creados y subdirectorios.  
  
-   FILE_ATTRIBUTE_DIRECTORY el archivo es un directorio.  
  
-   FILE_ATTRIBUTE_NORMAL el archivo no tiene otros atributos establecido. Este atributo solo es válido si se utiliza solo. Todos los demás atributos de archivo invalidan FILE_ATTRIBUTE_NORMAL:  
  
-   FILE_ATTRIBUTE_HIDDEN el archivo está oculto. No es va a incluir en un listado de directorios normal.  
  
-   FILE_ATTRIBUTE_READONLY el archivo es de solo lectura. Las aplicaciones pueden leer el archivo pero no se puede escribir en él o eliminarlo.  
  
-   FILE_ATTRIBUTE_SYSTEM el archivo forma parte de o se usa exclusivamente por el sistema operativo.  
  
-   FILE_ATTRIBUTE_TEMPORARY el archivo se está usando para el almacenamiento temporal. Las aplicaciones deben escribir en el archivo sólo cuando sea absolutamente necesario. La mayoría de los datos del archivo permanece en memoria y no se vuelca en el medio porque pronto se eliminará el archivo.  
  
 `dwFlags`  
 Especifica las condiciones en las que se produce la transferencia. Este parámetro puede ser cualquiera de los `dwFlags` describen los valores de [FtpGetFile](http://msdn.microsoft.com/library/windows/desktop/aa384157) en el SDK de Windows.  
  
 `dwContext`  
 El identificador de contexto para la recuperación de archivos. Vea **comentarios** para obtener más información acerca de `dwContext`.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.  
  
### <a name="remarks"></a>Comentarios  
 `GetFile`es una rutina de alto nivel que se encarga de toda la sobrecarga asociada a leer un archivo desde un servidor FTP y almacenarlos localmente. Las aplicaciones que solo recuperan datos de archivo, o que requieren un control detallado sobre la transferencia de archivos, deben utilizar `OpenFile` y [CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read) en su lugar.  
  
 Si `dwFlags` es FILE_TRANSFER_TYPE_ASCII, traducción de datos de archivo también convierte control y aplicar formato a caracteres en equivalentes de Windows. La transferencia predeterminado es el modo binario, donde se descarga el archivo en el mismo formato tal y como se almacena en el servidor.  
  
 Ambos `pstrRemoteFile` y `pstrLocalFile` puede ser cualquiera de los nombres de archivo parciales relativo al directorio actual o completo. Una barra diagonal inversa (\\) o barra diagonal (/) se puede utilizar como separador de directorio para cualquier nombre. `GetFile`traduce los separadores de nombre de directorio para los caracteres apropiados antes de utilizarlos.  
  
 Reemplace el valor predeterminado de `dwContext` para establecer el identificador de contexto en un valor que desee. El identificador de contexto está asociado a esta operación específica de la `CFtpConnection` objeto creado por su [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto. El valor se devuelve a [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con el que se identifica. Vea el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.  
  
##  <a name="openfile"></a>CFtpConnection:: OpenFile  
 Llame a esta función miembro para abrir un archivo que se encuentra en un servidor FTP para leer o escribir.  
  
```  
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,  
    DWORD dwAccess = GENERIC_READ,  
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parámetros  
 `pstrFileName`  
 Un puntero a una cadena que contiene el nombre del archivo que se puede abrir.  
  
 *dwAccess*  
 Determina cómo se accederá el archivo. Puede ser GENERIC_READ o GENERIC_WRITE, pero no ambos.  
  
 `dwFlags`  
 Especifica las condiciones en las que se producen las transferencias posteriores. Esto puede ser cualquiera de las siguientes constantes FTP_TRANSFER_ *:  
  
-   FTP_TRANSFER_TYPE_ASCII el archivo se transfiere mediante el método de transferencia ASCII de FTP (Type A). Convierte control y la información de formato para equivalentes locales.  
  
-   FTP_TRANSFER_TYPE_BINARY el archivo transfiere los datos mediante el método de transferencia de la imagen de FTP (tipo I). El archivo transfiere los datos tal y como existen en sin cambios. Este es el método de transferencia de manera predeterminada.  
  
 `dwContext`  
 El identificador de contexto para abrir el archivo. Vea **comentarios** para obtener más información acerca de `dwContext`.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CInternetFile](../../mfc/reference/cinternetfile-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 `OpenFile`debe utilizarse en las situaciones siguientes:  
  
-   Una aplicación tiene datos que es necesario que se envíen y se crea como un archivo en el servidor FTP, pero que los datos no están en un archivo local. Una vez `OpenFile` abre un archivo, la aplicación usa [CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write) para enviar los datos de archivo FTP al servidor.  
  
-   Una aplicación debe recuperar un archivo desde el servidor y lo coloca en la memoria controlada a la aplicación, en lugar de escribir en el disco. La aplicación usa [CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read) después de usar `OpenFile` para abrir el archivo.  
  
-   Una aplicación necesita un nivel exhaustivo de control sobre una transferencia de archivos. Por ejemplo, la aplicación puede mostrar un progreso control indicar el progreso del estado de transferencia de archivos mientras se descarga un archivo.  
  
 Después de llamar a `OpenFile` y hasta que realiza la llamada **CInternetConnection::Close**, la aplicación solo puede llamar a [CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read), [CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write), **CInternetConnection::Close**, o [CFtpFileFind:: FindFile](../../mfc/reference/cftpfilefind-class.md#findfile). Llamadas a otras funciones FTP para la misma sesión FTP se producirá un error y establece el código de error en FTP_ETRANSFER_IN_PROGRESS.  
  
 El `pstrFileName` parámetro puede ser un parcial filename acceso completa o relativa al directorio actual. Una barra diagonal inversa (\\) o barra diagonal (/) se puede utilizar como separador de directorio para cualquier nombre. `OpenFile`traduce los separadores de nombre de directorio para los caracteres apropiados antes de usarlo.  
  
 Reemplace el valor predeterminado de `dwContext` para establecer el identificador de contexto en un valor que desee. El identificador de contexto está asociado a esta operación específica de la `CFtpConnection` objeto creado por su [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto. El valor se devuelve a [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con el que se identifica. Vea el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.  
  
##  <a name="putfile"></a>CFtpConnection::PutFile  
 Llame a esta función miembro para almacenar un archivo en un servidor FTP.  
  
```  
BOOL PutFile(
    LPCTSTR pstrLocalFile,  
    LPCTSTR pstrRemoteFile,  
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parámetros  
 `pstrLocalFile`  
 Un puntero a una cadena que contiene el nombre del archivo que se envía desde el sistema local.  
  
 `pstrRemoteFile`  
 Un puntero a una cadena que contiene el nombre del archivo que se crea en el servidor FTP.  
  
 `dwFlags`  
 Especifica las condiciones en las que se produce la transferencia del archivo. Puede ser cualquiera de las constantes FTP_TRANSFER_ * descritas en [OpenFile](#openfile).  
  
 `dwContext`  
 El identificador de contexto para colocar el archivo. Vea **comentarios** para obtener más información acerca de `dwContext`.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.  
  
### <a name="remarks"></a>Comentarios  
 `PutFile`es una rutina de alto nivel que controla todas las operaciones asociadas con el almacenamiento de un archivo en un servidor FTP. Las aplicaciones que solo enviar datos, o que requieran mayor control sobre la transferencia de archivos, deben utilizar [OpenFile](#openfile) y [CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write).  
  
 Reemplace el valor predeterminado de `dwContext` para establecer el identificador de contexto en un valor que desee. El identificador de contexto está asociado a esta operación específica de la `CFtpConnection` objeto creado por su [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto. El valor se devuelve a [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con el que se identifica. Vea el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.  
  
##  <a name="remove"></a>CFtpConnection:: Remove  
 Llame a esta función miembro para eliminar el archivo especificado desde el servidor conectado.  
  
```  
BOOL Remove(LPCTSTR pstrFileName);
```  
  
### <a name="parameters"></a>Parámetros  
 `pstrFileName`  
 Un puntero a una cadena que contiene el nombre de archivo para quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.  
  
### <a name="remarks"></a>Comentarios  
 El `pstrFileName` parámetro puede ser un parcial filename acceso completa o relativa al directorio actual. Una barra diagonal inversa (\\) o barra diagonal (/) se puede utilizar como separador de directorio para cualquier nombre. El **quitar** función traduce los separadores de nombre de directorio para los caracteres apropiados antes de utilizarlos.  
  
##  <a name="removedirectory"></a>CFtpConnection::RemoveDirectory  
 Llame a esta función miembro para quitar el directorio especificado desde el servidor conectado.  
  
```  
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```  
  
### <a name="parameters"></a>Parámetros  
 `pstrDirName`  
 Un puntero a una cadena que contiene el directorio que se va a quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.  
  
### <a name="remarks"></a>Comentarios  
 Use [GetCurrentDirectory](#getcurrentdirectory) para determinar el directorio de trabajo actual del servidor. No se da por supuesto que el sistema remoto ha conectado al directorio raíz.  
  
 El `pstrDirName` parámetro puede ser cualquier un nombre parcial o completo relativo al directorio actual. Una barra diagonal inversa (\\) o barra diagonal (/) se puede utilizar como separador de directorio para cualquier nombre. `RemoveDirectory`traduce los separadores de nombre de directorio para los caracteres apropiados antes de utilizarlos.  
  
##  <a name="rename"></a>CFtpConnection::Rename  
 Llame a esta función miembro para cambiar el nombre del archivo especificado en el servidor conectado.  
  
```  
BOOL Rename(
    LPCTSTR pstrExisting,  
    LPCTSTR pstrNew);
```  
  
### <a name="parameters"></a>Parámetros  
 `pstrExisting`  
 Un puntero a una cadena que contiene el nombre actual del archivo se va a cambiar.  
  
 `pstrNew`  
 Un puntero a una cadena que contiene el nombre del archivo nuevo.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.  
  
### <a name="remarks"></a>Comentarios  
 El `pstrExisting` y `pstrNew` parámetros pueden ser cualquier un nombre de archivo parcial acceso completa o relativa al directorio actual. Una barra diagonal inversa (\\) o barra diagonal (/) se puede utilizar como separador de directorio para cualquier nombre. **Cambiar el nombre de** traduce los separadores de nombre de directorio para los caracteres apropiados antes de utilizarlos.  
  
##  <a name="setcurrentdirectory"></a>CFtpConnection:: SetCurrentDirectory  
 Llame a esta función miembro para cambiar a un directorio diferente en el servidor FTP.  
  
```  
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```  
  
### <a name="parameters"></a>Parámetros  
 `pstrDirName`  
 Un puntero a una cadena que contiene el nombre del directorio.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.  
  
### <a name="remarks"></a>Comentarios  
 El `pstrDirName` parámetro puede ser cualquier un nombre parcial o completo relativo al directorio actual. Una barra diagonal inversa (\\) o barra diagonal (/) se puede utilizar como separador de directorio para cualquier nombre. `SetCurrentDirectory`traduce los separadores de nombre de directorio para los caracteres apropiados antes de utilizarlos.  
  
 Use [GetCurrentDirectory](#getcurrentdirectory) para determinar el directorio de trabajo actual de un servidor FTP. No se da por supuesto que el sistema remoto ha conectado al directorio raíz.  
  
## <a name="see-also"></a>Vea también  
 [Clase de objeto CInternetConnection](../../mfc/reference/cinternetconnection-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clase de objeto CInternetConnection](../../mfc/reference/cinternetconnection-class.md)   
 [CInternetSession (clase)](../../mfc/reference/cinternetsession-class.md)
