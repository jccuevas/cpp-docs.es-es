---
title: "Diferencias entre aplicaciones y archivos DLL | Microsoft Docs"
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
  - "aplicaciones [C++], frente a DLL"
  - "DLL [C++], aplicaciones"
  - "archivos ejecutables [C++], DLL frente a aplicaciones"
ms.assetid: 8f271523-d8d0-4ad1-84d2-0c5645d7fd5b
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Diferencias entre aplicaciones y archivos DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Aunque tanto los archivos DLL como las aplicaciones son módulos de programas ejecutables, se diferencian en varios aspectos.  Para el usuario final, la diferencia más obvia es que los archivos DLL no son programas directamente ejecutables.  Desde el punto de vista del sistema, hay dos diferencias fundamentales entre las aplicaciones y los archivos DLL:  
  
-   Una aplicación puede tener varias instancias ejecutándose simultáneamente en el sistema, mientras que sólo se puede ejecutar una instancia de un archivo DLL.  
  
-   A diferencia de un archivo DLL, una aplicación puede ser propietaria de elementos como una pila, una memoria global, identificadores de archivo y una cola de mensajes.  
  
## ¿Qué desea hacer?  
  
-   [Exportar de un archivo DLL](../build/exporting-from-a-dll.md)  
  
-   [Vincular un ejecutable a un archivo DLL](../build/linking-an-executable-to-a-dll.md)  
  
-   [Inicializar un archivo DLL](../build/initializing-a-dll.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Ventajas de utilizar archivos DLL](../build/advantages-of-using-dlls.md)  
  
-   [Archivos DLL que no están basados en MFC: información general](../build/non-mfc-dlls-overview.md)  
  
-   [Archivos DLL estándar vinculados estáticamente a MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Archivos DLL estándar vinculados dinámicamente a MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Archivos DLL de extensión: información general](../build/extension-dlls-overview.md)  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)