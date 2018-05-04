---
title: -I (adicionales directorios de inclusión) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories
- VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories
- /I
- VC.Project.VCNMakeTool.IncludeSearchPath
dev_langs:
- C++
helpviewer_keywords:
- /I compiler option [C++]
- Additional Include Directories compiler option
- I compiler option [C++]
- -I compiler option [C++]
- set include directories
- include directories, compiler option [C++]
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 435714d72eeabe74f0cd85509d74dff5d541b019
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="i-additional-include-directories"></a>/I (Directorios de inclusión adicionales)
Agrega un directorio a la lista de directorios que donde se buscan archivos de inclusión.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/I[ ]directory  
```  
  
## <a name="arguments"></a>Argumentos  
 `directory`  
 Busca en el directorio que se va a agregar a la lista de directorios para archivos de inclusión.  
  
## <a name="remarks"></a>Comentarios  
 Para agregar más de un directorio, use esta opción varias veces. Directorios se buscan solo hasta que se encuentra el archivo de inclusión especificado.  
  
 Puede usar esta opción con Ignore Standard Include Paths ([/X (omitir estándar incluyen rutas de acceso)](../../build/reference/x-ignore-standard-include-paths.md)) opción.  
  
 El compilador busca en los directorios en el orden siguiente:  
  
1.  Directorios que contiene el archivo de origen.  
  
2.  Los directorios especificados con la **/I** opción, en el orden en que CL los encuentra.  
  
3.  Los directorios especificados en la **INCLUDE** variable de entorno.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en el **General** página de propiedades.  
  
4.  Modificar el **directorios de inclusión adicionales** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>.  
  
## <a name="example"></a>Ejemplo  
 El siguiente comando busca los archivos de inclusión solicitados por MAIN.c en el orden siguiente: primero en el directorio que contiene MAIN.c, a continuación, en el directorio \INCLUDE, luego, en el directorio \MY\INCLUDE y, por último, en los directorios asignados a la inclusión variable de entorno.  
  
```  
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C  
```  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)