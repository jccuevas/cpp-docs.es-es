---
title: CInternetConnection (clase)
ms.date: 11/04/2016
f1_keywords:
- CInternetConnection
- AFXINET/CInternetConnection
- AFXINET/CInternetConnection::CInternetConnection
- AFXINET/CInternetConnection::GetContext
- AFXINET/CInternetConnection::GetServerName
- AFXINET/CInternetConnection::GetSession
helpviewer_keywords:
- CInternetConnection [MFC], CInternetConnection
- CInternetConnection [MFC], GetContext
- CInternetConnection [MFC], GetServerName
- CInternetConnection [MFC], GetSession
ms.assetid: 62a5d1c3-8471-4e36-a064-48831829b2a7
ms.openlocfilehash: 9f17c3ade53ec45ddde654e83c77fe1d817d8495
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275355"
---
# <a name="cinternetconnection-class"></a>CInternetConnection (clase)

Administra la conexión a un servidor de Internet.

## <a name="syntax"></a>Sintaxis

```
class CInternetConnection : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CInternetConnection::CInternetConnection](#cinternetconnection)|Construye un objeto `CInternetConnection`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CInternetConnection::GetContext](#getcontext)|Obtiene el identificador de contexto para este objeto de conexión.|
|[CInternetConnection::GetServerName](#getservername)|Obtiene el nombre del servidor asociado con la conexión.|
|[CInternetConnection::GetSession](#getsession)|Obtiene un puntero a la [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto asociado con la conexión.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CInternetConnection::operator HINTERNET](#operator_hinternet)|Identificador de sesión de Internet.|

## <a name="remarks"></a>Comentarios

Es la clase base para clases MFC [CFtpConnection](../../mfc/reference/cftpconnection-class.md), [CHttpConnection](../../mfc/reference/chttpconnection-class.md), y [CGopherConnection](../../mfc/reference/cgopherconnection-class.md). Cada una de estas clases proporciona funcionalidad adicional para la comunicación con el servidor FTP, HTTP o gopher respectivo.

Para comunicarse directamente con un servidor de Internet, debe tener un [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto y un `CInternetConnection` objeto.

Para obtener más información sobre cómo el WinInet clases de trabajo, consulte el artículo [Internet programar con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CInternetConnection`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

##  <a name="cinternetconnection"></a>  CInternetConnection::CInternetConnection

Esta función miembro se llama cuando un `CInternetConnection` se crea el objeto.

```
CInternetConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parámetros

*pSession*<br/>
Un puntero a un [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto.

*pstrServer*<br/>
Un puntero a una cadena que contiene el nombre del servidor.

*nPort*<br/>
El número que identifica el puerto de Internet para esta conexión.

*dwContext*<br/>
El identificador de contexto para el `CInternetConnection` objeto. Consulte **comentarios** para obtener más información acerca de *dwContext*.

### <a name="remarks"></a>Comentarios

Nunca llaman a `CInternetConnection` usted mismo; en su lugar, llame a la [CInternetSession](../../mfc/reference/cinternetsession-class.md) función miembro para el tipo de conexión que desea establecer:

- [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)

- [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)

- [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)

El valor predeterminado de *dwContext* se envía por MFC para la `CInternetConnection`-objeto derivado de la [CInternetSession](../../mfc/reference/cinternetsession-class.md) de objeto que creó el **InternetConnection**- objeto derivado. El valor predeterminado se establece en 1; Sin embargo, puede asignar explícitamente un identificador de contexto específico en el [CInternetSession](../../mfc/reference/cinternetsession-class.md#cinternetsession) constructor para la conexión. El objeto y cualquier trabajo que se asociarán con ese identificador de contexto. El identificador de contexto se devuelve al [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Consulte el artículo [Internet primeros pasos: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

##  <a name="getcontext"></a>  CInternetConnection::GetContext

Llame a esta función miembro para obtener el identificador de contexto para esta sesión.

```
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Valor devuelto

El identificador de contexto asignado por aplicación.

### <a name="remarks"></a>Comentarios

El identificador de contexto se especificó originalmente en [CInternetSession](../../mfc/reference/cinternetsession-class.md) y se propaga a `CInternetConnection`- y [CInternetFile](../../mfc/reference/cinternetfile-class.md)-las clases derivadas, a menos que se especifican en la llamada a una función que se abre de forma diferente la conexión. El identificador de contexto está asociado a cualquier operación del objeto especificado e identifica información de estado de la operación devuelta por [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

Para obtener más información acerca de cómo `GetContext` funciona con otras clases WinInet para proporcionar la información de estado de usuario, consulte el artículo [Internet primeros pasos: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

##  <a name="getservername"></a>  CInternetConnection::GetServerName

Llame a esta función miembro para obtener el nombre del servidor asociado con esta conexión a Internet.

```
CString GetServerName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre del servidor de este objeto de conexión está trabajando con.

##  <a name="getsession"></a>  CInternetConnection::GetSession

Llame a esta función miembro para obtener un puntero a la `CInternetSession` objeto asociado a esta conexión.

```
CInternetSession* GetSession() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto asociado a este objeto de conexión de Internet.

##  <a name="operator_hinternet"></a>  CInternetConnection::operator HINTERNET

Utilice este operador para obtener el identificador de nivel de API para la sesión actual de Internet.

```
operator HINTERNET() const;
```

## <a name="see-also"></a>Vea también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
