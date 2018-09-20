---
title: Probar aplicaciones de Internet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Web applications [MFC], testing
- debugging Web applications [MFC], testing applications
- testing [MFC], Internet applications
- debugging [MFC], Web applications
- Internet debugging and testing
ms.assetid: ac4c74e3-d4ad-4e19-8f6c-e270de067f01
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 518fbe754b676798c6d2acc2a3e26ea1d3e3d4ac
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444171"
---
# <a name="testing-internet-applications"></a>Probar aplicaciones para Internet

Hay algunos desafíos únicos de pruebas en Internet, especialmente para aplicaciones que se ejecutan en un servidor Web. Las pruebas iniciales probablemente se realizará mediante un cliente de usuario único, conectarse a un servidor de prueba. Esto será útil para depurar el código.

También deseará probar en condiciones reales: con varios clientes conectados a través de conexiones de alta velocidad, así como las líneas de serie de baja velocidad, incluidas las conexiones de módem. Puede ser difícil simular condiciones reales, pero definitivamente vale la pena gasto escenarios posibles en tiempo de diseño y ejecutarlas. Si es posible, también querrá usar herramientas para la capacidad de hacer y las pruebas de esfuerzo. Ciertas clases de errores, como los errores de tiempo, son difíciles de encontrar y reproducir.

Uno de los desafíos de la programación de Internet es su visibilidad. Muchos de los accesos a su sitio pueden ralentizar el servidor. Desea que su servidor degradarse correctamente. Desea evitar que cualquier cosa que pueda dañar el equipo de un usuario si se produce un error en la aplicación (por ejemplo, los daños de datos al escribir en el registro o al escribir las cookies en el cliente).

## <a name="see-also"></a>Vea también

[Tareas de programación para Internet de MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)

