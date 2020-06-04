---
title: Error del evaluador de expresiones CXX0065
ms.date: 11/04/2016
f1_keywords:
- CXX0065
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
ms.openlocfilehash: b4120deec3c8e7ce14e381f782904cf83a588e43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184429"
---
# <a name="expression-evaluator-error-cxx0065"></a>Error del evaluador de expresiones CXX0065

la variable necesita el marco de pila

Una expresión contenía una variable que existe dentro del ámbito actual, pero aún no se ha creado.

Este error puede producirse cuando se ha ejecutado paso a paso el prólogo de una función pero aún no se ha configurado el marco de pila para la función, o si se ha ejecutado paso a paso el código de salida de la función.

Recorra paso a paso el código de prólogo hasta que se haya configurado el marco de pila antes de evaluar la expresión.

Este error es idéntico a CAN0065.
