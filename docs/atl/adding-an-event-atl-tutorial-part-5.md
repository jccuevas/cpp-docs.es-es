---
title: Agregar un evento (ATL Tutorial, parte 5) | Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb72babcc4bf425e4ea588e4e2a155b077c47cc
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754883"
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>Agregar un evento (Tutorial de ATL, Parte 5)

En este paso, agregará un `ClickIn` y un `ClickOut` eventos al control ATL. Desencadenará el `ClickIn` evento si el usuario hace clic dentro del polígono y fire `ClickOut` si el usuario hace clic fuera. Las tareas para agregar un evento son los siguientes:

- Agregar el `ClickIn` y `ClickOut` métodos

- Generar la biblioteca de tipos

- Implementación de las Interfaces de punto de conexión

## <a name="adding-the-clickin-and-clickout-methods"></a>Agregar los métodos ClickIn y ClickOut

Cuando el control ATL que creó en el paso 2, seleccionó la **puntos de conexión** casilla de verificación. Esto crea el `_IPolyCtlEvents` interfaz en el archivo Polygon.idl. Tenga en cuenta que el nombre de interfaz comienza con un carácter de subrayado. Esta es una convención para indicar que la interfaz es una interfaz interna. Por lo tanto, pueden elegir los programas que le permiten explorar los objetos COM no se muestre la interfaz para el usuario. Tenga en cuenta también que la selección **puntos de conexión** agregó la siguiente línea en el archivo Polygon.idl para indicar que `_IPolyCtlEvents` es la interfaz de origen predeterminada:

`[default, source] dispinterface _IPolyCtlEvents;`

El atributo de origen indica que el control es el origen de las notificaciones, por lo que llamará a esta interfaz en el contenedor.

Ahora, agregue el `ClickIn` y `ClickOut` métodos para la `_IPolyCtlEvents` interfaz.

#### <a name="to-add-the-clickin-and-clickout-methods"></a>Para agregar los métodos ClickIn y ClickOut

1. En la vista de clases, expanda Polygon y PolygonLib para mostrar _IPolyCtlEvents.

2. Haga clic en _IPolyCtlEvents. En el menú contextual, haga clic en **Agregar** y después en **Agregar método**.

3. Seleccione un **tipo de valor devuelto** de `void`.

4. Escriba *ClickIn* en el **nombre del método** cuadro.

5. En **atributos de parámetro**, seleccione el **en** cuadro.

6. Seleccione un **tipo de parámetro** de `LONG`.

7. Tipo *x* como el **nombre del parámetro**y haga clic en **agregar**.

8. Repita los pasos 5 a 7, esta vez para una **nombre del parámetro** de *y*.

9. Haga clic en **Siguiente**.

10. Tipo `method ClickIn` como el **helpstring**.

11. Haga clic en **Finalizar**.

12. Repita los pasos anteriores para definir un `ClickOut` método con el mismo `LONG` parámetros *x* y *y*, el mismo **atributos de parámetro** y el mismo `void` tipo de valor devuelto.

Compruebe el archivo Polygon.idl para ver que el código se ha agregado a la `_IPolyCtlEvents` dispinterface.

El `_IPolyCtlEvents` dispinterface del archivo Polygon.idl ahora debería parecerse a esto:

