---
title: "Advertencia de NMAKE U4010 | Microsoft Docs"
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
  - "U4010"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U4010"
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de NMAKE U4010
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'destino' : error al compilar; se especificó \/K, continuando  
  
 Un comando del bloque de comandos para el destino dado ha devuelto un código de salida distinto de cero.  La opción \/K indicó a NMAKE que continuara procesando partes no relacionadas de la compilación y que enviara un código de salida 1 cuando finalizara la sesión.  
  
 Si el destino dado es un dependiente de otro destino, NMAKE generará la advertencia [U4011](../../error-messages/tool-errors/nmake-warning-u4011.md) después de esta advertencia.