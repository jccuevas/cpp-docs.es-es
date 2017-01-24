---
title: "Agregar un evento (Tutorial de ATL, Parte 5) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar un evento (Tutorial de ATL, Parte 5)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este paso, agregará `ClickIn` y un evento de `ClickOut` al control ATL.  Desencadenará el evento de `ClickIn` si los clics del usuario dentro de polígono y fire `ClickOut` si el usuario hace clic fuera de.  Las tareas de agregar un evento son los siguientes:  
  
-   Agregar métodos de `ClickIn` y de `ClickOut`  
  
-   Generar la biblioteca de tipos  
  
-   Implementar las interfaces de punto de Conexión  
  
## Agregar métodos de ClickIn y de ClickOut  
 Cuando creó el control ATL en el paso 2, se activa la casilla de **Puntos de conexión** .  Esto creó la interfaz de `_IPolyCtlEvents` en el archivo de Polygon.idl.  Observe que el nombre de la interfaz comienza con un subrayado.  Esto es una convención para indicar que la interfaz es una interfaz interna.  Así, los programas que permiten examinar objetos COM pueden decidir no mostrar la interfaz al usuario.  Observe también que selecciona **Puntos de conexión** agregó la línea siguiente en el archivo de Polygon.idl para indicar que `_IPolyCtlEvents` es la interfaz predeterminada de origen:  
  
 `[default, source] dispinterface _IPolyCtlEvents;`  
  
 El atributo source indica que el control es el origen de las notificaciones, así que llamará esta interfaz en el contenedor.  
  
 Agregue los métodos de `ClickIn` y de `ClickOut` a la interfaz de `_IPolyCtlEvents` .  
  
#### Para agregar métodos de ClickIn y de ClickOut  
  
1.  En la vista de clases, expanda Polygon y PolygonLib para mostrar \_IPolyCtlEvents.  
  
2.  \_IPolyCtlEvents Del botón secundario.  En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar método**.  
  
3.  Seleccione **Tipo devuelto** de `void`.  
  
4.  ENTRAR `ClickIn` en el cuadro de **Nombre del método** .  
  
5.  En **Atributos del parámetro**, seleccione el cuadro de **en** .  
  
6.  Seleccione **Tipo de parámetro** de `LONG`.  
  
7.  Escriba `x` como **Nombre del parámetro**, y haga clic en **Agregar**.  
  
8.  Repita los pasos 5 a 7, esta vez para **Nombre del parámetro** de y.  
  
9. Haga clic en **Siguiente**.  
  
10. Tipo `método ClickIn` como **helpstring**.  
  
11. Haga clic en **Finalizar**.  
  
