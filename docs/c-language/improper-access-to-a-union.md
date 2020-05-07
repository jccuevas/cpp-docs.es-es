---
title: Access incorrecto a una unión
ms.date: 11/04/2016
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
ms.openlocfilehash: 9fd7bdc753f6359a8760e58813f9009411c1bf44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326136"
---
# <a name="improper-access-to-a-union"></a>Access incorrecto a una unión

**ANSI 3.3.2.3** El acceso a un objeto de unión se realiza mediante un miembro de tipo diferente

Si se declara una unión de dos tipos y se almacena un valor, pero se obtiene acceso a la unión con el otro tipo, los resultados no son confiables.

Por ejemplo, se declara una unión de **float** e `int`. Se almacena un valor **float**, pero el programa accede posteriormente al valor como `int`. En esta situación, el valor dependería del almacenamiento interno de los valores **float**. El valor entero no sería confiable.

## <a name="see-also"></a>Vea también

[Estructuras, uniones, enumeraciones y campos de bits](../c-language/structures-unions-enumerations-and-bit-fields.md)
