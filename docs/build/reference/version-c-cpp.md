---
title: "VERSION (C/C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VERSION"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VERSION (instrucción de archivo .def)"
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# VERSION (C/C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Indica a LINK que ponga un número de versión en el encabezado del archivo .exe o DLL.  
  
```  
VERSION major[.minor]  
```  
  
## Comentarios  
 Los argumentos *major* y *minor* son números decimales en el intervalo de 0 a 65535.  El valor predeterminado es la versión 0.0.  
  
 Un modo equivalente de especificar un número de versión es con la opción [Información de versión](../../build/reference/version-version-information.md) \(\/VERSION\).  
  
## Vea también  
 [Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)