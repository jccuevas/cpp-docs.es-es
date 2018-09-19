---
title: __thiscall | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __thiscall
- __thiscall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af20b6d406b0e2119df04d5348c554b3405e8597
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103378"
---
# <a name="thiscall"></a>__thiscall

**Específicos de Microsoft**

El **__thiscall** convención de llamada se usa en funciones miembro y es la convención de llamada predeterminado utilizada por las funciones de miembro de C++ que no usan argumentos de variable. En **__thiscall**, el destinatario limpia la pila, que es imposible `vararg` funciones. Los argumentos se insertan en la pila de derecha a izquierda, con el **esto** puntero que se pasa a través del registro ECX y no en la pila, en la x86 arquitectura.

Una razón para utilizar **__thiscall** son las clases cuyas funciones miembro utilizan `__clrcall` de forma predeterminada. En ese caso, puede usar **__thiscall** para convertir en funciones miembro individual que se puede llamar desde código nativo.

Cuando se compila con [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md), todas las funciones y punteros de función son `__clrcall` a menos que se especifique lo contrario. El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

En las versiones anteriores de Visual C++ 2005, el **__thiscall** convención de llamada puede no especificarse explícitamente en un programa, porque **__thiscall** no era una palabra clave.

`vararg` funciones miembro utilizan el **__cdecl** convención de llamada. Todos los argumentos de función se insertan en la pila, con el **esto** puntero colocado en la pila por última vez

Como esta convención de llamada solo se aplica a C++, no hay ningún esquema de decoración de nombres de C.

En ARM y x64 máquinas, **__thiscall** acepta y omite el compilador.

En el caso de funciones de clase no estáticas, si la función se define fuera de línea, no es necesario especificar el modificador de convención de llamada en la definición fuera de línea. Es decir, para los métodos miembro no estáticos de clase, en el momento de la definición se supone la convención de llamada especificada durante la declaración.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)