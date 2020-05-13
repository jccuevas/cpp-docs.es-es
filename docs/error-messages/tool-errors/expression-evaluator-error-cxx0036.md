---
title: Error del evaluador de expresiones CXX0036
ms.date: 11/04/2016
f1_keywords:
- CXX0036
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
ms.openlocfilehash: 164fd9ee00071e218e5bb4f3ab00febc618725a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195505"
---
# <a name="expression-evaluator-error-cxx0036"></a>Error del evaluador de expresiones CXX0036

contexto no válido {...} specification

Este mensaje puede ser generado por cualquiera de los diversos errores en el uso del operador de contexto ( **{}** ).

- La sintaxis del operador de contexto ( **{}** ) no se proporcionó correctamente.

   La sintaxis del operador de contexto es:

     {*function*,*Module*,*dll*} *expresión* de

   Esto especifica el contexto de la *expresión*. El operador de contexto tiene la misma precedencia y uso que una conversión de tipo.

   Se pueden omitir las comas finales. Si alguna de las *funciones*, *módulos*o *dll* contiene una coma literal, debe escribir el nombre completo entre paréntesis.

- El nombre de la función se ha escrito incorrectamente o no existe en el módulo especificado o en la biblioteca de vínculos dinámicos.

   Dado que C es un lenguaje que distingue entre mayúsculas y minúsculas, la *función* se debe proporcionar en el caso exacto, ya que se define en el origen.

- No se pudo encontrar el módulo o la DLL.

   Compruebe el nombre de la ruta de acceso completa del módulo o DLL especificado.

Este error es idéntico a CAN0036.
