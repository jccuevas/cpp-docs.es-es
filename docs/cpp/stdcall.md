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
ms.openlocfilehash: b9efac6f729a78db945ff3bd9ab16ebe315b7a5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560646"
---
# <a name="stdcall"></a>__stdcall

**Específicos de Microsoft**

El **__stdcall** convención de llamada se usa para llamar a funciones API de Win32. El destinatario limpia la pila, por lo que hace que el compilador `vararg` funciones **__cdecl**. Las funciones que usan esta convención de llamada requieren un prototipo de función.

## <a name="syntax"></a>Sintaxis

> *tipo de valor devuelto*  **\_ \_stdcall** *nombre de la función*[**(** *lista de argumentos* **)** ]

## <a name="remarks"></a>Comentarios

En la lista siguiente se muestra la implementación de esta convención de llamada.

|Elemento|Implementación|
|-------------|--------------------|
|Orden de paso de argumento|De derecha a izquierda.|
|Convención para pasar argumentos|Por valor, a menos que se pase un puntero o un tipo de referencia.|
|Responsabilidad de mantenimiento de pila|La función a la que se llama saca sus propios argumentos de la pila.|
|Convención de creación de nombres representativos|Un subrayado (_) precede al nombre. El nombre va seguido del signo @ seguido del número de bytes (en decimal) en la lista de argumentos. Por consiguiente, la función declarada como `int func( int a, double b )` se representa de la manera siguiente: `_func@12`|
|Convención de traducción de mayúsculas y minúsculas|Ninguna|

El [/Gz](../build/reference/gd-gr-gv-gz-calling-convention.md) especifica la opción del compilador **__stdcall** para todas las funciones no declaradas explícitamente con otra convención de llamada.

Para ofrecer compatibilidad con versiones anteriores, **_stdcall** es un sinónimo de **__stdcall** a menos que la opción de compilador [/Za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) es especificado.

Las funciones declaradas con el **__stdcall** del mismo modo que las funciones declaradas con los valores de modificador devuelto [__cdecl](../cpp/cdecl.md).

En ARM y x64 procesadores, **__stdcall** acepta y omite el compilador; en ARM y x64 arquitecturas, por convención, los argumentos se pasan en registros cuando sea posible, y los argumentos subsiguientes se pasan en la pila.

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

En el ejemplo siguiente, el uso de **__stdcall** da como resultado todos `WINAPI` tipos de función que se tratan como una llamada estándar:

```cpp
// Example of the __stdcall keyword
#define WINAPI __stdcall
// Example of the __stdcall keyword on function pointer
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Vea también

[Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)