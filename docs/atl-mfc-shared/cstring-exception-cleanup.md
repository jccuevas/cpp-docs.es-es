---
title: Limpieza de excepciones de CString | Microsoft Docs
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
ms.openlocfilehash: 656739ad000612f130f5cdfb1a53a6de2d67c4c8
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761373"
---
# <a name="cstring-exception-cleanup"></a>Limpieza de excepciones de CString

En versiones anteriores de MFC, que era importante limpiar [CString](../atl-mfc-shared/reference/cstringt-class.md) objetos tras su uso. Con la versión 3.0 y versiones posterior de MFC, ya no es necesaria una limpieza explícita.

En el mecanismo que ahora utiliza MFC de control de excepciones de C++, no es necesario preocuparse de limpieza después de una excepción. Para obtener una descripción de cómo C++ "desenreda" la pila después de que se detecta una excepción, vea [try, catch y throw (instrucciones)](../cpp/try-throw-and-catch-statements-cpp.md). Incluso si usa MFC **intente**/**CATCH** macros en lugar de las palabras clave de C++ **intente** y **catch**, MFC utiliza C++ mecanismo de excepción subyacente, por lo que todavía no es necesario limpiar de forma explícita.

## <a name="see-also"></a>Vea también

[Cadenas (ATL y MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
[Control de excepciones](../mfc/exception-handling-in-mfc.md)

