---
title: Uso de las pilas
ms.date: 11/04/2016
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: 5ee9da50a03e1137ed6543cd349481148c9127d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452226"
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