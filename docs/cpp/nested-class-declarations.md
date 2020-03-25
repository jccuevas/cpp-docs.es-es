---
title: Declaraciones de clase anidadas
ms.date: 11/04/2016
helpviewer_keywords:
- classes [C++], declaring
- declarations, class
- nested classes [C++]
- nested classes [C++], declaring
- declaring classes [C++]
- declarations, nested classes
ms.assetid: c02e471d-b7f9-41b8-8ef6-2323f006dbd5
ms.openlocfilehash: a1464ce9ca8349550160c768265c1c4eada93209
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161170"
---
# <a name="nested-class-declarations"></a>Declaraciones de clase anidadas

Una clase puede declararse dentro del ámbito de otra clase. Esta clase se denomina una “clase anidada”. Las clases anidadas se consideran dentro del ámbito de la clase envolvente y están disponibles para su uso dentro de ese ámbito. Para hacer referencia a una clase anidada de un ámbito distinto al ámbito de inclusión inmediato, debe utilizar un nombre completo.

En el siguiente ejemplo se muestra cómo declarar clases anidadas:

```cpp
// nested_class_declarations.cpp
class BufferedIO
{
public:
   enum IOError { None, Access, General };

   // Declare nested class BufferedInput.
   class BufferedInput
   {
   public:
      int read();
      int good()
      {
         return _inputerror == None;
      }
   private:
       IOError _inputerror;
   };

   // Declare nested class BufferedOutput.
   class BufferedOutput
   {
      // Member list
   };
};

int main()
{
}
```

`BufferedIO::BufferedInput` y `BufferedIO::BufferedOutput` se declaran en `BufferedIO`. Estos nombres de clase no son visibles fuera del ámbito de la clase `BufferedIO`. Sin embargo, un objeto de tipo `BufferedIO` no contiene objetos de los tipos `BufferedInput` o `BufferedOutput`.

Las clases anidadas pueden utilizar directamente nombres, nombres de tipo, nombres de miembros estáticos y enumeradores solo de la clase envolvente. Para usar nombres de otros miembros de clase, debe utilizar punteros, referencias o nombres de objeto.

En el ejemplo anterior de `BufferedIO`, pueden tener acceso directamente a la enumeración `IOError` funciones miembro de las clases anidadas, `BufferedIO::BufferedInput` o `BufferedIO::BufferedOutput`, como se muestra en la función `good`.

> [!NOTE]
>  Las clases anidadas declaran solo tipos dentro del ámbito de la clase. No provocan la creación de objetos contenidos de la clase anidada. El ejemplo anterior declara dos clases anidadas pero no declara ningún objeto de estos tipos de clase.

Una excepción a la visibilidad del ámbito de una declaración de clase es cuando se declara un nombre de tipo junto con una declaración adelantada.  En este caso, el nombre de clase declarado por la declaración adelantada está visible fuera de la clase envolvente, con el ámbito definido de modo que sea el menor envolvente no de clase.  Por ejemplo:

```cpp
// nested_class_declarations_2.cpp
class C
{
public:
    typedef class U u_t; // class U visible outside class C scope
    typedef class V {} v_t; // class V not visible outside class C
};

int main()
{
    // okay, forward declaration used above so file scope is used
    U* pu;

    // error, type name only exists in class C scope
    u_t* pu2; // C2065

    // error, class defined above so class C scope
    V* pv; // C2065

    // okay, fully qualified name
    C::V* pv2;
}
```

## <a name="access-privilege-in-nested-classes"></a>Privilegio de acceso en clases anidadas

El anidamiento de una clase dentro de otra clase no proporciona privilegios de acceso especiales a las funciones miembro de la clase anidada. De forma similar, las funciones miembro de la clase envolvente no tienen ningún acceso especial a los miembros de la clase anidada.

## <a name="member-functions-in-nested-classes"></a>Funciones miembro en clases anidadas

Las funciones miembro declaradas en clases anidadas se pueden definir en el ámbito del archivo. El ejemplo anterior se podría haber escrito:

```cpp
// member_functions_in_nested_classes.cpp
class BufferedIO
{
public:
    enum IOError { None, Access, General };
    class BufferedInput
    {
    public:
        int read(); // Declare but do not define member
        int good(); //  functions read and good.
    private:
        IOError _inputerror;
    };

    class BufferedOutput
    {
        // Member list.
    };
};
// Define member functions read and good in
//  file scope.
int BufferedIO::BufferedInput::read()
{
   return(1);
}

int BufferedIO::BufferedInput::good()
{
    return _inputerror == None;
}
int main()
{
}
```

En el ejemplo anterior, se utiliza la sintaxis *Qualified-type-name* para declarar el nombre de la función. La declaración:

```cpp
BufferedIO::BufferedInput::read()
```

significa “la función `read` que es miembro de la clase `BufferedInput` que está en el ámbito de la clase `BufferedIO`.” Dado que esta declaración usa la sintaxis *Qualified-type-name* , son posibles las construcciones de la forma siguiente:

```cpp
typedef BufferedIO::BufferedInput BIO_INPUT;

int BIO_INPUT::read()
```

La declaración anterior es equivalente a la anterior, pero usa un nombre **typedef** en lugar de los nombres de clase.

## <a name="friend-functions-in-nested-classes"></a>Funciones friend en clases anidadas

Las funciones friend declaradas en una clase anidada se considera que están en el ámbito de la clase anidada, no la clase envolvente. Por lo tanto, las funciones friend no obtienen privilegios de acceso especiales a miembros o funciones miembro de la clase envolvente. Si desea utilizar un nombre declarado en una clase anidada en una función friend y la función friend está definida en el ámbito del archivo, debe usar nombres de tipo representativo del modo siguiente:

```cpp
// friend_functions_and_nested_classes.cpp

#include <string.h>

enum
{
    sizeOfMessage = 255
};

char *rgszMessage[sizeOfMessage];

class BufferedIO
{
public:
    class BufferedInput
    {
    public:
        friend int GetExtendedErrorStatus();
        static char *message;
        static int  messageSize;
        int iMsgNo;
   };
};

char *BufferedIO::BufferedInput::message;
int BufferedIO::BufferedInput::messageSize;

int GetExtendedErrorStatus()
{
    int iMsgNo = 1; // assign arbitrary value as message number

    strcpy_s( BufferedIO::BufferedInput::message,
              BufferedIO::BufferedInput::messageSize,
              rgszMessage[iMsgNo] );

    return iMsgNo;
}

int main()
{
}
```

El código siguiente muestra la función `GetExtendedErrorStatus` declarada como una función friend. En la función, que se define en el ámbito de archivo, se copia un mensaje de una matriz estática en un miembro de clase. Observe que una mejor implementación de `GetExtendedErrorStatus` consiste en declararlo como:

```cpp
int GetExtendedErrorStatus( char *message )
```

Con la interfaz anterior, varias clases pueden utilizar los servicios de esta función pasando una ubicación de memoria en la que desean que se copie el mensaje de error.

## <a name="see-also"></a>Consulte también

[Clases y structs](../cpp/classes-and-structs-cpp.md)
