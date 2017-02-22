---
title: "/MANIFESTINPUT (Especificar entrada de manifiestos) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# /MANIFESTINPUT (Especificar entrada de manifiestos)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica un archivo de entrada de manifiesto que se debe incluir en el manifiesto integrado en la imagen.  
  
## Sintaxis  
  
```c#  
/MANIFESTINPUT:filename  
```  
  
#### Parámetros  
 `filename`  
 El archivo de manifiesto para incluir el manifiesto incrustado.  
  
## Comentarios  
 La opción **\/MANIFESTINPUT** especifica la ruta de acceso de un archivo de entrada que se usa para crear el manifiesto integrado en una imagen ejecutable.  Si tiene varios archivos de entrada de manifiesto, utilice el modificador varias veces, una para cada archivo de entrada.  Los archivos de entrada de manifiesto se combinan para crear el manifiesto incrustado.  Esta opción requiere la opción **\/MANIFEST:EMBED**.  
  
 Esta opción no se puede establecer directamente en [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)].  En su lugar, use la propiedad **Archivos de manifiesto adicionales** del proyecto para especificar archivos de manifiesto adicionales que se deben incluir.  Para obtener más información, vea [Entrada y salida, Herramienta Manifiesto, Propiedades de configuración, Páginas de propiedades de \<Projectname\> \(Cuadro de diálogo\)](../../ide/input-and-output-manifest-tool.md).  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)