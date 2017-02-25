---
title: "SOCKADDR (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SOCKADDR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SOCKADDR (estructura)"
ms.assetid: df1ed66a-f4b8-43f8-8db8-8c2533d25f68
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# SOCKADDR (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura `SOCKADDR` se utiliza para almacenar una dirección de protocolo de Internet \(IP\) para un equipo que participa en una comunicación de Windows Sockets.  
  
## Sintaxis  
  
```  
  
      struct sockaddr {  
   unsigned short sa_family;  
   char sa_data[14];  
};  
```  
  
#### Parámetros  
 *sa\_family*  
 Familia de direcciones de socket.  
  
 *sa\_data*  
 Tamaño máximo de todas las estructuras de dirección de socket diferentes.  
  
## Comentarios  
 El kit de Microsoft TCP\/IP para desarrolladores de sockets solo admite los dominios de dirección de Internet.  Para rellenar realmente los valores de cada parte de una dirección, se utiliza la estructura de datos `SOCKADDR_IN`, que es específica de este formato de dirección.  Las estructuras de datos `SOCKADDR` y `SOCKADDR_IN` tienen el mismo tamaño.  Simplemente se realiza una conversión para alternar entre los dos tipos de estructura.  
  
## Requisitos  
 **Encabezado:** winsock2.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [SOCKADDR\_IN \(Estructura\)](../../mfc/reference/sockaddr-in-structure.md)   
 [CAsyncSocket::Create](../Topic/CAsyncSocket::Create.md)   
 [CSocket::Create](../Topic/CSocket::Create.md)