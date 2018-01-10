---
title: Limpieza de excepciones de CString | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 496fdfe6a609bd4eceae225c2568c915d38aef07
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cstring-exception-cleanup"></a>Limpieza de excepciones de CString
En versiones anteriores de MFC, era importante limpiar [CString](../atl-mfc-shared/reference/cstringt-class.md) objetos tras su uso. Con la versión 3.0 y versiones posterior de MFC, ya no es necesario limpiar explícita.  
  
 En el mecanismo utilizado por MFC ahora de control de excepciones de C++, no tiene que preocuparse por la limpieza después de una excepción. Para obtener una descripción de cómo C++ "desenreda" la pila después de que se detecta una excepción, vea [try, catch y throw (instrucciones)](../cpp/try-throw-and-catch-statements-cpp.md). Incluso si se utiliza la MFC **intente**/**CATCH** macros en lugar de las palabras clave de C++ **intente** y **catch**, MFC utiliza C++ mecanismo de excepciones bajo, por lo que aún no es necesario limpiar explícitamente.  
  
## <a name="see-also"></a>Vea también  
 [Cadenas (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)

