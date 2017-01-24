---
title: "Compatibilidad del vinculador con las DLL de carga retrasada | Microsoft Docs"
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
  - "carga retrasada de archivos DLL, compatibilidad con el vinculador"
ms.assetid: b2d7e449-2809-42b1-9c90-2c0ca5e31a14
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compatibilidad del vinculador con las DLL de carga retrasada
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El vinculador de Visual C\+\+ admite actualmente la carga retrasada de las DLL.  Esto evita la necesidad de utilizar las funciones **LoadLibrary** y **GetProcAddress** de [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] para implementar la carga retrasada de las DLL.  
  
 Antes de Visual C\+\+ 6.0, la única forma de cargar una DLL en tiempo de ejecución era usando **LoadLibrary**y**GetProcAddress**; el sistema operativo cargaba la DLL una vez cargado el ejecutable o la DLL que lo utilizaba.  
  
 A partir de Visual C\+\+ 6.0, al vincular estáticamente con una DLL, el vinculador proporciona opciones para retrasar la carga de la DLL hasta que el programa llame a una función dentro de esa DLL.  
  
 Una aplicación puede retrasar la carga de una DLL usando la opción [\/DELAYLOAD \(Importación de carga retrasada\)](../../build/reference/delayload-delay-load-import.md) del vinculador con una función auxiliar \(implementación predeterminada proporcionada por Visual C\+\+\).  La función auxiliar cargará la DLL en tiempo de ejecución llamando a **LoadLibrary** y **GetProcAddress**.  
  
 Se debe considerar la carga retrasada de una DLL si:  
  
-   El programa no puede llamar a una función dentro de la DLL.  
  
-   Es posible que no se llame a una función de la DLL hasta bien avanzada la ejecución del programa.  
  
 La carga retrasada de una DLL se puede especificar durante la compilación de un proyecto .EXE o .DLL.  Un proyecto DLL que retrasa la carga de una o varias DLL no debe llamar a un punto de entrada de carga retrasada en Dllmain.  
  
 Los temas siguientes describen la carga retrasada de las DLL:  
  
-   [Especificar archivos DLL para carga retrasada](../../build/reference/specifying-dlls-to-delay-load.md)  
  
-   [Descargar explícitamente un archivo DLL de carga retrasada](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)  
  
-   [Cargar todas las importaciones para un archivo DLL de carga retrasada](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md)  
  
-   [Enlazar importaciones](../../build/reference/binding-imports.md)  
  
-   [Notificación y control de errores](../../build/reference/error-handling-and-notification.md)  
  
-   [Volcar importaciones de carga retrasada](../../build/reference/dumping-delay-loaded-imports.md)  
  
-   [Restricciones de las DLL de carga retrasada](../../build/reference/constraints-of-delay-loading-dlls.md)  
  
-   [Descripción de la función auxiliar](http://msdn.microsoft.com/es-es/6279c12c-d908-4967-b0b3-cabfc3e91d3d)  
  
-   [Crear una función auxiliar personalizada](../../build/reference/developing-your-own-helper-function.md)  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../../build/dlls-in-visual-cpp.md)   
 [Vinculación](../../build/reference/linking.md)