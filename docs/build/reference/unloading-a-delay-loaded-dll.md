---
title: Descargar un archivo DLL de carga retrasada
ms.date: 11/04/2016
helpviewer_keywords:
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
ms.openlocfilehash: 284a9cb9268c8c794379c6a5468b0f2b9092b7d0
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413295"
---
# <a name="unloading-a-delay-loaded-dll"></a>Descargar un archivo DLL de carga retrasada

La aplicación auxiliar de carga retrasada proporciona de forma predeterminada comprueba para ver si los descriptores de carga retrasada tienen un puntero y una copia de la tabla de direcciones de importación (IAT) original en el campo pUnloadIAT. Si es así, guardará un puntero en una lista para el descriptor de retraso de importación. Esto permite que la función auxiliar buscar el archivo DLL por nombre que admita la descarga explícitamente ese archivo DLL.

Estas son las estructuras y funciones asociadas para la descarga explícita de un archivo DLL de carga retrasada:

```cpp
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

La estructura UnloadInfo se implementa mediante una clase de C++ que utiliza **LocalAlloc** y **LocalFree** implementaciones como su operador **nueva** y operador  **eliminar** respectivamente. Estas opciones se mantienen en una lista vinculada estándar utilizando __puiHead como el encabezado de la lista.

Llamada a __FUnloadDelayLoadedDLL intentará encontrar el nombre que se proporciona en la lista de archivos DLL de carga (se requiere una coincidencia exacta). Si se encuentra, se copia la copia de la tabla IAT en pUnloadIAT a través de la parte superior de la ejecución IAT para restaurar los punteros de código thunk, la biblioteca se libera con **FreeLibrary**, la coincidencia de **UnloadInfo** registro se desvincula de la lista y elimina y se devuelve TRUE.

El argumento de la función __FUnloadDelayLoadedDLL2 distingue mayúsculas de minúsculas. Por ejemplo, especificaría:

```cpp
__FUnloadDelayLoadedDLL2("user32.DLL");
```

y no:

```cpp
__FUnloadDelayLoadedDLL2("User32.DLL");.
```

## <a name="see-also"></a>Vea también

[Descripción de la función auxiliar](understanding-the-helper-function.md)
