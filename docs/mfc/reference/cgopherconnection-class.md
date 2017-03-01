---
title: Clase de objeto CGopherConnection | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGopherConnection
dev_langs:
- C++
helpviewer_keywords:
- servers, connecting to
- Internet server, gopher
- connecting to servers, gopher servers
- protocols, gopher
- services, gopher
- CGopherConnection class
- gopher protocol
- gopher server
- connecting to servers
- Internet connections, gopher
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
caps.latest.revision: 21
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 6267dd226e87e5bf64faa7225e49d9a99af93e3e
ms.lasthandoff: 02/24/2017

---
# <a name="cgopherconnection-class"></a>Clase de objeto CGopherConnection
Administra la conexión a un servidor de Internet de gopher.  
  
> [!NOTE]
>  Las clases de `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` y sus miembros han quedado en desuso porque no funcionan en la plataforma Windows XP, pero seguirá funcionando en plataformas anteriores.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CGopherConnection : public CInternetConnection  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CGopherConnection::CGopherConnection](#cgopherconnection)|Construye un objeto `CGopherConnection`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CGopherConnection:: CreateLocator](#createlocator)|Crea un [objeto CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto para buscar archivos en un servidor gopher.|  
|[CGopherConnection::GetAttribute](#getattribute)|Recupera información de atributo sobre el objeto de gopher.|  
|[CGopherConnection:: OpenFile](#openfile)|Abre un archivo gopher.|  
  
## <a name="remarks"></a>Comentarios  
 El servicio gopher es uno de los tres servicios de Internet reconocidos por las clases WinInet de MFC.  
  
 La clase `CGopherConnection` contiene un constructor y tres funciones de miembro adicionales que administran el servicio gopher: [OpenFile](#openfile), [CreateLocator](#createlocator), y [GetAttribute](#getattribute).  
  
 Para comunicarse con un servidor de Internet de gopher, primero debe crear una instancia de [CInternetSession](../../mfc/reference/cinternetsession-class.md)y, a continuación, llame a [CInternetSession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), que crea el `CGopherConnection` de objetos y devuelve un puntero a ella. No cree nunca un `CGopherConnection` objeto directamente.  
  
 Para obtener más información acerca de cómo `CGopherConnection` funciona con otras clases de Internet de MFC, vea el artículo [programación para Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md). Para obtener más información acerca del uso de los otros dos admite servicios de Internet, FTP y HTTP vea las clases [objeto CHttpConnection](../../mfc/reference/chttpconnection-class.md) y [CFtpConnection](../../mfc/reference/cftpconnection-class.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CGopherConnection`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxinet.h  
  
##  <a name="a-namecgopherconnectiona--cgopherconnectioncgopherconnection"></a><a name="cgopherconnection"></a>CGopherConnection::CGopherConnection  
 Llama a esta función miembro para construir un `CGopherConnection` objeto.  
  
```  
CGopherConnection(
    CInternetSession* pSession,  
    HINTERNET hConnected,  
    LPCTSTR pstrServer,  
    DWORD_PTR dwContext);

 
CGopherConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    DWORD_PTR dwContext = 0,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSession`  
 Un puntero a la relacionados [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto.  
  
 `hConnected`  
 Identificador de Windows de la sesión actual de Internet.  
  
 `pstrServer`  
 Puntero a una cadena que contiene el nombre del servidor FTP.  
  
 `dwContext`  
 El identificador de contexto para la operación. `dwContext`identifica la información de estado de la operación devuelta por [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). El valor predeterminado se establece en 1; Sin embargo, puede asignar explícitamente un Id. de contexto específico para la operación. El objeto y cualquier trabajo que se asociarán con ese identificador de contexto.  
  
 `pstrUserName`  
 Puntero a una cadena terminada en null que especifica el nombre del usuario para iniciar sesión. Si **NULL**, el valor predeterminado es anónimo.  
  
 `pstrPassword`  
 Un puntero a una cadena terminada en null que especifica la contraseña que use para iniciar sesión. Si ambos `pstrPassword` y `pstrUserName` son **NULL**, la contraseña anónima predeterminada es el nombre de correo electrónico del usuario. Si `pstrPassword` es **NULL** (o una cadena vacía) pero `pstrUserName` no **NULL**, se utiliza una contraseña en blanco. En la tabla siguiente describe el comportamiento de las cuatro configuraciones posibles de `pstrUserName` y `pstrPassword`:  
  
|`pstrUserName`|`pstrPassword`|Nombre de usuario que se envía al servidor FTP|Contraseña que se envían al servidor FTP|  
|--------------------|--------------------|---------------------------------|---------------------------------|  
|**NULL** o ""|**NULL** o ""|"anónimo"|Nombre de correo electrónico del usuario|  
|No- **NULL** cadena|**NULL** o ""|`pstrUserName`|" "|  
|**NULL** no **NULL** cadena|**ERROR**|**ERROR**||  
|No- **NULL** cadena|No- **NULL** cadena|`pstrUserName`|`pstrPassword`|  
  
 `nPort`  
 Número que identifica el puerto TCP/IP en el servidor.  
  
### <a name="remarks"></a>Comentarios  
 No cree nunca un `CGopherConnection` directamente. En su lugar, llame a [CInternetSession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), que crea un `CGopherConnection` de objetos y devuelve un puntero a ella.  
  
##  <a name="a-namecreatelocatora--cgopherconnectioncreatelocator"></a><a name="createlocator"></a>CGopherConnection:: CreateLocator  
 Llame a esta función miembro para crear un localizador gopher para buscar o identificar un archivo en un servidor gopher.  
  
```  
CGopherLocator CreateLocator(
    LPCTSTR pstrDisplayString,  
    LPCTSTR pstrSelectorString,  
    DWORD dwGopherType);  
  
static CGopherLocator CreateLocator(LPCTSTR pstrLocator);

 
static CGopherLocator CreateLocator(
    LPCTSTR pstrServerName,  
    LPCTSTR pstrDisplayString,  
    LPCTSTR pstrSelectorString,  
    DWORD dwGopherType,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```  
  
### <a name="parameters"></a>Parámetros  
 `pstrDisplayString`  
 Un puntero a una cadena que contiene el nombre del documento gopher o directorio que desea recuperar. Si el `pstrDisplayString` parámetro es **NULL**, se devuelve el directorio predeterminado para el servidor gopher.  
  
 `pstrSelectorString`  
 Puntero a la cadena de selector para enviarse al servidor gopher para recuperar un elemento. `pstrSelectorString`puede ser **NULL**.  
  
 *dwGopherType*  
 Especifica si `pstrSelectorString` hace referencia a un directorio o un documento, y si la solicitud es gopher o gopher +. Ver los atributos de la estructura [GOPHER_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa384215) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `pstrLocator`  
 Puntero a una cadena que identifica el archivo que desea abrir. Por lo general, esta cadena se devuelve de una llamada a [CGopherFileFind:: GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator).  
  
 *pstrServerName*  
 Puntero a una cadena que contiene el nombre del servidor gopher.  
  
 `nPort`  
 Número que identifica el puerto de Internet para esta conexión.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [objeto CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 La versión de la función miembro estática requiere que especifique un servidor, mientras que la versión no estático utiliza el nombre del servidor desde el objeto de conexión.  
  
 Para recuperar información de un servidor gopher, una aplicación primero debe obtener un localizador gopher. La aplicación debe tratar el localizador como un token opaco (es decir, la aplicación puede utilizar el localizador pero no directamente manipular o compararlo). Normalmente, la aplicación utiliza el localizador de llamadas a la [CGopherFileFind:: FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) función miembro para recuperar una parte específica de la información.  
  
##  <a name="a-namegetattributea--cgopherconnectiongetattribute"></a><a name="getattribute"></a>CGopherConnection::GetAttribute  
 Llame a esta función miembro para recuperar información de atributos específicos acerca de los elementos del servidor gopher.  
  
```  
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,  
    CString& strResult,);
```  
  
### <a name="parameters"></a>Parámetros  
 `refLocator`  
 Una referencia a un [objeto CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto.  
  
 *strRequestedAttributes*  
 Cadena delimitada por espacios especificando los nombres de los atributos solicitados.  
  
 `strResult`  
 Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que recibe el tipo de localizador.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamar para determinar la causa del error.  
  
##  <a name="a-nameopenfilea--cgopherconnectionopenfile"></a><a name="openfile"></a>CGopherConnection:: OpenFile  
 Llame a esta función miembro para abrir un archivo en un servidor gopher.  
  
```  
CGopherFile* OpenFile(
    CGopherLocator& refLocator,  
    DWORD dwFlags = 0,  
    LPCTSTR pstrView = NULL,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parámetros  
 `refLocator`  
 Una referencia a un [objeto CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto.  
  
 `dwFlags`  
 Cualquier combinación de indicadores de INTERNET_FLAG_. Consulte [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) para obtener más información sobre INTERNET_FLAG_\* marcas.  
  
 `pstrView`  
 Un puntero a una cadena de archivo de la vista. Si existen varias vistas del archivo en el servidor, este parámetro especifica qué vista de archivo que desea abrir. Si `pstrView` es **NULL**, se utiliza la vista de archivo predeterminada.  
  
 `dwContext`  
 El identificador de contexto para el archivo que se abre. Consulte **comentarios** para obtener más información acerca de `dwContext`.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la [CGopherFile](../../mfc/reference/cgopherfile-class.md) objeto abrirse.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace el valor predeterminado de `dwContext` para establecer el identificador de contexto en un valor que desee. El identificador de contexto está asociado a esta operación específica de la `CGopherConnection` objeto creado por su [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto. El valor se devuelve a [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con el que se identifica. Consulte el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.  
  
## <a name="see-also"></a>Vea también  
 [CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CFtpConnection](../../mfc/reference/cftpconnection-class.md)   
 [Clase de objeto CHttpConnection](../../mfc/reference/chttpconnection-class.md)   
 [CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)   
 [Clase de objeto CGopherLocator](../../mfc/reference/cgopherlocator-class.md)   
 [CGopherFile (clase)](../../mfc/reference/cgopherfile-class.md)   
 [CInternetSession (clase)](../../mfc/reference/cinternetsession-class.md)

