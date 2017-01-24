---
title: "Windows Sockets: Puertos y direcciones de Socket | Microsoft Docs"
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
  - "direcciones [C++], socket"
  - "puertos [C++]"
  - "puertos [C++], definición"
  - "sockets [C++], direcciones"
  - "sockets [C++], puertos"
  - "Windows Sockets [C++], direcciones"
  - "Windows Sockets [C++], puertos"
ms.assetid: e050261a-9285-4f31-a1c5-6c8033af5b4a
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets: Puertos y direcciones de Socket
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica los términos “puerto” y “address” según se utiliza con Windows Sockets.  
  
##  <a name="_core_port"></a> Puerto  
 Un puerto identifica un proceso único para que el servicio puede ser proporcionado.  En el contexto actual, un puerto está asociado a una aplicación que admite el Windows Sockets.  La idea es identificar cada aplicación de Windows Sockets únicamente por lo que puede tener más de una ejecución de la aplicación de Windows Sockets en un equipo.  
  
 Determinados puertos están reservadas para los servicios comunes, como FTP.  Debe evitar usar esos puertos a menos que esté proporcionando esa clase de servicio.  Los detalles de la especificación de Windows Sockets estos puertos reservados.  El archivo WINSOCK.H también los enumera.  
  
 Para dejar el Windows Sockets DLL seleccionar un puerto utilizable para usted, pase 0 como valor de puerto.  MFC selecciona un valor de puerto mayor de 1.024 decimales.  Puede recuperar el valor del puerto que MFC seleccionado llamando a la función miembro de [CAsyncSocket::GetSockName](../Topic/CAsyncSocket::GetSockName.md) .  
  
##  <a name="_core_socket_address"></a> Dirección de socket  
 Cada objeto de socket se asocia a una dirección de \(IP\) de protocolo de Internet en la red.  Normalmente, la dirección es un nombre de equipo, como “ftp.microsoft.com”, o un número dotted, como “128.56.22.8”.  
  
 Cuando se intenta crear un socket, normalmente no es necesario especificar la propia dirección.  
  
> [!NOTE]
>  Es posible que el equipo tiene las tarjetas de red varias \(o la aplicación podría ejecutarse un día en este equipo\), cada uno de los cuales representa otra red.  Si es así puede ser necesario proporcionar una dirección para especificar que la tarjeta de red el socket utilizará.  Esto es seguramente un uso avanzado y un posible problema de portabilidad.  
  
 Para obtener más información, vea:  
  
-   [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Usar sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets: Cómo funcionan los sockets con archivos](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets: Sockets de secuencia](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sockets de datagrama](../mfc/windows-sockets-datagram-sockets.md)  
  
## Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)