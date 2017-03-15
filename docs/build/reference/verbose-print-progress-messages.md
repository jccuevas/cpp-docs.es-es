---
title: "/VERBOSE (Mostrar mensajes de progreso) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/verbose"
  - "VC.Project.VCLinkerTool.ShowProgress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/VERBOSE (opción del vinculador)"
  - "dependencias [C++], información de dependencias en los resultados del vinculador"
  - "vinculador [C++], información de dependencias de resultados"
  - "vincular [C++], información de progreso de sesión"
  - "imprimir mensajes de progreso (opción del vinculador)"
  - "VERBOSE (opción del vinculador)"
  - "-VERBOSE (opción del vinculador)"
ms.assetid: 9c347d98-4c37-4724-a39e-0983934693ab
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /VERBOSE (Mostrar mensajes de progreso)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/VERBOSE[:{ICF|INCR|LIB|REF|SAFESEH|UNUSEDLIBS}]  
```  
  
## Comentarios  
 El vinculador envía información sobre el progreso de la sesión de vinculación a la ventana **Salida**.  En la línea de comandos, la información se envía a la salida estándar y puede redirigirse a un archivo.  
  
|Opción|Descripción|  
|------------|-----------------|  
|\/VERBOSE|Muestra detalles sobre el proceso de vinculación.|  
|\/VERBOSE:ICF|Muestra información sobre la actividad del vinculador que resulta del uso de [\/OPT:ICF](../../build/reference/opt-optimizations.md).|  
|\/VERBOSE:INCR|Muestra información sobre el proceso de vinculación incremental.|  
|\/VERBOSE:LIB|Muestra mensajes de progreso que indican solamente las bibliotecas de búsqueda.<br /><br /> La información presentada incluye el proceso de búsqueda en las bibliotecas y enumera los nombres de las bibliotecas y objetos \(con la ruta de acceso completa\), el símbolo que se esté resolviendo de cada biblioteca y una lista de los objetos que hacen referencia al símbolo.|  
|\/VERBOSE:REF|Muestra información sobre la actividad del vinculador que resulta del uso de [\/OPT:REF](../../build/reference/opt-optimizations.md).|  
|\/VERBOSE:SAFESEH|Muestra información sobre los módulos que no son compatibles con el control de excepciones seguro cuando no se especifica [\/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md).|  
|\/VERBOSE:UNUSEDLIBS|Muestra información sobre los archivos de biblioteca que no se usan cuando se crea la imagen.|  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Expanda la carpeta **Vinculador**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  Agregue la opción al cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)