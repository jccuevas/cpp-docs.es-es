---
title: __thiscall
ms.date: 11/04/2016
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: e51879ae62b2881e0adadbe59859605f6cc58947
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221915"
---
# <a name="thiscall"></a>__thiscall

**Específicos de Microsoft**

El **__thiscall** convención de llamada se usa en funciones miembro y es el valor predeterminado que usa una convención de llamada C++ funciones miembro que no usan argumentos de variable. En **__thiscall**, el destinatario limpia la pila, que es imposible `vararg` funciones. Los argumentos se insertan en la pila de derecha a izquierda, con el **esto** puntero que se pasa a través del registro ECX y no en la pila, en la x86 arquitectura.

Una razón para utilizar **__thiscall** son las clases cuyas funciones miembro utilizan `__clrcall` de forma predeterminada. En ese caso, puede usar **__thiscall** para convertir en funciones miembro individual que se puede llamar desde código nativo.

Cuando se compila con [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md), todas las funciones y punteros de función son `__clrcall` a menos que se especifique lo contrario. El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

En versiones anteriores a Visual Studio 2005, el **__thiscall** convención de llamada puede no especificarse explícitamente en un programa, porque **__thiscall** no era una palabra clave.

`vararg` funciones miembro utilizan el **__cdecl** convención de llamada. Todos los argumentos de función se insertan en la pila, con el **esto** puntero colocado en la pila por última vez

Como esta convención de llamada solo se aplica a C++, no hay ningún esquema de decoración de nombres de C.

En ARM y x64 máquinas, **__thiscall** acepta y omite el compilador.

En el caso de funciones de clase no estáticas, si la función se define fuera de línea, no es necesario especificar el modificador de convención de llamada en la definición fuera de línea. Es decir, para los métodos miembro no estáticos de clase, en el momento de la definición se supone la convención de llamada especificada durante la declaración.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)