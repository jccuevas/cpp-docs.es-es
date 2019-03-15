---
title: LIBRARY
ms.date: 11/04/2016
f1_keywords:
- LIBRARY
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
ms.openlocfilehash: b43f269726e8925abeefd41aab0edfd57b071035
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811789"
---
# <a name="library"></a>LIBRARY

Indica a LINK para crear un archivo DLL. Al mismo tiempo, LINK crea una biblioteca de importación, a menos que se usa un archivo .exp en la compilación.

```
LIBRARY [library][BASE=address]
```

## <a name="remarks"></a>Comentarios

El *biblioteca* argumento especifica el nombre del archivo DLL. También puede usar el [/OUT](out-output-file-name.md) opción del vinculador para especificar el nombre de la salida del archivo DLL.

La BASE =*dirección* argumento establece la dirección base que el sistema operativo que se usa para cargar el archivo DLL. Este argumento reemplaza la ubicación del archivo DLL predeterminado de 0 x 10000000. Vea la descripción de la [/base](base-base-address.md) opción para obtener más información sobre las direcciones bases.

Recuerde que debe usar el [/DLL](dll-build-a-dll.md) del vinculador cuando se compila un archivo DLL.

## <a name="see-also"></a>Vea también

[Reglas para instrucciones de definición de módulos](rules-for-module-definition-statements.md)
