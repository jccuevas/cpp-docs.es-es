---
title: CGopherConnection (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CGopherConnection
- AFXINET/CGopherConnection
- AFXINET/CGopherConnection::CGopherConnection
- AFXINET/CGopherConnection::CreateLocator
- AFXINET/CGopherConnection::GetAttribute
- AFXINET/CGopherConnection::OpenFile
dev_langs:
- C++
helpviewer_keywords:
- CGopherConnection [MFC], CGopherConnection
- CGopherConnection [MFC], CreateLocator
- CGopherConnection [MFC], GetAttribute
- CGopherConnection [MFC], OpenFile
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f00a81aa7997591d152a665e14869f22bd14321
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377979"
---
# <a name="cgopherconnection-class"></a>CGopherConnection (clase)

Administra la conexión a un servidor de Internet de gopher.

> [!NOTE]
>  Las clases `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` y sus miembros se han quedado en desuso porque no funcionan en la plataforma Windows XP, pero seguirán funcionando en las plataformas anteriores.

## <a name="syntax"></a>Sintaxis

```
class CGopherConnection : public CInternetConnection
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CGopherConnection::CGopherConnection](#cgopherconnection)|Construye un objeto `CGopherConnection`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CGopherConnection:: CreateLocator](#createlocator)|Crea un [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto va a buscar archivos en un servidor gopher.|
|[CGopherConnection::GetAttribute](#getattribute)|Recupera información de atributos sobre el objeto gopher.|
|[CGopherConnection:: OpenFile](#openfile)|Abre un archivo gopher.|

## <a name="remarks"></a>Comentarios

El servicio gopher es uno de los tres servicios de Internet reconocidos por las clases WinInet de MFC.

La clase `CGopherConnection` contiene un constructor y tres funciones de miembro adicionales que administran el servicio gopher: [OpenFile](#openfile), [CreateLocator](#createlocator), y [GetAttribute](#getattribute).

Para comunicarse con un servidor de Internet de gopher, primero debe crear una instancia de [CInternetSession](../../mfc/reference/cinternetsession-class.md)y, a continuación, llame a [CInternetSession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), que crea el `CGopherConnection` objeto y devuelve un puntero a él. No crear nunca un `CGopherConnection` objeto directamente.

Para obtener más información sobre cómo `CGopherConnection` funciona con las clases de Internet de MFC, vea el artículo [Internet programar con WinInet](../../mfc/win32-internet-extensions-wininet.md). Para obtener más información sobre el uso de los otros dos admite servicios de Internet, HTTP y FTP vea las clases [CHttpConnection](../../mfc/reference/chttpconnection-class.md) y [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

##  <a name="cgopherconnection"></a>  CGopherConnection::CGopherConnection

Se llama a esta función miembro para construir un `CGopherConnection` objeto.

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

### <a name="remarks"></a>Comentarios

No crear nunca un `CGopherConnection` directamente. En su lugar, llame a [CInternetSession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), que crea un `CGopherConnection` de objetos y devuelve un puntero a él.

##  <a name="createlocator"></a>  CGopherConnection:: CreateLocator

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

*pstrDisplayString*<br/>
Un puntero a una cadena que contiene el nombre del documento gopher o del directorio va a recuperar. Si el *pstrDisplayString* parámetro es NULL, se devuelve el directorio predeterminado para el servidor gopher.

*pstrSelectorString*<br/>
Un puntero a la cadena de selector que deben enviarse al servidor gopher para recuperar un elemento. *pstrSelectorString* puede ser NULL.

*dwGopherType*<br/>
Especifica si *pstrSelectorString* hace referencia a un directorio o un documento, y si la solicitud es gopher o gopher +. Ver los atributos de la estructura [GOPHER_FIND_DATA](/windows/desktop/api/wininet/ns-wininet-gopher_find_dataa) en el SDK de Windows.

*pstrLocator*<br/>
Un puntero a una cadena que identifica el archivo que desea abrir. Por lo general, esta cadena se devuelve de una llamada a [CGopherFileFind:: GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator).

*pstrServerName*<br/>
Un puntero a una cadena que contiene el nombre del servidor gopher.

*nPort*<br/>
El número que identifica el puerto de Internet para esta conexión.

### <a name="return-value"></a>Valor devuelto

Un [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto.

### <a name="remarks"></a>Comentarios

La versión de la función miembro estática, deberá especificar un servidor, mientras que la versión no estáticos utiliza el nombre del servidor del objeto de conexión.

Con el fin de recuperar información de un servidor gopher, una aplicación primero debe obtener un localizador gopher. La aplicación, a continuación, debe tratar el localizador como un token opaco (es decir, la aplicación puede usar el localizador, pero no directamente manipular o compararlo). Normalmente, la aplicación utiliza el localizador para las llamadas a la [CGopherFileFind:: FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) función miembro para recuperar una parte específica de la información.

##  <a name="getattribute"></a>  CGopherConnection::GetAttribute

Llame a esta función miembro para recuperar información de atributos específicos acerca de un elemento del servidor gopher.

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>Parámetros

*refLocator*<br/>
Una referencia a un [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto.

*strRequestedAttributes*<br/>
Cadena delimitada por espacios que especifica los nombres de los atributos solicitados.

*strResult*<br/>
Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que recibe el tipo de localizador.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero. Si se produce un error en la llamada, la función de Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) puede llamarse para determinar la causa del error.

##  <a name="openfile"></a>  CGopherConnection:: OpenFile

Llame a esta función miembro para abrir un archivo en un servidor gopher.

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parámetros

*refLocator*<br/>
Una referencia a un [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objeto.

*dwFlags*<br/>
Cualquier combinación de marcas de INTERNET_FLAG_* . Consulte [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) para obtener más información sobre INTERNET_FLAG_\* marcas.

*pstrView*<br/>
Un puntero a una cadena de la vista de archivos. Si existen varias vistas del archivo en el servidor, este parámetro especifica qué vista de archivo que desea abrir. Si *pstrView* es NULL, se usa la vista predeterminada del archivo.

*dwContext*<br/>
Identificador de contexto para el archivo que se está abriendo. Consulte **comentarios** para obtener más información acerca de *dwContext*.

### <a name="return-value"></a>Valor devuelto

Un puntero a la [CGopherFile](../../mfc/reference/cgopherfile-class.md) objeto que se abrirá.

### <a name="remarks"></a>Comentarios

Invalidar el *dwContext* predeterminada para establecer el identificador de contexto en un valor de su elección. El identificador de contexto está asociado con esta operación específica de la `CGopherConnection` objeto creado por su [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto. El valor se devuelve al [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado de la operación con el que se identifica. Consulte el artículo [primeros pasos de Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

## <a name="see-also"></a>Vea también

[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFtpConnection (clase)](../../mfc/reference/cftpconnection-class.md)<br/>
[CHttpConnection (clase)](../../mfc/reference/chttpconnection-class.md)<br/>
[CInternetConnection (clase)](../../mfc/reference/cinternetconnection-class.md)<br/>
[CGopherLocator (clase)](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFile (clase)](../../mfc/reference/cgopherfile-class.md)<br/>
[CInternetSession (clase)](../../mfc/reference/cinternetsession-class.md)
