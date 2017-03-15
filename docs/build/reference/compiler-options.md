---
title: "Opciones del compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe (compilador)"
  - "opciones del compilador, C++"
  - "IPF (compilador de Visual C++)"
  - "Itanium (compilador de Visual C++)"
  - "x64 (compilador de Visual C++)"
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# Opciones del compilador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

cl.exe es una herramienta que controla el vinculador y los compiladores de Microsoft C y C\+\+. cl.exe se puede ejecutar solo en los sistemas operativos que admiten Microsoft Visual Studio.  
  
> [!NOTE]
>  Sólo puede iniciar esta herramienta desde el símbolo del sistema de [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)].  No puede iniciar desde una ventana del símbolo del sistema o desde el Explorador de archivos.  
  
 Los compiladores generan archivos objeto \(.obj\) en formato COFF \(Common Object File Format\).  El vinculador genera archivos ejecutables \(.exe\) o bibliotecas de vínculos dinámicos \(DLLs\).  
  
 Tenga en cuenta que todas las opciones del compilador distinguen entre mayúsculas y minúsculas.  
  
 Para compilar sin vinculación, utilice [\/c](../../build/reference/c-compile-without-linking.md).  
  
## Buscar una opción  
 Para buscar una opción determinada del compilador, vea las siguientes listas:  
  
-   [Opciones del compilador, por orden alfabético](../../build/reference/compiler-options-listed-alphabetically.md)  
  
-   [Opciones del compilador, por categoría](../../build/reference/compiler-options-listed-by-category.md)  
  
## Especificar opciones  
 En el tema correspondiente a cada opción del compilador se describe cómo definirla en el entorno de desarrollo.  Para obtener información sobre cómo especificar opciones fuera del entorno de desarrollo, vea:  
  
-   [Sintaxis de la línea de comandos del compilador](../../build/reference/compiler-command-line-syntax.md)  
  
-   [Archivos de comandos de CL](../../build/reference/cl-command-files.md)  
  
-   [Variables de entorno de CL](../../build/reference/cl-environment-variables.md)  
  
## Herramientas de compilación relacionadas  
 Utilice [NMAKE](../../build/nmake-reference.md) para compilar archivos de salida.  
  
 Utilice [BSCMAKE](../../build/reference/bscmake-reference.md) para agregar compatibilidad con el examen de clases.  
  
 [Las opciones del vinculador](../../build/reference/linker-options.md) también afectan a la compilación de programas.  
  
## Vea también  
 [Referencia de compilación de C\/C\+\+](../../build/reference/c-cpp-building-reference.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Compilación rápida](../../build/reference/fast-compilation.md)   
 [CL invoca el vinculador](../../build/reference/cl-invokes-the-linker.md)