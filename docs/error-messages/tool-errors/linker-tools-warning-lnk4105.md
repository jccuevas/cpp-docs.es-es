---
title: Las herramientas del vinculador LNK4105 advertencia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4105
dev_langs:
- C++
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4411421741cf8bf7c714a6322d58bd177e7e7270
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024988"
---
# <a name="linker-tools-warning-lnk4105"></a>Advertencia de las herramientas del vinculador LNK4105

ningún argumento especificado con la opción 'opción'; omitiendo la opción

Esta advertencia sólo aparece cuando el [/libpath](../../build/reference/libpath-additional-libpath.md) opción está establecida. Si no se especifica ningún directorio con esta opción, el vinculador omite la opción y genera este mensaje de advertencia.

Si no es necesario invalidar la configuración de la biblioteca del entorno existente, quite la opción/LIBPATH desde la línea de comandos del vinculador. Si desea utilizar una ruta de acceso de búsqueda alternativos para bibliotecas, especifique la ruta de acceso alternativa después de la opción/LIBPATH.

## <a name="example"></a>Ejemplo

```
link /libpath:c:\filepath\lib bar.obj
```

el vinculador para buscar las bibliotecas requeridas en `c:\filepath\lib` antes de buscar en las ubicaciones predeterminadas.