---
title: Compatibilidad del vinculador con las DLL de carga de retraso | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, linker support
ms.assetid: b2d7e449-2809-42b1-9c90-2c0ca5e31a14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aea4ca6d5391f71f27d59d0192fcf1f832dd6702
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="linker-support-for-delay-loaded-dlls"></a>Compatibilidad del vinculador con las DLL de carga retrasada
El vinculador de Visual C++ ahora es compatible con la carga retrasada de archivos DLL. Esto evita la necesidad de utilizar las funciones de Windows SDK **LoadLibrary** y **GetProcAddress** para implementar la carga retrasada de DLL.  
  
 Antes de Visual C++ 6.0, la única manera de cargar un archivo DLL en tiempo de ejecución era mediante **LoadLibrary** y **GetProcAddress**; el sistema operativo carga el archivo DLL cuando el archivo ejecutable o DLL mediante archivos que se cargó.  
  
 A partir de Visual C++ 6.0, al vincular estáticamente con un archivo DLL, el vinculador proporciona opciones para retrasar cargar el archivo DLL hasta que el programa llama a una función en ese archivo DLL.  
  
 Una aplicación puede retrasar la carga de un archivo DLL mediante la [/DELAYLOAD (importación de carga retrasada)](../../build/reference/delayload-delay-load-import.md) opción del vinculador con una función auxiliar (implementación predeterminada proporcionada por Visual C++). La función auxiliar cargará la DLL en tiempo de ejecución mediante una llamada a **LoadLibrary** y **GetProcAddress** para usted.  
  
 Debe considerar la carga retrasada de una DLL si:  
  
-   El programa no puede llamar a una función en el archivo DLL.  
  
-   No se puede llamar una función en el archivo DLL hasta más adelante en la ejecución del programa.  
  
 La carga retrasada de una DLL se puede especificar durante la generación de una. EXE o. Proyecto DLL. UN ARCHIVO. Proyecto DLL que retrasa la carga de uno o más archivos DLL no debería propio llamar a un punto de entrada de carga retrasada en Dllmain.  
  
 Los temas siguientes describen los archivos DLL de carga retrasada:  
  
-   [Especificar archivos DLL para carga retrasada](../../build/reference/specifying-dlls-to-delay-load.md)  
  
-   [Descargar explícitamente un archivo DLL de carga retrasada](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)  
  
-   [Cargar todas las importaciones para un archivo DLL de carga retrasada](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md)  
  
-   [Enlazar importaciones](../../build/reference/binding-imports.md)  
  
-   [Notificación y control de errores](../../build/reference/error-handling-and-notification.md)  
  
-   [Volcar importaciones de carga retrasada](../../build/reference/dumping-delay-loaded-imports.md)  
  
-   [Restricciones de las DLL de carga retrasada](../../build/reference/constraints-of-delay-loading-dlls.md)  
  
-   [Descripción de la función auxiliar](understanding-the-helper-function.md)  
  
-   [Crear una función auxiliar personalizada](../../build/reference/developing-your-own-helper-function.md)  
  
## <a name="see-also"></a>Vea también  
 [Archivos DLL en Visual C++](../../build/dlls-in-visual-cpp.md)   
 [Vinculación](../../build/reference/linking.md)