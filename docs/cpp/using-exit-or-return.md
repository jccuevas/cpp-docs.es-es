---
title: Usar exit o return
ms.date: 11/04/2016
f1_keywords:
- Exit
helpviewer_keywords:
- exit function
- return keyword [C++], using for program termination
ms.assetid: b5136c5c-2505-4229-8691-2a1d6a98760b
ms.openlocfilehash: d60084c0d07d3eeb3f49a1fea53de04d150a701b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152727"
---
# <a name="using-exit-or-return"></a>Usar exit o return

Cuando se llama a **salir** o ejecutar un **devolver** instrucción desde `main`, objetos estáticos se destruyen en el orden inverso de la inicialización. En el ejemplo siguiente se muestra cómo funcionan esa inicialización y limpieza.

## <a name="example"></a>Ejemplo

```cpp
// using_exit_or_return1.cpp
#include <stdio.h>
class ShowData {
public:
   // Constructor opens a file.
   ShowData( const char *szDev ) {
   errno_t err;
      err = fopen_s(&OutputDev, szDev, "w" );
   }

   // Destructor closes the file.
   ~ShowData() { fclose( OutputDev ); }

   // Disp function shows a string on the output device.
   void Disp( char *szData ) {
      fputs( szData, OutputDev );
   }
private:
   FILE *OutputDev;
};

//  Define a static object of type ShowData. The output device
//   selected is "CON" -- the standard output device.
ShowData sd1 = "CON";

//  Define another static object of type ShowData. The output
//   is directed to a file called "HELLO.DAT"
ShowData sd2 = "hello.dat";

int main() {
   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

En el ejemplo anterior, los objetos estáticos `sd1` y `sd2` se crean e inicializan antes de la entrada a `main`. Después de que finalice este programa mediante el **devolver** instrucción, primero `sd2` se destruye y, a continuación, `sd1`. El destructor para la clase de `ShowData` cierra los archivos asociados a estos objetos estáticos.

Otra forma de escribir este código es declarar los objetos `ShowData` con ámbito de bloque, lo que permite destruirlos cuando salen del ámbito:

```cpp
int main() {
   ShowData sd1, sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

## <a name="see-also"></a>Vea también

[Consideraciones de finalización adicionales](../cpp/additional-termination-considerations.md)