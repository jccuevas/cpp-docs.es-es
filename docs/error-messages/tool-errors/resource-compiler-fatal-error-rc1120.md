---
title: "Error irrecuperable del compilador de recursos RC1120 | Microsoft Docs"
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
  - "RC1120"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC1120"
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable del compilador de recursos RC1120
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**memoria insuficiente, se necesitan '**   
 ***número* ' bytes**  
  
 El compilador de recursos se quedó sin espacio de almacenamiento para los elementos que almacena en su montón.  Este suele ser el resultado de tener demasiados símbolos.  
  
### Se corrige mediante algunas de las siguientes posibles soluciones  
  
1.  Aumente el tamaño del archivo de intercambio de Windows.  Para obtener más información sobre cómo aumentar el tamaño del archivo de intercambio, busque memoria virtual en la Ayuda de Windows.  
  
2.  Elimine los archivos de inclusión que no sean necesarios, especialmente las directivas `#define` y los prototipos de función.  
  
3.  Divida el archivo actual en dos o más archivos y compílelos por separado.  
  
4.  Quite otros programas o controladores que se estén ejecutando en el sistema y puedan estar consumiendo una cantidad de memoria importante.