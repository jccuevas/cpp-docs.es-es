---
title: Las herramientas del vinculador LNK4070 advertencia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4070
dev_langs:
- C++
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9cfb4ae1c5440742c491d9615a2b4929a9b04f66
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106965"
---
# <a name="linker-tools-warning-lnk4070"></a>Advertencia de las herramientas del vinculador LNK4070

Directiva/out: nombreDeArchivo en. EXP difiere del nombre de archivo de salida 'filename'; se omite la directiva

El `filename` especificado en el [nombre](../../build/reference/name-c-cpp.md) o [biblioteca](../../build/reference/library.md) instrucción cuando se creó el archivo .exp difiere de la salida `filename` que se asume de forma predeterminada o se especificó con el [/OUT](../../build/reference/out-output-file-name.md) opción.

Verá esta advertencia si cambia el nombre de un archivo de salida en el entorno de desarrollo y donde no se actualizó el archivo .def del proyecto. Actualice manualmente el archivo .def para resolver esta advertencia.

Un programa cliente que utiliza el archivo DLL resultante podría tener problemas.