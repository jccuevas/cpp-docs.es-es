---
title: Archivos de salida binarios
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], binary output files
- files [C++], binary output files
- binary data, binary output files
ms.assetid: 180954af-8cd6-444b-9a76-2f630a3389d8
ms.openlocfilehash: 99445275a8f92622f451e8a88082dc2b28fb60b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62414066"
---
# <a name="binary-output-files"></a>Archivos de salida binarios

Los flujos se diseñaron originalmente para texto, por lo que el modo de salida predeterminado es texto. En modo de texto, el carácter de nueva línea (hexadecimal 10) se expande a un retorno de carro-salto de línea (solo de 16 bits). La expansión puede causar problemas, como se muestra aquí:

```cpp
// binary_output_files.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;
int iarray[2] = { 99, 10 };
int main( )
{
    ofstream os( "test.dat" );
    os.write( (char *) iarray, sizeof( iarray ) );
}
```

Puede esperar que este programa envíe la secuencia de bytes { 99, 0, 10, 0 }; en su lugar, envía { 99, 0, 13, 10, 0 }, lo que provoca problemas para un programa que esperaba una entrada binaria. Si necesita una salida binaria True, en la que se escriben caracteres sin traducir, puede especificar la salida binaria mediante el argumento openmode del constructor [ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream):

```cpp
// binary_output_files2.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;
int iarray[2] = { 99, 10 };

int main()
{
   ofstream ofs ( "test.dat", ios_base::binary );

   // Exactly 8 bytes written
   ofs.write( (char*)&iarray[0], sizeof(int)*2 );
}
```

## <a name="see-also"></a>Vea también

[Flujos de salida](../standard-library/output-streams.md)<br/>
