---
title: "Descargar un archivo DLL de carga retrasada | Microsoft Docs"
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
  - "__FUnloadDelayLoadedDLL2"
  - "carga retrasada de archivos DLL, descargar"
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Descargar un archivo DLL de carga retrasada
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La rutina auxiliar de carga retrasada que se proporciona de forma predeterminada comprueba si los descriptores de carga retrasada tienen un puntero y una copia de la tabla de direcciones de importación \(IAT\) original en el campo pUnloadIAT.  Si es así, guardará un puntero en una lista para el descriptor de importación de carga retrasada.  De este modo, la función auxiliar puede buscar la DLL por el nombre y permitir que se descargue de forma explícita.  
  
 Estas son las estructuras y funciones asociadas para la descarga explícita de una DLL de carga retrasada:  
  
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
  
 La estructura UnloadInfo se implementa mediante una clase de C\+\+ que utiliza las implementaciones **LocalAlloc** y **LocalFree** como operador **new** y operador **delete**, respectivamente.  Estas opciones se conservan en una lista vinculada estándar utilizando \_\_puiHead como encabezado de la lista.  
  
 La llamada a \_\_FUnloadDelayLoadedDLL intentará encontrar el nombre proporcionado en la lista de las DLL cargadas \(se requiere una coincidencia exacta\).  Si se encuentra, la copia de la tabla IAT en pUnloadIAT se copia al principio de la tabla IAT en ejecución para restaurar los punteros del thunk, la biblioteca se libera con **FreeLibrary**, el registro coincidente de **UnloadInfo** se desvincula de la lista y se elimina, y se devuelve TRUE.  
  
 El argumento de la función \_\_FUnloadDelayLoadedDLL2 hace distinción entre mayúsculas y minúsculas.  Por ejemplo, se debe especificar:  
  
```  
__FUnloadDelayLoadedDLL2("user32.DLL");  
```  
  
 y no:  
  
```  
__FUnloadDelayLoadedDLL2("User32.DLL");.  
```  
  
## Vea también  
 [Understanding the Helper Function](http://msdn.microsoft.com/es-es/6279c12c-d908-4967-b0b3-cabfc3e91d3d)