---
title: '-FU (Name Forced #using archivo) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ForcedUsingFiles
- /FU
- VC.Project.VCNMakeTool.ForcedUsingAssemblies
dev_langs:
- C++
helpviewer_keywords:
- -FU compiler option [C++]
- FU compiler option [C++]
- /FU compiler option [C++]
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c9a27d8c689b198bde47047969d38cf14b41c46
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375680"
---
# <a name="fu-name-forced-using-file"></a>/FU (Asignar nombre al archivo #using obligatorio)
Una opción del compilador que puede usar como alternativa a pasar un nombre de archivo para [#using (directiva)](../../preprocessor/hash-using-directive-cpp.md) en el código fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/FU file  
```  
  
## <a name="arguments"></a>Argumentos  
 `file`  
 Especifica el archivo de metadatos que hacen referencia en esta compilación.  
  
## <a name="remarks"></a>Comentarios  
 El conmutador /FU toma un solo nombre de archivo. Para especificar varios archivos, use /FU con cada uno de ellos.  
  
 Si utilizas [!INCLUDE[cppcli](../../build/reference/includes/cppcli_md.md)] y se hace referencia a metadatos para que utilicen el [Friend (ensamblados)](../../dotnet/friend-assemblies-cpp.md) característica, no puede usar **/FU**. Debe hacer referencia a los metadatos en el código mediante el uso de `#using`, junto con el `[as friend]` atributo. No se admiten ensamblados de confianza en [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] ([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]).  
  
 Para obtener información sobre cómo crear un ensamblado o módulo para common language runtime (CLR), consulte [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md). Para obtener información sobre cómo crear [!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)], consulte [compilar aplicaciones y bibliotecas](../../cppcx/building-apps-and-libraries-c-cx.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **C/C++** carpeta.  
  
3.  Seleccione el **avanzadas** página de propiedades.  
  
4.  Modificar el **Force #using** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Archivo de salida (/ F) opciones](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)