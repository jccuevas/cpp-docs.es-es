---
title: Descripción de la función del asistente
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, helper function
- __delayLoadHelper2 function
- delayimp.lib
- __delayLoadHelper function
- delayhlp.cpp
- delayimp.h
- helper functions
ms.assetid: 6279c12c-d908-4967-b0b3-cabfc3e91d3d
ms.openlocfilehash: 3ad193d0101507f43145c6af9f8e6200ab6fcdb5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818000"
---
# <a name="understanding-the-helper-function"></a>Descripción de la función del asistente

La función auxiliar de carga retrasada del enlazador compatible es lo que realmente carga el archivo DLL en tiempo de ejecución. Puede modificar la función auxiliar para personalizar su comportamiento escribiendo su propia función y vincularla a su programa en lugar de usar la función auxiliar proporcionada en Delayimp.lib. Una función auxiliar sirve todas las DLL de carga retrasada.

Puede proporcionar su propia versión de la función auxiliar si desea realizar un procesamiento específico en función de los nombres de las DLL o las importaciones.

La función auxiliar realiza las acciones siguientes:

- Comprueba el identificador almacenado en la biblioteca para ver si ya se ha cargado

- Las llamadas **LoadLibrary** para intentar cargar la DLL.

- Las llamadas **GetProcAddress** al intentar obtener la dirección del procedimiento

- Devuelve a la importación de retraso carga código thunk para llamar al punto de entrada cargado actualmente.

La función auxiliar puede devolver la llamada a un enlace de notificación en el programa después de cada una de las siguientes acciones:

- Cuando se inicia la función auxiliar

- Justo antes **LoadLibrary** se llama en la función auxiliar

- Justo antes **GetProcAddress** se llama en la función auxiliar

- Si la llamada a **LoadLibrary** en la función auxiliar de error

- Si la llamada a **GetProcAddress** en la función auxiliar de error

- Después de la aplicación auxiliar se realiza la función de procesamiento

Cada uno de estos puntos de enlace puede devolver un valor que modificará el procesamiento normal de la rutina de la aplicación auxiliar de alguna manera, excepto el retorno de código thunk la carga de importación de retraso.

El código auxiliar predeterminado puede encontrarse en Delayhlp.cpp y Delayimp.h (en vc\include) y se compila en Delayimp.lib (en vc\lib). Deberá incluir esta biblioteca en las compilaciones a menos que escriba una función auxiliar personalizada.

Los temas siguientes describen la función auxiliar:

- [Cambios en la función auxiliar de carga retrasada de DLL desde Visual C++ 6.0](changes-in-the-dll-delayed-loading-helper-function-since-visual-cpp-6-0.md)

- [Convenciones de llamada, parámetros y tipo de valor devuelto](calling-conventions-parameters-and-return-type.md)

- [Definiciones de estructura y de constante](structure-and-constant-definitions.md)

- [Calcular valores necesarios](calculating-necessary-values.md)

- [Descargar un archivo DLL de carga retrasada](explicitly-unloading-a-delay-loaded-dll.md)

## <a name="see-also"></a>Vea también

[Compatibilidad del vinculador con las DLL de carga retrasada](linker-support-for-delay-loaded-dlls.md)
