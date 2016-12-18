---
title: "/Zp (Alineaci&#243;n de miembros de estructura) | Microsoft Docs"
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
  - "/zp"
  - "VC.Project.VCCLCompilerTool.StructMemberAlignment"
  - "VC.Project.VCCLWCECompilerTool.StructMemberAlignment"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zp (opción del compilador) [C++]"
  - "alineación de miembros de estructura (opción del compilador)"
  - "Zp (opción del compilador)"
  - "-Zp (opción del compilador) [C++]"
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Zp (Alineaci&#243;n de miembros de estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Controla la forma en que los miembros de un struct se empaquetan en la memoria y especifica el mismo tipo de empaquetado para todos los struct de un módulo.  
  
## Sintaxis  
  
```  
/Zp[1|2|4|8|16]  
```  
  
## Comentarios  
 Si especifica esta opción, los miembros de struct a partir del primero se almacenan con el tamaño del tipo de miembro o en límites de `n` bytes \(donde `n` es 1, 2, 4, 8 o 16\), el valor que sea más pequeño de los dos.  
  
 En la siguiente tabla se describen los valores disponibles.  
  
 1  
 Empaqueta las estructuras en límites de 1 byte.  Igual que **\/Zp**.  
  
 2  
 Empaqueta las estructuras en límites de 2 bytes.  
  
 4  
 Empaqueta las estructuras en límites de 4 bytes.  
  
 8  
 Empaqueta las estructuras en límites de 8 bytes \(valor predeterminado\).  
  
 16  
 Empaqueta las estructuras en límites de 16 bytes.  
  
 No use esta opción si no ha especificado requisitos de alineación.  
  
 También puede utilizar [pack](../../preprocessor/pack.md) para controlar el empaquetamiento de structs.  Para obtener más información sobre la alineación, vea:  
  
-   [align](../../cpp/align-cpp.md)  
  
-   [\_\_alignof \(Operador\)](../../cpp/alignof-operator.md)  
  
-   [\_\_unaligned](../../cpp/unaligned.md)  
  
-   [Ejemplos de alineación de estructuras](../../build/examples-of-structure-alignment.md) \(específico de x64\)  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Generación de código**.  
  
4.  Modifique la propiedad **Alineación de miembros de struct**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)