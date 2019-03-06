---
title: Orden de las opciones de CL
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: d87e3214d4829f81258acd00abebced34d7d969d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423695"
---
# <a name="order-of-cl-options"></a>Orden de las opciones de CL

Las opciones pueden aparecer en cualquier lugar en la línea de comandos de CL, excepto la opción /link, que debe aparecer en último lugar. El compilador comienza con las opciones especificadas en el [variable de entorno de CL](../../build/reference/cl-environment-variables.md) y, a continuación, lee la línea de comandos de izquierda a derecha: procesamiento de archivos de comandos en el orden en que los encuentra. Cada opción se aplica a todos los archivos en la línea de comandos. Si CL encuentra opciones en conflicto, utiliza la opción más a la derecha.

## <a name="see-also"></a>Vea también

[Sintaxis de la línea de comandos del compilador](../../build/reference/compiler-command-line-syntax.md)
