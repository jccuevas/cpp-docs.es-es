---
title: -MANIFESTDEPENDENCY (especificar las dependencias del manifiesto) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCLinkerTool.AdditionalManifestDependencies
dev_langs: C++
helpviewer_keywords:
- MANIFESTDEPENDENCY linker option
- /MANIFESTDEPENDENCY linker option
- -MANIFESTDEPENDENCY linker option
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 01da83a57769dbe5b86c5bc2a73875231b769cdd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="manifestdependency-specify-manifest-dependencies"></a>/MANIFESTDEPENDENCY (Especificar las dependencias del manifiesto)
```  
/MANIFESTDEPENDENCY:manifest_dependency  
```  
  
## <a name="remarks"></a>Comentarios  
 /MANIFESTDEPENDENCY le permite especificar los atributos que se colocarán en el \<dependencia > sección del archivo de manifiesto.  
  
 Vea [/manifest (Create Side-by-Side Assembly Manifest)](../../build/reference/manifest-create-side-by-side-assembly-manifest.md) para obtener información sobre cómo crear un archivo de manifiesto.  
  
 Para obtener más información sobre la \<dependencia > sección del archivo de manifiesto, vea [Publisher Configuration Files](http://msdn.microsoft.com/library/aa375682).  
  
 Información de /MANIFESTDEPENDENCY se puede pasar al vinculador de una de dos maneras:  
  
-   Directamente en la línea de comandos (o en un archivo de respuesta) con/MANIFESTDEPENDENCY.  
  
-   A través de la [comentario](../../preprocessor/comment-c-cpp.md) pragma.  
  
 En el ejemplo siguiente se muestra un comentario /MANIFESTDEPENDENCY pasado mediante pragma:  
  
```  
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")  
```  
  
 que da como resultado la siguiente entrada en el archivo de manifiesto:  
  
```  
<dependency>  
  <dependentAssembly>  
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />  
  </dependentAssembly>  
</dependency>  
```  
  
 Los mismos comentarios /MANIFESTDEPENDENCY se pueden pasar en la línea de comandos como se indica a continuación:  
  
```  
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"  
```  
  
 El vinculador recopilar comentarios/MANIFESTDEPENDENCY, eliminará las entradas duplicadas y, a continuación, agregue la cadena XML resultante al archivo de manifiesto.  Si el vinculador busca entradas en conflicto, el archivo de manifiesto se dañará y se producirá un error de la aplicación iniciar (puede agregarse una entrada en el registro de eventos, que indica el origen del error).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda el **propiedades de configuración** nodo.  
  
3.  Expanda el **vinculador** nodo.  
  
4.  Seleccione el **archivo de manifiesto** página de propiedades.  
  
5.  Modificar el **dependencias de manifiesto adicionales** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)