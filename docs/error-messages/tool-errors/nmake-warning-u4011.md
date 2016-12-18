---
title: "Advertencia de NMAKE U4011 | Microsoft Docs"
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
  - "U4011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U4011"
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de NMAKE U4011
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'destino' : no están disponibles todos los dependientes; destino no compilado  
  
 Un dependiente del destino dado no existe o no está actualizado, y un comando para actualizar el dependiente ha devuelto un código de salida distinto de cero.  La opción \/K indicó a NMAKE que continuara procesando partes no relacionadas de la compilación y que enviara un código de salida 1 cuando finalizara la sesión.  
  
 Esta advertencia va precedida de la advertencia [U4010](../../error-messages/tool-errors/nmake-warning-u4010.md) para cada dependiente que no se ha podido crear o actualizar.