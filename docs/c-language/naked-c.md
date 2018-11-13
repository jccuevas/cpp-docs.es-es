---
title: Naked (C)
ms.date: 11/04/2016
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
ms.openlocfilehash: c79502d1793df2a3340eed26c67cca5d2a8b0d9b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537246"
---
# <a name="naked-c"></a>Naked (C)

**Específicos de Microsoft**

El atributo de clase de almacenamiento naked es una extensión específica de Microsoft para el lenguaje C. El compilador genera código sin código de prólogo y epílogo para las funciones declaradas con el atributo de clase de almacenamiento naked. Las funciones naked son útiles cuando se necesita escribir secuencias de código de prólogo/epílogo propias mediante código ensamblador alineado. Las funciones naked son útiles para escribir controladores de dispositivos virtuales.

Para obtener información concreta sobre cómo se usa el atributo naked, vea [Funciones naked](../c-language/naked-functions.md).

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Atributos extendidos de clase de almacenamiento de C](../c-language/c-extended-storage-class-attributes.md)