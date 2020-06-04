---
title: Limpieza de excepciones de CString
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
ms.openlocfilehash: d131ce8ebe5158d7f3a567580064068742b63707
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236633"
---
# <a name="cstring-exception-cleanup"></a>Limpieza de excepciones de CString

En versiones anteriores de MFC, que era importante limpiar [CString](../atl-mfc-shared/reference/cstringt-class.md) objetos tras su uso. Con la versión 3.0 y versiones posterior de MFC, ya no es necesaria una limpieza explícita.

En el mecanismo que ahora utiliza MFC de control de excepciones de C++, no es necesario preocuparse de limpieza después de una excepción. Para obtener una descripción de cómo C++ "desenreda" la pila después de que se detecta una excepción, vea [try, catch y throw (instrucciones)](../cpp/try-throw-and-catch-statements-cpp.md). Incluso si usa MFC **intente**/**CATCH** macros en lugar de las palabras clave de C++ **intente** y **catch**, MFC utiliza C++ mecanismo de excepción subyacente, por lo que todavía no es necesario limpiar de forma explícita.

## <a name="see-also"></a>Vea también

[Cadenas (ATL y MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Control de excepciones](../mfc/exception-handling-in-mfc.md)
