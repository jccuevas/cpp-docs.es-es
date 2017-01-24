---
title: "ML Nonfatal Error A2085 | Microsoft Docs"
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
  - "A2085"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A2085"
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ML Nonfatal Error A2085
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**instrucción o registro no aceptan en el modo actual de CPU**  
  
 Se intentó utilizar una instrucción, un registro, o una palabra clave que no era válida para el modo de procesador actual.  
  
 Por ejemplo, los registros de 32 bits requieren [.386](../../assembler/masm/dot-386.md) o anteriormente.  El Control como CR0 requieren el modo privilegiado [.386P](../../assembler/masm/dot-386p.md) o anteriormente.  Este error también se producirá para **NEAR32**, **FAR32**, y las palabras clave de **Plana** , que requieren.**386** o anteriormente.  
  
## Vea también  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)