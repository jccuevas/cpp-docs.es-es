---
title: "ML Nonfatal Error A2006 | Microsoft Docs"
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
  - "A2006"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A2006"
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ML Nonfatal Error A2006
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**símbolo no definido: identificador**  
  
 Se intentó utilizar un símbolo que no estaba definido.  
  
 Uno de los siguientes podría haberse producido:  
  
-   Un símbolo no está definido.  
  
-   Un campo no es un miembro de la estructura especificada.  
  
-   Un símbolo está definido en un archivo de inclusión no incluido.  
  
-   Un símbolo externo se utilizó sin una directiva de [EXTERN](../../assembler/masm/extern-masm.md) o de [EXTERNDEF](../../assembler/masm/externdef.md) .  
  
-   Un nombre de símbolo estaba mal escrito.  
  
-   Una etiqueta de código local se hizo referencia fuera del ámbito.  
  
## Vea también  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)