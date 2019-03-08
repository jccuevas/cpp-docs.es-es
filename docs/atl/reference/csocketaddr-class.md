---
title: CSocketAddr (clase)
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
ms.openlocfilehash: e94d92b11a7f200edb1815a0b384d0fc0428001f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280334"
---
# <a name="csocketaddr-class"></a>CSocketAddr (clase)

Esta clase proporciona métodos para convertir los nombres de host a direcciones de host, que admiten formatos de IPv4 e IPV6.

## <a name="syntax"></a>Sintaxis

```
class CSocketAddr
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CSocketAddr::CSocketAddr](#csocketaddr)|El constructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSocketAddr::FindAddr](#findaddr)|Llame a este método para convertir el nombre de host proporcionado en la dirección del host.|
|[CSocketAddr::FindINET4Addr](#findinet4addr)|Llame a este método para convertir el nombre de host de IPv4 en la dirección del host.|
|[CSocketAddr::FindINET6Addr](#findinet6addr)|Llame a este método para convertir el nombre de host de IPv6 en la dirección del host.|
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|Llame a este método para devolver un puntero a un elemento específico de la `addrinfo` lista.|
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|Llamar a este método para devolver un puntero a la `addrinfo` lista.|

## <a name="remarks"></a>Comentarios

Esta clase proporciona una versión IP independiente del enfoque para buscar las direcciones de red para su uso con Windows sockets funciones de la API y los contenedores de socket en las bibliotecas.

Los miembros de esta clase que se usan para buscar las direcciones de red use la función de la API Win32 [getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo). La versión ANSI o UNICODE de la función se denomina dependiendo de si se compila el código de ANSI o UNICODE.

Esta clase es compatible con ambas direcciones de red IPv4 andIPv6.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsocket.h

##  <a name="csocketaddr"></a>  CSocketAddr::CSocketAddr

El constructor.

```
CSocketAddr();
```

### <a name="remarks"></a>Comentarios

Crea un nuevo `CSocketAddr` objeto e inicializa la lista vinculada que contiene información de la respuesta sobre el host.

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
El nombre de host o dirección IP con puntos.

*szPortOrServiceName*<br/>
El número de puerto o nombre de servicio del host.

*nPortNo*<br/>
El número de puerto.

*flags*<br/>
0 o combinación de AI_PASSIVE, AI_CANONNAME o AI_NUMERICHOST.

*addr_family*<br/>
(Por ejemplo, PF_INET) de la familia de direcciones.

*sock_type*<br/>
Tipo de socket (por ejemplo, SOCK_STREAM).

*ai_proto*<br/>
Protocolo (por ejemplo, IPPROTO_IP o IPPROTO_IPV6).

### <a name="return-value"></a>Valor devuelto

Devuelve cero si la dirección se calcula correctamente. Devuelve un código de error de Socket de Windows distinto de cero en caso de error. Si es correcto, la dirección calculada se almacena en una lista vinculada que pueda hacer referencia mediante `CSocketAddr::GetAddrInfoList` y `CSocketAddr::GetAddrInfo`.

### <a name="remarks"></a>Comentarios

El parámetro de nombre de host puede estar en formato IPv4 o IPv6. Este método llama a la función de la API Win32 [getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) para realizar la conversión.

##  <a name="findinet4addr"></a>  CSocketAddr::FindINET4Addr

Llame a este método para convertir el nombre de host de IPv4 en la dirección del host.

```
int FindINET4Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parámetros

*szHost*<br/>
El nombre de host o dirección IP con puntos.

*nPortNo*<br/>
El número de puerto.

*flags*<br/>
0 o combinación de AI_PASSIVE, AI_CANONNAME o AI_NUMERICHOST.

*sock_type*<br/>
Tipo de socket (por ejemplo, SOCK_STREAM).

### <a name="return-value"></a>Valor devuelto

Devuelve cero si la dirección se calcula correctamente. Devuelve un código de error de Socket de Windows distinto de cero en caso de error. Si es correcto, la dirección calculada se almacena en una lista vinculada que pueda hacer referencia mediante `CSocketAddr::GetAddrInfoList` y `CSocketAddr::GetAddrInfo`.

### <a name="remarks"></a>Comentarios

Este método llama a la función de la API Win32 [getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) para realizar la conversión.

##  <a name="findinet6addr"></a>  CSocketAddr::FindINET6Addr

Llame a este método para convertir el nombre de host de IPv6 en la dirección del host.

```
int FindINET6Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Parámetros

*szHost*<br/>
El nombre de host o dirección IP con puntos.

*nPortNo*<br/>
El número de puerto.

*flags*<br/>
0 o combinación de AI_PASSIVE, AI_CANONNAME o AI_NUMERICHOST.

*sock_type*<br/>
Tipo de socket (por ejemplo, SOCK_STREAM).

### <a name="return-value"></a>Valor devuelto

Devuelve cero si la dirección se calcula correctamente. Devuelve un código de error de Socket de Windows distinto de cero en caso de error. Si es correcto, la dirección calculada se almacena en una lista vinculada que pueda hacer referencia mediante `CSocketAddr::GetAddrInfoList` y `CSocketAddr::GetAddrInfo`.

### <a name="remarks"></a>Comentarios

Este método llama a la función de la API Win32 [getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) para realizar la conversión.

##  <a name="getaddrinfo"></a>  CSocketAddr::GetAddrInfo

Llame a este método para devolver un puntero a un elemento específico de la `addrinfo` lista.

```
addrinfo* const GetAddrInfo(int nIndex = 0) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Una referencia a un elemento específico de la [addrinfo](/windows/desktop/api/ws2def/ns-ws2def-addrinfoa) lista.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la `addrinfo` estructura al que hace referencia *nIndex* en la lista vinculada que contiene información de la respuesta sobre el host.

##  <a name="getaddrinfolist"></a>  CSocketAddr::GetAddrInfoList

Llamar a este método para devolver un puntero a la `addrinfo` lista.

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a una lista vinculada de uno o varios `addrinfo` estructuras que contienen información de la respuesta sobre el host. Para obtener más información, consulte [addrinfo estructura](/windows/desktop/api/ws2def/ns-ws2def-addrinfoa).

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
