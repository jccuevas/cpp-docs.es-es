---
title: Operadores de conversión
ms.date: 11/04/2016
helpviewer_keywords:
- cast operators
- type casts, operators
- operators [C++], cast
- type conversion, cast operators
ms.assetid: 43b90bbd-39ef-43e6-ae5d-e8a67a01de40
ms.openlocfilehash: e3d892a5aede4cd2d6a980b440875f0ac9837120
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147950"
---
# <a name="cast-operators"></a>Operadores de conversión

Una conversión de tipo proporciona un método para la conversión explícita del tipo de un objeto en una situación concreta.

## <a name="syntax"></a>Sintaxis

*cast-expression*: *unary-expression*

**(**  *type-name*  **)**  *cast-expression*

El compilador trata *cast-expression* como tipo *type-name* una vez realizada una conversión de tipo. Las conversiones se pueden utilizar para convertir objetos de cualquier tipo escalar en cualquier otro tipo escalar. Las conversiones de tipos explícitas están restringidas por las mismas reglas que determinan los efectos de las conversiones implícitas, que se describen en [Conversiones de asignación](../c-language/assignment-conversions.md). Se pueden aplicar otras restricciones derivadas de los tamaños reales o de la representación de tipos específicos. Vea [Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md) para obtener información sobre los tamaños reales de los tipos enteros. Para obtener más información sobre la conversión de tipos, vea [Conversiones de tipos](../c-language/type-cast-conversions.md).

## <a name="see-also"></a>Vea también

[Operador de conversión: ()](../cpp/cast-operator-parens.md)
