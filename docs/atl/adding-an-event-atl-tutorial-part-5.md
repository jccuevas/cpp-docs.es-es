---
title: Agregar un evento (ATL Tutorial, parte 5) | Documentos de Microsoft
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
ms.openlocfilehash: a118cf29546ac8dae2e882d5658b07e3b5e085f6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361270"
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>Agregar un evento (Tutorial de ATL, Parte 5)
En este paso, agregará un `ClickIn` y un `ClickOut` evento al control ATL. Se activará la `ClickIn` evento si el usuario hace clic dentro del polígono y activan `ClickOut` si el usuario hace clic fuera de. Las tareas para agregar un evento son los siguientes:  
  
-   Agregar el `ClickIn` y `ClickOut` métodos  
  
-   Generar la biblioteca de tipos  
  
-   Implementar las Interfaces de punto de conexión  
  
## <a name="adding-the-clickin-and-clickout-methods"></a>Agregar los métodos ClickIn y ClickOut  
 Cuando se creó el control ATL en el paso 2, seleccionó la **puntos de conexión** casilla de verificación. Esto crea la `_IPolyCtlEvents` interfaz en el archivo Polygon.idl. Tenga en cuenta que el nombre de interfaz comienza con un carácter de subrayado. Se trata de una convención para indicar que la interfaz es una interfaz interna. Por lo tanto, pueden elegir programas que le permiten examinar objetos COM no se muestre la interfaz para el usuario. Tenga en cuenta también que, al seleccionar **puntos de conexión** agregue la siguiente línea en el archivo Polygon.idl para indicar que `_IPolyCtlEvents` es la interfaz de origen predeterminada:  
  
 `[default, source] dispinterface _IPolyCtlEvents;`  
  
 El atributo de origen indica que el control es el origen de las notificaciones, por lo que llamará a esta interfaz en el contenedor.  
  
 A continuación, agregue el `ClickIn` y `ClickOut` métodos para la `_IPolyCtlEvents` interfaz.  
  
#### <a name="to-add-the-clickin-and-clickout-methods"></a>Para agregar los métodos ClickIn y ClickOut  
  
1.  En la vista de clases, expanda Polygon y PolygonLib para mostrar _IPolyCtlEvents.  
  
2.  Haga clic en _IPolyCtlEvents. En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **Agregar método**.  
  
3.  Seleccione un **tipo de valor devuelto** de `void`.  
  
4.  Escriba `ClickIn` en el **nombre del método** cuadro.  
  
5.  En **atributos de parámetro**, seleccione la **en** cuadro.  
  
6.  Seleccione un **tipo de parámetro** de `LONG`.  
  
7.  Tipo de `x` como el **nombre de parámetro**y haga clic en **agregar**.  
  
8.  Repita los pasos 5 a 7, esta vez para una **nombre de parámetro** de `y`.  
  
9. Haga clic en **Siguiente**.  
  
10. Tipo de `method ClickIn` como el **helpstring**.  
  
11. Haga clic en **Finalizar**.  
  
