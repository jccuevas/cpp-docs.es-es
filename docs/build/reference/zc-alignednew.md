---
title: /Zc:alignedNew (asignación alineada en exceso de C++17)
ms.date: 05/18/2019
f1_keywords:
- /Zc:alignedNew
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
ms.openlocfilehash: 041f62bbbf5f7a2750960d21d1534cf6daf4b874
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335693"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew (asignación alineada en exceso de C++17)

Habilite la compatibilidad con la asignación de memoria dinámica **new** alineada en exceso de C++17 en límites mayores que el predeterminado para el tipo alineado estándar de tamaño máximo, **max\_align\_t**.

## <a name="syntax"></a>Sintaxis

> **/Zc:alignedNew**\[-]

## <a name="remarks"></a>Observaciones

La biblioteca y el compilador de MSVC admiten la asignación de memoria dinámica alineada en exceso estándar de C++17. Cuando se especifica la opción **/Zc:alignedNew,** `new Example;` una asignación dinámica como respeta la `max_align_t`alineación de *Ejemplo* incluso cuando es mayor que , la alineación más grande necesaria para cualquier tipo fundamental. Cuando la alineación del tipo asignado no es superior `::operator new(size_t)` a la alineación garantizada por el operador original **new**, `new Example;` disponible como el valor de la macro ** \_ \_predefinida\_STDCPP DEFAULT\_NEW\_ALIGNMENT\_**, la instrucción da como lo hizo en C++14. Cuando la alineación es mayor que `::operator new(size_t, align_val_t)` ** \_ \_STDCPP\_DEFAULT\_NEW\_ALIGNMENT\_**, la implementación en su lugar obtiene la memoria mediante . Del mismo modo, la eliminación de tipos alineados en exceso invoca a `::operator delete(void*, align_val_t)` o la firma de eliminación redimensionada `::operator delete(void*, size_t, align_val_t)`.

La opción **/Zc:alignedNew** solo está disponible cuando se habilitan [/std:c++17](std-specify-language-standard-version.md) o [/std:c++latest](std-specify-language-standard-version.md). En **/std:c++17** o **/std:c++latest**, **/Zc:alignedNew** está habilitada de forma predeterminada para cumplir con la norma ISO C++17 estándar. Si el único motivo para implementar los operadores **new** y **delete** es admitir asignaciones alineadas en exceso, es posible que ya no necesite este código en modo C++17. Para desactivar esta opción y revertir al comportamiento de **new** y **delete** de C++14 al usar **/std::c++17** o **/std:c++latest**, especifique **/Zc:alignedNew-**. Si implementa los operadores **new** y **delete** pero no está listo para implementar las sobrecargas alineadas en exceso de los operadores **new** y **delete** que tienen el parámetro `align_val_t`, use la opción **/Zc:alignedNew-** para evitar que el compilador y la biblioteca estándar generen llamadas a las sobrecargas alineadas en exceso. La opción [/permissive-](permissive-standards-conformance.md) no cambia el valor predeterminado de **/Zc:alignedNew**.

Existe compatibilidad con **/Zc:alignedNew** disponible a partir de Visual Studio 2017 versión 15.5.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo se comportan el operador **new** y el operador **delete** cuando se establece la opción **/Zc:alignedNew**.

```cpp
// alignedNew.cpp
// Compile by using: cl /EHsc /std:c++17 /W4 alignedNew.cpp
#include <iostream>
#include <malloc.h>
#include <new>

// "old" unaligned overloads
void* operator new(std::size_t size) {
    auto ptr = malloc(size);
    std::cout << "unaligned new(" << size << ") = " << ptr << '\n';
    return ptr ? ptr : throw std::bad_alloc{};
}

void operator delete(void* ptr, std::size_t size) {
    std::cout << "unaligned sized delete(" << ptr << ", " << size << ")\n";
    free(ptr);
}

void operator delete(void* ptr) {
    std::cout << "unaligned unsized delete(" << ptr << ")\n";
    free(ptr);
}

// "new" over-aligned overloads
void* operator new(std::size_t size, std::align_val_t align) {
    auto ptr = _aligned_malloc(size, static_cast<std::size_t>(align));
    std::cout << "aligned new(" << size << ", " <<
        static_cast<std::size_t>(align) << ") = " << ptr << '\n';
    return ptr ? ptr : throw std::bad_alloc{};
}

void operator delete(void* ptr, std::size_t size, std::align_val_t align) {
    std::cout << "aligned sized delete(" << ptr << ", " << size <<
        ", " << static_cast<std::size_t>(align) << ")\n";
    _aligned_free(ptr);
}

void operator delete(void* ptr, std::align_val_t align) {
    std::cout << "aligned unsized delete(" << ptr <<
        ", " << static_cast<std::size_t>(align) << ")\n";
    _aligned_free(ptr);
}

struct alignas(256) OverAligned {}; // warning C4324, structure is padded

int main() {
    delete new int;
    delete new OverAligned;
}
```

Esta salida es típica de las compilaciones de 32 bits. Los valores de puntero varían en función de dónde se ejecuta la aplicación en la memoria.

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Comportamiento no estándar](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de**propiedades** **De propiedades** > de configuración**C/C++.** > 

1. Modifique la propiedad **Opciones adicionales** para incluir **/Zc:alignedNew** o **/Zc:alignedNew-** y luego elija **Aceptar**.

## <a name="see-also"></a>Consulte también

[/Zc (Ajuste)](zc-conformance.md)
