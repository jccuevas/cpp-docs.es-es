---
title: __if_not_exists (Instrucción)
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: 1118f9fcca525b2b2d5869fb507ee974d2b0d28f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374143"
---
# <a name="__if_not_exists-statement"></a>__if_not_exists (Instrucción)

La **instrucción __if_not_exists** comprueba si existe el identificador especificado. Si el identificador no existe, se ejecuta el bloque de instrucción especificado.

## <a name="syntax"></a>Sintaxis

```
__if_not_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Identificador*|El identificador cuya existencia se desea probar.|
|*Declaraciones*|Una o más instrucciones para ejecutar si no existe *identificador.*|

## <a name="remarks"></a>Observaciones

> [!CAUTION]
> Para lograr los resultados más fiables, utilice la instrucción **__if_not_exists** bajo las siguientes restricciones.

- Aplique la instrucción **__if_not_exists** solo a tipos simples, no a plantillas.

- Aplique la instrucción **__if_not_exists** a los identificadores dentro o fuera de una clase. No aplique la instrucción **__if_not_exists** a variables locales.

- Utilice la **instrucción __if_not_exists** solo en el cuerpo de una función. Fuera del cuerpo de una función, la instrucción **__if_not_exists** solo puede probar tipos completamente definidos.

- Cuando se prueban funciones sobrecargadas, no se puede probar una forma específica de la sobrecarga.

El complemento de la instrucción **__if_not_exists** es [la](../cpp/if-exists-statement.md) __if_exists.

## <a name="example"></a>Ejemplo

Para obtener un ejemplo sobre cómo utilizar **__if_not_exists**, vea [__if_exists (Instrucción).](../cpp/if-exists-statement.md)

## <a name="see-also"></a>Consulte también

[Instrucciones de selección](../cpp/selection-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Declaración __if_exists](../cpp/if-exists-statement.md)
