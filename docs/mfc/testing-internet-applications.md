---
title: Probar aplicaciones de Internet | Documentos de Microsoft
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
ms.openlocfilehash: 61ffc5b11783806555b210b8561cbe6cdd2878ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380076"
---
# <a name="testing-internet-applications"></a>Probar aplicaciones para Internet
Hay algunos desafíos únicos de pruebas en Internet, especialmente para las aplicaciones que se ejecutan en un servidor Web. Las pruebas iniciales suelen llevarse a cabo mediante un cliente de usuario único que se conecta a un servidor de prueba. Esto será útil para depurar el código.  
  
 También deseará probar en condiciones reales: con varios clientes conectados a través de conexiones de alta velocidad, así como las líneas de serie de baja velocidad, incluidas las conexiones de módem. Puede ser difícil simular condiciones reales, pero por supuesto, merece la pena de gastos escenarios posibles en tiempo de diseño y ejecutarlas. Si es posible, también deberá utilizar las herramientas a la capacidad de hacer pruebas de esfuerzo. Determinadas clases de errores, como errores de tiempo, son difíciles de encontrar y reproducir.  
  
 Uno de los desafíos de programación para Internet es su visibilidad. Muchos de los accesos a su sitio pueden ralentizar el servidor. Desea que el servidor de degradación correcta. Puede evitar cualquier cosa que pueda dañar el equipo de un usuario si se produce un error en la aplicación (por ejemplo, daños de los datos al escribir en el registro o al escribir las cookies en el cliente).  
  
## <a name="see-also"></a>Vea también  
 [Tareas de programación de Internet MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)

