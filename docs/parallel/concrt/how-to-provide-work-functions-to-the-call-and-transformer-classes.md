---
title: 'Cómo: proporcionar funciones de trabajo a las clases call y transformer | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- call class, example
- using the transformer class [Concurrency Runtime]
- using the call class [Concurrency Runtime]
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3102947009780f6f4e735b70506c5b2dc02f416b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438969"
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>Cómo: Proporcionar funciones de trabajo a las clases call y transformer

En este tema se ilustra varias maneras de proporcionar funciones de trabajo para el [Concurrency:: call](../../parallel/concrt/reference/call-class.md) y [Concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) clases.

En el primer ejemplo se muestra cómo pasar una expresión lambda a un objeto `call`. En el segundo ejemplo se muestra cómo pasar un objeto de función a un objeto `call`. En el tercer ejemplo se muestra cómo enlazar un método de clase a un objeto `call`.

Para que sirva de ilustración, cada ejemplo en este tema usa la clase `call`. Para obtener un ejemplo que usa el `transformer` de clases, vea [Cómo: usar la clase transformer en una canalización de datos](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra una manera común de usar la clase `call`: En este ejemplo se pasa una función lambda al constructor `call`.

[!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]

Este ejemplo produce el siguiente resultado:

```Output
13 squared is 169.
```

## <a name="example"></a>Ejemplo

El siguiente ejemplo se parece el anterior, sólo que usa la clase `call` junto con un objeto de función (functor).

[!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se parece el anterior, salvo que usa el [std:: bind1st](../../standard-library/functional-functions.md#bind1st) y [std:: mem_fun](../../standard-library/functional-functions.md#mem_fun) funciones para enlazar un `call` objeto a un método de clase.

Use esta técnica si tiene que enlazar un objeto `call` o `transformer` a un método de clase concreto en lugar del operador de llamada de función, `operator()`.

[!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]

También puede asignar el resultado de la `bind1st` funcione a un [std:: Function](../../standard-library/function-class.md) de objeto o usar el `auto` palabra clave, como se muestra en el ejemplo siguiente.

[!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `call.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe/EHsc call.cpp**

## <a name="see-also"></a>Vea también

[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Procedimiento para usar la clase transformer en una canalización de datos](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
[call (clase)](../../parallel/concrt/reference/call-class.md)<br/>
[transformer (clase)](../../parallel/concrt/reference/transformer-class.md)
