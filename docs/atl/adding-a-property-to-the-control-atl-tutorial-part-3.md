---
title: Agregar una propiedad al Control (ATL Tutorial, parte 3) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8a316ba56c551d0ee47261160058b00eca5e51a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>Agregar una propiedad al control (Tutorial de ATL, Parte 3)
`IPolyCtl`es la interfaz que contiene las propiedades y los métodos del control personalizado y lo agregará una propiedad en.  
  
### <a name="to-add-a-property-using-the-add-property-wizard"></a>Para agregar una propiedad mediante el Asistente para agregar propiedades  
  
1.  En la vista de clases, expanda la rama de polígono.  
  
2.  Haga clic en IPolyCtl.  
  
3.  En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **Agregar propiedad**.  
  
     Aparecerá el Asistente para agregar propiedades.  
  
4.  En la lista desplegable de tipos de propiedades, seleccione `SHORT`.  
  
5.  Tipo de `Sides` como el **nombre de la propiedad.**  
  
6.  Haga clic en **finalizar** para terminar de agregar la propiedad.  
  
 Cuando se agrega la propiedad a la interfaz, MIDL (el programa que compila los archivos .idl) define un `Get` método para recuperar su valor y un `Put` método para establecer un nuevo valor. Los métodos se denominan anteponiendo `put_` y `get_` al nombre de propiedad.  
  
 El Asistente para agregar propiedades agrega las líneas necesarias al archivo .idl. También agrega la `Get` y `Put` función prototipos para la definición de clase en PolyCtl.h y agrega una implementación vacía a PolyCtl.cpp. Puede comprobarlo abriendo PolyCtl.cpp y buscando las funciones `get_Sides` y `put_Sides`.  
  
 Aunque ahora dispone de funciones esqueletos para establecer y recuperar la propiedad, necesita un lugar donde se almacenan. Se creará una variable para almacenar la propiedad y actualizar las funciones en consecuencia.  
  
#### <a name="to-create-a-variable-to-store-the-property-and-update-the-put-and-get-methods"></a>Para crear una variable para almacenar la propiedad y actualizar la ubicación y los métodos get  
  
1.  En el Explorador de soluciones, abra PolyCtl.h y agregue la siguiente línea después de la definición de `m_clrFillColor`:  
  
     [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]  
  
2.  Establecer el valor predeterminado de `m_nSides`. Convierta la forma predeterminada un triángulo agregando una línea al constructor en PolyCtl.h:  
  
     [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]  
  
3.  Implemente el `Get` y `Put` métodos. El `get_Sides` y `put_Sides` declaraciones de función se agregaron a PolyCtl.h. Reemplace el código de PolyCtl.cpp para `get_Sides` y `put_Sides` con el código siguiente:  
  
     [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]  
  
 El `get_Sides` método devuelve el valor actual de la `Sides` propiedad a través de la `pVal` puntero. En el `put_Sides` método, el código garantiza el usuario establezca la `Sides` propiedad a un valor aceptable. El valor mínimo debe ser 2, y dado que se usará una matriz de puntos para cada lado, 100 es un límite razonable para un valor máximo.  
  
 Ahora tiene una propiedad denominada `Sides`. En el paso siguiente, cambiará el código de dibujo para usarlo.  
  
 [Vuelva al paso 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [Al paso 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)  
  
## <a name="see-also"></a>Vea también  
 [Tutorial](../atl/active-template-library-atl-tutorial.md)

