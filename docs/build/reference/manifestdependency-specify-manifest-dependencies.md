---
title: "/MANIFESTDEPENDENCY (Especificar las dependencias del manifiesto) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.AdditionalManifestDependencies"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MANIFESTDEPENDENCY (opción del vinculador)"
  - "MANIFESTDEPENDENCY (opción del vinculador)"
  - "-MANIFESTDEPENDENCY (opción del vinculador)"
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /MANIFESTDEPENDENCY (Especificar las dependencias del manifiesto)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MANIFESTDEPENDENCY:manifest_dependency  
```  
  
## Comentarios  
 \/MANIFESTDEPENDENCY permite especificar atributos que se incluirán en la sección de dependencias del archivo de manifiesto. \<\>  
  
 Vea [\/MANIFEST \(Crear el manifiesto del ensamblado simultáneo\)](../../build/reference/manifest-create-side-by-side-assembly-manifest.md) para obtener información sobre cómo crear un archivo de manifiesto.  
  
 Para obtener más información en \<la sección\> de dependencia del archivo de manifiesto, vea [Archivos de configuración de editor](http://msdn.microsoft.com/library/aa375682).  
  
 La información de \/MANIFESTDEPENDENCY se puede pasar al vinculador de una de estas dos maneras:  
  
-   Directamente en la línea de comandos \(o en un archivo de respuesta\) con \/MANIFESTDEPENDENCY.  
  
-   Mediante el pragma [comment](../../preprocessor/comment-c-cpp.md).  
  
 El ejemplo siguiente muestra un comentario \/MANIFESTDEPENDENCY pasado mediante pragma:  
  
```  
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")  
```  
  
 que genera la entrada siguiente en el archivo de manifiesto:  
  
```  
<dependency>  
  <dependentAssembly>  
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />  
  </dependentAssembly>  
</dependency>  
```  
  
 Los mismos comentarios \/MANIFESTDEPENDENCY se pueden pasar en la línea de comandos como se indica a continuación:  
  
```  
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"  
```  
  
 El vinculador recogerá los comentarios \/MANIFESTDEPENDENCY, eliminará las entradas duplicadas y, a continuación, agregará la cadena XML resultante al archivo de manifiesto.  Si el vinculador encuentra entradas incompatibles, el archivo de manifiesto se dañará y la aplicación no podrá iniciarse \(podría agregarse una entrada en el registro de eventos, para indicar el origen del error\).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el nodo **Vinculador**.  
  
4.  Seleccione la página de propiedades **Archivo de manifiesto**.  
  
5.  Modifique la propiedad **Dependencias de manifiesto adicionales**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)