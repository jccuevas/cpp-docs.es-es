---
title: Naked (C)
ms.date: 11/04/2016
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
ms.openlocfilehash: 519d7bceb700e9862f0d0025b755cf28fb0fbc0c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325785"
---
# <a name="naked-c"></a>Naked (C)

**Específicos de Microsoft**

El atributo de clase de almacenamiento naked es una extensión específica de Microsoft para el lenguaje C. El compilador genera código sin código de prólogo y epílogo para las funciones declaradas con el atributo de clase de almacenamiento naked. Las funciones naked son útiles cuando se necesita escribir secuencias de código de prólogo/epílogo propias mediante código ensamblador alineado. Las funciones naked son útiles para escribir controladores de dispositivos virtuales.

Para obtener información concreta sobre cómo se usa el atributo naked, vea [Funciones naked](../c-language/naked-functions.md).

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Atributos extendidos de clase de almacenamiento de C](../c-language/c-extended-storage-class-attributes.md)
