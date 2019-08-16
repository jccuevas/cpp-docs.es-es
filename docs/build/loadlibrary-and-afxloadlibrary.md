---
title: LoadLibrary y AfxLoadLibrary
ms.date: 05/24/2018
f1_keywords:
- LoadLibrary
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
ms.openlocfilehash: c7700dd865e320686a2ad8bd036f207b9ecee6ac
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493208"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary y AfxLoadLibrary

Los procesos llaman a [LoadLibraryExA](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa) o [LoadLibraryExW](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) (o [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) para vincularse explícitamente a un archivo dll. Si la función se ejecuta correctamente, asigna el archivo dll especificado en el espacio de direcciones del proceso de llamada y devuelve un identificador al archivo DLL que se puede usar con otras funciones en la vinculación explícita `GetProcAddress` , `FreeLibrary`por ejemplo, y.

`LoadLibrary`intenta localizar el archivo DLL con la misma secuencia de búsqueda que se utiliza para la vinculación implícita. Si el sistema no puede encontrar el archivo dll o si la función de punto de entrada `LoadLibrary` devuelve false, devuelve NULL. Si la llamada a `LoadLibrary` especifica un módulo DLL que ya está asignado en el espacio de direcciones del proceso de llamada, la función devuelve un identificador del archivo DLL e incrementa el recuento de referencias del módulo.

Si el archivo DLL tiene una función de punto de entrada, el sistema operativo llama a la función en el contexto del subproceso que llamó a `LoadLibrary`. No se llama a la función de punto de entrada si el archivo DLL ya está asociado al proceso debido a una llamada `LoadLibrary` anterior a que no tiene ninguna llamada `FreeLibrary` correspondiente a la función.

En el caso de las aplicaciones MFC que cargan archivos dll de extensión `AfxLoadLibrary` de MFC, `LoadLibrary`se recomienda utilizar en lugar de. `AfxLoadLibrary`controla la sincronización de subprocesos antes de llamar a `LoadLibrary`. La interfaz (prototipo de función) `AfxLoadLibrary` en es igual que `LoadLibrary`.

Si Windows no puede cargar el archivo DLL, el proceso puede intentar recuperarse del error. Por ejemplo, el proceso podría notificar el error al usuario y pedir al usuario que especifique otra ruta de acceso al archivo DLL.

> [!IMPORTANT]
> Asegúrese de especificar la ruta de acceso completa de los archivos dll. En primer lugar, se busca en el directorio actual cuando se cargan los archivos. Si no califica la ruta de acceso del archivo, es posible que se cargue un archivo que no sea el deseado. Otra manera de evitar esto es mediante la opción del enlazador [/DEPENDENTLOADFLAG](reference/dependentloadflag.md) .

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Vincular un ejecutable a un archivo DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Vincular un ejecutable a un archivo DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Orden de búsqueda de la biblioteca de vínculos dinámicos](/windows/win32/Dlls/dynamic-link-library-search-order)

- [FreeLibrary y AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>Vea también

- [Creación de archivos DLL de C/C++ en Visual Studio](dlls-in-visual-cpp.md)
