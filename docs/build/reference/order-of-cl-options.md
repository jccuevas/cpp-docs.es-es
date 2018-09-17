---
title: Orden de las opciones de CL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ffe9a440396df14823775db335e52bca6cacdb3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725028"
---
# <a name="order-of-cl-options"></a>Orden de las opciones de CL

Las opciones pueden aparecer en cualquier lugar en la línea de comandos de CL, excepto la opción /link, que debe aparecer en último lugar. El compilador comienza con las opciones especificadas en el [variable de entorno de CL](../../build/reference/cl-environment-variables.md) y, a continuación, lee la línea de comandos de izquierda a derecha: procesamiento de archivos de comandos en el orden en que los encuentra. Cada opción se aplica a todos los archivos en la línea de comandos. Si CL encuentra opciones en conflicto, utiliza la opción más a la derecha.

## <a name="see-also"></a>Vea también

[Sintaxis de la línea de comandos del compilador](../../build/reference/compiler-command-line-syntax.md)