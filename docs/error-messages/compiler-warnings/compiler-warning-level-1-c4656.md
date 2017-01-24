---
title: "Advertencia del compilador (nivel 1) C4656 | Microsoft Docs"
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
  - "C4656"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4656"
ms.assetid: b5aaef74-2320-4345-a6ae-b813881a491c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4656
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'símbolo' : el tipo de datos es nuevo, ha cambiado desde la última compilación o bien se ha definido de forma distinta en otro lugar  
  
 Se agregó o cambió un tipo de datos, convirtiéndolo en nuevo para el código fuente desde la última compilación correcta.  Editar y continuar no admite cambios en los tipos de datos existentes.  
  
 Esta advertencia viene seguida del [Error irrecuperable C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md).  Para obtener información adicional, vea [Cambios admitidos en el código](../Topic/Supported%20Code%20Changes%20\(C++\).md).  
  
### Para quitar la advertencia sin terminar la sesión de depuración actual  
  
1.  Cambie el tipo de datos a su estado anterior al error.  
  
2.  En el menú **Depurar**, elija **Aplicar cambios en el código**.  
  
### Para quitar el error sin cambiar el código fuente  
  
1.  En el menú **Depurar**, elija **Detener depuración**.  
  
2.  En el menú **Compilar**, elija **Compilar**.