---
title: "MFC ActiveX Controls: Returning Error Codes From a (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "errores [C++], códigos de error del control ActiveX"
  - "FireError (método)"
  - "GetNotSupported (método)"
  - "controles ActiveX en MFC, códigos de error"
  - "SCODE, controles ActiveX en MFC"
  - "SetNotSupported (método), utilizar"
  - "ThrowError (método)"
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX Controls: Returning Error Codes From a (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe cómo devolver códigos de error de un método de control ActiveX.  
  
 Para indicar que se ha producido un error en un método, debe utilizar la función miembro de [COleControl::ThrowError](../Topic/COleControl::ThrowError.md) , que toma `SCODE` \(código de estado\) como parámetro.  Puede utilizar `SCODE` predefinido o definir uno de sea propietario.  
  
> [!NOTE]
>  `ThrowError` está diseñado para usarse sólo como medio para devolver un error dentro de una propiedad obtiene o establece la función o método de automatización.  Estos son los únicos veces que el controlador de excepciones adecuado aparecerá en la pila.  
  
 Las funciones auxiliares existen para la mayoría de s predefinida común de `SCODE`, como [COleControl::SetNotSupported](../Topic/COleControl::SetNotSupported.md), [COleControl::GetNotSupported](../Topic/COleControl::GetNotSupported.md), y [COleControl::SetNotPermitted](../Topic/COleControl::SetNotPermitted.md).  
  
 Para obtener una lista de s predefinida de `SCODE`e instrucciones en la definición de s personalizada de `SCODE`, vea la sección [Controlar errores en el control ActiveX se](../mfc/mfc-activex-controls-advanced-topics.md) en Controles ActiveX: Temas avanzados.  
  
 Para obtener más información sobre excepciones de informe en otras áreas de código, vea [COleControl::FireError](../Topic/COleControl::FireError.md) y la sección [Controlar errores en el control ActiveX se](../mfc/mfc-activex-controls-advanced-topics.md) en Controles ActiveX: Temas avanzados.  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)