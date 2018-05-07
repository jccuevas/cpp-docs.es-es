---
title: SOCKADDR (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SOCKADDR
dev_langs:
- C++
helpviewer_keywords:
- SOCKADDR structure [MFC]
ms.assetid: df1ed66a-f4b8-43f8-8db8-8c2533d25f68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f468a0a68dcfedab3b92deea492b48f7876c1610
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="sockaddr-structure"></a>SOCKADDR (Estructura)
La estructura `SOCKADDR` se utiliza para almacenar una dirección de protocolo de Internet (IP) para un equipo que participa en una comunicación de Windows Sockets.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct sockaddr {  
    unsigned short sa_family;  
    char sa_data[14];  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 *sa_family*  
 Familia de direcciones de socket.  
  
 *sa_data*  
 Tamaño máximo de todas las estructuras de dirección de socket diferentes.  
  
## <a name="remarks"></a>Comentarios  
 El kit de Microsoft TCP/IP para desarrolladores de sockets solo admite los dominios de dirección de Internet. Para rellenar realmente los valores de cada parte de una dirección, se utiliza la estructura de datos `SOCKADDR_IN`, que es específica de este formato de dirección. Las estructuras de datos `SOCKADDR` y `SOCKADDR_IN` tienen el mismo tamaño. Simplemente se realiza una conversión para alternar entre los dos tipos de estructura.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winsock2.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [SOCKADDR_IN (estructura)](../../mfc/reference/sockaddr-in-structure.md)   
 [CAsyncSocket::Create](../../mfc/reference/casyncsocket-class.md#create)   
 [CSocket::Create](../../mfc/reference/csocket-class.md#create)

