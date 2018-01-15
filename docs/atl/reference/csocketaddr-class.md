---
title: Clase CSocketAddr | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSocketAddr
- ATLSOCKET/ATL::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::FindAddr
- ATLSOCKET/ATL::CSocketAddr::FindINET4Addr
- ATLSOCKET/ATL::CSocketAddr::FindINET6Addr
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfo
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfoList
dev_langs: C++
helpviewer_keywords: CSocketAddr class
ms.assetid: 2fb2d8a7-899e-4a36-a342-cc9f4fcdd68c
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cadd771e6c3a9e7addb6893b4427183cfff293c9
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="csocketaddr-class"></a>Clase CSocketAddr
Esta clase proporciona métodos para convertir los nombres de host en direcciones de host, admiten formatos de IPv4 e IPV6.  
  
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
|[CSocketAddr::FindAddr](#findaddr)|Llamar a este método para convertir el nombre de host proporcionado en la dirección del host.|  
|[CSocketAddr::FindINET4Addr](#findinet4addr)|Llamar a este método para convertir el nombre de host de IPv4 en la dirección del host.|  
|[CSocketAddr::FindINET6Addr](#findinet6addr)|Llamar a este método para convertir el nombre de host IPv6 para la dirección del host.|  
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|Llamar a este método para devolver un puntero a un elemento específico de la **addrinfo** lista.|  
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|Llamar a este método para devolver un puntero a la **addrinfo** lista.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona una versión IP enfoque independiente para buscar direcciones de red para su uso con Windows sockets funciones de la API y contenedores de socket en bibliotecas.  
  
 Los miembros de esta clase que se utilizan para buscar direcciones de red utilizan la función de la API de Win32 [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520).  
  
 Esta clase es compatible con dos direcciones de red de IPv4 andIPv6.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsocket.h  
  
##  <a name="csocketaddr"></a>CSocketAddr::CSocketAddr  
 El constructor.  
  
```
CSocketAddr();
```  
  
### <a name="remarks"></a>Comentarios  
 Crea un nuevo `CSocketAddr` objeto e inicializa la lista vinculada que contiene información sobre las respuestas acerca del host.  
  
##  <a name="findaddr"></a>CSocketAddr::FindAddr  
 Llamar a este método para convertir el nombre de host proporcionado en la dirección del host.  
  
```
int FindAddr(
    const char *szHost,
    const char *szPortOrServiceName,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);

int FindAddr(
    const char *szHost,
    int nPortNo,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);
```  
  
### <a name="parameters"></a>Parámetros  
 `szHost`  
 El nombre de host o dirección IP con puntos.  
  
 *szPortOrServiceName*  
 El número de puerto o nombre del servicio en el host.  
  
 `nPortNo`  
 El número de puerto.  
  
 `flags`  
 0 o una combinación de AI_PASSIVE, AI_CANONNAME o AI_NUMERICHOST.  
  
 *addr_family*  
 Familia (por ejemplo, PF_INET) de direcciones.  
  
 `sock_type`  
 Tipo de socket (por ejemplo, SOCK_STREAM).  
  
 *ai_proto*  
 Protocolo (por ejemplo, IPPROTO_IP o IPPROTO_IPV6).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve cero si la dirección se calcula correctamente. Devuelve un código de error de Socket de Windows es distinto de cero en caso de error. Si tiene éxito, la dirección calculada se almacena en una lista vinculada a la que se puede hacer referencia mediante `CSocketAddr::GetAddrInfoList` y `CSocketAddr::GetAddrInfo`.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro de nombre de host puede estar en formato IPv4 o IPv6. Este método llama a la función API de Win32 [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520) para realizar la conversión.  
  
##  <a name="findinet4addr"></a>CSocketAddr::FindINET4Addr  
 Llamar a este método para convertir el nombre de host de IPv4 en la dirección del host.  
  
```
int FindINET4Addr(
    const char *szHost,
    int nPortNo,
    int flags,
    int sock_type,);
```  
  
### <a name="parameters"></a>Parámetros  
 `szHost`  
 El nombre de host o dirección IP con puntos.  
  
 `nPortNo`  
 El número de puerto.  
  
 `flags`  
 0 o una combinación de AI_PASSIVE, AI_CANONNAME o AI_NUMERICHOST.  
  
 `sock_type`  
 Tipo de socket (por ejemplo, SOCK_STREAM).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve cero si la dirección se calcula correctamente. Devuelve un código de error de Socket de Windows es distinto de cero en caso de error. Si tiene éxito, la dirección calculada se almacena en una lista vinculada a la que se puede hacer referencia mediante `CSocketAddr::GetAddrInfoList` y `CSocketAddr::GetAddrInfo`.  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a la función API de Win32 [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520) para realizar la conversión.  
  
##  <a name="findinet6addr"></a>CSocketAddr::FindINET6Addr  
 Llamar a este método para convertir el nombre de host IPv6 para la dirección del host.  
  
```
int FindINET6Addr(
    const char *szHost,
    int nPortNo,
    int flags,
    int sock_type,);
```  
  
### <a name="parameters"></a>Parámetros  
 `szHost`  
 El nombre de host o dirección IP con puntos.  
  
 `nPortNo`  
 El número de puerto.  
  
 `flags`  
 0 o una combinación de AI_PASSIVE, AI_CANONNAME o AI_NUMERICHOST.  
  
 `sock_type`  
 Tipo de socket (por ejemplo, SOCK_STREAM).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve cero si la dirección se calcula correctamente. Devuelve un código de error de Socket de Windows es distinto de cero en caso de error. Si tiene éxito, la dirección calculada se almacena en una lista vinculada a la que se puede hacer referencia mediante `CSocketAddr::GetAddrInfoList` y `CSocketAddr::GetAddrInfo`.  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a la función API de Win32 [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520) para realizar la conversión.  
  
##  <a name="getaddrinfo"></a>CSocketAddr::GetAddrInfo  
 Llamar a este método para devolver un puntero a un elemento específico de la **addrinfo** lista.  
  
```
addrinfo* const GetAddrInfoint nIndex = 0) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Una referencia a un elemento específico de la [addrinfo](http://msdn.microsoft.com/library/windows/desktop/ms737530) lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la **addrinfo** estructura al que hace referencia `nIndex` en la lista vinculada que contiene información sobre las respuestas acerca del host.  
  
##  <a name="getaddrinfolist"></a>CSocketAddr::GetAddrInfoList  
 Llamar a este método para devolver un puntero a la **addrinfo** lista.  
  
```
addrinfo* const GetAddrInfoList() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una lista vinculada de uno o más `addrinfo` las estructuras que contienen información sobre las respuestas acerca del host. Para obtener más información, consulte [addrinfo estructura](https://msdn.microsoft.com/library/windows/desktop/ms737530).
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
