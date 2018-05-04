---
title: -DLL (compilar un archivo DLL) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /dll
dev_langs:
- C++
helpviewer_keywords:
- -DLL linker option
- /DLL linker option [C++]
- exporting DLLs [C++], specifying exports
- DLLs [C++], building
- DLL linker option [C++]
ms.assetid: c7685aec-31d0-490f-9503-fb5171a23609
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1767ac9ef063ace2ee9d567dd9038519afababf8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="dll-build-a-dll"></a>/DLL (Compilar un archivo DLL)
```  
/DLL  
```  
  
## <a name="remarks"></a>Comentarios  
 La opción /DLL genera un archivo DLL como el archivo de salida principal. Normalmente, un archivo DLL contiene exportaciones que pueden ser utilizadas por otro programa. Existen tres métodos para especificar exportaciones, aparecen en el orden recomendado de uso:  
  
1.  [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) en el código fuente  
  
2.  Un [exportaciones](../../build/reference/exports.md) instrucción en un archivo .def  
  
3.  Un [/exportación](../../build/reference/export-exports-a-function.md) especificación en un comando de LINK  
  
 Un programa puede usar más de un método.  
  
 Otra manera de generar un archivo DLL es con el **biblioteca** instrucción de definición de módulo. Las opciones /BASE y /DLL juntas equivalen a la **biblioteca** instrucción.  
  
 No se especifica esta opción en el entorno de desarrollo; Esta opción es para su uso solo en la línea de comandos. Esta opción se establece cuando se crea un proyecto DLL con un Asistente para aplicaciones.  
  
 Tenga en cuenta que si crea la biblioteca de importación en un paso preliminar, antes de crear el archivo .dll, debe pasar el mismo conjunto de archivos de objeto al crear el archivo .dll, tal y como se haya pasado al crear la biblioteca de importación.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **propiedades de configuración** carpeta.  
  
3.  Haga clic en el **General** página de propiedades.  
  
4.  Modificar el **tipo de configuración** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCPropertySheet.ConfigurationType%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)