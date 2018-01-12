---
title: Array y WriteOnlyArray (C++ / CX) | Documentos de Microsoft
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef7cc5f9-cae6-4636-8220-f789e5b6aea4
caps.latest.revision: "28"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6c2e05e3570179ac315e16576c72d2a37b580482
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="array-and-writeonlyarray-ccx"></a>Array y WriteOnlyArray (C++/CX)
También puede utilizar libremente matrices normales de estilo C o [std:: Array](../standard-library/array-class-stl.md) en C++ / programa CX (aunque [std:: vector](../standard-library/vector-class.md) a menudo es mejor usar), pero en cualquier API que está publicado en metadatos, debe convertir una matriz de estilo C o de vector en una [Platform:: Array](../cppcx/platform-array-class.md) o [writeonlyarray](../cppcx/platform-writeonlyarray-class.md) tipo dependiendo de cómo se usa. El tipo [Platform::Array](../cppcx/platform-array-class.md) no es tan eficaz como [std::vector](../standard-library/vector-class.md), por lo que, como regla general, no debes utilizarlo en código interno que realice gran cantidad de operaciones en los elementos de la matriz.  
  
 Los tipos de matriz siguientes se pueden pasar a través de ABI:  
  
1.  const Platform::Array^  
  
2.  Platform::Array^*  
  
3.  Platform::WriteOnlyArray  
  
4.  valor devuelto de Platform::Array^  
  
 Utilice estos tipos de matriz para implementar los tres tipos de patrones de matriz definidos por el tiempo de ejecución de Windows.  
  
 PassArray  
 Se utiliza cuando el llamador pasa una matriz a un método. El tipo de parámetro de entrada de C++ es `const` [Platform:: Array](../cppcx/platform-array-class.md)\<T >.  
  
 FillArray  
 Se utiliza cuando el llamador pasa una matriz para el método que se va a rellenar. El tipo de parámetro de entrada de C++ es [writeonlyarray](../cppcx/platform-writeonlyarray-class.md)\<T >.  
  
 ReceiveArray  
 Se usa cuando el llamador recibe una matriz que el método asigna. En C++/CX puedes devolver la matriz en el valor devuelto como Array^ o puedes devolverla como parámetro de salida como tipo Array^*.  
  
## <a name="passarray-pattern"></a>Patrón PassArray  
 Cuando el código de cliente pasa una matriz a un método de C++ y el método no la modifica, el método acepta la matriz como const Array^. En el nivel de interfaz binaria (ABI) de aplicación en tiempo de ejecución de Windows, esto se conoce como PassArray. En el ejemplo siguiente se muestra cómo pasar una matriz asignada en JavaScript a una función de C++ que lee en ella.  
  
 [!code-javascript[cx_arrays#101](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_1.js)]  
  
 En el siguiente fragmento de código se muestra el método de C++:  
  
 [!code-cpp[cx_arrays#01](../cppcx/codesnippet/CPP/js-array/class1.cpp#01)]  
  
## <a name="receivearray-pattern"></a>Patrón ReceiveArray  
 En el patrón ReceiveArray, el código de cliente declara una matriz y la pasa a un método que le asigna memoria y la inicializa. El tipo de parámetro de entrada de C++ es un "puntero a sombrero": `Array<T>^*`. En el ejemplo siguiente se muestra cómo se declara un objeto de matriz en JavaScript y cómo se pasa a una función de C++ que asigna memoria, inicializa los elementos y lo devuelve a JavaScript. JavaScript trata la matriz asignada como un valor devuelto, pero la función de C++ la trata como un parámetro out.  
  
 [!code-javascript[cx_arrays#102](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_3.js)]  
  
 En el fragmento de código siguiente se muestran dos maneras de implementar el método de C++:  
  
 [!code-cpp[cx_arrays#02](../cppcx/codesnippet/CPP/js-array/class1.cpp#02)]  
  
## <a name="fill-arrays"></a>Rellenar matrices  
 Si deseas asignar una matriz en el llamador y la inicializas o modificas en el destinatario, debes usar `WriteOnlyArray`. En el ejemplo siguiente se muestra cómo se implementa una función de C++ que utiliza `WriteOnlyArray` y se invoca desde JavaScript.  
  
 [!code-javascript[cx_arrays#103](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_5.js)]  
  
 En el fragmento de código siguiente se muestra cómo implementar el método de C++:  
  
 [!code-cpp[cx_arrays#03](../cppcx/codesnippet/CPP/js-array/class1.cpp#03)]  
  
## <a name="array-conversions"></a>Conversiones de matriz  
 En este ejemplo se muestra cómo utilizar un tipo [Platform::Array](../cppcx/platform-array-class.md) para crear otros tipos de colecciones:  
  
 [!code-cpp[cx_arrays#05](../cppcx/codesnippet/CPP/js-array/class1.cpp#05)]  
  
 En el ejemplo siguiente se muestra cómo se crea un tipo [Platform::Array](../cppcx/platform-array-class.md) a partir de una matriz de estilo C y se devuelve desde un método público.  
  
 [!code-cpp[cx_arrays#06](../cppcx/codesnippet/CPP/js-array/class1.cpp#06)]  
  
## <a name="jagged-arrays"></a>Matrices escalonadas  
 El sistema de tipos de Windows en tiempo de ejecución no admite el concepto de matrices escalonadas y, por consiguiente, no se puede usar `IVector<Platform::Array<T>>` como valor devuelto o parámetro del método en un método público. Para pasar una matriz escalonada o un grupo de secuencias a través de la ABI, usa `IVector<IVector<T>^>`.  
  
## <a name="use-arrayreference-to-avoid-copying-data"></a>Usar ArrayReference para evitar la copia de datos  
 En algunos escenarios donde los datos se pasan a través de la ABI en un tipo [Platform::Array](../cppcx/platform-array-class.md)y deseas en última instancia que dichos datos se procesen en una matriz de estilo C por razones de eficacia, puedes utilizar [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) para evitar la operación de copia adicional. Cuando pases un tipo [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) como argumento a un parámetro que toma un tipo `Platform::Array`, el objeto `ArrayReference` almacenará los datos directamente en la matriz de estilo C que especifiques. Solo debes tener en cuenta que `ArrayReference` no tiene ningún bloqueo en los datos de origen, por lo que si esos datos se modifican o eliminan en otro subproceso antes de completarse la llamada, los resultados serán no definidos (undefined).  
  
 En el siguiente fragmento de código se muestra cómo copiar los resultados de una operación [DataReader](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.datareader.aspx) en un tipo `Platform::Array` (el patrón habitual) y, a continuación, cómo sustituir `ArrayReference` para copiar los datos directamente en una matriz de estilo C:  
  
 [!code-cpp[cx_arrays#07](../cppcx/codesnippet/CPP/js-array/class1.h#07)]  
  
## <a name="avoid-exposing-an-array-as-a-property"></a>Evitar exponer una matriz como una propiedad  
 En general, debes evitar exponer un tipo `Platform::Array` como una propiedad de una clase ref porque se devuelve la matriz completa, incluso cuando el código de cliente intenta únicamente acceder a un solo elemento. Cuando necesites exponer un contenedor de secuencias como una propiedad en una clase ref pública, es preferible que uses [Windows::Foundation::IVector](http://msdn.microsoft.com/library/windows/apps/br206631.aspx) . En las API privadas o internas (que no se publican para metadatos), considera la opción de utilizar un contenedor de C++ estándar como [std::vector](../standard-library/vector-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Sistema de tipos](../cppcx/type-system-c-cx.md)   
 [Referencia del lenguaje de Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)