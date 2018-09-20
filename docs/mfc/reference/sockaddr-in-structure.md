---
title: SOCKADDR_IN (estructura) | Microsoft Docs
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
ms.openlocfilehash: 207f437c4af4d8eee41bb625490534416e376dca
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377466"
---
# <a name="sockaddrin-structure"></a>SOCKADDR_IN (Estructura)

En la familia de direcciones de Internet, el `SOCKADDR_IN` estructura está usando Windows Sockets para especificar una dirección de punto de conexión local o remoto que se va a conectar un socket.

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

*sin_family*<br/>
Familia de direcciones (debe ser AF_INET).

*sin_port*<br/>
Puerto IP.

*sin_addr*<br/>
Dirección IP.

*Sin_Zero*<br/>
Relleno para crear la estructura del mismo tamaño que `SOCKADDR`.

## <a name="remarks"></a>Comentarios

Este es el formulario de la `SOCKADDR` estructura concreta para la familia de direcciones de Internet y se puede convertir en `SOCKADDR`.

El componente de la dirección IP de esta estructura es de tipo `IN_ADDR`. El `IN_ADDR` estructura se define en el archivo de encabezado de Windows Sockets WINSOCK. H como sigue:

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

[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[SOCKADDR (estructura)](../../mfc/reference/sockaddr-structure.md)
