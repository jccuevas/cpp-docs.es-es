---
title: Advertencia de las herramientas del vinculador LNK4070
ms.date: 11/04/2016
f1_keywords:
- LNK4070
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
ms.openlocfilehash: e7139b21f053ea8633356c7194cd719a6a4aef35
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622981"
---
# <a name="linker-tools-warning-lnk4070"></a>Advertencia de las herramientas del vinculador LNK4070

Directiva/out: nombreDeArchivo en. EXP difiere del nombre de archivo de salida 'filename'; se omite la directiva

El `filename` especificado en el [nombre](../../build/reference/name-c-cpp.md) o [biblioteca](../../build/reference/library.md) instrucción cuando se creó el archivo .exp difiere de la salida `filename` que se asume de forma predeterminada o se especificó con el [/OUT](../../build/reference/out-output-file-name.md) opción.

Verá esta advertencia si cambia el nombre de un archivo de salida en el entorno de desarrollo y donde no se actualizó el archivo .def del proyecto. Actualice manualmente el archivo .def para resolver esta advertencia.

Un programa cliente que utiliza el archivo DLL resultante podría tener problemas.