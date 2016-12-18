---
title: "Advertencia de las herramientas del vinculador LNK4105 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4105"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4105"
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de las herramientas del vinculador LNK4105
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ningún argumento especificado con la opción 'opción'; se omite la opción  
  
 Esta advertencia sólo aparece cuando se establece la opción [\/LIBPATH](../../build/reference/libpath-additional-libpath.md).  Si no hay especificado un directorio con esta opción, el vinculador la omite y genera este mensaje de advertencia.  
  
 Si no necesita reemplazar la configuración de entorno de biblioteca existente, quite la opción \/LIBPATH de la línea de comandos del vinculador.  Si desea utilizar una ruta de búsqueda alternativa para las bibliotecas, especifíquela a continuación de la opción \/LIBPATH.  
  
## Ejemplo  
  
```  
link /libpath:c:\filepath\lib bar.obj  
```  
  
 indica al vinculador que busque las bibliotecas requeridas en `c:\filepath\lib` antes de hacerlo en las ubicaciones predeterminadas.