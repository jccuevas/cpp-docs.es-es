---
title: Limpieza de excepciones de CString | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d18d10d517a6c5b0d075a7fb0ed113448625b698
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="cstring-exception-cleanup"></a>Limpieza de excepciones de CString
En versiones anteriores de MFC, era importante limpiar [CString](../atl-mfc-shared/reference/cstringt-class.md) objetos tras su uso. Con la versión 3.0 y versiones posterior de MFC, ya no es necesario limpiar explícita.  
  
 En el mecanismo utilizado por MFC ahora de control de excepciones de C++, no tiene que preocuparse por la limpieza después de una excepción. Para obtener una descripción de cómo C++ "desenreda" la pila después de que se detecta una excepción, vea [try, catch y throw (instrucciones)](../cpp/try-throw-and-catch-statements-cpp.md). Incluso si se utiliza la MFC **intente**/**CATCH** macros en lugar de las palabras clave de C++ **intente** y **catch**, MFC utiliza C++ mecanismo de excepciones bajo, por lo que aún no es necesario limpiar explícitamente.  
  
## <a name="see-also"></a>Vea también  
 [Cadenas (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)

