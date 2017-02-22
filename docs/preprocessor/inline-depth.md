---
title: "inline_depth | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "inline_depth_CPP"
  - "vc-pragma.inline_depth"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "inline_depth (pragma)"
  - "pragma (directivas), inline_depth"
ms.assetid: 2bba60fe-43ea-4d09-90f7-aafaba3bad07
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# inline_depth
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica la profundidad de búsqueda heurística alineada de tal forma que ninguna función se inserte si está en una profundidad \(en el gráfico de llamadas\) mayor que `n`.  
  
## Sintaxis  
  
```  
  
#pragma inline_depth( [n] )  
```  
  
## Comentarios  
 Esta directiva pragma controla la inserción de las funciones marcadas como [inline](../misc/inline-inline-forceinline.md) e [\_\_inline](../misc/inline-inline-forceinline.md), o insertadas automáticamente bajo la opción \/Ob2.  
  
 `n` puede ser un valor entre 0 y 255, donde 255 significa una profundidad ilimitada en el gráfico de llamadas y cero deshabilita la expansión alineada.  Cuando no se especifica `n`, se usa el valor predeterminado \(254\).  
  
 La directiva pragma **inline\_depth** controla el número de veces que se puede expandir una serie de llamadas a función.  Por ejemplo, si la profundidad alineada es cuatro y A llama a B y B después llama a C, las tres llamadas se expandirán alineadas.  Sin embargo, si la expansión alineada más próxima es de dos, solo se expanden A y B, y C permanece como una llamada a función.  
  
 Para utilizar esta directiva pragma, debe establecer la opción del compilador \/Ob en 1 o 2.  La profundidad establecida mediante esta directiva pragma surte efecto en la primera llamada a función después de pragma.  
  
 La profundidad alineada puede reducirse durante la expansión, pero no se puede aumentar.  Si la profundidad alineada es seis y, durante la expansión, el preprocesador encuentra una directiva pragma **inline\_depth** con un valor de ocho, la profundidad permanece en seis.  
  
 La directiva pragma **inline\_depth** no tiene ningún efecto en las funciones marcadas con `__forceinline`.  
  
> [!NOTE]
>  Las funciones recursivas pueden sustituirse alineadas con una profundidad máxima de 16 llamadas.  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [inline\_recursion](../preprocessor/inline-recursion.md)