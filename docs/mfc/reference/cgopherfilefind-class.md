---
title: Clase CGopherFileFind | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CGopherFileFind
- AFXINET/CGopherFileFind
- AFXINET/CGopherFileFind::CGopherFileFind
- AFXINET/CGopherFileFind::FindFile
- AFXINET/CGopherFileFind::FindNextFile
- AFXINET/CGopherFileFind::GetCreationTime
- AFXINET/CGopherFileFind::GetLastAccessTime
- AFXINET/CGopherFileFind::GetLastWriteTime
- AFXINET/CGopherFileFind::GetLength
- AFXINET/CGopherFileFind::GetLocator
- AFXINET/CGopherFileFind::GetScreenName
- AFXINET/CGopherFileFind::IsDots
dev_langs:
- C++
helpviewer_keywords:
- CGopherFileFind [MFC], CGopherFileFind
- CGopherFileFind [MFC], FindFile
- CGopherFileFind [MFC], FindNextFile
- CGopherFileFind [MFC], GetCreationTime
- CGopherFileFind [MFC], GetLastAccessTime
- CGopherFileFind [MFC], GetLastWriteTime
- CGopherFileFind [MFC], GetLength
- CGopherFileFind [MFC], GetLocator
- CGopherFileFind [MFC], GetScreenName
- CGopherFileFind [MFC], IsDots
ms.assetid: 8465a979-6323-496d-ab4b-e81383fb999d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eae84c647f068e49136968e60bfd8bd51a528112
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038534"
---
# <a name="cgopherfilefind-class"></a>Clase CGopherFileFind
Ayuda en las búsquedas de archivos de Internet de servidores gopher.  
  
