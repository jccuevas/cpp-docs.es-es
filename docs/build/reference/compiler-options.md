---
title: Opciones del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- cl.exe compiler
- IPF Visual C++ compiler
- Itanium Visual C++ compiler
- compiler options, C++
- x64 Visual C++ compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 490814f85199450d4261bf4071184b75b5ea10c2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-options"></a>Opciones del compilador
cl.exe es una herramienta que controla los compiladores de Microsoft C y C++ y el vinculador. cl.exe puede realizarse únicamente en sistemas operativos compatibles con Microsoft Visual Studio.  
  
> [!NOTE]
>  Puede iniciar esta herramienta solo desde el símbolo del sistema de [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.  
  
 Los compiladores generan archivos objeto (.obj) de formato de archivo de objeto común (COFF). El vinculador genera archivos ejecutables (.exe) o bibliotecas de vínculos dinámicos (DLL).  
  
 Tenga en cuenta que todas las opciones del compilador distinguen mayúsculas de minúsculas.  
  
 Para compilar sin vinculación, use [/c](../../build/reference/c-compile-without-linking.md).  
  
## <a name="finding-an-option"></a>Buscar una opción  
 Para buscar una opción de compilador determinado, consulte una de las listas siguientes:  
  
-   [Opciones del compilador por orden alfabético](../../build/reference/compiler-options-listed-alphabetically.md)  
  
-   [Opciones del compilador por categoría](../../build/reference/compiler-options-listed-by-category.md)  
  
## <a name="specifying-options"></a>Especificar opciones  
 El tema de cada opción del compilador describe cómo se puede establecer en el entorno de desarrollo. Para obtener información sobre cómo especificar opciones fuera del entorno de desarrollo, consulte:  
  
-   [Sintaxis de la línea de comandos del compilador](../../build/reference/compiler-command-line-syntax.md)  
  
-   [Archivos de comandos de CL](../../build/reference/cl-command-files.md)  
  
-   [Variables de entorno de CL](../../build/reference/cl-environment-variables.md)  
  
## <a name="related-build-tools"></a>Herramientas de generación relacionadas  
 Use [NMAKE](../../build/nmake-reference.md) para generar el archivo de salida.  
  
 Use [BSCMAKE](../../build/reference/bscmake-reference.md) para admitir el examen de clases.  
  
 [Opciones del vinculador](../../build/reference/linker-options.md) también afectan al modo en que se compila el programa.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de compilación de C/C++](../../build/reference/c-cpp-building-reference.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Compilación rápida](../../build/reference/fast-compilation.md)   
 [CL invoca el vinculador](../../build/reference/cl-invokes-the-linker.md)