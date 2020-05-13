---
title: Advertencia de las herramientas del vinculador LNK4105
ms.date: 11/04/2016
f1_keywords:
- LNK4105
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
ms.openlocfilehash: 655a6dfde77984cd0c941ec0d8abb0c4d099c80f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183298"
---
# <a name="linker-tools-warning-lnk4105"></a>Advertencia de las herramientas del vinculador LNK4105

no se especificó ningún argumento con la opción ' opción '; opción omitir

Esta advertencia solo se produce cuando se establece la opción [/LIBPATH](../../build/reference/libpath-additional-libpath.md) . Si no se especifica ningún directorio con esta opción, el vinculador omite la opción y genera este mensaje de advertencia.

Si no necesita invalidar la configuración existente de la biblioteca de entorno, quite la opción/LIBPATH de la línea de comandos del vinculador. Si desea usar una ruta de búsqueda alternativa para las bibliotecas, especifique la ruta de acceso alternativa que sigue a la opción/LIBPATH.

## <a name="example"></a>Ejemplo

```
link /libpath:c:\filepath\lib bar.obj
```

indicaría al enlazador que buscara las bibliotecas necesarias en `c:\filepath\lib` antes de buscar en las ubicaciones predeterminadas.
