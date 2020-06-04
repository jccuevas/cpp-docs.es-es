---
title: Agregar puntos de conexión a un objeto
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], adding to ATL objects
- Implement Connection Point ATL wizard
ms.assetid: 843531be-4a36-4db0-9d54-e029b1a72a8b
ms.openlocfilehash: 7341e69852ed804122e0196b51d305f5af0c35b9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223524"
---
# <a name="adding-connection-points-to-an-object"></a>Agregar puntos de conexión a un objeto

El [Tutorial de ATL](../atl/active-template-library-atl-tutorial.md) muestra cómo crear un control con compatibilidad para puntos de conexión, cómo agregar eventos y, a continuación, cómo implementar el punto de conexión. ATL implementa puntos de conexión con el [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) clase.

Para implementar un punto de conexión, tiene dos opciones:

- Implemente su propio origen de eventos salientes, mediante la adición de un punto de conexión para el control u objeto.

- Volver a usar una interfaz de punto de conexión definida en otra biblioteca de tipos.

En cualquier caso, el Asistente para implementar puntos de conexión utiliza una biblioteca de tipos para realizar su trabajo.

### <a name="to-add-a-connection-point-to-a-control-or-object"></a>Para agregar un punto de conexión a un control u objeto

1. Defina una interfaz dispinterface en el bloque de biblioteca del archivo .idl. Si habilitó la compatibilidad con puntos de conexión cuando creó el control con el Asistente para controles ATL, ya se creará la interfaz dispinterface. Si no habilitó la compatibilidad con puntos de conexión cuando se creó el control, debe agregar manualmente la dispinterface en el archivo. idl. El siguiente es un ejemplo de una interfaz dispinterface. Interfaces de salida no son necesarias para interfaces de envío, pero muchos lenguajes de scripting como VBScript y JScript requieren esto, por lo que este ejemplo usa dos interfaces dispinterface:

   [!code-cpp[NVC_ATL_Windowing#81](../atl/codesnippet/cpp/adding-connection-points-to-an-object_1.idl)]

   Use la utilidad uuidgen.exe o guidgen.exe para generar un GUID.

2. Agregue la dispinterface como la `[default,source]` interfaz en la coclase para el objeto en el archivo .idl del proyecto. Nuevamente, si habilitó la compatibilidad con puntos de conexión cuando se creó el control, el Asistente para controles ATL creará el `[default,source`] entrada. Para agregar manualmente esta entrada, agregue la línea en negrita:

   [!code-cpp[NVC_ATL_Windowing#82](../atl/codesnippet/cpp/adding-connection-points-to-an-object_2.idl)]

   Consulte el archivo .idl en el [Circ](../overview/visual-cpp-samples.md) ejemplo ATL para ver un ejemplo.

3. Utilice la vista de clases para agregar métodos y propiedades a la interfaz de eventos. Haga clic en la clase en la vista de clases, seleccione **agregar** en el menú contextual y haga clic en **agregar punto de conexión**.

4. En el **Interfaces de origen** cuadro de lista de la conexión de Asistente para implementar puntos, seleccione **interfaces del proyecto**. Si elige una interfaz para el control y presione **Aceptar**, tendrá que:

   - Generar un archivo de encabezado con una clase de proxy de eventos que implementa el código que hará que las llamadas salientes para el evento.

   - Agregue una entrada a la asignación de punto de conexión.

   También verá una lista de todas las bibliotecas de tipos en el equipo. Solo debe usar una de estas otras bibliotecas de tipos para definir el punto de conexión si desea implementar la interfaz de salida misma exacta que se encuentra en otra biblioteca de tipos.

### <a name="to-reuse-a-connection-point-interface-defined-in-another-type-library"></a>Para volver a usar una interfaz de punto de conexión definida en otra biblioteca de tipos

1. En la vista de clases, haga clic en una clase que implementa un **BEGIN_COM_MAP** macros, seleccione **agregar** en el menú contextual y haga clic en **agregar punto de conexión**.

2. En el Asistente para implementar puntos de conexión, seleccione una biblioteca de tipos y una interfaz en la biblioteca de tipos y haga clic en **agregar**.

3. Edite el archivo .idl para:

   - Copie la interfaz dispinterface del archivo .idl del objeto cuyo origen del evento que se está usando.

   - Use la **importlib** instrucciones sobre la biblioteca de tipos.

## <a name="see-also"></a>Vea también

[Punto de conexión](../atl/atl-connection-points.md)
