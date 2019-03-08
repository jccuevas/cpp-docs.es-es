---
title: __if_not_exists (Instrucción)
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: 845597460cdc0ce83adcbba1f47a78c83735cbf9
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327777"
---
# <a name="ifnotexists-statement"></a>__if_not_exists (Instrucción)

El **__if_not_exists** instrucción comprueba si existe el identificador especificado. Si el identificador no existe, se ejecuta el bloque de instrucción especificado.

## <a name="syntax"></a>Sintaxis

```
__if_not_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*identifier*|El identificador cuya existencia se desea probar.|
|*Instrucciones*|Una o varias instrucciones que se ejecutarán si *identificador* no existe.|

## <a name="remarks"></a>Comentarios

> [!CAUTION]
>  Para lograr los resultados más confiables, use el **__if_not_exists** instrucción con las restricciones siguientes.

- Aplicar el **__if_not_exists** instrucción solo a tipos simples, no a plantillas.

- Aplicar el **__if_not_exists** instrucción a identificadores tanto dentro como fuera de una clase. No se aplican los **__if_not_exists** instrucción a variables locales.

- Use la **__if_not_exists** instrucción sólo en el cuerpo de una función. Fuera del cuerpo de una función, el **__if_not_exists** instrucción puede probar solo tipos totalmente definidos.

- Cuando se prueban funciones sobrecargadas, no se puede probar una forma específica de la sobrecarga.

El complemento para el **__if_not_exists** instrucción es la [__if_exists](../cpp/if-exists-statement.md) instrucción.

## <a name="example"></a>Ejemplo

Para obtener un ejemplo sobre cómo usar **__if_not_exists**, consulte [__if_exists instrucción](../cpp/if-exists-statement.md).

## <a name="see-also"></a>Vea también

[Instrucciones de selección](../cpp/selection-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[__if_exists (Instrucción)](../cpp/if-exists-statement.md)