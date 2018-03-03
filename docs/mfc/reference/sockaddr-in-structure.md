---
title: SOCKADDR_IN (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SOCKADDR_IN
dev_langs:
- C++
helpviewer_keywords:
- SOCKADDR_IN structure [MFC]
ms.assetid: e8cd7c34-78bd-4e28-a990-eb3ca070b7a6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e5350e48570a564361328e7b666a1cbb976221a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="sockaddrin-structure"></a>SOCKADDR_IN (Estructura)
En la familia de direcciones de Internet, el `SOCKADDR_IN` estructura se usa Windows Sockets para especificar una dirección de extremo local o remoto que se va a conectar un socket.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct sockaddr_in{  
    short sin_family;  
    unsigned short sin_port;  
struct in_addr sin_addr;  
    char sin_zero[8];  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 *sin_family*  
 Familia de direcciones (debe ser **AF_INET**).  
  
 *sin_port*  
 Puerto de IP.  
  
 *sin_addr*  
 Dirección IP.  
  
 *Sin_Zero*  
 Relleno para igualar el tamaño como de la estructura `SOCKADDR`.  
  
## <a name="remarks"></a>Comentarios  
 Esta es la forma de la `SOCKADDR` estructura específicas de la familia de direcciones de Internet y se puede convertir en `SOCKADDR`.  
  
 El componente de dirección IP de esta estructura es de tipo **dir_in**. El **dir_in** estructura se define en el archivo de encabezado de Windows Sockets WINSOCK. H como sigue:  
  
```  
struct in_addr {
    union {
        struct {  
            unsigned char s_b1, s_b2, s_b3, s_b4;  
        } S_un_b;  
        struct {  
            unsigned short s_w1, s_w2;
        } S_un_w;
        unsigned long S_addr;
    } S_un;  
};  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winsock2.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [SOCKADDR (estructura)](../../mfc/reference/sockaddr-structure.md)
