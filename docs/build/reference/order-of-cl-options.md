---
title: 'Orden de las opciones de CL (C++): Visual Studio'
ms.date: 12/14/2018
f1_keywords:
- cl
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: 93907265bed8141b5c63edd5e75d632e060351fe
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811646"
---
# <a name="order-of-cl-options"></a>Orden de las opciones de CL

Las opciones pueden aparecer en cualquier lugar en la línea de comandos de CL, excepto la opción /link, que debe aparecer en último lugar. El compilador comienza con las opciones especificadas en el [variable de entorno de CL](cl-environment-variables.md) y, a continuación, lee la línea de comandos de izquierda a derecha: procesamiento de archivos de comandos en el orden en que los encuentra. Cada opción se aplica a todos los archivos en la línea de comandos. Si CL encuentra opciones en conflicto, utiliza la opción más a la derecha.

## <a name="see-also"></a>Vea también

[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
