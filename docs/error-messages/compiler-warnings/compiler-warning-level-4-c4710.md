---
title: "Advertencia del compilador (nivel 4) C4710 | Microsoft Docs"
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
  - "C4710"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4710"
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4710
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : la función no está entre líneas  
  
 La función dada fue seleccionada para la expansión en línea, pero el compilador no realizó la expansión.  
  
 La inclusión de funciones en línea tiene lugar a discreción del compilador.  La palabra clave **inline**, al igual que la palabra clave **register**, se utiliza como sugerencia para el compilador.  El compilador utiliza la heurística para determinar si debe incluir en línea una función particular con objeto de acelerar el código, al compilar para optimizar la velocidad, o para reducir el tamaño del código al compilar para optimizar el espacio.  El compilador sólo realiza la inclusión en línea de funciones muy pequeñas al compilar para optimizar el espacio.  
  
 En algunos casos, el compilador no incluye en línea una determinada función por motivos mecánicos.  Vea [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) para obtener una lista de motivos por los que el compilador no incluye en línea una función.  
  
 De forma predeterminada, esta advertencia está desactivada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).