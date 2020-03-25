---
title: Error del evaluador de expresiones CXX0021
ms.date: 11/04/2016
f1_keywords:
- CXX0021
helpviewer_keywords:
- CXX0021
- CAN0021
ms.assetid: d6c0c35a-16c2-42c0-a7d2-e910350a47f0
ms.openlocfilehash: a800deb6bacbcae8666a3abad08b87d4f027790f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195844"
---
# <a name="expression-evaluator-error-cxx0021"></a>Error del evaluador de expresiones CXX0021

struct o Union usados como escalares

Se usó una estructura o una Unión en una expresión, pero no se especificó ningún elemento.

Al manipular una variable de estructura o de Unión, el nombre de la variable puede aparecer por sí mismo, sin un calificador de campo. Si se usa una estructura o una Unión en una expresión, se debe calificar con el elemento específico deseado.

Especifique el elemento cuyo valor se va a utilizar en la expresión.

Este error es idéntico a CAN0021.
