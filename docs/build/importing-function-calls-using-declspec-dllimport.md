---
title: Importar llamadas a funciones mediante __declspec(dllimport)
ms.date: 11/04/2016
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 1743cbba8c3046ef844f16be8e78d43c61f62606
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442512"
---
# <a name="importing-function-calls-using-__declspecdllimport"></a>Importar llamadas a funciones mediante __declspec(dllimport)

En el ejemplo de código siguiente se muestra cómo usar **_declspec (dllimport)** para importar llamadas a funciones desde un archivo dll en una aplicación. Supongamos que `func1` es una función que reside en una DLL independiente del archivo. exe que contiene la función **Main** .

Sin **__declspec (dllimport)** , dado este código:

```
int main(void)
{
   func1();
}
```

el compilador genera código similar al siguiente:

```
call func1
```

y el vinculador traduce la llamada a algo parecido a lo siguiente:

```
call 0x4000000         ; The address of 'func1'.
```

Si `func1` existe en otro archivo DLL, el vinculador no puede resolver esto directamente porque no tiene ninguna manera de saber cuál es la dirección de `func1`. En entornos de 16 bits, el vinculador agrega esta dirección de código a una lista del archivo. exe que el cargador revisará en tiempo de ejecución con la dirección correcta. En entornos de 32 bits y de 64 bits, el enlazador genera un código thunk del que conoce la dirección. En un entorno de 32 bits, el código thunk tiene el siguiente aspecto:

```
0x40000000:    jmp DWORD PTR __imp_func1
```

Aquí `imp_func1` es la dirección de la ranura de `func1` en la tabla de direcciones de importación del archivo. exe. Por lo tanto, el enlazador conoce todas las direcciones. El cargador solo tiene que actualizar la tabla de direcciones de importación del archivo. exe en el momento de la carga para que todo funcione correctamente.

Por lo tanto, el uso de **__declspec (dllimport)** es mejor porque el enlazador no genera un código thunk si no es necesario. Los códigos thunk hacen que el código sea más grande (en sistemas RISC, puede ser varias instrucciones) y puede degradar el rendimiento de la memoria caché. Si indica al compilador que la función está en un archivo DLL, puede generar una llamada indirecta.

Ahora, este código:

```
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

genera esta instrucción:

```
call DWORD PTR __imp_func1
```

No hay código thunk ni instrucción `jmp`, por lo que el código es más pequeño y más rápido.

Por otra parte, para las llamadas de función dentro de un archivo DLL, no desea tener que usar una llamada indirecta. Ya conoce la dirección de una función. Dado que la hora y el espacio son necesarios para cargar y almacenar la dirección de la función antes de una llamada indirecta, una llamada directa siempre es más rápida y más pequeña. Solo desea utilizar **__declspec (dllimport)** al llamar a funciones dll desde fuera del propio archivo dll. No utilice **__declspec (dllimport)** en funciones dentro de un archivo dll al compilar ese archivo dll.

## <a name="see-also"></a>Consulte también

[Importación a una aplicación](importing-into-an-application.md)
