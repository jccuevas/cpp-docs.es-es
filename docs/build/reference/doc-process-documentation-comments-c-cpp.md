---
title: "-/doc (procesar comentarios de documentación) (C/C ++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- /doc
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
dev_langs:
- C++
helpviewer_keywords:
- /doc compiler option [C++]
- comments, C++ code
- XML documentation, comments in source files
- -doc compiler option [C++]
ms.assetid: b54f7e2c-f28f-4f46-9ed6-0db09be2cc63
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8737c0e33d33fe062d9a07f18d9005e58463f5b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="doc-process-documentation-comments-cc"></a>/doc (Procesar comentarios de documentación) (C/C++)
Hace que el compilador para procesar los comentarios de documentación en archivos de código fuente y para crear un archivo .xdc por cada archivo de código fuente que tenga comentarios de documentación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/doc[name]  
```  
  
## <a name="arguments"></a>Argumentos  
 `name`  
 El nombre del archivo .xdc que creará el compilador. Solo es válido cuando se pasa un archivo .cpp en la compilación.  
  
## <a name="remarks"></a>Comentarios  
 Los archivos .xdc se procesan en un archivo .xml con xdcmake.exe. Para obtener más información, consulte [XDCMake Reference](../../ide/xdcmake-reference.md).  
  
 Puede agregar comentarios de documentación a los archivos de código fuente. Para obtener más información, consulte [etiquetas recomendadas para comentarios de documentación](../../ide/recommended-tags-for-documentation-comments-visual-cpp.md).  
  
 Para utilizar el archivo .xml generado con IntelliSense, realizar el nombre de archivo del archivo .xml igual que el ensamblado que desea admitir y ponga el archivo .xml se encuentra en el mismo directorio que el ensamblado. Cuando se hace referencia al ensamblado en el proyecto de Visual Studio, también se encuentra el archivo XML. Para obtener más información, consulte [utilizar IntelliSense](/visualstudio/ide/using-intellisense) y [proporcionar comentarios del código XML](/visualstudio/ide/supplying-xml-code-comments).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda el **propiedades de configuración** nodo.  
  
3.  Expanda el **C/C++** nodo.  
  
4.  Seleccione el **archivos de salida** página de propiedades.  
  
5.  Modificar el **generar archivos de documentación XML** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GenerateXMLDocumentationFiles%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)