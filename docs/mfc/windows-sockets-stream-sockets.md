---
title: "Windows Sockets: Sockets de secuencias | Microsoft Docs"
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
  - "sockets [C++], sockets de secuencia"
  - "sockets de secuencia [C++]"
  - "Windows Sockets [C++], sockets de secuencia"
ms.assetid: 31faaa34-a995-493f-a30b-b8115293d619
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Windows Sockets: Sockets de secuencias
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe los sockets de secuencia, uno de los dos tipos de socket de Windows disponibles. \(El otro tipo es [socket de datagrama](../mfc/windows-sockets-datagram-sockets.md).\)  
  
 Los sockets de secuencia preven un flujo de datos sin límites de registro: una secuencia de bytes que pueden ser bidireccionales \(la aplicación está llena \- dúplex: puede transmitir y recibir a través de socket\).  Las secuencias se pueden confirmar sobre para entregar datos ordenados, unduplicated. \(“Secuenciado” significa que los paquetes se entregarán en el orden enviado. “Unduplicated” significa que obtiene un paquete determinado solo una vez.\) La recepción de los mensajes de secuencia se garantiza, y secuencias son apropiadas a administrar grandes cantidades de datos.  
  
 El nivel de transporte de red puede dividir o agrupar datos en los paquetes de tamaño razonable.  La clase de `CSocket` administrará el empaquetado y el desempaque automáticamente.  
  
 Las secuencias se basan en conexiones explícitas: el socket A solicita una conexión a b de socket; b de socket acepta o rechaza la solicitud de conexión.  
  
 Una llamada telefónica proporciona una buena analogía para una secuencia.  En circunstancias normales, la parte receptora oye lo que se indica en el orden que se indica, sin la duplicación o la pérdida.  Los sockets de secuencia son adecuados, por ejemplo, para las implementaciones como el Protocolo de transferencia de archivos \(FTP\), que facilita transferir ASCII o archivos binarios de tamaño arbitrario.  
  
 Los sockets de secuencia son preferibles a sockets de datagrama cuando los datos se deben garantizar para proteger y cuando el tamaño de datos es grande.  Para obtener más información sobre los sockets de secuencia, vea la especificación de Windows Sockets.  La especificación de está disponible en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
 Mediante sockets de secuencia puede ser superior a las aplicaciones diseñadas para utilizar un socket de datagrama para propagar todos los sockets receptora en red porque  
  
-   El modelo de difusión está sujeto a problemas de la inundación de red \(o “tormenta”\).  
  
-   El modelo cliente\-servidor adoptado posteriormente es más eficaz.  
  
-   La transferencia de datos confiable de fuentes del modelo de la secuencia, donde no hace el modelo de datagrama.  
  
-   El modelo final aprovecha la capacidad de comunicarse entre Unicode y aplicaciones de socket ANSI que la clase CArchive presta a la clase CSocket.  
  
    > [!NOTE]
    >  Si utiliza la clase `CSocket`, debe utilizar una secuencia.  Una aserción de MFC produce un error si especifica el socket de la **SOCK\_DGRAM**.  
  
## Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)   
 [Windows Sockets: Nociones](../mfc/windows-sockets-background.md)