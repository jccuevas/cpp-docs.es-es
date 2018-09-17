---
title: LoadLibrary y AfxLoadLibrary | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- LoadLibrary
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e2fe0b0523fb411b8ef4700a7dea7832c1cdfc52
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726305"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary y AfxLoadLibrary

Procesa llamada [LoadLibraryExA](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa) o [LoadLibraryExW](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexw)(o [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) para vincularse explícitamente a un archivo DLL. Si la función se realiza correctamente, se asigna el archivo DLL especificado en el espacio de direcciones del proceso que realiza la llamada y devuelve un identificador para el archivo DLL que se puede usar con otras funciones en la vinculación explícita, por ejemplo, `GetProcAddress` y `FreeLibrary`.

`LoadLibrary` intenta encontrar el archivo DLL mediante el uso de la misma secuencia de búsqueda que se utiliza para la vinculación implícita. Si el sistema no encuentra el archivo DLL o si la función de punto de entrada devuelve FALSE, `LoadLibrary` devuelve NULL. Si la llamada a `LoadLibrary` especifica un módulo DLL que ya está asignado al espacio de direcciones del proceso que realiza la llamada, la función devuelve un identificador de la DLL e incrementa el recuento de referencias del módulo.

Si el archivo DLL tiene una función de punto de entrada, el sistema operativo llama a la función en el contexto del subproceso que llama `LoadLibrary`. No se llama a la función de punto de entrada si el archivo DLL ya está asociado al proceso a causa de una llamada anterior a `LoadLibrary` que tiene una llamada correspondiente a la `FreeLibrary` función.

Para aplicaciones MFC que cargan archivos DLL de extensión MFC, se recomienda que use `AfxLoadLibrary` en lugar de `LoadLibrary`. `AfxLoadLibrary` identificadores de sincronización de subprocesos antes de llamar a `LoadLibrary`. La interfaz (prototipo de función) a `AfxLoadLibrary` es el mismo que `LoadLibrary`.

Si Windows no pueden cargar el archivo DLL, el proceso puede intentar recuperarse del error. Por ejemplo, el proceso podría notificar al usuario sobre el error y pedir al usuario que especifique otra ruta de acceso al archivo DLL.

> [!IMPORTANT]
> Asegúrese de especificar la ruta de acceso completa de los archivos DLL. Se busca primero en el directorio actual cuando se cargan archivos. Si no califica la ruta de acceso del archivo, se puede cargar un archivo que no es lo previsto. Otra manera de evitar que esto es mediante la [/DEPENDENTLOADFLAG](../build/reference/dependentloadflag.md) opción del vinculador.

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Cómo vincular implícitamente a un archivo DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)

- [Determinar qué método de vinculación para usar](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Orden de búsqueda de la biblioteca de vínculos dinámicos](/windows/desktop/Dlls/dynamic-link-library-search-order)

- [FreeLibrary y AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](../build/getprocaddress.md)

## <a name="see-also"></a>Vea también

- [Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)
