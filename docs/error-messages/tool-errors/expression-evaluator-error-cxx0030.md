---
title: Error del evaluador de expresiones CXX0030
ms.date: 11/04/2016
f1_keywords:
- CXX0030
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
ms.openlocfilehash: 477ec31d18924e91baf2d8b7b732bc7a50eee53b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195622"
---
# <a name="expression-evaluator-error-cxx0030"></a>Error del evaluador de expresiones CXX0030

expresión no evaluable

El evaluador de expresiones del depurador no pudo obtener un valor para la expresión escrita. Una causa probable es que la expresión hace referencia a la memoria que se encuentra fuera del espacio de direcciones del programa (el hecho de desreferenciar un puntero nulo es un ejemplo). Windows no permite el acceso a la memoria que se encuentra fuera del espacio de direcciones del programa.

Puede que desee volver a escribir la expresión usando paréntesis para controlar el orden de evaluación.

Este error es idéntico a CAN0030.
