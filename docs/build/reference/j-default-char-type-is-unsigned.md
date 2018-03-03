---
title: "-J (carácter predeterminado es de tipo sin signo) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
dev_langs:
- C++
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5195822908c13217244a344357a6140d67a9e7df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="j-default-char-type-is-unsigned"></a>/J (El tipo de carácter predeterminado no tiene signo)
Cambia el valor predeterminado `char` escriba desde `signed char` a `unsigned char`y el `char` tipo es ceros cuando se amplían a un `int` tipo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/J  
```  
  
## <a name="remarks"></a>Comentarios  
 Si un `char` valor se declara explícitamente como `signed`, **/j** opción no le afecta, y el valor es signos hasta llegar al que se amplía a un `int` tipo.  
  
 El **/j** define la opción `_CHAR_UNSIGNED`, que se usa con `#ifndef` en el archivo LIMITS.h para definir el intervalo del valor predeterminado `char` tipo.  
  
 ANSI C y C++ no requieren una implementación específica de la `char` tipo. Esta opción es útil cuando se trabaja con datos de caracteres que finalmente se traducirá en un idioma distinto del inglés.  
  
> [!NOTE]
>  Si usa esta opción del compilador con ATL/MFC, es posible que genera un error. Aunque se podía deshabilitar este error mediante la definición de `_ATL_ALLOW_CHAR_UNSIGNED`, esta solución no se admite y no siempre se funcionen.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.  
  
2.  En el proyecto **páginas de propiedades** cuadro de diálogo, en el panel izquierdo bajo **propiedades de configuración**, expanda **C/C++** y, a continuación, seleccione **delíneadecomandos**.  
  
3.  En el **opciones adicionales** panel, especifique la **/j** opción del compilador.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md)