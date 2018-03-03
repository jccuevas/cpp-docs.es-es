---
title: -hotpatch (crear una imagen) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /hotpatch
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- C++
helpviewer_keywords:
- hot patching
- -hotpatch compiler option [C++]
- /hotpatch compiler option [C++]
- hotpatching
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ad7ab4e6450d33923b728f20c8a35185edd2b05e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="hotpatch-create-hotpatchable-image"></a>/hotpatch (Crear una imagen a la que se puede aplicar una revisión reciente)
Prepara una imagen para aplicar una revisión activa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/hotpatch  
```  
  
## <a name="remarks"></a>Comentarios  
 Cuando **/hotpatch** se utiliza en una compilación, el compilador garantiza que primera instrucción de cada función sea al menos dos bytes, que es necesario para aplicar una revisión activa.  
  
 Para completar la preparación para que la imagen admita hotpatch, después de usar **/hotpatch** para compilar, debe usar [/FUNCTIONPADMIN (crear una imagen)](../../build/reference/functionpadmin-create-hotpatchable-image.md) para vincular. Cuando se compila y vincula una imagen mediante una invocación de cl.exe, **/hotpatch** implica **/functionpadmin**.  
  
 Dado que las instrucciones siempre son dos bytes o mayores en la arquitectura ARM y porque x64 compilación siempre se trata como si **/hotpatch** se ha especificado, no tiene que especificar **/hotpatch** cuando compilar para estos destinos; Sin embargo, aún debe vincular mediante **/functionpadmin** para crear imágenes de hotpatchable de ellos. El **/hotpatch** solo afecta a x86 compilación de opción de compilador.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **C/C++** carpeta.  
  
3.  Seleccione el **línea de comandos** página de propiedades.  
  
4.  Agregue la opción del compilador para la **opciones adicionales** cuadro.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="guidance"></a>Orientación  
 Para obtener más información acerca de la administración de actualizaciones, vea "Security Guidance for Update Management" en [http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx](http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx).  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)