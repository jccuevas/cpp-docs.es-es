---
title: Importar llamadas a funciones mediante __declspec(dllimport)
ms.date: 11/04/2016
f1_keywords:
- __declspec
- dllimport
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 8635cf5d389f72972f471a4fd53ed56c3497bfe9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188800"
---
# <a name="importing-function-calls-using-declspecdllimport"></a>Importar llamadas a funciones mediante __declspec(dllimport)

El ejemplo de código siguiente muestra cómo usar **_declspec (dllimport)** para importar las llamadas de función desde un archivo DLL en una aplicación. Supongamos que `func1` es una función que reside en un archivo DLL independiente desde el archivo .exe que contiene el **principal** función.

Sin **__declspec (dllimport)**, dado el código:

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

y el vinculador traducirá la llamada en algo parecido a esto:

```
call 0x4000000         ; The address of 'func1'.
```

Si `func1` existe en otro archivo DLL, el vinculador no puede resolver directamente porque no tiene ninguna manera de saber lo que la dirección de `func1` es. En entornos de 16 bits, el vinculador agrega esta dirección de código a una lista en el archivo .exe que el cargador revisaría en tiempo de ejecución con la dirección correcta. En entornos de 32 bits y 64 bits, el vinculador genera un código thunk de los cuales conoce la dirección. En un entorno de 32 bits del código thunk es similar:

```
0x40000000:    jmp DWORD PTR __imp_func1
```

Aquí `imp_func1` es la dirección para el `func1` ranura en la tabla de direcciones de importación del archivo .exe. Todas las direcciones, por tanto, se sabe que el vinculador. El cargador solo tiene que actualizar la tabla de direcciones de importación del archivo .exe en tiempo de carga para que todo funcione correctamente.

Por lo tanto, uso **__declspec (dllimport)** es mejor porque el vinculador no genera un código thunk si no es necesario. Fragmentos de código thunk que el código de mayor tamaño (en sistemas RISC, pueden ser varias instrucciones) y puede degradar el rendimiento de la memoria caché. Si indica al compilador que la función está en un archivo DLL, puede generar una llamada indirecta.

Así que ahora este código:

```
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

genera la siguiente instrucción:

```
call DWORD PTR __imp_func1
```

No hay ningún código thunk y ningún `jmp` instrucciones, por lo que el código es más pequeñas y rápidas.

Por otro lado, para las llamadas de función dentro de un archivo DLL, no desea tener que usar una llamada indirecta. Ya sabe de dirección de una función. Dado que se requiere tiempo y espacio para cargar y almacenar la dirección de la función antes de una llamada indirecta, una llamada directa es siempre más rápido y más pequeños. Solo desea usar **__declspec (dllimport)** al llamar a funciones DLL desde fuera el propio archivo DLL. No use **__declspec (dllimport)** en funciones dentro de un archivo DLL al compilar ese archivo DLL.

## <a name="see-also"></a>Vea también

[Importación a una aplicación](importing-into-an-application.md)
