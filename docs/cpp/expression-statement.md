---
title: Expression (Instrucción)
ms.date: 11/04/2016
helpviewer_keywords:
- statements [C++], expression
- expression statements
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
ms.openlocfilehash: 2f12bbbafd9be50f851e36f472098431f9ac0d5d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189005"
---
# <a name="expression-statement"></a>Expression (Instrucción)

Las instrucciones de expresión hacen que se evalúen las expresiones. No se realiza ninguna transferencia de control o iteración como resultado de una instrucción de expresión.

La sintaxis de la instrucción de expresión es simplemente

## <a name="syntax"></a>Sintaxis

```
[expression ] ;
```

## <a name="remarks"></a>Observaciones

Todas las expresiones de una instrucción de expresión se evalúan y se aplican todos los efectos secundarios antes de que se ejecute la siguiente instrucción. Las instrucciones de expresión más comunes son las asignaciones y las llamadas a funciones.  Dado que la expresión es opcional, un punto y coma solo se considera una instrucción de expresión vacía, que se conoce como la instrucción [null](../cpp/null-statement.md) .

## <a name="see-also"></a>Consulte también

[Información general sobre las instrucciones de C++](../cpp/overview-of-cpp-statements.md)
