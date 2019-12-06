---
title: __stdcall
ms.date: 10/10/2018
f1_keywords:
- __stdcall_cpp
- __stdcall
- _stdcall
helpviewer_keywords:
- __stdcall keyword [C++]
ms.assetid: e212594b-1827-4d07-9527-7d412b300df8
ms.openlocfilehash: df753241c093db75202a10b106631ce36cf73379
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857286"
---
# <a name="__stdcall"></a>__stdcall

La Convención de llamada de **__stdcall** se usa para llamar a funciones de la API de Win32. El destinatario limpia la pila, por lo que el compilador realiza `vararg` funciones **__cdecl**. Las funciones que usan esta convención de llamada requieren un prototipo de función. El modificador **__stdcall** es específico de Microsoft.

## <a name="syntax"></a>Sintaxis

> *return-type* **\_\_stdcall** *function-name*[ **(** *argument-list* **)** ]

## <a name="remarks"></a>Notas

En la lista siguiente se muestra la implementación de esta convención de llamada.

|Elemento|Implementación|
|-------------|--------------------|
|Orden de paso de argumento|De derecha a izquierda.|
|Convención para pasar argumentos|Por valor, a menos que se pase un puntero o un tipo de referencia.|
|Responsabilidad de mantenimiento de pila|La función a la que se llama saca sus propios argumentos de la pila.|
|Convención de creación de nombres representativos|Un subrayado (_) precede al nombre. El nombre va seguido del signo @ seguido del número de bytes (en decimal) en la lista de argumentos. Por consiguiente, la función declarada como `int func( int a, double b )` se representa de la manera siguiente: `_func@12`|
|Convención de traducción de mayúsculas y minúsculas|Ninguno|

La opción del compilador [/gz](../build/reference/gd-gr-gv-gz-calling-convention.md) especifica **__stdcall** para todas las funciones no declaradas explícitamente con otra Convención de llamada.

Por compatibilidad con versiones anteriores, **_stdcall** es un sinónimo de **__stdcall** a menos que se especifique la opción del compilador [/za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) .

Las funciones declaradas con el modificador **__stdcall** devuelven los valores de la misma manera que las funciones declaradas mediante [__cdecl](../cpp/cdecl.md).

En los procesadores ARM y x64, el compilador acepta y omite **__stdcall** . en las arquitecturas ARM y x64, por Convención, los argumentos se pasan en registros cuando es posible y los argumentos subsiguientes se pasan en la pila.

En el caso de funciones de clase no estáticas, si la función se define fuera de línea, no es necesario especificar el modificador de convención de llamada en la definición fuera de línea. Es decir, para los métodos miembro no estáticos de clase, en el momento de la definición se supone la convención de llamada especificada durante la declaración. Dada esta definición de clase,

```cpp
struct CMyClass {
   void __stdcall mymethod();
};
```

this

```cpp
void CMyClass::mymethod() { return; }
```

equivale a esto

```cpp
void __stdcall CMyClass::mymethod() { return; }
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, el uso de **__stdcall** da como resultado que todos los tipos de función de `WINAPI` se controlen como una llamada estándar:

```cpp
// Example of the __stdcall keyword
#define WINAPI __stdcall
// Example of the __stdcall keyword on function pointer
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Vea también

[Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)