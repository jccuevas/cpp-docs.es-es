---
title: "Operadores de conversi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "index-page "
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operadores de conversión"
  - "operadores [C++], convertir"
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operadores de conversi&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Hay varios operadores de conversión específicos del lenguaje C\+\+.  Estos operadores están diseñados para quitar una parte de la ambigüedad y riesgo inherentes a las conversiones antiguas del lenguaje C.  Estos operadores son:  
  
-   [dynamic\_cast](../cpp/dynamic-cast-operator.md) Se usa para la conversión de tipos polimórficos.  
  
-   [static\_cast](../cpp/static-cast-operator.md) Se usa para la conversión de tipos no polimórficos.  
  
-   [const\_cast](../cpp/const-cast-operator.md) Se usa para quitar los atributos `const`, `volatile` y `__unaligned`.  
  
-   [reinterpret\_cast](../cpp/reinterpret-cast-operator.md) Se usa para la reinterpretación simple de bits.  
  
-   [safe\_cast](../windows/safe-cast-cpp-component-extensions.md) Se usa para producir MSIL que se puede comprobar.  
  
 Use `const_cast` y `reinterpret_cast` como último recurso, ya que estos operadores plantean los mismos peligros que las conversiones antiguas.  Sin embargo, siguen siendo necesarios para reemplazar completamente las conversiones antiguas.  
  
## Vea también  
 [Convertir](../cpp/casting.md)