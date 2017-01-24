---
title: "Vinculaci&#243;n en nombres con &#225;mbito de bloque | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ámbito de bloque [C++]"
  - "vinculación externa, reglas de vinculación de ámbito"
  - "vinculación [C++], reglas de vinculación de ámbito"
  - "nombres [C++], reglas de vinculación de ámbito"
  - "ámbito [C++], reglas de vinculación"
ms.assetid: 73efa91a-f761-47f7-bbd9-9f9e3508e218
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Vinculaci&#243;n en nombres con &#225;mbito de bloque
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las siguientes reglas de vinculación se aplican a los nombres con ámbito de bloque \(nombres locales\):  
  
-   Los nombres declarados como `extern` tienen vinculación externa a menos que se hayan declarado previamente como **static**.  
  
-   El resto de los nombres con ámbito de bloque no tienen vinculación.  
  
## Vea también  
 [Programa y vinculación](../cpp/program-and-linkage-cpp.md)