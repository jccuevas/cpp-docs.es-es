---
title: "Advertencia del compilador C4746 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
caps.latest.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 2
---
# Advertencia del compilador C4746
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el acceso volatile '\<de expresión\>' se bajo \/volatile: \[ISO&#124;valor de MS\]; considere utilizar funciones intrínsecas de \_\_iso\_volatile\_load\/store.  
  
 Se emite C4746 siempre que una variable volatile se almacenan directamente.  Está diseñado para ayudar a los desarrolladores a identificar las ubicaciones de código afectadas por el modelo específico de volatile especificado actualmente \(que se puede controlar con la opción del compilador [\/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) \).  En particular, puede ser útil para localizar de barreras compilador\- generadas de memoria de hardware cuando se utiliza \/volatile:ms .  
  
 Función intrínseca de \_\_iso\_volatile\_load\/store se pueden utilizar explícitamente para tener acceso a memoria volátil sin verse afectado por el modelo volatile.  Mediante estos intrínseco no desencadenará C4746.  
  
 De forma predeterminada, esta advertencia está desactivada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).