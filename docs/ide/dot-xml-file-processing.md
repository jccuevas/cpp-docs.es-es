---
title: Procesamiento de archivos .Xml
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation, processing XML file
ms.assetid: e70fdeae-80ac-4872-ab24-771c5635cfbf
ms.openlocfilehash: 6592352e2afc02d3689f328ab37db6f289880cec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522192"
---
# <a name="xml-file-processing"></a>Procesamiento de archivos .Xml

El compilador genera una cadena de identificador para cada construcción del código que se etiqueta para generar documentación. Para obtener más información, vea [Etiquetas recomendadas para los comentarios de documentación](../ide/recommended-tags-for-documentation-comments-visual-cpp.md). La cadena de identificador identifica la construcción de forma exclusiva. Los programas que procesan el archivo .xml pueden usar la cadena de identificador para identificar el elemento de reflexión o de metadatos de .NET Framework correspondiente al que se aplica la documentación.

El archivo .xml no es una representación jerárquica del código; es una lista plana con un identificador generado para cada elemento.

El compilador cumple las siguientes reglas cuando genera las cadenas de identificador:

- No se coloca espacio en blanco en la cadena.

- La primera parte de la cadena ID identifica el tipo de miembro identificado, mediante un carácter único seguido de dos puntos. Se utilizan los siguientes tipos de miembros:

   |Carácter|Descripción|
   |---------------|-----------------|
   |N|namespace<br /><br /> No se pueden agregar comentarios de documentación a un espacio de nombres, pero se admiten referencias cref a un espacio de nombres.|
   |T|tipo: clase, interfaz, estructura, enumeración y delegado|
   |D|definición de tipos|
   |F|campo|
   |P|propiedad (incluidos indizadores u otras propiedades indizadas)|
   |M|método (incluidos métodos especiales como constructores, operadores, etc.)|
   |E|evento|
   |!|cadena de error<br /><br /> El resto de la cadena proporciona información sobre el error. El compilador de Visual C++ genera información de error para los vínculos que no se pueden resolver.|

- La segunda parte de la cadena es el nombre completo del elemento, que empieza por la raíz del espacio de nombres. El nombre del elemento, su tipo envolvente y el espacio de nombres se separan mediante puntos. Si el nombre del elemento ya contiene puntos, estos se reemplazan por el signo hash ("#"). Se supone que ningún elemento tiene un signo hash directamente en el nombre. Por ejemplo, el nombre completo del constructor de `String` sería "System.String.#ctor".

- Para propiedades y métodos, si hay argumentos para el método, sigue la lista de argumentos entre paréntesis. Si no hay ningún argumento, tampoco habrá paréntesis. Los argumentos están separados por comas. La codificación de cada argumento indica directamente cómo se codifica en una firma de .NET Framework:

   - Tipos base. Los tipos habituales (ELEMENT_TYPE_CLASS o ELEMENT_TYPE_VALUETYPE) se representan como el nombre completo del tipo.

   - Los tipos intrínsecos (por ejemplo, ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF y ELEMENT_TYPE_VOID) se representan como el nombre completo del tipo completo correspondiente, por ejemplo **System.Int32** o **System.TypedReference**.

   - ELEMENT_TYPE_PTR se representa como un "*" después del tipo modificado.

   - ELEMENT_TYPE_BYREF se representa como un "\@" después del tipo modificado.

   - ELEMENT_TYPE_PINNED se representa como "^" después del tipo modificado. El compilador de Visual C++ nunca genera este resultado.

   - ELEMENT_TYPE_CMOD_REQ se representa como "&#124;" y el nombre completo de la clase modificadora, después del tipo modificado. El compilador de Visual C++ nunca genera este resultado.

   - ELEMENT_TYPE_CMOD_OPT se representa como "!" y el nombre completo de la clase modificadora, después del tipo modificado.

   - ELEMENT_TYPE_SZARRAY se representa como "[]" después del tipo de elemento de la matriz.

   - ELEMENT_TYPE_GENERICARRAY se representa como "[?]" después del tipo de elemento de la matriz. El compilador de Visual C++ nunca genera este resultado.

   - ELEMENT_TYPE_ARRAY se representa como [*límite inferior*:`size`,*límite inferior*:`size`], donde el número de comas es la clasificación - 1, y los límites inferiores y el tamaño de cada dimensión, si se conocen, se representan en decimales. Si no se especifican un límite inferior ni un tamaño, simplemente se omiten. Si se omiten el límite inferior y el tamaño de una dimensión determinada, también se omite ":". Por ejemplo, una matriz de dos dimensiones con 1 como los límites inferiores y tamaños no especificados es [1:,1:].

   - ELEMENT_TYPE_FNPTR se representa como "=FUNC:`type`(*signature*)", donde `type` es el tipo de valor devuelto y *signature* se corresponde con los argumentos del método. Si no hay ningún argumento, se omiten los paréntesis. El compilador de Visual C++ nunca genera este resultado.

   Los siguientes componentes de la firma no se representan porque nunca se usan para diferenciar métodos sobrecargados:

   - Convención de llamada

   - Tipo de valor devuelto

   - ELEMENT_TYPE_SENTINEL

