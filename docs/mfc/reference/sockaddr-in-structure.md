---
title: "SOCKADDR_IN (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SOCKADDR_IN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SOCKADDR_IN (estructura)"
ms.assetid: e8cd7c34-78bd-4e28-a990-eb3ca070b7a6
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SOCKADDR_IN (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En la familia de direcciones de Internet, la estructura de `SOCKADDR_IN` utiliza Windows Sockets para especificar una dirección local o remota del extremo al conectar un socket.  
  
## Sintaxis  
  
```  
  
      struct sockaddr_in{  
   short sin_family;  
   unsigned short sin_port;  
   struct in_addr sin_addr;  
   char sin_zero[8];  
};  
```  
  
#### Parámetros  
 *sin\_family*  
 Familia de direcciones \(debe ser **AF\_INET**\).  
  
 *sin\_port*  
 Puerto IP.  
  
 *sin\_addr*  
 Dirección IP.  
  
 *sin\_zero*  
 Relleno para crear estructura del mismo tamaño que `SOCKADDR`.  
  
## Comentarios  
 Este es el formulario de la estructura concreta `SOCKADDR` de la familia de direcciones de Internet y se puede convertir en `SOCKADDR`.  
  
 El componente de la dirección IP de esta estructura es de tipo **IN\_ADDR**.  La estructura **IN\_ADDR** se define en el archivo de encabezado WINSOCK.H de Windows Sockets como sigue:  
  
 `struct   in_addr {`  
  
 `union   {`  
  
 `struct{`  
  
 `unsigned  char   s_b1,`  
  
 `s_b2,`  
  
 `s_b3,`  
  
 `s_b4;`  
  
 `}  S_un_b;`  
  
 `struct  {`  
  
 `unsigned  short  s_w1,`  
  
 `s_w2;`  
  
 `}  S_un_w;`  
  
 `unsigned long  S_addr;`  
  
 `} S_un;`  
  
 `};`  
  
## Requisitos  
 **Encabezado:** winsock2.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [SOCKADDR \(Estructura\)](../../mfc/reference/sockaddr-structure.md)