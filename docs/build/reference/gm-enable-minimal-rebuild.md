---
title: -Gm (habilitar recompilación mínima) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- /FD
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
dev_langs:
- C++
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e0b83c34b0ff8cacbca9d21a40c6c9572f516d1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (Habilitar recompilación mínima)
Habilita la recompilación mínima, que determina si es necesario recompilar los archivos de origen de C++ que incluyen definiciones de clases de C++ cambiadas (almacenadas en archivos de encabezado (.h)).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Gm  
```  
  
## <a name="remarks"></a>Comentarios  
 El compilador almacena la información de dependencias entre los archivos de origen y las definiciones de clases en el archivo .idb del proyecto durante la primera compilación. (Información de dependencias indica qué archivo de código fuente depende de qué definición de clase, y qué archivo .h la definición se encuentra en.) Las compilaciones posteriores utilizan la información almacenada en el archivo .idb para determinar si un archivo de origen debe ser compilado, aunque incluya un archivo .h modificado.  
  
> [!NOTE]
>  La recompilación mínima se basa en las definiciones de clases que no cambian entre los archivos de inclusión. Las definiciones de clases deben ser globales del proyecto (solo debe haber una definición de cada clase), porque la información de dependencias del archivo .idb se crea para todo el proyecto. Si alguna clase del proyecto tiene más de una definición, deshabilite la recompilación mínima.  
  
 Dado que el vinculador incremental no es compatible con los metadatos de Windows incluidos en los archivos .obj mediante la [/ZW (compilación de Windows en tiempo de ejecución)](../../build/reference/zw-windows-runtime-compilation.md) opción, el **/Gm** es incompatible con la opción  **/ ZW**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en el **generación de código** página de propiedades.  
  
4.  Modificar el **habilitar recompilación mínima** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)