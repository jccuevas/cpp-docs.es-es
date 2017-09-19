---
title: CFtpFileFind (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFtpFileFind
- AFXINET/CFtpFileFind
- AFXINET/CFtpFileFind::CFtpFileFind
- AFXINET/CFtpFileFind::FindFile
- AFXINET/CFtpFileFind::FindNextFile
- AFXINET/CFtpFileFind::GetFileURL
dev_langs:
- C++
helpviewer_keywords:
- CFtpFileFind class
- file searches [C++]
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 6e84282cc2f22e813ea44318d497c7e32e3280d8
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cftpfilefind-class"></a>CFtpFileFind (clase)
Ayuda en las búsquedas del archivo de Internet de servidores FTP.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CFtpFileFind : public CFileFind  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFtpFileFind::CFtpFileFind](#cftpfilefind)|Construye un objeto `CFtpFileFind`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFtpFileFind:: FindFile](#findfile)|Busca un archivo en un servidor FTP.|  
|[CFtpFileFind:: FindNextFile](#findnextfile)|Continúa la búsqueda de archivos de una llamada anterior a [FindFile](#findfile).|  
|[CFtpFileFind::GetFileURL](#getfileurl)|Obtiene la dirección URL, incluida la ruta de acceso del archivo encontrado.|  
  
## <a name="remarks"></a>Comentarios  
 `CFtpFileFind`incluye funciones miembro que se inicia la búsqueda, busque un archivo y devuelvan la dirección URL u otra información descriptiva acerca del archivo.  
  
 Otras clases MFC diseñados para Internet y archivo local buscará incluyen [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) y [CFileFind](../../mfc/reference/cfilefind-class.md). Junto con `CFtpFileFind`, estas clases proporcionan un mecanismo transparente para el cliente buscar archivos específicos, independientemente del servidor de protocolo o tipo de archivo (un equipo local o un servidor remoto). Tenga en cuenta que no hay ninguna clase MFC para las búsquedas en servidores HTTP porque HTTP no admite la manipulación de archivos directamente necesaria para las búsquedas.  
  
 Para obtener más información acerca de cómo usar `CFtpFileFind` y las otras clases WinInet, vea el artículo [programación para Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="example"></a>Ejemplo  
 El código siguiente muestra cómo enumerar todos los archivos en el directorio actual del servidor FTP.  
  
 [!code-cpp[NVC_MFCWinInet Nº&8;](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFileFind](../../mfc/reference/cfilefind-class.md)  
  
 `CFtpFileFind`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxinet.h  
  
##  <a name="cftpfilefind"></a>CFtpFileFind::CFtpFileFind  
 Llama a esta función miembro para construir un `CFtpFileFind` objeto.  
  
```  
explicit CFtpFileFind(
    CFtpConnection* pConnection,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parámetros  
 `pConnection`  
 Un puntero a un `CFtpConnection` objeto. Puede obtener una conexión FTP mediante una llamada a [CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection).  
  
 `dwContext`  
 El identificador de contexto para la `CFtpFileFind` objeto. Consulte **comentarios** para obtener más información acerca de este parámetro.  
  
### <a name="remarks"></a>Comentarios  
 El valor predeterminado de `dwContext` enviados por MFC para la `CFtpFileFind` objeto desde el [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto que creó el `CFtpFileFind` objeto. Puede invalidar el valor predeterminado para establecer el identificador de contexto en un valor de su elección. El identificador de contexto se devuelve a [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Consulte el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de la información general de la clase anteriormente en este tema.  
  
##  <a name="findfile"></a>CFtpFileFind:: FindFile  
 Llame a esta función miembro para buscar un archivo FTP.  
  
```  
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,  
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```  
  
### <a name="parameters"></a>Parámetros  
 `pstrName`  
 Puntero a una cadena que contiene el nombre del archivo que se va a buscar. Si **NULL**, la llamada realizará una búsqueda de carácter comodín (*).  
  
 `dwFlags`  
 Las marcas que describen cómo controlar esta sesión. Estas marcas se pueden combinar con el operador OR bit a bit (|) y son los siguientes:  
  
-   INTERNET_FLAG_RELOAD obtener los datos de la conexión aunque localmente se almacena en caché. Se trata de la marca predeterminada.  
  
-   INTERNET_FLAG_DONT_CACHE no almacenar en caché los datos, ya sea localmente o en las puertas de enlace.  
  
-   INTERNET_FLAG_RAW_DATA reemplazar el valor predeterminado para devolver los datos sin procesar ( [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) estructuras de FTP).  
  
-   INTERNET_FLAG_SECURE protege las transacciones en la conexión con la capa de Sockets seguros o PCT. Este indicador es aplicable a las solicitudes HTTP solo.  
  
-   INTERNET_FLAG_EXISTING_CONNECT si es posible, reutilizar las conexiones existentes en el servidor para el nuevo **FindFile** solicitudes en lugar de crear una nueva sesión para cada solicitud.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Para obtener información de error extendida, llame a la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Comentarios  
 Después de llamar a **FindFile** para recuperar el primer archivo FTP, puede llamar a [FindNextFile](#findnextfile) para recuperar los archivos FTP subsiguientes.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo anterior de este tema.  
  
##  <a name="findnextfile"></a>CFtpFileFind:: FindNextFile  
 Llame a esta función miembro para continuar una búsqueda de archivo comenzada con una llamada a la [FindFile](#findfile) función miembro.  
  
```  
virtual BOOL FindNextFile();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si no hay más archivos; cero si el archivo se encuentra es la última en el directorio o si se produjo un error. Para obtener información de error extendida, llame a la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360). Si el archivo se encuentra es el último archivo en el directorio, o si no hay coincidencia de archivos pueden encontrarse el `GetLastError` función devuelve ERROR_NO_MORE_FILES.  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a esta función al menos una vez antes de llamar a cualquier función de atributo (consulte [CFileFind::FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)).  
  
 `FindNextFile`contiene la función de Win32 [FindNextFile](http://msdn.microsoft.com/library/windows/desktop/aa364428).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo anterior de este tema.  
  
##  <a name="getfileurl"></a>CFtpFileFind::GetFileURL  
 Llame a esta función miembro para obtener la dirección URL del archivo especificado.  
  
```  
CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El archivo y la ruta de acceso del localizador de recursos Universal (URL).  
  
### <a name="remarks"></a>Comentarios  
 `GetFileURL`es similar a la función miembro [CFileFind::GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath), excepto en que devuelve la dirección URL en el formulario `ftp://moose/dir/file.txt`.  
  
## <a name="see-also"></a>Vea también  
 [Clase CFileFind](../../mfc/reference/cfilefind-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)   
 [CInternetFile (clase)](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile (clase)](../../mfc/reference/cgopherfile-class.md)   
 [Clase CHttpFile](../../mfc/reference/chttpfile-class.md)

