---
title: 'Windows Sockets: Puertos y direcciones de Socket | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ports [MFC], definition
- Windows Sockets [MFC], ports
- Windows Sockets [MFC], addresses
- ports [MFC]
- addresses [MFC], socket
- sockets [MFC], addresses
- sockets [MFC], ports
ms.assetid: e050261a-9285-4f31-a1c5-6c8033af5b4a
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0c7b2e15761815b75ba8001ad4eb5a5c276f5056
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows Sockets: Puertos y direcciones de Socket
Este artículo explica los términos "puerto" y "dirección" como utilizada con Windows Sockets.  
  
##  <a name="_core_port"></a>Puerto  
 Un puerto identifica un proceso único para el que se puede proporcionar un servicio. En este contexto, un puerto está asociado con una aplicación que admite Windows Sockets. La idea es identificar de forma única cada aplicación de Windows Sockets por lo que puede tener más de una aplicación de Windows Sockets que se ejecuta en un equipo al mismo tiempo.  
  
 Algunos puertos están reservados para servicios comunes, como FTP. Debe evitar el uso de estos puertos a menos que se va a proporcionar ese tipo de servicio. La especificación de Windows Sockets detalla estos puertos reservados. En el archivo WINSOCK. H también enumera.  
  
 Para permitir que la DLL de Windows Sockets seleccionar un puerto libre para usted, pase 0 como el valor del puerto. MFC selecciona un valor de puerto mayor que 1.024 decimal. Puede recuperar el valor de puerto que MFC seleccionado mediante una llamada a la [CAsyncSocket::GetSockName](../mfc/reference/casyncsocket-class.md#getsockname) función miembro.  
  
##  <a name="_core_socket_address"></a>Dirección de socket  
 Cada objeto de socket está asociado a una dirección de protocolo de Internet (IP) en la red. Normalmente, la dirección es un nombre de equipo, como "ftp.microsoft.com", o un número de puntos, como "128.56.22.8".  
  
 Al intentar crear un socket, normalmente no es necesario especificar su propia dirección.  
  
> [!NOTE]
>  Es posible que su equipo tiene varias tarjetas de red (o algún día puede ejecutar la aplicación en un equipo), que representa una red diferente. Si es así, debe proporcionar una dirección para especificar qué tarjeta de red que se va a utilizar el socket. Esto tiene la certeza de que un uso avanzado y un posible problema de portabilidad.  
  
 Para obtener más información, consulte:  
  
-   [Windows Sockets: Usar la clase CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Usar Sockets con archivos](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets: Cómo funcionan los Sockets con archivos](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets: Sockets de flujos](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sockets de datagramas](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)

