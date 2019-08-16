---
title: /DEPENDENTLOADFLAG (Establecer marcas de carga dependientes predeterminadas)
description: La opción/DEPENDENTLOADFLAG establece las marcas predeterminadas para los archivos dll cargados mediante LoadLibrary
ms.date: 05/18/2018
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 072fa1103d049c7d5c395ae88d268f3b47e20b4f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492949"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/DEPENDENTLOADFLAG (Establecer marcas de carga dependientes predeterminadas)

Establece los marcadores de carga predeterminados que se usan cuando `LoadLibrary` se usa para cargar archivos dll.

## <a name="syntax"></a>Sintaxis

> **/DEPENDENTLOADFLAG**[ **:** _loadflags_]

### <a name="arguments"></a>Argumentos

*loadflags*<br/>
Valor entero de 16 bits de estilo "C" opcional en formato decimal, octal con un cero a la izquierda, o hexadecimal con un `0x`inicial, que especifica las marcas de carga dependientes que se van a aplicar a todas las llamadas [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) . El valor predeterminado es 0.

## <a name="remarks"></a>Comentarios

Esta opción es nueva en Visual Studio 2017 y se aplica solo a las aplicaciones que se ejecutan en Windows 10 RS1 y versiones posteriores. Otros sistemas operativos que ejecutan la aplicación omiten esta opción.

En los sistemas operativos compatibles, esta opción tiene el efecto de cambiar las `LoadLibrary("dependent.dll")` llamadas a al equivalente `LoadLibraryEx("dependent.dll", 0, loadflags)`de. Las llamadas a [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) no se ven afectadas. Esta opción no se aplica de forma recursiva a los archivos dll cargados por la aplicación.

Esta marca se puede usar para evitar ataques de plantación de archivos DLL. Por ejemplo, si una aplicación usa `LoadLibrary` para cargar un archivo dll dependiente, un atacante podría plantar un archivo dll con el mismo nombre en la ruta `LoadLibrary`de acceso de búsqueda que usa, como el directorio actual, que se puede comprobar antes que los directorios del sistema si el modo de búsqueda de dll seguro es disponible. El modo de búsqueda segura de DLL coloca el directorio actual del usuario más adelante en el orden de búsqueda y está habilitado de forma predeterminada en Windows XP SP2 y versiones posteriores. Para obtener más información, vea [orden de búsqueda en la biblioteca de vínculos dinámicos](/windows/win32/Dlls/dynamic-link-library-search-order).

Si especifica la opción `/DEPENDENTLOADFLAG:0xA00` de vínculo (el valor de las marcas `LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`combinadas), incluso si el modo de búsqueda de archivos dll seguro está deshabilitado en el equipo del usuario, la ruta de búsqueda de dll se limita a los directorios protegidos que son más difíciles de encontrar para un atacante. cambios. Para obtener información sobre las marcas disponibles y sus valores simbólicos y numéricos, vea la descripción del parámetro *dwFlags* en [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw).

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Para establecer la opción del vinculador DEPENDENTLOADFLAG en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades**línea de comandos** del**vinculador** > de **propiedades** > de configuración.

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
