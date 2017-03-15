---
title: "Historial de DCOM | Microsoft Docs"
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
  - "DCOM"
  - "DCOM, acerca de DCOM"
  - "automatización remota, DCOM"
ms.assetid: c21aa0ea-1396-4b52-b77f-88fb0fdd2a5c
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Historial de DCOM
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando la automatización primero se introdujo a principios de 1993, fue capaz de utilizar sólo entre las aplicaciones que se ejecutan en el mismo equipo.  Sin embargo, dado que compartan los mismos apoyos que el resto de OLE, es decir, COM \(o modelo de objetos componentes\), se pretendía usar siempre que protegió a ser “remoto” cuando COM propio se actualizó para incluir capacidades de comunicación remota.  También se planeado que la transición de la operación puramente local a la operación distribuida con poco o nada de cambios en el código existente.  
  
 ¿Qué hace en medio de “interacción remota”?  El valor local COM dictó que el consumidor de una interfaz reside y se ejecuta en el mismo equipo que el proveedor de la interfaz.  Por ejemplo, Microsoft Visual Basic puede controlar una copia de Microsoft Excel en el equipo de escritorio, pero no es capaz de resolver la ejecución de Excel en otro equipo.  Con el desarrollo de COM distribuido, el consumidor de una interfaz no necesite residir en el mismo equipo que el en las que el proveedor de la interfaz se ejecute.  
  
 Una vez que COM fuera apropiado para trabajar en una red, cualquier interfaz que no fuera atada a un modelo local de ejecución \(algunas interfaces tiene confianza inherente a los servicios del equipo local, como esas interfaces de gráfico cuyos métodos tienen identificadores a los contextos de dispositivo como parámetros\) tendrían la capacidad de distribuir.  Un consumidor de la interfaz hacer una solicitud de una interfaz determinada; esta interfaz se puede proporcionar a una instancia de un objeto que se está ejecutando \(o ejecutar\) en otro equipo.  El mecanismo de distribución dentro de COM conectarse al consumidor al proveedor de manera que las llamadas al método realizadas por el consumidor aparecieran al final del proveedor, donde se ejecutan.  Cualquier valor devuelto después sería enviado al consumidor.  Para fines prácticos, el acto de distribución es transparente para el consumidor y el proveedor.  
  
 Una variedad de COM existe ahora.  DCOM \(para “COM distribuido”\) ha enviado con las versiones de Windows NT a partir de la versión 4.0 e incluir Windows 2000.  Desde finales de 1996, también ha sido disponibles para Windows 9x.  En ambos casos, DCOM comprende un conjunto de reemplazo y archivos DLL adicionales, con algunas utilidades, que proporcionan funciones COM locales y remotas.  Ahora es por consiguiente una parte inherente de plataformas de win32, y se habla en otras plataformas por otras organizaciones con el tiempo.  
  
## En esta sección  
 [¿Dónde automatización remota cabe en?](../mfc/where-does-remote-automation-fit-in-q.md)  
  
 [¿Qué automatización remota proporciona?](../mfc/what-does-remote-automation-provide-q.md)  
  
## Vea también  
 [Automatización remota](../mfc/remote-automation.md)