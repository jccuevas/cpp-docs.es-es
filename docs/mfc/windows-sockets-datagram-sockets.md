---
title: 'Windows Sockets: Sockets de datagramas'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], datagram
- Windows Sockets [MFC], bi-directional data flow
- datagram sockets [MFC]
- Windows Sockets [MFC], datagram
- sockets [MFC], bi-directional data flow
ms.assetid: bec16a1c-74c0-4ff9-8c18-c2d87897d264
ms.openlocfilehash: 886409d4072a77244cff415c6f0a6a3f533e42d4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462132"
---
# <a name="windows-sockets-datagram-sockets"></a>Windows Sockets: Sockets de datagramas

Este artículo describe los sockets de datagrama, uno de los dos tipos de Windows Sockets disponibles. (El otro tipo es el [socket de secuencia](../mfc/windows-sockets-stream-sockets.md).)

Sockets de datagrama admiten un flujo de datos bidireccional que no se garantiza que se va a secuenciar o sin duplicar. También datagramas no se garantiza que sean confiables; pueden producirse errores en llegar. Los datos del datagrama pueden llegar desordenados y posiblemente duplicados, pero se conservan los límites de registro en los datos, siempre y cuando los registros son menores que el límite de tamaño interno del receptor. Usted es responsable de la administración de secuenciación y confiabilidad. (Confiabilidad tiende a ser buenas en redes de área local [LAN] pero menos etc. de área extensa de redes [WAN], como Internet).

Los datagramas son "sin conexión", es decir, no se establece ninguna conexión explícita; enviar un mensaje de datagrama a un socket especificado y puede recibir mensajes de un socket especificado.

Un ejemplo de un socket de datagrama es una aplicación que mantiene los relojes del sistema en la red que se sincronizan. Esto ilustra una capacidad adicional de los sockets de datagrama en al menos algunas opciones de configuración: difundir mensajes a un gran número de direcciones de red.

Sockets de datagramas son mejores que los sockets de secuencias de datos orientado a registro. Para obtener más información acerca de los sockets de datagrama, vea la especificación de Windows Sockets, disponible en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[Windows Sockets: Nociones](../mfc/windows-sockets-background.md)

