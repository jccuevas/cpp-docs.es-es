---
title: 'Tutorial: Implementar futuros | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- implementing futures [Concurrency Runtime]
- futures, implementing [Concurrency Runtime]
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12f2bd5897945dec0045019462c2faeb665a19e4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="walkthrough-implementing-futures"></a>Tutorial: Implementar futuros
En este tema se muestra cómo implementar futuros en la aplicación. En el tema se muestra cómo combinar la funcionalidad existente en el Runtime de simultaneidad para conseguir algo que hace más.  
  
> [!IMPORTANT]
>  En este tema se muestra el concepto de futuros para fines de demostración. Se recomienda que use [std:: Future](../../standard-library/future-class.md) o [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) cuando necesite una tarea asincrónica que calcula un valor para su uso posterior.  
  
 A *tarea* es un cálculo que se puede descomponer en otros cálculos más específicos. A *futuras* es una tarea asincrónica que calcula un valor para su uso posterior.  
  
 Para implementar futuros, este tema define la clase `async_future`. El `async_future` clase usa los siguientes componentes del Runtime de simultaneidad: la [Concurrency:: task_group](reference/task-group-class.md) clase y la [Concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) clase. La clase `async_future` utiliza la clase `task_group` para calcular un valor de forma asincrónica y la clase `single_assignment` para almacenar el resultado del cálculo. El constructor de la clase `async_future` toma una función de trabajo que calcula el resultado, y el método `get` recupera el resultado.  
  
### <a name="to-implement-the-asyncfuture-class"></a>Para implementar la clase async_future  
  
1.  Declare una clase de plantilla con el nombre `async_future` que se parametrice en el tipo del cálculo resultante. Agregue secciones `public` y `private` a esta clase.  
  
 [!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_1.cpp)]  
  
2.  En la sección `private` de la clase `async_future`, declare miembros de datos `task_group` y `single_assignment`.  
  
 [!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_2.cpp)]  
  

3.  En la sección `public` de la clase `async_future`, implemente el constructor. El constructor es una plantilla que se parametriza en la función de trabajo que calcula el resultado. El constructor ejecuta de forma asincrónica la función de trabajo en el `task_group` miembro de datos y se utiliza el [Concurrency:: Send](reference/concurrency-namespace-functions.md#send) función para escribir el resultado en la `single_assignment` miembro de datos.  
  
 [!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_3.cpp)]  
  
4.  En la sección `public` de la clase `async_future`, implemente el destructor. El destructor espera hasta que finaliza la tarea.  
  
 [!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_4.cpp)]  
  

5.  En la sección `public` de la clase `async_future`, implemente el método `get`. Este método usa la [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) función para recuperar el resultado de la función de trabajo.  

  
 [!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_5.cpp)]  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 En el siguiente ejemplo se muestran la clase `async_future` completa y un ejemplo de su uso. El `wmain` función crea un std::[vector](../../standard-library/vector-class.md) objeto que contiene 10.000 valores enteros aleatorios. A continuación, utiliza objetos `async_future` para encontrar los valores mayor y menor incluidos en el objeto `vector`.  
  
### <a name="code"></a>Código  
 [!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_6.cpp)]  
  
### <a name="comments"></a>Comentarios  
 Este ejemplo produce el siguiente resultado:  
  
```Output  
smallest: 0  
largest:  9999  
average:  4981  
```  
  
 En el ejemplo se usa el método `async_future::get` para recuperar los resultado del cálculo. El método `async_future::get` espera hasta que finaliza el cálculo si este está todavía activo.  
  
## <a name="robust-programming"></a>Programación sólida  


 Para ampliar la `async_future` clase para controlar las excepciones producidas por la función de trabajo, modifique la `async_future::get` método para llamar a la [concurrency::task_group::wait](reference/task-group-class.md#wait) método. El método `task_group::wait` inicia las excepciones que genera la función de trabajo.  


  
 En el ejemplo siguiente se muestra la versión modificada de la clase `async_future`: El `wmain` función utiliza un `try` - `catch` bloque para imprimir el resultado de la `async_future` objeto o para imprimir el valor de la excepción que se genera mediante la función de trabajo.  
  
 [!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_7.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
```Output  
caught exception: error  
```  
  
 Para obtener más información sobre el modelo de control de excepciones en el Runtime de simultaneidad, vea [Exception Handling](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `futures.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe/EHsc futures.cpp**  
  
## <a name="see-also"></a>Vea también  
 [Tutoriales del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [Control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [task_group (clase)](reference/task-group-class.md)   
 [single_assignment (clase)](../../parallel/concrt/reference/single-assignment-class.md)
