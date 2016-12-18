---
title: "Advertencia de las herramientas del vinculador LNK4014 | Microsoft Docs"
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
  - "LNK4014"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4014"
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de las herramientas del vinculador LNK4014
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede buscar el objeto miembro "objectname"  
  
 LIB no ha podido encontrar `objectname` en la biblioteca.  
  
 Las opciones **\/REMOVE** y **\/EXTRACT** requieren el nombre completo del objeto miembro que se va a eliminar o copiar en un archivo.  El nombre completo incluye la ruta de acceso al archivo objeto original.  Para ver los nombres completos de los objetos miembro de una biblioteca, use DUMPBIN [\/ARCHIVEMEMBERS](../../build/reference/archivemembers.md) o LIB [\/LIST](../../build/reference/managing-a-library.md).