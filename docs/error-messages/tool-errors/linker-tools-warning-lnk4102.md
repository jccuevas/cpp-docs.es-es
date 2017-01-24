---
title: "Advertencia de las herramientas del vinculador LNK4102 | Microsoft Docs"
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
  - "LNK4102"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4102"
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de las herramientas del vinculador LNK4102
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

exportación del destructor 'nombre' de eliminación; es posible que la imagen no se ejecute correctamente  
  
 El programa intentó exportar un destructor de eliminación.  La eliminación resultante puede producirse a través de un límite de DLL, de manera que un proceso puede liberar memoria que no le pertenece.  Compruebe que el símbolo dado no figura en el archivo .def y que tampoco aparece como argumento de la opción **\/IMPORT** o **\/EXPORT** en la línea de comandos del vinculador.  
  
 Si se recompila la biblioteca en tiempo de ejecución de C, se puede omitir el mensaje.