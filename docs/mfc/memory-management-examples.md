---
title: "Administraci&#243;n de memoria: Ejemplos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "matrices [C++], asignar recursos"
  - "matrices [C++], administración de memoria"
  - "estructuras de datos [C++]"
  - "estructuras de datos [C++], asignar memoria"
  - "ejemplos [MFC], asignación de memoria"
  - "asignación de marcos"
  - "asignación en el montón, ejemplos"
  - "asignación de memoria [C++], matrices"
  - "asignación de memoria [C++], estructuras de datos"
  - "asignación de memoria [C++], ejemplos"
  - "asignación de memoria [C++], objetos"
  - "MFC [C++], administración de memoria"
  - "objetos [C++], asignar memoria"
  - "objetos [C++], asignación de memoria"
  - "asignación de memoria de estructura"
  - "tipos [C++], asignación de memoria"
ms.assetid: f10240f8-b698-4c83-9288-97a54318930b
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Administraci&#243;n de memoria: Ejemplos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe cómo MFC realiza asignaciones de marco y las asignaciones de pila para cada uno de los tres tipos habituales de asignaciones de memoria:  
  
-   [Una matriz de bytes](#_core_allocation_of_an_array_of_bytes)  
  
-   [Una estructura de datos](#_core_allocation_of_a_data_structure)  
  
-   [Objeto](#_core_allocation_of_an_object)  
  
##  <a name="_core_allocation_of_an_array_of_bytes"></a> Asignación de una matriz de bytes  
  
#### Para asignar una matriz de bytes en el cuadro  
  
1.  Defina la matriz como se muestra en el código siguiente.  La matriz se elimina automáticamente y su memoria se recupera cuando desapareciese la variable de matriz su ámbito.  
  
     [!code-cpp[NVC_MFC_Utilities#1](../mfc/codesnippet/CPP/memory-management-examples_1.cpp)]  
  
#### Para asignar una matriz de bytes \(o de cualquier tipo de datos primitivo\) de la pila  
  
1.  Utilice el operador de **new** con la sintaxis de matriz mostrada en este ejemplo:  
  
     [!code-cpp[NVC_MFC_Utilities#2](../mfc/codesnippet/CPP/memory-management-examples_2.cpp)]  
  
#### Para desasignar matrices de pila  
  
1.  Utilice el operador de **borrar** como sigue:  
  
     [!code-cpp[NVC_MFC_Utilities#3](../mfc/codesnippet/CPP/memory-management-examples_3.cpp)]  
  
##  <a name="_core_allocation_of_a_data_structure"></a> Asignación de una estructura de datos  
  
#### Para asignar una estructura de datos en el cuadro  
  
1.  Defina la variable de estructura como sigue:  
  
     [!code-cpp[NVC_MFC_Utilities#4](../mfc/codesnippet/CPP/memory-management-examples_4.cpp)]  
  
     La memoria ocupada por la estructura se recupera cuando sale del ámbito.  
  
#### Para asignar las estructuras de datos en la pila  
  
1.  Utilice **new** para asignar las estructuras de datos en la pila y **borrar** para desasignarlos, como se muestra en los ejemplos siguientes:  
  
     [!code-cpp[NVC_MFC_Utilities#5](../mfc/codesnippet/CPP/memory-management-examples_5.cpp)]  
  
##  <a name="_core_allocation_of_an_object"></a> Asignación de un objeto  
  
#### Para asignar un objeto en el cuadro  
  
1.  Declare el objeto como sigue:  
  
     [!code-cpp[NVC_MFC_Utilities#6](../mfc/codesnippet/CPP/memory-management-examples_6.cpp)]  
  
     El destructor del objeto automáticamente se invoca cuando finaliza el objeto su ámbito.  
  
#### Para asignar un objeto en el montón  
  
1.  Utilice el operador de **new** , que devuelve un puntero al objeto, para asignar objetos en el montón.  Utilice el operador de **borrar** para eliminarlos.  
  
     Los ejemplos siguientes de la pila y el cuadro se supone que el constructor de `CPerson` no toma ningún argumento.  
  
     [!code-cpp[NVC_MFC_Utilities#7](../mfc/codesnippet/CPP/memory-management-examples_7.cpp)]  
  
     Si el argumento del constructor de `CPerson` es un puntero a `char`, la instrucción para la asignación del cuadro es:  
  
     [!code-cpp[NVC_MFC_Utilities#8](../mfc/codesnippet/CPP/memory-management-examples_8.cpp)]  
  
     La instrucción para la asignación de pila es:  
  
     [!code-cpp[NVC_MFC_Utilities#9](../mfc/codesnippet/CPP/memory-management-examples_9.cpp)]  
  
## Vea también  
 [Administración de memoria: Asignación del montón](../mfc/memory-management-heap-allocation.md)