---
title: Error PRJ0044 al compilar del proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0044
dev_langs:
- C++
helpviewer_keywords:
- PRJ0044
ms.assetid: 5d78c45a-f9e9-4d2b-a3b6-5a5d1421ab84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac5ac11ae8622e2f153effd2cfb5ab0055414331
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028498"
---
# <a name="project-build-error-prj0044"></a>Error PRJ0044 al compilar el proyecto

La propiedad 'Dependencias adicionales' para la regla de compilación personalizada 'rule' asignada al archivo 'archivo' no es válida. La propiedad contenía una cadena 'string' que se evalúa en 'value'.

El **dependencias adicionales** propiedad evaluado como una cadena vacía, o en una cadena que contiene caracteres no válidos (es decir, cualquier carácter que no pueden estar en un nombre de archivo o directorio). Las reglas de compilación personalizadas necesitan la salida de la acción de compilación.

Para obtener más información, consulte [Specifying Custom Build Tools](../../ide/specifying-custom-build-tools.md).

## <a name="see-also"></a>Vea también

[Errores y advertencias de compilación del proyecto (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)