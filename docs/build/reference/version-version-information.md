---
title: "/VERSION (Informaci&#243;n de versi&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.Version"
  - "/version"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/VERSION (opción del vinculador)"
  - "información de versión (opción del vinculador)"
  - "VERSION (opción del vinculador)"
  - "-VERSION (opción del vinculador)"
  - "números de versión, especificar en .exe"
ms.assetid: b86d0e86-dca6-4316-aee2-d863ccb9f223
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /VERSION (Informaci&#243;n de versi&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/VERSION:major[.minor]  
```  
  
## Comentarios  
 donde:  
  
 *major* y *minor*  
 Número de versión que se desea incluir en el encabezado del archivo .exe o .dll.  
  
## Comentarios  
 La opción \/VERSION indica al vinculador que incluya un número de versión en el encabezado del archivo .exe o .dll.  Para obtener el campo de versión de imagen de OPTIONAL HEADER VALUES y ver el efecto de \/VERSION, puede usarse DUMPBIN [\/HEADERS](../../build/reference/headers.md).  
  
 Los argumentos *major* y *minor* son números decimales en el intervalo de 0 a 65535.  El valor predeterminado es la versión 0.0.  
  
 La información especificada con \/VERSION no afecta a la información de versión que aparece para una aplicación al ver sus propiedades en el Explorador de archivos.  Dicha información se obtiene de un archivo de recursos utilizado en la compilación de la aplicación.  Para obtener más información, vea [Editor de información de versión](../../mfc/version-information-editor.md).  
  
 Otro método para insertar un número de versión es mediante la instrucción de definición de módulos [VERSION](../../build/reference/version-c-cpp.md).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **General**.  
  
4.  Modifique la propiedad **Version**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Version%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)