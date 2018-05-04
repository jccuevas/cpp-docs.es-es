---
title: /Zc:alignedNew (c ++ 17 exceso asignación alineadas) | Documentos de Microsoft
ms.date: 02/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:alignedNew
dev_langs:
- C++
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
author: corob-msft
ms.author: corob
ms.openlocfilehash: 5f9527d63a9843bd4df90520e5b4759126d72fe1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew (c ++ 17 exceso asignación alineadas)

Habilitar la compatibilidad con C ++ 17 exceso alineado **nueva**, asignación de memoria dinámica alineada en límites de mayores que el valor predeterminado para el tamaño máximo alineado tipo estándar, **max\_alinear\_t**.

## <a name="syntax"></a>Sintaxis

> **/Zc:alignedNew**[-]

## <a name="remarks"></a>Comentarios

Visual Studio versión 15,5 permite compilador y compatibilidad con bibliotecas para la asignación de C ++ 17 estándar alineadas excesiva memoria dinámica. Cuando el **/Zc:alignedNew** se especifica la opción, una asignación dinámica como `new Example;` respeta la alineación de *ejemplo* incluso cuando es mayor que `max_align_t`, la alineación mayor necesario para cualquier tipo fundamental. Cuando la alineación del tipo asignado no es más que garantiza que el operador original **nueva**, que está disponible como el valor de la macro predefinida  **\_ \_STDCPP\_predeterminado \_NEW\_alineación\_\_**, la instrucción `new Example;` da como resultado una llamada a `::operator new(size_t)` tal y como se hacía en C ++ 14. Cuando es mayor que la alineación  **\_ \_STDCPP\_predeterminado\_NEW\_alineación\_\_**, la implementación en su lugar obtiene la memoria mediante el uso de `::operator new(size_t, align_val_t)`. Del mismo modo, se invoca la eliminación de tipos alineados exceso `::operator delete(void*, align_val_t)` o elimina el tamaño firma `::operator delete(void*, size_t, align_val_t)`.

El **/Zc:alignedNew** opción sólo está disponible cuando [/std:c ++ 17](std-specify-language-standard-version.md) o [/std:c ++ más reciente](std-specify-language-standard-version.md) está habilitado. En **/std:c ++ 17** o **/std:c ++ más reciente**, **/Zc:alignedNew** está habilitada de forma predeterminada para que se ajuste a la norma ISO C ++ 17 estándar. Si la única razón implementa operador **nueva** y **eliminar** consiste en admitir las asignaciones de exceso alineadas, ya no necesite este código en modo de C ++ 17. Para desactivar esta opción y revertir al comportamiento 14 C ++ de **nueva** y **eliminar** cuando **/std::c ++ 17** o **/std:c ++ más reciente** se especifica, Especifique **/Zc:alignedNew-**. Si implementa el operador **nueva** y **eliminar** pero no está listo para implementar el operador exceso alineado **nueva** y **eliminar** las sobrecargas que tienen la `align_val_t` parámetro, use la **/Zc:alignedNew-** opción para impedir que el compilador y la biblioteca estándar de generar llamadas a las sobrecargas exceso alineadas. El [/ permisivo-](permissive-standards-conformance.md) opción no cambia la configuración predeterminada de **/Zc:alignedNew**.

## <a name="example"></a>Ejemplo

Este ejemplo se muestra cómo operador **nueva** and (operador) **eliminar** comportará cuando la **/Zc:alignedNew** opción está establecida.

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

Esta salida es típica para las compilaciones de 32 bits. El puntero valores varían según donde se ejecuta la aplicación en la memoria.

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

Para obtener información acerca de los problemas de conformidad en Visual C++, vea [comportamiento no estándar](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C/C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad para incluir **/Zc:alignedNew** o **/Zc:alignedNew-** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](../../build/reference/zc-conformance.md)  
