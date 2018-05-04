---
title: Agregar puntos de conexión a un objeto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], adding to ATL objects
- Implement Connection Point ATL wizard
ms.assetid: 843531be-4a36-4db0-9d54-e029b1a72a8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71f9d136ccdeded02303894195c7b8126acafd9c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="adding-connection-points-to-an-object"></a>Agregar puntos de conexión a un objeto
El [Tutorial de ATL](../atl/active-template-library-atl-tutorial.md) muestra cómo crear un control con compatibilidad para puntos de conexión, cómo agregar eventos y, a continuación, cómo implementar el punto de conexión. ATL implementa los puntos de conexión con el [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) clase.  
  
 Para implementar un punto de conexión, tiene dos opciones:  
  
-   Implemente su propio origen de eventos salientes, mediante la adición de un punto de conexión que el objeto o el control.  
  
-   Volver a utilizar una interfaz de punto de conexión definida en otra biblioteca de tipos.  
  
 En cualquier caso, el Asistente para implementar puntos de conexión utiliza una biblioteca de tipos para realizar su trabajo.  
  
### <a name="to-add-a-connection-point-to-a-control-or-object"></a>Para agregar un punto de conexión a un control o un objeto  
  
1.  Defina una interfaz dispinterface en el bloque de biblioteca del archivo .idl. Si has habilitado el soporte para los puntos de conexión cuando se creó el control con el Asistente para controles ATL, la dispinterface ya se creará. Si no habilitó la compatibilidad con puntos de conexión cuando se creó el control, debe agregar manualmente una dispinterface al archivo .idl. El siguiente es un ejemplo de una interfaz dispinterface. Interfaces de salida no son necesarias para interfaces de envío, pero muchos lenguajes de scripting como VBScript y JScript requieren esta opción, por lo que este ejemplo usa dos interfaces dispinterface:  
  
     [!code-cpp[NVC_ATL_Windowing#81](../atl/codesnippet/cpp/adding-connection-points-to-an-object_1.idl)]  
  
     Use el uuidgen.exe o guidgen.exe Utilidad para generar un GUID.  
  
2.  Agregue la dispinterface como la `[default,source]` interfaz en la coclase para el objeto en el archivo .idl del proyecto. Una vez más, si has habilitado el soporte para puntos de conexión cuando se creó el control, el Asistente para controles ATL creará el `[default,source`] entrada. Para agregar manualmente esta entrada, agregue la línea en negrita:  
  
     [!code-cpp[NVC_ATL_Windowing#82](../atl/codesnippet/cpp/adding-connection-points-to-an-object_2.idl)]  
  
     Vea el archivo .idl en el [Circ](../visual-cpp-samples.md) ejemplo ATL para obtener un ejemplo.  
  
3.  Use la vista de clases para agregar métodos y propiedades para la interfaz de eventos. Haga clic en la clase de vista de clases, seleccione **agregar** en el menú contextual y haga clic en **agregar punto de conexión**.  
  
4.  En el **Interfaces de origen** cuadro de lista del Asistente de punto de conexión de implementar, seleccione **interfaces del proyecto**. Si elige una interfaz para el control y presione **Aceptar**, tendrá que:  
  
    -   Generar un archivo de encabezado con una clase de proxy de evento que implementa el código que hará que las llamadas salientes para el evento.  
  
    -   Agregue una entrada a la asignación de punto de conexión.  
  
     También verá una lista de todas las bibliotecas de tipos en el equipo. Sólo se debe utilizar una de estas otras bibliotecas de tipos para definir el punto de conexión si desea implementar la interfaz de salida mismo exacta que se encuentra en otra biblioteca de tipos.  
  
### <a name="to-reuse-a-connection-point-interface-defined-in-another-type-library"></a>Para reutilizar una interfaz de punto de conexión definida en otra biblioteca de tipos  
  
1.  En la vista de clases, haga clic en una clase que implementa un **BEGIN_COM_MAP** (macro), seleccione **agregar** en el menú contextual y haga clic en **agregar punto de conexión**.  
  
2.  En el Asistente para implementar puntos de conexión, seleccione una biblioteca de tipos y una interfaz en la biblioteca de tipos y haga clic en **agregar**.  
  
3.  Edite el archivo .idl para:  
  
    -   Copiar la dispinterface desde el archivo IDL para el objeto cuyo origen de eventos está usándola.  
  
    -   Use la **importlib** instrucciones sobre la biblioteca de tipos.  
  
## <a name="see-also"></a>Vea también  
 [Punto de conexión](../atl/atl-connection-points.md)

