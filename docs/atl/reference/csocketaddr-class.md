---
title: Clase CSocketAddr
ms.date: 10/22/2018
f1_keywords:
- CSocketAddr
- ATLSOCKET/ATL::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::FindAddr
- ATLSOCKET/ATL::CSocketAddr::FindINET4Addr
- ATLSOCKET/ATL::CSocketAddr::FindINET6Addr
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfo
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfoList
helpviewer_keywords:
- CSocketAddr class
ms.assetid: 2fb2d8a7-899e-4a36-a342-cc9f4fcdd68c
ms.openlocfilehash: 2a131323e64b1bf67f76ec92e7a3e4fcba899661
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496348"
---
# <a name="csocketaddr-class"></a>Clase CSocketAddr

Esta clase proporciona métodos para convertir los nombres de host en direcciones de host, que admiten los formatos de IPv4 e IPV6.

## <a name="syntax"></a>Sintaxis

```
class CSocketAddr
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSocketAddr::CSocketAddr](#csocketaddr)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSocketAddr::FindAddr](#findaddr)|Llame a este método para convertir el nombre de host proporcionado en la dirección del host.|
|[CSocketAddr::FindINET4Addr](#findinet4addr)|Llame a este método para convertir el nombre de host IPv4 en la dirección del host.|
|[CSocketAddr::FindINET6Addr](#findinet6addr)|Llame a este método para convertir el nombre de host IPv6 en la dirección del host.|
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|Llame a este método para devolver un puntero a un elemento específico de `addrinfo` la lista.|
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|Llame a este método para devolver un puntero a `addrinfo` la lista.|

## <a name="remarks"></a>Comentarios

Esta clase proporciona un enfoque independiente de la versión de IP para buscar direcciones de red para su uso con las funciones de la API de Windows Sockets y contenedores de sockets en las bibliotecas.

Los miembros de esta clase que se usan para buscar direcciones de red utilizan la función de la API de Win32 [función getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo). Se llama a la versión ANSI o Unicode de la función dependiendo de si el código se compila para ANSI o Unicode.

Esta clase admite ambas direcciones de red andIPv6 de IPv4.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsocket. h

##  <a name="csocketaddr"></a>  CSocketAddr::CSocketAddr

El constructor.

```
CSocketAddr();
```

### <a name="remarks"></a>Comentarios

Crea un nuevo `CSocketAddr` objeto e inicializa la lista vinculada que contiene la información de respuesta del host.

##  <a name="findaddr"></a>  CSocketAddr::FindAddr

Llame a este método para convertir el nombre de host proporcionado en la dirección del host.

```
int FindAddr(
    const TCHAR *szHost,
    const TCHAR *szPortOrServiceName,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);

int FindAddr(
    const TCHAR *szHost,
    int nPortNo,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);
```

### <a name="parameters"></a>Parámetros

*szHost*<br/>
El nombre de host o la dirección IP con puntos.

*szPortOrServiceName*<br/>
El número de puerto o el nombre del servicio en el host.

*nPortNo*<br/>
El número de puerto.

*flags*<br/>
0 o combinación de AI_PASSIVE, AI_CANONNAME o AI_NUMERICHOST.

*addr_family*<br/>
Familia de direcciones (por ejemplo, PF_INET).

*sock_type*<br/>
Tipo de socket (por ejemplo, SOCK_STREAM).

*ai_proto*<br/>
Protocolo (como IPPROTO_IP o IPPROTO_IPV6).

### <a name="return-value"></a>Valor devuelto

Devuelve cero si la dirección se calcula correctamente. Devuelve un código de error de Windows socket distinto de cero en caso de error. Si se realiza correctamente, la dirección calculada se almacena en una lista vinculada a la `CSocketAddr::GetAddrInfoList` que `CSocketAddr::GetAddrInfo`se puede hacer referencia mediante y.

### <a name="remarks"></a>Comentarios

El parámetro de nombre de host puede tener el formato IPv4 o IPv6. Este método llama a la función de la API de Win32 [función getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) para realizar la conversión.

##  <a name="findinet4addr"></a>  CSocketAddr::FindINET4Addr

Llame a este método para convertir el nombre de host IPv4 en la dirección del host.

```
int FindINET4Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parámetros

*szHost*<br/>
El nombre de host o la dirección IP con puntos.

*nPortNo*<br/>
El número de puerto.

*flags*<br/>
0 o combinación de AI_PASSIVE, AI_CANONNAME o AI_NUMERICHOST.

*sock_type*<br/>
Tipo de socket (por ejemplo, SOCK_STREAM).

### <a name="return-value"></a>Valor devuelto

Devuelve cero si la dirección se calcula correctamente. Devuelve un código de error de Windows socket distinto de cero en caso de error. Si se realiza correctamente, la dirección calculada se almacena en una lista vinculada a la `CSocketAddr::GetAddrInfoList` que `CSocketAddr::GetAddrInfo`se puede hacer referencia mediante y.

### <a name="remarks"></a>Comentarios

Este método llama a la función de la API de Win32 [función getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) para realizar la conversión.

##  <a name="findinet6addr"></a>  CSocketAddr::FindINET6Addr

Llame a este método para convertir el nombre de host IPv6 en la dirección del host.

```
int FindINET6Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parámetros

*szHost*<br/>
El nombre de host o la dirección IP con puntos.

*nPortNo*<br/>
El número de puerto.

*flags*<br/>
0 o combinación de AI_PASSIVE, AI_CANONNAME o AI_NUMERICHOST.

*sock_type*<br/>
Tipo de socket (por ejemplo, SOCK_STREAM).

### <a name="return-value"></a>Valor devuelto

Devuelve cero si la dirección se calcula correctamente. Devuelve un código de error de Windows socket distinto de cero en caso de error. Si se realiza correctamente, la dirección calculada se almacena en una lista vinculada a la `CSocketAddr::GetAddrInfoList` que `CSocketAddr::GetAddrInfo`se puede hacer referencia mediante y.

### <a name="remarks"></a>Comentarios

Este método llama a la función de la API de Win32 [función getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) para realizar la conversión.

##  <a name="getaddrinfo"></a>  CSocketAddr::GetAddrInfo

Llame a este método para devolver un puntero a un elemento específico de `addrinfo` la lista.

```
addrinfo* const GetAddrInfo(int nIndex = 0) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Referencia a un elemento específico de la lista [addrinfo](/windows/win32/api/ws2def/ns-ws2def-addrinfow) .

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la `addrinfo` estructura a la que hace referencia *NINDEX* en la lista vinculada que contiene la información de respuesta del host.

##  <a name="getaddrinfolist"></a>  CSocketAddr::GetAddrInfoList

Llame a este método para devolver un puntero a `addrinfo` la lista.

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a una lista vinculada de una o `addrinfo` más estructuras que contienen información de respuesta sobre el host. Para obtener más información, consulte [estructura addrinfo](/windows/win32/api/ws2def/ns-ws2def-addrinfow).

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
