---
title: Error en tiempo de ejecución de C R6035
ms.date: 11/04/2016
f1_keywords:
- R6035
helpviewer_keywords:
- R6035
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
ms.openlocfilehash: 7c497347689bcfc5528280bd22aa5183d5fafd61
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197009"
---
# <a name="c-runtime-error-r6035"></a>Error en tiempo de ejecución de C R6035

Biblioteca en tiempo de ejecución de Microsoft Visual C++, error R6035: Un módulo de esta aplicación está inicializando la cookie de seguridad global del módulo al mismo tiempo que una función basada en dicha cookie de seguridad está activa.  Llame previamente a __security_init_cookie.

se debe llamar a [__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md) antes de que se use por primera vez la cookie de seguridad global.

La cookie de seguridad global se usa para la protección de saturación del búfer en el código compilado con [/GS (comprobación de seguridad del búfer)](../../build/reference/gs-buffer-security-check.md) y en el código que usa el control de excepciones estructurado. Fundamentalmente, en la entrada a una función con protección de saturación, la cookie se coloca en la pila y, en la salida, el valor de la pila se compara con respecto a la cookie global. Cualquier diferencia en la comparación indica que se ha producido una saturación del búfer y da lugar a la finalización inmediata del programa.

El error R6035 indica que se ha realizado una llamada a `__security_init_cookie` después de la introducción de una función protegida. Si la ejecución continuara, se detectaría una saturación del búfer falsa porque la cookie de la pila dejaría de coincidir con la cookie global.

Considere el ejemplo de archivo DLL siguiente. El punto de entrada de DLL se establece en DllEntryPoint mediante la opción del enlazador [/entry (símbolo de punto de entrada)](../../build/reference/entry-entry-point-symbol.md) . Esto hace que la inicialización de CRT se omita, con lo que la cookie de seguridad global se inicializaría normalmente, de modo que el propio archivo DLL debe llamar a `__security_init_cookie`.

```
// Wrong way to call __security_init_cookie
DllEntryPoint(...) {
   DllInitialize();
   ...
   __try {
      ...
   } __except()... {
      ...
   }
}

void DllInitialize() {
   __security_init_cookie();
}
```

En este ejemplo se generará el error R6035 porque DllEntryPoint utiliza el control de excepciones estructurado y, por consiguiente, utiliza la cookie de seguridad para detectar las saturaciones del búfer. En el momento de llamar a DllInitialize, ya se ha colocado la cookie de seguridad global en la pila.

En este ejemplo se muestra el método correcto:

```
// Correct way to call __security_init_cookie
DllEntryPoint(...) {
   __security_init_cookie();
   DllEntryHelper();
}

void DllEntryHelper() {
   ...
   __try {
      ...
   } __except()... {
      ...
   }
}
```

En este caso, DllEntryPoint no tiene protección de saturación del búfer (no tiene ningún búfer de cadenas local y no utiliza el control de excepciones estructurado); por lo tanto, puede llamar con seguridad a `__security_init_cookie`. A continuación, llama a una función del asistente que está protegida.

> [!NOTE]
>  El mensaje de error R6035 sólo lo genera el CRT de depuración x86, y para el control de excepciones estructurado exclusivamente, pero la condición de error se produce en todas las plataformas y para todas las formas de control de excepciones, como C++ EH.

## <a name="see-also"></a>Consulte también

[Características de seguridad de MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/)
