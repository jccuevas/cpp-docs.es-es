---
title: PROTO
ms.date: 10/22/2018
f1_keywords:
- PROTO
helpviewer_keywords:
- PROTO directive
ms.assetid: 0487ee16-9dc7-43d1-9445-cd1601f5a080
ms.openlocfilehash: 616b6be2a5c191ebc67d61288cb5fa6c183091fa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62210526"
---
# <a name="proto"></a>PROTO

Prototipos de función o procedimiento. Puede llamar a la función prototipo lo PROTO (directiva) mediante el uso de la [INVOKE](invoke.md) directiva.

## <a name="syntax"></a>Sintaxis

> *etiqueta* **PROTO** \[ *distancia*] \[ *langtype*] \[ __,__ \[ *parámetro*]__:__*etiqueta*]...

### <a name="parameters"></a>Parámetros

*label*<br/>
El nombre de la función de prototipo.

*distance*<br/>
(Opcional) Utilizadas en modelos de memoria de 16 bits para invalidar el valor predeterminado e indique **NEAR** o **lejano** llamadas.

*langtype*<br/>
(Opcional) Establece la convención de llamada y nomenclatura para los procedimientos y los símbolos públicos. Convenciones admitidas son:

- 32 bits **planos** modelo: **C**, **STDCALL**

- modelos de 16 bits: **C**, **BASIC**, **FORTRAN**, **PASCAL**, **SYSCALL**, **STDCALL**

*parameter*<br/>
El nombre opcional para un parámetro de función.

*tag*<br/>
El tipo de un parámetro de función.

El *parámetro* y *etiqueta* parámetros pueden aparecer varias veces, una vez para cada argumento pasado.

## <a name="example"></a>Ejemplo

Este ejemplo se muestra un **PROTO** declaración para una función denominada `addup3` que usa un **NEAR** llamada para invalidar el valor predeterminado de modelo de 16 bits para las llamadas a procedimientos y utiliza el **C**convención de llamada para apilar los parámetros y valores devueltos. Acepta dos argumentos: un **WORD** y un **VARARG**.

```MASM
addup3 PROTO NEAR C, argcount:WORD, arg1:VARARG
```

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)<br/>
[. Referencia del modelo](dot-model.md)<br/>