12. Repita los pasos anteriores para definir un `ClickOut` método con el mismo `LONG` parámetros `x` y `y`, el mismo **atributos de parámetro** y el mismo `void` tipo de valor devuelto.  
  
 Compruebe el archivo Polygon.idl y comprobar que el código se ha agregado a la `_IPolyCtlEvents` dispinterface.  
  
 El `_IPolyCtlEvents` dispinterface en el archivo Polygon.idl debe tener el siguiente aspecto:  
  
 [!code-cpp[NVC_ATL_Windowing#56](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_1.idl)]  
  
 El `ClickIn` y `ClickOut` métodos toman la x y coordenadas del punto donde ha hecho clic como parámetros.  
  
## <a name="generating-the-type-library"></a>Generar la biblioteca de tipos  
 Generar la biblioteca de tipos en este momento, porque el Asistente para puntos de conexión se utiliza para obtener la información que necesita construir una interfaz de punto de conexión y una interfaz de contenedor de punto de conexión para el control.  
  
#### <a name="to-generate-the-type-library"></a>Para generar la biblioteca de tipos  
  
1.  Recompile el proyecto.  
  
     -o bien-  
  
2.  Haga clic en el archivo Polygon.idl en el Explorador de soluciones y haga clic en **compilar** en el menú contextual.  
  
 Esto creará el archivo Polygon.tlb, que es la biblioteca de tipos. El archivo Polygon.tlb no es visible desde el Explorador de soluciones, porque es un archivo binario y no se puede ver ni modificar directamente.  
  
## <a name="implementing-the-connection-point-interfaces"></a>Implementar las Interfaces de punto de conexión  
 Implementar una interfaz de punto de conexión y una interfaz de contenedor de punto de conexión para el control. En COM, los eventos se implementan a través del mecanismo de puntos de conexión. Para recibir eventos de un objeto COM, un contenedor establece una conexión de consulta para el punto de conexión que el objeto COM implementa. Dado que un objeto COM puede tener varios puntos de conexión, el objeto COM también implementa una interfaz de contenedor de punto de conexión. A través de esta interfaz, el contenedor puede determinar qué puntos de conexión son compatibles.  
  
 La interfaz que implementa un punto de conexión se denomina `IConnectionPoint`, y la interfaz que implementa un contenedor de punto de conexión se denomina `IConnectionPointContainer`.  
  
 Para ayudar a implementar `IConnectionPoint`, utilizará el Asistente para implementar puntos de conexión. Este asistente genera el `IConnectionPoint` interfaz al leer la biblioteca de tipos e implementando una función para cada evento que se pueden activar.  
  
#### <a name="to-use-the-implement-connection-point-wizard"></a>Para usar al Asistente para implementar puntos de conexión  
  
1.  En la vista de clases, haga clic en la clase del control implementación `CPolyCtl`.  
  
2.  En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **agregar punto de conexión**.  
  
3.  Seleccione `_IPolyCtlEvents` desde el **Interfaces de origen** lista y haga doble clic en él para agregarlo a la **implementar puntos de conexión** columna. Haga clic en **Finalizar**. Se generará una clase de proxy para el punto de conexión, en este caso, `CProxy_IPolyCtlEvents`.  
  
 Si mira el archivo _IPolyCtlEvents_CP.h generado en el Explorador de soluciones, verá que tiene una clase denominada `CProxy_IPolyCtlEvents` que se deriva de `IConnectionPointImpl`. _IPolyCtlEvents_CP.h también define los dos métodos `Fire_ClickIn` y `Fire_ClickOut`, que toma dos parámetros de coordenadas. Estos métodos se llaman cuando desea desencadenar un evento desde el control.  
  
 El asistente también agregado `CProxy_PolyEvents` y `IConnectionPointContainerImpl` a la lista de herencia múltiple del control. El asistente también expuesto `IConnectionPointContainer` automáticamente mediante la adición de entradas correspondientes a la asignación COM.  
  
 Haya terminado de implementar el código para que admita eventos. Ahora, agregue código para activar los eventos en el momento adecuado. Recuerde que se va a desencadenar una `ClickIn` o `ClickOut` cuando el usuario hace clic en el botón primario del mouse en el control de eventos. Para averiguar cuándo el usuario hace clic en el botón, agregue un controlador para el `WM_LBUTTONDOWN` mensaje.  
  
#### <a name="to-add-a-handler-for-the-wmlbuttondown-message"></a>Para agregar un controlador para el mensaje WM_LBUTTONDOWN  
  
1.  En la vista de clases, haga clic en la clase CPolyCtl y haga clic en **propiedades** en el menú contextual.  
  
2.  En el **propiedades** ventana, haga clic en el **mensajes** icono y, a continuación, haga clic en `WM_LBUTTONDOWN` en la lista de la izquierda.  
  
3.  En la lista desplegable que aparece, haga clic en  **\<Agregar > OnLButtonDown**. El `OnLButtonDown` declaración del controlador se agregará a PolyCtl.h, y la implementación del controlador se agregarán a PolyCtl.cpp.  
  
 A continuación, modifique el controlador.  
  
#### <a name="to-modify-the-onlbuttondown-method"></a>Para modificar el OnLButtonDown (método)  
  
1.  Cambiar el código que comprende el `OnLButtonDown` método en PolyCtl.cpp (eliminando el código que haya insertado por el asistente) para que tenga un aspecto similar al siguiente:  
  
     [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]  
  
 Esto hace que la código calcula el uso de los puntos en el `OnDraw` función para crear una región que detecta los clics del usuario con la llamada a `PtInRegion`.  
  
 El `uMsg` parámetro es el identificador de mensaje de Windows está controlando. Esto le permite disponer de una función que controla un intervalo de mensajes. El `wParam` y `lParam` parámetros son los valores estándar para el mensaje que se está controlando. El parámetro bHandled permite especificar si la función controló el mensaje o no. De forma predeterminada, el valor se establece en `TRUE` para indicar que la función controló el mensaje, pero se puede establecer en `FALSE`. Esto hará que ATL a continuar buscando otra función de controlador de mensaje enviar el mensaje.  
  
## <a name="building-and-testing-the-control"></a>Compilar y probar el control  
 Ahora pruebe sus eventos. Genere el control e inicie de nuevo ActiveX Control Test Container. Esta vez, abra la ventana de registro de eventos. Para enrutar los eventos a la ventana de resultados, haga clic en **registro** desde el **opciones** menú y seleccione **registro de la ventana de salida**. Insertar el control e intente hacer clic en la ventana. Tenga en cuenta que `ClickIn` se activa si hace clic dentro del polígono rellenado, y `ClickOut` se activa al hacer clic fuera de ella.  
  
 A continuación, agregará una página de propiedades.  
  
 [Vuelva al paso 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [al paso 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)  
  
## <a name="see-also"></a>Vea también  
 [Tutorial](../atl/active-template-library-atl-tutorial.md)

