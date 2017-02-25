---
title: "LINGER (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LINGER"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LINGER (estructura)"
ms.assetid: 1fb1c5bf-a64e-4a6c-89d6-1734e4fdbb1b
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# LINGER (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `LINGER` se utiliza para manipular las opciones de **SO\_LINGER** y de **SO\_DONTLINGER** de `CAsyncSocket::GetSockOpt`.  
  
## Sintaxis  
  
```  
  
      struct linger {  
   u_short l_onoff;            // option on/off  
   u_short l_linger;           // linger time  
};  
```  
  
## Comentarios  
 Establecer la opción de **SO\_DONTLINGER** evita el bloqueo en la función **cerrar** miembro mientras espera los datos no enviars que se envían.  Establecer esta opción equivale a establecer **SO\_LINGER** con **l\_onoff** establecido en 0.  
  
## Requisitos  
 **Encabezado:** winsock2.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CAsyncSocket::GetSockOpt](../Topic/CAsyncSocket::GetSockOpt.md)   
 [CAsyncSocket::SetSockOpt](../Topic/CAsyncSocket::SetSockOpt.md)