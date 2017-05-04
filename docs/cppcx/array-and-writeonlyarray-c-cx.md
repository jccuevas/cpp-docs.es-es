---
title: "Array y WriteOnlyArray (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef7cc5f9-cae6-4636-8220-f789e5b6aea4
caps.latest.revision: 28
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 28
---
# Array y WriteOnlyArray (C++/CX)
Puedes utilizar libremente matrices normales de estilo C o [std::array](../standard-library/array-class-stl.md) en un programa de [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] \(aunque [std::vector](../Topic/vector%20Class%201.md) suele ser preferible\), pero en las API publicadas en metadatos, debes convertir una matriz o vector de estilo C a un tipo [Platform::Array](../cppcx/platform-array-class.md) o [Platform::WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md) según como se vaya a usar. El tipo [Platform::Array](../cppcx/platform-array-class.md) no es tan eficaz como [std::vector](../Topic/vector%20Class%201.md), por lo que, como regla general, no debes utilizarlo en código interno que realice gran cantidad de operaciones en los elementos de la matriz.  
  
 Los tipos de matriz siguientes se pueden pasar a través de ABI:  
  
1.  const Platform::Array^  
  
2.  Platform::Array^\*  
  
3.  Platform::WriteOnlyArray  
  
4.  valor devuelto de Platform::Array^  
  
 Utiliza estos tipos de matriz para implementar los tres tipos de patrones de matriz definidos por [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)].  
  
 PassArray  
 Se utiliza cuando el llamador pasa una matriz a un método. El tipo de parámetro de entrada de C\+\+ es `const`[Platform::Array](../cppcx/platform-array-class.md)\<T\>.  
  
 FillArray  
 Se utiliza cuando el llamador pasa una matriz para el método que se va a rellenar. El tipo de parámetro de entrada de C\+\+ es [Platform::WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md)\<T\>.  
  
 ReceiveArray  
 Se usa cuando el llamador recibe una matriz que el método asigna. En C\+\+\/CX puedes devolver la matriz en el valor devuelto como Array^ o puedes devolverla como parámetro de salida como tipo Array^\*.  
  
