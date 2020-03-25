---
title: __if_not_exists (Instrucción)
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: 7372ac127a7b4dd5c05d58cfecca25f87690b0ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178199"
---
# <a name="__if_not_exists-statement"></a>__if_not_exists (Instrucción)

La instrucción **__if_not_exists** comprueba si existe el identificador especificado. Si el identificador no existe, se ejecuta el bloque de instrucción especificado.

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
|*afirma*|Una o varias instrucciones que se ejecutarán si el *identificador* no existe.|

## <a name="remarks"></a>Observaciones

> [!CAUTION]
>  Para obtener los resultados más confiables, utilice la instrucción **__if_not_exists** en las siguientes restricciones.

- Aplique la instrucción **__if_not_exists** solo a tipos simples, no a plantillas.

- Aplique la instrucción **__if_not_exists** a los identificadores tanto dentro como fuera de una clase. No aplique la instrucción **__if_not_exists** a las variables locales.

- Use la instrucción **__if_not_exists** solo en el cuerpo de una función. Fuera del cuerpo de una función, la instrucción **__if_not_exists** solo puede probar tipos totalmente definidos.

- Cuando se prueban funciones sobrecargadas, no se puede probar una forma específica de la sobrecarga.

El complemento a la instrucción **__if_not_exists** es la instrucción [__if_exists](../cpp/if-exists-statement.md) .

## <a name="example"></a>Ejemplo

Para obtener un ejemplo sobre cómo usar **__if_not_exists**, vea la [instrucción __if_exists](../cpp/if-exists-statement.md).

## <a name="see-also"></a>Consulte también

[Instrucciones de selección](../cpp/selection-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[__if_exists (Instrucción)](../cpp/if-exists-statement.md)
