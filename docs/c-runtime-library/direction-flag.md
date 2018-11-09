---
title: Marca de dirección
ms.date: 11/04/2016
f1_keywords:
- c.flags
helpviewer_keywords:
- direction flag
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
ms.openlocfilehash: ae2936c4e07a434a49d931ed60a7d7dee74e3177
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534890"
---
# <a name="direction-flag"></a>Marca de dirección

La marca de dirección es una marca de CPU específica de procesadores Intel 80x86. Se aplica a todas las instrucciones de ensamblado que usan el prefijo REP (repeticiones), como MOVS, MOVSD, MOVSW y otros. Las direcciones proporcionadas para las instrucciones aplicables se incrementan si está desactivada la marca de dirección.

Las rutinas de tiempo de ejecución de C suponen que la marca de dirección está desactivada. Si usa otras funciones con las funciones de tiempo de ejecución de C, debe asegurarse de que las demás funciones dejan la marca de dirección tal cual o que la restauran a su condición original. Esperar que la marca de dirección se desactive al realizar la entrada hace que el código de tiempo de ejecución resulte más rápido y eficaz.

Las funciones de la biblioteca en tiempo de ejecución de C, como las rutinas de manipulación de cadenas y de manipulación de búfer, esperan que la marca de dirección se desactive.

## <a name="see-also"></a>Vea también

[Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)