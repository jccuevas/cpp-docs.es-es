---
title: Agregar una propiedad al Control (ATL Tutorial, parte 3) | Microsoft Docs
ms.custom: get-started-article
ms.date: 09/26/2018
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2373d2d703f18824274df158b31023669d8df945
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820478"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>Agregar una propiedad al control (Tutorial de ATL, Parte 3)

`IPolyCtl` es la interfaz que contiene las propiedades y los métodos del control personalizado y agregará una propiedad a él.

### <a name="to-add-the-property-definitions-to-your-project"></a>Para agregar las definiciones de propiedad al proyecto

1. En **vista de clases**, expanda el `Polygon` rama.

1. Haga clic en `IPolyCtl`.

1. En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **Agregar propiedad**. El **Agregar propiedad** aparecerá el asistente.

1. Tipo `Sides` como el **nombre de la propiedad**.

1. En la lista desplegable de **tipo de propiedad**, seleccione `short`.

1. Haga clic en **Aceptar** para terminar de agregar la propiedad.

1. Desde **el Explorador de soluciones**, abra Polygon.idl y reemplace las líneas siguientes al final de la `IPolyCtl : IDispatch` interfaz:

    ```cpp
    short get_Sides();
    void set_Sides(short value);
    ```

    with

    ```cpp
    [propget, id(1), helpstring("property Sides")] HRESULT Sides([out, retval] short *pVal);
    [propput, id(1), helpstring("property Sides")] HRESULT Sides([in] short newVal);
    ```

1. Desde **el Explorador de soluciones**, abra PolyCtl.h y agregue las líneas siguientes después de la definición de `m_clrFillColor`:

    [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]

Aunque ahora dispone de funciones esqueletos para establecer y recuperar la propiedad y una variable para almacenar la propiedad, debe implementar las funciones en consecuencia.

### <a name="to-update-the-get-and-put-methods"></a>Para actualizar get y put métodos

1. Establecer el valor predeterminado de `m_nSides`. Convierta la forma predeterminada un triángulo agregando una línea al constructor en PolyCtl.h:

    [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]

1. Implemente el `Get` y `Put` métodos. El `get_Sides` y `put_Sides` a PolyCtl.h se han agregado las declaraciones de función. Ahora, agregue el código para `get_Sides` y `put_Sides` a PolyCtl.cpp con lo siguiente:

    [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]

El `get_Sides` método devuelve el valor actual de la `Sides` propiedad a través de la `pVal` puntero. En el `put_Sides` método, el código garantiza que el usuario establezca el `Sides` propiedad a un valor aceptable. El mínimo debe ser 3, y porque se usará una matriz de puntos para cada lado, 100 es un límite razonable para un valor máximo.

Ahora tiene una propiedad denominada `Sides`. En el paso siguiente, cambiará el código de dibujo para que lo utilicen.

[Vuelva al paso 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [con el paso 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)

## <a name="see-also"></a>Vea también

[Tutorial](../atl/active-template-library-atl-tutorial.md)
