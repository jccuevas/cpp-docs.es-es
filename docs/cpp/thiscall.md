---
title: __thiscall
ms.date: 11/04/2016
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: 8772159dca71bb7605af5e5919425065423d503d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188160"
---
# <a name="__thiscall"></a>__thiscall

**Específicos de Microsoft**

La Convención de llamada de **__thiscall** se usa en las funciones miembro y es la Convención de C++ llamada predeterminada utilizada por las funciones miembro que no usan argumentos variables. En **__thiscall**, el destinatario limpia la pila, lo que es imposible para las funciones de `vararg`. Los argumentos se insertan en la pila de derecha a izquierda, con el puntero **this** que se pasa a través del registro ECX y no en la pila, en la arquitectura x86.

Una razón para usar **__thiscall** es en las clases cuyas funciones miembro usan `__clrcall` de forma predeterminada. En ese caso, puede usar **__thiscall** para hacer que se pueda llamar a funciones de miembro individuales desde código nativo.

Al compilar con [/clr: Pure](../build/reference/clr-common-language-runtime-compilation.md), todas las funciones y los punteros de función se `__clrcall` a menos que se especifique lo contrario. Las opciones del compilador **/clr: Pure** y **/clr: Safe** están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017.

En las versiones anteriores a Visual Studio 2005, la Convención de llamada **__thiscall** no se pudo especificar explícitamente en un programa, porque **__thiscall** no era una palabra clave.

`vararg` funciones miembro usan la Convención de llamada **__cdecl** . Todos los argumentos de función se insertan en la pila, con el puntero **this** colocado en la pila por última vez

Como esta convención de llamada solo se aplica a C++, no hay ningún esquema de decoración de nombres de C.

En máquinas ARM y x64, el compilador acepta y omite **__thiscall** .

En el caso de funciones de clase no estáticas, si la función se define fuera de línea, no es necesario especificar el modificador de convención de llamada en la definición fuera de línea. Es decir, para los métodos miembro no estáticos de clase, en el momento de la definición se supone la convención de llamada especificada durante la declaración.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)