> [!NOTE]
>  Las clases de `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` y sus miembros se han quedado en desuso porque no funcionan en la plataforma Windows XP, pero continuarán funcionando en plataformas anteriores.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CGopherFileFind : public CFileFind  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGopherFileFind::CGopherFileFind](#cgopherfilefind)|Construye un objeto `CGopherFileFind`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGopherFileFind:: FindFile](#findfile)|Busca un archivo en un servidor gopher.|  
|[CGopherFileFind:: FindNextFile](#findnextfile)|Continúa una búsqueda de archivos de una llamada anterior a [FindFile](#findfile).|  
|[CGopherFileFind::GetCreationTime](#getcreationtime)|Obtiene la hora en que se creó el archivo especificado.|  
|[CGopherFileFind::GetLastAccessTime](#getlastaccesstime)|Obtiene la hora de que último acceso al archivo especificado.|  
|[CGopherFileFind::GetLastWriteTime](#getlastwritetime)|Obtiene la hora en que se escribió el archivo especificado por última.|  
|[CGopherFileFind::GetLength](#getlength)|Obtiene la longitud del archivo se encuentra, en bytes.|  
|[CGopherFileFind:: GetLocator](#getlocator)|Obtener un `CGopherLocator` objeto.|  
|[CGopherFileFind::GetScreenName](#getscreenname)|Obtiene el nombre de una pantalla de gopher.|  
|[CGopherFileFind::IsDots](#isdots)|Comprueba si los marcadores de directorio principal y el directorio actuales que se va iterando a través de archivos.|  
  
## <a name="remarks"></a>Comentarios  
 `CGopherFileFind` incluye funciones miembro que iniciar una búsqueda, busque un archivo y devuelven la dirección URL de un archivo.  
  
 Otras clases MFC diseñados para Internet y archivo local buscadas incluyen [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) y [CFileFind](../../mfc/reference/cfilefind-class.md). Junto con `CGopherFileFind`, estas clases proporcionan un mecanismo sin problemas para el usuario buscar archivos específicos, independientemente del protocolo del servidor, el tipo de archivo o la ubicación (un equipo local o un servidor remoto.) Tenga en cuenta que no hay ninguna clase MFC para las búsquedas en servidores HTTP porque HTTP no admite la manipulación directa de archivo requerida por las búsquedas.  
  
> [!NOTE]
> `CGopherFileFind` no admite las siguientes funciones de miembro de su clase base [CFileFind](../../mfc/reference/cfilefind-class.md):  
  
- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)  
  
- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)  
  
- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)  
  
- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)  
  
- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)  
  
 Además, cuando se usa con `CGopherFileFind`, `CFileFind` función miembro [IsDots](../../mfc/reference/cfilefind-class.md#isdots) siempre es **FALSE**.  
  
 Para obtener más información sobre cómo usar `CGopherFileFind` y las demás clases WinInet, vea el artículo [programación para Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFileFind](../../mfc/reference/cfilefind-class.md)  
  
 `CGopherFileFind`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxinet.h  
  
##  <a name="cgopherfilefind"></a>  CGopherFileFind::CGopherFileFind  
 Se llama a esta función miembro para construir un `CGopherFileFind` objeto.  
  
```  
explicit CGopherFileFind(
    CGopherConnection* pConnection,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parámetros  
 *pConnection*  
 Un puntero a un [objeto CGopherConnection](../../mfc/reference/cgopherconnection-class.md) objeto.  
  
 *dwContext*  
 El identificador de contexto para la operación. Vea **comentarios** para obtener más información acerca de *dwContext*.  
  
### <a name="remarks"></a>Comentarios  
 El valor predeterminado de *dwContext* se envía por MFC para la `CGopherFileFind` objeto desde el [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto que creó el `CGopherFileFind` objeto. Al construir un `CGopherFileFind` de objeto, puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve al [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Vea el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.  
  
##  <a name="findfile"></a>  CGopherFileFind:: FindFile  
 Llame a esta función miembro para buscar un archivo gopher.  
  
```  
virtual BOOL FindFile(
    CGopherLocator& refLocator,  
    LPCTSTR pstrString,  
    DWORD dwFlags = INTERNET_FLAG_RELOAD);

 
virtual BOOL FindFile(
    LPCTSTR pstrString,  
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```  
  
### <a name="parameters"></a>Parámetros  
 *refLocator*  
 Una referencia a un [objeto CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto.  
  
 *pstrString*  
 Un puntero a una cadena que contiene el nombre de archivo.  
  
 *dwFlags*  
 Las marcas que describen cómo controlar esta sesión. Las marcas válidas son:  
  
-   INTERNET_FLAG_RELOAD obtener los datos del servidor remoto, incluso si localmente se almacena en caché.  
  
-   INTERNET_FLAG_DONT_CACHE no almacenar en caché los datos, ya sea localmente o en las puertas de enlace.  
  
-   Solicitar INTERNET_FLAG_SECURE transacciones seguras en la conexión con la capa de Sockets seguros o PCT. Esta marca es aplicable a las solicitudes HTTP solo.  
  
-   INTERNET_FLAG_USE_EXISTING si es posible, reutilizar las conexiones existentes en el servidor para el nuevo **FindFile** solicitudes, en lugar de crear una nueva sesión para cada solicitud.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Para obtener información de error extendida, llame a la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Comentarios  
 Después de llamar a **FindFile** para recuperar el primer objeto gopher, puede llamar a [FindNextFile](#findnextfile) para recuperar archivos gopher posteriores.  
  
##  <a name="findnextfile"></a>  CGopherFileFind:: FindNextFile  
 Llame a esta función miembro para continuar una búsqueda de archivo iniciada con una llamada a [CGopherFileFind:: FindFile](#findfile).  
  
```  
virtual BOOL FindNextFile();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si no hay más archivos; Devuelve cero si se encuentra el archivo es la última de ellas en el directorio o si se produjo un error. Para obtener información de error extendida, llame a la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360). Si se encuentra el archivo es el último archivo en el directorio, o si no hay coincidencia de archivos pueden encontrarse los `GetLastError` función devuelve ERROR_NO_MORE_FILES.  
  
##  <a name="getcreationtime"></a>  CGopherFileFind::GetCreationTime  
 Obtiene la hora de creación para el archivo actual.  
  
```  
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;  
virtual BOOL GetCreationTime(CTime& refTime) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *pTimeStamp*  
 Un puntero a un [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) estructura que contiene la hora en que se creó el archivo.  
  
 *refTime*  
 Una referencia a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente; 0 si no lo consigue. `GetCreationTime` Devuelve 0 si [FindNextFile](#findnextfile) nunca se ha llamado en el objeto `CGopherFileFind` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes de llamar a `GetCreationTime`.  
  
> [!NOTE]
>  No todos los sistemas de archivos usan la misma semántica para implementar la marca de tiempo devuelta por esta función. Esta función puede devolver el mismo valor devuelto por otras funciones de marca de tiempo si el sistema de archivos o servidor subyacente no admite mantener el atributo de tiempo. Consulte la [Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) estructura para obtener información sobre formatos de hora. En algunos sistemas operativos, la hora devuelta está en la hora local de la zona a la máquina estaban se encuentra el archivo. Vea el Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) API para obtener más información.  
  
##  <a name="getlastaccesstime"></a>  CGopherFileFind::GetLastAccessTime  
 Obtiene la hora de que último acceso al archivo especificado.  
  
```  
virtual BOOL GetLastAccessTime(CTime& refTime) const;  
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *refTime*  
 Una referencia a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto.  
  
 *pTimeStamp*  
 Un puntero a un [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) estructura que contiene la hora de último acceso al archivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente; 0 si no lo consigue. `GetLastAccessTime` Devuelve 0 si [FindNextFile](#findnextfile) nunca se ha llamado en el objeto `CGopherFileFind` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes de llamar a `GetLastAccessTime`.  
  
> [!NOTE]
>  No todos los sistemas de archivos usan la misma semántica para implementar la marca de tiempo devuelta por esta función. Esta función puede devolver el mismo valor devuelto por otras funciones de marca de tiempo si el sistema de archivos o servidor subyacente no admite mantener el atributo de tiempo. Consulte la [Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) estructura para obtener información sobre formatos de hora. En algunos sistemas operativos, la hora devuelta está en la hora local de la zona a la máquina estaban se encuentra el archivo. Vea el Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) API para obtener más información.  
  
##  <a name="getlastwritetime"></a>  CGopherFileFind::GetLastWriteTime  
 Obtiene la última vez que se modificó el archivo.  
  
```  
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;  
virtual BOOL GetLastWriteTime(CTime& refTime) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *pTimeStamp*  
 Un puntero a un [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) estructura que contiene la hora en que se escribió el archivo por última.  
  
 *refTime*  
 Una referencia a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente; 0 si no lo consigue. `GetLastWriteTime` Devuelve 0 si [FindNextFile](#findnextfile) nunca se ha llamado en el objeto `CGopherFileFind` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes de llamar a `GetLastWriteTime`.  
  
> [!NOTE]
>  No todos los sistemas de archivos usan la misma semántica para implementar la marca de tiempo devuelta por esta función. Esta función puede devolver el mismo valor devuelto por otras funciones de marca de tiempo si el sistema de archivos o servidor subyacente no admite mantener el atributo de tiempo. Consulte la [Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) estructura para obtener información sobre formatos de hora. En algunos sistemas operativos, la hora devuelta está en la hora local de la zona a la máquina estaban se encuentra el archivo. Vea el Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) API para obtener más información.  
  
##  <a name="getlength"></a>  CGopherFileFind::GetLength  
 Llame a esta función miembro para obtener la longitud, en bytes, del archivo se encuentra.  
  
```  
virtual ULONGLONG GetLength() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud, en bytes, del archivo se encuentra.  
  
### <a name="remarks"></a>Comentarios  
 `GetLength` utiliza la estructura de Win32 [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) para obtener el valor del tamaño del archivo en bytes.  
  
> [!NOTE]
>  A partir de MFC 7.0, `GetLength` admite tipos enteros de 64 bits. Compiladas con esta versión más reciente de la biblioteca de código existentes anteriormente podrían producir advertencias de truncamiento de.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) (implementación de la clase base).  
  
##  <a name="getlocator"></a>  CGopherFileFind:: GetLocator  
 Llame a esta función miembro para obtener la [objeto CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto que [FindFile](#findfile) utiliza para buscar el archivo gopher.  
  
```  
CGopherLocator GetLocator() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un objeto `CGopherLocator`.  
  
##  <a name="getscreenname"></a>  CGopherFileFind::GetScreenName  
 Llame a esta función miembro para obtener el nombre de la pantalla de gopher.  
  
```  
CString GetScreenName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El nombre de la pantalla de gopher.  
  
##  <a name="isdots"></a>  CGopherFileFind::IsDots  
 Comprueba si los marcadores de directorio principal y el directorio actuales que se va iterando a través de archivos.  
  
```  
virtual BOOL IsDots() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el archivo se encuentra con el nombre "."o"..", lo que indica que el archivo se encuentra es realmente un directorio. En caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a [FindNextFile](#findnextfile) al menos una vez antes de llamar a `IsDots`.  
  
## <a name="see-also"></a>Vea también  
 [Clase CFileFind](../../mfc/reference/cfilefind-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFtpFileFind (clase)](../../mfc/reference/cftpfilefind-class.md)   
 [Clase CFileFind](../../mfc/reference/cfilefind-class.md)   
 [CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile (clase)](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile (clase)](../../mfc/reference/chttpfile-class.md)
