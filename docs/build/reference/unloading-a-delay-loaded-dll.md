---
title: Descargar una archivo DLL de carga retrasada | Documentos de Microsoft
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
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b47969da4c560f28c07ac09caef83873e362ddc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="unloading-a-delay-loaded-dll"></a>Descargar un archivo DLL de carga retrasada
La aplicación auxiliar de carga retrasada proporciona de forma predeterminada se comprueba para ver si los descriptores de carga retrasada tienen un puntero y una copia de la tabla de direcciones de importación (IAT) original en el campo pUnloadIAT. Si es así, guardará un puntero en una lista para el descriptor de retraso de importación. Esto permite que la función auxiliar buscar el archivo DLL por nombre para admitir la descarga explícitamente ese archivo DLL.  
  
 Estas son las estructuras y funciones asociadas para descargar explícitamente una archivo DLL de carga retrasada:  
  
```  
//  
// Unload support from delayimp.h  
//  
  
// routine definition; takes a pointer to a name to unload  
  
ExternC  
BOOL WINAPI  
__FUnloadDelayLoadedDLL2(LPCSTR szDll);  
  
// structure definitions for the list of unload records  
typedef struct UnloadInfo * PUnloadInfo;  
typedef struct UnloadInfo {  
    PUnloadInfo     puiNext;  
    PCImgDelayDescr pidd;  
    } UnloadInfo;  
  
// from delayhlp.cpp  
// the default delay load helper places the unloadinfo records in the   
// list headed by the following pointer.  
ExternC  
PUnloadInfo __puiHead;  
```  
  
 La estructura UnloadInfo se implementa mediante una clase de C++ que utiliza **LocalAlloc** y **LocalFree** implementaciones como su operador **nueva** and (operador)  **eliminar** respectivamente. Estas opciones se mantienen en una lista vinculada estándar utilizando __puiHead como el encabezado de la lista.  
  
 Llamada a __FUnloadDelayLoadedDLL intentará encontrar el nombre proporcionado en la lista de las DLL cargadas (se requiere una coincidencia exacta). Si se encuentra, se copia la copia de la tabla IAT en pUnloadIAT sobre la parte superior de la ejecución IAT para restaurar los punteros del thunk, la biblioteca se libera con **FreeLibrary**, la búsqueda de coincidencias **UnloadInfo** registro se desvincula de la lista y elimina y se devuelve TRUE.  
  
 El argumento de la función __FUnloadDelayLoadedDLL2 distingue mayúsculas de minúsculas. Por ejemplo, debe especificar:  
  
```  
__FUnloadDelayLoadedDLL2("user32.DLL");  
```  
  
 y que no:  
  
```  
__FUnloadDelayLoadedDLL2("User32.DLL");.  
```  
  
## <a name="see-also"></a>Vea también  
 [Descripción de la función auxiliar](understanding-the-helper-function.md)