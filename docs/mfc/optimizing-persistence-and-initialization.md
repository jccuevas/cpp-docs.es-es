---
title: "Optimizar la persistencia y la inicializaci&#243;n | Microsoft Docs"
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
  - "controles ActiveX en MFC, optimizar"
  - "optimización, controles ActiveX"
  - "optimizar el rendimiento, controles ActiveX"
  - "rendimiento, controles ActiveX"
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Optimizar la persistencia y la inicializaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

De forma predeterminada, la persistencia y la inicialización de un control se controlan mediante la función miembro de `DoPropExchange` .  En un control típico, esta función contiene las llamadas a las funciones de **PX\_** \(`PX_Color`, `PX_Font`, etc.\), una para cada propiedad.  
  
 Este enfoque tiene la ventaja de que una implementación única de `DoPropExchange` se puede utilizar para la inicialización, para la persistencia en formato binario, y para la persistencia en el supuesto formato “contenedor de propiedades” utilizado por algunos contenedores.  Esta función proporciona toda la información sobre las propiedades y sus valores predeterminados en un lugar apropiado.  
  
 Sin embargo, esta generalidad llega a expensas de la eficacia.  Las funciones de **PX\_** obtiene su flexibilidad con las implementaciones de varias capas que inherentemente menos eficaces que más directos, pero el menos flexibles, enfoques.  Además, si un control pasa un valor predeterminado a una función de **PX\_** , ese valor predeterminado se debe proporcionar cada vez, incluso en situaciones en las que el valor no se puede utilizar necesariamente.  Si se genera el valor predeterminado es una tarea no trivial \(por ejemplo, cuando se obtiene el valor de una propiedad de ambiente\), se hace que el complemento, trabajo innecesario en caso de que el valor no se utiliza.  
  
 Puede mejorar el rendimiento binario de persistencia de control reemplazando la función de `Serialize` del control.  La implementación predeterminada de esta función miembro realiza una llamada a la función de `DoPropExchange` .  Invalidandola, puede proporcionar una implementación más sencilla para persistencia binaria.  Por ejemplo, considere esta función de `DoPropExchange` :  
  
 [!code-cpp[NVC_MFC_AxOpt#1](../mfc/codesnippet/CPP/optimizing-persistence-and-initialization_1.cpp)]  
  
 Para mejorar el rendimiento de persistencia binaria de este control, puede reemplazar la función de `Serialize` como sigue:  
  
 [!code-cpp[NVC_MFC_AxOpt#2](../mfc/codesnippet/CPP/optimizing-persistence-and-initialization_2.cpp)]  
  
 La variable local de `dwVersion` se puede utilizar para detectar la versión de estado persistente de control cargada o guardada.  Puede utilizar esta variable en lugar de llamar a [CPropExchange::GetVersion](../Topic/CPropExchange::GetVersion.md).  
  
 Para guardar un poco espacio en el formato persistente para una propiedad de **bool** \(y mantenerla compatible con el formato generado por `PX_Bool`\), puede almacenar la propiedad como **byte**, como sigue:  
  
 [!code-cpp[NVC_MFC_AxOpt#3](../mfc/codesnippet/CPP/optimizing-persistence-and-initialization_3.cpp)]  
  
 Observe que en el caso de carga, una variable temporal se utiliza a continuación el valor asignado, en lugar de `m_boolProp` de inicio a una referencia de **byte** .  La técnica de fotograma produciría un byte de `m_boolProp` que se ha modificado, ya que los bytes restantes desinicializó.  
  
 Para el mismo control, puede optimizar la inicialización de control reemplazando [COleControl::OnResetState](../Topic/COleControl::OnResetState.md) como sigue:  
  
 [!code-cpp[NVC_MFC_AxOpt#4](../mfc/codesnippet/CPP/optimizing-persistence-and-initialization_4.cpp)]  
  
 Aunque `Serialize` y `OnResetState` han reemplazado, la función de `DoPropExchange` se debe mantener intacta porque todavía se utiliza para la persistencia en el formato del contenedor de propiedades.  Es importante mantener los tres de estas funciones para asegurarse de que el control administra sus propiedades de forma coherente, independientemente de las que el mecanismo de persistencia el contenedor utiliza.  
  
## Vea también  
 [Controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md)