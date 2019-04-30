---
title: Error de las herramientas del vinculador LNK1211
ms.date: 12/05/2017
f1_keywords:
- LNK1211
helpviewer_keywords:
- LNK1211
ms.assetid: 607400eb-4180-4892-817f-eedfa628af61
ms.openlocfilehash: 7c918cacb87460c2aad30285b750d9b170425534
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242674"
---
# <a name="linker-tools-error-lnk1211"></a>Error de las herramientas del vinculador LNK1211

> información de tipo precompilado que no se encuentra; '*filename*' no vinculado o reemplazado

El *filename* archivo objeto compilado con [/Yc](../../build/reference/yc-create-precompiled-header-file.md), no se especificó en el comando de vínculo o se ha sobrescrito.

Si va a crear una biblioteca de depuración que usa encabezados precompilados y si se especifica **/Yc** y [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), Visual C++ genera un archivo objeto precompilado que contiene información de depuración. El error produce sólo cuando se almacena el archivo objeto precompilado en una biblioteca, use la biblioteca para crear una imagen ejecutable y los archivos de objeto que se hace referencia no tienen ninguna referencia transitiva a cualquiera de las funciones que define el archivo objeto precompilado.

Hay dos métodos para solucionar esta situación:

- Especifique el [/Yd](../../build/reference/yd-place-debug-information-in-object-file.md) opción del compilador para agregar la información de depuración del encabezado precompilado a cada módulo de objeto. Este método es menos deseable, ya que genera normalmente los módulos de objetos grandes que pueden aumentar el tiempo necesario para vincular la aplicación.

- Especificar [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) y pase el nombre de cualquier cadena arbitraria, cuando se crea un archivo de encabezado precompilado que no contiene ninguna definición de función. Esto indica al compilador para crear un símbolo en el archivo objeto precompilado y para emitir una referencia a ese símbolo en cada archivo de objeto que se usó el archivo de encabezado precompilado que está asociado con el archivo objeto precompilado.

Cuando se compila un módulo con **/Yc** y **/Yl**, el compilador crea un símbolo similar a `__@@_PchSym_@00@...@symbol_name`, donde los puntos suspensivos (...) representa una cadena de caracteres generado por el compilador y lo almacena en el módulo de objeto. Cualquier archivo de código fuente que se compila con el encabezado precompilado hace referencia al símbolo especificado, lo que hace que el vinculador que incluya el módulo de objeto y su información de depuración de la biblioteca.
