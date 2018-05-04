---
title: -Y-(Omitir opciones de encabezado precompilado) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /y-
dev_langs:
- C++
helpviewer_keywords:
- Y- compiler option [C++]
- -Y- compiler option [C++]
- /Y- compiler option [C++]
ms.assetid: cfaecb36-58db-46b8-b04d-cca6072b1b7a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b67520bd1cb961b7dcef7b05cb23a59ed9e6a4b2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="y--ignore-precompiled-header-options"></a>/Y- (Omitir opciones de encabezado precompilado)
Causas todos los demás `/Y` compilador opciones que se omitan (y no se puede invalidar).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Y-  
```  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información sobre encabezados precompilados, vea:  
  
-   [/Y (Encabezados precompilados)](../../build/reference/y-precompiled-headers.md)  
  
-   [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en la página de propiedades **Línea de comandos** .  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)