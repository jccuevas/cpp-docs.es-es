---
title: "Advertencia de las herramientas del vinculador LNK4219 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4219"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4219"
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia de las herramientas del vinculador LNK4219
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

desbordamiento de la corrección 'nombre de corrección'.'nombre de símbolo de destino' de destino está fuera de intervalo, se insertará código thunk  
  
 El vinculador insertó código thunk en situación en que no se puede ajustar la dirección o desplazamiento en la instrucción dada, porque el símbolo de destino se encuentra demasiado lejos de la ubicación de la instrucción.  
  
 Puede resultar conveniente reordenar la imagen \(usando la opción [\/ORDER](../../build/reference/order-put-functions-in-order.md), por ejemplo\) para evitar el nivel adicional de direccionamiento indirecto.