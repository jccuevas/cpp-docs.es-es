---
title: "Administraci&#243;n de memoria: asignaci&#243;n de marcos | Microsoft Docs"
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
helpviewer_keywords: 
  - "detectar pérdidas de memoria"
  - "asignación de marcos"
  - "variables de marco"
  - "variables de marco, eliminación automática de"
  - "asignación en el montón, frente a asignación de marcos"
  - "asignación de memoria, marcos"
  - "pérdidas de memoria, asignar objetos del marco"
  - "pérdidas de memoria, detectar"
  - "pérdidas de memoria, asignación de marcos"
  - "memoria, detectar pérdidas"
  - "memoria, reclamar"
  - "memoria, liberación"
  - "ámbito, variables de marco"
  - "marcos de pila"
  - "variables, variables de marco"
ms.assetid: 945a211a-6f4f-4679-bb6a-b0f2a0d4a6c1
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Administraci&#243;n de memoria: asignaci&#243;n de marcos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La asignación en el cuadro toma su nombre de “marco de pila” se configurar siempre que se llame a una función.  El marco de pila es un área de memoria que almacena temporalmente los argumentos a la función así como las variables que se local definido a la función.  Las variables de capítulos a menudo se denominan variables “automáticas” porque el compilador automáticamente asigna espacio para ellos.  
  
 Hay dos características clave de las asignaciones del cuadro.  Primero, cuando define una variable local, suficiente espacio se asigna en el marco de pila para la variable completa, aunque es una matriz o una estructura de datos grande.  En segundo lugar, las variables de marco automáticamente se eliminan cuando salen del ámbito:  
  
 [!code-cpp[NVC_MFC_Utilities#10](../mfc/codesnippet/CPP/memory-management-frame-allocation_1.cpp)]  
  
 Para las variables de la función local, esta transición de ámbito ocurre cuando sale de la función, pero el ámbito de una variable de cuadro puede ser menor que una función si se utilizan llaves anidadas.  Esta eliminación automática de las variables de marco es muy importante.  En el caso de tipos primitivos simples \(como `int` o **byte**\), las matrices, o estructuras de datos, la eliminación automática reclaman simplemente la memoria utilizada por la variable.  Dado que la variable ha salido del ámbito, no será accesible de todos modos.  En el caso de objetos de C\+\+, sin embargo, el proceso de eliminación automática es un poco más complejo.  
  
 Cuando un objeto se define como variable de marco, invoque a su constructor automáticamente en el punto donde se encuentra la definición.  Cuando el objeto salga del ámbito, el destructor se invoca antes de que la memoria del objeto se reclame.  Esta construcción y destrucción automáticas pueden ser muy procedimientos, pero debe tener en cuenta las llamadas automáticas, especialmente al destructor.  
  
 La ventaja clave de asignar objetos en el cuadro es que automáticamente se eliminarán.  Cuando asigna los objetos en el cuadro, no tiene que preocuparse de objetos olvidados produciendo pérdidas de memoria. \(Para obtener detalles sobre las pérdidas de memoria, vea el artículo [Detectar pérdidas de memoria en MFC](http://msdn.microsoft.com/es-es/29ee8909-96e9-4246-9332-d3a8aa8d4658).\) Una desventaja de la asignación del cuadro es que las variables de marco no se pueden utilizar fuera del ámbito.  Otro factor de elegir la asignación del cuadro en la asignación de pila es que para las estructuras grandes y objetos, suele ser preferible utilizar la pila en lugar de la pila para el almacenamiento desde el espacio de pila se limita a menudo.  
  
## Vea también  
 [Administración de memoria](../mfc/memory-management.md)