---
title: 'Windows Sockets: Sockets de secuencia | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- stream sockets [MFC]
ms.assetid: 31faaa34-a995-493f-a30b-b8115293d619
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bc112bd3cfbf1194a2898afecb513edcbc456747
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-stream-sockets"></a>Windows Sockets: Sockets de secuencias
Este artículo describen los sockets de secuencias, uno de los dos tipos de Socket de Windows disponibles. (El otro tipo es el [socket de datagrama](../mfc/windows-sockets-datagram-sockets.md).)  
  
 Sockets de secuencias proporcionan un flujo de datos sin límite de registros: una secuencia de bytes que puede ser bidireccional (la aplicación es dúplex completo: pueden transmitir y recibir a través del socket). Pueden confiar en secuencias para entregar datos de orden y sin duplicar. ("Secuenciar" significa que los paquetes se entregan en el orden que se enviaron. "Sin duplicar" significa que un paquete determinado solo una vez.) Se garantiza la recepción de mensajes de secuencia y secuencias se adapta perfectamente para controlar grandes cantidades de datos.  
  
 La capa de transporte de red puede dividir o agrupar datos en paquetes de un tamaño razonable. La `CSocket` clase controlará el empaquetado y el desempaquetado.  
  
 Secuencias se basan en conexiones explícitas: socket A solicita una conexión al socket B; socket B acepta o rechaza la solicitud de conexión.  
  
 Una llamada telefónica proporciona una buena analogía de una secuencia. En circunstancias normales, la entidad de recepción escucha lo que dice en el orden en que lo dice, sin duplicación o pérdida. Sockets de secuencias son adecuados, por ejemplo, para las implementaciones, como el archivo de protocolo de transferencia (FTP), que facilita la transferencia ASCII o archivos binarios de tamaño arbitrario.  
  
 Sockets de secuencias son preferibles a los sockets de datagramas cuando deben garantiza que los datos llegan y al tamaño de los datos es grande. Para obtener más información acerca de los sockets de secuencia, vea la especificación de Windows Sockets. La especificación está disponible en el SDK de Windows.  
  
 Uso de sockets de secuencia puede ser superior a las aplicaciones diseñadas para usar un socket de datagrama de difusión a todos los sockets de recepción en la red porque  
  
-   El modelo de difusión está sujeto a problemas de saturación (o "tormenta") de red.  
  
-   El modelo de cliente-servidor adoptado posteriormente es más eficaz.  
  
-   El modelo de secuencias proporciona a transferencia de datos confiable, donde el modelo de datagrama no lo hace.  
  
-   El modelo final aprovecha las ventajas de la capacidad para comunicarse entre Unicode y ANSI de las aplicaciones de socket que ofrece la clase CArchive a la clase CSocket.  
  
    > [!NOTE]
    >  Si utiliza la clase `CSocket`, debe utilizar una secuencia. Se produce un error en una aserción de MFC si especifica el tipo de socket como **SOCK_DGRAM**.  
  
## <a name="see-also"></a>Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)   
 [Windows Sockets: Nociones](../mfc/windows-sockets-background.md)

