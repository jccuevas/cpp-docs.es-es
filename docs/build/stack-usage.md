---
title: Uso de la pila | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 827a129c0b7a444cc5b48ba68a3e360712e1c08e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721544"
---
# <a name="stack-usage"></a>Uso de las pilas

Toda la memoria más allá de la dirección actual de RSP se considera volátil: el sistema operativo o un depurador, puede sobrescribir esta memoria durante una sesión de depuración de usuario o un controlador de interrupción. Por lo tanto, se debe establecer siempre RSP antes de intentar leer o escribir valores en un marco de pila.

En esta sección se explica la asignación de espacio de pila para las variables locales y la **alloca** intrínseco.

- [Asignación de espacio de pila](../build/stack-allocation.md)

- [Construcción del área de pila para el parámetro dinámico](../build/dynamic-parameter-stack-area-construction.md)

- [Tipos de funciones](../build/function-types.md)

- [Alineación de malloc](../build/malloc-alignment.md)

- [alloca](../build/alloca.md)

## <a name="see-also"></a>Vea también

[Convenciones de software x64](../build/x64-software-conventions.md)