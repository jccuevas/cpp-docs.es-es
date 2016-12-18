---
title: "Error del compilador C2220 | Microsoft Docs"
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
  - "C2220"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2220"
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2220
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

advertencia tratada como error \- no se ha generado ningún archivo objeto  
  
 [\/WX](../../build/reference/compiler-option-warning-level.md) le indica al compilador que trate todas las advertencias como errores.  Debido a que se ha producido un error, no se ha generado ningún archivo objeto o ejecutable.  
  
 Este error solo aparece cuando el marcador **\/WX** está establecido y se genera una advertencia durante la compilación.  Para corregir este error, debe eliminar cada advertencia en el proyecto.  
  
### Para corregirlo, use una de las técnicas siguientes  
  
-   Corregir los problemas que producen advertencias en el proyecto.  
  
-   Compilar en un nivel de advertencia inferior, por ejemplo, utilice **\/W3** en lugar de **\/W4**.  
  
-   Utilice una directiva pragma [warning](../../preprocessor/warning.md) para deshabilitar o suprimir una advertencia específica.  
  
-   No utilice **\/WX** para compilar.