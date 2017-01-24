---
title: "Error de las herramientas del vinculador LNK2039 | Microsoft Docs"
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
  - "LNK2039"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2039"
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK2039
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

importar el tipo de clase de referencia '\<\>' que se define en another.obj; debe ser importado o definir, pero no ambos  
  
 La clase`type` '\<\>' de referencia se importa al archivo especificado .obj pero también se define en otro archivo .obj.  Esta situación puede provocar el error en tiempo de ejecución u otro comportamiento inesperado.  
  
### Para corregir este error  
  
1.  Compruebe si '`type`' se debe definir en el otro archivo y comprobación .obj si debe estar importada del archivo de .winmd.  
  
2.  Quite la definición o la importación.  
  
## Vea también  
 [Errores y advertencias de las herramientas del vinculador](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)   
 [Error de las herramientas del vinculador LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)