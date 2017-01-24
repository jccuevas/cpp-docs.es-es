---
title: "&#191;Qu&#233; es un flujo? | Microsoft Docs"
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
  - "datos [C++], leer"
  - "leer datos [C++], programación con iostream"
  - "secuencias [C++]"
  - "secuencias [C++], en las clases iostream"
ms.assetid: a7e661e9-6cd1-4543-a9a4-c58ee9fd32f3
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &#191;Qu&#233; es un flujo?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Como C, C\+\+ no tiene capacidad integrada de entrada\/salida.  Todos los compiladores de C\+\+, sin embargo, proceden empaquetado con un paquete sistemático, orientada a objetos de E\/S, conocido como clases iostream.  La secuencia es el concepto central de las clases iostream.  Puede considerar un objeto de secuencia como archivo inteligente que actúa como origen y destino para los bytes.  Las características de una secuencia vienen determinadas por la clase y por operadores personalizados de inserción y de extracción.  
  
 A través de los controladores de dispositivo, el sistema operativo de disco trata de teclado, de la pantalla, de la impresora, y puertos de comunicación como archivos extendidos.  Las clases iostream interactúan con estos archivos extendidos.  Las clases integradas admiten leer y escribir en memoria con la sintaxis idéntica a la de la E\/S de disco, que facilita derivar clases de la secuencia.  
  
## En esta sección  
 [Alternativas de entrada\/salida](../standard-library/input-output-alternatives.md)  
  
## Vea también  
 [Programación con iostream](../standard-library/iostream-programming.md)