---
title: 'Cómo: Proporcionar funciones de trabajo a las clases call y transformer'
ms.date: 11/04/2016
helpviewer_keywords:
- call class, example
- using the transformer class [Concurrency Runtime]
- using the call class [Concurrency Runtime]
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
ms.openlocfilehash: 4d2b7b3c88b51003a96526ef14d9940a8c26c3b3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142490"
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>Cómo: Proporcionar funciones de trabajo a las clases call y transformer

En este tema se muestran varias maneras de proporcionar funciones de trabajo a las clases [Concurrency:: Call](../../parallel/concrt/reference/call-class.md) y [Concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) .

En el primer ejemplo se muestra cómo pasar una expresión lambda a un objeto `call`. En el segundo ejemplo se muestra cómo pasar un objeto de función a un objeto `call`. En el tercer ejemplo se muestra cómo enlazar un método de clase a un objeto `call`.

Para que sirva de ilustración, cada ejemplo en este tema usa la clase `call`. Para obtener un ejemplo en el que se usa la clase `transformer`, vea [Cómo: usar el transformador en una canalización de datos](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).

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

El siguiente ejemplo es similar al anterior, salvo que usa las funciones [STD:: bind1st](../../standard-library/functional-functions.md#bind1st) y [std:: mem_fun](../../standard-library/functional-functions.md#mem_fun) para enlazar un objeto `call` a un método de clase.

Use esta técnica si tiene que enlazar un objeto `call` o `transformer` a un método de clase concreto en lugar del operador de llamada de función, `operator()`.

[!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]

También puede asignar el resultado de la función `bind1st` a un objeto [STD:: function](../../standard-library/function-class.md) o utilizar la palabra clave `auto`, como se muestra en el ejemplo siguiente.

[!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `call.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

> **cl. exe/EHsc Call. cpp**

## <a name="see-also"></a>Consulte también

[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Procedimiento para usar la clase transformer en una canalización de datos](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
[call (clase)](../../parallel/concrt/reference/call-class.md)<br/>
[transformer (clase)](../../parallel/concrt/reference/transformer-class.md)
