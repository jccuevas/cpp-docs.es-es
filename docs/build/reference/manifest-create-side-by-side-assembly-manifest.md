---
title: "/MANIFEST (Crear el manifiesto del ensamblado simult&#225;neo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.GenerateManifest"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MANIFEST (opción del vinculador)"
  - "MANIFEST (opción del vinculador)"
  - "-MANIFEST (opción del vinculador)"
ms.assetid: 98c52e1e-712c-4f49-b149-4d0a3501b600
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# /MANIFEST (Crear el manifiesto del ensamblado simult&#225;neo)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MANIFEST[:{EMBED[,ID=#]|NO}]  
```  
  
## Comentarios  
 \/MANIFEST especifica que el vinculador debe crear un archivo de manifiesto en paralelo.  Para obtener más información sobre los archivos de manifiesto, vea [Referencia de archivos de manifiesto](http://msdn.microsoft.com/library/aa375632).  
  
 El valor predeterminado es \/MANIFEST.  
  
 La opción \/MANIFEST:EMBED especifica que el vinculador debe incrustar el archivo de manifiesto en la imagen como recurso de tipo RT\_MANIFEST.  El parámetro `ID` opcional es el id. de recurso que se utilizará para el manifiesto.  Utilice un valor de 1 para un archivo ejecutable.  Utilice un valor de 2 en un archivo DLL para habilitarlo si desea especificar dependencias privadas.  Si no se especifica el parámetro `ID`, el valor predeterminado es 2 si se establece la opción \/DLL; de lo contrario, el valor predeterminado es 1.  
  
 A partir de [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)], los archivos de manifiesto para archivos ejecutables contienen una sección en la que se especifica la información de Control de cuentas de usuario \(UAC\).  Si especifica \/MANIFEST pero no especifica [\/MANIFESTUAC](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md) ni [\/DLL](../../build/reference/dll-build-a-dll.md), se insertará en el manifiesto un fragmento predeterminado de UAC con el nivel de UAC establecido en *asInvoker*.  Para obtener más información sobre los niveles de UAC, vea [\/MANIFESTUAC \(Incrustar información de UAC en el manifiesto\)](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md).  
  
 Para cambiar el comportamiento predeterminado de UAC, realice una de las siguientes operaciones:  
  
-   Especifique la opción \/MANIFESTUAC y establezca el nivel de UAC en el nivel deseado.  
  
-   O bien, especifique la opción \/MANIFESTUAC:NO si no desea generar un fragmento de UAC en el manifiesto.  
  
 Si no especifica \/MANIFEST pero especifica comentarios [\/MANIFESTDEPENDENCY](../../build/reference/manifestdependency-specify-manifest-dependencies.md), se creará un archivo de manifiesto.  No se creará un archivo de manifiesto si especifica \/MANIFEST:NO.  
  
 Si especifica \/MANIFEST, el nombre del archivo de manifiesto coincidirá con el nombre del archivo de salida, pero se agregará .manifest al nombre de archivo.  Por ejemplo, si el nombre del archivo de salida es MiArchivo.exe, el nombre del archivo de manifiesto será MiArchivo.exe.manifest.  Si especifica \/MANIFESTFILE:*name*, el nombre del manifiesto es el que se especifica en *name*.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el nodo **Vinculador**.  
  
4.  Seleccione la página de propiedades **Archivo de manifiesto**.  
  
5.  Modifique la propiedad **Generar manifiesto**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateManifest%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)