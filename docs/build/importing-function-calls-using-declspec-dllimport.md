---
title: Importar llamadas a funciones mediante __declspec(dllimport)
description: Cómo y por qué usar __declspec (dllimport) al llamar a funciones y datos de archivos DLL.
ms.date: 05/03/2020
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 515fbdb2824c1eaf41e822adeae1a16d3072eec4
ms.sourcegitcommit: 8a01ae145bc65f5bc90d6e47b4a1bdf47b073ee7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765726"
---
# <a name="importing-function-calls-using-__declspecdllimport"></a>Importar llamadas a funciones mediante`__declspec(dllimport)`

La anotación de **`__declspec(dllimport)`** llamadas con puede agilizarlas. **`__declspec(dllimport)`** siempre es necesario para tener acceso a los datos de DLL exportados.

## <a name="import-a-function-from-a-dll"></a>Importar una función desde un archivo DLL

En el ejemplo de código siguiente se muestra **`__declspec(dllimport)`** cómo usar para importar llamadas a funciones desde un archivo dll en una aplicación. Suponga que `func1` es una función que está en un archivo dll independiente del archivo ejecutable que contiene la función **Main** .

Sin **`__declspec(dllimport)`**, dado este código:

```C
int main(void)
{
   func1();
}
```

el compilador genera código similar al siguiente:

```asm
call func1
```

y el vinculador traduce la llamada a algo parecido a lo siguiente:

```asm
call 0x4000000         ; The address of 'func1'.
```

Si `func1` existe en otro archivo dll, el vinculador no puede resolver esta dirección directamente porque no tiene ninguna manera de saber cuál es `func1` la dirección de. En entornos de 32 bits y de 64 bits, el vinculador genera un código thunk en una dirección conocida. En un entorno de 32 bits, el código thunk tiene el siguiente aspecto:

```asm
0x40000000:    jmp DWORD PTR __imp_func1
```

Esta `__imp_func1` es la dirección de la `func1` ranura de la tabla de direcciones de importación del archivo ejecutable. El enlazador conoce todas estas direcciones. El cargador solo tiene que actualizar la tabla de direcciones de importación del archivo ejecutable en el momento de la carga para que todo funcione correctamente.

Este es el motivo **`__declspec(dllimport)`** por el que el uso de es mejor: dado que el enlazador no genera un código thunk si no es necesario. Los códigos thunk hacen que el código sea más grande (en sistemas RISC, puede ser varias instrucciones) y puede degradar el rendimiento de la memoria caché. Si indica al compilador que la función está en un archivo DLL, puede generar una llamada indirecta.

Ahora, este código:

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

No hay código thunk ni `jmp` instrucción, por lo que el código es más pequeño y más rápido. También puede obtener el mismo efecto sin **`__declspec(dllimport)`** usar la optimización de todo el programa. Para obtener más información, consulte [/GL (Optimización de todo el programa)](reference/gl-whole-program-optimization.md).

En el caso de las llamadas de función dentro de un archivo DLL, no desea tener que usar una llamada indirecta. El enlazador ya conoce la dirección de la función. Requiere tiempo y espacio adicionales para cargar y almacenar la dirección de la función antes de una llamada indirecta. Una llamada directa siempre es más rápida y más pequeña. Solo desea usar **`__declspec(dllimport)`** al llamar a funciones dll desde fuera del propio archivo dll. No use **`__declspec(dllimport)`** en funciones dentro de un archivo dll al compilar ese archivo dll.

## <a name="see-also"></a>Vea también

[Importar en una aplicación](importing-into-an-application.md)
