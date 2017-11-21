---
title: "Conceptos básicos de HTTP | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- HTTP [MFC], return codes
- return codes [MFC]
- HTTP requests [MFC], return codes
ms.assetid: 5b7421bf-42c8-4f3a-8566-8ff5957f58cc
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1fa71e0aa1dc73884ef9783824198912758592ff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="http-basics"></a>Conceptos básicos de HTTP
Al escribir una aplicación de internet, a menudo examinar y agregar a la información de encabezado HTTP. Códigos de retorno indican el éxito o fracaso del evento solicitado. Varios códigos de retorno comunes se enumeran en la tabla siguiente.  
  
|Código de retorno|Significado|  
|-----------------|-------------|  
|200|Después de la transmisión en la dirección URL que se encuentra,|  
|400|Solicitud ininteligible|  
|404|Solicitado no se encontró la dirección URL|  
|405|Servidor no admite el método solicitado|  
|500|Error desconocido del servidor|  
|503|Servicio no disponible|  
  
 Las respuestas HTTP se agrupan como se muestra en la tabla siguiente.  
  
|Agrupar|Significado|  
|-----------|-------------|  
|200-299|Correcto|  
|300-399|Información|  
|400-499|Error de solicitud|  
|500-599|Error del servidor|  
  
 El protocolo de transferencia de hipertexto (HTTP) es un protocolo de nivel de aplicación para los sistemas de información de hipermedia. Para obtener más información acerca de HTTP y cómo se comunican los servidores y exploradores Web, vea la especificación de protocolo de transferencia de hipertexto (HTTP):  
  
 [http://www.w3.org/pub/www/Protocols/](http://www.w3.org/pub/www/protocols/)  
  
## <a name="see-also"></a>Vea también  
 [Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)

