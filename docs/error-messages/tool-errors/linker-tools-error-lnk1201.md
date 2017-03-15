---
title: "Error de las herramientas del vinculador LNK1201 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1201"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1201"
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error de las herramientas del vinculador LNK1201
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error al escribir en la base de datos del programa 'nombredearchivo'; compruebe si tiene suficiente espacio en disco, si la ruta es válida o si tiene privilegios suficientes  
  
 LINK no pudo escribir en la base de datos de programa \(PDB\) del archivo de salida.  
  
### Posibles causas del error:  
  
1.  El archivo está dañado.  Elimine el archivo PDB y vuelva a vincular.  
  
2.  No hay espacio en disco suficiente para escribir el archivo.  
  
3.  La unidad no está disponible, posiblemente por un problema de la red.  
  
4.  El depurador está funcionando en el programa que se intenta vincular.  
  
5.  El espacio en el montón es insuficiente  Para obtener más información, vea [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md).