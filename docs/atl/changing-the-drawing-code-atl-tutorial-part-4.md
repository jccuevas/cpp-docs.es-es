---
title: Cambiar el código de dibujo (Tutorial de ATL, Parte 4)
ms.custom: get-started-article
ms.date: 09/26/2018
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
ms.openlocfilehash: df89837e8f453443dc092a1b96e9c3f395fa2353
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127387"
---
# <a name="changing-the-drawing-code-atl-tutorial-part-4"></a>Cambiar el código de dibujo (Tutorial de ATL, Parte 4)

De forma predeterminada, el código de dibujo del control muestra un cuadrado y el texto **PolyCtl**. En este paso, cambiará el código para mostrar algo más interesante. Están implicadas las siguientes tareas:

- Modificar el archivo de encabezado

- Modificar la función `OnDraw`

- Agregar un método para calcular los puntos de polígono

- Inicializar el color de relleno

## <a name="modifying-the-header-file"></a>Modificar el archivo de encabezado

Comience agregando compatibilidad para las funciones matemáticas `sin` y `cos`, que se usarán para calcular los puntos de polígono y creando una matriz para almacenar las posiciones.

### <a name="to-modify-the-header-file"></a>Para modificar el archivo de encabezado

1. Agregue la línea `#include <math.h>` a la parte superior de PolyCtl. h. La parte superior del archivo debe ser similar a la siguiente:

    [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]

1. Implemente la interfaz `IProvideClassInfo` para proporcionar información de método para el control, agregando el código siguiente a PolyCtl. h. En la clase `CPolyCtl`, reemplace line:

    ```cpp
    public CComControl<CPolyCtl>
    ```

    con

    ```cpp
    public CComControl<CPolyCtl>,
    public IProvideClassInfo2Impl<&CLSID_PolyCtl, &DIID__IPolyCtlEvents, &LIBID_PolygonLib>
    ```

    y en `BEGIN_COM_MAP(CPolyCtl)`, agregue las líneas:

    ```cpp
    COM_INTERFACE_ENTRY(IProvideClassInfo)
    COM_INTERFACE_ENTRY(IProvideClassInfo2)
    ```

1. Una vez que se calculan los puntos de polígono, se almacenan en una matriz de tipo `POINT`, por lo que debe agregar la matriz después de la instrucción de definición `short m_nSides;` en PolyCtl. h:

    [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_2.h)]

## <a name="modifying-the-ondraw-method"></a>Modificar el método OnDraw

Ahora debe modificar el método `OnDraw` en PolyCtl. h. El código que va a agregar crea un nuevo lápiz y un pincel con el que dibujar el polígono y, a continuación, llama a las funciones de la API de Win32 `Ellipse` y `Polygon` para realizar el dibujo real.

### <a name="to-modify-the-ondraw-function"></a>Para modificar la función OnDraw

1. Reemplace el método de `OnDraw` existente en PolyCtl. h por el código siguiente:

    [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]

## <a name="adding-a-method-to-calculate-the-polygon-points"></a>Agregar un método para calcular los puntos de polígono

Agregue un método, llamado `CalcPoints`, que calculará las coordenadas de los puntos que componen el perímetro del polígono. Estos cálculos se basarán en la variable RECT que se pasa a la función.

### <a name="to-add-the-calcpoints-method"></a>Para agregar el método CalcPoints

1. Agregue la declaración de `CalcPoints` a la sección `IPolyCtl` público de la clase `CPolyCtl` en PolyCtl. h:

    [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_4.h)]

    La última parte de la sección pública de la clase `CPolyCtl` tendrá el siguiente aspecto:

    [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_5.h)]

1. Agregue esta implementación de la función `CalcPoints` al final de PolyCtl. cpp:

    [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]

## <a name="initializing-the-fill-color"></a>Inicializar el color de relleno

Inicializa `m_clrFillColor` con un color predeterminado.

### <a name="to-initialize-the-fill-color"></a>Para inicializar el color de relleno

1. Use el color verde como valor predeterminado; para ello, agregue esta línea al constructor `CPolyCtl` en PolyCtl. h:

    [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_7.h)]

