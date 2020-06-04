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
ms.openlocfilehash: 66d33d62212389a2b0f318250c1c16a99167c6eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330681"
---
# <a name="csocketaddr-class"></a>Clase CSocketAddr

Esta clase proporciona métodos para convertir nombres de host en direcciones de host, lo que admite los formatos IPv4 e IPV6.

## <a name="syntax"></a>Sintaxis

```
class CSocketAddr
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSocketAddr::CSocketAddr](#csocketaddr)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSocketAddr::FindAddr](#findaddr)|Llame a este método para convertir el nombre de host proporcionado a la dirección de host.|
|[CSocketAddr::FindINET4Addr](#findinet4addr)|Llame a este método para convertir el nombre de host IPv4 en la dirección de host.|
|[CSocketAddr::FindINET6Addr](#findinet6addr)|Llame a este método para convertir el nombre de host IPv6 a la dirección de host.|
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|Llame a este método para devolver un `addrinfo` puntero a un elemento específico de la lista.|
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|Llame a este método para `addrinfo` devolver un puntero a la lista.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona un enfoque independiente de la versión IP para buscar direcciones de red para su uso con funciones de API de sockets de Windows y contenedores de socket en bibliotecas.

Los miembros de esta clase que se utilizan para buscar direcciones de red utilizan la función de API de Win32 [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo). Se llama a la versión ANSI o UNICODE de la función en función de si el código se compila para ANSI o UNICODE.

Esta clase admite direcciones de red IPv4 e IPv6.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsocket.h

## <a name="csocketaddrcsocketaddr"></a><a name="csocketaddr"></a>CSocketAddr::CSocketAddr

El constructor.

```
CSocketAddr();
```

### <a name="remarks"></a>Observaciones

Crea un `CSocketAddr` nuevo objeto e inicializa la lista vinculada que contiene información de respuesta sobre el host.

## <a name="csocketaddrfindaddr"></a><a name="findaddr"></a>CSocketAddr::FindAddr

Llame a este método para convertir el nombre de host proporcionado a la dirección de host.

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
El nombre de host o la dirección IP punteada.

*szPortOrServiceName*<br/>
El número de puerto o el nombre del servicio en el host.

*nPortNo*<br/>
Número del puerto.

*Banderas*<br/>
0 o combinación de AI_PASSIVE, AI_CANONNAME o AI_NUMERICHOST.

*addr_family*<br/>
Familia de direcciones (como PF_INET).

*sock_type*<br/>
Tipo de socket (por ejemplo, SOCK_STREAM).

*ai_proto*<br/>
Protocolo (como IPPROTO_IP o IPPROTO_IPV6).

### <a name="return-value"></a>Valor devuelto

Devuelve cero si la dirección se calcula correctamente. Devuelve un código de error de Windows Socket distinto de cero en caso de error. Si se realiza correctamente, la dirección calculada se almacena `CSocketAddr::GetAddrInfoList` `CSocketAddr::GetAddrInfo`en una lista vinculada a la que se puede hacer referencia mediante y .

### <a name="remarks"></a>Observaciones

El parámetro de nombre de host puede estar en formato IPv4 o IPv6. Este método llama a la función [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) de la API de Win32 para realizar la conversión.

## <a name="csocketaddrfindinet4addr"></a><a name="findinet4addr"></a>CSocketAddr::FindINET4Addr

Llame a este método para convertir el nombre de host IPv4 en la dirección de host.

```
int FindINET4Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parámetros

*szHost*<br/>
El nombre de host o la dirección IP punteada.

*nPortNo*<br/>
Número del puerto.

*Banderas*<br/>
0 o combinación de AI_PASSIVE, AI_CANONNAME o AI_NUMERICHOST.

*sock_type*<br/>
Tipo de socket (por ejemplo, SOCK_STREAM).

### <a name="return-value"></a>Valor devuelto

Devuelve cero si la dirección se calcula correctamente. Devuelve un código de error de Windows Socket distinto de cero en caso de error. Si se realiza correctamente, la dirección calculada se almacena `CSocketAddr::GetAddrInfoList` `CSocketAddr::GetAddrInfo`en una lista vinculada a la que se puede hacer referencia mediante y .

### <a name="remarks"></a>Observaciones

Este método llama a la función [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) de la API de Win32 para realizar la conversión.

## <a name="csocketaddrfindinet6addr"></a><a name="findinet6addr"></a>CSocketAddr::FindINET6Addr

Llame a este método para convertir el nombre de host IPv6 a la dirección de host.

```
int FindINET6Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parámetros

*szHost*<br/>
El nombre de host o la dirección IP punteada.

*nPortNo*<br/>
Número del puerto.

*Banderas*<br/>
0 o combinación de AI_PASSIVE, AI_CANONNAME o AI_NUMERICHOST.

*sock_type*<br/>
Tipo de socket (por ejemplo, SOCK_STREAM).

### <a name="return-value"></a>Valor devuelto

Devuelve cero si la dirección se calcula correctamente. Devuelve un código de error de Windows Socket distinto de cero en caso de error. Si se realiza correctamente, la dirección calculada se almacena `CSocketAddr::GetAddrInfoList` `CSocketAddr::GetAddrInfo`en una lista vinculada a la que se puede hacer referencia mediante y .

### <a name="remarks"></a>Observaciones

Este método llama a la función [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) de la API de Win32 para realizar la conversión.

## <a name="csocketaddrgetaddrinfo"></a><a name="getaddrinfo"></a>CSocketAddr::GetAddrInfo

Llame a este método para devolver un `addrinfo` puntero a un elemento específico de la lista.

```
addrinfo* const GetAddrInfo(int nIndex = 0) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Una referencia a un elemento específico de la lista [addrinfo.](/windows/win32/api/ws2def/ns-ws2def-addrinfow)

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero `addrinfo` a la estructura a la que hace referencia *nIndex* en la lista vinculada que contiene información de respuesta sobre el host.

## <a name="csocketaddrgetaddrinfolist"></a><a name="getaddrinfolist"></a>CSocketAddr::GetAddrInfoList

Llame a este método para `addrinfo` devolver un puntero a la lista.

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a una lista vinculada `addrinfo` de una o más estructuras que contienen información de respuesta sobre el host. Para obtener más información, consulte [estructura addrinfo](/windows/win32/api/ws2def/ns-ws2def-addrinfow).

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
