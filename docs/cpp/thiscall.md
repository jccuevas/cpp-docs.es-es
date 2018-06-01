---
title: __thiscall | Documentos de Microsoft
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
ms.openlocfilehash: 4912628529ae0b47a5a5b938ab8e6d25a9099510
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704408"
---
# <a name="thiscall"></a>__thiscall

**Específicos de Microsoft**

La convención de llamada `__thiscall` se utiliza en funciones miembro y es la convención de llamada predeterminada que emplean las funciones miembro de C++ que no utilizan argumentos de variable. En `__thiscall`, el destinatario limpia la pila, lo que es imposible para las funciones `vararg`. Los argumentos se insertan en la pila de derecha a izquierda; el puntero `this` se pasa a través del registro ECX, y no en la pila, en la arquitectura x86.

Un motivo para utilizar `__thiscall` son las clases cuyas funciones miembro utilizan `__clrcall` de forma predeterminada. En ese caso, puede utilizar `__thiscall` para crear funciones miembro individuales que se puedan llamar desde código nativo.

Cuando se compila con [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md), todas las funciones y los punteros de función son `__clrcall` a menos que se especifique lo contrario. El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

En las versiones anteriores de Visual C++ 2005, la `__thiscall` convención de llamada puede no especificarse explícitamente en un programa, porque `__thiscall` no era una palabra clave.

Las funciones miembro `vararg` usan la convención de llamada `__cdecl`. Todos los argumentos de función se insertan en la pila, colocándose el puntero `this` en el último lugar de la pila.

Como esta convención de llamada solo se aplica a C++, no hay ningún esquema de decoración de nombres de C.

En ARM y x64 máquinas, `__thiscall` acepta y omite por el compilador.

En el caso de funciones de clase no estáticas, si la función se define fuera de línea, no es necesario especificar el modificador de convención de llamada en la definición fuera de línea. Es decir, para los métodos miembro no estáticos de clase, en el momento de la definición se supone la convención de llamada especificada durante la declaración.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

- [Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)
