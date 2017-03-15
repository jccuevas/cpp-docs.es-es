---
title: "Descripci&#243;n de la funci&#243;n auxiliar | Microsoft Docs"
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
  - "__delayLoadHelper (función)"
  - "__delayLoadHelper2 (función)"
  - "carga retrasada de archivos DLL, función auxiliar"
  - "delayhlp.cpp"
  - "delayimp.h"
  - "delayimp.lib"
  - "funciones auxiliares"
ms.assetid: 6279c12c-d908-4967-b0b3-cabfc3e91d3d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Descripci&#243;n de la funci&#243;n auxiliar
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La función auxiliar para efectuar carga retrasada compatible con el vinculador es lo que carga realmente la DLL en tiempo de ejecución.  Se puede modificar la función auxiliar para personalizar su comportamiento creando una función propia y vinculándola al programa, en lugar de usar la función auxiliar proporcionada en Delayimp.lib.  Una función auxiliar sirve a todas las DLL de carga retrasada.  
  
 Se puede proporcionar una versión propia de la función auxiliar si se desea realizar un procesamiento específico basado en los nombres de las DLL o las importaciones.  
  
 La función auxiliar realiza las siguientes acciones:  
  
-   Comprueba el identificador almacenado para la biblioteca con el fin de ver si ya se ha cargado.  
  
-   Llama a **LoadLibrary** para intentar cargar la DLL.  
  
-   Llama a **GetProcAddress** para intentar obtener la dirección del procedimiento.  
  
-   Vuelve al thunk de importación de carga retrasada para llamar al punto de entrada cargado actualmente.  
  
 La función auxiliar puede devolver la llamada a un enlace de notificación del programa después de cada una de las siguientes acciones:  
  
-   Cuando se inicia la función auxiliar.  
  
-   Inmediatamente antes de que se llame a **LoadLibrary** en la función auxiliar.  
  
-   Inmediatamente antes de que se llame a **GetProcAddress** en la función auxiliar.  
  
-   Si se produce un error en la llamada a **LoadLibrary** en la función auxiliar.  
  
-   Si se produce un error en la llamada a **GetProcAddress** en la función auxiliar.  
  
-   Después del procesamiento de la función auxiliar.  
  
 Cada uno de estos puntos de enlace puede devolver un valor que modificará, en cierto modo, el procesamiento normal de la rutina auxiliar, excepto el thunk de importación de carga retrasada.  
  
 El código auxiliar predeterminado puede encontrarse en Delayhlp.cpp y Delayimp.h \(en vc\\include\) y ésta compilado en Delayimp.lib \(en vc\\lib\).  Será necesario incluir esta biblioteca en las compilaciones, a menos que se escriba una función auxiliar propia.  
  
 Los temas siguientes describen la función auxiliar:  
  
-   [Cambios en la función auxiliar de carga retrasada de DLL desde Visual C\+\+ 6.0](../../build/reference/changes-in-the-dll-delayed-loading-helper-function-since-visual-cpp-6-0.md)  
  
-   [Convenciones de llamada, parámetros y tipo de valor devuelto](../../build/reference/calling-conventions-parameters-and-return-type.md)  
  
-   [Definiciones de estructura y de constante](../../build/reference/structure-and-constant-definitions.md)  
  
-   [Calcular valores necesarios](../../build/reference/calculating-necessary-values.md)  
  
-   [Descargar un archivo DLL de carga retrasada](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)  
  
## Vea también  
 [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)