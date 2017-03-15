---
title: "Conceptos b&#225;sicos de HTTP | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "solicitudes HTTP, códigos devueltos"
  - "HTTP, códigos devueltos"
  - "códigos devueltos"
ms.assetid: 5b7421bf-42c8-4f3a-8566-8ff5957f58cc
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Conceptos b&#225;sicos de HTTP
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al escribir una aplicación de Internet, examine y agrega a la información de encabezado HTTP.  Los códigos devueltos indican el éxito o error de evento solicitado.  Varios códigos devueltos más comunes se enumeran en la tabla siguiente.  
  
|Código de retorno|Significado|  
|-----------------------|-----------------|  
|200|La dirección URL adaptada, transmisión sigue|  
|400|Solicitud incomprensible|  
|404|Dirección URL solicitada no encontrada|  
|405|El Servidor no admite método solicitado|  
|500|Error de servidor desconocido|  
|503|Servicio no disponible|  
  
 Las respuestas HTTP se agrupan como se muestra en la tabla siguiente.  
  
|Group|Significado|  
|-----------|-----------------|  
|200–299|Correcto|  
|300–399|Información|  
|400–499|Error de la solicitud|  
|500–599|Error de servidor|  
  
 El protocolo HTTP \(Hypertext Transfer Protocol\) es un protocolo en la aplicación para los sistemas de información de la hipermedia.  Para obtener más información sobre HTTP, y cómo los exploradores web y los servidores comunicación, vea la especificación de Protocolo de transferencia de hipertexto \(HTTP\):  
  
 [http:\/\/www.w3.org\/pub\/WWW\/Protocols\/](http://www.w3.org/pub/WWW/Protocols/)  
  
## Vea también  
 [Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)