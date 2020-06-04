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
ms.openlocfilehash: 6649986f279e010a833b31157922cb4fd1ea8613
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372421"
---
# <a name="cinternetconnection-class"></a>CInternetConnection (clase)

Administra la conexión a un servidor de Internet.

## <a name="syntax"></a>Sintaxis

```
class CInternetConnection : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CInternetConnection::CInternetConnection](#cinternetconnection)|Construye un objeto `CInternetConnection`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CInternetConnection::GetContext](#getcontext)|Obtiene el identificador de contexto para este objeto de conexión.|
|[CInternetConnection::GetServerName](#getservername)|Obtiene el nombre del servidor asociado a la conexión.|
|[CInternetConnection::GetSession](#getsession)|Obtiene un puntero a la [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto asociado a la conexión.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CInternetConnection::operador HINTERNET](#operator_hinternet)|Un identificador de una sesión de Internet.|

## <a name="remarks"></a>Observaciones

Es la clase base para las clases MFC [CFtpConnection](../../mfc/reference/cftpconnection-class.md), [CHttpConnection](../../mfc/reference/chttpconnection-class.md)y [CGopherConnection](../../mfc/reference/cgopherconnection-class.md). Cada una de estas clases proporciona funcionalidad adicional para comunicarse con el servidor FTP, HTTP o gopher respectivo.

Para comunicarse directamente con un servidor de Internet, `CInternetConnection` debe tener un [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto y un objeto.

Para obtener más información sobre cómo funcionan las clases WinInet, consulte el artículo Programación de [Internet con WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CInternetConnection`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxinet.h

## <a name="cinternetconnectioncinternetconnection"></a><a name="cinternetconnection"></a>CInternetConnection::CInternetConnection

Se llama a esta `CInternetConnection` función miembro cuando se crea un objeto.

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
Puntero a una cadena que contiene el nombre del servidor.

*Nport*<br/>
El número que identifica el puerto de Internet para esta conexión.

*dwContext*<br/>
Identificador de contexto `CInternetConnection` para el objeto. Consulte **Comentarios** para obtener más información sobre *dwContext*.

### <a name="remarks"></a>Observaciones

Nunca `CInternetConnection` te llamas a ti mismo; en su lugar, llame a la [CInternetSession](../../mfc/reference/cinternetsession-class.md) función miembro para el tipo de conexión que desea establecer:

- [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)

- [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)

- [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)

MFC envía `CInternetConnection`el valor predeterminado de *dwContext* al objeto derivado del objeto [CInternetSession](../../mfc/reference/cinternetsession-class.md) que creó el objeto derivado **InternetConnection.** El valor predeterminado se establece en 1; sin embargo, puede asignar explícitamente un identificador de contexto específico en el [CInternetSession](../../mfc/reference/cinternetsession-class.md#cinternetsession) constructor para la conexión. El objeto y cualquier trabajo que realice se asociarán con ese identificador de contexto. El identificador de contexto se devuelve a [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) para proporcionar el estado en el objeto con el que se identifica. Consulte el artículo Primeros pasos de [Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

## <a name="cinternetconnectiongetcontext"></a><a name="getcontext"></a>CInternetConnection::GetContext

Llame a esta función miembro para obtener el identificador de contexto para esta sesión.

```
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Valor devuelto

El identificador de contexto asignado por la aplicación.

### <a name="remarks"></a>Observaciones

El identificador de contexto se especifica originalmente en `CInternetConnection` [CInternetSession](../../mfc/reference/cinternetsession-class.md) y se propaga a - y [CInternetFile](../../mfc/reference/cinternetfile-class.md)-clases derivadas, a menos que se especifique de forma diferente en la llamada a una función que abre la conexión. El identificador de contexto está asociado a cualquier operación del objeto especificado e identifica la información de estado de la operación devuelta por [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

Para obtener más `GetContext` información acerca de cómo funciona con otras clases WinInet para proporcionar la información de estado de usuario, consulte el artículo Primeros pasos de [Internet: WinInet](../../mfc/wininet-basics.md) para obtener más información sobre el identificador de contexto.

## <a name="cinternetconnectiongetservername"></a><a name="getservername"></a>CInternetConnection::GetServerName

Llame a esta función miembro para obtener el nombre del servidor asociado a esta conexión a Internet.

```
CString GetServerName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre del servidor con el que está trabajando este objeto de conexión.

## <a name="cinternetconnectiongetsession"></a><a name="getsession"></a>CInternetConnection::GetSession

Llame a esta función miembro `CInternetSession` para obtener un puntero al objeto que está asociado a esta conexión.

```
CInternetSession* GetSession() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a un [CInternetSession](../../mfc/reference/cinternetsession-class.md) objeto asociado a este objeto de conexión a Internet.

## <a name="cinternetconnectionoperator-hinternet"></a><a name="operator_hinternet"></a>CInternetConnection::operador HINTERNET

Utilice este operador para obtener el identificador de nivel de API para la sesión de Internet actual.

```
operator HINTERNET() const;
```

## <a name="see-also"></a>Consulte también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
