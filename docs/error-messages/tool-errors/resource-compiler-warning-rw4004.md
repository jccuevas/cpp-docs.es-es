---
title: "Advertencia del compilador de recursos RW4004 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RW4004"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RW4004"
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador de recursos RW4004
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Carácter ASCII no equivalente a código de tecla virtual  
  
 Se utilizó un literal de cadena para el código de tecla virtual en un acelerador de tipo VIRTKEY.  
  
 Esta advertencia permite continuar, pero se debe tener en cuenta que las teclas de aceleración generadas pueden no coincidir con la cadena indicada. \(VIRTKEY usa códigos de teclas distintos a los de los aceleradores ASCII.\)  
  
 Mientras los literales de cadena sean válidos sintácticamente, sólo se puede asegurar que se consigue el acelerador deseado mediante los valores **VK\_\* \#define** en WINDOWS.h.