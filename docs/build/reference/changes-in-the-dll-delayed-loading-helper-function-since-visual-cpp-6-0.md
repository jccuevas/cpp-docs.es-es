---
title: "Cambios en la funci&#243;n auxiliar de carga retrasada de DLL desde Visual C++ 6.0 | Microsoft Docs"
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
  - "__delayLoadHelper2 (función)"
  - "carga retrasada de archivos DLL, cambios"
  - "funciones auxiliares, cambios"
  - "PFromRva (método)"
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Cambios en la funci&#243;n auxiliar de carga retrasada de DLL desde Visual C++ 6.0
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Si tiene varias versiones de Visual C\+\+ en el equipo o ha definido una función auxiliar propia, es posible que le afecten los cambios realizados en la función auxiliar de carga retrasada de la DLL.  Por ejemplo:  
  
-   **\_\_delayLoadHelper** es ahora **\_\_delayLoadHelper2**  
  
-   **\_\_pfnDliNotifyHook** es ahora **\_\_pfnDliNotifyHook2**  
  
-   **\_\_pfnDliFailureHook** es ahora **\_\_pfnDliFailureHook2**  
  
-   **\_\_FUnloadDelayLoadedDLL** es ahora **\_\_FUnloadDelayLoadedDLL2**  
  
> [!NOTE]
>  Si está utilizando la función auxiliar predeterminada, estos cambios no le afectarán.  Además, no se producen cambios relacionados con el modo de llamar al vinculador.  
  
## Varias versiones de Visual C\+\+  
 Si dispone de varias versiones de Visual C\+\+ en su equipo, asegúrese de que el vinculador coincide con delayimp.lib.  En caso contrario, se producirá un error del vinculador y se indicará que `___delayLoadHelper2@8` o `___delayLoadHelper@8` aparecen como símbolos externos no resueltos.  El primero implica un vinculador nuevo con una versión anterior de delayimp.lib, y el segundo implica un vinculador antiguo con una versión nueva de delayimp.lib.  
  
 Si obtiene un error de vinculador sin resolver, ejecute [dumpbin \/linkermember](../../build/reference/linkermember.md):1 en el archivo delayimp.lib que espera que contenga la función auxiliar para ver qué función auxiliar se define en su lugar.  La función auxiliar también puede estar definida en un archivo objeto; ejecute [dumpbin \/symbols](../../build/reference/symbols.md) y busque `delayLoadHelper(2)`.  
  
 Si sabe que tiene el vinculador de Visual C\+\+ 6.0, entonces:  
  
-   Ejecute **dumpbin** en el archivo .lib u .obj de la rutina auxiliar de carga retrasada para determinar si éste define **\_\_delayLoadHelper2**.  En caso contrario, el vínculo producirá un error.  
  
-   Defina **\_\_delayLoadHelper** en el archivo .lib u .obj de la rutina auxiliar de carga retrasada.  
  
## Función auxiliar definida por el usuario  
 Si ha definido una función auxiliar propia y está utilizando la versión actual de Visual C\+\+, siga este procedimiento:  
  
-   Cambie el nombre de la función auxiliar denominándola **\_\_delayLoadHelper2**.  
  
-   Dado que los punteros en el descriptor de carga retrasada \(ImgDelayDescr en delayimp.h\) se han cambiado de direcciones absolutas \(VA\) a direcciones relativas \(RVA\) para el funcionamiento correcto en los programas de 32 y 64 bits, es necesario convertirlos de nuevo en punteros.  Se ha introducido una nueva función, PFromRva, ubicada en delayhlp.cpp.  Esta función se puede utilizar en cada uno de los campos del descriptor para volver a convertirlos en punteros de 32 ó 64 bits.  La función auxiliar de carga retrasada predeterminada sigue siendo una plantilla excelente para utilizarla como ejemplo.  
  
## Cargar todas las importaciones para un archivo DLL de carga retrasada  
 El vinculador puede cargar todas las importaciones de un archivo DLL para el que se ha especificado la carga retrasada.  Vea [Cargar todas las importaciones para un archivo DLL de carga retrasada](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md) para obtener más información.  
  
## Vea también  
 [Understanding the Helper Function](http://msdn.microsoft.com/es-es/6279c12c-d908-4967-b0b3-cabfc3e91d3d)