[!code-cpp[NVC_ATL_Windowing#56](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_1.idl)]

El `ClickIn` y `ClickOut` métodos toman la x y coordenadas del punto donde ha hecho clic como parámetros.

## <a name="generating-the-type-library"></a>Generar la biblioteca de tipos

Generar la biblioteca de tipos en este momento, ya que el Asistente para puntos de conexión se utiliza para obtener la información que necesita construir una interfaz de punto de conexión y una interfaz de contenedor de punto de conexión para el control.

#### <a name="to-generate-the-type-library"></a>Para generar la biblioteca de tipos

1. Recompile el proyecto.

     O bien

2. Haga clic en el archivo Polygon.idl en el Explorador de soluciones y haga clic en **compilar** en el menú contextual.

Esto creará el archivo Polygon.tlb, que es la biblioteca de tipos. El archivo Polygon.tlb no es visible desde el Explorador de soluciones, ya que es un archivo binario y no puede ver ni modificar directamente.

## <a name="implementing-the-connection-point-interfaces"></a>Implementación de las Interfaces de punto de conexión

Implementar una interfaz de punto de conexión y una interfaz de contenedor de punto de conexión para el control. En COM, los eventos se implementan a través del mecanismo de puntos de conexión. Para recibir eventos de un objeto COM, un contenedor establece una conexión de consulta al punto de conexión que el objeto COM implementa. Dado un objeto COM puede tener varios puntos de conexión, el objeto COM también implementa una interfaz de contenedor de punto de conexión. Mediante esta interfaz, el contenedor puede determinar qué puntos de conexión se admiten.

La interfaz que implementa un punto de conexión se denomina `IConnectionPoint`, y la interfaz que implementa un contenedor de punto de conexión se denomina `IConnectionPointContainer`.

Para ayudar a implementar `IConnectionPoint`, utilizará el Asistente para implementar puntos de conexión. Este asistente genera el `IConnectionPoint` interfaz mediante la lectura de la biblioteca de tipos e implementando una función por cada evento que se puede activar.

#### <a name="to-use-the-implement-connection-point-wizard"></a>Para usar al Asistente para implementar puntos de conexión

1. En la vista de clases, haga clic en la clase del control implementación `CPolyCtl`.

2. En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **agregar punto de conexión**.

3. Seleccione `_IPolyCtlEvents` desde el **Interfaces de origen** lista y haga doble clic en él para agregarlo a la **implementar puntos de conexión** columna. Haga clic en **Finalizar**. Se generará una clase de proxy del punto de conexión, en este caso, `CProxy_IPolyCtlEvents`.

Si observa el archivo _IPolyCtlEvents_CP.h generado en el Explorador de soluciones, verá que tiene una clase denominada `CProxy_IPolyCtlEvents` que se deriva de `IConnectionPointImpl`. _IPolyCtlEvents_CP.h también define los dos métodos `Fire_ClickIn` y `Fire_ClickOut`, que toman los dos parámetros de coordenadas. Estos métodos se llaman cuando desea desencadenar un evento desde el control.

El asistente también agrega `CProxy_PolyEvents` y `IConnectionPointContainerImpl` a la lista de herencia múltiple de su control. El asistente también expuesto `IConnectionPointContainer` automáticamente mediante la adición de entradas correspondientes al mapa COM.

Ya ha terminado de implementar el código para admitir los eventos. Ahora, agregue código para activar los eventos en el momento adecuado. Recuerde que va a activar una `ClickIn` o `ClickOut` cuando el usuario hace clic en el botón primario del mouse en el control de eventos. Para averiguar cuándo el usuario hace clic en el botón, agregue un controlador para el `WM_LBUTTONDOWN` mensaje.

#### <a name="to-add-a-handler-for-the-wmlbuttondown-message"></a>Para agregar un controlador para el mensaje WM_LBUTTONDOWN

1. En la vista de clases, haga clic en la clase CPolyCtl y haga clic en **propiedades** en el menú contextual.

2. En el **propiedades** ventana, haga clic en el **mensajes** icono y, a continuación, haga clic en `WM_LBUTTONDOWN` en la lista de la izquierda.

3. En la lista desplegable que aparece, haga clic en  **\<Agregar > OnLButtonDown**. El `OnLButtonDown` declaración del controlador se agregarán a PolyCtl.h y la implementación del controlador se agregarán a PolyCtl.cpp.

A continuación, modifique el controlador.

#### <a name="to-modify-the-onlbuttondown-method"></a>Para modificar el método OnLButtonDown

1. Cambiar el código que contiene el `OnLButtonDown` método PolyCtl.cpp (eliminando el código insertado el asistente) para que se parece a esto:

     [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]

Esto permite código calcula el uso de los puntos en el `OnDraw` función para crear una región que detecta los clics del usuario con la llamada a `PtInRegion`.

El *uMsg* parámetro es el identificador del mensaje de Windows está controlando. Esto le permite tener una función que controla un intervalo de mensajes. El *wParam* y *lParam* parámetros son los valores estándar para el mensaje que se está controlando. El parámetro bHandled permite especificar si la función controló el mensaje o no. De forma predeterminada, el valor se establece en TRUE para indicar que la función controló el mensaje, pero se puede establecer en FALSE. Esto hará que ATL continuar buscando otra función de controlador de mensajes enviar el mensaje.

## <a name="building-and-testing-the-control"></a>Compilar y probar el control

Pruebe ahora los eventos. Compilar el control y vuelva a iniciar el Control ActiveX Test Container. Esta vez, abra la ventana de registro de eventos. Para enrutar eventos a la ventana de salida, haga clic en **registro** desde el **opciones** menú y seleccione **registro de la ventana de salida**. Insertar el control e intente hacer clic en la ventana. Tenga en cuenta que `ClickIn` se activa si hace clic dentro del polígono de relleno y `ClickOut` se desencadena al hacer clic fuera de él.

A continuación, agregará una página de propiedades.

[Vuelva al paso 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [con el paso 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="see-also"></a>Vea también

[Tutorial](../atl/active-template-library-atl-tutorial.md)

