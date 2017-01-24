---
title: "Advertencia de las herramientas del vinculador LNK4099 | Microsoft Docs"
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
  - "LNK4099"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4099"
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de las herramientas del vinculador LNK4099
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se encontró PDB 'nombredearchivo' con 'object\/library' o en 'ruta de acceso'; se vinculará el objeto sin tener en cuenta información de depuración  
  
 El vinculador no encontró el archivo .pdb.  Copie el archivo en el directorio que contiene `object/library`.  
  
 Para encontrar el nombre del archivo .pdb asociado al archivo objeto:  
  
1.  Extraiga un archivo objeto de la biblioteca con [lib](../../build/reference/lib-reference.md) **\/extract:**`objectname`**.obj** `xyz`**.lib**.  
  
2.  Compruebe la ruta de acceso al archivo .pdb con **dumpbin \/section:.debug$T \/rawdata** `objectname`**.obj**.  
  
 También puede compilar con [\/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), de modo que no sea necesario utilizar el archivo .pdb, o quitar la opción del vinculador [\/DEBUG](../../build/reference/debug-generate-debug-info.md) si no dispone de archivos .pdb para los objetos que está vinculando.