## Patrón PassArray  
 Cuando el código de cliente pasa una matriz a un método de C\+\+ y el método no la modifica, el método acepta la matriz como const Array^. En el nivel de interfaz binaria de aplicación \(ABI\) de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)], esto se conoce como PassArray. En el ejemplo siguiente se muestra cómo pasar una matriz asignada en JavaScript a una función de C\+\+ que lee en ella.  
  
 [!code-javascript[cx_arrays#101](../snippets/javascript/VS_Snippets_Misc/cx_arrays/javascript/default.js#101)]  
  
 En el siguiente fragmento de código se muestra el método de C\+\+:  
  
 [!code-cpp[cx_arrays#01](../snippets/cpp/VS_Snippets_Misc/cx_arrays/cpp/class1.cpp#01)]  
  
## Patrón ReceiveArray  
 En el patrón ReceiveArray, el código de cliente declara una matriz y la pasa a un método que le asigna memoria y la inicializa. El tipo de parámetro de entrada de C\+\+ es un "puntero a sombrero": `Array<T>^*`. En el ejemplo siguiente se muestra cómo se declara un objeto de matriz en JavaScript y cómo se pasa a una función de C\+\+ que asigna memoria, inicializa los elementos y lo devuelve a JavaScript. JavaScript trata la matriz asignada como un valor devuelto, pero la función de C\+\+ la trata como un parámetro out.  
  
 [!code-javascript[cx_arrays#102](../snippets/javascript/VS_Snippets_Misc/cx_arrays/javascript/default.js#102)]  
  
 En el fragmento de código siguiente se muestran dos maneras de implementar el método de C\+\+:  
  
 [!code-cpp[cx_arrays#02](../snippets/cpp/VS_Snippets_Misc/cx_arrays/cpp/class1.cpp#02)]  
  
## Rellenar matrices  
 Si deseas asignar una matriz en el llamador y la inicializas o modificas en el destinatario, debes usar `WriteOnlyArray`. En el ejemplo siguiente se muestra cómo se implementa una función de C\+\+ que utiliza `WriteOnlyArray` y se invoca desde JavaScript.  
  
 [!code-javascript[cx_arrays#103](../snippets/javascript/VS_Snippets_Misc/cx_arrays/javascript/default.js#103)]  
  
 En el fragmento de código siguiente se muestra cómo implementar el método de C\+\+:  
  
 [!code-cpp[cx_arrays#03](../snippets/cpp/VS_Snippets_Misc/cx_arrays/cpp/class1.cpp#03)]  
  
## Conversiones de matriz  
 En este ejemplo se muestra cómo utilizar un tipo [Platform::Array](../cppcx/platform-array-class.md) para crear otros tipos de colecciones:  
  
 [!code-cpp[cx_arrays#05](../snippets/cpp/VS_Snippets_Misc/cx_arrays/cpp/class1.cpp#05)]  
  
 En el ejemplo siguiente se muestra cómo se crea un tipo [Platform::Array](../cppcx/platform-array-class.md) a partir de una matriz de estilo C y se devuelve desde un método público.  
  
 [!code-cpp[cx_arrays#06](../snippets/cpp/VS_Snippets_Misc/cx_arrays/cpp/class1.cpp#06)]  
  
## Matrices escalonadas  
 El sistema de tipos de Windows en tiempo de ejecución no admite el concepto de matrices escalonadas y, por consiguiente, no se puede usar `IVector<Platform::Array<T>>` como valor devuelto o parámetro del método en un método público. Para pasar una matriz escalonada o un grupo de secuencias a través de la ABI, usa `IVector<IVector<T>^>`.  
  
## Usar ArrayReference para evitar la copia de datos  
 En algunos escenarios donde los datos se pasan a través de la ABI en un tipo [Platform::Array](../cppcx/platform-array-class.md) y deseas en última instancia que dichos datos se procesen en una matriz de estilo C por razones de eficacia, puedes utilizar [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) para evitar la operación de copia adicional. Cuando pases un tipo [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) como argumento a un parámetro que toma un tipo `Platform::Array`, el objeto `ArrayReference` almacenará los datos directamente en la matriz de estilo C que especifiques. Solo debes tener en cuenta que `ArrayReference` no tiene ningún bloqueo en los datos de origen, por lo que si esos datos se modifican o eliminan en otro subproceso antes de completarse la llamada, los resultados serán no definidos \(undefined\).  
  
 En el siguiente fragmento de código se muestra cómo copiar los resultados de una operación [DataReader](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.datareader.aspx) en un tipo `Platform::Array` \(el patrón habitual\) y, a continuación, cómo sustituir `ArrayReference` para copiar los datos directamente en una matriz de estilo C:  
  
 [!code-cpp[cx_arrays#07](../snippets/cpp/VS_Snippets_Misc/cx_arrays/cpp/class1.h#07)]  
  
## Evitar exponer una matriz como una propiedad  
 En general, debes evitar exponer un tipo `Platform::Array` como una propiedad de una clase ref porque se devuelve la matriz completa, incluso cuando el código de cliente intenta únicamente acceder a un solo elemento. Cuando necesites exponer un contenedor de secuencias como una propiedad en una clase ref pública, es preferible que uses [Windows::Foundation::IVector](http://msdn.microsoft.com/library/windows/apps/br206631.aspx). En las API privadas o internas \(que no se publican para metadatos\), considera la opción de utilizar un contenedor de C\+\+ estándar como [std::vector](../Topic/vector%20Class%201.md).  
  
## Vea también  
 [Sistema de tipos](../cppcx/type-system-c-cx.md)   
 [Referencia del lenguaje Visual C\+\+](../cppcx/visual-c-language-reference-c-cx.md)   
 [Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)