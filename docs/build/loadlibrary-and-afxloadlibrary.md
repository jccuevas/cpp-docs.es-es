---
title: LoadLibrary y AfxLoadLibrary
description: Uso de LoadLibrary y AfxLoadLibrary para la carga explícita de archivos DLL en MSVC.
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821543"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary y AfxLoadLibrary

Los procesos llaman a [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) o [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) para vincular explícitamente a un archivo DLL. (Las aplicaciones de MFC usan [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary) o [AfxLoadLibraryEx](../mfc/reference/application-information-and-management.md#afxloadlibraryex)). Si la función se ejecuta correctamente, asigna el archivo DLL especificado en el espacio de direcciones del proceso de llamada y devuelve un controlador para el archivo DLL. El controlador es necesario en otras funciones empleadas para la vinculación explícita, como `GetProcAddress` y `FreeLibrary`. Para obtener más información, vea [Vinculación explícita](linking-an-executable-to-a-dll.md#linking-explicitly).

`LoadLibrary` intenta localizar el archivo DLL con la misma secuencia de búsqueda que se usa para la vinculación implícita. `LoadLibraryEx` proporciona un mayor control sobre el orden de la ruta de búsqueda. Para obtener más información, vea [Orden de búsqueda de las bibliotecas de vínculos dinámicos](/windows/win32/dlls/dynamic-link-library-search-order). Si el sistema no puede encontrar el archivo DLL o si la función de punto de entrada devuelve FALSE, `LoadLibrary` devuelve NULL. Si la llamada a `LoadLibrary` especifica un módulo DLL que ya está asignado en el espacio de direcciones del proceso de llamada, la función devuelve un controlador para el archivo DLL e incrementa el recuento de referencias del módulo.

Si el archivo DLL tiene una función de punto de entrada, el sistema operativo llamará a la función en el contexto del subproceso que ha llamado a `LoadLibraryEx` o `LoadLibrary`. Si el archivo DLL ya está asociado al proceso, no se llama a la función de punto de entrada. Esto sucede cuando una llamada anterior a `LoadLibrary` o `LoadLibraryEx` para la DLL no ha obtenido una llamada correspondiente a la función `FreeLibrary`.

En el caso de las aplicaciones de MFC que cargan archivos DLL de extensión de MFC, se recomienda usar `AfxLoadLibrary` o `AfxLoadLibraryEx` en lugar de `LoadLibrary` o `LoadLibraryEx`. Las funciones de MFC controlan la sincronización de subprocesos antes de cargar el archivo DLL explícitamente. Las interfaces (prototipos de función) para `AfxLoadLibrary` y `AfxLoadLibraryEx` son las mismas que para `LoadLibrary` y `LoadLibraryEx`.

Si Windows no puede cargar el archivo DLL, el proceso puede intentar recuperarse del error. Por ejemplo, podría mostrar una notificación al usuario el error y, luego, solicitar otra ruta de acceso al archivo DLL.

> [!IMPORTANT]
> Asegúrese de especificar la ruta de acceso completa de los archivos DLL. Cuando `LoadLibrary` carga los archivos, se puede buscar primero en el directorio actual. Si no se usa un nombre completo para la ruta de acceso del archivo, es posible que se cargue un archivo que no sea el deseado. Cuando cree un archivo DLL, use la opción [/DEPENDENTLOADFLAG](reference/dependentloadflag.md) del enlazador a fin de especificar un orden de búsqueda para las dependencias del archivo DLL vinculadas estáticamente. En los archivos DLL, use rutas de acceso completas para las dependencias cargadas explícitamente, así como parámetros de llamada `LoadLibraryEx` o `AfxLoadLibraryEx` para especificar el orden de búsqueda de módulos. Para obtener más información, consulte [Seguridad de la biblioteca de vínculos dinámicos](/windows/win32/dlls/dynamic-link-library-security) y [Orden de búsqueda de las bibliotecas de vínculos dinámicos](/windows/win32/dlls/dynamic-link-library-search-order).

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Vincular un ejecutable a un archivo DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Vincular un ejecutable a un archivo DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Orden de búsqueda de la biblioteca de vínculos dinámicos](/windows/win32/Dlls/dynamic-link-library-search-order)

- [FreeLibrary y AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>Vea también

- [Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)
