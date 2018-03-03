---
title: Probar propiedades y eventos con Test Container | Documentos de Microsoft
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
- testing, test containers
- tstcon32.exe
- debugging ActiveX controls
- test container
- ActiveX Control Test Container
- ActiveX controls [MFC], testing
- properties [MFC], testing
ms.assetid: 626867cf-fe53-4c30-8973-55bb93ef3917
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 381f4e421b63b2ba48fe649a30e5bf7648b50d27
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="testing-properties-and-events-with-test-container"></a>Probar propiedades y eventos con un contenedor de prueba
La aplicación Test Container, suministrada en Visual C++, es un contenedor de controles ActiveX para probar y depurar controles ActiveX. Contenedor de prueba permite al desarrollador de control probar la funcionalidad del control cambiando sus propiedades, invocando sus métodos y activando sus eventos. Contenedor de prueba puede mostrar registros de notificaciones de enlace de datos y también proporciona medios para probar la funcionalidad de persistencia de un control ActiveX: puede guardar las propiedades en una secuencia o a subalmacenamiento, recargue y examinar los datos de la secuencia almacenada. En esta sección se describe cómo usar las características básicas de Test Container. Para obtener más información, seleccione la **ayuda** menú mientras se ejecuta el contenedor de prueba.  
  
### <a name="to-access-the-activex-control-test-container"></a>Para obtener acceso a ActiveX Control Test Container  
  
1.  Compilar el [ejemplo TSTCON: ActiveX Control Test Container](../visual-cpp-samples.md).  
  
### <a name="to-test-your-activex-control"></a>Para probar el control ActiveX  
  
1.  En el **editar** menú de Test Container, haga clic en **Insertar nuevo Control**.  
  
2.  En el **insertar Control** , seleccione el control deseado y haga clic en **Aceptar**. El control aparecerá en el contenedor del control.  
  
    > [!NOTE]
    >  Si el control no aparece en la **insertar Control** diálogo cuadro, asegúrese de que se ha registrado con el **registrar controles** línea de comandos desde el **archivo** menú de prueba Contenedor.  
  
 En este momento puede probar el control propiedades o eventos.  
  
#### <a name="to-test-properties"></a>Para probar propiedades  
  
1.  En el **Control** menú, haga clic en **invocar métodos**.  
  
2.  En el **nombre del método** lista desplegable, seleccione el método PropPut para la propiedad que desea probar.  
  
3.  Modificar el **el valor del parámetro** o **tipo de parámetro** y haga clic en el **establecer valor** botón.  
  
4.  Haga clic en **Invoke** para aplicar el nuevo valor para el objeto.  
  
     La propiedad contiene ahora el nuevo valor.  
  
#### <a name="to-test-events-and-specify-the-destination-of-event-information"></a>Para probar eventos y especificar el destino de la información del evento.  
  
1.  En el **opciones** menú, haga clic en **registro**.  
  
2.  Especifique el destino de información de eventos.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md)   
 [Cómo: Depurar un control ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)

