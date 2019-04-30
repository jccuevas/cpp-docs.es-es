---
title: '/ Zc: alignednew (c ++ 17 asignación alineada en exceso)'
ms.date: 02/28/2018
f1_keywords:
- /Zc:alignedNew
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
ms.openlocfilehash: e0d850d54611579288b81a334af4abdfab6e411c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315805"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/ Zc: alignednew (c ++ 17 asignación alineada en exceso)

Habilitar la compatibilidad con C ++ 17 demasiado alineados **nueva**, asignación de memoria dinámica que se alinean en límites mayores que el valor predeterminado para el tamaño máximo estándar tipo alineado, **max\_alinear\_t**.

## <a name="syntax"></a>Sintaxis

> **/Zc:alignedNew**[-]

## <a name="remarks"></a>Comentarios

Versión 15.5 de Visual Studio permite la compatibilidad del compilador y biblioteca de C ++ 17 estándar alineada en exceso la asignación de memoria. Cuando el **/Zc: alignednew** se especifica la opción, una asignación dinámica como `new Example;` respeta la alineación de *ejemplo* incluso cuando es mayor que `max_align_t`, la alineación mayor se requiere para cualquier tipo fundamental. Cuando la alineación del tipo asignado es no más que eso garantiza que el operador original **nueva**, disponible como el valor de la macro predefinida  **\_ \_STDCPP\_predeterminado \_NEW\_alineación\_\_**, la instrucción `new Example;` da como resultado una llamada a `::operator new(size_t)` como lo hacía en C ++ 14. Cuando es mayor que la alineación  **\_ \_STDCPP\_predeterminado\_NEW\_alineación\_\_**, la implementación en su lugar obtiene la memoria mediante el uso de `::operator new(size_t, align_val_t)`. Del mismo modo, se invoca la eliminación de tipos sobrealineados `::operator delete(void*, align_val_t)` o elimina el ajusta firma `::operator delete(void*, size_t, align_val_t)`.

El **/Zc: alignednew** opción solo está disponible cuando [/std: c ++ 17](std-specify-language-standard-version.md) o [/std: c ++ más reciente](std-specify-language-standard-version.md) está habilitado. En **/std: c ++ 17** o **/std: c ++ más reciente**, **/Zc: alignednew** está habilitada de forma predeterminada para cumplir con la norma ISO C ++ 17 estándar. Si el único motivo implementan operador **nueva** y **eliminar** es admitir alineada en exceso de asignaciones, es posible que ya no necesita este código en modo C ++ 17. Para desactivar esta opción y revertir al comportamiento 14 C ++ de **nueva** y **eliminar** cuando **/std::c ++ 17** o **/std: c ++ más reciente** se especifica, especificar **/Zc:alignedNew-**. Si implementa el operador **nueva** y **eliminar** pero no está listo para implementar el operador sobrealineado **nueva** y **eliminar** las sobrecargas que tienen el `align_val_t` parámetro, use el **/Zc:alignedNew-** opción para evitar que el compilador y la biblioteca estándar de generación de las llamadas a las sobrecargas alineadas en exceso. El [/ permissive-](permissive-standards-conformance.md) opción no cambia la configuración predeterminada de **/Zc: alignednew**.

## <a name="example"></a>Ejemplo

Este ejemplo se muestra cómo operador **nueva** y operador **eliminar** comportará cuando la **/Zc: alignednew** opción está establecida.

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

Esta salida es típica de las compilaciones de 32 bits. El puntero valores varían en función de donde se ejecuta la aplicación en la memoria.

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

Para obtener información acerca de problemas de conformidad en Visual C++, vea [comportamiento no estándar](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad incluir **/Zc: alignednew** o **/Zc:alignedNew-** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](zc-conformance.md)
