---
title: "Error de las herramientas del vinculador LNK2013 | Microsoft Docs"
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
  - "LNK2013"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2013"
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK2013
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Desbordamiento de la corrección tipo de corrección.'symbol name' de destino fuera del intervalo  
  
 El vinculador no puede ajustar la dirección o desplazamiento requeridos en la instrucción dada, porque el símbolo de destino se encuentra demasiado lejos de la ubicación de la instrucción.  
  
 Se puede resolver este problema creando varias imágenes o usando la opción [\/ORDER](../../build/reference/order-put-functions-in-order.md) para que la instrucción y el destino estén más cerca.  
  
 Cuando el nombre del símbolo es un símbolo definido por el usuario \(y no uno generado por el compilador\) también pueden probarse las siguientes acciones para resolver el error:  
  
-   Cambiar la función estática para que no sea estática.  
  
-   Cambiar el nombre de la sección de código que contiene la función estática para que sea el mismo que el de la sección que realiza la llamada.  
  
 Utilice `DUMPBIN /SYMBOLS` para ver si una función es estática.