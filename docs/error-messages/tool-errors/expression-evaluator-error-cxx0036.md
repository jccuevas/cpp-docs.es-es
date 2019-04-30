---
title: Error del evaluador de expresiones CXX0036
ms.date: 11/04/2016
f1_keywords:
- CXX0036
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
ms.openlocfilehash: d7961d92760cc5ac325b4bc9f187d4ee2298479a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397034"
---
# <a name="expression-evaluator-error-cxx0036"></a>Error del evaluador de expresiones CXX0036

contexto no válido {...} especificación

Este mensaje puede generarse por varios errores en el uso del operador de contexto (**{}**).

- La sintaxis del operador de contexto (**{}**) se asignó incorrectamente.

   La sintaxis del operador de contexto es:

     {*function*,*module*,*dll*}*expression*

   Especifica el contexto de *expresión*. El operador de contexto tiene la misma prioridad y uso como una conversión de tipo.

   Pueden omitir las comas finales. Si cualquiera de *función*, *módulo*, o *dll* contiene una coma literal, se debe encerrar el nombre completo entre paréntesis.

- El nombre de función se ha escrito incorrectamente, o no existe en el módulo especificado o la biblioteca de vínculos dinámicos.

   Dado que C es un lenguaje que distingue mayúsculas de minúsculas, *función* deben proporcionarse en las mayúsculas como se define en el origen.

- No se encontró el módulo o DLL.

   Compruebe el nombre de ruta de acceso completa del archivo DLL o módulo especificado.

Este error es idéntico a CAN0036.