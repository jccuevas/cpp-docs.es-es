---
title: "Error matem&#225;tico M6202 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "M6202"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "M6202"
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error matem&#225;tico M6202
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : error \_SING  
  
 Un argumento para la función dada es un valor de singularidad para esta función.  La función no está definida para ese argumento.  
  
 Este error invoca la función `_matherr` con el nombre de la función, sus argumentos y el tipo de error.  Se puede volver a escribir la función `_matherr` para personalizar el control de algunos errores matemáticos de punto flotante en tiempo de ejecución.