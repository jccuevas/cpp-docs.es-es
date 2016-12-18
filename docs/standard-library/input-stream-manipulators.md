---
title: "Manipuladores de flujos de entrada | Microsoft Docs"
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
  - "objetos de flujo de entrada"
  - "flujos de entrada, manipuladores"
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Manipuladores de flujos de entrada
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Muchos manipuladores, como [setprecision](../Topic/setprecision.md), se definen para la clase de `ios` y aplican junto a los flujos de entrada.  Pocos manipuladores, sin embargo, afectan realmente a objetos del flujo de entrada.  De los que lo hace, el más importantes son los manipuladores, `dec`, `oct`, y `hex`de base, que determinan la conversión utilizada con números del flujo de entrada.  
  
 En la recuperación, el manipulador de `hex` habilita el procesamiento de varios formatos de entrada.  Por ejemplo, c, C, 0xc, 0xC, 0Xc, y 0XC todos se interpretan como el entero decimal 12.  Cualquier carácter distinto de 0 a 9, de con f, de con f, de x, y de X finaliza la conversión numérica.  Así la secuencia `"124n5"` se convierte el número 124 con el conjunto mordido [basic\_ios::fail](../Topic/basic_ios::fail.md) .  
  
## Vea también  
 [Flujos de entrada](../standard-library/input-streams.md)