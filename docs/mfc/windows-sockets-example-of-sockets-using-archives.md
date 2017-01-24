---
title: "Windows Sockets: Ejemplo de Sockets que usan archivos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ejemplos [MFC], Windows Sockets"
  - "sockets [C++], que contengan archivos"
  - "Windows Sockets [C++], que contengan archivos"
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets: Ejemplo de Sockets que usan archivos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este artículo muestra un ejemplo de la clase mediante [CSocket](../mfc/reference/csocket-class.md).  El ejemplo emplea los objetos de `CArchive` para serializar datos mediante un socket.  Observe que no es serialización de documentos a o desde un archivo.  
  
 El ejemplo siguiente se muestra cómo utilizar el archivo para enviar y recibir datos a través de los objetos de `CSocket` .  Diseñar el ejemplo para dos instancias de intercambiar los datos de la aplicación \(en el mismo equipo o en equipos diferentes en la red\).  Una instancia envía los datos, que la otra instancia recibe y confirma.  Cualquier aplicación puede iniciar un intercambio, y cualquiera puede actuar como un servidor o como cliente a otra aplicación.  La siguiente función se define en la clase de vista de la aplicación:  
  
 [!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/CPP/windows-sockets-example-of-sockets-using-archives_1.cpp)]  
  
 Lo más importante sobre este ejemplo es que sus paralelos de estructura que MFC `Serialize` funcione.  La función miembro de **PacketSerialize** consiste en una instrucción de **if** con una cláusula de **else** .  La función recibe dos referencias de [CArchive](../mfc/reference/carchive-class.md) como parámetros: `arData` y `arAck`.  Si el objeto del archivo de `arData` se establece para almacenar \(transporte\), la bifurcación de **if** se ejecuta; si no, si `arData` se establece para la carga \(receptora\) la función toma la bifurcación de **else** .  Para obtener más información sobre la serialización en MFC, vea [Serialización](../mfc/how-to-make-a-type-safe-collection.md).  
  
> [!NOTE]
>  El objeto del archivo de `arAck` se asume que el cambio de `arData`.  Si `arData` es para enviar, `arAck` recibe, y el inverso es true.  
  
 Para enviar, bucles de la función de ejemplo para un número especificado de veces, generar cada vez algunos datos aleatorios demostración.  La aplicación obtendría datos reales de algún origen, como un archivo.  Se utiliza el operador de inserción del archivo de `arData` \(**\<\<**\) para enviar una secuencia de tres partes consecutivos de datos:  
  
-   Un “encabezado” que especifica la naturaleza de los datos \(en este caso, el valor de la variable de `bValue` y cuántos copias se enviarán\).  
  
     Ambos elementos se generan de forma aleatoria para este ejemplo.  
  
-   El número especificado de copias de los datos.  
  
     El bucle interno de **para** envía `bValue` el número especificado de veces.  
  
-   Una cadena denominada `strText` que el receptor muestra al usuario.  
  
 Para recibir, la función funciona de forma similar, pero utiliza el operador de extracción de archivo \(**\>\>**\) para recopilar datos de archivo.  La aplicación receptora comprueba los datos que recibe, muestra el mensaje “recibido” end, y después devuelven a un mensaje que indica “Sent” para que la aplicación de envío muestra.  
  
 En este las comunicaciones de, la palabra “recibida”, el mensaje enviado en la variable de `strText` , son para la presentación en el otro extremo de la comunicación, por lo que especifica el usuario que recibe que algunos paquetes de datos se han recibido.  El receptor responde con una cadena similar que indica “Sent”, para la presentación en la pantalla del remitente original.  La recepción de ambas cadenas indica que la comunicación correcta ha producido.  
  
> [!CAUTION]
>  Si está escribiendo un programa cliente de MFC para comunicarse con los servidores establecidos \(de no MFC\), no envíe los objetos de C\+\+ a través del archivo.  A menos que el servidor es una aplicación MFC que entienda las clases de objetos desee enviar, no podrá recibir y deserializar objetos.  Un ejemplo en el caso [Windows Sockets: El orden de byte](../mfc/windows-sockets-byte-ordering.md) muestra una comunicación de este tipo.  
  
 Para obtener más información, vea la especificación de Windows Sockets: **htonl**, **htons**, **ntohl**, **ntohs**.  Además, para obtener más información, vea:  
  
-   [Windows Sockets: Derivar clases de socket](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows Sockets: Cómo funcionan los sockets con archivos](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets: En segundo plano](../mfc/windows-sockets-background.md)  
  
## Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)   
 [CArchive::IsStoring](../Topic/CArchive::IsStoring.md)   
 [CArchive::operator \<\<](../Topic/CArchive::operator%20%3C%3C.md)   
 [CArchive::operator \>\>](../Topic/CArchive::operator%20%3E%3E.md)   
 [CArchive::Flush](../Topic/CArchive::Flush.md)   
 [CObject::Serialize](../Topic/CObject::Serialize.md)