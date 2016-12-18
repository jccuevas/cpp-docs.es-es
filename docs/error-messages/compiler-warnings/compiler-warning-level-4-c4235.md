---
title: "Advertencia del compilador (nivel 4) C4235 | Microsoft Docs"
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
  - "C4235"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4235"
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4235
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se ha utilizado una extensión no estándar : la palabra clave 'palabra clave' no se admite en esta arquitectura  
  
 El compilador aún no admite la palabra clave utilizada.  
  
 Esta advertencia suele convertirse automáticamente en un error.  Si desea modificar este comportamiento, use [\#pragma warning](../../preprocessor/warning.md).  Por ejemplo, para convertir C4235 en una advertencia de nivel 2, utilice la siguiente línea de código  
  
```  
#pragma warning(2:4235)  
```  
  
 en el archivo de código fuente.