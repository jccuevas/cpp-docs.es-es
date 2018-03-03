---
title: "Descripción de la función auxiliar | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, helper function
- __delayLoadHelper2 function
- delayimp.lib
- __delayLoadHelper function
- delayhlp.cpp
- delayimp.h
- helper functions
ms.assetid: 6279c12c-d908-4967-b0b3-cabfc3e91d3d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c3a013cf584c37f84331a5ab5dfe74eaa213c851
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="understanding-the-helper-function"></a>Descripción de la función auxiliar
La función auxiliar de carga retrasada admitidos por el vinculador es lo que carga realmente la DLL en tiempo de ejecución. Puede modificar la función auxiliar para personalizar su comportamiento escribiendo su propia función y vincularlo a su programa en lugar de usar la función auxiliar proporcionada en Delayimp.lib. Una función auxiliar sirve a todos los archivos DLL de carga retrasada.  
  
 Puede proporcionar su propia versión de la función auxiliar si desea realizar un procesamiento específico basado en los nombres de las DLL o las importaciones.  
  
 La función auxiliar realiza las siguientes acciones:  
  
-   Comprueba el identificador almacenado para la biblioteca para ver si ya se ha cargado  
  
-   Llamadas **LoadLibrary** al intentar cargar la DLL  
  
-   Llamadas **GetProcAddress** al intentar obtener la dirección del procedimiento  
  
-   Devuelve a la importación de retraso carga código thunk para llamar al punto de entrada cargado actualmente.  
  
 La función auxiliar puede devolver la llamada a un enlace de notificación en el programa después de cada una de las siguientes acciones:  
  
-   Cuando se inicia la función auxiliar  
  
-   Justo antes **LoadLibrary** se llama en la función auxiliar  
  
-   Justo antes **GetProcAddress** se llama en la función auxiliar  
  
-   Si la llamada a **LoadLibrary** en la función auxiliar error  
  
-   Si la llamada a **GetProcAddress** en la función auxiliar error  
  
-   Después de la aplicación auxiliar se realiza la función de procesamiento  
  
 Cada uno de estos puntos de enlace puede devolver un valor que modificará el procesamiento normal de la rutina de aplicación auxiliar de alguna manera excepto volver al thunk de importación de carga de retraso.  
  
 El código auxiliar predeterminado puede encontrarse en Delayhlp.cpp y Delayimp.h (en vc\include) y ésta compilado en Delayimp.lib (en vc\lib). Debe incluir esta biblioteca en las compilaciones a menos que escriba una función auxiliar personalizada.  
  
 Los temas siguientes describen la función auxiliar:  
  
-   [Cambios en la función auxiliar de carga retrasada de DLL desde Visual C++ 6.0](../../build/reference/changes-in-the-dll-delayed-loading-helper-function-since-visual-cpp-6-0.md)  
  
-   [Convenciones de llamada, parámetros y tipo de valor devuelto](../../build/reference/calling-conventions-parameters-and-return-type.md)  
  
-   [Definiciones de estructura y de constante](../../build/reference/structure-and-constant-definitions.md)  
  
-   [Calcular valores necesarios](../../build/reference/calculating-necessary-values.md)  
  
-   [Descargar un archivo DLL de carga retrasada](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)