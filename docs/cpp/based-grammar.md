---
title: Gramática __based
ms.date: 11/04/2016
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
ms.openlocfilehash: 8dec9b0bcc7db25e2ec4c39b9d907922691bfc05
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558150"
---
# <a name="based-grammar"></a>Gramática __based

## <a name="microsoft-specific"></a>Específicos de Microsoft

El direccionamiento de base es útil cuando se necesita el control preciso del segmento en el que se asignan los objetos (datos basados estáticos y dinámicos).

La única forma de direccionamiento de base aceptable en compilaciones de 32 bits y 64 bits es "basado en un puntero" que define un tipo que contiene un desplazamiento de 32 bits o 64 bits a una base de 32 bits o 64 bits o basado en **void**.

## <a name="grammar"></a>Gramática

*modificador de intervalo en función*: **__based (***base expresión***)** 

*expresión base*: *based-variablebased-abstract-declaratorsegment-namesegment-cast*

*en función de variable*: *identificador*

*en función-abstract-declarator*: *abstract-declarator*

*tipo base*: *nombre de tipo*

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Punteros con base](../cpp/based-pointers-cpp.md)