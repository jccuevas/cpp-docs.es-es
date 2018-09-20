---
title: Probar propiedades y eventos con un contenedor de prueba | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e06f10114b896e2728e5a017281e54f75ce534e5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404636"
---
# <a name="testing-properties-and-events-with-test-container"></a>Probar propiedades y eventos con un contenedor de prueba

La aplicación de contenedor de prueba, que se incluye en Visual C++, es un contenedor de controles ActiveX para probar y depurar controles ActiveX. Contenedor de prueba permite al desarrollador de control probar la funcionalidad del control cambiando sus propiedades, invocar sus métodos y activando sus eventos. Contenedor de prueba puede mostrar los registros de notificaciones de enlace de datos y también proporciona servicios para probar la funcionalidad de persistencia de un control ActiveX: puede guardar las propiedades en una secuencia o en subalmacenamiento, volver a cargarlos y examinar los datos de flujo almacenado. En esta sección se describe cómo usar las características básicas del contenedor de prueba. Para obtener más información, seleccione el **ayuda** menú mientras se ejecuta el contenedor de prueba.

### <a name="to-access-the-activex-control-test-container"></a>Para obtener acceso a ActiveX Control Test Container

1. Compilar el [ejemplo TSTCON: ActiveX Control Test Container](../visual-cpp-samples.md).

### <a name="to-test-your-activex-control"></a>Para probar el control ActiveX

1. En el **editar** menú del contenedor de prueba, haga clic en **Insertar nuevo Control**.

1. En el **insertar Control** , seleccione el control deseado y haga clic en **Aceptar**. El control aparecerá en el contenedor del control.

    > [!NOTE]
    >  Si el control no aparece en el **insertar Control** diálogo cuadro, asegúrese de que ha registrado con el **registrar controles** comando desde el **archivo** menú de prueba Contenedor.

En este momento puede probar el control propiedades o eventos.

#### <a name="to-test-properties"></a>Para probar las propiedades

1. En el **Control** menú, haga clic en **invocar métodos**.

1. En el **nombre del método** lista desplegable, seleccione el método PropPut para la propiedad que desea probar.

1. Modificar el **el valor del parámetro** o **tipo de parámetro** y haga clic en el **establecer valor** botón.

1. Haga clic en **Invoke** para aplicar el nuevo valor para el objeto.

     La propiedad contiene ahora el nuevo valor.

#### <a name="to-test-events-and-specify-the-destination-of-event-information"></a>Para probar eventos y especificar el destino de la información de eventos.

1. En el **opciones** menú, haga clic en **registro**.

1. Especifique el destino de la información de evento.

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Cómo: Depurar un control ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)