- Solo para los operadores de conversión, el valor devuelto del método se codifica como "~" seguido por el tipo de valor devuelto, como se ha codificado anteriormente.

- Para tipos genéricos, el nombre del tipo irá seguido de una tilde aguda y después de un número que indica el número de parámetros de tipo genérico.  Por ejemplo,

    ```xml
    <member name="T:MyClass`2">
    ```

   Para un tipo que se define como `public class MyClass<T, U>`.

   Para los métodos que toman tipos genéricos como parámetros, los parámetros de tipo genérico se especifican como números precedidos por tildes agudas (por ejemplo, \`0, \`1).  Cada número representa una notación de matriz de base cero para los parámetros genéricos del tipo.

## <a name="example"></a>Ejemplo

En los ejemplos siguientes se muestra cómo se generarían las cadenas de identificador para una clase y sus miembros.

```cpp
// xml_id_strings.cpp
// compile with: /clr /doc /LD
///
namespace N {
// "N:N"

   /// <see cref="System" />
   //  <see cref="N:System"/>
   ref class X {
   // "T:N.X"

   protected:
      ///
      !X(){}
      // "M:N.X.Finalize", destructor's representation in metadata

   public:
      ///
      X() {}
      // "M:N.X.#ctor"

      ///
      static X() {}
      // "M:N.X.#cctor"

      ///
      X(int i) {}
      // "M:N.X.#ctor(System.Int32)"

      ///
      ~X() {}
      // "M:N.X.Dispose", Dispose function representation in metadata

      ///
      System::String^ q;
      // "F:N.X.q"

      ///
      double PI;
      // "F:N.X.PI"

      ///
      int f() { return 1; }
      // "M:N.X.f"

      ///
      int bb(System::String ^ s, int % y, void * z) { return 1; }
      // "M:N.X.bb(System.String,System.Int32@,System.Void*)"

      ///
      int gg(array<short> ^ array1, array< int, 2 >^ IntArray) { return 0; }
      // "M:N.X.gg(System.Int16[], System.Int32[0:,0:])"

      ///
      static X^ operator+(X^ x, X^ xx) { return x; }
     // "M:N.X.op_Addition(N.X,N.X)"

      ///
      property int prop;
      // "M:N.X.prop"

      ///
      property int prop2 {
      // "P:N.X.prop2"

         ///
         int get() { return 0; }
         // M:N.X.get_prop2

         ///
         void set(int i) {}
         // M:N.X.set_prop2(System.Int32)
      }

      ///
      delegate void D(int i);
      // "T:N.X.D"

      ///
      event D ^ d;
      // "E:N.X.d"

      ///
      ref class Nested {};
      // "T:N.X.Nested"

      ///
      static explicit operator System::Int32 (X x) { return 1; }
      // "M:N.X.op_Explicit(N.X!System.Runtime.CompilerServices.IsByValue)~System.Int32"
   };
}
```

## <a name="see-also"></a>Vea también

[Documentación de XML](../ide/xml-documentation-visual-cpp.md)