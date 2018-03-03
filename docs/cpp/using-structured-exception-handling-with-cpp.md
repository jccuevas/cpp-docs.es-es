---
title: Uso de excepciones estructurado con C++ | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling, mixed with SEH
- structured exception handling [C++], with C++ exception handling
ms.assetid: ec34b528-8c26-4429-b24a-6a68553aaa91
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db5d067a391512d56a2d01ce3052ac3fab061f28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-structured-exception-handling-with-c"></a>Usar el control de excepciones estructurado con C++
El control de excepciones estructurado descrito en estos artículos funciona con archivos de código fuente de C y C++. Sin embargo, no está diseñado específicamente para C++ y no se recomienda. Para asegurarse de que el código será más portable, use el control de excepciones de C++. Además, el mecanismo de control de excepciones de C++ es más flexible, ya que puede controlar excepciones de cualquier tipo.  
  
 Microsoft C++ admite el modelo de control de excepciones de C++, basado en el estándar ANSI C++. Este mecanismo controla automáticamente la destrucción de objetos locales durante el desenredo de la pila. Si está escribiendo código de C++ con tolerancia a errores y desea implementar el control de excepciones, se recomienda encarecidamente utilizar el control de excepciones de C++, en lugar del control de excepciones estructurado. (Tenga en cuenta que mientras que el compilador de C++ admite construcciones de control de excepciones estructurado como se describe en estos artículos, el compilador de C estándar no admite la sintaxis de control de excepciones de C++). Para obtener información detallada sobre el control de excepciones de C++, vea [control de excepciones de C++](../cpp/cpp-exception-handling.md) y *Annotated C++ Reference Manual* de Margaret Ellis y Bjarne Stroustrup.  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)