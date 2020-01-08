---
title: /DEPENDENTLOADFLAG (Establecer marcas de carga dependientes predeterminadas)
description: La opción/DEPENDENTLOADFLAG establece las marcas predeterminadas para los archivos dll cargados mediante LoadLibrary
ms.date: 12/22/2018
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 3a403f22c88ccd3e25ba95c183656ad2ffafd05a
ms.sourcegitcommit: ef34a11cb04511221bf5c7b9f4f55ad91a7a603f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/23/2019
ms.locfileid: "75330003"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/DEPENDENTLOADFLAG (Establecer marcas de carga dependientes predeterminadas)

Establece los indicadores de carga predeterminados que se usan cuando se usa `LoadLibrary` para cargar archivos dll.

## <a name="syntax"></a>Sintaxis

> **/DEPENDENTLOADFLAG**[ __:__ *load_flags*]

### <a name="arguments"></a>Argumentos

*load_flags*<br/>
Valor entero de 16 bits de estilo "C" opcional en formato decimal, octal con un cero a la izquierda, o hexadecimal con un `0x`inicial, que especifica las marcas de carga dependientes que se van a aplicar a todas las llamadas [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) . El valor predeterminado es 0.

## <a name="remarks"></a>Notas

Esta opción es nueva en Visual Studio 2017. Solo se aplica a las aplicaciones que se ejecutan en Windows 10 RS1 y versiones posteriores. Otros sistemas operativos que ejecutan la aplicación omiten esta opción.

En los sistemas operativos compatibles, esta opción tiene el efecto de cambiar las llamadas a `LoadLibrary("dependent.dll")` al equivalente de `LoadLibraryEx("dependent.dll", 0, load_flags)`. Las llamadas a [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) no se ven afectadas. Esta opción no se aplica de forma recursiva a los archivos dll cargados por la aplicación.

Esta marca se puede usar para hacer que los [ataques de plantación de archivos dll](/windows/win32/dlls/dynamic-link-library-security) sean más difíciles. Por ejemplo, si una aplicación usa `LoadLibrary` para cargar un archivo DLL dependiente, un atacante podría plantar un archivo DLL con el mismo nombre en la ruta de acceso de búsqueda que usa `LoadLibrary`, como el directorio actual, que se puede comprobar antes que los directorios del sistema si el modo de búsqueda segura de DLL está deshabilitado. El modo de búsqueda segura de DLL coloca el directorio actual del usuario más adelante en el orden de búsqueda y está habilitado de forma predeterminada en Windows XP SP2 y versiones posteriores. Para obtener más información, vea [orden de búsqueda en la biblioteca de vínculos dinámicos](/windows/win32/Dlls/dynamic-link-library-search-order).

Si especifica la opción de vínculo `/DEPENDENTLOADFLAG:0xA00` (el valor de las marcas combinadas `LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`), incluso si el modo de búsqueda de archivos DLL seguro está deshabilitado en el equipo del usuario, la ruta de acceso de búsqueda de DLL se limita al directorio de la aplicación, seguido del directorio%Windows%\System32 Una opción de `/DEPENDENTLOADFLAG:0x800` es incluso más restrictiva, lo que limita la búsqueda al directorio%Windows%\System32 Los directorios protegidos son más difíciles, pero no imposibles, para que un atacante cambie. Para obtener información sobre las marcas disponibles y sus valores simbólicos y numéricos, vea la descripción del parámetro *dwFlags* en [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw). Para obtener información sobre el orden de búsqueda que se usa cuando se usan varias marcas de carga dependientes, vea [orden de búsqueda con marcas de LOAD_LIBRARY_SEARCH](/windows/win32/dlls/dynamic-link-library-search-order#search-order-using-load_library_search-flags).

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Para establecer la opción del vinculador DEPENDENTLOADFLAG en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **Propiedades de configuración** > **Enlazador** > **Línea de comandos**.

1. Escriba la opción en **opciones adicionales**.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

- [Referencia del enlazador MSVC](linking.md)
- [Opciones del enlazador MSVC](linker-options.md)
- [Vincular un ejecutable a un archivo DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [Vincular un ejecutable a un archivo DLL](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)
- [Orden de búsqueda de la biblioteca de vínculos dinámicos](/windows/win32/Dlls/dynamic-link-library-search-order)
