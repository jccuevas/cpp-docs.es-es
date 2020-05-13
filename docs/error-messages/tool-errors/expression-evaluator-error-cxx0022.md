---
title: Error del evaluador de expresiones CXX0022
ms.date: 11/04/2016
f1_keywords:
- CXX0022
helpviewer_keywords:
- CXX0022
- CAN0022
ms.assetid: f6b299ac-a4ee-492c-bd9f-6fff005bc537
ms.openlocfilehash: 5858ce936acfb8b949351c9263f3a9379c73648e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195830"
---
# <a name="expression-evaluator-error-cxx0022"></a>Error del evaluador de expresiones CXX0022

llamada de función antes de _main

El evaluador de expresiones de C no puede evaluar una función antes de que el depurador haya entrado en la función **_main**. El programa no se inicializa correctamente hasta que se ha llamado a **_main** .

Este error es idéntico a CAN0022.
