---
title: "Error de las herramientas del vinculador LNK2017 | Microsoft Docs"
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
  - "LNK2017"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2017"
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK2017
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

reubicación de 'símbolo' a 'segmento' no válida sin \/LARGEADDRESSAWARE:NO  
  
 Se intenta compilar una imagen de 64 bits con direcciones de 32 bits.  Para hacerlo, deberá:  
  
-   Usar una dirección de carga fija.  
  
-   Restringir el tamaño de la imagen a 3 GB.  
  
-   Especificar [\/largeaddressaware:no](../../build/reference/largeaddressaware-handle-large-addresses.md).