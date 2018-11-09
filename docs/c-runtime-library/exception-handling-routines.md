---
title: Rutinas para el control de excepciones
ms.date: 11/04/2016
f1_keywords:
- c.exceptions
helpviewer_keywords:
- exception handling, routines
ms.assetid: f60548c6-850a-4e1e-a79b-a2a6a541ab62
ms.openlocfilehash: 09d58e49d3c9dc9b4b8ef40f725e927603e3e47c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507463"
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
