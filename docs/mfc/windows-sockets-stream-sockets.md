---
title: 'Windows Sockets: Sockets de secuencias'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- stream sockets [MFC]
ms.assetid: 31faaa34-a995-493f-a30b-b8115293d619
ms.openlocfilehash: 298428bd5e81d11eb62907dfbac39acda24524f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560230"
---
# <a name="windows-sockets-stream-sockets"></a>Windows Sockets: Sockets de secuencias

Este artículo describe los sockets de secuencias, uno de los dos tipos de Windows Sockets disponibles. (El otro tipo es el [socket de datagrama](../mfc/windows-sockets-datagram-sockets.md).)

Sockets de Stream proporcionan un flujo de datos sin límites de registro: un flujo de bytes que puede ser bidireccional (la aplicación es dúplex completo: pueden transmitir y recibir a través del socket). Secuencias se pueden confiar en entregar secuenciadas, sin duplicidad de datos. ("Secuenciado" significa que los paquetes se entregan en el orden enviado. "Sin duplicar" significa que un paquete determinado solo una vez.) Se garantiza la recepción de mensajes de secuencia y secuencias se adapta perfectamente para controlar grandes cantidades de datos.

La capa de transporte de red puede dividir o agrupar datos en paquetes de un tamaño razonable. La `CSocket` clase controlará el empaquetado y el desempaquetado.

Secuencias se basan en conexiones explícitas: socket A solicita una conexión de socket B; socket B acepta o rechaza la solicitud de conexión.

Una llamada de teléfono es una buena analogía de una secuencia. En circunstancias normales, la entidad de recepción escucha lo que dice en el orden en que afirman que, sin duplicación o pérdida. Sockets de Stream son adecuados, por ejemplo, para las implementaciones, como el archivo de protocolo de transferencia (FTP), que facilita la transferencia ASCII o archivos binarios de tamaño arbitrario.

Sockets de Stream son preferibles a sockets de datagramas cuando los datos deben ser garantiza que lleguen y al tamaño de los datos es grande. Para obtener más información acerca de los sockets de secuencias, vea la especificación Windows Sockets. La especificación está disponible en el SDK de Windows.

Uso de sockets de secuencia puede ser superior a las aplicaciones diseñadas para usar un socket de datagrama de difusión a todos los sockets de recepción en la red porque

- El modelo de difusión está sujeto a los problemas de saturación (o "storm") de red.

- El modelo de cliente-servidor posteriormente es más eficaz.

- El modelo de flujo proporciona la transferencia de datos confiable, donde el modelo de datagrama no.

- El modelo final aprovecha la capacidad para comunicarse entre Unicode y ANSI, las aplicaciones de socket que ofrece la clase CArchive a la clase CSocket.

    > [!NOTE]
    >  Si usa la clase `CSocket`, debe utilizar una secuencia. Una aserción de MFC se produce un error si se especifica el tipo de socket como **SOCK_DGRAM**.

## <a name="see-also"></a>Vea también

[Windows Sockets en MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[Windows Sockets: Nociones](../mfc/windows-sockets-background.md)

