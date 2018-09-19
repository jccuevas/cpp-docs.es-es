---
title: Rutinas para el control de excepciones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.exceptions
dev_langs:
- C++
helpviewer_keywords:
- exception handling, routines
ms.assetid: f60548c6-850a-4e1e-a79b-a2a6a541ab62
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eea92c5bfdb54b6c15ae2ae643b2d23b397a3bf6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389080"
---
# <a name="exception-handling-routines"></a>Rutinas para el control de excepciones

Utilice las funciones de control de excepciones de C++ para recuperarse de eventos inesperados durante la ejecución del programa.

## <a name="exception-handling-functions"></a>Funciones de control de excepciones

|Función|Usar|
|--------------|---------|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Controla las excepciones Win32 (excepciones estructuradas de C), como excepciones con tipo de C++.|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Instala su propia rutina de finalización a la que debe llamar **terminate**|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Instala su propia función de finalización a la que debe llamar **unexpected**|
|[terminate](../c-runtime-library/reference/terminate-crt.md)|Se llama automáticamente en determinadas circunstancias una vez generada la excepción. La función **terminate** llama a **abort** o a una función que especifique mediante **set_terminate**|
|[unexpected](../c-runtime-library/reference/unexpected-crt.md)|Llama a **terminate** o a una función que especifique mediante **set_unexpected**. La función **unexpected** no se usa en la implementación actual del control de excepciones de Microsoft C++.|

## <a name="see-also"></a>Vea también

[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>
