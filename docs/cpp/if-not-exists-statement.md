---
title: __if_not_exists (instrucción) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __if_not_exists_cpp
dev_langs:
- C++
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66999d99e7809a3588dc3c92cae822bb4295ee07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073361"
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