12. Repita los pasos anteriores para definir un método de `ClickOut` con los mismos parámetros `x` y `y`, mismo **Atributos del parámetro** de `LONG` y el mismo tipo de valor devuelto de `void` .  
  
 Compruebe el archivo de Polygon.idl para comprobar que el código se agregaron a la interfaz dispinterface de `_IPolyCtlEvents` .  
  
 El dispinterface de `_IPolyCtlEvents` en el archivo de Polygon.idl ahora debería ser similar a:  
  
 [!code-cpp[NVC_ATL_Windowing#56](../atl/codesnippet/CPP/adding-an-event-atl-tutorial-part-5_1.idl)]  
  
 Los métodos de `ClickIn` y de `ClickOut` toman las coordenadas x e y del punto hizo clic como parámetros.  
  
## Generar la biblioteca de tipos  
 Generar la biblioteca de tipos en este punto, porque el asistente de punto de Conexión utilizarla para obtener la información que necesita crear una interfaz de punto de conexión y una interfaz de contenedor de punto de conexión para el control.  
  
#### Para generar la biblioteca de tipos  
  
1.  Recompile el proyecto.  
  
     O bien  
  
2.  Haga clic con el botón secundario en el archivo de Polygon.idl en el explorador de soluciones y haga clic en **Compilar** en el menú contextual.  
  
 Esto creará el archivo de Polygon.tlb, que es la biblioteca de tipos.  El archivo de Polygon.tlb no está visible en el explorador de soluciones, porque es un archivo binario y no se puede ver o modificarse.  
  
## Implementar las interfaces de punto de Conexión  
 Implemente una interfaz de punto de conexión y una interfaz de contenedor de punto de conexión para el control.  En COM, los eventos se implementan a través del mecanismo de puntos de conexión.  Para recibir los eventos de un objeto COM, un contenedor establece una conexión asesor anclar que el objeto COM implementa.  Porque un objeto COM puede tener varios puntos de conexión, el objeto COM también implementa una interfaz de contenedor de punto de conexión.  a través de esta interfaz, el contenedor puede determinar que los puntos de conexión se admiten.  
  
 La interfaz que implementa un punto de conexión se denomina `IConnectionPoint`, y la interfaz que implementa un contenedor de punto de conexión se denomina `IConnectionPointContainer`.  
  
 Para ayudar a implementar `IConnectionPoint`, utilizará el asistente para implementar.  Este asistente representa la interfaz de `IConnectionPoint` leyendo la biblioteca de tipos e implementa una función para cada evento que se desencadena.  
  
#### Para utilizar el asistente para implementar  
  
1.  En la vista de clases, haga clic con el botón secundario en la clase `CPolyCtl`de implementación del control.  
  
2.  En el menú contextual, haga clic en **Agregar**, y haga clic en **Agregar punto de conexión**.  
  
3.  `_IPolyCtlEvents` seleccione de **Interfaces de origen** lo muestra y haga doble clic en para agregarlo a la columna de **Implementar puntos de conexión** .  Haga clic en **Finalizar**.  Una clase de proxy para el punto de conexión se representará, en este caso, `CProxy_IPolyCtlEvents`.  
  
 Si examina el archivo de \_IPolyCtlEvents\_CP.h en el explorador de soluciones, verá que tiene una clase denominada `CProxy_IPolyCtlEvents` que deriva de `IConnectionPointImpl`.  \_IPolyCtlEvents\_CP.h también define los dos métodos `Fire_ClickIn` y `Fire_ClickOut`, que toman los dos parámetros de coordenadas.  Se llama a estos métodos cuando desee desencadenar un evento del control.  
  
 El asistente `CProxy_PolyEvents` también agregado y `IConnectionPointContainerImpl` a la lista de herencia múltiple del control.  El asistente `IConnectionPointContainer` también expuesto automáticamente agregando entradas correspondientes al mapa COM.  
  
 Termine que implementa el código admitir eventos.  Ahora, agregue el código para desencadenar los eventos en el momento adecuado.  Recuerde, se va a desencadenar un evento de `ClickIn` o de `ClickOut` cuando el usuario hace clic en el botón primario en el control.  Para averiguar cuando el usuario hace clic en el botón, agregue un controlador para el mensaje de `WM_LBUTTONDOWN` .  
  
#### Para agregar un controlador para el mensaje de WM\_LBUTTONDOWN  
  
1.  En la vista de clases, haga clic con el botón secundario en la clase y haga clic en **Propiedades** de CPolyCtl en el menú contextual.  
  
2.  En la ventana de **Propiedades** , haga clic en el icono de **Mensajes** y haga clic en `WM_LBUTTONDOWN` de la lista a la izquierda.  
  
3.  En la lista desplegable que aparece, haga clic **\<Add\>  OnLButtonDown**.  La declaración del controlador de `OnLButtonDown` se agregará a PolyCtl.h, y la implementación del controlador se agregará a PolyCtl.cpp.  
  
 A continuación, modifica el controlador.  
  
#### Para modificar el método de OnLButtonDown  
  
1.  Cambie el código que incluye el método de `OnLButtonDown` en PolyCtl.cpp \(que elimina cualquier codificados colocado por el asistente\) para que sigue:  
  
     [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/CPP/adding-an-event-atl-tutorial-part-5_2.cpp)]  
  
 Este código utiliza los puntos calculados en función de `OnDraw` para crear una región que detecte los clics del mouse del usuario con la llamada a `PtInRegion`.  
  
 El parámetro de `uMsg` es el id. de mensaje de Windows que es administrado.  Esto le permite tener una función que controla un intervalo de mensajes.  `wParam` y los parámetros de `lParam` son los valores estándar para el mensaje que es administrado.  El parámetro bHandled permite especificar si la función manejara el mensaje o no.  De forma predeterminada, el valor se establece en `TRUE` para indicar que la función controló el mensaje, pero puede establecerlo en `FALSE`.  Esto hará ATL para continuar buscando otra función de controlador de mensajes para enviar el mensaje a.  
  
## Compilar y probar el Control  
 Ahora pruebe sus eventos.  Compile el control y inicie el contenedor del control ActiveX de nuevo.  Esta vez, ve la ventana del registro de eventos.  Para distribuir eventos a la ventana de resultados, haga clic **Registro** de menú de **Opciones recomendadas** y seleccione **Registrar en la ventana de resultados**.  Inserte el control e intente que haga clic en la ventana.  Observe que `ClickIn` se desencadena si hace clic dentro del polígono relleno, y se inicia `ClickOut` cuando se hace clic fuera de él.  
  
 A continuación, agregará una página de propiedades.  
  
 [De nuevo al paso 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [En el paso 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)  
  
## Vea también  
 [Tutorial](../atl/active-template-library-atl-tutorial.md)