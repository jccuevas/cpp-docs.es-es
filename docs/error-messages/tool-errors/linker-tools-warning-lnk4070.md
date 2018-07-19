---
title: Las herramientas del vinculador LNK4070 advertencia | Documentos de Microsoft
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
ms.openlocfilehash: 9e4599e96552f1b98ef0b1af8d38995ebbe5a83e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302508"
---
# <a name="linker-tools-warning-lnk4070"></a>Advertencia de las herramientas del vinculador LNK4070
Directiva/out: nombredearchivo de. EXP difiere del nombre de archivo de salida 'nombredearchivo'; se omite la directiva  
  
 El `filename` especificado en el [nombre](../../build/reference/name-c-cpp.md) o [biblioteca](../../build/reference/library.md) instrucción cuando se creó el archivo .exp difiere de la salida `filename` que se asume de forma predeterminada o se especificó con el [/OUT](../../build/reference/out-output-file-name.md) opción.  
  
 Si cambia el nombre de un archivo de salida en el entorno de desarrollo y donde no se actualizó el archivo del proyecto .def aparecerá esta advertencia. Actualizar manualmente el archivo .def para resolver esta advertencia.  
  
 Un programa cliente que utiliza el archivo DLL resultante podría encontrar problemas.