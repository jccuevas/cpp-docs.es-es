---
title: "Changing the Names of Symbol Header Files | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.symbol.changing.header"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resource files, multiple"
  - "Resource Includes dialog box"
  - "symbol header files, changing names"
  - "symbol header files"
  - "header files, changing names"
  - "names [C++], symbol header files"
  - "symbols, symbol header files"
  - "Resource.h"
ms.assetid: b948284a-7899-402e-ab12-9f2c8480ca9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Changing the Names of Symbol Header Files
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Normalmente todas las definiciones de símbolos se guardan en Resource.h.  Sin embargo, puede que necesite cambiar este nombre de archivo de inclusión para, por ejemplo, poder trabajar con más de un archivo de recursos en el mismo directorio.  
  
### Para cambiar el nombre del archivo de encabezado de símbolos de recurso  
  
1.  En [Vista de recursos](../windows/resource-view-window.md), haga clic con el botón derecho en el archivo .rc y elija [Archivos de inclusión de recursos](../windows/resource-includes-dialog-box.md) en el menú contextual.  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  En el cuadro **Archivo de encabezado de símbolos**, escriba el nuevo nombre del archivo de inclusión.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*.  
  
 Requisitos  
  
 Win32  
  
## Vea también  
 [Viewing Resource Symbols](../windows/viewing-resource-symbols.md)   
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)