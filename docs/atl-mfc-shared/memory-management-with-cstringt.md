---
title: "Memory Management with CStringT | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStringT"
  - "ATL::CStringT"
  - "ATL.CStringT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFixedStringT class, description of"
  - "CString objects, administración de memoria"
  - "CStringT class, administración de memoria"
  - "IAtlStringMgr class, utilizar"
  - "memoria [C++], uso"
  - "cadenas [C++], custom memory management"
  - "cadenas [C++], administración de memoria"
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Memory Management with CStringT
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

la clase [CStringT](../atl-mfc-shared/reference/cstringt-class.md) es una clase de plantilla utilizada para manipular las cadenas de caracteres de longitud variable.  Memoria para contener estas cadenas se asigna y se libera a través de un objeto de administrador de cadena, asociado a cada instancia de `CStringT`.  MFC y ATL proporcionan las instancias predeterminadas de `CStringT`, denominadas `CString`, `CStringA`, y `CStringW`, que manipulan cadenas de diferentes tipos de caracteres.  Estos tipos de caracteres son de **TCHAR**con tipo, de `char`, y de `wchar_t`, respectivamente.  Estos tipos de cadena predeterminados usan un administrador de la cadena que asigna memoria de montón de proceso \(en ATL\) o del montón de CRT \(en MFC\).  para las aplicaciones típicas, este esquema de asignación de memoria es suficiente.  Sin embargo, como código que realiza un uso intensivo de cadenas \(o código multiproceso\) que los administradores de memoria predeterminados no pueden realizar óptimo.  Este tema describe cómo reemplazar el comportamiento predeterminado de administración de memoria de `CStringT`, creando los asignadores optimizados específicamente para la tarea a mano.  
  
-   [Implementación de un administrador de cadena personalizado \(método básico\)](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)  
  
-   [Evasión de contención de pila](../atl-mfc-shared/avoidance-of-heap-contention.md)  
  
-   [Implementación de un administrador de cadena personalizado \(método avanzadas\)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)  
  
-   [CFixedStringT: Un ejemplo de un administrador de cadena personalizado](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)  
  
## Vea también  
 [Ejemplo CustomString](../top/visual-cpp-samples.md)