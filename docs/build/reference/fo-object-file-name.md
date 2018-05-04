---
title: -Fo (nombre del archivo objeto) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
dev_langs:
- C++
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea552b149270b8e644140a4dd51f220648ef376e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="fo-object-file-name"></a>/Fo (Nombre del archivo objeto)
Especifica un nombre de archivo objeto (.obj) o un directorio que se utilizará en lugar del predeterminado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Fopathname  
```  
  
## <a name="remarks"></a>Comentarios  
 Si no utiliza esta opción, el archivo objeto utiliza el nombre base del archivo de origen y la extensión de obj. Puede usar cualquier nombre y extensión que desee, pero la convención recomendada es utilizar. obj.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en la página de propiedades **Archivos de salida** .  
  
4.  Modificar el **nombre del archivo objeto** propiedad.  En el entorno de desarrollo, el archivo de objeto debe tener la extensión. obj.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>.  
  
## <a name="example"></a>Ejemplo  
 La siguiente línea de comandos crea un archivo de objeto denominado THIS.obj en un directorio existente, \OBJECT, de la unidad B.  
  
```  
CL /FoB:\OBJECT\ THIS.C  
```  
  
## <a name="see-also"></a>Vea también  
 [Archivo de salida (/ F) opciones](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Especificar la ruta de acceso](../../build/reference/specifying-the-pathname.md)