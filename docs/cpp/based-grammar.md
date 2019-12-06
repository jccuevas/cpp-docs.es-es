---
title: Gramática __based
ms.date: 11/04/2016
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
ms.openlocfilehash: a8c923b5a111144c539b5bea1b2f47eb58dd1fbd
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857650"
---
# <a name="__based-grammar"></a>Gramática __based

**Específicos de Microsoft**

El direccionamiento de base es útil cuando se necesita el control preciso del segmento en el que se asignan los objetos (datos basados estáticos y dinámicos).

La única forma de direccionamiento de base aceptable en las compilaciones de 32 bits y 64 bits es "basada en un puntero" que define un tipo que contiene un desplazamiento de 32 bits o de 64 bits a una base de 32 bits o de 64 bits o que se basa en **void**.

## <a name="grammar"></a>Gramática

*modificador*-de-intervalo: **__based (**  *base-expresión*  **)**

*base-expresión*: *based-variablebased-Abstract-declaratorsegment-namesegment-Cast*

*based-variable*: *Identifier*

*based-Abstract-declarator*: *abstract-declarator*

tipo *base*: *type-name*

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Punteros con base](../cpp/based-pointers-cpp.md)