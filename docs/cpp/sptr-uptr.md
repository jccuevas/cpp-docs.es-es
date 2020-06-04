---
title: __sptr, __uptr
ms.date: 10/10/2018
f1_keywords:
- __uptr_cpp
- __sptr_cpp
- __uptr
- __sptr
- _uptr
- _sptr
helpviewer_keywords:
- __sptr modifier
- __uptr modifier
ms.assetid: c7f5f3b2-9106-4a0b-a6de-d1588ab153ed
ms.openlocfilehash: bfa468c96196c417415801239925707c43a49c4e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178683"
---
# <a name="__sptr-__uptr"></a>__sptr, __uptr

**Específicos de Microsoft**

Utilice el modificador **__sptr** o **__uptr** en una declaración de puntero de 32 bits para especificar cómo el compilador convierte un puntero de 32 bits en un puntero de 64 bits. Un puntero de 32 bits se convierte, por ejemplo, cuando se asigna a una variable de puntero de 64 bits o se deshace la referencia en una plataforma de 64 bits.

La documentación de Microsoft para la compatibilidad con plataformas de 64 bits hace referencia a veces al bit más significativo de un puntero de 32 bits como el bit de signo. De forma predeterminada, el compilador utiliza la extensión de signo para convertir un puntero de 32 bits en un puntero de 64 bits. Es decir, los 32 bits menos significativos del puntero de 64 bits se establecen en el valor del puntero de 32 bits y los 32 bits más significativos se establecen en el valor del bit de signo del puntero de 32 bits. Esta conversión produce resultados correctos si el bit de signo es 0, pero no si el bit de signo es 1. Por ejemplo, la dirección de 32 bits 0x7FFFFFFF produce la dirección de 64 bits equivalente 0x000000007FFFFFFF, pero la dirección de 32 bits 0x80000000 cambia incorrectamente a 0xFFFFFFFF80000000.

El modificador **__sptr**, o el puntero con signo, especifica que una conversión de puntero establezca los bits más significativos de un puntero de 64 bits en el bit de signo del puntero de 32 bits. El modificador **__uptr**, o el puntero sin signo especifica que una conversión establezca los bits más significativos en cero. Las declaraciones siguientes muestran los modificadores **__sptr** y **__uptr** utilizados con dos punteros incompletos, dos punteros calificados con el tipo [__ptr32](../cpp/ptr32-ptr64.md) y un parámetro de función.

```cpp
int * __sptr psp;
int * __uptr pup;
int * __ptr32 __sptr psp32;
int * __ptr32 __uptr pup32;
void MyFunction(char * __uptr __ptr32 myValue);
```

Use los modificadores **__sptr** y **__uptr** con las declaraciones de puntero. Use los modificadores en la posición de un [calificador de tipo de puntero](../c-language/pointer-declarations.md), lo que significa que el modificador debe seguir el asterisco. No se pueden usar los modificadores con [punteros a miembros](../cpp/pointers-to-members.md). Los modificadores no afectan a las declaraciones que no son de puntero.

Por compatibilidad con versiones anteriores, **_sptr** y **_uptr** son sinónimos para **__sptr** y **__uptr** a menos que se especifique la opción del compilador [/za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se declaran punteros de 32 bits que usan los modificadores **__sptr** y **__uptr** , se asigna cada puntero de 32 bits a una variable de puntero de 64 bits y, a continuación, se muestra el valor hexadecimal de cada puntero de 64 bits. El ejemplo se compila con el compilador de 64 bits nativo y se ejecuta en una plataforma de 64 bits.

```cpp
// sptr_uptr.cpp
// processor: x64
#include "stdio.h"

int main()
{
    void *        __ptr64 p64;
    void *        __ptr32 p32d; //default signed pointer
    void * __sptr __ptr32 p32s; //explicit signed pointer
    void * __uptr __ptr32 p32u; //explicit unsigned pointer

// Set the 32-bit pointers to a value whose sign bit is 1.
    p32d = reinterpret_cast<void *>(0x87654321);
    p32s = p32d;
    p32u = p32d;

// The printf() function automatically displays leading zeroes with each 32-bit pointer. These are unrelated
// to the __sptr and __uptr modifiers.
    printf("Display each 32-bit pointer (as an unsigned 64-bit pointer):\n");
    printf("p32d:       %p\n", p32d);
    printf("p32s:       %p\n", p32s);
    printf("p32u:       %p\n", p32u);

    printf("\nDisplay the 64-bit pointer created from each 32-bit pointer:\n");
    p64 = p32d;
    printf("p32d: p64 = %p\n", p64);
    p64 = p32s;
    printf("p32s: p64 = %p\n", p64);
    p64 = p32u;
    printf("p32u: p64 = %p\n", p64);
    return 0;
}
```

```Output
Display each 32-bit pointer (as an unsigned 64-bit pointer):
p32d:       0000000087654321
p32s:       0000000087654321
p32u:       0000000087654321

Display the 64-bit pointer created from each 32-bit pointer:
p32d: p64 = FFFFFFFF87654321
p32s: p64 = FFFFFFFF87654321
p32u: p64 = 0000000087654321
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md)
