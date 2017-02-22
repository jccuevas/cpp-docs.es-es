---
title: "Advertencia del compilador (nivel 4) C4234 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4234"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4234"
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 4) C4234
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se ha utilizado una extensión no estándar: la palabra clave 'palabraclave' se reserva para uso posterior  
  
 El compilador aún no implementa la palabra clave utilizada.  
  
 Esta advertencia suele convertirse automáticamente en un error.  Si desea modificar este comportamiento, use [\#pragma warning](../../preprocessor/warning.md).  Por ejemplo, para convertir C4234 en una advertencia de nivel 4:  
  
```  
#pragma warning(2:4234)  
```  
  
 en el archivo de código fuente.