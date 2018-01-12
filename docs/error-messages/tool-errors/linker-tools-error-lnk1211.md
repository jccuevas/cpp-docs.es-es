---
title: Las herramientas del vinculador LNK1211 Error | Documentos de Microsoft
ms.date: 12/05/2017
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1211
dev_langs: C++
helpviewer_keywords: LNK1211
ms.assetid: 607400eb-4180-4892-817f-eedfa628af61
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 51150fb2a57f48f04cca97e5f16fe1a28ead2c50
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1211"></a>Error de las herramientas del vinculador LNK1211

> información de tipo precompilado no se encuentra; '*filename*' no vinculado o reemplazado

El *filename* archivo de objeto, compilado mediante [/Yc](../../build/reference/yc-create-precompiled-header-file.md), no se especificó en el comando LINK o se sobrescribió.

Si va a crear una biblioteca de depuración que usa encabezados precompilados, y si se especifica **/Yc** y [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), Visual C++ genera un archivo objeto precompilado que contiene información de depuración. El error produce solo cuando se almacena el archivo objeto precompilado en una biblioteca, usar la biblioteca para crear una imagen ejecutable y los archivos de objeto que se hace referencia no tienen transitivas referencias a cualquiera de las funciones que define el archivo objeto precompilado.

Hay dos métodos para solucionar esta situación:

- Especifique el [/Yd](../../build/reference/yd-place-debug-information-in-object-file.md) opción del compilador para agregar la información de depuración del encabezado precompilado a cada módulo de objeto. Este método es menos aconsejable ya que genera normalmente grandes módulos de objeto que pueden aumentar el tiempo necesario para vincular la aplicación.

- Especifique [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) y pase el nombre de cualquier cadena arbitraria, cuando se crea un archivo de encabezado precompilado que no contiene ninguna definición de función. Esto indica al compilador que cree un símbolo en el archivo objeto precompilado y emita una referencia a ese símbolo en cada archivo de objeto que utiliza el archivo de encabezado precompilado que está asociado con el archivo objeto precompilado.

Cuando se compila un módulo con **/Yc** y **/Yl**, el compilador crea un símbolo similar a `__@@_PchSym_@00@...@symbol_name`, donde los puntos suspensivos (...) representan una cadena de caracteres generada por el compilador y lo almacena en el módulo de objeto. Cualquier archivo de código fuente que se compilan con este encabezado precompilado hace referencia al símbolo especificado, que hace que el vinculador para que incluya el módulo de objeto y su información de depuración de la biblioteca.
