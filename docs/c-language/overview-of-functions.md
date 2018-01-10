---
title: "Información general de funciones | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- functions [C++]
- control flow, function calls
ms.assetid: b6f4637f-02b9-49d8-8601-1f886bd2cfb9
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 093400e5d98b0b5e0336c2f640ed0937bdb157b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-functions"></a>Información general de funciones
Las funciones deben tener una definición y deberían tener una declaración, aunque una definición puede actuar como declaración si la declaración aparece antes de que se llame a la función. La definición de función incluye el cuerpo de la función (el código que se ejecuta cuando se llama a la función).  
  
 Una declaración de función establece el nombre, el tipo de valor devuelto y los atributos de una función definida en otra parte del programa. Una declaración de función debe preceder a la llamada a la función. Esta es la razón por la que los archivos de encabezado que contienen las declaraciones de las funciones en tiempo de ejecución se incluyen en el código antes de la llamada a una función en tiempo de ejecución. Si la declaración tiene información sobre los tipos y el número de parámetros, la declaración es un prototipo. Vea [Prototipos de función](../c-language/function-prototypes.md) para obtener más información.  
  
 El compilador utiliza el prototipo para comparar los tipos de los argumentos en las llamadas subsiguientes a la función con los parámetros de la función y para convertir los tipos de los argumentos a los tipos de los parámetros cuando sea necesario.  
  
 Una llamada de función pasa el control de la ejecución de la función de llamada a la función llamada. Los argumentos, si existe, se pasan por valor a la función llamada. La ejecución de una instrucción `return` en la función llamada devuelve el control y probablemente un valor a la función de llamada.  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../c-language/functions-c.md)