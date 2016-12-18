---
title: "Procesamiento de archivos .Xml | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "documentación XML, procesar archivos XML"
ms.assetid: e70fdeae-80ac-4872-ab24-771c5635cfbf
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procesamiento de archivos .Xml
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El compilador genera una cadena id. por cada construcción del código marcada para generar documentación.  Para obtener más información, vea [Comentarios de documentación recomendados de etiquetas](../ide/recommended-tags-for-documentation-comments-visual-cpp.md).  La cadena id. identifica de forma exclusiva cada construcción.  Programas que procesan el archivo .xml pueden utilizar la cadena de identificador para identificar los metadatos de .NET Framework o el elemento correspondientes de la reflexión para los que la documentación se aplica.  
  
 El archivo .xml no es una representación jerárquica del código, es una lista plana con un identificador generado para cada elemento.  
  
 El compilador cumple las siguientes reglas cuando genera las cadenas id.:  
  
-   No se coloca ningún espacio en blanco en la cadena.  
  
-   La primera parte de la cadena de id. identifica el tipo de miembro por medio de un único carácter seguido de dos puntos.  Se utilizan los siguientes tipos de miembros:  
  
    |Carácter|Descripción|  
    |--------------|-----------------|  
    |N|Espacio de nombres<br /><br /> No puede agregar los comentarios de documentación a un espacio de nombres, referencias cref a un espacio de nombres es posible.|  
    |T|tipo: class, interface, struct, enum, delegate|  
    |D|definición de tipos|  
    |F|campo|  
    |P|propiedad \(incluidos indizadores u otras propiedades indizadas\)|  
    |M|método \(incluidos métodos especiales como constructores, operadores, etc.\)|  
    |E|evento|  
    |\!|cadena de error<br /><br /> El resto de la cadena proporciona información acerca del error.  El compilador de Visual C\+\+ genera información de error para los vínculos que no pueden resolver.|  
  
-   La segunda parte de la cadena es el nombre completo del elemento, empezando en la raíz del espacio de nombres.  Separan el nombre del elemento, el tipo contenedor o tipos, y el espacio de nombres durante períodos.  Si el propio nombre del elemento contiene puntos, éstos se reemplazan por el signo \#.  Se supone que ningún elemento tiene un hash\- signo directamente en su nombre.  Por ejemplo, el nombre completo del constructor de `String` sería “System.String.\#ctor”.  
  
-   Para propiedades y métodos, si existen argumentos para el método, la lista de argumentos que se encuentra entre paréntesis aparece a continuación.  Si no existen argumentos, no se escribe ningún paréntesis.  Los argumentos se separan por comas.  La codificación de cada argumento indica directamente cómo se codifica en una firma de .NET Framework:  
  
    -   Tipos base.  Los tipos normales \(ELEMENT\_TYPE\_CLASS o ELEMENT\_TYPE\_VALUETYPE\) se representan como el nombre completo del tipo.  
  
    -   Tipos intrínsecos \(por ejemplo, ELEMENT\_TYPE\_I4, ELEMENT\_TYPE\_OBJECT, ELEMENT\_TYPE\_STRING, ELEMENT\_TYPE\_TYPEDBYREF.  y ELEMENT\_TYPE\_VOID\) se representan como el nombre completo del tipo completo correspondiente, por ejemplo, **System.Int32** o **System.TypedReference**.  
  
    -   ELEMENT\_TYPE\_PTR se representa con un '\*' a continuación del tipo modificado.  
  
    -   ELEMENT\_TYPE\_BYREF se representa con un signo '@' a continuación del tipo modificado.  
  
    -   ELEMENT\_TYPE\_PINNED se representa con un signo '^' a continuación del tipo modificado.  El compilador de Visual C\+\+ nunca genera esto.  
  
    -   ELEMENT\_TYPE\_CMOD\_REQ se representa como una '&#124;' y el nombre completo de la clase modificadora, a continuación del tipo modificado.  El compilador de Visual C\+\+ nunca genera esto.  
  
    -   ELEMENT\_TYPE\_CMOD\_OPT se representa como '\!' y el nombre completo de la clase modificadora, a continuación del tipo modificado.  
  
    -   ELEMENT\_TYPE\_SZARRAY se representa como "\[\]" a continuación del tipo de elemento de la matriz.  
  
    -   ELEMENT\_TYPE\_GENERICARRAY se representa como "\[?\]" a continuación del tipo de elemento de la matriz.  El compilador de Visual C\+\+ nunca genera esto.  
  
    -   ELEMENT\_TYPE\_ARRAY se representa como \[*límite inferior*:`size`,*límite inferior*:`size`\] donde el número de comas es el rango, 1, y los límites inferiores y el tamaño de cada dimensión, si se conocen, se representan en decimal.  Si no se especifica un límite inferior ni un tamaño, simplemente se omite.  Si el límite inferior y el tamaño de una dimensión particular se omiten, el signo ':' también se omite.  Por ejemplo, una matriz de dos dimensiones con 1 como límites inferiores y sin tamaños especificados se representa como \[1:,1:\].  
  
    -   ELEMENT\_TYPE\_FNPTR se representa como "\=FUNC:`type` \(*firma*\)", donde `type` es el tipo de valor devuelto y *firma* corresponde a los argumentos del método.  Si no existen argumentos, los paréntesis se omiten.  El compilador de Visual C\+\+ nunca genera esto.  
  
     Los siguientes componentes de una firma no se representan porque nunca se utilizan para diferenciar métodos sobrecargados:  
  
    -   convención de llamadas  
  
    -   tipo de valor devuelto  
  
    -   ELEMENT\_TYPE\_SENTINEL  
  
-   Para los operadores de conversión sólo, el valor devuelto del método se codifica como “~” seguido del tipo de valor devuelto, como codificado previamente.  
  
-   En los tipos genéricos, el nombre del tipo va seguido de un acento invertido y de un número que indica el número de parámetros de tipo genérico.  Por ejemplo,  
  
    ```  
    <member name="T:MyClass`2">  
    ```  
  
     Para un tipo que se define como `public class MyClass<T, U>`.  
  
     Para métodos que toman tipos genéricos como parámetros, los parámetros de tipo genérico se especifican como números con un acento invertido antepuesto \(por ejemplo \`0, \`1\).  Cada número representa una notación de matrices basada en cero en los parámetros genéricos del tipo.  
  
## Ejemplo  
 Los ejemplos siguientes muestran cómo generarían cadenas de una clase y sus miembros.  
  
```  
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
  
## Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)