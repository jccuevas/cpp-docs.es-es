---
title: "/LN (Crear un m&#243;dulo MSIL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/LN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LN (opción del compilador) [C++]"
  - "-LN (opción del compilador) [C++]"
ms.assetid: 4f38f4f4-3176-4caf-8200-5c7585dc1ed3
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# /LN (Crear un m&#243;dulo MSIL)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica que no se debe insertar un manifiesto del ensamblado en el archivo de salida.  
  
## Sintaxis  
  
```  
/LN  
```  
  
## Comentarios  
 De forma predeterminada, **\/LN** está desactivado \(se inserta un manifiesto del ensamblado en el archivo de salida\).  
  
 Si se utiliza **\/LN**, se debe usar también una de las opciones de [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 Un programa administrado que no tiene metadatos de ensamblado en el manifiesto se denomina módulo.  Si compila con [\/c \(Compilar sin vincular\)](../../build/reference/c-compile-without-linking.md) y **\/LN**, especifique [\/NOASSEMBLY \(Crear un módulo MSIL\)](../../build/reference/noassembly-create-a-msil-module.md) en la fase del vinculador para crear el archivo de salida.  
  
 Tal vez desee crear módulos si va a utilizar un enfoque basado en componentes para generar ensamblados.  Es decir, puede crear tipos y compilarlos en módulos.  A continuación, puede generar un ensamblado a partir de algunos de los módulos.  Para obtener más información sobre cómo crear ensamblados a partir de módulos, vea [.Archivos netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md) o [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).  
  
 La extensión de archivo predeterminada para un módulo es .netmodule.  
  
 En versiones de [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] anteriores a Visual C\+\+ 2005, un módulo se creaba con **\/clr:noAssembly**.  
  
 El vinculador de Visual C\+\+ acepta archivos .netmodule como entrada y el archivo de salida generado por el vinculador se un ensamblado o un .netmodule sin dependencia en tiempo de ejecución en .netmodules cualquiera de los que se especifican al vinculador.  Para obtener más información, vea [.Archivos netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
-   Especifique [\/NOASSEMBLY \(Crear un módulo MSIL\)](../../build/reference/noassembly-create-a-msil-module.md) en la fase del vinculador para crear el archivo de salida.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Esta opción del compilador no se puede modificar mediante programación.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)