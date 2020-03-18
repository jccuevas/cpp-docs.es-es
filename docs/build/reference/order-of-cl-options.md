---
title: Orden de las opciones deC++cl ()-Visual Studio
ms.date: 12/14/2018
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: 6c57a68dd15d82a9d6a01bfe145374bda6eb1510
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439200"
---
# <a name="order-of-cl-options"></a>Orden de las opciones de CL

Las opciones pueden aparecer en cualquier parte de la línea de comandos de CL, excepto en la opción/Link, que debe aparecer en último lugar. El compilador comienza con las opciones especificadas en la [variable de entorno de cl](cl-environment-variables.md) y, a continuación, lee la línea de comandos de izquierda a derecha, y procesa los archivos de comandos en el orden en que los encuentra. Cada opción se aplica a todos los archivos de la línea de comandos. Si CL encuentra opciones en conflicto, usa la opción situada más a la derecha.

## <a name="see-also"></a>Consulte también

[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
