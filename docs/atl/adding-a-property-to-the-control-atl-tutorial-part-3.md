---
title: Agregar una propiedad al control (Tutorial de ATL, Parte 3)
ms.custom: get-started-article
ms.date: 09/26/2018
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
ms.openlocfilehash: 288dc9f5af57c02639d15a9a971419a633cfc08d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127592"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>Agregar una propiedad al control (Tutorial de ATL, Parte 3)

`IPolyCtl` es la interfaz que contiene los métodos y propiedades personalizados del control y le agregará una propiedad.

### <a name="to-add-the-property-definitions-to-your-project"></a>Para agregar las definiciones de propiedad al proyecto

1. En **vista de clases**, expanda la rama `Polygon`.

1. Haga clic con el botón secundario en `IPolyCtl`.

1. En el menú contextual, haga clic en **Agregar**y, a continuación, haga clic en **Agregar propiedad**. Aparecerá el Asistente para **Agregar propiedades** .

1. Escriba `Sides` como nombre de la **propiedad**.

1. En la lista desplegable de **tipo de propiedad**, seleccione `short`.

1. Haga clic en **Aceptar** para terminar de agregar la propiedad.

1. En **Explorador de soluciones**, abra Polygon. idl y reemplace las líneas siguientes al final de la interfaz `IPolyCtl : IDispatch`:

    ```cpp
    short get_Sides();
    void set_Sides(short value);
    ```

    con

    ```cpp
    [propget, id(1), helpstring("property Sides")] HRESULT Sides([out, retval] short *pVal);
    [propput, id(1), helpstring("property Sides")] HRESULT Sides([in] short newVal);
    ```

1. En **Explorador de soluciones**, abra PolyCtl. h y agregue las siguientes líneas después de la definición de `m_clrFillColor`:

    [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]

Aunque ahora tiene funciones esqueleto para establecer y recuperar la propiedad y una variable para almacenar la propiedad, debe implementar las funciones en consecuencia.

### <a name="to-update-the-get-and-put-methods"></a>Para actualizar los métodos GET y put

1. Establezca el valor predeterminado de `m_nSides`. Haga que la forma predeterminada sea un triángulo agregando una línea al constructor en PolyCtl. h:

    [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]

1. Implemente los métodos `Get` y `Put`. Las declaraciones de funciones `get_Sides` y `put_Sides` se han agregado a PolyCtl. h. Ahora agregue el código para `get_Sides` y `put_Sides` a PolyCtl. cpp con lo siguiente:

    [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]

El método `get_Sides` devuelve el valor actual de la propiedad `Sides` a través del puntero de `pVal`. En el método `put_Sides`, el código garantiza que el usuario está estableciendo la propiedad `Sides` en un valor aceptable. El mínimo debe ser 3, y dado que se usará una matriz de puntos para cada lado, 100 es un límite razonable para un valor máximo.

Ahora tiene una propiedad denominada `Sides`. En el paso siguiente, cambiará el código de dibujo para usarlo.

[Volver al paso 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [en el paso 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)

## <a name="see-also"></a>Consulte también

[Tutorial](../atl/active-template-library-atl-tutorial.md)
