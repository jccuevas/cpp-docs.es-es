---
title: 'Windows Sockets: Sockets de datagramas | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sockets [MFC], datagram
- Windows Sockets [MFC], bi-directional data flow
- datagram sockets [MFC]
- Windows Sockets [MFC], datagram
- sockets [MFC], bi-directional data flow
ms.assetid: bec16a1c-74c0-4ff9-8c18-c2d87897d264
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 30ad7cab43301ae2cb7ebcb1fb4dfa850090955d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="windows-sockets-datagram-sockets"></a>Windows Sockets: Sockets de datagramas
Este artículo describen los sockets de datagramas, uno de los dos tipos de Socket de Windows disponibles. (El otro tipo es el [socket de secuencia](../mfc/windows-sockets-stream-sockets.md).)  
  
 Sockets de datagramas admiten un flujo de datos bidireccional que no se garantiza que lleguen por orden y sin duplicar. También datagramas no se garantiza que sea fiable; pueden producirse errores de llegada. Datos de datagrama pueden llegar desordenados y posiblemente duplicados, pero se conservan los límites del registros en los datos, siempre y cuando los registros son menores que el límite de tamaño interno del receptor. Son responsables de administrar secuenciación y confiabilidad. (Confiabilidad tiende a ser bien en redes de área local [LAN] pero menos área extensa etc. redes [WAN], como Internet).  
  
 Los datagramas son "sin conexión", es decir, se establece ninguna conexión explícita; enviar un mensaje de datagrama a un socket determinado y puede recibir mensajes de un socket especificado.  
  
 Un ejemplo de un socket de datagrama es una aplicación que mantiene los relojes del sistema en la red que se sincronizan. Esto ilustra una capacidad adicional de los sockets de datagramas en al menos algunas opciones de configuración: difundir mensajes a un gran número de direcciones de red.  
  
 Sockets de datagramas son mejores que los sockets de secuencias de datos orientado al registro. Para obtener más información acerca de los sockets de datagramas, vea la especificación de Windows Sockets, disponible en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)   
 [Windows Sockets: Nociones](../mfc/windows-sockets-background.md)

