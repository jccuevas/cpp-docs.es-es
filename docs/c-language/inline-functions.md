---
title: Funciones insertadas | Microsoft Docs
ms.custom: 
ms.date: 10/16/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- fast code
- inline functions, __inline keyword
- functions [C++], inline functions
ms.assetid: 00f4b2ff-8ad0-4165-9f4c-2ef157d03f31
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b5adadc990bed67abe739a4d73b2973b26ca207
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="inline-functions"></a>Funciones insertadas

**Específicos de Microsoft**

La palabra clave `__inline` indica al compilador que sustituya el código en la definición de función para cada instancia de una llamada a función. Sin embargo, la sustitución solo se produce a discreción del compilador. Por ejemplo, el compilador no alinea una función si se usa su dirección o si es demasiado grande para alinearla.

Para que una función se considere candidata para la inserción, debe usar una definición de función nueva.

Use este formato para especificar una función insertada:

> **__inline** *type*<sub>opt</sub> *function-definition*

El uso de funciones insertadas genera código más rápido, e incluso a veces genera código más pequeño que la llamada a función equivalente, por los motivos siguientes:

- Reduce el tiempo necesario para ejecutar llamadas a función.

- Las funciones insertadas pequeñas, de quizás tres o menos líneas, generan menos código que la llamada a función equivalente, porque el compilador no genera código para controlar los argumentos y el valor devuelto.

- Las funciones generadas alineadas están sujetas a optimizaciones de código que no están disponibles para las funciones normales, porque el compilador no realiza optimizaciones entre procedimientos.

No deben confundirse las funciones que usan `__inline` con el código ensamblador alineado. Vea [Ensamblador en línea](../c-language/inline-assembler-c.md) para obtener más información.

**FIN de Específicos de Microsoft**  

## <a name="see-also"></a>Vea también

[inline, __inline, \__forceinline](../cpp/inline-functions-cpp.md)

