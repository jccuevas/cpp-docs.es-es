---
title: 'Excepciones: Iniciar excepciones desde sus propias funciones | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 15aeb1af7f41cf2df8be3f69657ec6870c55ab34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>Excepciones: Iniciar excepciones desde sus propias funciones
Es posible utilizar el paradigma de control de excepciones de MFC solamente para detectar las excepciones producidas por las funciones de MFC o de otras bibliotecas. Además de detectar las excepciones producidas por código de la biblioteca, puede iniciar excepciones desde su propio código si va a escribir las funciones que pueden encontrar situaciones excepcionales.  
  
 Cuando se produce una excepción, la ejecución de la función actual se ha detenido y salta directamente a la **catch** bloque del marco de excepciones más interno. El mecanismo de excepción omite la ruta de acceso de salida normal de una función. Por lo tanto, debe asegurarse de eliminar los bloques de memoria que se eliminarían en una salida normal.  
  
#### <a name="to-throw-an-exception"></a>Se producirá una excepción  
  
1.  Use una de las funciones auxiliares MFC, como `AfxThrowMemoryException`. Estas funciones inician un objeto de excepción preasignado del tipo adecuado.  
  
     En el ejemplo siguiente, una función intenta asignar dos bloques de memoria y produce una excepción si se produce un error en cualquier asignación:  
  
     [!code-cpp[NVC_MFCExceptions#17](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]  
  
     Si se produce un error en la primera asignación, simplemente puede producir la excepción de memoria. Si la primera asignación es correcta, pero se produce un error en la otra, debe liberar el primer bloque de asignación antes de iniciar la excepción. Si ambas asignaciones se realizan correctamente, puede continuar normalmente y liberar los bloques al salir de la función.  
  
     - O  
  
2.  Utilice una excepción definida por el usuario para indicar una condición de problema. Puede iniciar un elemento de cualquier tipo, incluso una clase entera, como la excepción.  
  
     En el ejemplo siguiente se intenta reproducir un sonido a través de un dispositivo de onda y produce una excepción si se produce un error.  
  
     [!code-cpp[NVC_MFCExceptions#18](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]  
  
> [!NOTE]
>  Del MFC control predeterminado de las excepciones se aplica solo a los punteros a `CException` objetos (y los objetos de `CException`-las clases derivadas). El ejemplo anterior omite el mecanismo de excepciones de MFC.  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)

