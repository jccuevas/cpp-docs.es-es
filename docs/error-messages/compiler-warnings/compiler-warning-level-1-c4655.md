---
title: "Advertencia del compilador (nivel 1) C4655 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4655"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4655"
ms.assetid: 540f2c7a-e4a1-49af-84b4-03eeea1bbf41
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4655
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**'**   
 ***symbol* ': el tipo de variable es nuevo desde la última compilación o bien se ha definido de forma distinta en otro lugar.**  
  
 Ha cambiado o agregado un nuevo tipo de datos desde la última compilación correcta. La función Editar y continuar no admite cambios en los tipos de datos existentes.  
  
 Esta advertencia va seguida de un [Error irrecuperable C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Para obtener más información, consulte [Cambios admitidos en el código](../Topic/Supported%20Code%20Changes%20\(C++\).md).  
  
### Para quitar la advertencia sin terminar la sesión de depuración actual  
  
1.  Cambie el tipo de datos a su estado anterior al error.  
  
2.  En el menú **Depurar**, elija **Aplicar cambios en el código**.  
  
### Para quitar la advertencia sin cambiar el código fuente  
  
1.  En el menú **Depurar**, elija **Detener depuración**.  
  
2.  En el menú **Compilar**, elija **Compilar**.