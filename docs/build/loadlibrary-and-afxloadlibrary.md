---
title: LoadLibrary y AfxLoadLibrary | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dd24f125398cab606ca835094727a4a2819fb17e
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary y AfxLoadLibrary
Procesa llamada [LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187) (o [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) para vincularse explícitamente a un archivo DLL. Si la función se realiza correctamente, se asigna el archivo DLL especificado en el espacio de direcciones del proceso que realiza la llamada y devuelve un identificador al archivo DLL que puede utilizarse con otras funciones en la vinculación explícita, por ejemplo, `GetProcAddress` y `FreeLibrary`.  
  
 `LoadLibrary`intenta encontrar el archivo DLL mediante el uso de la misma secuencia de búsqueda que se utiliza para la vinculación implícita. Si el sistema no encuentra el archivo DLL o si la función de punto de entrada devuelve FALSE, `LoadLibrary` devuelve NULL. Si la llamada a `LoadLibrary` especifica un módulo DLL que ya está asignado en el espacio de direcciones del proceso que realiza la llamada, la función devuelve un identificador de la DLL y se incrementa el recuento de referencias del módulo.  
  
 Si el archivo DLL tiene una función de punto de entrada, el sistema operativo llama a la función en el contexto del subproceso que llamó a `LoadLibrary`. No se llama a la función de punto de entrada si el archivo DLL ya está asociado al proceso a causa de una llamada anterior a `LoadLibrary` no cuya una llamada correspondiente a la `FreeLibrary` (función).  
  
 Para aplicaciones MFC que cargan archivos DLL de extensión MFC, se recomienda que realice `AfxLoadLibrary` en lugar de `LoadLibrary`. `AfxLoadLibrary`identificadores de sincronización de subprocesos antes de llamar a `LoadLibrary`. La interfaz (prototipo de función) a `AfxLoadLibrary` es el mismo que `LoadLibrary`.  
  
 Si Windows no puede cargar el archivo DLL, el proceso puede intentar recuperarse del error. Por ejemplo, el proceso podría notificar al usuario del error y pedir al usuario que especifique otra ruta de acceso al archivo DLL.  
  
> [!IMPORTANT]
>  Asegúrese de especificar la ruta de acceso completa de los archivos DLL. Se busca primero en el directorio actual cuando se cargan los archivos. Si no cumple la ruta de acceso del archivo, puede cargar un archivo que no es el previsto.  
  
## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?  
  
-   [Cómo vincular implícitamente a un archivo DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [Determinar qué método de vinculación para usar](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [La ruta de acceso de búsqueda que usa Windows para encontrar un archivo DLL](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
-   [FreeLibrary y AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
## <a name="see-also"></a>Vea también  
 [Archivos DLL en Visual C++](../build/dlls-in-visual-cpp.md)   
 [LoadLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259187)   
 [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)