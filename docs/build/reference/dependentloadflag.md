---
title: /DEPENDENTLOADFLAG (Establecer marcas de carga dependientes predeterminadas)
description: La opción/DEPENDENTLOADFLAG establece los marcadores de carga dependientes predeterminados para los archivos dll cargados por este módulo.
ms.date: 01/22/2020
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 5e31a0d747e7186814cba3ae1c4cf243569d87a8
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725713"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/DEPENDENTLOADFLAG (Establecer marcas de carga dependientes predeterminadas)

::: moniker range="vs-2015"

La opción **/DEPENDENTLOADFLAG** requiere Visual Studio 2017 o posterior.

::: moniker-end

::: moniker range=">=vs-2017"

Establece las marcas de carga predeterminadas que se usan cuando el sistema operativo resuelve las importaciones vinculadas estáticamente de un módulo.

## <a name="syntax"></a>Sintaxis

> **/DEPENDENTLOADFLAG**[ __:__ *load_flags*]

### <a name="arguments"></a>Argumentos

*load_flags*<br/>
Valor entero opcional que especifica las marcas de carga que se van a aplicar al resolver las dependencias de importación vinculadas estáticamente del módulo. El valor predeterminado es 0. Para obtener una lista de valores de marca compatibles, vea las entradas de `LOAD_LIBRARY_SEARCH_*` en [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw).

## <a name="remarks"></a>Notas

Cuando el sistema operativo resuelve las importaciones vinculadas estáticamente de un módulo, usa el [orden de búsqueda predeterminado](/windows/win32/dlls/dynamic-link-library-search-order). Use la opción **/DEPENDENTLOADFLAG** para especificar un valor *load_flags* que cambie la ruta de búsqueda usada para resolver estas importaciones. En los sistemas operativos compatibles, cambia el orden de búsqueda de la resolución de importación estática, de forma similar a lo que se hace [en el uso](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa) de los parámetros de `LOAD_LIBRARY_SEARCH`. Para obtener información sobre el orden de búsqueda establecido por *load_flags*, vea [Buscar el orden mediante marcas de LOAD_LIBRARY_SEARCH](/windows/win32/dlls/dynamic-link-library-search-order#search-order-using-load_library_search-flags).

Esta marca se puede usar para hacer que un vector de [ataque](/windows/win32/dlls/dynamic-link-library-security) sea más difícil. Por ejemplo, considere una aplicación que ha vinculado estáticamente un archivo DLL:

- Un atacante podría plantar un archivo DLL con el mismo nombre anteriormente en la ruta de búsqueda de la resolución de importación, como el directorio de la aplicación. Los directorios protegidos son más difíciles, pero no imposibles, para que un atacante cambie.

- Si falta el archivo DLL de la aplicación,%Windows%\System32 y% Windows% directorios, la resolución de importación se realiza a través del directorio actual. Un atacante podría plantar allí un archivo DLL.

En ambos casos, si se especifica la opción de vínculo `/DEPENDENTLOADFLAG:0x800` (el valor de la marca `LOAD_LIBRARY_SEARCH_SYSTEM32`), la ruta de acceso de búsqueda del módulo se limita al directorio%Windows%\System32 Ofrece cierta protección contra la plantación de ataques en los otros directorios. Para obtener más información, vea [seguridad de la biblioteca de vínculos dinámicos](/windows/win32/dlls/dynamic-link-library-security).

Para ver el valor establecido por la opción **/DEPENDENTLOADFLAG** en cualquier archivo dll, use el comando [dumpbin](dumpbin-reference.md) con la opción [/LOADCONFIG](loadconfig.md) .

La opción **/DEPENDENTLOADFLAG** es nueva en Visual Studio 2017. Solo se aplica a las aplicaciones que se ejecutan en Windows 10 RS1 y versiones posteriores. Otros sistemas operativos que ejecutan la aplicación omiten esta opción.

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Para establecer la opción del vinculador DEPENDENTLOADFLAG en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione las **propiedades de configuración** > **enlazador** > página de propiedades **línea de comandos** .

1. Escriba la opción en **opciones adicionales**.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

- [Referencia del enlazador MSVC](linking.md)
- [Opciones del vinculador MSVC](linker-options.md)
- [Vincular un ejecutable a un archivo DLL implícitamente](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [Determinar el método de vinculación que se va a usar](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)
- [Orden de búsqueda de la biblioteca de vínculos dinámicos](/windows/win32/Dlls/dynamic-link-library-search-order)
- [Seguridad de la biblioteca de vínculos dinámicos](/windows/win32/dlls/dynamic-link-library-security)

::: moniker-end
