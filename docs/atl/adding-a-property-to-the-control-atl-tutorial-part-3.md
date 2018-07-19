---
title: Agregar una propiedad al Control (ATL Tutorial, parte 3) | Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
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
ms.openlocfilehash: 7cbfb0b22579aceb5cbee196e3c5eda3079c9304
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848722"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>Agregar una propiedad al control (Tutorial de ATL, Parte 3)
`IPolyCtl` es la interfaz que contiene las propiedades y los métodos del control personalizado y agregará una propiedad a él.  
  
### <a name="to-add-a-property-using-the-add-property-wizard"></a>Para agregar una propiedad mediante el Asistente para agregar propiedades  
  
1.  En la vista de clases, expanda la rama de polígono.  
  
2.  Haga clic en IPolyCtl.  
  
3.  En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **Agregar propiedad**.  
  
     Aparecerá el Asistente para agregar propiedades.  
  
4.  En la lista desplegable de tipos de propiedades, seleccione `SHORT`.  
  
5.  Tipo *lados* como el **nombre de propiedad.**  
  
6.  Haga clic en **finalizar** para terminar de agregar la propiedad.  
  
 Cuando se agrega la propiedad a la interfaz, MIDL (el programa que compila los archivos .idl) define un `Get` método para recuperar su valor y un `Put` método para establecer un nuevo valor. Los métodos se denominan anteponiendo `put_` y `get_` al nombre de propiedad.  
  
 El Asistente para agregar propiedades agrega las líneas necesarias al archivo .idl. También agrega el `Get` y `Put` a la definición de clase en PolyCtl.h los prototipos de función y agrega una implementación vacía a PolyCtl.cpp. Puede comprobarlo abriendo PolyCtl.cpp y buscando las funciones `get_Sides` y `put_Sides`.  
  
 Aunque ahora dispone de funciones esqueletos para establecer y recuperar la propiedad, necesita un lugar donde se almacenan. Creará una variable para almacenar la propiedad y actualizar las funciones en consecuencia.  
  
#### <a name="to-create-a-variable-to-store-the-property-and-update-the-put-and-get-methods"></a>Para crear una variable para almacenar la propiedad y actualizar la put y los métodos get  
  
1.  En el Explorador de soluciones, abra PolyCtl.h y agregue la siguiente línea después de la definición de `m_clrFillColor`:  
  
     [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]  
  
2.  Establecer el valor predeterminado de `m_nSides`. Convierta la forma predeterminada un triángulo agregando una línea al constructor en PolyCtl.h:  
  
     [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]  
  
3.  Implemente el `Get` y `Put` métodos. El `get_Sides` y `put_Sides` a PolyCtl.h se han agregado las declaraciones de función. Reemplace el código de PolyCtl.cpp para `get_Sides` y `put_Sides` con el código siguiente:  
  
     [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]  
  
 El `get_Sides` método devuelve el valor actual de la `Sides` propiedad a través de la `pVal` puntero. En el `put_Sides` método, el código garantiza que el usuario establezca el `Sides` propiedad a un valor aceptable. El mínimo debe ser 3, y porque se usará una matriz de puntos para cada lado, 100 es un límite razonable para un valor máximo.  
  
 Ahora tiene una propiedad denominada `Sides`. En el paso siguiente, cambiará el código de dibujo para que lo utilicen.  
  
 [Vuelva al paso 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [con el paso 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)  
  
## <a name="see-also"></a>Vea también  
 [Tutorial](../atl/active-template-library-atl-tutorial.md)

