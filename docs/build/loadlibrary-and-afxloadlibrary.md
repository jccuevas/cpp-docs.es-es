---
title: LoadLibrary y AfxLoadLibrary
description: Usar LoadLibrary y AfxLoadLibrary para la carga explícita de archivos dll en MSVC.
ms.date: 01/28/2020
f1_keywords:
- LoadLibrary
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
ms.openlocfilehash: f803212c4485f7517dc42802f1ff581ffa4e609d
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821543"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary y AfxLoadLibrary

Los procesos llaman a [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) o [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) para vincularse explícitamente a un archivo dll. (Las aplicaciones MFC usan [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary) o [AfxLoadLibraryEx](../mfc/reference/application-information-and-management.md#afxloadlibraryex)). Si la función se ejecuta correctamente, asigna el archivo DLL especificado en el espacio de direcciones del proceso de llamada y devuelve un identificador al archivo DLL. El identificador es necesario en otras funciones usadas para la vinculación explícita; por ejemplo, `GetProcAddress` y `FreeLibrary`. Para obtener más información, vea [vinculación explícita](linking-an-executable-to-a-dll.md#linking-explicitly).

`LoadLibrary` intenta encontrar el archivo DLL con la misma secuencia de búsqueda que se usa para la vinculación implícita. `LoadLibraryEx` proporciona más control sobre el orden de la ruta de búsqueda. Para obtener más información, vea orden de búsqueda de la [biblioteca de vínculos dinámicos](/windows/win32/dlls/dynamic-link-library-search-order). Si el sistema no puede encontrar el archivo DLL o si la función de punto de entrada devuelve FALSE, `LoadLibrary` devuelve NULL. Si la llamada a `LoadLibrary` especifica un módulo DLL que ya está asignado en el espacio de direcciones del proceso de llamada, la función devuelve un identificador del archivo DLL e incrementa el recuento de referencias del módulo.

Si el archivo DLL tiene una función de punto de entrada, el sistema operativo llama a la función en el contexto del subproceso que llamó a `LoadLibrary` o `LoadLibraryEx`. No se llama a la función de punto de entrada si el archivo DLL ya está asociado al proceso. Esto sucede cuando una llamada anterior a `LoadLibrary` o `LoadLibraryEx` para la DLL no tiene una llamada correspondiente a la función `FreeLibrary`.

En el caso de las aplicaciones MFC que cargan archivos dll de extensión de MFC, se recomienda usar `AfxLoadLibrary` o `AfxLoadLibraryEx` en lugar de `LoadLibrary` o `LoadLibraryEx`. Las funciones de MFC controlan la sincronización de subprocesos antes de cargar el archivo DLL explícitamente. Las interfaces (prototipos de función) para `AfxLoadLibrary` y `AfxLoadLibraryEx` son las mismas que `LoadLibrary` y `LoadLibraryEx`.

Si Windows no puede cargar el archivo DLL, el proceso puede intentar recuperarse del error. Por ejemplo, puede notificar al usuario el error y, a continuación, solicitar otra ruta de acceso al archivo DLL.

> [!IMPORTANT]
> Asegúrese de especificar la ruta de acceso completa de los archivos dll. Se puede buscar primero en el directorio actual cuando los archivos se cargan mediante `LoadLibrary`. Si no califica completamente la ruta de acceso del archivo, es posible que se cargue un archivo que no sea el deseado. Cuando cree un archivo DLL, utilice la opción del vinculador [/DEPENDENTLOADFLAG](reference/dependentloadflag.md) para especificar un orden de búsqueda para las dependencias de dll vinculadas estáticamente. Dentro de los archivos dll, utilice rutas de acceso completas para las dependencias cargadas explícitamente y `LoadLibraryEx` o `AfxLoadLibraryEx` parámetros de llamada para especificar el orden de búsqueda de módulos. Para obtener más información, vea [seguridad de la biblioteca de vínculos dinámicos](/windows/win32/dlls/dynamic-link-library-security) y orden de búsqueda de la [biblioteca de vínculos dinámicos](/windows/win32/dlls/dynamic-link-library-search-order).

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Vincular un ejecutable a un archivo DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Vincular un ejecutable a un archivo DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Orden de búsqueda de la biblioteca de vínculos dinámicos](/windows/win32/Dlls/dynamic-link-library-search-order)

- [FreeLibrary y AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>Vea también

- [Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)
