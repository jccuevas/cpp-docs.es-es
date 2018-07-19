---
title: SOCKADDR_IN (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SOCKADDR_IN
dev_langs:
- C++
helpviewer_keywords:
- SOCKADDR_IN structure [MFC]
ms.assetid: e8cd7c34-78bd-4e28-a990-eb3ca070b7a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aeb9e61f94ddd5f41ff3de26728c1fbe155f809d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373643"
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
