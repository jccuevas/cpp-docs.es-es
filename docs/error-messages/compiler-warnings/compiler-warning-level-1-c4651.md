---
title: "Advertencia del compilador (nivel 1) C4651 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4651"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4651"
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 1) C4651
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se especificó 'definición' para el encabezado precompilado pero no para la compilación actual  
  
 Se especificó la definición al generar el encabezado precompilado, pero no en esta compilación.  
  
 La definición tendrá vigor en el encabezado precompilado, pero no en el resto del código.  
  
 Si un encabezado precompilado se generara con \/DSYMBOL, el compilador mostrará esta advertencia si la opción \/Yu no tiene \/DSYMBOL.  Agregando \/DSYMBOL a la línea de comandos de \/Yu se corrige esta advertencia.