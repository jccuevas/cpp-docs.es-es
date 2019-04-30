---
title: Tutoriales del Runtime de simultaneidad
ms.date: 11/04/2016
helpviewer_keywords:
- walkthroughs [Concurrency Runtime]
- Concurrency Runtime, walkthroughs
ms.assetid: 7374c5e9-54eb-44bf-9ed9-5e190cfd290b
ms.openlocfilehash: d176049bb3b03ae0f55170e45e20e7c2c0e322ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296499"
---
# <a name="concurrency-runtime-walkthroughs"></a>Tutoriales del Runtime de simultaneidad

Los temas basados en escenarios de esta sección muestran cómo utilizar muchas de las características del Runtime de simultaneidad.

## <a name="in-this-section"></a>En esta sección

[Tutorial: Conexión con tareas y solicitudes HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
Se muestra cómo usar el [IXMLHTTPRequest2](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2) y [IXMLHTTPRequest2Callback](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2callback) interfaces junto con las tareas para enviar solicitudes HTTP GET y POST a un servicio web en una aplicación de plataforma Universal de Windows (UWP).

[Tutorial: Creación de una aplicación basada en agente](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br/>
Describe cómo crear una aplicación basada en agente básica.

[Tutorial: Creación de un agente de flujo de datos](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
Muestra cómo crear aplicaciones basadas en agentes que se basan en el flujo de datos, en lugar de en el flujo de control.

[Tutorial: Creación de una red de procesamiento de imagen](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
Muestra cómo crear una red de bloques de mensajes asincrónicos que realizan procesamiento de imágenes.

[Tutorial: Implementación de futuros](../../parallel/concrt/walkthrough-implementing-futures.md)<br/>
Se muestra cómo calcular los valores para su uso posterior de forma asincrónica.

[Tutorial: Uso de una combinación para evitar el interbloqueo](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)<br/>
Usa el problema cena de los filósofos para ilustrar cómo se usa el [Concurrency:: join](../../parallel/concrt/reference/join-class.md) clase para evitar el interbloqueo en la aplicación.

[Tutorial: Eliminación de trabajo de un subproceso de la interfaz de usuario](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)<br/>
Muestra cómo mejorar el rendimiento de una aplicación MFC que dibuja el fractal de Mandelbrot.

[Tutorial: Uso del Runtime de simultaneidad en una aplicación habilitada para COM](../../parallel/concrt/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application.md)<br/>
Muestra cómo usar el Runtime de simultaneidad en una aplicación que utiliza el modelo de objetos componentes (COM).

[Tutorial: Adaptación del código existente para usar tareas ligeras](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)<br/>
Muestra cómo adaptar código existente que usa la API de Windows para crear y ejecutar un subproceso para utilizar una tarea ligera.

[Tutorial: Creación de un bloque de mensajes personalizado](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)<br/>
Describe cómo crear un tipo de bloque de mensajes personalizado que ordena los mensajes entrantes por prioridad.

## <a name="related-sections"></a>Secciones relacionadas

[Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime.md)<br/>
Presenta el marco de programación simultáneo para Visual C++.
