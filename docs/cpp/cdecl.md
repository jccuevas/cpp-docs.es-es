---
title: __cdecl
ms.date: 10/09/2018
f1_keywords:
- __cdecl_cpp
- __cdecl
- _cdecl
- cdecl
helpviewer_keywords:
- __cdecl keyword [C++]
ms.assetid: 1ff1d03e-fb4e-4562-8be1-74f1ad6427f1
ms.openlocfilehash: f4cca797c0bff94a54b0f3302c6c475908870a99
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857624"
---
# <a name="__cdecl"></a>__cdecl

**__cdecl** es la Convención de llamada predeterminada para C C++ y programas. Dado que el llamador limpia la pila, puede realizar `vararg` funciones. La Convención de llamada de **__cdecl** crea archivos ejecutables mayores que [__stdcall](../cpp/stdcall.md), porque requiere que cada llamada a función incluya el código de limpieza de la pila. En la lista siguiente se muestra la implementación de esta convención de llamada. El modificador **__cdecl** es específico de Microsoft.

|Elemento|Implementación|
|-------------|--------------------|
|Orden de paso de argumento|De derecha a izquierda.|
|Responsabilidad de mantenimiento de pila|Al llamar a la función, se extraen los argumentos de la pila.|
|Convención de creación de nombres representativos|El carácter de subrayado (_) se antepone a los nombres, excepto cuando se exportan \__cdecl funciones que usan la vinculación C.|
|Convención de traducción de mayúsculas y minúsculas|No se lleva a cabo una traducción de mayúsculas y minúsculas.|

> [!NOTE]
>  Para obtener información relacionada, vea [nombres representativos](../build/reference/decorated-names.md).

Coloque el modificador **__cdecl** delante de una variable o un nombre de función. Dado que las convenciones de llamada y nomenclatura de C son el valor predeterminado, la única vez que debe usar **__cdecl** en código x86 es cuando se ha especificado la opción del compilador `/Gv` (vectorcall), `/Gz` (Stdcall) o `/Gr` (fastcall). La opción del compilador [/GD](../build/reference/gd-gr-gv-gz-calling-convention.md) fuerza la Convención de llamada de **__cdecl** .

En los procesadores ARM y x64, se acepta **__cdecl** , pero el compilador normalmente lo omite. Por convención en ARM y x64, los argumentos se pasan en registros siempre que es posible y los argumentos subsiguientes se pasan en la pila. En código x64, use **__cdecl** para invalidar la opción del compilador **/GV** y usar la Convención de llamada x64 predeterminada.

En el caso de funciones de clase no estáticas, si la función se define fuera de línea, no es necesario especificar el modificador de convención de llamada en la definición fuera de línea. Es decir, para los métodos miembro no estáticos de clase, en el momento de la definición se supone la convención de llamada especificada durante la declaración. Dada esta definición de clase:

```cpp
struct CMyClass {
   void __cdecl mymethod();
};
```

esto:

```cpp
void CMyClass::mymethod() { return; }
```

equivale a esto:

```cpp
void __cdecl CMyClass::mymethod() { return; }
```

Por compatibilidad con versiones anteriores, **Cdecl** y **_cdecl** son un sinónimo de **__cdecl** a menos que se especifique la opción del compilador [/za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, se le indica al compilador que utilice nombres y convenciones de llamada de C para la función `system`.

```cpp
// Example of the __cdecl keyword on function
int __cdecl system(const char *);
// Example of the __cdecl keyword on function pointer
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Vea también

[Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)