---
title: Importar llamadas a funciones mediante __declspec(dllimport)
description: Cómo y por qué usar __declspec(dllimport) al llamar a datos y funciones de DLL.
ms.date: 05/03/2020
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 515fbdb2824c1eaf41e822adeae1a16d3072eec4
ms.sourcegitcommit: 8a01ae145bc65f5bc90d6e47b4a1bdf47b073ee7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765726"
---
# <a name="importing-function-calls-using-__declspecdllimport"></a>Importación de llamadas a funciones mediante `__declspec(dllimport)`

La anotación de llamadas mediante **`__declspec(dllimport)`** puede agilizarlas. **`__declspec(dllimport)`** siempre es necesario para acceder a los datos de DLL exportados.

## <a name="import-a-function-from-a-dll"></a>Importación de una función desde un archivo DLL

En el ejemplo de código siguiente se muestra cómo usar **`__declspec(dllimport)`** para importar llamadas a funciones desde un archivo DLL en una aplicación. Imagine que `func1` es una función que se encuentra en un archivo DLL independiente del archivo ejecutable que contiene la función **main**.

Sin **`__declspec(dllimport)`** , dado este código:

```C
int main(void)
{
   func1();
}
```

el compilador genera código como el siguiente:

```asm
call func1
```

y el enlazador traduce la llamada a algo parecido a lo siguiente:

```asm
call 0x4000000         ; The address of 'func1'.
```

Si `func1` existe en otro archivo DLL, el enlazador no puede resolver esta dirección directamente porque no tiene ninguna manera de saber cuál es la dirección de `func1`. En entornos de 32 y 64 bits, el enlazador genera un código thunk en una dirección conocida. En un entorno de 32 bits, el código thunk tiene el siguiente aspecto:

```asm
0x40000000:    jmp DWORD PTR __imp_func1
```

Aquí, `__imp_func1` es la dirección de la ranura `func1` en la tabla de direcciones de importación del archivo ejecutable. El enlazador conoce todas estas direcciones. El cargador solo tiene que actualizar la tabla de direcciones de importación del archivo ejecutable en el momento de la carga para que todo funcione correctamente.

Por eso, el uso de **`__declspec(dllimport)`** es mejor, ya que el enlazador no genera un código thunk si no es necesario. Los códigos thunk aumentan el tamaño del código (en sistemas RISC, puede constar de varias instrucciones) y pueden degradar el rendimiento de la caché. Si indica al compilador que la función está en un archivo DLL, puede generar una llamada indirecta de forma automática.

Por tanto, ahora este código:

```C
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

genera esta instrucción:

```asm
call DWORD PTR __imp_func1
```

No hay código thunk ni ninguna instrucción `jmp`, por lo que el código es más pequeño y más rápido. También puede obtener el mismo efecto sin **`__declspec(dllimport)`** mediante la optimización de todo el programa. Para obtener más información, consulte [/GL (Optimización de todo el programa)](reference/gl-whole-program-optimization.md).

En el caso de las llamadas de función dentro de un archivo DLL, no le interesa tener que usar una llamada indirecta. El enlazador ya conoce la dirección de la función. Se necesita tiempo y espacio adicional para cargar y almacenar la dirección de la función antes de una llamada indirecta. Una llamada directa siempre es más rápida y de menor tamaño. Solo le interesa usar **`__declspec(dllimport)`** al llamar a funciones DLL desde fuera del propio archivo DLL. No use **`__declspec(dllimport)`** en funciones dentro de un archivo DLL al compilarlo.

## <a name="see-also"></a>Vea también

[Importación a una aplicación](importing-into-an-application.md)
