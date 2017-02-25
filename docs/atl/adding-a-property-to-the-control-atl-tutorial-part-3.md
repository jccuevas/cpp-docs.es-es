---
title: "Agregar una propiedad al control (Tutorial de ATL, Parte 3) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Agregar una propiedad al control (Tutorial de ATL, Parte 3)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`IPolyCtl` es la interfaz que contiene métodos personalizados y las propiedades del control, y agregue una propiedad a él.  
  
### Para agregar una propiedad mediante el asistente para agregar propiedades  
  
1.  En la vista de clases, expanda la bifurcación Polygon.  
  
2.  Haga clic con el botón secundario IPolyCtl.  
  
3.  En el menú contextual, haga clic en **Agregar**, y haga clic en **Agregar propiedad**.  
  
     El asistente para agregar aparecerá.  
  
4.  En la lista desplegable de tipos de propiedades, seleccione `SHORT`.  
  
5.  tipo `lados` como **nombre de propiedad.**  
  
6.  Haga clic **Finalizar** a termine de agregar la propiedad.  
  
 Cuando se agrega una propiedad a la interfaz, MIDL \(el programa que los archivos de compilaciones .idl\) define un método de `Get` para recuperar su valor y un método de `Put` para establecer un nuevo valor.  Llama a los métodos anteponiendo `put_` y `get_` al nombre de propiedad.  
  
 El asistente para agregar agrega líneas necesarias al archivo .idl.  También agrega los prototipos de función de `Get` y de `Put` a la definición de clase en PolyCtl.h y agrega una implementación vacía a PolyCtl.cpp.  Puede comprobarlo PolyCtl.cpp que abre y buscando las funciones `get_Sides` y `put_Sides`.  
  
 Aunque ahora tiene funciones esquemáticas para establecer y recuperar la propiedad, necesita un lugar almacenarse.  Creará una variable para almacenar la propiedad y actualizar las funciones en consecuencia.  
  
#### Para crear una variable para almacenar la propiedad, y actualizar un título y recopilar métodos  
  
1.  En el explorador de soluciones, PolyCtl.h abierto y agregue la siguiente línea después de la definición de `m_clrFillColor`:  
  
     [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/CPP/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]  
  
2.  establezca el valor predeterminado de `m_nSides`.  Cree la forma predeterminada un triángulo agregando una línea al constructor en PolyCtl.h:  
  
     [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/CPP/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]  
  
3.  Implemente los métodos `Get` y `Put`.  las declaraciones de función de `get_Sides` y de `put_Sides` se han agregado a PolyCtl.h.  Reemplace el código de PolyCtl.cpp para `get_Sides` y `put_Sides` con el código siguiente:  
  
     [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/CPP/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]  
  
 El método de `get_Sides` devuelve el valor actual de la propiedad de `Sides` a través del puntero de `pVal` .  En el método de `put_Sides` , el código garantiza el usuario está estableciendo la propiedad de `Sides` un valor aceptable.  El mínimo debe ser 2, y como una matriz de puntos se utilizará para cada lado, 100 es un límite razonable por un valor máximo.  
  
 Ahora tiene `Sides`propiedad denominada.  En el paso siguiente, cambiará el código de dibujo para utilizarlo.  
  
 [De nuevo al paso 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [En el paso 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)  
  
## Vea también  
 [Tutorial](../atl/active-template-library-atl-tutorial.md)