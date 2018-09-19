---
title: Tutoriales del Runtime de simultaneidad | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- walkthroughs [Concurrency Runtime]
- Concurrency Runtime, walkthroughs
ms.assetid: 7374c5e9-54eb-44bf-9ed9-5e190cfd290b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19de73a99384d8cea0f9f594b5a1a214f8aaaf22
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2018
ms.locfileid: "42545899"
---
# <a name="concurrency-runtime-walkthroughs"></a>Tutoriales del Runtime de simultaneidad
Los temas basados en escenarios de esta sección muestran cómo utilizar muchas de las características del Runtime de simultaneidad.  
  
## <a name="in-this-section"></a>En esta sección  
 [Tutorial: Conectar mediante tareas y solicitudes HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)  
 Se muestra cómo usar el [IXMLHTTPRequest2](/previous-versions/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2) y [IXMLHTTPRequest2Callback](/previous-versions/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2callback) interfaces junto con las tareas para enviar solicitudes HTTP GET y POST a un servicio web en una aplicación de plataforma Universal de Windows (UWP).  
  
 [Tutorial: Crear una aplicación basada en agente](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)  
 Describe cómo crear una aplicación basada en agente básica.  
  
 [Tutorial: Crear un agente de flujo de datos](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)  
 Muestra cómo crear aplicaciones basadas en agentes que se basan en el flujo de datos, en lugar de en el flujo de control.  
  
 [Tutorial: Crear una red de procesamiento de imagen](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)  
 Muestra cómo crear una red de bloques de mensajes asincrónicos que realizan procesamiento de imágenes.  
  
 [Tutorial: Implementar futuros](../../parallel/concrt/walkthrough-implementing-futures.md)  
 Se muestra cómo calcular los valores para su uso posterior de forma asincrónica.  
  
 [Tutorial: Usar la clase join para evitar un interbloqueo](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)  
 Usa el problema cena de los filósofos para ilustrar cómo se usa el [Concurrency:: join](../../parallel/concrt/reference/join-class.md) clase para evitar el interbloqueo en la aplicación.  
  
 [Tutorial: Quitar trabajo de un subproceso de la interfaz de usuario](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)  
 Muestra cómo mejorar el rendimiento de una aplicación MFC que dibuja el fractal de Mandelbrot.  
  
 [Tutorial: Usar el Runtime de simultaneidad en una aplicación habilitada para COM](../../parallel/concrt/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application.md)  
 Muestra cómo usar el Runtime de simultaneidad en una aplicación que utiliza el modelo de objetos componentes (COM).  
  
 [Tutorial: Adaptar el código existente para usar tareas ligeras](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)  
 Muestra cómo adaptar código existente que usa la API de Windows para crear y ejecutar un subproceso para utilizar una tarea ligera.  
  
 [Tutorial: Crear un bloque de mensajes personalizado](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)  
 Describe cómo crear un tipo de bloque de mensajes personalizado que ordena los mensajes entrantes por prioridad.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime.md)  
 Presenta el marco de programación simultáneo para Visual C++.

