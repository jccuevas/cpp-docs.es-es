---
title: Instrucciones de iteración (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- iteration statements
- loop structures, iteration statements
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
ms.openlocfilehash: e8f064fd19e69de2819673f48a7f14e26d60b87e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178266"
---
# <a name="iteration-statements-c"></a>Instrucciones de iteración (C++)

Las instrucciones de iteración producen instrucciones (o instrucciones compuestas) que se ejecutarán cero o más veces, según determinados criterios de la finalización de bucle. Cuando estas instrucciones son instrucciones compuestas, se ejecutan en orden, excepto cuando se encuentra la instrucción [break](../cpp/break-statement-cpp.md) o la instrucción [continue](../cpp/continue-statement-cpp.md) .

C++proporciona cuatro instrucciones de iteración ( [While](../cpp/while-statement-cpp.md), [do](../cpp/do-while-statement-cpp.md), [for](../cpp/for-statement-cpp.md)y [basada en intervalo para](../cpp/range-based-for-statement-cpp.md). Cada una de estas iteraciones hasta que su expresión de finalización se evalúa como cero (false) o hasta que la terminación del bucle se fuerza con una instrucción **break** . En la tabla siguiente se resumen estas instrucciones y sus acciones; cada una se explica detalladamente en las secciones siguientes.

### <a name="iteration-statements"></a>Instrucciones de iteración

|.|Se evalúa en|Inicialización|Incremento|
|---------------|------------------|--------------------|---------------|
|**while**|Principio del bucle|No|No|
|**do**|Final del bucle|No|No|
|**for**|Principio del bucle|Sí|Sí|
|**basado en intervalo para**|Principio del bucle|Sí|Sí|

La parte de instrucción de una instrucción de iteración no puede ser una declaración. Sin embargo, puede ser una instrucción compuesta que contenga una declaración.

## <a name="see-also"></a>Consulte también

[Información general sobre las instrucciones de C++](../cpp/overview-of-cpp-statements.md)
