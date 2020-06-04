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
ms.openlocfilehash: b4a86c49880b0c40d402c7cec863f79e24bc4dc1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371564"
---
# <a name="__cdecl"></a>__cdecl

**__cdecl** es la convención de llamada predeterminada para los programas C y C++. Dado que el autor de la llamada `vararg` limpia la pila, puede realizar funciones. La **convención de** llamada __cdecl crea ejecutables más grandes que [__stdcall](../cpp/stdcall.md), porque requiere que cada llamada de función incluya código de limpieza de pila. En la lista siguiente se muestra la implementación de esta convención de llamada. El modificador **__cdecl** es específico de Microsoft.

|Elemento|Implementación|
|-------------|--------------------|
|Orden de paso de argumento|De derecha a izquierda.|
|Responsabilidad de mantenimiento de pila|Al llamar a la función, se extraen los argumentos de la pila.|
|Convención de creación de nombres representativos|El carácter de subrayado (_) \_tiene el prefijo de los nombres, excepto cuando se exportan _cdecl funciones que utilizan la vinculación De C.|
|Convención de traducción de mayúsculas y minúsculas|No se lleva a cabo una traducción de mayúsculas y minúsculas.|

> [!NOTE]
> Para obtener información relacionada, consulte [Nombres decorados](../build/reference/decorated-names.md).

Coloque el modificador **__cdecl** antes de una variable o un nombre de función. Dado que las convenciones de nomenclatura y llamada de C son el valor predeterminado, la `/Gv` única vez `/Gz` que debe usar `/Gr` **__cdecl** en código x86 es cuando se ha especificado la opción del compilador (vectorcall), (stdcall) o (fastcall). La opción del compilador [/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md) fuerza la **convención de** llamada __cdecl.

En los procesadores ARM y x64, **__cdecl** es aceptado pero normalmente ignorado por el compilador. Por convención en ARM y x64, los argumentos se pasan en registros siempre que es posible y los argumentos subsiguientes se pasan en la pila. En código x64, use **__cdecl** para invalidar la opción del compilador **/Gv** y use la convención de llamada x64 predeterminada.

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

Por compatibilidad con versiones anteriores, **cdecl** y **_cdecl** son sinónimo de **__cdecl** a menos que se especifique la opción del compilador [ \(/Za Disable language extensions).](../build/reference/za-ze-disable-language-extensions.md)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, se le indica al compilador que utilice nombres y convenciones de llamada de C para la función `system`.

```cpp
// Example of the __cdecl keyword on function
int __cdecl system(const char *);
// Example of the __cdecl keyword on function pointer
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Consulte también

[Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
