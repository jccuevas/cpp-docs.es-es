---
title: Cambiar el código de dibujo (Tutorial, parte 4 de ATL) | Documentos de Microsoft
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c077aca8c3276fac963eda8cdd2c413a9d6d5f5b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="changing-the-drawing-code-atl-tutorial-part-4"></a>Cambiar el código de dibujo (Tutorial de ATL, Parte 4)
De forma predeterminada, código de dibujo del control muestra un cuadrado y el texto **PolyCtl**. En este paso, cambiará el código para mostrar algo más interesante. Se incluyen las siguientes tareas:  
  
-   Modificar el archivo de encabezado  
  
-   Modificar el `OnDraw` (función)  
  
-   Agregar un método para calcular los puntos del polígono  
  
-   Inicializar el Color de relleno  
  
## <a name="modifying-the-header-file"></a>Modificar el archivo de encabezado  
 Empiece por agregar compatibilidad con las funciones matemáticas `sin` y `cos`, que se usará calcular los puntos del polígono y creando una matriz para almacenar las posiciones.  
  
#### <a name="to-modify-the-header-file"></a>Para modificar el archivo de encabezado  
  
1.  Agregue la línea `#include <math.h>` al principio del archivo PolyCtl.h. La parte superior del archivo debe tener este aspecto:  
  
     [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]  
  
2.  Una vez que se calculan los puntos del polígono, se almacenará en una matriz de tipo `POINT`, por lo que agregar la matriz después de la definición de `m_nSides` en PolyCtl.h:  
  
     [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_2.h)]  
  
## <a name="modifying-the-ondraw-method"></a>Modificar el OnDraw (método)  
 Ahora, debe modificar el `OnDraw` método en PolyCtl.h. Crea un nuevo lápiz y el pincel con la que se va a dibujar el polígono el código que se va a agregar y, a continuación, llama a la `Ellipse` y `Polygon` funciones de la API de Win32 para realizar el dibujo real.  
  
#### <a name="to-modify-the-ondraw-function"></a>Para modificar la función OnDraw  
  
1.  Reemplazar el existente `OnDraw` método en PolyCtl.h con el código siguiente:  
  
     [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]  
  
## <a name="adding-a-method-to-calculate-the-polygon-points"></a>Agregar un método para calcular los puntos del polígono  
 Agregue un método, denominado `CalcPoints`, que calculará las coordenadas de los puntos que componen el perímetro del polígono. Estos cálculos se basarán en la variable RECT que se pasa a la función.  
  
#### <a name="to-add-the-calcpoints-method"></a>Para agregar el método CalcPoints  
  
1.  Agregue la declaración de `CalcPoints` a la `IPolyCtl` sección pública de la `CPolyCtl` clase en PolyCtl.h:  
  
     [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_4.h)]  
  
     La última parte de la sección pública de la `CPolyCtl` clase tendrá un aspecto similar al siguiente:  
  
     [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_5.h)]  
  
2.  Agregue esta implementación de la `CalcPoints` función al final de PolyCtl.cpp:  
  
     [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]  
  
## <a name="initializing-the-fill-color"></a>Inicializar el Color de relleno  
 Inicializar `m_clrFillColor` con un color predeterminado.  
  
#### <a name="to-initialize-the-fill-color"></a>Para inicializar el color de relleno  
  
1.  Utilice el verde como color predeterminado agregando esta línea a la `CPolyCtl` constructor en PolyCtl.h:  
  
     [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_7.h)]  
  
 El constructor ahora este aspecto:  
  
 [!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_8.h)]  
  
## <a name="building-and-testing-the-control"></a>Compilar y probar el control  
 Vuelva a generar el control. Asegúrese de que se cierra el archivo PolyCtl.htm si está todavía abierta y, a continuación, haga clic en **Generar Polygon** en el **generar** menú. Podría ver el control una vez más en la página PolyCtl.htm, pero esta vez utilice ActiveX Control Test Container.  
  
#### <a name="to-use-the-activex-control-test-container"></a>Para usar el Control ActiveX Test Container  
  
1.  Generar e iniciar el Control ActiveX Test Container. Para obtener más información, consulte [ejemplo TSTCON: ActiveX Control Test Container](../visual-cpp-samples.md).  
  
2.  En el contenedor de prueba, en la **editar** menú, haga clic en **Insertar nuevo Control**.  
  
3.  Busque el control, que se llamará `PolyCtl Class`y haga clic en **Aceptar**. Verá un triángulo verde dentro de un círculo.  
  
 Intente cambiar el número de lados siguiendo el procedimiento siguiente. Para modificar las propiedades en una interfaz dual desde Test Container, utilice **invocar métodos**.  
  
#### <a name="to-modify-a-controls-property-from-within-the-test-container"></a>Para modificar la propiedad de un control desde el contenedor de prueba  
  
1.  En el contenedor de prueba, haga clic en **invocar métodos** en el **Control** menú.  
  
     El **invocar método** se muestra el cuadro de diálogo.  
  
2.  Seleccione el **PropPut** versión de la **lados** propiedad desde el **nombre del método** cuadro de lista desplegable.  
  
3.  Tipo de `5` en el **el valor del parámetro** cuadro, haga clic en **establecer valor**y haga clic en **Invoke**.  
  
 Tenga en cuenta que el control no cambia. Si bien cambiamos el número de caras internamente estableciendo la `m_nSides` variable, esto no producía el control vuelva a dibujar. Si cambia a otra aplicación y, a continuación, vuelva a Test Container, encontrará que el control se vuelve a dibujar y tiene el número correcto de lados.  
  
 Para corregir este problema, agregue una llamada a la `FireViewChange` función, definida en `IViewObjectExImpl`, después de establecer el número de lados. Si el control se ejecuta en su propia ventana, `FireViewChange` llamará el `InvalidateRect` método directamente. Si está ejecutando el control sin ventana, el `InvalidateRect` se llamará el método en la interfaz del contenedor sitio. Esto obliga al control a dibujarse.  
  
#### <a name="to-add-a-call-to-fireviewchange"></a>Para agregar una llamada a FireViewChange  
  
1.  Actualice el archivo PolyCtl.cpp agregando la llamada a `FireViewChange` a la `put_Sides` método. Cuando haya terminado, la `put_Sides` método debe tener el siguiente aspecto:  
  
     [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]  
  
 Después de agregar `FireViewChange`, volver a generar e inténtelo de nuevo el control en ActiveX Control Test Container. Esta vez, al cambiar el número de lados y haga clic en `Invoke`, verá que el control cambia inmediatamente.  
  
 En el paso siguiente, agregará un evento.  
  
 [Vuelva al paso 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; [al paso 5](../atl/adding-an-event-atl-tutorial-part-5.md)  
  
## <a name="see-also"></a>Vea también  
 [Tutorial](../atl/active-template-library-atl-tutorial.md)   
 [Prueba de propiedades y eventos con un contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md)

