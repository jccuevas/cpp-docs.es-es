---
title: BIBLIOTECA | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- LIBRARY
dev_langs:
- C++
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43b14e8e8ff4871ba4319c7f4fac5545e72e710b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723559"
---
# <a name="library"></a>LIBRARY

Indica a LINK para crear un archivo DLL. Al mismo tiempo, LINK crea una biblioteca de importación, a menos que se usa un archivo .exp en la compilación.

```
LIBRARY [library][BASE=address]
```

## <a name="remarks"></a>Comentarios

El *biblioteca* argumento especifica el nombre del archivo DLL. También puede usar el [/OUT](../../build/reference/out-output-file-name.md) opción del vinculador para especificar el nombre de la salida del archivo DLL.

La BASE =*dirección* argumento establece la dirección base que el sistema operativo que se usa para cargar el archivo DLL. Este argumento reemplaza la ubicación del archivo DLL predeterminado de 0 x 10000000. Vea la descripción de la [/base](../../build/reference/base-base-address.md) opción para obtener más información sobre las direcciones bases.

Recuerde que debe usar el [/DLL](../../build/reference/dll-build-a-dll.md) del vinculador cuando se compila un archivo DLL.

## <a name="see-also"></a>Vea también

[Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)