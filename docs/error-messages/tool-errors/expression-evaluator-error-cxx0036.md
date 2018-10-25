---
title: Error del evaluador de expresiones CXX0036 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0036
dev_langs:
- C++
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a94ed846d2d4ebda2e457ee772a9f8bf081d69d6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077179"
---
# <a name="expression-evaluator-error-cxx0036"></a>Error del evaluador de expresiones CXX0036

contexto no válido {...} especificación

Este mensaje puede generarse por varios errores en el uso del operador de contexto (**{}**).

- La sintaxis del operador de contexto (**{}**) se asignó incorrectamente.

   La sintaxis del operador de contexto es:

     {*función*,*módulo*,*dll*}*expresión*

   Especifica el contexto de *expresión*. El operador de contexto tiene la misma prioridad y uso como una conversión de tipo.

   Pueden omitir las comas finales. Si cualquiera de *función*, *módulo*, o *dll* contiene una coma literal, se debe encerrar el nombre completo entre paréntesis.

- El nombre de función se ha escrito incorrectamente, o no existe en el módulo especificado o la biblioteca de vínculos dinámicos.

   Dado que C es un lenguaje que distingue mayúsculas de minúsculas, *función* deben proporcionarse en las mayúsculas como se define en el origen.

- No se encontró el módulo o DLL.

   Compruebe el nombre de ruta de acceso completa del archivo DLL o módulo especificado.

Este error es idéntico a CAN0036.