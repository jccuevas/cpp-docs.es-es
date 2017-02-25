---
title: "/TLBID (Especificar un identificador de recursos para una biblioteca de tipos) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/tlbid"
  - "VC.Project.VCLinkerTool.TypeLibraryResourceID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".tlb (archivos), especificar el identificador del recurso"
  - "/TLBID (opción del vinculador)"
  - "tlb (archivos), especificar el identificador del recurso"
  - "TLBID (opción del vinculador)"
  - "-TLBID (opción del vinculador)"
  - "bibliotecas de tipos, especificar el identificador del recurso"
ms.assetid: 434b28a2-4656-4d52-ac82-8b18bf486fb2
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /TLBID (Especificar un identificador de recursos para una biblioteca de tipos)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/TLBID:id  
```  
  
## Comentarios  
 donde:  
  
 `id`  
 Valor especificado por el usuario para una biblioteca de tipos creada por el vinculador.  Reemplaza el identificador de recurso 1 \(valor predeterminado\).  
  
## Comentarios  
 Al compilar un programa que usa atributos, el vinculador crea una biblioteca de tipos  y le asigna el identificador de recurso 1.  
  
 Si este identificador entra en conflicto con alguno de los recursos existentes, con \/TLBID se podrá especificar un identificador distinto.  El rango de valores que puede pasar al identificador \(`id`\) es de 1 a 65535.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **IDL incrustado**.  
  
4.  Modifique la propiedad **Identificador de recursos de biblioteca de tipos**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryResourceID%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)