Ahora el constructor tiene el siguiente aspecto:

[!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_8.h)]

## <a name="building-and-testing-the-control"></a>Compilar y probar el control

Vuelva a generar el control. Asegúrese de que el archivo PolyCtl. htm está cerrado si todavía está abierto y, a continuación, haga clic en **generar polígono** en el menú **compilar** . Podría ver el control una vez más en la página PolyCtl. htm, pero esta vez use el ActiveX Control Test Container.

### <a name="to-use-the-activex-control-test-container"></a>Para usar ActiveX Control Test Container

1. Compile e inicie el ActiveX Control Test Container. El [ejemplo TSTCON: ActiveX Control Test Container](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole/TstCon) se puede encontrar en github.

    > [!NOTE]
    > En el caso de los errores que impliquen `ATL::CW2AEX`, en script. cpp, reemplace `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT );` de línea por `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT.m_psz );`y `TRACE( "Source Text: %s\n", COLE2CT( bstrSourceLineText ) );` de línea por `TRACE( "Source Text: %s\n", bstrSourceLineText );`.<br/>
    > En el caso de los errores que impliquen `HMONITOR`, abra StdAfx. h en el proyecto `TCProps` y reemplace:
    > ```
    > #ifndef WINVER
    > #define WINVER 0x0400
    > #endif
    > ```
    > con
    > ```
    > #ifndef WINVER
    > #define WINVER 0x0500
    > #define _WIN32_WINNT 0x0500
    > #endif
    > ```

1. En **Test Container**, en el menú **edición** , haga clic en **Insertar nuevo control**.

1. Busque el control, al que se llamará `PolyCtl class`y haga clic en **Aceptar**. Verá un triángulo verde dentro de un círculo.

Intente cambiar el número de partes siguiendo el procedimiento siguiente. Para modificar las propiedades de una interfaz dual desde el **contenedor de prueba**, use **invocar métodos**.

### <a name="to-modify-a-controls-property-from-within-the-test-container"></a>Para modificar la propiedad de un control desde el contenedor de prueba

1. En **Test Container**, haga clic en **invocar métodos** en el menú **control** .

    Se muestra el cuadro de diálogo **invocar método** .

1. Seleccione la versión **PROPPUT** de la propiedad **Sides** en el cuadro de lista desplegable **nombre del método** .

1. Escriba `5` en el cuadro **valor de parámetro** , haga clic en **establecer valor**y haga clic en **invocar**.

Tenga en cuenta que el control no cambia. Aunque ha cambiado el número de lados internamente estableciendo la variable `m_nSides`, esto no hace que el control vuelva a dibujarse. Si cambia a otra aplicación y, a continuación, cambia a **Test Container**, observará que el control se ha vuelto a dibujar y tiene el número correcto de lados.

Para corregir este problema, agregue una llamada a la función `FireViewChange`, definida en `IViewObjectExImpl`, después de establecer el número de lados. Si el control se ejecuta en su propia ventana, `FireViewChange` llamará al método `InvalidateRect` directamente. Si el control se está ejecutando sin ventana, se llamará al método `InvalidateRect` en la interfaz de sitio del contenedor. Esto obliga a que el control se vuelva a dibujar.

### <a name="to-add-a-call-to-fireviewchange"></a>Para agregar una llamada a FireViewChange

1. Actualice PolyCtl. cpp agregando la llamada a `FireViewChange` al método `put_Sides`. Cuando haya terminado, el método de `put_Sides` debe tener el siguiente aspecto:

    [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]

Después de agregar `FireViewChange`, vuelva a generar y vuelva a intentar el control en el contenedor de pruebas de control ActiveX. Esta vez, cuando cambie el número de lados y haga clic en `Invoke`, debería ver el cambio de control inmediatamente.

En el paso siguiente, agregará un evento.

[Volver al paso 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) &#124; [en el paso 5](../atl/adding-an-event-atl-tutorial-part-5.md)

## <a name="see-also"></a>Consulte también

[Tutorial](../atl/active-template-library-atl-tutorial.md)<br/>
[Prueba de propiedades y eventos con un contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md)
