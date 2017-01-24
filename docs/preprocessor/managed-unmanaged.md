---
title: "managed, unmanaged | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.unmanaged"
  - "managed_CPP"
  - "unmanaged_CPP"
  - "vc-pragma.managed"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "pragma administrada"
  - "pragma (directivas), administradas"
  - "pragma (directivas), no administrados"
  - "pragma no administrada"
ms.assetid: f072ddcc-e1ec-408a-8ce1-326ddb60e4a4
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# managed, unmanaged
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Habilite el control de nivel de función para compilar las funciones como administradas o no administradas.  
  
## Sintaxis  
  
```  
  
        #pragma managed  
#pragma unmanaged  
#pragma managed([push,] on | off)  
#pragma managed(pop)  
```  
  
## Comentarios  
 La opción del compilador [\/clr](../build/reference/clr-common-language-runtime-compilation.md) proporciona control de nivel de módulo para compilar las funciones como administradas o no administradas.  
  
 Una función no administrada se compilará para la plataforma nativa, a la cual Common Language Runtime pasará la ejecución de esa parte del programa.  
  
 Las funciones se compilan como administradas de forma predeterminada cuando se utiliza **\/clr**.  
  
 Al aplicar estas pragmas:  
  
-   Agregue la pragma que precede a una función, pero no dentro del cuerpo de la función.  
  
-   Agregue la pragma después de las instrucciones `#include`.  No use estas pragmas antes de las instrucciones `#include`.  
  
 El compilador omite las pragmas `managed` y `unmanaged` si no se utiliza **\/clr** en la compilación.  
  
 Cuando se crea una función de plantilla, el estado de pragma en el momento de definir la plantilla determina si es managed o unmanaged.  
  
 Para obtener más información, vea [Inicialización de ensamblados mixtos](../dotnet/initialization-of-mixed-assemblies.md).  
  
## Ejemplo  
  
```  
// pragma_directives_managed_unmanaged.cpp  
// compile with: /clr  
#include <stdio.h>  
  
// func1 is managed  
void func1() {  
   System::Console::WriteLine("In managed function.");  
}  
  
// #pragma unmanaged  
// push managed state on to stack and set unmanaged state  
#pragma managed(push, off)  
  
// func2 is unmanaged  
void func2() {  
   printf("In unmanaged function.\n");  
}  
  
// #pragma managed  
#pragma managed(pop)  
  
// main is managed  
int main() {  
   func1();  
   func2();  
}  
```  
  
  **En la función administrada.  En la función no administrada.**    
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)