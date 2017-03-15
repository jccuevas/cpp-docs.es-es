---
title: Clase CSocketAddr | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSocketAddr
- ATL.CSocketAddr
- ATL::CSocketAddr
dev_langs:
- C++
helpviewer_keywords:
- CSocketAddr class
ms.assetid: 2fb2d8a7-899e-4a36-a342-cc9f4fcdd68c
caps.latest.revision: 19
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
ms.openlocfilehash: ee3f69874460d09e495a237985a98ace19134a01
ms.lasthandoff: 02/24/2017

---
# <a name="csocketaddr-class"></a>Clase CSocketAddr
Esta clase proporciona métodos para convertir los nombres de host en direcciones de host, admiten formatos de IPv4 e IPV6.  
  
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
|[CSocketAddr::FindAddr](#findaddr)|Llamar a este método para convertir el nombre de host proporcionado en la dirección del host.|  
|[CSocketAddr::FindINET4Addr](#findinet4addr)|Llamar a este método para convertir el nombre de host de IPv4 en la dirección del host.|  
|[CSocketAddr::FindINET6Addr](#findinet6addr)|Llamar a este método para convertir el nombre de host de IPv6 en la dirección del host.|  
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|Llamar a este método para devolver un puntero a un elemento específico de la **addrinfo** lista.|  
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|Llamar a este método para devolver un puntero a la **addrinfo** lista.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona una versión IP enfoque independiente para buscar direcciones de red para su uso con Windows sockets funciones de la API y los contenedores de socket en bibliotecas.  
  
 Los miembros de esta clase que se utilizan para buscar direcciones de red utilizan la función API de Win32 [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520).  
  
 Esta clase admite ambas direcciones de red IPv4 andIPv6.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsocket.h  
  
##  <a name="a-namecsocketaddra--csocketaddrcsocketaddr"></a><a name="csocketaddr"></a>CSocketAddr::CSocketAddr  
 El constructor.  
  
```
CSocketAddr();
```  
  
### <a name="remarks"></a>Comentarios  
 Crea un nuevo `CSocketAddr` objeto e inicializa la lista vinculada que contiene información de respuesta acerca del host.  
  
##  <a name="a-namefindaddra--csocketaddrfindaddr"></a><a name="findaddr"></a>CSocketAddr::FindAddr  
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
 El nombre de host o la dirección IP con puntos.  
  
 *szPortOrServiceName*  
 El número de puerto o nombre del servicio en el host.  
  
 `nPortNo`  
 El número de puerto.  
  
 `flags`  
 0 o combinación de AI_PASSIVE, AI_CANONNAME o AI_NUMERICHOST.  
  
 *addr_family*  
 (Por ejemplo, PF_INET) de la familia de direcciones.  
  
 `sock_type`  
 Tipo de socket (por ejemplo, SOCK_STREAM).  
  
 *ai_proto*  
 Protocolo (por ejemplo, IPPROTO_IP o IPPROTO_IPV6).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve cero si la dirección se calcula correctamente. Devuelve un código de error de Windows Sockets es distinto de cero en caso de error. Si tiene éxito, la dirección calculada se almacena en una lista vinculada que se puede hacer referencia mediante `CSocketAddr::GetAddrInfoList` y `CSocketAddr::GetAddrInfo`.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro de nombre de host puede estar en formato IPv4 o IPv6. Este método llama a la función API de Win32 [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520) para realizar la conversión.  
  
##  <a name="a-namefindinet4addra--csocketaddrfindinet4addr"></a><a name="findinet4addr"></a>CSocketAddr::FindINET4Addr  
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
 El nombre de host o la dirección IP con puntos.  
  
 `nPortNo`  
 El número de puerto.  
  
 `flags`  
 0 o combinación de AI_PASSIVE, AI_CANONNAME o AI_NUMERICHOST.  
  
 `sock_type`  
 Tipo de socket (por ejemplo, SOCK_STREAM).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve cero si la dirección se calcula correctamente. Devuelve un código de error de Windows Sockets es distinto de cero en caso de error. Si tiene éxito, la dirección calculada se almacena en una lista vinculada que se puede hacer referencia mediante `CSocketAddr::GetAddrInfoList` y `CSocketAddr::GetAddrInfo`.  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a la función API de Win32 [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520) para realizar la conversión.  
  
##  <a name="a-namefindinet6addra--csocketaddrfindinet6addr"></a><a name="findinet6addr"></a>CSocketAddr::FindINET6Addr  
 Llamar a este método para convertir el nombre de host de IPv6 en la dirección del host.  
  
```
int FindINET6Addr(
    const char *szHost,
    int nPortNo,
    int flags,
    int sock_type,);
```  
  
### <a name="parameters"></a>Parámetros  
 `szHost`  
 El nombre de host o la dirección IP con puntos.  
  
 `nPortNo`  
 El número de puerto.  
  
 `flags`  
 0 o combinación de AI_PASSIVE, AI_CANONNAME o AI_NUMERICHOST.  
  
 `sock_type`  
 Tipo de socket (por ejemplo, SOCK_STREAM).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve cero si la dirección se calcula correctamente. Devuelve un código de error de Windows Sockets es distinto de cero en caso de error. Si tiene éxito, la dirección calculada se almacena en una lista vinculada que se puede hacer referencia mediante `CSocketAddr::GetAddrInfoList` y `CSocketAddr::GetAddrInfo`.  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a la función API de Win32 [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520) para realizar la conversión.  
  
##  <a name="a-namegetaddrinfoa--csocketaddrgetaddrinfo"></a><a name="getaddrinfo"></a>CSocketAddr::GetAddrInfo  
 Llamar a este método para devolver un puntero a un elemento específico de la **addrinfo** lista.  
  
```
addrinfo* const GetAddrInfoint nIndex = 0) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Una referencia a un elemento específico de la [addrinfo](http://msdn.microsoft.com/library/windows/desktop/ms737530) lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la **addrinfo** estructura hace referencia a `nIndex` en la lista vinculada que contiene información de respuesta acerca del host.  
  
##  <a name="a-namegetaddrinfolista--csocketaddrgetaddrinfolist"></a><a name="getaddrinfolist"></a>CSocketAddr::GetAddrInfoList  
 Llamar a este método para devolver un puntero a la **addrinfo** lista.  
  
```
addrinfo* const GetAddrInfoList() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una lista vinculada de uno o más `addrinfo` las estructuras que contienen información de respuesta acerca del host. Para obtener más información acerca de la `addrinfo` estructura, vea el artículo "addrinfo" en la [MSDN Library](http://go.microsoft.com/fwlink/linkid=556)  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)

