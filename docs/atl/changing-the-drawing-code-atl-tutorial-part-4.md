---
title: "Cambiar el c&#243;digo de dibujo (Tutorial de ATL, Parte 4) | Microsoft Docs"
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
helpviewer_keywords: 
  - "_ATL_MIN_CRT (macro)"
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
caps.latest.revision: 18
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Cambiar el c&#243;digo de dibujo (Tutorial de ATL, Parte 4)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

De forma predeterminada, el código de dibujo del control muestra un cuadrado y el texto **PolyCtl**.  En este paso, cambiará el código para mostrar algo más interesante.  Las siguientes tareas relacionadas:  
  
-   Modificar el archivo de encabezado  
  
-   Modificar la función de `OnDraw`  
  
-   Agregar un método para calcular los puntos Polygon  
  
-   Inicializar el color de relleno  
  
## Modificar el archivo de encabezado  
 El inicio agregando compatibilidad para las funciones matemáticas `sin` y `cos`, que se utilizarán calcula los puntos del polígono, y creando una matriz para almacenar posiciones.  
  
#### Para modificar el archivo de encabezado  
  
1.  Agregue la línea `#include <math.h>` a la parte superior de PolyCtl.h.  La parte superior del archivo debe ser similar a:  
  
     [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]  
  
2.  Una vez que se calculan los puntos del polígono, se almacenan en una matriz de `POINT`escrito, así que agregue la matriz después de la definición de `m_nSides` en PolyCtl.h:  
  
     [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_2.h)]  
  
## Modificar el método de OnDraw  
 Ahora debe modificar el método de `OnDraw` en PolyCtl.h.  El código que creará un nuevo lápiz y el pincel con el que para dibujar el polígono, y después llama a `Ellipse` y la API Win32 de `Polygon` funciona para realizar el dibujo real.  
  
#### Para modificar la función de OnDraw  
  
1.  Reemplace el método existente de `OnDraw` en PolyCtl.h con el código siguiente:  
  
     [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]  
  
## Agregar un método para calcular los puntos Polygon  
 Agregue un método, denominado `CalcPoints`, que calculará las coordenadas de puntos que componen el borde del polígono.  Estos cálculos se basan en la variable RECT que se pasa a la función.  
  
#### Para agregar el método de CalcPoints  
  
1.  Agregue la declaración de `CalcPoints` a la sección pública de `IPolyCtl` de la clase de `CPolyCtl` en PolyCtl.h:  
  
     [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_4.h)]  
  
     La última parte de la sección public de la clase de `CPolyCtl` será similar a:  
  
     [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_5.h)]  
  
2.  Agregue esta implementación de la función de `CalcPoints` al final de PolyCtl.cpp:  
  
     [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]  
  
## Inicializar el color de relleno  
 Inicializa `m_clrFillColor` con el color predeterminado.  
  
#### Para inicializar el color de relleno  
  
1.  Utilice el verde como color predeterminado agregando esta línea al constructor de `CPolyCtl` en PolyCtl.h:  
  
     [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_7.h)]  
  
 El constructor ahora tiene este aspecto:  
  
 [!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_8.h)]  
  
## Compilar y probar el Control  
 Recompile el control.  Asegúrese de que el archivo PolyCtl.htm cerrado si todavía está abierto, y después haga clic en **Compilar polígono** en el menú de **Compilación** .  Puede ver el control de nuevo de la página de PolyCtl.htm, pero este uso de nuevo el ActiveX control test container.  
  
#### Para utilizar el ActiveX control test container  
  
1.  Compilar e inicie el contenedor del control ActiveX.  Para obtener más información, vea [Ejemplo TSTCON: ActiveX control test container](../top/visual-cpp-samples.md).  
  
2.  En contenedor de prueba, en el menú de **Editar** , haga clic **Nueva Control INSERT**.  
  
3.  Busque el control, que se llama `PolyCtl Class`, y haga clic **Aceptar**.  Verá un triángulo verde dentro de un círculo.  
  
 Pruebe a cambiar el número de lados siguiendo el procedimiento siguiente.  Modificar propiedades de una interfaz dual dentro del contenedor de prueba, utilice **Invoke Methods**.  
  
#### Para modificar la propiedad de un control dentro del contenedor de prueba  
  
1.  En contenedor de prueba, haga clic en **Invocar métodos** en el menú de **Control** .  
  
     Aparecerá el cuadro de diálogo **Invocar método** .  
  
2.  Seleccione la versión de **PropPut** de la propiedad de **Sides** de cuadro de lista desplegable de **Nombre del método** .  
  
3.  Escriba `5` en el cuadro de **Valor del parámetro** , haga clic en **Establecer valor**, y haga clic en **Invocar**.  
  
 Observe que el control no cambia.  Aunque ha modificado el número de lados internamente estableciendo la variable de `m_nSides` , no ejecutó el control para que vuelva a.  Si cambia a otra aplicación y vuelve al contenedor de prueba, verá que el control ha repintado y tiene el número correcto de lados.  
  
 Para corregir este problema, agregue una llamada a la función de `FireViewChange` , definida en `IViewObjectExImpl`, después de establecer el número de lados.  Si el control se ejecuta en su propia ventana, `FireViewChange` llamará al método de `InvalidateRect` directamente.  Si el control se ejecuta sin ventana, el método de `InvalidateRect` se en la interfaz del sitio del contenedor.  Esto obliga al control para representar.  
  
#### Para agregar una llamada a FireViewChange  
  
1.  Actualice PolyCtl.cpp si la llamada a `FireViewChange` al método de `put_Sides` .  Cuando haya finalizado, el método de `put_Sides` debe ser similar a:  
  
     [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/CPP/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]  
  
 Después de agregar `FireViewChange`, recompile y pruebe el control de nuevo en el contenedor de prueba del control ActiveX.  Esta vez cuando cambia el número de lados y haga clic en `Invoke`, debería ver el cambio de control inmediatamente.  
  
 En el paso siguiente, agregará un evento.  
  
 [De nuevo al paso 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; [En el paso 5](../atl/adding-an-event-atl-tutorial-part-5.md)  
  
## Vea también  
 [Tutorial](../atl/active-template-library-atl-tutorial.md)   
 [Probar propiedades y eventos con un contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md)