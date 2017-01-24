---
title: "Tipo double | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "double (tipo de datos)"
  - "mantisas, variables de punto flotante"
  - "portabilidad [C++], tipo double"
  - "tipo double"
ms.assetid: 17c85b24-1475-4d41-a03c-ddf2d6561d34
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tipo double
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los valores de precisión doble con tipo double tienen 8 bytes.  El formato es similar al formato float, excepto que tiene un exponente 1023 que supera los 11 bits y una mantisa de 52 bits, más el bit de orden superior implícito.  Este formato proporciona un intervalo de aproximadamente 1,7E–308 a 1,7E\+308 para el tipo double.  
  
 **Específicos de Microsoft**  
  
 El tipo double contiene 64 bits: 1 para el signo, 11 para el exponente y 52 para la mantisa.  El intervalo es \+\/\-1,7E308 con al menos 15 dígitos de precisión.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md)