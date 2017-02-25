---
title: "Advertencia del compilador (nivel 1) C4657 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4657"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4657"
ms.assetid: eb750050-cea6-4ead-b80c-d5dcd4971cfc
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 1) C4657
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la expresión requiere un tipo de datos que sea nuevo desde la última compilación  
  
 El usuario agrega o cambia un tipo de datos, que se convierte en nuevo para el código fuente desde la última compilación correcta. La función Editar y continuar no admite cambios en los tipos de datos existentes.  
  
 Esta advertencia siempre irá seguida del [Error irrecuperable C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Para obtener más información, consulte [Cambios admitidos en el código](../Topic/Supported%20Code%20Changes%20\(C++\).md).  
  
### Para quitar esta advertencia sin terminar la sesión de depuración actual  
  
1.  Cambie el tipo de datos a su estado anterior al error.  
  
2.  En el menú **Depurar**, elija **Aplicar cambios en el código**.  
  
### Para quitar este error sin cambiar el código fuente  
  
1.  En el menú **Depurar**, elija **Detener depuración**.  
  
2.  En el menú **Compilar**, elija **Compilar**.