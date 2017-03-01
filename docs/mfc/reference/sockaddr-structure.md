---
title: SOCKADDR (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SOCKADDR
dev_langs:
- C++
helpviewer_keywords:
- SOCKADDR structure
ms.assetid: df1ed66a-f4b8-43f8-8db8-8c2533d25f68
caps.latest.revision: 12
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 28984fcc5614a5f901a01ffdeff4ea5f360f63fc
ms.lasthandoff: 02/24/2017

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


