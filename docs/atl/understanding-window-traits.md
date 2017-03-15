---
title: "Understanding Window Traits | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "window traits"
ms.assetid: c90cf850-9e91-49da-9cf3-ad4efb30347d
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Understanding Window Traits
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las clases de los rasgos de la ventana proporcionan un método sencillo para normalizar los estilos utilizados para la creación de un objeto de la ventana de ATL.  Con los de la ventana son aceptados como parámetros de plantilla por [CWindowImpl](../atl/reference/cwindowimpl-class.md) y otras clases de ventana ATL como una manera de proporcionar los estilos de ventana predeterminadas en el nivel de clase.  
  
 Si el generador de una instancia de ventana no proporciona estilos explícitamente en la llamada a [Crear](../Topic/CWindowImpl::Create.md), puede utilizar una clase de los rasgos para asegurarse de que la ventana todavía se crea con estilos correctos.  Incluso puede garantizar que ciertos estilos están establecidos para todas las instancias de esta clase de ventana mientras permiten otros estilos están establecidos en una base de por instancia.  
  
## Plantillas de con los de la ventana de ATL  
 ATL proporciona dos plantillas de con los de la ventana que permiten establecer estilos predeterminados en tiempo de compilación mediante los parámetros de plantilla.  
  
|Clase|Descripción|  
|-----------|-----------------|  
|[CWinTraits](../atl/reference/cwintraits-class.md)|Utilice esta plantilla cuando se desea proporcionar los estilos de ventana predeterminadas que se usarán cuando no se especifica ningún otros estilos en la llamada a **Crear**.  Los estilos proporcionados en tiempo de ejecución tienen prioridad sobre los estilos establecidos en tiempo de compilación.|  
|[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)|Utilice esta clase cuando desee especificar los estilos que se deben establecer siempre para la clase de ventana.  Los estilos proporcionados en tiempo de ejecución se combinan con los estilos establecidos en tiempo de compilación mediante el OR bit a bit el operador.|  
  
 Además de estas plantillas, ATL proporciona varias especializaciones predefinidas de la plantilla de `CWinTraits` para combinaciones de uso general de estilos de ventana.  Vea la documentación de referencia de [CWinTraits](../atl/reference/cwintraits-class.md) para detalles completos.  
  
## rasgos personalizados de la ventana  
 En el caso improbable que la especialización de una de las plantillas proporcionadas por ATL no es suficiente y necesita crear dispone los rasgos clase, sólo deberá crear una clase que implemente dos funciones estáticas: `GetWndStyle` y **GetWndStyleEx**:  
  
 [!code-cpp[NVC_ATL_Windowing#68](../atl/codesnippet/CPP/understanding-window-traits_1.h)]  
  
 Cada una de estas funciones se pasará algún valor de estilo en tiempo de ejecución que puede utilizar para generar un nuevo estilo.  Si la clase de los rasgos de la ventana se utiliza como argumento de plantilla a una clase de ventana ATL, los valores de estilo pasados a estas funciones estáticas se aquello que se pasó como argumentos de estilo a [Crear](../Topic/CWindowImpl::Create.md).  
  
## Vea también  
 [Clases de ventanas](../atl/atl-window-classes.md)