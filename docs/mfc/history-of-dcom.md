---
title: Historial de DCOM | Documentos de Microsoft
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
- Remote Automation, DCOM
- DCOM, about DCOM
- DCOM
ms.assetid: c21aa0ea-1396-4b52-b77f-88fb0fdd2a5c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6ef567c39c93c3d43fdfc0fa63886144b03cd474
ms.sourcegitcommit: fa7a6dccddce3747389c91277a53e296f905305c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="history-of-dcom"></a>Historial de DCOM
Cuando automatización se introdujo en principios de 1993, fue capaz de ser utilizada únicamente entre aplicaciones que se ejecutan en el mismo equipo. Sin embargo, dado que estos comparten la misma base que el resto de OLE, es decir, COM (o modelo de objetos componentes), siempre estaba previsto que convertiría en "remoto" cuando se actualizara COM para incluir capacidades de comunicación remota. También se planeó que la transición de un funcionamiento exclusivamente local al funcionamiento distribuido requeriría pocos o ningún cambio en el código existente.  
  
 Por lo que ¿qué "remoting" significa COM Local indica que el consumidor de una interfaz residen y se ejecutan en el mismo equipo que el proveedor de dicha interfaz. Por ejemplo, Microsoft Visual Basic podía controlar una copia de Microsoft Excel en su equipo de escritorio, pero no era capaz de controlar la ejecución de Excel en otro equipo. Con el desarrollo de COM distribuido, el consumidor de una interfaz ya no debe residir en el mismo equipo que en el que se ejecuta el proveedor de interfaz.  
  
 Una vez que COM se adaptó para que funcione a través de una red, cualquier interfaz que no se ha asociado a un modelo de ejecución local (algunas interfaces tienen inherentes a la dependencia de los servicios del equipo local, como las interfaces dibujo cuyos métodos tienen identificadores de contextos de dispositivo parámetros) tendría la capacidad de que se está distribuyendo. Un consumidor de interfaz podría realizar una solicitud para una interfaz determinada; una instancia de un objeto que se ejecuta (o para ejecutarse) pueden proporcionar esa interfaz en un equipo diferente. El mecanismo de distribución dentro de COM conectará el consumidor al proveedor de tal manera que las llamadas de método realizadas por el consumidor aparecería en el extremo de proveedor, donde se ejecutará. Todos los valores, a continuación, se envía al consumidor de retorno. A efectos prácticos, el hecho de distribución es transparente para el consumidor y el proveedor.  
  
 Ahora existe una variedad de COM. DCOM (para "COM distribuido") se envía con las versiones de Windows NT a partir de la versión 4.0 y en Windows 2000. Desde 1996, también ha estado disponible para Windows 9 x. En ambos casos, DCOM consta de un conjunto de reemplazo y archivos DLL adicionales, con algunas de las utilidades, que proporcionan características COM locales y remotos. Por lo tanto, ahora es una parte inherente de plataformas basadas en Win32 y estará disponible en otras plataformas por otras organizaciones con el tiempo.  
  
## <a name="in-this-section"></a>En esta sección  
 [Dónde encaja la automatización remota](where-does-remote-automation-fit-in-q.md)  
  
 [¿Qué proporciona la automatización remota](what-does-remote-automation-provide-q.md)  
  
## <a name="see-also"></a>Vea también  
 [Automatización remota](../mfc/remote-automation.md)
